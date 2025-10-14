# Production Crew Management System

A comprehensive web application for managing school production crew equipment, schedules, and events.

## Features

- 📦 **Equipment Tracking** - Barcode scanning system to track equipment locations
- 📋 **Collaborative Pick Lists** - Team-based checklists for events
- 🎨 **Stage Plan Sharing** - Upload and share stage layouts
- 📅 **Event Calendar** - Schedule events and assign crew members
- 👥 **Crew Scheduling** - Assign roles and track crew availability
- 🔐 **Access Control** - User authentication with admin privileges

## Setup Instructions

### 1. Install Python Requirements

```bash
pip install -r requirements.txt
```

### 2. Create Folder Structure

Create the following folders in your project directory:

```bash
mkdir templates uploads
```

### 3. Save Template Files

Save all the HTML templates in the `templates` folder:
- `base.html`
- `login.html`
- `dashboard.html`
- `equipment.html`
- `picklist.html`
- `stageplans.html`
- `calendar.html`
- `event_detail.html`
- `admin.html`

### 4. Run the Application

```bash
python app.py
```

The application will:
- Create the SQLite database automatically
- Create a default admin account:
  - Username: `admin`
  - Password: `admin123`
- Start the server on `http://0.0.0.0:5000`

### 5. Change Default Admin Password

**IMPORTANT:** After first login, create a new admin account and delete the default one for security.

## Accessing on School Network

### Option 1: Direct IP Access
1. Find your laptop's local IP address:
   - Windows: `ipconfig` (look for IPv4 Address)
   - Mac/Linux: `ifconfig` or `ip addr`
2. Access from any device on the school network: `http://YOUR_IP:5000`

### Option 2: Set a Hostname
Configure your laptop with a static hostname that can be accessed via `http://hostname.local:5000`

## Google Sheets Integration for Equipment

To sync equipment from Google Sheets:

1. Export your Google Sheet as CSV
2. Use the Admin panel to bulk import equipment (you'll need to add this feature or manually add items)
3. Each item should have:
   - Barcode (unique identifier)
   - Name
   - Category
   - Storage Location
   - Notes

## Using Barcodes

### For Scanning:
1. Generate barcodes for your equipment (you can use free online barcode generators)
2. Print and attach them to equipment boxes
3. Users can access the Equipment page and enter the barcode manually
4. The system will display the item's location instantly

### Barcode Format Recommendations:
- Use Code 128 or QR codes
- Include the barcode number on the label for manual entry
- Format: `PROD-XXXX` (e.g., PROD-0001, PROD-0002)

## Mobile Access

The application is mobile-responsive. Crew members can:
- Scan barcodes by typing them in (camera scanning requires additional JavaScript libraries)
- Check off pick list items
- View stage plans
- Check their schedule

## Security Recommendations

1. **Change the SECRET_KEY** in `app.py`:
   ```python
   app.config['SECRET_KEY'] = 'your-unique-secret-key-here'
   ```

2. **Use HTTPS** if exposing publicly (consider using ngrok or reverse proxy)

3. **Regular Backups**: Backup the `production_crew.db` file regularly

4. **Limit Admin Access**: Only give admin privileges to trusted crew leaders

## Database Location

The SQLite database (`production_crew.db`) is created in the same directory as `app.py`.

## File Uploads

Stage plans and images are stored in the `uploads/` folder. Maximum file size: 16MB.

## Troubleshooting

### Can't Access from Other Devices
- Check firewall settings on the host laptop
- Ensure all devices are on the same network
- Try accessing via IP address instead of hostname

### Database Errors
- Delete `production_crew.db` and restart to recreate
- Check file permissions on the database file

### Upload Errors
- Verify the `uploads` folder exists and is writable
- Check file size (max 16MB)

## Future Enhancements

Consider adding:
- Camera-based barcode scanning (using a library like QuaggaJS)
- Email notifications for event assignments
- Conflict checking for equipment double-booking
- Export reports to PDF
- Mobile app version

## Support

For issues or questions, contact your school's tech crew supervisor.

## License

This is custom software for educational use.
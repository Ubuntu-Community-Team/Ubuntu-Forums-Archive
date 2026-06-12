---
title: "CUPS doesn't let me print from network"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by Queue29 on 2009-10-02
I have a headless ubuntu server that needs to share a printer (a Brother 2070N on USB). To configure cups, I had to modify cups.conf quite a bit to let me access the printer management pages, but I did manage to get it working. I can print using the lpr command, as well as print test pages using the management interface's "Print Test Page" button from any computer on my network. However, I cannot actually set up Ubuntu, Fedora, Vista, or OSX to see the network printer, and it's driving me insane. 

I would have expected at least ubuntu to be able to connect, but all I get is "This print share is not accessible."

This is my cupsd.conf file:
```

#
# "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $"
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# A mess of guesses just to add a printer over http management 
# 192.168.1.148 is the assigned ip of the server
Allow all
AccessLog mycupsd.log
AutoPurgeJobs Yes
BrowseAddress 192.168.1.148
BrowseAllow all
Listen *:631
Port 631
BrowsePort 631
ServerName localhost


# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Yes
Browsing On
BrowseOrder allow,allow


# Default authentication type, when authentication is required...
DefaultAuthType None

# Restrict access to the server...
<Location />
  Order allow,allow
  Allow 192.168.1.0/24
  Allow From 127.0.0.1
  Allow From 192.168.1.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Never
  Order allow,allow
  Allow 192.168.1.0/24
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType None
  Order allow,allow
  Allow 192.168.1.0/24
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Order allow,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType None
    Order allow,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType None
    Order allow,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order allow,allow
  </Limit>

  <Limit All>
    Order allow,allow
  </Limit>
</Policy>

#
# End of "$Id: cupsd.conf.in 7199 2008-01-08 00:16:30Z mike $".
#

```

---


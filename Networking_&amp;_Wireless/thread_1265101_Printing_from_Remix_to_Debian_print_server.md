---
title: "Printing from Remix to Debian print server"
date: 2009-09-13
forum: Networking &amp; Wireless
---

### Post by Opens on 2009-09-13
Hi All, following problem:

1. Laptop with Ubuntu Remix 9.04 should print to Debian Server connected to HP psc 1210
2. The laptop sees the printer (see attached screenshot)
3. The laptop cannot access the printer (see attached screenshot)
4. Sometimes I get to select the printer and the printer status is set with a green tik, sometimes not
5. When I used Mepis 7 on this laptop, it was no problem to print via the debian server to the HP printer, so I assume that it is not a debian configuration problem.

Here the laptop cupsd.conf
> #
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See &quot;man cupsd.conf&quot; for a complete description of this
#   file.
#

# Log general information in error_log - change &quot;info&quot; to &quot;debug&quot; for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen localhost:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing Off
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#
Here the debian cupsd.conf
> #
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See &quot;man cupsd.conf&quot; for a complete description of this
#   file.
#

# Log general information in error_log - change &quot;info&quot; to &quot;debug&quot; for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen *:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server... (christian)
<Location />
  Order allow,deny
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>


  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

#
#
I guess somebody will spot the permission problem in a second :)
 Thanks for your help in advance

Cheers
Chris

---

### Post by Opens on 2009-09-15
Hmm, seems to be trickier than I thought. Well, I will wait a bit perhaps, somebody comes up with an idea.

Thanks in advance for this
Chris

---

### Post by Opens on 2009-09-20
I used the [http://192.168.44.74:631/printers/](http://192.168.44.74:631/printers/) command on the ubuntu remix machine  to find the printer share and was able to print the  testpage. Only when I configure the whole thing with the printer tool of ubuntu and click verify, it says "this print share is not accessible".

Thanks in advance
Chris

---


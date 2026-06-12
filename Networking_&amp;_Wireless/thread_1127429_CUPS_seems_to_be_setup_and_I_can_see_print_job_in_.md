---
title: "CUPS seems to be setup and I can see print job in admin, but no prints"
date: 2009-04-16
forum: Networking &amp; Wireless
---

### Post by Rebajas on 2009-04-16
Hi everyone,

Not sure where to start with this as I have found far too many threads offering advice to follow.

I have set up CUPS and can administer my printer and connect to it from my wired Ubuntu desktop and my wireless Ubuntu laptop (XP to do later).

I can send a print job from both machines and they appear in the jobs list in the admin screen, but nothing comes out of the printer.

Not sure where to start looking for a fix as I have no clue what might be broken (first attempt at network printing).

The printer is attached to a headless Ubuntu Server install with no GUI, the printer is a Epson R300 (prints from nozzle check).

The config is below:
```

LogLevel debug

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
Listen localhost:631
Listen 192.168.0.6:631
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
# BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic
DefaultEncryption Never

# Restrict access to the server...
<Location />
  Allow all
  Order allow,deny
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Allow all
  Order allow,deny
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  Allow all
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
```

If you think you might have an idea but need more info, give me a shout and I'll get it posted! 

Thanks in advance,


Tony.

---

### Post by Rebajas on 2009-04-16
Well how about that - Windows XP tells me that I have the wrong driver installed on the server for that printer.

So now the question is what PPD profile do I need to use from the rather long dropdown in the admin screen:

Or do I need to install something like Gutenberg (or similar) that I have seen mentioned in the past?

Good I have at least one Microsoft box in my house :)


Tony.

---

### Post by Rebajas on 2009-04-16
Okay - I can now print from the 2 Ubuntu machines - but now need to work out the XP machine (not such a big deal tbh).

The problem seemed to be the driver I had chosen, I switched it to 'Epson Stylus Color 300 Foomatic/stcolor' and did a full reboot and it all worked.

I'm not entirely convinced it is all done as the printer seems to switch itself off occasionally now; something it never used to do when it was local?

Anyways - all is good for now :)

---


---
title: "Cups makes me want to scream"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by decahedron on 2009-09-24
I have a document that must be printed from my laptop.  I have tried all night to get cups working to no avail.  Where is a simple to understand tutorial to set cups up?  Seriously, it cant be this hard.  

I am using Jaunty 9.04 on both laptop and desktop.  

What is the step by step to making it work?  could someone post a cupsd.conf that works?

Thanks[LEFT][/LEFT]

---

### Post by wojox on 2009-09-24
Have you tried setting it up @ [http://127.0.0.1:631/](http://127.0.0.1:631/)

---

### Post by decahedron on 2009-09-24
Here is my cupsd.conf.  Is there another configuration file I may need to edit?



LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
Listen 127.0.0.1:631           # existing loopback Listen
Listen 192.168.0.100:631      # Listen on the LAN interface, Port 631 (IPP)

# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
#BrowseAddress @LOCAL
BrowseAllow all
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Encryption Required
  # Restrict access to the admin pages...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

---

### Post by Whiffle on 2009-09-24
What have you got so far?  Does it give any errors? Is your printer added and not printing, or what?  More details :D

---

### Post by decahedron on 2009-09-26
The printer is connected and works fine.  Cups has the printer added and prints test pages just fine.  However, other computers on the network do not see the printer.  From the add printer dialog box I search for the printer at 192.168.0.100 and 132.168.0.100:631 but the printer is not found.

I have edited my cupsd.conf into oblivion to no avail.  Nothing in the conf file seems to allow the printer to be seen by other computers.  maybe the problem is not cupsd.conf.  I don't know.  

Thanks for listening

---


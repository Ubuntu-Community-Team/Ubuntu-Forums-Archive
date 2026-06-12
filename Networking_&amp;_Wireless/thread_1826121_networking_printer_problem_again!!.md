---
title: "networking printer problem again!!"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by mamboze on 2011-08-16
I'm frustrated (and embarrassed) at having to visit this networked printer issua again, having previously aired the problem on this thread
[http://ubuntuforums.org/showthread.php?t=1799528](http://ubuntuforums.org/showthread.php?t=1799528)

I reinstalled 10.04 on a desktop which has a HP LaserJet 1022 attached and is networked with a laptop also running 10.04. 

I'm now unable to access the printer from the laptop. I'm obviously missing something here, but I can't work out what.

At the moment, the printer is accessible from the desktop to which it is attached. No problem there. And, on the laptop, the printer appears in the System>Administration>Printing dialog but is not accessible. 

I've rung the changes on the various options in Settings and Connect but no joy. 

Any help much appreciated.

---

### Post by mamboze on 2011-08-18
No suggestions?

---

### Post by drdos2006 on 2011-08-18
What do you get when you point your browser to the printer on the desktop IP.

http://<desktop-IP-address>:631

regards

---

### Post by mamboze on 2011-08-19
Thank you for your reply

accessing [http://192.168.1.2:631](http://192.168.1.2:631)  gives CUPS

and 

[http://192.168.1.2:631/printers/](http://192.168.1.2:631/printers/) gives

Showing 2 of 2 printers.
Queue Name 	   Description	   Location	  Make and Model	Status
HP-LaserJet-1022  Hewlett-Packard HP LaserJet 1022  prospero	HP LaserJet 1022 Foomatic/foo2zjs (recommended)	Idle
PSC-1400-series	HP PSC 1400 series	prospero	HP PSC 1400 Series hpijs, 3.10.2	Idle

Sorry about the formating, 2 printers are reported HP-LaserJet-1022 and HP PSC-1400-series

---

### Post by drdos2006 on 2011-08-19
Try connecting from System -> Administration -> Printing.
Server -> Connect -> 192.168.1.2

Also check the /etc/cups/cupsd.conf file.

```

Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic

```


regards

---

### Post by mamboze on 2011-08-19
OK, 

> connecting from System -> Administration -> Printing.
Server -> Connect -> 192.168.1.2

gave

"CUPS server error
there was an error during the CUPS operation
'failed to connect to server' "

cupsd.conf file 

```
LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
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
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
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
      AuthType Default
      Require user @OWNER @SYSTEM
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>

```
Unfortunately, I'm afraid the most of this file doesn't mean very much to me.

---

### Post by drdos2006 on 2011-08-20
[edit]
This is my CUPS configuration file on the Desktop.
[/edit]
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all ...................................
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all...................................
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all...................................
</Location>
/////////////////////////////////////////

I have highlighted that section which I feel is different to your configuration file.
Use your browser to access :-  [http://192.168.1.2:631](http://192.168.1.2:631)
Go to Administration and under Server, Edit Configuration File to change to "all" rather than "@LOCAL".
Save the changes. See if that helps. You may have to reboot the Desktop or restart CUPS.

regards

---

### Post by mamboze on 2011-08-22
I made the changes you suggested to the cupsd.conf file on desktop (192.168.1.2) and the CUPS server error message does NOT appear. 

However I think I've made some progress. I deleted the printer on the laptop (192.168.1.3) and reinstalled it (the LaserJet) Administration>Printing>Add>Network Printer>LPD/LPR Host or Printer and selected the printer. This put the two printers connected to the desktop in the window. But still no connection, printing test page command >>>  HP LaserJet not connected (or similar message).

Thank you drdos2006 for your help, it is much appreciated.

It seems to be extraordinarily difficult in Ubuntu to simply connect to a printer on a network. We're not talking about rocket science here, just a simple network connection. Is it possible to do this in a finite number of steps??

---

### Post by praseodym on 2011-08-23
Maybe [this]("http://ubuntuforums.org/showpost.php?p=11176497&postcount=2") works. Worked here, too.

---

### Post by mamboze on 2011-08-23
Hi praseodym,

Your suggestion worked. But at first I got a 'can't connect to CUPS' (or similar) message from 'cupsctl --remote-printers' on the notebook. So I reinstalled CUPS and rebooted. Success!! The two printers attached to the desktop were available on the network.

Thanks mate, I am grateful for your help. Your advice was spot on.

---


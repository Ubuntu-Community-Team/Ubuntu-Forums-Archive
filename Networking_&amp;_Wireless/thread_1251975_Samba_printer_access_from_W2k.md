---
title: "Samba printer access from W2k"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by tantares on 2009-08-28
Hello, I'm running Samba 1.2.50 on Ubuntu 8.04. The systems shares file folders and a printer queue for Xindows XP and Vista desktops. After initital difficulties with removable disks, I managed to get it all running well. Access is set to everyone.
Now I tried to print from a Windows 2000 system and it does not work. I can open the file folders and open the remote printer, but when I send a print job, I get an access denied error.

What is the difference between XP and W2000? Do they use a different login attempt? Where and how could I log and view the Samba access attempts. It's currently not logged in the smbd or nmbd logs.

Any idea?

---

### Post by dmizer on 2009-08-28
Don't use samba.

Configure your printer shares from System > administration > printing. It will give directions on how to connect to the share in Windows.

---

### Post by tantares on 2009-09-07
Good advice but it does not work with CUPS neither. I cannot manage to install the IPP printer on the W2k system. 
I can connect from that system, with a browser on port 631 to CUPS. But when I try to setup the printer with the URL: [http://printer_host:631/printers/shared_printer](http://printer_host:631/printers/shared_printer) it does not work. The CUPS error log says: cupsdAuthorize: No authentication data provided.

Again with the XP systems it works. So I suspect, their is a problem with the way W2k connects to the remote printer.

---

### Post by dmizer on 2009-09-08
> **tantares said:**
> Good advice but it does not work with CUPS neither. I cannot manage to install the IPP printer on the W2k system. 
I can connect from that system, with a browser on port 631 to CUPS. But when I try to setup the printer with the URL: [http://printer_host:631/printers/shared_printer](http://printer_host:631/printers/shared_printer) it does not work. The CUPS error log says: cupsdAuthorize: No authentication data provided.

Again with the XP systems it works. So I suspect, their is a problem with the way W2k connects to the remote printer.

Please post the contents of /etc/cups/cupsd.conf

As well as the output of:
```
ifconfig
```

---

### Post by tantares on 2009-09-09
> **dmizer said:**
> Please post the contents of /etc/cups/cupsd.conf

As well as the output of:
```
ifconfig
```

Below you find the requested info. Please keep in mind, that the printing works ok from any Windows XP client. So my guess is, that there must be a difference in the way the W2k client connects and authenticates to remote printers
[B]
cupsd.conf[/B]
[I][SIZE="1"]LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  Allow all
  Allow all
  Allow all
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Allow all
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Allow all
  # Allow remote access to the configuration files...
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
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Location /printers>
  AuthType None
  Order Deny,Allow
  Deny From None
  Allow From All
</Location>


**ifconfig**
eth0      Link encap:Ethernet  Hardware Adresse 00:0c:6e:08:2f:90  
          inet Adresse:192.168.0.4  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::20c:6eff:fe08:2f90/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4325 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:4957146 (4.7 MB)  TX bytes:597326 (583.3 KB)
          Interrupt:20 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:3277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3277 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:149744 (146.2 KB)  TX bytes:149744 (146.2 KB)[/SIZE][/I]

---

### Post by dmizer on 2009-09-09
Ok, please post the output of:
```
sudo iptables -L
```

---

### Post by tantares on 2009-09-11
Sorry, I was away for a day. No particular Firewall rules, beside the Samba entries:

[I]
**sudo iptables -L**

[SIZE="2"]Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN
ACCEPT     udp  --  192.168.0.1          anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.0.2          192.168.0.1         tcp dpt:domain
ACCEPT     udp  --  192.168.0.2          192.168.0.1         udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'

Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  192.168.0.0/25       anywhere
ACCEPT     tcp  --  192.168.0.0/25       anywhere            tcp dpt:microsoft-ds
ACCEPT     udp  --  192.168.0.0/25       anywhere            udp dpt:microsoft-ds
ACCEPT     tcp  --  192.168.0.0/25       anywhere            tcp dpts:netbios-ns:netbios-ssn
ACCEPT     udp  --  192.168.0.0/25       anywhere            udp dpts:netbios-ns:netbios-ssn
ACCEPT     tcp  --  192.168.0.0/25       anywhere            tcp dpt:microsoft-ds
ACCEPT     udp  --  192.168.0.0/25       anywhere            udp dpt:microsoft-ds
LSI        all  --  anywhere             anywhere

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

[/I]

---

### Post by dmizer on 2009-09-11
Try disabling your firewall, or allowing port 631. You should be able to print then.

---

### Post by tantares on 2009-09-14
Unfortunately this did not help.  The rule "ACCEPT all -- 192.168.0.0/25 anywhere" does already allow the whole subnet access anyhow, and remember I can print from any other XP machine. Also, please note, that I can connect from W2k to CUPS on 631 using a browser. 

I suspect the problem to be in the implementation of the IPP protocol on W2k.

---

### Post by tantares on 2009-09-14
Today, I made another test by sharing the CUPS PDF Printer. I can install this printer on W2k in contrast to the HP PSC1210 printer. I can also send a print job without error, although I did not find the resulting PDF. However this could be a hint, that the error occurs soemwhere in the handshake and could depend on the printer type (driver)

---

### Post by tantares on 2009-10-30
Still searching for an explanation, what could cause the difference between W2K and XP, when accessing a remote CUPS printer.

):P

---


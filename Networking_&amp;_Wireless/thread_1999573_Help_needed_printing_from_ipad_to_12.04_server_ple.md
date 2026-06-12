---
title: "Help needed printing from ipad to 12.04 server please"
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by MrGrumpyArse on 2012-06-08
[AS THIS IS NOW SOLVED SHOULD YOU BE READING TO HELP WITH YOUR PARTICULAR PROBLEM,THEN PLEASE SEE THE FINAL POST IN THE THREAD AS THIS MAY SAVE YOU TIME :-) ]

Sorry for the long post, I have tried to supply any info that may be relevant - please ask if anything else would be helpful 

HISTORY - 
After running Ubuntu for a couple of years on various pc/laptops I decided to take the plunge and set up a home server running 12.04 64bit server edition.
So far things have gone well and with the aid of google and many tutorials the server is set up as follows -

SETUP- 
Headless server with 12.04 installed to 160GB disk
Created static ip
Additional 1tb sata disk added and 3x user named folders shared over local network (password protected / syncs password to user accounts)
File sharing via Samba to Ubuntu desktops x2 (12.04 gnome shell)and to windows Vista and Windows 7
Shared printer on server shared via cups to Ubuntu Desktops and Samba to Windows machines.(all tested and working)

THE PROBLEM-
No matter what I attempt I cannot get the printer to share with iphone or ipad.  I have read through and implemented numerous tutorials but to no avail. 

CURRENT STATE -
Following this thread -
[http://ubuntuforums.org/showthread.php?t=1976277](http://ubuntuforums.org/showthread.php?t=1976277) 
I have downloaded and installed the .deb file (airprint-daemon_1.0-1-1_all.deb).  During installation all went well untill the import error shown towards the end -

 ```
mark@grumpyserver:~$ sudo dpkg -i airprint-daemon_1.0-1-1_all.deb 
[sudo] password for mark: 
Selecting previously unselected package airprint-daemon.
(Reading database ... 97233 files and directories currently installed.)
Unpacking airprint-daemon (from airprint-daemon_1.0-1-1_all.deb) ...
Setting up airprint-daemon (1.0-1-1) ...
Configuring CUPS
Running post-install tasks...
 Adding system startup for /etc/init.d/airprint-daemon ...
   /etc/rc0.d/K20airprint-daemon -> ../init.d/airprint-daemon
   /etc/rc1.d/K20airprint-daemon -> ../init.d/airprint-daemon
   /etc/rc6.d/K20airprint-daemon -> ../init.d/airprint-daemon
   /etc/rc2.d/S20airprint-daemon -> ../init.d/airprint-daemon
   /etc/rc3.d/S20airprint-daemon -> ../init.d/airprint-daemon
   /etc/rc4.d/S20airprint-daemon -> ../init.d/airprint-daemon
   /etc/rc5.d/S20airprint-daemon -> ../init.d/airprint-daemon
Starting AirPrint Daemon...
[LIST=1]
[*]Traceback (most recent call last):
[*]  File "/usr/sbin/airprint-daemon", line 10, in <module>
[*]    import gnomevfs
[*]ImportError: No module named gnomevfs
[/LIST][COLOR="Red"][/COLOR]
Restarting CUPS
cups stop/waiting
cups start/running, process 1923
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
mark@grumpyserver:~$ sudo reboot

Broadcast message from mark@grumpyserver
	(/dev/pts/0) at 12:58 ...

```

After a quick google for info i have edited the file mentioned (/usr/sbin/airprint-daemon) and changed the line that read "import gnomevfs" so it now reads "import gvfs" which seems to have removed the error message.

After restarting both cups and the avahi daemon and rebooting the server the apple devices still show "no air-print printer found" and there is no sign of the printer in the avahi-discovery window. 

I have attached some screen shots which may be relevant and my full /etc/cups/cupsd.conf is hopefully shown below.....

Any advice or help would be much appreciated 

```
LogLevel debug
MaxLogSize 1m
SystemGroup lpadmin
ServerAlias *
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols cups ldap
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
WebInterface Yes
<Location />
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
<Policy authenticated>
  JobPrivateAccess default
  JobPrivateValues default
  SubscriptionPrivateAccess default
  SubscriptionPrivateValues default
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job Cancel-My-Jobs Close-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After Cancel-Jobs CUPS-Accept-Jobs CUPS-Reject-Jobs>
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
ServerAlias *
```

---

### Post by lhowaf on 2012-06-08
You may have already solved this but [here]("https://lists.ubuntu.com/archives/ubuntu-devel/2011-June/033611.html") is a reference for airprint on Natty and Oneiric.
I only have a 10.04 server but I used [this]("http://confoundedtech.blogspot.com/2011/05/ios-airprint-without-ture-airprint.html") and [this]("http://www.sharedknowhow.com/2010/11/share-printer-with-airprint-under-linuxubuntu-10-04/").

---

### Post by MrGrumpyArse on 2012-06-08
lhowaf, thanks for the reply - The links you left were in fact some (or very similar) to the ones I had originally been working through, unsuccessfully that is....

I have reversed much of what was done by following those or similar links and tried downloading the .deb file and taking that approach.

Unfortunately still no success 

Any further help or suggestions welcomed from anyone, as this one (for the moment!) has the better of me.

Thanks 

Mark

---

### Post by MrGrumpyArse on 2012-06-14
UPDATE -

Ok its several days on from my original post and I still haven`t got this working, I have however made some progress I believe.

CURRENT POSITION -

I have un-installed the .deb file(airprint-daemon_1.0-1-1_all.deb), that I had previously used, and reverted to creating a .service file using the python script provided here - 

[https://github.com/tjfontaine/airprint-generate](https://github.com/tjfontaine/airprint-generate)

Creating the .service file with the script went fine with no errors and the resultant  "AirPrint-HP_OfficeJet_6100_Series.service" file now resides in /etc/avahi/services/.

Now reverting to service file method, didnt I believe, fundamentally change anything, however on discovering via a forum post, that if I installed "avahi-utils" on the server I could run what appears to be a text version of the "Avahi Discovery" browser directly on the server using the following command.

```
avahi-browse -a
```

This produced something interesting (see attached screenshot "avahi-browse -a")  
It appears that avahi knows the printer is there and is listing it twice (ipv4 /ipv6) and there is also another version of the same printer listed "eth0 IPv4 HP OfficeJet 6100 Series @ grumpyserver"

Spurred on by this progress I ran the "Avahi Discovery" browser from aN Ubuntu 12.04 pc which is wired to the network, as all previous work was done on a 12.04 laptop over wireless.

Again an interesting result,(see attached screenshot "avahi discovery wired") the wired pc shows a similar output to the "avahi-browse -a" command run on the server.  The printer is again listed on ipv4/ipv6 along with the same second listing of the printer under the name  "eth0 IPv4 HP OfficeJet 6100 Series @ grumpyserver".

So it would appear to me that the avahi daemon is broadcasting the info in the .service file to produce -

```
eth0 IPv4 AirPrint HP_OfficeJet_6100_Series @ grumpyserver 

```

and broadcasting the second listing -

```
eth0 IPv4 HP OfficeJet 6100 Series @ grumpyserver
```
which presumably it is picking up directly from cups (i think thats possible on 12.04)

Either way I can have a look at that point later, the issue appears to be that any information broadcast is only visible over Ethernet and not over wireless?

If anybody has anything to contribute that may help in anyway it would be much appreciated 

Mark

---

### Post by MrGrumpyArse on 2012-06-14
Some further progress made -

This appears to be an issue with how my network is set up, let me explain.....

My "Netgear DGN1000sp ADSL modem /router is positioned upstairs in the "back bedroom" of my house, along with my server and desktop pc.  Both are wired directly into the modem/router. 

 To enable wireless access to the network from anywhere in the house the "wireless" is turned OFF on that router and a second router (Netgear WNR2000 v2)is located more centrally in the house and is being used as an access point. It is wired to the main modem/router.  
This set up has been used for a year or two now with no noticeable problems........

As a result of the progress made in my previous post I decided to turn on the wireless on the main ADSL modem/router and connect my laptop to it directly (but still wireless, if that makes sense).

When the laptop is connected to the network via the  Netgear DGN1000sp ADSL modem/router, the Avahi Discovery browser now shows the printer (same result as when connected by ethernet) so presumably will be available to an apple device connected in the same way.

Ideally I would like know how to make the "Avahi broadcasts" be visible to devices connected to the network via the "Netgear WNR2000 v2 access point" as currently all wireless devices connect to my network this way.

As I read someone say in one of the many articles/posts I have read to get this far, "I really am at the limits of my knowledge here".

Therefore If anyone can help in anyway, even perhaps give me the correct terminology for what I am trying to achieve it would be appreciated

Mark

---

### Post by MrGrumpyArse on 2012-06-15
Ok this problem has finally been resolved  :)

Following on from yesterday, I tried connecting my laptop to the Netgear WNR2000 v2, which is basically acting as the wireless access point for the house, via Ethernet.

Again the Avahi browser showed the two versions of the same printer, so back to wireless through the same router/access point, and as previously the printer disappears (along with any trace of the server) from the Avahi Discovery browser.

A little more research alludes to this being a "multicast" issue, where if I understand correctly, the router/access point is treating the wired network and the WiFi network as 2 separate networks.

Into the router config utility and no setting referring to "multicast" to be found.  

Back to google, and a search for firmware updates reveals in the paperwork a reference to "multicast".  A quick download and then flash the new firmware onto the router.

Instantly everything is working!!!

The printer is now showing (albeit twice) in the Avahi Discovery browser, and more importantly is visible from the Ipad /Iphone.  A quick test print reveals all is well.

So finally to tidy up, I removed the .service file which I had previously added to /etc/avahi/services/ which successfully removed the second entry from the printers list, leaving only the one which is presumably being detected directly from cups by the Avahi daemon.

So it would appear had it not being for my physical network configuration, and an out of date firmware version on my router, printing from the iphone/ipad (which incidentally belong to my girlfriend, its android and Linux all the way for me )would have worked pretty much out of the box on Ubuntu 12.04. Just a case of adding a printer via cups, selecting the relevant share options, and "viola" everything should work...........

Ah well such is life! anyway I learned much more this way :lolflag:

---


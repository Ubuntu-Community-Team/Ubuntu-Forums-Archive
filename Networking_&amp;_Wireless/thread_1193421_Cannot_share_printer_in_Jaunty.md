---
title: "Cannot share printer in Jaunty"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by fondle-em on 2009-06-21
Since the only response I got asking about this in the Hardware support forum was silence, I'll try asking in *here* before I go and roll back several computers to a version of Ubuntu that actually *works as it's supposed to.*

To begin, no, I am not running a firewall.

My Laserjet 4L printer is attached to a computer running 9.04, which is SUPPOSED to share it to all computers on my local network. However, it doesn't. Even though in the Printer Properties the checkboxes for Enabled, Accepting Jobs and Shared are all selected, the printer isn't actually shared - there's an italicised message next to the checkboxes which reads...

"[I]Not published
See Server Settings[/I]"

So, fair enough, let's do that, then. I'll just go to Settings under the Server menu in Printer Configuration, where I'll see that "Publish shared printers connected to this system" is checked. I'd think, then, that this means that the printer is actually shared. I'd be wrong. I have to uncheck that box, and then check it again. At that point, the "not published" message goes away.  For a while, this meant that the printer was actually being temporarily shared.  However, after the last CUPS update, it doesn't even mean that any more and **sharing doesn't work at all.**  And if I close the Printing control panel, reopen it, and then reopen the Printer Properties window, it's back to "Not Published - See Server Settings".   The server is set to "Publish Shared Printers Connected To This System".
 
This is a new "feature" in 9.04.   Printer sharing was flawless in Intrepid and Hardy.  What, if anything, am I doing wrong here?

---

### Post by fondle-em on 2009-06-26
It would be greatly appreciated if someone could help me in any way.

---

### Post by hipsterical on 2009-06-27
i am facing the same trouble. still clueless, it would be nice if some guru shows us the Light.

---

### Post by LashSilence83 on 2009-06-27
I too share this problem on a 9.04 system. Everything was fine until recently when (I'm assuming) an update to cups changed this. When I try to delete and add the printer again on another box on the network, it sees the printer and knows what ip it's on, but when I try to verify the share, it says it's not accessible.

---

### Post by cwalke32477 on 2009-06-27
I too am having issues trying to share my printer.
When I check the printer properties, it says the printer is not published, see server settings.
Where do I go to view these settings?

---

### Post by linuxmagick on 2009-06-27
You should be able to view your CUPS server settings by opening up a browser and visiting localhost:631.  You can publish/unpublish the printer from the Printers tab here.

---

### Post by LashSilence83 on 2009-06-27
I've been pulling my hair out all day long trying to deal with this issue. I've tried reinstalling cups 1.3.9, rolling it back a version, and even forward two versions and it still won't share the printer. I've been searching for several hours and haven't found any information that would help me fix this. I'm not terribly knowledgeable with things concerning CUPS, but if anyone knows what logs to look at or how to further diagnose this problem, please help!

---

### Post by LashSilence83 on 2009-06-27
Upon reading a forum I saw a suggestion for reinstalling libpng3 so (after installing cups 1.3.10) I did that and restarted cups and somehow now I can print from the network again. Whats annoying is that on the print server, it still says "not published, see server settings". The other strange behavior is that on any of the print clients if I go into the printer config and try to right click on the printer icon to get into the properties, it causes xorg to use 100% cpu, thus hanging up the whole system. This may just be MY problem, but I just thought I would mention it.

---

### Post by fondle-em on 2009-06-29
> **LashSilence83 said:**
> Upon reading a forum I saw a suggestion for reinstalling libpng3 so (after installing cups 1.3.10) I did that and restarted cups and somehow now I can print from the network again. Whats annoying is that on the print server, it still says "not published, see server settings". The other strange behavior is that on any of the print clients if I go into the printer config and try to right click on the printer icon to get into the properties, it causes xorg to use 100% cpu, thus hanging up the whole system. This may just be MY problem, but I just thought I would mention it.

My libpng3 wasn't installed - however, libpng12 is.  I'll see if installing libpng3 makes any difference.

---

### Post by LashSilence83 on 2009-06-29
Well, I finally gave up and set up an old computer running debian as a print server using cups 1.3.8 and everything works fine now. It's hard for me to know if this is a bug strictly in cups or if it's an issue with system-config-printer or if out of ignorance I did something to break my system. Really the only changes that were made between the time it was working and the time it stopped were the official updates were being ran once a week. I know that's terribly vague, but from some of the info I've been reading on forums, lots of folks have broken printing and print sharing in many different ways. Some of them you wouldn't think were related to printing at all! Still, I wonder if the issue on one of my laptops with the printer properties hanging the system is related to this at all...

---

### Post by LashSilence83 on 2009-06-29
well, I just checked the updates available and I notice there are some cups related ones and also some system-config-printer ones as well. Perhaps these will fix the issues everyone here is having. Here's hoping...

---

### Post by raph666 on 2009-07-08
I have the same problem with a HP Laserjet 1020.
> **linuxmagick said:**
> You should be able to view your CUPS server settings by opening up a browser and visiting localhost:631.  You can publish/unpublish the printer from the Printers tab here.
Original post states that the printer is actually published in the server settings. Logically, there shouldn't be a difference between the Printing administration tool and the web control panel but I tried anyway.

The printer state properties are all checked:
Enabled
Accepting jobs
Shared

However, like OP, I have the "Not published See Server Settings" message even though the "Publish shared printers connected to this system" server setting is checked. When I uncheck/check and click OK, the message disappear in my printer properties but if I exit and go back to the Printing administration tool the message is displayed again. Other systems on the network (using mac os x and windows vista) never see the printer.

I certainly hope *I* did something wrong somewhere and that can be fixed. Thanks

---

### Post by Panoshots on 2009-07-10
I am having the same problem with a network printer (HP Photosmart Pro B9180). I am new to Linux, having just installed Jaunty in a dual boot configuration with XP. When I go to localhost:631 the printer has the message "/usr/lib/cups/filter/foomatic-rip failed". When I try to print a document it prints an error message instead "**** Unable to open the initial device, quitting" neither of which means very much to me. Any suggestions?

---

### Post by fondle-em on 2009-07-11
> **fondle-em said:**
> My libpng3 wasn't installed - however, libpng12 is.  I'll see if installing libpng3 makes any difference.

Kinda late in reporting back but no, it didn't make any difference.  This is something of a nasty little issue, it seems.

---

### Post by quaternion on 2009-07-17
I am not a printer expert by an measure but I can share both a ML-2010 and a HP Color laser jet 2605 dn connected via usb on Jaunty with both another Ubuntu machine and windows XP.  If you would like to know anything about my system just ask.  

I had an "unable to add the 2605 as a shared printer" issue when it was connected to the network and I was trying to get my Jaunty machine to share the network printer and act as a gateway... which you think would work the same if everyone followed the rules but no it didn't work out.  But everything is fine locally as I mentioned.

---

### Post by ghmason on 2009-07-23
While I'm not quite a complete newbie, this issue is kicking my butt.  I agree with what was stated above that this is a problem.  I had this working in Intrepid, that is sharing the printer that is connected to my desktop, with other vista notebooks over my home wireless network.  Upgrade to jaunty and no-joy.  I'm thinking this should be easy and I am doing something wrong, but I have followed all the "how-to's" I can find and still can't get it to work.  I can however print from this notebook booted into jaunty to my desktop where the printer is connected when it is booted to jaunty.  My wife and daughters with their vista notebooks cannot.  I am willing to start over completely on my desktop in an effort to get rid of vista all together - any help would be greatly appreciated.  Thanks in advance, George
*************Edit*****************
Ok, sorry for all of the above.  In diving back into Samba and editing the smb.conf file, I have the functionality that I was after. (see smb.conf below) I want to get rid of Vista on my Desktop and just run Jaunty.  My wife and my daughters (and I) however, have vista notebooks and occasionally need to print to the color laser that is connected to the Desktop. Well all that as well as some limited file sharing now work and everything looks good for dumping vista off my desktop.  The ironic thing is that with my dual boot notebook, when I am logged into jaunty, I cannot see (nautilus), hence file share with the Desktop.  I can print as that goes via ipp I believe.  I can also ping the samba share (DESKTOP) from the jaunty client but cannot browse to the shared folder on the Desktop or copy any files back and forth  I have been chasing the solution to this for most of the day and the best I can tell it is a bug in nautilus.  I know my smb.conf will probably raise some eyebrows as well - but it works for my purposes.  Thanks, George

[global]
workgroup = WORKGROUP 
netbios name = DESKTOP 
security = share 
printcap name = cups 
disable spoolss = Yes 
client lanman auth = yes

[printers]
comment = All Printers 
path = /var/spool/samba 
guest ok = Yes 
printable = Yes 
use client driver = Yes 
browseable = No

[data]
comment = data
path = /home/george/Downloads
read only = No
guest ok = Yes

---

### Post by peterroots on 2009-09-30
You can, but for all the good it does you may as well poke yourself in the eye!*** Comment was in response to what seemed like the last post (when I first found this thread) saying you can just share published printers. Only found later there were a whole load of posts following that comment - oops***

From cups 1.3.9 at localhost:631 on jaunty 9.04 you can
select a printer and click on 'publish printer' and it will tell you it is published but an ubuntu machine can not find it from the cups web interface 'Administration>find new printer' nor can it print to it if you specify an address using http:// ipp:// or socket:// and the ip of the host and ports 9100 or 631 with and without a /ipp before the port and you try with no port at all
Zilch!

on the host computer you can then try the cups admin page and discover that, despite the fact your printer says it is published, your server is not publishing any printer! So you tick 'shared published printers....' and click 'change settings'.  At this point the cups server restarts and you try to print from a computer on the network - It does not detect any printers so you try http: ipp: and socket again.  You try from system setting>printer configuration (again)
You try it on the host with [http://localhhost](http://localhhost) etc etc etc
Zilch (again)

You think 'why did it used to work on older versions of Kubuntu and Ubuntu?' so you try the forums

Does anyone have the faintest idea what is going on here?  I am baffled having exhausted everything I can think of?

Just after writing the above (ever so slightly facetious comments) I thought 'why don't I unplug everything and take the printer to the other compter?'
So I did - Ubuntu8.04 running cups 1.3.7
localhost:361 Adminsitration>share published....  and 'change settings'
all the published printer are available on the network to my Kubuntu Jaunty setup.
As leaving the printer on the floor under my wife's desk is not really a viable option I am still looking for a solution (the jaunty repositories seem not to have an older version of cups I can try)

---

### Post by bigwolf on 2009-10-16
Have had this issue too.  In my case it could be solved by editing /etc/cups/cupsd.conf as I show below.  I believe the main culpurit was the BrowseAddress @LOCAL setting.  Here is what I have now for the top part of the configuration file.  Since my local network is 172.16.0.0 I have that as my browse address.  You can of course supply 0.0.0.0 if you like which will place no restriction (although not recommended for obvious reasons).  I also tidied up the <Location /> configuration settings, you may want to do the same.  Seems like the GUI configuration tools place too many "Allow all" statements in there.

---snip---

```
LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress 172.16.0.0
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow all
</Location>

```---snip---

After making the changes restart the cups daemon by typing

sudo /etc/init.d cups restart

---

### Post by DantePasquale on 2009-10-22
Here's what worked for me:

```
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
**[COLOR="DarkRed"]LogLevel debug[/COLOR]**

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
#Listen localhost:631
**[COLOR="DarkRed"]Port 631[/COLOR]**
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
**[INDENT]Browsing On[/INDENT]**
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  **[COLOR="DarkRed"]Allow @LOCAL[/COLOR]**
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
```

---

### Post by ASchweitzer on 2009-11-13
well, for future reference, if anyone still has problems:

I shared the printer through the GUI, and enabled remote administration. This changed the config file /etc/cups/cupsd.conf as in the above post. I suppose you could manually change localhost:631 to port 631 if you don't want to use the gui.

I then pulled up the remote.machine:631 interface in firefox, and made sure the printer was published.

At this point, I was still unable to verify the printer through my local cups GUI (was still getting "print share not accessible").

I copied the printer UID out of the cups web interface and added the printer by UID in the cups interface. This worked, and I was then asked to specify a driver.

Hope this helps somebody.

---

### Post by peterroots on 2009-11-25
I recently upgraded to karmic Kubuntu
Still could not share my printer and during the upgrade my printer had been unshared and my cups server no longer was set to publish shared printers.
After activating these options again (tried both in system settings>printer configuration and via localhost:631) but still no printer share.
As I had been fighting samba shares for the last couple of days - stubborn ufw would not let samba through the firewall - I thought, hey let me try that printer again.
Turn firewall off (gufw) printer seen on network!
Turn firewall on and add a rule in gufw - allow 631 from xxx.xxx.xxx.xxx/24 no printer
try various things, forgot what, no printer. allow anything to anything from xxx.xxx.xxx.xxx/24 does work though
tried, from command line, sudo ufw allow CUPS this also works but shows up in gufw that I am allowing access to cups from anywhere (?internet inculded)
Tried to restrict cups access to local network but could not use CUPS on gufw or add a network range to CUPS using ufw

As both the cups web interface and printer configuration have settings to publish printer with an option to publish to internet i would have thought they would be modifying the firewall rules. silly me.

For me this has solved the problem, it may help others or may not but worth a quick try

---

### Post by J.G. on 2011-10-15
I had the same trouble.  I could ping the printer remotely etc.   Don't ask me why but when I decided to change the workgroup name on both the remote machine and the desktop to which the printer was connected, all worked like a breeze....




> **fondle-em said:**
> Since the only response I got asking about this in the Hardware support forum was silence, I'll try asking in *here* before I go and roll back several computers to a version of Ubuntu that actually *works as it's supposed to.*

To begin, no, I am not running a firewall.

My Laserjet 4L printer is attached to a computer running 9.04, which is SUPPOSED to share it to all computers on my local network. However, it doesn't. Even though in the Printer Properties the checkboxes for Enabled, Accepting Jobs and Shared are all selected, the printer isn't actually shared - there's an italicised message next to the checkboxes which reads...

"[I]Not published
See Server Settings[/I]"

So, fair enough, let's do that, then. I'll just go to Settings under the Server menu in Printer Configuration, where I'll see that "Publish shared printers connected to this system" is checked. I'd think, then, that this means that the printer is actually shared. I'd be wrong. I have to uncheck that box, and then check it again. At that point, the "not published" message goes away.  For a while, this meant that the printer was actually being temporarily shared.  However, after the last CUPS update, it doesn't even mean that any more and **sharing doesn't work at all.**  And if I close the Printing control panel, reopen it, and then reopen the Printer Properties window, it's back to "Not Published - See Server Settings".   The server is set to "Publish Shared Printers Connected To This System".
 
This is a new "feature" in 9.04.   Printer sharing was flawless in Intrepid and Hardy.  What, if anything, am I doing wrong here?

---


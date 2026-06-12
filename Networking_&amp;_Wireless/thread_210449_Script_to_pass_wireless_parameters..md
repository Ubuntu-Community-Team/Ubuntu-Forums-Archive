---
title: "Script to pass wireless parameters."
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by wjc on 2006-07-06
My wireless card works fine using the RT61 linux drivers.  The only problem is that I have to assign the SSID, WPA key, etc... everytime my machine reboots.  So to make life easier, I tried to create a script and I placed it in the /etc/init.d/ folder. But when I try to run the script, it won't work.  I believe it's a permissions issue.  Afer I created the script I ran the following commond: sudo chmod 755 /etc/init.d/my-script

Here is what is in my script file:
#!/bin/bash
# my wireless card script

ifconfig ra0 inet up
iwpriv ra0 set NetworkType=Infra
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwpriv ra0 set SSID=mySSID
iwpriv ra0 set WPAPSK=myPassword
iwpriv ra0 set SSID=mySSID
dhclient ra0

Any ideas on why this won't work?  Thanks.

---

### Post by mpvano on 2006-07-06
That's usually not the best way to run a script like this.

If you want to configure your network manually, you should use the facilities of /etc/network/interfaces to control the process.

try:

man interfaces

for complete details.

Basically this file is used to decide what to do for each interface at all of the times when networking is started or stopped. It's used by the "ifup" and "ifdown" commands that are called at startup, sleep, resume, run level changes, etc by other scripts.

You can put all your special commands into paragraphs of this file associated with each interface There are a number of builtin statements to control DHCP and static addressing, but you can also put arbitrary commands into the paragraphs to be run before or after the interface is started.

This works very well, but don't try to mix it with other network control panels.

I use an elaborate set of these files that get swapped in to change networking profiles. I've given up on the mystery-meat GUI configurators that don't seem to be documented at all!

hope this gets you started!

Mario

P.S. FYI, however, startup scripts are a little more complicated than they seem. Ubuntu uses a variation of System V init scripts. Startup scripts run in a special environment. It's not enough to just put them into init.d. You need to make links that start/stop them as required and in the correct sequence in each of the "rc.n" directories in /etc. There's one for each runlevel and they get called several times at startup and shutdown and at other times.  Look at the man pages for "start-stop-daemon" and "update-rc.d" for more info....
mv

---


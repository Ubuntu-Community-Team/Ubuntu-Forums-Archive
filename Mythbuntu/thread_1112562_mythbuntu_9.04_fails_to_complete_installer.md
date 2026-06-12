---
title: "mythbuntu 9.04 fails to complete installer"
date: 2009-03-31
forum: Mythbuntu
---

### Post by cuervo73 on 2009-03-31
Trying to install CD:  mythbuntu-9.04-beta-desktop-i386.iso

It gets stuck at the screen titled, "Master Backend Connection Information".

I am trying to build this box as a frontend-only.  The backend runs on another box.  It has MythDora 10.21 running successfully for the last 2 months.  That box is up and running <mythbackend> when I try to "Test Connection".  But, that consistently fails with error message:  Connection Results: Failed

I have tried both: 
 
1) the default 4 settings of: localhost/mythconverg/mythtv/default-pwd
2) the true values of 192.168.1.4/mythconverg/mythtv/correct-pwd

I cannot proceed and try to fix this brokenness later, because the <Forward> button is inactive, presumably until I successfully <Test Connection>

No remote connection is ever going to be possible until the network is enabled first.  I have not seen any Network Setup screen up to this current screen.

Even if I go over to an shell (<CTRL><ALT><F2>) and setup network via ifconfig/route-add-def-gw, the Test Connection still fails.

Was this even tested by Ubuntu?  separate BE/FE boxes?

---

### Post by nickrout on 2009-03-31
from the console can you ping 192.168.1.4 ?

usually the network is set up automatically when the liveCD boots to the desktop. Are you using dhcp?

Perhaps you should be using network-manager on the desktop to set up your network?

Anyway, ping is the first thing to do.

Also look on the backend logs. Do they show an error? 

Hard to tell at this stage whether it is a network error or a mysql error.

Can other frontends connect? Is the backend listening on 192.168.1.4? can you telnet 192.168.1.4 3306  (ie mysql's port)?

Have you plugged in the network cable (but maybe you are not as prone to silliness as me!)

---

### Post by cuervo73 on 2009-04-01
> **nickrout said:**
> from the console can you ping 192.168.1.4 ?

>>>  yes..  192.168.1.4 is Mythbackend box.  I pinged it several times

usually the network is set up automatically when the liveCD boots to the desktop. Are you using dhcp?

>>> I need help with INSTALLATION, please

>>>  I am NOT using a LiveCD..  I am INSTALLING mythbuntu to HDD.
>>>  Not using DHCP; static addresses all around.  Besides, no networking setup screen has yet appeared, so I have to go to a console tty and setup networking manually.

Perhaps you should be using network-manager on the desktop to set up your network?

>>> Uhh, NetworkManager usually runs AFTER installation.  I am talking about an installation problem which PRECLUDES the completion of the installation of M/B.  

Anyway, ping is the first thing to do.

>>>  I know that.. I pinged 192.168.1.4 just after I MANUALLY setup networking via:
   ifconfig eth0 192.168.1.9 netmask 255.255.255.0 up
   route add default gw 192.168.1.1

>>> Why is the mythbuntu installer asking for mythtv settings before it even finishes loading Ubuntu? or before setting up networking?  

>>>  When I installed MythDora a few weeks ago on the backend box, it totally installed Fedora 10, and only THEN started asking setup questions for MythTV.  

Also look on the backend logs. Do they show an error? 

>>>  not checked backend logs yet.. will check now and report back..

Hard to tell at this stage whether it is a network error or a mysql error.

>>>>  Maybe you should re-read my original posting, and see where I currently am stuck.

Can other frontends connect? Is the backend listening on 192.168.1.4? can you telnet 192.168.1.4 3306  (ie mysql's port)?

Have you plugged in the network cable (but maybe you are not as prone to silliness as me!)

>>> no other frontends; backend is running; I ran the following commands in a shell on the mythbackend before trying to "Test Connection" on this install:

>>>    service mythbackend stop
>>>    mythfilldatabase
>>>    service mythbackend start

>>> all commands completed successfully.

>>>  Yes, I telnetted port 3306 on 192.168.1.4 and mysql was running.

>>>  Yes, network cable is properly inserted into the NIC and there is connectivity to the rest of the network, including 192.168.1.4


>>>  I'll ask my question again, "Has anyone associated with Mythbuntu development tried to do an "install to HDD" and "frontend only" with mythbuntu 9.04 beta?  It seems not.

---

### Post by cuervo73 on 2009-04-01
OK, checked the logfile: /var/log/mythtv/mythbackend.log on the backend machine 192.168.1.4.

I ran a live tail on that file:  tail -f /var/log/mythtv/mythbackend.log

Then, I reran the <Test Connection> on the mythbuntu installer screen.. it fails again as before, and there is nothing new in the logtail from mythbackend.log

It is as if the frontend is not communicating with the backend when I click on that text widget <Test Connection>.

---

### Post by nickrout on 2009-04-01
Re the board colours today some kind of sick April fools joke? Hard luck, its 2 april now!

You usually install from a live cd, if you aren't using a live cd, are you using the alternative install cd or something?

---

### Post by superm1 on 2009-04-01
I'm not sure the circumstances that are causing you to not be able to contact your backend, but I've committed a change that makes the check optional.  You can grab the latest daily build at
[http://cdimages.ubuntu.com/mythbuntu](http://cdimages.ubuntu.com/mythbuntu)

and install from that.

---


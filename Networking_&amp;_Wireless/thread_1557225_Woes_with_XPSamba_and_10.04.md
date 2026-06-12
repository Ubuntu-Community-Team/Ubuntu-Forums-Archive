---
title: "Woes with XP/Samba and 10.04"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by alano999@att.net on 2010-08-20
Ever since my upgrade to 10.04 I no longer have Samba shares to my WinXP system(s).  I have searched the forums high and low and for the life of me cant figure out what I am doing wrong.  I am not able to see my XP system from Ubuntu, nor see my Ubuntu system from XP.
Attached here is a copy of my smb.conf.  

Thanks in advance to any/all that are able to help!
Best Regards Alan

---

### Post by CharlesA on 2010-08-20
smb.conf looks fine.

Are you blocking ports?

You need to have TCP ports 139 and 445 open and UDP ports 137 and 138 open.

---

### Post by Iowan on 2010-08-20
Is networking functioning? (Can you ping from each machine to the other?)

---

### Post by alano999@att.net on 2010-08-20
I am able to use both systems to do web browing, etc.  But I just tried to ping each system from the other and am NOT able to.

Also, I believe TCP 139 is open (issued a netstat -an |grep 139).  The other tcp and both UDP ports do not appear to be open.  Then again I'm not sure if I am testing this properly nor how to open these ports.
Thanks!
Alan

---

### Post by CharlesA on 2010-08-20
Try running this please:

```
netstat -ln
```

Mine looks like this:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
udp        0      0 192.168.1.2:137         0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 192.168.1.2:138         0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*

```

---

### Post by alano999@att.net on 2010-08-20
CharlesA,
I ran netstat -ln and do indeed get both tcp and udp ports shown as listening/open.
now for the life of me I dont understand why I cant ping from system to system.
I have both the XP and Ubuntu systems 100bT hardwired into the **same switch** with addresses of 192.168.1.100 and 192.168.1.102 respectively.
I checked the WinXP firewall and all four port numbers are already 'SMB' and/or Netbios assigned, so they are enabled and functional.
Ugh!
Thank you all for the prompt replies!
Alan

---

### Post by Iowan on 2010-08-20
> **alano999@att.net said:**
> But I just tried to ping each system from the other and am NOT able to.
Pinging by name or IP address (or both)? 
What lies between the two machines - hub/switch, router, ...?
Are the machines in the same subnet?

---

### Post by alano999@att.net on 2010-08-20
I have tried using both IP addresses and names to attempt the ping.  Neither one works.
The only piece of network equipment between the two systems is a Airlink switch.  No hub.  
Alan

---

### Post by CharlesA on 2010-08-20
What does it say when you try to ping?

Please post ipconfig /all (windows) and ifconfig eth0 (linux).

---

### Post by alano999@att.net on 2010-08-20
The ICMP replies from Linux are "Destination Host Unreachable".
Those from the XP system are "Request Timed Out"

Not too verbose.....

Alan

---

### Post by CharlesA on 2010-08-20
Yah, post the ipconfig/ifconfig and we'll see if they are correct.

---

### Post by chrisinspace on 2010-08-20
Did you make sure the Windows Firewall is off in the Control Panel in XP?  I have seen so many networking problems as a result of that half-baked firewall.  If you are using it...don't.  Disable it and install something free like ZoneAlarm.

---

### Post by alano999@att.net on 2010-08-20
I do not have the WinXP firewall off, but did verify the ports for tcp and udp are open and functional.
Strange, but i am now able to ping from my WinXP system to the Ubuntu address.  However I still cant ping from 10.04 back to the WinXP system.  This is so strange as they are both only connected via a switch and are on the same 192.168.1.10x network!  Although I can ping the Linux system, I still cant use the 'Network Neighborhood' to browse the Ubuntu shares.  It keeps telling me the network path is not found...

---

### Post by chrisinspace on 2010-08-20
If you haven't already, you should disable it completely and see if things work. 

When Windows Firewall was first introduced, I tried to configure it to allow specific kinds of traffic.  Everything would look right and it would still screw things up.  There are a few good free options out there to replace the built-in firewall.  I download my freeware from [FileHippo.com]("http://www.filehippo.com").  There are several firewalls there to choose from.

---

### Post by alano999@att.net on 2010-08-20
Okay, I did two things so I'm not sure which change did what.  First thing was to disable the Winxp firewall.  The 2nd thing is I found a "personal file sharing" option in 10.04.  I enabled it.

I am now about to browse the Ubuntu 10.04 system from WinXP just fine.
From 10.04 Network File Manager, I now have an icon for the Win system.  It however does NOT let me connect.  The nasty error message 10.04 keeps giving me (when trying to browse winxp system) is "Unable to Mount Location"  "Unable to retrieve share list from server".

Hopefully this narrows things down a bit (hopefully?)....

Alan

---

### Post by theozzlives on 2010-08-20
You need to edit the /etc/hosts file. An example follows:
```
127.0.0.1	localhost

127.0.0.1   ozzie-laptop.ipserver.com   ozzie-laptop
192.168.1.4     ozzie-laptop
192.168.1.6     ozzie-tower
192.168.1.3     windows-7
192.168.1.2	mike-desktop
192.168.1.5	april-laptop
192.168.1.8	windows-xp
```

---


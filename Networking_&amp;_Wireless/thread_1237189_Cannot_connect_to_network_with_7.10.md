---
title: "Cannot connect to network with 7.10"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by nandinibhaduri on 2009-08-11
I am an absolute beginer. Had someone load 7.10 in my Lenovo laptop. But I cannot seem to be able to connect to my office network.

Followed the steps from [http://lapserv.maths.cam.ac.uk/docs/ubuntu-710.html](http://lapserv.maths.cam.ac.uk/docs/ubuntu-710.html).

But nothing happened.

I would like to upgrade to 9.10 - but without the internet connection I am unable to do so.

---

### Post by zkriesse on 2009-08-11
you could download the Ubuntu desktop cd...i assume you are using a different pc to post?

---

### Post by nandinibhaduri on 2009-08-11
More information, if that helps.

nandini@nandini-home-lp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:EC:0E:EF:44  
          inet6 addr: fe80::21e:ecff:fe0e:ef44/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37677 (36.7 KB)  TX bytes:492 (492.0 b)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22944 (22.4 KB)  TX bytes:22944 (22.4 KB)


Another thing - Why cant I see the wireless connection thing in the Connection Tab?

Thanks for any help in advance.

---

### Post by nandinibhaduri on 2009-08-11
But wont that mean that I will have to format and install ubuntu again?

---

### Post by slakkie on 2009-08-11
What kind of wireless card do you have?

please post any relevant output of these two commands:

```

lspci | grep -i network
lsusb | grep -i network

```

---

### Post by nandinibhaduri on 2009-08-11
nandini@nandini-home-lp:~$ lspci | grep -i network
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
nandini@nandini-home-lp:~$ lsusb | grep -i network
nandini@nandini-home-lp:~$

---

### Post by arch0njw on 2009-08-11
> **nandinibhaduri said:**
> More information, if that helps.

nandini@nandini-home-lp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1E:EC:0E:EF:44  
          inet6 addr: fe80::21e:ecff:fe0e:ef44/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37677 (36.7 KB)  TX bytes:492 (492.0 b)
          Interrupt:19 

Another thing - Why cant I see the wireless connection thing in the Connection Tab?

Thanks for any help in advance.

Silly question:  you have rebooted, yes?

From the command line, you you type the following (within the quotes), do you get any errors?
1) "sudo ifdown eth0"
2) "sudo ifup eth0"
-- just in case you don't know, when it asks for a password, it is your password

Finally, ah, the Broadcom wireless.  You'll need to get wired working first so you can enable the restricted drivers.  I have this wireless card in one of my laptops and I go bonkers every time I do an version upgrade.

---

### Post by slakkie on 2009-08-11
Please have a look here

[http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html](http://www.colinblog.com/2008/04/how-to-install-broadcom-bcm4310-usb.html)

---

### Post by nandinibhaduri on 2009-08-11
> **arch0njw said:**
> Silly question:  you have rebooted, yes?

From the command line, you you type the following (within the quotes), do you get any errors?
1) "sudo ifdown eth0"
2) "sudo ifup eth0"
-- just in case you don't know, when it asks for a password, it is your password

Finally, ah, the Broadcom wireless.  You'll need to get wired working first so you can enable the restricted drivers.  I have this wireless card in one of my laptops and I go bonkers every time I do an version upgrade.

rebooted - yes.

"sudo ifup/ifdown eth0" says nothing

---

### Post by nandinibhaduri on 2009-08-11
hei, i got wired. just changed eth0 properties - Configuration to Automatic Configuration (DHCP), and my net started working.

now - can you please help me about the wireless?

---

### Post by slakkie on 2009-08-11
see the link i posted for your wireless.

---

### Post by nandinibhaduri on 2009-08-11
To Install "ndiswrapper" and "ndisgtk" it looks like I will have to upgrade to 8.04 first.[B] [FONT=Arial][/FONT]
[/B]

---

### Post by nandinibhaduri on 2009-08-12
Well, terrible thing happened. 

Tried to upgrade to 8.04 LTS using update-manager. Everything was going well. After downloading - during the installation of the upgrade - which said wud take another 20 minutes - I left for a cup of coffee - came back to find the laptop shut. I swtiched it on - and tried to boot in Ubuntu - but when I entered my administrator login - I got an error saying the 'HOME' directory was missing, and it would use /root as home. Clicked OK - it said that it was ignoring the .dmrc entry, permission denied. Clicked OK, there was a blank brown screen. :confused:

Tried to Google search a lot. Booted in the recovery mode. Created the home directory. Created a .dmrc file. Changed the permissions with chmod, and gave ownership with chown to the administrator user.

Now no error is coming - just a blank brown screen. :(

Do I have to clean install?

---

### Post by arch0njw on 2009-08-12
If it were me, at this point I would burn the 8.04 CD on another machine and install from the CD.  When you do that, you can tell it which partitions to format, and which to keep and mount as-is.  You can reformat your system partitions (e.g,. /, /boot, etc.) and if you have a specific /home partition, you can tell it to just mount that as-is.  That will let you keep your files.

Perhaps someone else has a magic trick they can pull, but that's my non-magical trick.

If you do not currently have a "/home" partition, I strongly suggest that if you do a full reinstall (complete with repartitioning) that you create one.  This makes it really easy to fully reinstall the OS without losing your personal files (just sayin' in case you didn't know).

Sorry I can't be of more help.

---

### Post by nandinibhaduri on 2009-08-13
Got the thing working. Deleted the .dmrc file. Set the default language and session from the option thing.

And Hardy Heron started working. Some things was not working. But after I ran dpkg --configure -a, everything was fine. Even my wireless is working now.

:)

Thanks for all your help.

---

### Post by arch0njw on 2009-08-13
> **nandinibhaduri said:**
> Got the thing working. Deleted the .dmrc file. Set the default language and session from the option thing.

And Hardy Heron started working. Some things was not working. But after I ran dpkg --configure -a, everything was fine. Even my wireless is working now.

:)

Thanks for all your help.

Glad to hear you got it working!

---


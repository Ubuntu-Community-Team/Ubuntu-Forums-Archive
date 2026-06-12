---
title: "MythTV Frontend Sleep/Wake function"
date: 2013-04-09
forum: Mythbuntu
---

### Post by gga96 on 2013-04-09
Hi All,
I am researching frontend sleep/wake with the intention of implementing the functions.

My system is:
Linux Frontemd-L 3.2.0-39-generic-pae #62-Ubuntu SMP Wed Feb 27 22:25:11 UTC 2013 i686 i686 i386 GNU/Linux
MythBuntu 12.04, MythTV 0.26.

Reading [http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep](http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep) and [http://forums.overclockers.com.au/showthread.php?t=810214](http://forums.overclockers.com.au/showthread.php?t=810214) both refer to "cat /proc/acpi/wakeup" and these files do not exist on my system.

To get away to a clean start how should I install the appropriate files and pre-requisites?

Greatfull for your help.
Glen

---

### Post by PhilWig on 2013-04-10
Do these help:

[http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
[http://www.mythtv.org/wiki/Mythwelcome](http://www.mythtv.org/wiki/Mythwelcome)

Regards
Phil

---

### Post by gga96 on 2013-04-10
Good morning Phil from under down under, thanks.

Found the answer to my question on the second reading of [ACPI Wakeup]("http://ubuntuforums.org/wiki/ACPI_Wakeup")
> 
Which kernel are you using?
...
- Kernel versions 2.6.22 and newer use /sys/class/rtc/rtc0/wakealarm - [see "Using /sys/class/rtc/rtc0/wakealarm", next]("http://ubuntuforums.org/#Using_.2Fsys.2Fclass.2Frtc.2Frtc0.2Fwakealarm") - Kernel versions 2.6.21 and older use /proc/acpi/alarm - see ["Archive: Using /proc/acpi/alarm"]("http://ubuntuforums.org/#Archive:_Using_.2Fproc.2Facpi.2Falarm") below
...


I am swimming in deep water at the moment with linux, it is a new world.

Thanks again.
Glen

---

### Post by gga96 on 2013-04-12
I have progressed to "Manually test wakealarm".
The hwclock update function has been disabled as described above for Ubuntu 9.10 and later.

When I run the following with or without the sudo prefix
> 
echo 0 > /sys/class/rtc/rtc0/wakealarm
echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm

the response to both commands is "bash: /sys/class/rtc/rtc0/wakealarm:  Permission denied".

What password do I use?

Glen

---

### Post by PhilWig on 2013-04-15
Permissions on my system are like this:
> ls -l  /sys/class/rtc/rtc0/wakealarm
-rw-r--r-- 1 root root 4096 Apr 15 17:54 /sys/class/rtc/rtc0/wakealarm

Your motherboard does support ACPI?  It is turned on in your bios?

Regards
Phil

---

### Post by gga96 on 2013-04-15
Hi Phil,

I am having heaps of trouble.

MythTV remote frontend is now unstable and I cannot answer your questions without re-installing. 
What I can say is about 4 days ago the responce to "# sudo grep -i rtc /var/log/dmesg" was something like "RTC can wake from S4" and "rtc0: alarms up to one month". The answer to permissions would be as installed.

The remote frontend desktop opens with:
- no mouse cursor
- multiple restored windows on top of "Applications Panel" with all window origins at 0,0
- I am able to move top windows to clear panel and the change panel to vertical and open gedit which enables mouse with desktop X cursor(plus cursors in various windows).
- no z order change when window clicked
- no menu response

The backend desktop adopted the same symptoms and eventually had to re-install the lot.
I am desperatley trying to avoid a re-install, the unstable state must have a cause.

Thanks Phil and ideas appreciated
Glen

---

### Post by PhilWig on 2013-04-17
Hi Glen,

Let's recap. We seem to have two issues here (ACPI and stability) and two systems - a remote frontend and a separate (dedicated?) backend.  ACPI is of course only really appropriate for the backend but that now seems secondary to:  > MythTV remote frontend is now unstable  Why 'now' I wonder?  Your symptoms seem to go far deeper than the Mythtv application, Myth settings or even database corruption.
 
An update perhaps?  I have automatic updating turned off for stability but that's a personal choice.

Do you think hardware checks might be appropriate now?  Memory test?  Smart data? Cooling?  Power? Re-seat boards and connectors?  Don't forget your anti-static lead!

Keep cool!
Phil

---

### Post by gga96 on 2013-04-17
Hi Phil,

Some progress, I have found that the backend does not connect to the net during boot.
History is that the backend required a static IP so the front end could connect to the DB. 

The file "/etc/network/interfaces" was edited to the following:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3
gateway 192.168.1.1
netmask 255.255.255.0

File "/etc/resolv.conf" was appended with the Router IP:
> 
nameserver 192.168.1.1

Changes made to backend>general and frontend data relating to 192.168.1.3, the two connected  and all appeared to be normal ops.

Subsequent cold boots to both machines seemed normal over the next several days. Then I realized the EPG was not being updated. The backend and mythfilldatabase were not connecting to the net.

I discovered that file "/etc/resolv.conf" was being overwritten during boot and "nameserver 192.168.1.1" was lost.

I have tried putting "nameserver 192.168.1.1" back again and the net ops are normal until reboot.
I have also used ISP DNS IPs "nameserver 180.181.127.3: and "nameserver 180.181.127.4", and all works well with that until reboot.
I have also reverted back to dynamic IPs and loopback IPs, in that config all net ops are normal and persistent.
The reboot clears all nameserver data.

The frontend is wired and "Network Connections" data MAC is correct.

First things first, I am looking to get the backend network working correctly with a static IP.

I am at a loss to know what to try next. Any ideas?

Thanks Phil.
Cheers
Glen

---

### Post by PhilWig on 2013-04-18
Two suggestions:

1. use DHCP but have the router configured to give the same fixed address each time.  Simple; no changes on Ubuntu version changes.

2.  Lurk or put a query to the ubuntu > networking forum where they deal with such issues.  See this for example:
[http://ubuntuforums.org/showthread.php?t=2081392](http://ubuntuforums.org/showthread.php?t=2081392)

Regards
Phil

---

### Post by gga96 on 2013-04-18
Hi Phil,

Followed idea 2 and then followed chili555 instructions with dns-nameservers primary, secondary of the router.
The file "/etc/network/interfaces" was edited to the following:
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3
gateway 192.168.1.1
netmask 255.255.255.0
dns-nameservers 180.181.127.3 180.181.127.3

The ping worked, rebooted and the backend connected to the net. The problem seems to be associated with static IP.

Well spotted, thank you. Will apply the same fix to the frontend.

btw: With reference to my previous comment:
> 
The backend desktop adopted the same symptoms and eventually had to re-install the lot.

This was definately caused when Update Manager got to the point of processing samba and lacked permission, the process stopped at this point, resulting in a corrupted desktop. 

I do not think hardware is an issue. Two machines, two different applications frontend/backend, o**ne **common desktop.
I am beginning to think the Update Manager is hazadous material.

The frontend is back on the agender, will check it out, I live in hope the desktop can be repaired. 

Thanks again.
glen

---

### Post by PhilWig on 2013-04-18
Good.  How did you find out your DNS server addresses?
Phil

---

### Post by gga96 on 2013-04-18
Good morning Phil,

I have a NetGear N150 router and it came with some Windows interface software.  Poking around in this software I arrived at tab Advanced > Setup > Internet Setup > Domain Name Server> Use These DNS Servers(radio button): and it listed the Primary and Secondary DNS IPs.

The frontend is still corrupt but it connects to the net and I was able to run Update Manager. It did not improve or make things worse.

There remains four issuses:
1. desktop corruptsion?
2. deside to not continue with Update Manager? I beleave it stirs the pot and introduces unknown side affects.
3. frontend cant connect to DB.
4. re-install frontend? Do not like to do this again!!!

I will continue item 3 on the network forum, and continue with 1 & 2 here.

Thanks Phil
Cheers
Glen

---

### Post by gga96 on 2013-04-18
Well I did what I could, but could not stop the frontend curruption problem and therefore could not seek help on the network forum, so I re-installed the frontend and I am still stuck with no DB connection. Have posted this issue on network forum "Frontend not Conecting to DB error 130".

This thread has been hijacked by other issues and probably should be killed.
Glen

---

### Post by gga96 on 2013-04-27
Just to tidy up. 

The frontend connection problem was solved and I have now successfully implemented the Sleep/Wake functions as detailed in reference [http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep](http://www.mythtv.org/wiki/Putting_mythfrontend_to_sleep) with out any [SIZE=2]issues[/SIZE]. Moving on to backend sleep now.

This thread is now CLOSED.

Thank you all for your help.
Glen

---


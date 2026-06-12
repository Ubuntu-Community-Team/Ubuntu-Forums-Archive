---
title: "Not Connection to the internet"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by Q.Q on 2009-10-10
I'm unable to connect to the internet. it keeps saying connecting...then a few minutes later..i get network timeout. Someone please help me. URGENTLY:(

---

### Post by Q.Q on 2009-10-10
I am fairly new to using ubuntu and now i cannot browse the internet.  I am geting network timeout.  Can somebody tell me what to do please?? :confused:

---

### Post by Iowan on 2009-10-10
Check **ifconfig -a** to see if your interface is getting an IP address - BTW, are you connecting via wireless or wired?  Connecting via Network Manager?

---

### Post by bapoumba on 2009-10-10
Threads merged.

---

### Post by Q.Q on 2009-10-11
connecting via wireless using network manager

---

### Post by fixerman on 2009-10-11
> **Q.Q said:**
> I'm unable to connect to the internet. it keeps saying connecting...then a few minutes later..i get network timeout. Someone please help me. URGENTLY:(

You are not alone Q.Q.

I installed Ubuntu on a laptop yesterday and I have the same problem with my wireless connection. When I boot up all is well for a minute or two and then I loose access to the internet and my network. Yet the indicator still shows an 84% strong connection.If I disconnect and reconnect it comes back again but only for a very short while before it looses access again. Wired connection works fine.

Hopefully we will get some solution from this forum.

---

### Post by houstonbofh on 2009-10-11
You will get lots of solutions.  However, they vary based on what card you have.  There are several known issues with the broadcom WiFi cards, for example...

Some things to start, go to System -> Administration -> Hardware Drivers and make sure the card is actually enabled.

Show the results of 'ifconfig' and 'lspci' from the command line.

---

### Post by fixerman on 2009-10-11
> **houstonbofh said:**
> You will get lots of solutions.  However, they vary based on what card you have.  There are several known issues with the broadcom WiFi cards, for example...

Some things to start, go to System -> Administration -> Hardware Drivers and make sure the card is actually enabled.

Show the results of 'ifconfig' and 'lspci' from the command line.

fixerman@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
fixerman@ubuntu:~$

---

### Post by fixerman on 2009-10-11
> **houstonbofh said:**
> You will get lots of solutions.  However, they vary based on what card you have.  There are several known issues with the broadcom WiFi cards, for example...

Some things to start, go to System -> Administration -> Hardware Drivers and make sure the card is actually enabled.

Show the results of 'ifconfig' and 'lspci' from the command line.

fixerman@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"John"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1C:DF:7D:7A:65   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-48 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

fixerman@ubuntu:~$

---

### Post by fixerman on 2009-10-11
> **houstonbofh said:**
> You will get lots of solutions.  However, they vary based on what card you have.  There are several known issues with the broadcom WiFi cards, for example...

Some things to start, go to System -> Administration -> Hardware Drivers and make sure the card is actually enabled.

Show the results of 'ifconfig' and 'lspci' from the command line.

When I go to Hardware drivers the only driver shown is for the video card.

---

### Post by Iowan on 2009-10-11
Another source for hardware information:```
lshw -C network
```

---

### Post by houstonbofh on 2009-10-11
> **houstonbofh said:**
> Show the results of 'ifconfig' and 'lspci' from the command line.
> **fixerman said:**
> fixerman@ubuntu:~$ iwconfig
Notice anything wrong here? :)
I want to see if you are pulling an ip address.

Also, while trying to connect, (associate with the AP, not open a browser...) open another terminal, and run 'tail /var/log/syslog -f' in it, and see if you notice some errors looping.

---

### Post by fixerman on 2009-10-12
> **houstonbofh said:**
> Notice anything wrong here? :)
I want to see if you are pulling an ip address.

Also, while trying to connect, (associate with the AP, not open a browser...) open another terminal, and run 'tail /var/log/syslog -f' in it, and see if you notice some errors looping.

I'm sorry but I am a complete novice when it comes to Linux. Thank you for your advice but it went right over my head.

I am going to post my difficulty on the Beginners forum.

Thanks again!

---

### Post by shredder12 on 2009-10-12
> **fixerman said:**
> I'm sorry but I am a complete novice when it comes to Linux. Thank you for your advice but it went right over my head.

I am going to post my difficulty on the Beginners forum.

Thanks again!
Don't worry everyone is a newbie once ...
you don't have to post it on beginners forum.. everybody here will help you.. 
Look... the commands you have been asked to run give the hardware information about your system... 
In this way you will know if there is some hardware compatibility issue..
nd /var/log/syslog is a file where system activities are logged...
running it with a "-f" option gives you the benefit to watch the changes in the file in real time (or directly)..
so when you try to connect and the system receives some error.. you will be able to see them simultaneously getting logged in that file after running that command.


Hope that helped you!!

---

### Post by fixerman on 2009-10-12
> **shredder12 said:**
> Don't worry everyone is a newbie once ...
you don't have to post it on beginners forum.. everybody here will help you.. 
Look... the commands you have been asked to run give the hardware information about your system... 
In this way you will know if there is some hardware compatibility issue..
nd /var/log/syslog is a file where system activities are logged...
running it with a "-f" option gives you the benefit to watch the changes in the file in real time (or directly)..
so when you try to connect and the system receives some error.. you will be able to see them simultaneously getting logged in that file after running that command.


Hope that helped you!!


Sorry but, like I said, over my head. At present I can get a good wireless connection but it drops out again after anything between 10 seconds and 10 minutes. The indicator always show max signal strength. It does not come back until I disconnect and reconnect using the connection manager.

---

### Post by fixerman on 2009-10-12
I tried what you said and got...

Error: GET failed, `System Error'

---

### Post by shredder12 on 2009-10-12
I don't think I will be able to help you with this problem. But still you should post the whole output that you got while connecting. I am sure others will be able to help you with it..

---

### Post by fixerman on 2009-10-12
> **shredder12 said:**
> I don't think I will be able to help you with this problem. But still you should post the whole output that you got while connecting. I am sure others will be able to help you with it..

Sorry but I don't understand what you mean by "post the whole output".

---

### Post by shredder12 on 2009-10-12
I meant the output of tail /var/log/syslog -f while you were trying to connect

---

### Post by fixerman on 2009-10-12
> **shredder12 said:**
> I meant the output of tail /var/log/syslog -f while you were trying to connect

This is what I got???? I hope it means something to you!

Oct 12 18:20:01 fixerman-laptop /USR/SBIN/CRON[8608]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 18:28:25 fixerman-laptop kernel: [ 1728.629307] NVRM: Xid (0001:00): 6, PE0000 0200 05000000 0000fd30 80807364 03200000
Oct 12 18:30:01 fixerman-laptop /USR/SBIN/CRON[12546]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 18:40:01 fixerman-laptop /USR/SBIN/CRON[16761]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 18:50:01 fixerman-laptop /USR/SBIN/CRON[20664]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 19:00:01 fixerman-laptop /USR/SBIN/CRON[24675]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd hourly 2>/dev/null)
Oct 12 19:00:01 fixerman-laptop /USR/SBIN/CRON[24677]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 19:10:01 fixerman-laptop /USR/SBIN/CRON[30584]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 19:17:01 fixerman-laptop /USR/SBIN/CRON[3488]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 12 19:20:01 fixerman-laptop /USR/SBIN/CRON[5719]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

---

### Post by shredder12 on 2009-10-12
Well,, honestly speaking i can't figure out anything important here. Where did you get the "Get Failed: System error" from ??
Are you sure this is the output of the whole time you were trying to connect because i don't see any networking related trace anywhere

---

### Post by houstonbofh on 2009-10-12
Either you did not type -f (which I doubt) or syslog was seeing no errors.  This is odd...  I am about to go over your head again, so let me back up and say what I am trying to do...

First, in linux there are many ways to view a file...  (more, less, cat, tail...)  They all have slight differences related to how they pipe.

"How they what?"  In DOS, you can pipe as well, with something like "dir > output.txt" but it is limited.  In Linux you can pipe to a pipe to a pipe, and so on... (In linux the pipe is the "|" key)  A common one is to pipe to a program called "grep" which filter output.  For example, "more /var/log/syslog | grep wlan" will list the entire syslog file, but only display lines with "wlan" in them.

You can also "tail" a file.  the program "tail" by default prints the last 5 lines of a file.  But you can print the last 10, or 3, or whatever.  With "-f" it doesn't exit, and keeps going.  This gives you a continuous view of a log file, which is very handy.

Here is an example on a loptop with this problem I am looking for.
```
lee@portable:~$ tail /var/log/syslog -f
Oct 12 15:44:23 portable NetworkManager: <debug> [1255380263.001847] periodic_update(): Roamed from BSSID (none) ((none)) to 00:02:6F:56:0C:18 (AON) 
Oct 12 15:46:17 portable NetworkManager: <debug> [1255380377.001813] periodic_update(): Roamed from BSSID 00:02:6F:56:0C:18 (AON) to (none) ((none)) 
Oct 12 15:46:23 portable NetworkManager: <debug> [1255380383.002011] periodic_update(): Roamed from BSSID (none) ((none)) to 00:02:6F:56:0C:18 (AON) 
Oct 12 15:48:17 portable NetworkManager: <debug> [1255380497.001444] periodic_update(): Roamed from BSSID 00:02:6F:56:0C:18 (AON) to (none) ((none)) 
Oct 12 15:48:22 portable NetworkManager: <debug> [1255380503.002172] periodic_update(): Roamed from BSSID (none) ((none)) to 00:02:6F:56:0C:18 (AON) 
Oct 12 15:50:01 portable /USR/SBIN/CRON[11573]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Oct 12 15:50:17 portable NetworkManager: <debug> [1255380617.002214] periodic_update(): Roamed from BSSID 00:02:6F:56:0C:18 (AON) to (none) ((none)) 
Oct 12 15:50:23 portable NetworkManager: <debug> [1255380623.002104] periodic_update(): Roamed from BSSID (none) ((none)) to 00:02:6F:56:0C:18 (AON) 
Oct 12 15:52:17 portable NetworkManager: <debug> [1255380737.000295] periodic_update(): Roamed from BSSID 00:02:6F:56:0C:18 (AON) to (none) ((none)) 
Oct 12 15:52:23 portable NetworkManager: <debug> [1255380743.001525] periodic_update(): Roamed from BSSID (none) ((none)) to 00:02:6F:56:0C:18 (AON)
```

So, if you could try that command again, and let it run a bit while you try and bust the WiFi, it may look like this.

---


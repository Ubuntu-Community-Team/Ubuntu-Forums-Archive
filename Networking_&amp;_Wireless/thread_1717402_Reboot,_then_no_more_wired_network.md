---
title: "Reboot, then no more wired network"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by MaxxJ on 2011-03-29
Hi everyone,

I have rebooted, then my wired network kept telling me that it was disconnected. I have rebooted: same result. I have tried another port on the router: same result. I'm currently using my wireless PCI card, hoping it won't stop working too! :P

I would need some (possibly heavy) guidance into resolving this issue.

BTW, I don't think there was any updates before the "buggy reboot".

Any help is welcome.

Thanks,

MJ



max@Blackbox:~$ **uname -a**
Linux Blackbox 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux

max@Blackbox:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:b8:ba:33  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5527 (5.5 KB)  TX bytes:5527 (5.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:01:c7:a9  
          inet addr:192.168.10.147  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe01:c7a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4041365 (4.0 MB)  TX bytes:1210066 (1.2 MB)

---

### Post by Do_Japan on 2011-03-29
> **MaxxJ said:**
> Hi everyone,

I have rebooted, then my wired network kept telling me that it was disconnected. I have rebooted: same result. I have tried another port on the router: same result. I'm currently using my wireless PCI card, hoping it won't stop working too! :P



Where did you hear that your wired network is disconnected?  Your ifconfig results indicate that you have a local IP address, which suggests that the router and computer are still communicating.  Is the activity light on the front of the router that corresponds with the port you are using lit of flashing when your PC is turned on?

---

### Post by MaxxJ on 2011-03-29
> **Do_Japan said:**
> Where did you hear that your wired network is disconnected?  Your ifconfig results indicate that you have a local IP address, which suggests that the router and computer are still communicating.  Is the activity light on the front of the router that corresponds with the port you are using lit of flashing when your PC is turned on?

No, it is not flashing on the router. There is a yellow light flashing behind my computer.. every maybe 3 seconds. Another computer is connected and its router light is flashing like it should.

I somehow cannot take a screenshot of that, but when I click on the network icon in the system tray (gnome panel), it says:
  Wired Network
    disconnected
  Wireless Networks
    ... (The network I'm connected to.)
    Disconnect
      --- Available ---
    ... (The networks I can see.)
    ...

This is where I see that I'm "disconnected" even though I'm not, physically.

Thanks,

MJ

---

### Post by Do_Japan on 2011-03-29
Bad cable or NIC.  Start with a different cable as those are cheaper, then NIC.

---

### Post by MaxxJ on 2011-03-29
> **Do_Japan said:**
> Bad cable or NIC.  Start with a different cable as those are cheaper, then NIC.

Already tried 2 cables in different hub ports which usually work good. (I had a 2nd one already there because I often connect my laptop wired on this desk too and it always works.)

Oh wait a sec. Lets make 2000 % sure...

OK, the cables are good, the router is good too. I plugged my laptop with both wires and both lights on the router lit. The laptop was connected to the Internet in both cases.

Thanks,

MJ

---

### Post by Do_Japan on 2011-03-29
Check the connection on both ends, check the ports for debris to be sure, the light not flashing on the router means it doesn't even think it's plugged in to an active computer.  Most likely culprit is the NIC.  It could be the software, might want to check network tools, make sure wired networks is enabled.  Last resort, get a new NIC.  If its a desktop then it's a super easy fix.  Laptop is more problematic. 

PS Reinstall your OS if you are really cheap and dont want to shell out for a new NIC.  I say maybe .5% chance that reinstall will fix this... :P

---

### Post by collisionystm on 2011-03-29
Okay so you have a wireless connection that is receiving a dhcp. If you right click on your networking icon, and disconnect from your wireless, then hit auto eth0 it should attempt to establish a wired connection.

Then bring up terminal, ifconfig and see if eth0 has an address. try to ping google.com

I have had problems with being on a wired and wireless connection at the same time.

---

### Post by MaxxJ on 2011-03-29
Thanks collisionystm for your reply.

Do_Japan is correct. The NIC seems broken. I have rebooted on another HDD which has Win7 on it. The adapter wasn't working more. It suggested a driver update, so I tried that: no luck. Check the BIOS: enabled.

This is the worst motherboard I have ever bought. First some USB ports started to act weird. Then the audio in/out stopped working. Now the onboard network adapter... 

Sorry guys, it had nothing to do with Ubuntu this time.

Thank you for your help though.

This could be marked as resolved....

Thanks

MJ


ahh for the record, the mobo is an ASUS M4A79XTD EVO... It's slowly dying, one "module" at a time. Don't ever buy that. -_-'

---


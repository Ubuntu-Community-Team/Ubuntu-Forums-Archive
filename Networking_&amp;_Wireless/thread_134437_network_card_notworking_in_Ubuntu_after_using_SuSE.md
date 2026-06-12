---
title: "network card notworking in Ubuntu after using SuSE for a while"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by daedalusman on 2006-02-21
Well here is the problem, I have been using SuSE 10.0 for a while now (which is what I'm using right now) and was wanting to go back in to Ubuntu and use that to test dapper and to check out Xgl and compiz. Well when I restarted, while Ubuntu was going through the boot process, it got the the point where it configures the network connection and just paused for about a min or 2 and then just continued to boot but without the network card actually working. I've noticed that the same thing happens when I try and use windows, no network connection. I have no idea how to fix this, I have tried to reconfigure the card in Ubuntu and then restarting but to no avail. Back before I had Ubuntu SuSE and Windows on this machince (when I was just using Ubuntu and Windows) both were able to connect to the internet with no problems. Then I installed SuSE 10.0 and thats when this problem started. Can anyone here shed some light on this for me. I have posted this in a SuSE forum as well but I find this forum to be way better so I thought I might try here as well, thanks for any help.

---

### Post by atomicmoose on 2006-02-22
Is this a wireless card or wired?

---

### Post by zachtib on 2006-02-22
i had a similar problem last year going from suse >> ubuntu >> suse, and lost internet

turned out, i had my laptop on a switch, and my uni doesnt like switches.

likely, its something outside of your computer thats causing problems

---

### Post by daedalusman on 2006-02-22
[QUOTE=atomicmoose]Is this a wireless card or wired?[/QUOTE]


It's the on board Marvell gigabit ethernet on my ASUS A8V Deluxe.

---

### Post by jamesr on 2006-02-22
Does Dmesg indicate that it is being seen during the boot up stage.

Please Post section

Post output from 
sudo ifconfig -a

---

### Post by daedalusman on 2006-02-22
[QUOTE=jamesr]Does Dmesg indicate that it is being seen during the boot up stage.

Please Post section

Post output from 
sudo ifconfig -a[/QUOTE]

Well this is all that refferes to eth0 from the dmesg output...

```
[   27.399331] skge addr 0xf9a00000 irq 17 chip Yukon-Lite rev 9
[   27.399401] skge eth0: addr 00:13:d4:78:11:45

[   55.841843] skge eth0: enabling interface
[   55.881208] NET: Registered protocol family 17

[  307.225527] NET: Registered protocol family 10
[  307.225662] Disabled Privacy Extensions on device c02eb280(lo)
[  307.225840] IPv6 over IPv4 tunneling driver
[  318.188322] eth0: no IPv6 routers present
```

And here is what I got from ifconfig -a...

```
eth0      Link encap:Ethernet  HWaddr 00:13:D4:78:11:45
          inet6 addr: fe80::213:d4ff:fe78:1145/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:139023 (135.7 KiB)  TX bytes:139023 (135.7 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

Also a thing to note, in SuSE the IRQ that is given to the card is 11 but in both Ubuntu and Windows it is assigned IRQ 17, could that be the problem? Also, I have disabled IPv6 under SuSE as well. Don't know if this info will help but I thought it was interesting. Thanks

---

### Post by jamesr on 2006-02-23
It seems to seeing the card but not getting an address under inet 4 but is under inet6.

the dmesg is also saying no ipv6 routers present 

try sudo dhclient

and note the error messages 

then sudo ifconfig -a again

It might interesting to disable ipv6 on the Ubuntu version.

What is your router?

---

### Post by daedalusman on 2006-02-23
Well dhclient told me that there were no dhcpoffers present, and here is the out put from ifconfig -a...

```
eth0      Link encap:Ethernet  HWaddr 00:13:D4:78:11:45
          inet6 addr: fe80::213:d4ff:fe78:1145/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17016 (16.6 KiB)  TX bytes:17016 (16.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Also, how do I go about disabling ipv6 in ubuntu?

---

### Post by dbott67 on 2006-02-23
Are you behind a D-Link-type router (or linksys, netgear, etc)?  Occasionally, the router acts up and the DHCP service hangs (or other problems).  Simply cycling the power on the router will reboot the router's OS and re-start all of the services.

Then try re-obtaining an IP address (sudo dhclient) from your Ubuntu computer.

-Dave

btw, the Suse box may not have issues because the IP address lease has not expired and therefore has not attempted to renew or acquire a new address.

---

### Post by daedalusman on 2006-02-23
I'm using a D-link DI-604 router. I tried cycling the power and then dhclient but to no avail, just the same output saying there were no dhcpoffers.

---

### Post by mips on 2006-02-23
What happens if you use a static address ? I suspect your card is fine.

Try upgrading the firmware on the D-Link.
**Model Rev A-C**: [ftp://ftp.dlink.com/Gateway/di604/Firmware/di604_firmware_220.bin](ftp://ftp.dlink.com/Gateway/di604/Firmware/di604_firmware_220.bin)
**Model Rev E**: [ftp://ftp.dlink.com/Gateway/di604_revE1/Firmware/di604_firmware_351.bin](ftp://ftp.dlink.com/Gateway/di604_revE1/Firmware/di604_firmware_351.bin)

Check the bottom of the router for the Review version. On the label it says **H/W:B1** or something in the range of A-C & E. Do NOT use the wrong firmware version for your device.

Do NOT upgrade over a wireless link.

---

### Post by daedalusman on 2006-02-23
See thing about the firmware is that there are some people in my house that use Xbox live and the 2.20 version isn't compatiable with this xbox live, that and it only adds support for static dhcp. I'm using version 2.18 and that is the most recent version that supports xbox live.

---

### Post by jamesr on 2006-02-24
Can you look at the admin page of the Router to check that there is nothing funny going on there, because I have seen after a power reset the router can change it's config, ie not activating the DHCP, I am not sure what the defaults on the 604 are. Also the reset functionally ie just reset or or reset to factory defaults can depend on the time of the reset.

I will have to check how to disable the ipv6, if I remember correctly it something like renaming the ipv6 file so that is not found but, of course, you then get an error message in dmesg.

---

### Post by daedalusman on 2006-02-24
No, everything looked good to me, DHCP was enabled and I didn't see anything weird. I was able to get the internet to work in Ubuntu though. What I did was I shutdown my PC, disconected the power cord, hit the power switch, and then plugged the power cord back in. I then started up into Ubuntu and the internet worked fine. I'm thinking that its not a router problem now but I really don't know. I have since boot to SuSE and then back to Ubuntu and things are still working fine. I don't know if I will have to do this again but if the problem comes back I will post here again. Thanks for the help and if you can think of something else or for a reason on why this has helped please post your thoughts.

---

### Post by jamesr on 2006-02-24
All's well that ends well

BUT that is certainly an interesting way to reset a PC but that can be one of the way to do a partial reset of the BIOS on some ATX motherboard. DFI , if remember correctly, was one of them. A full reset to factory defaults was done  by following the first stage ie above , by changing a link on the mobo and the returning to the original setting after 1 minute.  Because in an ATX system, the PSU always supplies some power as seen by a red LED on the mobo., by disconnecting the power cord first and the switching  the power switch on,  you will see that the LED extinguishes. Perhaps this was the problem.

---


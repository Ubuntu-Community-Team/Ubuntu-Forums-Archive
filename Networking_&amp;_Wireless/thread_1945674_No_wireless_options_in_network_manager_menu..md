---
title: "No wireless options in network manager menu."
date: 2012-03-23
forum: Networking &amp; Wireless
---

### Post by danceswithcats on 2012-03-23
I have had to unplug my wired connection to my desktop and set up wifi.  I haven't got wireless connections options in network manager menu.  I was following the troubleshotter in the documentation and when I ran nm-applet I got 

[I]An instance of nm-applet is already running..

**(nm-applet:1744):  WARNING ** <WARN> constructor ():  Couldn't initialize the D-Bus manager.

[/I]

At this point, the troubleshooter said go to the forums, so here I am.  I've got 11.04.  I'm sure wireless was working okay a while back.  It's just that I've always used it wired on this machine, so haven't needed it.  The wifi network is working fine on my laptop.

Any help gratefully received.

---

### Post by Ms. Daisy on 2012-03-24
What is the output of 

```
ifconfig
```

---

### Post by danceswithcats on 2012-03-26
Hi Ms Daisy,

I've been able to plug etho back in but the wifi applet still doesn't work, and I would like it to, in order to not have wires trailing around the house.  Anyway, this is the output with internet plugged in:



eth0      Link encap:Ethernet  HWaddr d0:27:88:4e:78:ee  
          inet addr:192.168.1.60  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:fe4e:78ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6189 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6841342 (6.8 MB)  TX bytes:798688 (798.6 KB)
          Interrupt:42 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:688 (688.0 B)  TX bytes:688 (688.0 B)


Thanks,

Pete (DWC)

---

### Post by Ms. Daisy on 2012-03-26
OK. We need to know what the wireless hardware is to get it configured. What is the output of
```
lspci -v | grep WiFi
```

---

### Post by danceswithcats on 2012-03-26
I'm afraid it gave no output.  It just gave back the prompt.

---

### Post by Ms. Daisy on 2012-03-26
Try 
```
lspci
```
and see if it gives you something called wireless or wifi. Or if you know the brand of your wireless interface look for that. (It might be easier to read the output if you maximize your terminal window first.)

---

### Post by wildmanne39 on 2012-03-26
Hi, try this please:
```
lspci -nnk | grep -iA2 net
lsusb
```
post the output here.
Thanks

---

### Post by danceswithcats on 2012-03-27
First of all, can I say how grateful I am for your help, Ms Daisy and Wildmanne 39?

I couldn't find any wifi output in the lspci command, so I ran your command, WM, and got this:

peter@peter-desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Foxconn International, Inc. Device [105b:0e27]
	Kernel driver in use: r8169
peter@peter-desktop:~$ lsusb

I would have sworn that I was receiving wifi signals when I first set up the machine, although a nagging doubt is undermining my certainty now.  My wife has become tired of having a cable trailing across the hall and up the stairs, so I was going to activate it.  

This output seems to say that I don't have a wireless card.  I thought the ethernet card was wireless, but, what do I know?  

Thanks again,

Pete

---

### Post by bkratz on 2012-03-27
> **danceswithcats said:**
> First of all, can I say how grateful I am for your help, Ms Daisy and Wildmanne 39?

I couldn't find any wifi output in the lspci command, so I ran your command, WM, and got this:

peter@peter-desktop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Foxconn International, Inc. Device [105b:0e27]
    Kernel driver in use: r8169
peter@peter-desktop:~$ lsusb

I would have sworn that I was receiving wifi signals when I first set up the machine, although a nagging doubt is undermining my certainty now.  My wife has become tired of having a cable trailing across the hall and up the stairs, so I was going to activate it.  

This output seems to say that I don't have a wireless card.  I thought the ethernet card was wireless, but, what do I know?  

Thanks again,

Pete


What was the output of lsusb?  The ethernet is the wired connection.  If the device is a usb "dongle" it would show up with the lsusb command and not with anything using lspci.

---

### Post by wildmanne39 on 2012-03-27
Hi, the ```
lsusb
```command I gave you should have said something even if you do not have an usb adapter so I know that command did not work right.

You can check your bios and see if the wireless is turned on, if it is a desktop reset the card or move it to another slot and try the commands again.
Thanks

---


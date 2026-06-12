---
title: "Help with Netgear MA401 card"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by jalotta@earthlink.net on 2005-12-28
Greetings,

I am new to Linux, but experienced in OSX and others.  I booted the Live CD on my Powerbook G4.  I can't tell if it recognized the Netgear MA401 card.  Where do I look?  I looked in Network Connection and there is just the lo.

I need to tell you that I have DSL with Airport.  It works well on my other macs.

Just tell me what to do next.  Thank you.

Joe.

---

### Post by Lambert on 2005-12-28
If you look in network from system>administration and do not see your card in the list then there is no driver currently working for the device.

I show this card using the linux-wlan-ng driver. It's not installed by default but it's on the install cd. Put the cd back in the driver and type this terminal command.

```
sudo apt-get install linux-wlan-ng
```

then reboot.

now look in system>admin>network to see if your card shows up, if so, then configure and activate.

---

### Post by dsierpin on 2006-02-02
Hello! 

I just bought that same card.  It shows up as eth1 next to my ethernet card.  Shouldn't it be wlan0?  This wouldn't be a problem, but the command:

```
sudo iwconfig eth1 mode monitor
```

Tells me that the argument "monitor" is invalid.  The card has a prism chipset, and I know it is capable of monitor mode.  Any ideas?

---

### Post by Lambert on 2006-02-02
Not sure if this will help. There are some links that might lead you some where.



> 
You can capture raw 802.11 packets with Prism II adapters on Linux systems with the 0.1.14-pre6 or later version of the linux-wlan-ng drivers (see [[IMG]http://wiki.ethereal.com/wiki/ethereal/img/ethereal-www.gif[/IMG]the linux-wlan page]("http://www.linux-wlan.org/index.html"), and [[IMG]http://wiki.ethereal.com/wiki/ethereal/img/ethereal-www.gif[/IMG]the linux-wlan-ng tarball directory]("ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/")), or with [[IMG]http://wiki.ethereal.com/wiki/ethereal/img/ethereal-www.gif[/IMG]the hostap driver for Prism II/2.5/3]("http://hostap.epitest.fi/").




With the linux-wlan-ng driver, put the card into monitor mode with the command wlanctl-ng *interface* lnxreq_wlansniff enable=true. You should request 802.11 headers by adding to that command the option prismheader=true or, if supported, wlanheader=true; the latter might require libpcap 0.8.1 or later. You can also set the channel to monitor by adding the argument channel=*channel_number* to that command. When the capture completes, turn off monitor mode with the command wlanctl-ng *interface* enable=false. You might also have to turn 802.11 headers off with prismheader=false or wlanheader=false. See [[IMG]http://wiki.ethereal.com/wiki/ethereal/img/ethereal-www.gif[/IMG]the wlan-ng FAQ]("ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/FAQ") for additional information, although note that it does not appear to be up-to-date. 
 With the hostap driver, you should put the card into monitor mode with the command iwpriv *interface* monitor *mode*, where *mode* is 2 or 3 (mode 3 would require libpcap 0.8.1 or later).  When the capture completes, turn off monitor mode with the command iwpriv *interface* monitor 0.

With the hostap driver, you should put the card into monitor mode with the command iwpriv *interface* monitor *mode*, where *mode* is 2 or 3 (mode 3 would require libpcap 0.8.1 or later).  When the capture completes, turn off monitor mode with the command iwpriv *interface* monitor 0.


---

### Post by az on 2006-02-02
Hostap, orinocco and prism2 all can run this device.  The kernel uses orinocco, by default.

I can't search the contents of the linux-image for PPC package on packages.ubuntu.com right now, for some reason, but I would wonder which driver they use.  I know the prism2 ones work on mac, but I am not sure about orinocco.  I think it's only the usb ones that are troublesome - prism2_usb runs on mac.

Maybe you can build the prism2 drivers and try them?

Does the light come on at all?  I had a similar problem and it was because the PCMCIA system was not being initialised.  It worked on Warty and then stopped working on Hoary.  What is the output of 

find /sys/class/pcmcia_socket


[https://launchpad.net/distros/ubuntu/+source/laptop-detect/+bug/14897](https://launchpad.net/distros/ubuntu/+source/laptop-detect/+bug/14897)

---

### Post by dsierpin on 2006-02-03
Hey guys (most likely)-

Thanks for the replies.  I have to go to work now, but I'll mess around with those other drivers later and see if I can get something going.  Azz, the light does come on.  Here is the output of find /sys/class/pcmcia_socket:

```
david@ubuntu:~$ find /sys/class/pcmcia_socket
/sys/class/pcmcia_socket
/sys/class/pcmcia_socket/pcmcia_socket0
/sys/class/pcmcia_socket/pcmcia_socket0/device
/sys/class/pcmcia_socket/pcmcia_socket0/available_resources_mem
/sys/class/pcmcia_socket/pcmcia_socket0/available_resources_io
/sys/class/pcmcia_socket/pcmcia_socket0/available_resources_setup_done
/sys/class/pcmcia_socket/pcmcia_socket0/card_irq_mask
/sys/class/pcmcia_socket/pcmcia_socket0/card_eject
/sys/class/pcmcia_socket/pcmcia_socket0/card_insert
/sys/class/pcmcia_socket/pcmcia_socket0/card_vcc
/sys/class/pcmcia_socket/pcmcia_socket0/card_vpp
/sys/class/pcmcia_socket/pcmcia_socket0/card_voltage
/sys/class/pcmcia_socket/pcmcia_socket0/card_type

```

---

### Post by az on 2006-02-03
[QUOTE=dsierpin]Hello! 

I just bought that same card.  It shows up as eth1 next to my ethernet card.  Shouldn't it be wlan0?[/QUOTE]
No.  The orinoco pcmcia driver makes an ethx device.

[QUOTE=dsierpin]
Tells me that the argument "monitor" is invalid.  The card has a prism chipset, and I know it is capable of monitor mode.  Any ideas?[/QUOTE]

You need the hostap driver for monitor mode.  To use monitor mode with the prism driver, you need to buy the firmware from intersil.  The hostap implements monitor mode in the software.

---

### Post by dsierpin on 2006-02-07
Hello again-

I can't get the card recognized with the hostap driver :confused: I downloaded the latest stable version (0.4.7) from hostap.epitest.fi/, gunzipped it, edited the Makefile so that KSRC pointed to my kernel at /usr/src/linux, entered the directory and did "make" and "sudo make install".  Everything seemed to work without a problem, but iwconfig gives:

```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

ppp0      no wireless extensions.

```

Ejecting and reinserting, rebooting does no good.  I tried installing from the source code that's in the repos according to [zencoder's howto]("http://www.ubuntuforums.org/showthread.php?t=126229&highlight=howto+hostap"), but the same thing happened: everything went fine but my card  was still not recognized.  Any ideas?  I'm stumped.  Is there anyone out there who has gotten this card to work with the hostap driver?

---

### Post by dsierpin on 2006-02-21
I don't know how, but the card works fine with hostap now  \\:D/ .

Just rebooted a few times, and when I took a look at iwconfig, why, I had a wifi0 and a wlan0, neat as you please :-k .

---

### Post by tgoins on 2006-02-21
Howdy all,

Having searched through the forums I can't seem to find an answer to the issues that I am having with my MA401 Card. I am running a Gateway 9200 solo laptop with ubuntu 5.10 installed. The system works great and runs beautifully but the device manager shows that there is a card installed in the pcmcia slot but cannot identify the make model etc. Is there a way to force the hardware recognition and load up a compatable driver and get this card functioning? Thanks.

Tim

---

### Post by az on 2006-02-21
[QUOTE=tgoins]Howdy all,

Having searched through the forums I can't seem to find an answer to the issues that I am having with my MA401 Card. I am running a Gateway 9200 solo laptop with ubuntu 5.10 installed. The system works great and runs beautifully but the device manager shows that there is a card installed in the pcmcia slot but cannot identify the make model etc. Is there a way to force the hardware recognition and load up a compatable driver and get this card functioning? Thanks.

Tim[/QUOTE]
Do you have the ubuntu-desktop package installed?  Do the lights come on when you plug it in?

Show the output of
tail -f /var/log/messages
when you plug in the card.  (run the command, then plug in the card)

---


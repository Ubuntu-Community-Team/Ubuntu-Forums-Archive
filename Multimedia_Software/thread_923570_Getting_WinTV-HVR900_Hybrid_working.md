---
title: "Getting WinTV-HVR900 Hybrid working"
date: 2008-09-18
forum: Multimedia Software
---

### Post by gardara on 2008-09-18
I am trying to get a usb connected Hauppauge WinTV-HVR900 Hybrid working.
I followed this manual: [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices) but kaffine didn't recognize my card.

```
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: Invalid Service : basket_config_features.desktop
kio (KService*): WARNING: Invalid Service : basket_config_notes.desktop
kbuildsycoca: WARNING: Parse error in /home/gardar/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kbuildsycoca: WARNING: Parse error in /home/gardar/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu, line 1, col 1: unexpected end of file
kio (KService*): WARNING: Invalid Service : googleearth.desktop
kio (KService*): WARNING: The desktop entry file UltraMixer/UltraMixer on the web.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : UltraMixer/UltraMixer on the web.desktop
kio (KService*): WARNING: Invalid Service : /home/gardar/.local/share/applications/googleearth.desktop
DCOP Cleaning up dead connections.
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Any idea what's wrong? Am I maby using the wrong drivers or firmware?

---

### Post by gardara on 2008-09-19
seems like the hvr-900h isn't supported yet

[QUOTE=http://www.hauppauge.com/site/support/linux.html]Linux support for the WinTV-HVR-900 series will be in the upcoming kernel 2.6.26 release. Work is under way for the WinTV-HVR-900H. [/QUOTE]

I sent them a mail asking for ETA.. Let's hope it's soon...
But while I wait, could I use ndiswrapper or something to emulate the windows driver?

---

### Post by gardara on 2008-09-27
Bump! No one that has an idea?

---

### Post by cynop on 2008-11-17
Bump! i'm sure lot's of people will be interested in this, as the product get's a bigger base

---

### Post by con on 2008-11-22
I've just got one of these, I upgraded to 8.10 as the newer kernel is supposed to support it but I haven't been able to get it to work. Apparently the appropriate kernel module is available. 

There are instructions available for getting it to work on older kernels but surely it should be possible to get it working without modifying the new kernel.

I ran sudo modprobe em28xx and plugged the device in but no application seems to be able to use it. Below is the output from dmesg and lsusb if its of any help.

[   32.412322] Registered led device: iwl-phy0:radio                                                                
[   32.412512] Registered led device: iwl-phy0:assoc                                                                
[   32.412635] Registered led device: iwl-phy0:RX                                                                   
[   32.412750] Registered led device: iwl-phy0:TX                                                                   
[   32.498154] NET: Registered protocol family 17                                                                   
[   75.998003] process `skype' is using obsolete setsockopt SO_BSDCOMPAT                                            
[   79.766352] NET: Registered protocol family 10                                                                   
[   79.768001] lo: Disabled Privacy Extensions                                                                      
[   79.772474] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                        
[   89.952050] eth0: no IPv6 routers present                                                                        
[  185.771633] usb 7-1: USB disconnect, address 2                                                                   
[  188.940206] usb 7-1: new high speed USB device using ehci_hcd and address 5                                      
[  189.078791] usb 7-1: configuration #1 chosen from 1 choice                                                       
[  212.742273] usb 7-1: USB disconnect, address 5                                                                   
[  220.181618] em28xx v4l2 driver version 0.1.0 loaded                                                              
[  220.181721] usbcore: registered new interface driver em28xx                                                      
[  233.068154] usb 7-1: new high speed USB device using ehci_hcd and address 6
[  233.206789] usb 7-1: configuration #1 chosen from 1 choice
conor@conor-laptop:~$ cd /dev/dvb
bash: cd: /dev/dvb: No such file or directory
conor@conor-laptop:~$ lsusb
Bus 007 Device 006: ID 2040:6600 Hauppauge
Bus 007 Device 004: ID 0471:082d Philips
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by con on 2008-11-22
I've found out what my problem is. The retail box was says "HVR 900" but the device itself is a "HVR 900H". They've got two different chipsets and the HVR 900H doesn't seem to work at all under Linux.

[http://www.hauppauge.com/site/support/linux.html](http://www.hauppauge.com/site/support/linux.html)

---

### Post by gardara on 2008-11-24
Yeah it really sucks... I bought my card in september, and assumed it would work with linux so I didn't check it.
The hauppauge page says > Work is under way for the WinTV-HVR-900H. 

and has been doing so since I bought my card... And they haven't replied my emails asking about ETA.

My card has just been lying on my table and collecting dust since september.

I still have to check if it's possible to use ndiswrapper and emulate windows drivers.... Have you looked at ndiswrapper con?

---

### Post by garvint on 2009-03-04
has anything developed with the hvr 900h?

The Hauppauge site says that work is still under way!

Did you get the windows drivers to run in linux or is there another option that can be implemented?

---

### Post by cstoh on 2009-05-08
Hello everybody. Does anyone out there know if there has been any development in this area?

Thanks and thanks again

---

### Post by MatsK on 2009-05-10
> **cstoh said:**
> Hello everybody. Does anyone out there know if there has been any development in this area?

Thanks and thanks again

Do like me, mail them. Many requests = higher probability that they get their thumb out of their mouth and start writing code....


/M

---

### Post by garvint on 2009-05-12
have sent request today, so hopefully in 2 days will get reply.

---

### Post by MatsK on 2009-05-12
Nice !

> I got this answer, You will need to check on the [www.linuxtv.org](www.linuxtv.org) website.

But linuxtv doesn't have a working driver yet.

So lets keep the pot boiling and bombard them with request/questions....


/Mats

---

### Post by cstoh on 2009-05-15
> **MatsK said:**
> Do like me, mail them. Many requests = higher probability that they get their thumb out of their mouth and start writing code....


/M

How to mail them? Any email or snail mail address?

---

### Post by MatsK on 2009-05-17
> **cstoh said:**
> How to mail them? Any email or snail mail address?

Check their website.

/M

---

### Post by keiffee30 on 2009-06-14
Hi guys....

I too have got this USB from PC World and have got the same problems. I have been looking at all the posts and i have just emailed Hi support on 

   [B] *   Tech Support:
    * +44 (0) 207 378 0202
    * [email]support@hauppauge.co.uk[/email][/B]

Just in case someone needs to know what the address or number is.... Lets hope that "power to the poeple" will work (i know im old to remember the TV program)

---

### Post by keiffee30 on 2009-06-14
i have just got a email back from the support people ( working on a sunday wow) ok it was a auto reply and they have asked for me to fill out all the support Q's on the website. so here it is 

**[http://www.hauppauge.co.uk/site/support/support_supcontact.html](http://www.hauppauge.co.uk/site/support/support_supcontact.html)**

I hope this helps someone

---

### Post by opensourcederry on 2009-07-23
Found this for 8.10, hopefully should help

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/357568](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/357568)

---

### Post by kosmo90 on 2009-08-17
> **opensourcederry said:**
> Found this for 8.10, hopefully should help

[http://www.gossamer-threads.com/lists/mythtv/mythtvnz/357568](http://www.gossamer-threads.com/lists/mythtv/mythtvnz/357568)

That's the vanilla 900,Has anyone got this card (900h) working yet?

Thanks

---

### Post by R.v.Muilekom on 2009-08-19
Same problems here, bought this usb tv stick today, and finding out it's H version.
Emailed to support, the question if it is ever going to work, or if i get another version (i did buy a plain 900)...:confused:

ps my old internal card was working under linux, and not Windows 7, and this one.. well i think you can guess? <>

Lets keep our fingers crossed.

Greets, Ron

---

### Post by cstoh on 2009-08-20
I emailed them and they said flatly that they don't support Linux.


> **keiffee30 said:**
> i have just got a email back from the support people ( working on a sunday wow) ok it was a auto reply and they have asked for me to fill out all the support Q's on the website. so here it is 

**[http://www.hauppauge.co.uk/site/support/support_supcontact.html](http://www.hauppauge.co.uk/site/support/support_supcontact.html)**

I hope this helps someone

---

### Post by gardara on 2009-08-30
Hey guys.

I gave up and sold my WinTV-HVR900h

I am going to go with the Sundtek MediaTV Pro.

It's supposed to work very well with linux.

[http://sundtek.de/shop/Digital-TV-Sticks-oxid/Sundtek-MediaTV-Pro.html](http://sundtek.de/shop/Digital-TV-Sticks-oxid/Sundtek-MediaTV-Pro.html)


Cheers.

---


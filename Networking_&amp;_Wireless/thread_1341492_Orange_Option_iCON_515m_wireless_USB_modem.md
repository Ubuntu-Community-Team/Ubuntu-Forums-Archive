---
title: "Orange Option iCON 515m wireless USB modem?"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by icheyne on 2009-11-29
I'm running UNR Karmic 9.10 and I'm failing to get my brand new Orange Option iCON 515m wireless USB modem working.

It's not detected automatically and Network Manager can't seem to get it going.

There seems to be a nasty bug with the iCON 255 USB modem, which probably uses the same driver.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418499)

Can anyone help?

---

### Post by alexfish on 2009-11-29
[SIZE=2]hi [/SIZE]

 [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]                                                                                                 [SIZE=2]                          [SOLVED]                          [Re:  Option iCON 515m wireless USB modem (Orange)]("http://ubuntuforums.org/showthread.php?t=1351612")

Follow The  Post Carfully
[/SIZE]

---

### Post by icheyne on 2009-11-30
Hi Alexfish

```

Bus 003 Device 002: ID 0a5c:2150 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 0af0:d157 Option 
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 090c:9371 Feiya Technology Corp. 
```

I had problems, as it was being detected as a USB flash drive, but I was able to get it recognised by taking out the memory card.

---

### Post by alexfish on 2009-11-30
See Below

RE: PHARSCAPE

---

### Post by alexfish on 2009-12-01
I have added this link it is worth reading , may give you an idecation as to why some devices do not work on linux  

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)


it may also help in your choice of device

Regards

 alexfish

ps 
just found some info on this device / but requires loading usb-mode switch  may work

   if it is done from  synaptic  some of the config files may be empty 

       but it will do no harm to install it 

   let me kown if you have done this

---

### Post by alexfish on 2009-12-04
Hi 

 i have look at this  


[http://shop.orange.co.uk/pdf/mobile_broadband/Option515m5-QuickStartGuide.pdf](http://shop.orange.co.uk/pdf/mobile_broadband/Option515m5-QuickStartGuide.pdf)

  its only a comment  'does not give much help on linux 

regards

alexfish

---

### Post by alexfish on 2009-12-05
_Removed Mode Switch_

---

### Post by alexfish on 2009-12-10
See below

---

### Post by alexfish on 2009-12-10
This is a small update to HSOconnect that allows it to work with the iCon 515 as sold by Orange

RE: Pharscape

Install the ozerocdoff utility:
1. Download the udev-icon5x5-pharscape-091208.tar.gz [COLOR=White],,,,,,,,,,,,,,,[/COLOR]                 [[IMG]http://pharscape.org/forum/Themes/pharscape/images/icons/clip.gif[/IMG] udev-icon5x5-pharscape-091208.tar.gz]("http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=39") (25.54 KB - downloaded 3 times.)
2. Untar the file:  tar zxf udev-icon5x5*
3. Change to the udev directory: cd udev*
4. Install the udev rules: sudo make install
5. Reboot (to reload the rules!)

Install hsolinkcontrol: [http://www.pharscape.org/hsolinkcontrol.html](http://www.pharscape.org/hsolinkcontrol.html)

Install hsoconnect:
1. Download the hsoconnect-1.2.19.tar.gz file[COLOR=White] ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,[/COLOR]                                 [[IMG]http://pharscape.org/forum/Themes/pharscape/images/icons/clip.gif[/IMG] hsoconnect-1.2.19.tar.gz]("http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=38") (92.92 KB - downloaded 6 times.)
2. Untar the file : tar zxf hsoconnect*
3. Change to the hsoconnect directory : cd hsoconnect*               
4. Install hsoconnect : sudo make install

To use it: 

1. Disable NetworkManager Wireless (right mouse button menu).
2. Run HSOconnect from the Applications/Internet menu.

Tested with Ubuntu 9.10.
                                                                             [[IMG]http://pharscape.org/forum/Themes/pharscape/images/icons/clip.gif[/IMG] hsoconnect-1.2.19.tar.gz]("http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=38") (92.92 KB - downloaded 6 times.)
                                        [[IMG]http://pharscape.org/forum/Themes/pharscape/images/icons/clip.gif[/IMG] udev-icon5x5-pharscape-091208.tar.gz]("http://www.pharscape.org/forum/index.php?action=dlattach;topic=809.0;attach=39") (25.54 KB - downloaded 3 times.)

The Site

[http://www.pharscape.org/article-1260306492.html?searched=icon+515m&advsearch=oneword&highlight=ajaxSearch_highlight+ajaxSearch_highlight1+ajaxSearch_highlight2](http://www.pharscape.org/article-1260306492.html?searched=icon+515m&advsearch=oneword&highlight=ajaxSearch_highlight+ajaxSearch_highlight1+ajaxSearch_highlight2)

---

### Post by artg on 2009-12-20
Hi alexfish ; thanks for that update.

I've also just got a 515 modem and have installed as above. The only difference is that there was no option to disable wireless on the network manager but since this laptop has no wireless card, that might be normal. I did disconnect physically the ethernet cable. I had previously registered the modem using the Windows app.

On starting up hsconnect all looked pretty good : the modem flashes a blue light and hsoconnect reports a rather low signal strength but reports 'Orange, Registered, UMTS' or Orange, Registered, Edge' with a higher signal strength on 2G.

However, the Connect button pauses for a while, then brings up an error box 'Failed to Connect'. The result is the same on both 2G and 3G.

Any idea what's failing ? 

thanks,

-adrian



Seems I've found the answer : the user & password in HSOconnect needs to be set to the values that can be found in Network manager (orange,orange,orangeinternet). The connection now seems very slow and a bit flaky, but it's working :-)


Spoke too soon - I seem to be experiencing crashes as described in the launchpad article linked by icheyne

---

### Post by alexfish on 2009-12-20
Hi
 Try This code from the terminal and post the results

dmesg | grep -e "modem" -e "tty"

ls -al /dev/ttyU*

Also Check out Read All

                          [Mobile Broadband  can't connect]("http://ubuntuforums.org/showthread.php?t=1331317")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331317") [2]("http://ubuntuforums.org/showthread.php?t=1331317&page=2"))
[URL="http://ubuntuforums.org/showthread.php?t=1331317"]
[/URL]

---

### Post by alexfish on 2009-12-20
Hi

Try This

                                 From The Terminal

Open the file with  

  Code:

 sudo gedit /etc/udev/rules.d/51-hso-udev.rules 

 you need to paste two lines of code in different sections.

First line to paste in the ATTRS section:

Edit id's According to product iCON 515 = d157


  Code:

 ATTRS{idVendor}=="0af0", ATTRS{idProduct}=="d055", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}" 

Second line to paste in the SUBSYSTEM section:

  Code:

 SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0af0", SYSFS{idProduct}=="d055", SYSFS{bDeviceClass}=="00", RUN+="/usr/sbin/ozerocdoff -wi 0x%s{idProduct}" 

Save the file and exit gedit.

[COLOR=Navy] **Enter your APN **[/COLOR]

Use the Profile / Edit Connection menu. All network providers have different APN's  Find out From your 

Provider

Make Sure All Wireless connections Are Disabled

 Run HSOconnect from the Applications/Internet menu.

[SIZE=2][COLOR=Navy]Full Instruction Here[/COLOR][/SIZE]

[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]                                                                                                                           [SOLVED]                          [Re:  Option iCON 515m wireless USB modem (Orange)]("http://ubuntuforums.org/showthread.php?t=1351612")

---

### Post by artg on 2009-12-21
Thanks ; I've sorted out the login stuff, and added those lines to the udev rules. 

The device shows up as ID d157 in lsusb, but there's already a line for that in udev rules. There are no /dev/ttyU* devices, and no modem or tty lines (apart from those for an internal 16550 and for the console) in dmesg.

Hsoconnect can now do a login, but after a short while the connection fails. If I disconnect and shut down before it fails, all is well. If I allow it to fail, then the machine crashes (hangs or fills creen with garbage) when I close it down.

---

### Post by alexfish on 2009-12-23
> **artg said:**
> Hi alexfish ; thanks for that update.

I've also just got a 515 modem and have installed as above. The only difference is that there was no option to disable wireless on the network manager but since this laptop has no wireless card, that might be normal. I did disconnect physically the ethernet cable. I had previously registered the modem using the Windows app.

On starting up hsconnect all looked pretty good : the modem flashes a blue light and hsoconnect reports a rather low signal strength but reports 'Orange, Registered, UMTS' or Orange, Registered, Edge' with a higher signal strength on 2G.

However, the Connect button pauses for a while, then brings up an error box 'Failed to Connect'. The result is the same on both 2G and 3G.

Any idea what's failing ? 

thanks,

-adrian



Seems I've found the answer : the user & password in HSOconnect needs to be set to the values that can be found in Network manager (orange,orange,orangeinternet). The connection now seems very slow and a bit flaky, but it's working :-)


Spoke too soon - I seem to be experiencing crashes as described in the launchpad article linked by icheyne

Hi

Can You Post The

[  When it Crashes ]

The last 20 lines from log viewer / messages

or this command from the terminal

tail -f /var/log/messages



Also This one

dmesg | grep -e "modem" -e "tty"

---

### Post by artg on 2009-12-29
Hi alex,

As noted above, it does work when the uSD card is removed. It's possible that the connection (location on USB, plugged in at boot or later) is also relevant. I will try to work through the variations and find out what's critical.

However, I'm not sure that any useful dmesg output can be gathered as I think it always freezes the machine. I'll try to see if there's any output before it dies.

---

### Post by alexfish on 2009-12-29
> **artg said:**
> Hi alex,

As noted above, it does work when the uSD card is removed. It's possible that the connection (location on USB, plugged in at boot or later) is also relevant. I will try to work through the variations and find out what's critical.

However, I'm not sure that any useful dmesg output can be gathered as I think it always freezes the machine. I'll try to see if there's any output before it dies.

Hi

 the

 dmesg | grep -e "modem" -e "tty"

should show which ports/lines  ie; tty(n) are allocated to the modem , this may indicate that the mode switching is correct :

Reason :  the first is used for data and the second monitoring and control

Added  From the log file viewer We Might See system lines like This

Dec 29 14:44:02 alexfish2-desktop pppd[1800]: Using interface ppp0
Dec 29 14:44:02 alexfish2-desktop pppd[1800]: Connect: ppp0 <--> /dev/ttyUSB1
[COLOR=Red]Dec 29 14:44:02 alexfish2-desktop kernel: [   89.040110] PPP BSD Compression module registered
Dec 29 14:44:02 alexfish2-desktop kernel: [   89.073236] PPP Deflate Compression module registered[/COLOR]

---


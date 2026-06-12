---
title: "Connecting ubuntu 7.10 computer to the internet using SE 580i phone Modem"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by charliebanda on 2010-03-09
Hi everybody,

I have just installed ubuntu 7.10 on my computer. The problem is getting it connected to the internet using my Sony Ericsson w580i as a modem. I have used my phone to connect to the internet on XP operating system easily. Please assist me and try to give me a more simplified step by step procedure. 

Thanks for your help in advance.

Charlie

---

### Post by GeorgeVita on 2010-03-09
Hi **charliebanda**, welcome to this forum!

Are you sure that you installed Ubuntu **[size=3]7[/size]**.10 or the latest version 9.10?

Regards,
George

---

### Post by charliebanda on 2010-03-11
Hi George,

thanks for your tips. I am sure ,I installed ubuntu 7.10. I would like to have the latest 9.10 when I can. If anybody has a cd of ubuntu 9.10 and wants to give it away, I would like if he or she  can just post it to  [COLOR=DarkGreen]**Charles Banda ,Box 160, Madisi. Dowa. Malawi**[/COLOR] (Cellphone: +265999277677) plus any additional multimedia Ubuntu software cds if available. 

For now let me say, I downloaded ***wvdial_1.60.1+nmu2_i386.deb*** and ***network-****manager_0.7.1~rc4.1.cf199a964-0ubuntu2_i386.deb*** using xp operating system and booted my Ubuntu OS then copied the two softwares on the desktop. When I double clicked them they did show a progress just for a little while and then reported the following error  	:[COLOR=Red]*Dependency is not satisfiable: libuniconf4.4 *[COLOR=Black]and [/COLOR]*Dependency is not satisfiable: libdbus-glib-1-2.  *[COLOR=Black]am I going about it the right way?
  
 thanks

CharlieBanda
[/COLOR][/COLOR]

---

### Post by charliebanda on 2010-03-11
Hi George,

thanks for your tips. I am sure ,I installed ubuntu 7.10. I would like to have the latest 9.10 when I can. If anybody has a cd of ubuntu 9.10 and wants to give it away, I would like if he or she  can just post it to  [COLOR=DarkGreen]**Charles Banda ,Box 160, Madisi. Dowa. Malawi**[/COLOR] (Cellphone: +265999277677) plus any additional multimedia Ubuntu software cds if available. 

For now let me say, I downloaded ***wvdial_1.60.1+nmu2_i386.deb*** and ***network-****manager_0.7.1~rc4.1.cf199a964-0ubuntu2_i386.deb*** using xp operating system and booted my Ubuntu OS then copied the two softwares on the desktop. When I double clicked them they did show a progress just for a little while and then reported the following error  	:[COLOR=Red]*Dependency is not satisfiable: libuniconf4.4 *[COLOR=Black]and [/COLOR]*Dependency is not satisfiable: libdbus-glib-1-2.  *[COLOR=Black]am I going about it the right way?
  
 thanks

CharlieBanda
[/COLOR][/COLOR]

---

### Post by sports fan Matt on 2010-03-11
Hi Charlie,

If you have a blank disc (I use cdr's) you could burn 9.10 using Brasero located in Symnaptic or add and remove programs.  It I think would be easier then waiting for a disc.  I have heard of changing what is known as your "sources list" but I am not sure if even you changed this to gutsy which is the codename for 7.10, it would work.

---

### Post by GeorgeVita on 2010-03-11
Hi **charliebanda** and **sox fan Matt**,
if I understood correctly the only internet connection is the mobile one (phone as modem) so a complete CD download is impossible.

>>> 7.10 has wvdial pre-installed (which is missing on 9.04 and 9.10)

One possible solution is to try 'Connecting ubuntu 7.10 computer to the internet using SE 580i phone Modem', so do the following:

- Boot Ubuntu without the phone/modem connected
- open a terminal window and try: **sudo dmesg -c**
this will show all system activity till then and will 'clear' this log. Next **dmesg** (without -c) will show only 'new' activity
- from terminal: **lsusb**
- attach phone/modem
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**

- Check for any changes comparing 'lsusb' outputs. The 'new line' is your phone/modem.
- Search within second 'dmesg' for any driver used or any communication port created (ttyUSB0 ?)

Post any new data to follow up, but DO NOT post output of the 'sudo dmesg -c' as this is huge and without data for your phone/modem!

Regards,
George

---

### Post by charliebanda on 2010-03-12
Hi George,

I tried to follow your instructions. what I got is pasted below. Did I follow right? What next?

	 	 charles@charles-desktop:~$ dmesg  
 charles@charles-desktop:~$ lsusb  
 Bus 004 Device 001: ID 0000:0000   
 Bus 003 Device 001: ID 0000:0000   
 Bus 002 Device 001: ID 0000:0000   
 Bus 001 Device 007: ID 1c4f:0003   
 Bus 001 Device 001: ID 0000:0000   
 charles@charles-desktop:~$ dmesg  
 [ 1387.987716] usb 3-1: new full speed USB device using uhci_hcd and address 2  
 [ 1388.169656] usb 3-1: configuration #3 chosen from 1 choice  
 [ 1388.948213] cdc_acm 3-1:3.1: ttyACM0: USB ACM device  
 [ 1388.951809] cdc_acm 3-1:3.3: ttyACM1: USB ACM device  
 [ 1388.954346] usbcore: registered new interface driver cdc_acm  
 [ 1388.954778] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters  
 [ 1389.095137] usb0: register 'cdc_ether' at usb-0000:00:1d.2-1, CDC Ethernet Device, 02:80:37:ff:02:00  
 [ 1389.095560] usbcore: registered new interface driver cdc_ether  
 charles@charles-desktop:~$ lsusb  
 Bus 004 Device 001: ID 0000:0000   
 Bus 003 Device 002: ID 0fce:d089 Sony Ericsson Mobile Communications AB  
 Bus 003 Device 001: ID 0000:0000   
 Bus 002 Device 001: ID 0000:0000   
 Bus 001 Device 007: ID 1c4f:0003   
 Bus 001 Device 001: ID 0000:0000   
 charles@charles-desktop:~$ 



CharlieBanda

---

### Post by charliebanda on 2010-03-12
Hi [B]sox fan Matt,

I am completely new to ubuntu. I have no source [/B]** for ubuntu 9.10 **[B]other than downloading it from the internet. But the nature of my internet connection makes it almost impossible to download the whole cd data considering the time and cost that would be involved. For now a cd from somewhere would help. Nevertheless I still want to get the 7.10 ubuntu connected to the Web. When I get the 9.10, it will be just a climb higher.

Charlie
[/B]

---

### Post by charliebanda on 2010-03-13
Hi George and Everyone,

This morning has been amazing. I have successfully configured and connected my Ubuntu 7.10 to the internet. I am actually posting this post using ubuntu operating system 7.10. it's great! The info I got  from the terminal window , the modem info etc has helped me to configure the settings. **Thank you George** for telling me about the terminal window which I didn't even knew it existed. I am connected what a feeling!  Any additional tips are much welcome. Getting the 9.10 and getting more applications will be my next goal. Thanks for your contributions, George and everyone. 

CharlieBanda

---

### Post by GeorgeVita on 2010-03-13
Hi **charliebanda**, so you have good news!

Nou use your 'Ubuntu 7.10 mobile connection' to ask a newer version CD at:
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Regards,
George

---

### Post by davidevb6 on 2013-04-29
Hi Charly, i'm in Malawi now, i would to call you if you are allerady interessed about ubuntu :)
response if ok. TNX
Davide Caminati

---

### Post by howefield on 2013-04-29
Rather old thread closed.

---


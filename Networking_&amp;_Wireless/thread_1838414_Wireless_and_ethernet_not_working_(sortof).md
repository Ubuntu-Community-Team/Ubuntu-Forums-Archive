---
title: "Wireless and ethernet not working (sortof)"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by tjw921 on 2011-09-03
Hi,
 
I just installed 11.04 on an old thinkpad t40 it went well however I am having issues with internet connectivity. The hardware seems to be working as it detects my wireless network and it detects the network when I connect an ethernet cable however after trying to connect it just says you are now disconnected. Im a linux newbie and any help you guys can provide would be much appreciated.

---

### Post by josephmills on 2011-09-03
Hi there and Welcom to Ubuntu fourms ! 

lets take a better look at you hardware first before making any choices 
please open your terminal (ctrl+alt+t) then type in 


```
lspci -nn 
``````
lsusb
``````
rfkill list all  
``````
lsmod
``````
cat /etc/modprobe.d/blacklist.conf
```  then paste here thanks

---

### Post by tjw921 on 2011-09-03
Ok, so I got the wired connection to work by just resetting my cable modem. But alas no such luck with the router. I hope I did this right and all this is what you were looking for. Thanks so much for the help



 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)
taylor@taylor-ThinkPad-T40:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rfkill list all
this didnt produce anything

 lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
sha256_generic         20911  2 
dm_crypt               22463  1 
pcmcia                 39671  0 
cryptd                 19801  0 
aes_i586               16956  83 
aes_generic            38023  1 aes_i586
thinkpad_acpi          73750  0 
snd_seq_midi           13132  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_rawmidi            25269  1 snd_seq_midi
nsc_ircc               23199  0 
irda                  185091  1 nsc_ircc
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27230  0 
airo                   73165  0 
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia_rsrc            18292  1 yenta_socket
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
crc_ccitt              12595  1 irda
snd                    55295  12 thinkpad_acpi,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
parport_pc             32111  1 
shpchp                 32345  0 
psmouse                73312  0 
serio_raw              12990  0 
nvram                  14035  1 thinkpad_acpi
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  4 radeon,ttm,drm_kms_helper
e100                   40108  0 
video                  18951  0 
floppy                 60032  0 
i2c_algo_bit           13184  1 radeon

 cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by josephmills on 2011-09-03
> **tjw921 said:**
> Ok, so I got the wired connection to work by just resetting my cable modem. But alas no such luck with the router. I hope I did this right and all this is what you were looking for. Thanks so much for the help



 lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:00.0 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:00.1 CardBus bridge [0607]: Texas Instruments PCI1520 PC card Cardbus Controller [104c:ac55] (rev 01)
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)
taylor@taylor-ThinkPad-T40:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

rfkill list all
this didnt produce anything

 lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
sha256_generic         20911  2 
dm_crypt               22463  1 
pcmcia                 39671  0 
cryptd                 19801  0 
aes_i586               16956  83 
aes_generic            38023  1 aes_i586
thinkpad_acpi          73750  0 
snd_seq_midi           13132  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_rawmidi            25269  1 snd_seq_midi
nsc_ircc               23199  0 
irda                  185091  1 nsc_ircc
snd_seq_midi_event     14475  1 snd_seq_midi
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27230  0 
airo                   73165  0 
snd_timer              28659  2 snd_pcm,snd_seq
pcmcia_rsrc            18292  1 yenta_socket
joydev                 17322  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
crc_ccitt              12595  1 irda
snd                    55295  12 thinkpad_acpi,snd_intel8x0,snd_ac97_codec,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
parport_pc             32111  1 
shpchp                 32345  0 
psmouse                73312  0 
serio_raw              12990  0 
nvram                  14035  1 thinkpad_acpi
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
radeon                900494  2 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  4 radeon,ttm,drm_kms_helper
e100                   40108  0 
video                  18951  0 
floppy                 60032  0 
i2c_algo_bit           13184  1 radeon

 cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac



umm... I am alittle bit stumped 
02:02.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]

is you wireless card and it needs the mod or driver 
airo                   73165  0 

which is loaded 

is this a wpa2 conection? If it is can you drop to wpa ? and see if it works? I know that you dont want to spit out any more info but could we please see a 
```
dmesg | grep airo
```

please take out this line 
   13.000588] airo(eth1): MAC enabled **:**:**:**:**

so we can not see it.

---

### Post by northd_tech on 2011-09-03
Let's also see the output of this Ubuntu terminal command:

```
lsusb
```

There is a different command for PCMCIA laptop wireless that I can't remember, but I've posted recently here on Ubuntuforums about that one- I think that wildmanne39? and I were working on that (but PCMCIA cards are VERY rare nowadays...)

---

### Post by tjw921 on 2011-09-03
Im sorry I dont know what WPA or WPA2 is or how to change it. But no worries on posting info Im just thankful for the help. If youll tell me how to check/change the WPA/WPA2 thing Id be happy to do it!

dmesg | grep airo
[   10.742999] airo(): Probing for PCI adapters
[   10.743070] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.743098] airo(): Found an MPI350 card
[   12.393094] airo(eth1): Firmware version 5.41.00
[   12.393098] airo(eth1): WPA supported.
[   12.393102] airo(eth1): MAC enabled *******************
[   12.394504] airo(): Finished probing for PCI adapters

---

### Post by tjw921 on 2011-09-03
Here is the output for lsusb and yeah they are rare this is an old pc lol I bought it for 15 bucks to run some simple software for work. Thanks again for the help!



lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by nm_geo on 2011-09-03
How about this one tj

```
nm-tool
```

If it say you don't have it installed follow the instruction.

---

### Post by tjw921 on 2011-09-03
Here ya go!


NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             connected
  Default:           yes
  HW Address:        *********************

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         *************
    Prefix:          19 (***************)
    Gateway:         *************

    DNS:             *****************
    DNS:            ****************


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             disconnected
  Default:           no
  HW Address:        **********************

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 
    Belkin_G_Wireless_395D0B: Infra, 94:44:52:39:5D:0B, Freq 2437 MHz, Rate 54 Mb/s, Strength 23

---

### Post by josephmills on 2011-09-03
> **tjw921 said:**
> Im sorry I dont know what WPA or WPA2 is or how to change it. But no worries on posting info Im just thankful for the help. If youll tell me how to check/change the WPA/WPA2 thing Id be happy to do it!

dmesg | grep airo
[   10.742999] airo(): Probing for PCI adapters
[   10.743070] airo 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   10.743098] airo(): Found an MPI350 card
[   12.393094] airo(eth1): Firmware version 5.41.00
[   12.393098] airo(eth1): WPA supported.
[   12.393102] airo(eth1): MAC enabled *******************
[   12.394504] airo(): Finished probing for PCI adapters
Awesome job at editing that text !
:P

ok so to change you security level there are a couple of ways to do this 
one 
call you isp and ask them to help with this 
two 

click on the network managers icon the thing that looks like a up and down arrow when you ethernet cable is pluged in then select "connection information" 
now do you see the one that says "default route" now copy the number only and open firefox and put it into your browser. you will be asked for a username and also a pass word. they are admin and password or password password or admin admin. play with the teo words. there is also a site that lists all default password by isp and by router. 
Once you are "in" you then go to your wireless wizard or something to that nature and re-set up you configuration so that you are using wpa. if you still dont have that think about no encription ONLY DO THIS AS A TEST no matter what it is better to pay 40 dollors for this [http://www.google.com/products/catalog?ds=pr&pq=alfa+wireless&hl=en&sugexp=gsis,i18n%3Dtrue&cp=17&gs_id=c&xhr=t&q=alfa+wireless+2000mw&client=ubuntu&channel=fs&biw=1366&bih=574&gs_upl=&bav=on.2,or.r_gc.r_pw.&um=1&ie=UTF-8&tbm=shop&cid=16484229304999046118&sa=X&ei=TuxiTrjHJsPe0QGZnNi3Cg&sqi=2&ved=0CG4Q8wIwAg](http://www.google.com/products/catalog?ds=pr&pq=alfa+wireless&hl=en&sugexp=gsis,i18n%3Dtrue&cp=17&gs_id=c&xhr=t&q=alfa+wireless+2000mw&client=ubuntu&channel=fs&biw=1366&bih=574&gs_upl=&bav=on.2,or.r_gc.r_pw.&um=1&ie=UTF-8&tbm=shop&cid=16484229304999046118&sa=X&ei=TuxiTrjHJsPe0QGZnNi3Cg&sqi=2&ved=0CG4Q8wIwAg)

then it is to use no security. but is it works with no evcription there is the  bug in the jar. but please if it works with out encyription  just us you cable untill you can get a new wireless usb   also you can log a bug with launchpad.net

---

### Post by nm_geo on 2011-09-03
Look like the GUI to the Belkin wireless AP may be

 [http://192.168.2.1](http://192.168.2.1)

Still googling for more info..

---

### Post by tjw921 on 2011-09-03
Thanks! :P I get nothing when typing the default route in the browser. Isnt that to access router settings? Im bypassing my router and going from my cable modem straight to the pc with the cable. It almost seems like the problem is with the router but the wireless is working fine on my windows machine and my fedora machine. Also Im in an apartment and it finds several unsecured networks other than mine but just wont complete a connection with any of them. I hope this helps! Thanks again!

---

### Post by nm_geo on 2011-09-03
> **tjw921 said:**
> Thanks! :P I get nothing when typing the default route in the browser. Isnt that to access router settings? Im bypassing my router and going from my cable modem straight to the pc with the cable. It almost seems like the problem is with the router but the wireless is working fine on my windows machine and my fedora machine. Also Im in an apartment and it finds several unsecured networks other than mine but just wont complete a connection with any of them. I hope this helps! Thanks again!

That is the access to the wireless router yes.. That is what joseph was telling you how to do.. You can just attach a ethernet cable to an powered up wireless router and change things, but if your wireless works on windows you might not want to monkey with the security settings.  WEP is not as good as WPA and WPA is not as good as WPA2... Someday there will be even more better ones.

Our concern is that you driver modinfo tells us that is runs under WPA with no mention of WEP.

By the way, you should be able to plug that ethernet cable into the wireless AP if it has a few ports and do the same thing that you are doing directly to the DSL modem.

---

### Post by tjw921 on 2011-09-03
I know Im probably being stupid here and Im sorry for that but how do I access the wireless router when my computer wont connect to it?

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> I know Im probably being stupid here and Im sorry for that but how do I access the wireless router when my computer wont connect to it?

You most certainly are not stupid.. The same ethernet cable that you have plugged into the computer and now directly into the DSL modem.. The DSL end can be moved to the wireless router if it is powered up you could then connect to the wireless router directly.. BUt if you change things in it all device and os like windows will be changed.

I know this because i upgrade one of my wireless router today.. With ethernet cable and dd-WRT a firmware that gives me more options in my linksys wrt54gl wireless router.

---

### Post by josephmills on 2011-09-04
> **tjw921 said:**
> I know Im probably being stupid here and Im sorry for that but how do I access the wireless router when my computer wont connect to it?
this depends on the type of router that that it is. 
                                                                                            [IMG]http://2.bp.blogspot.com/_BgoH3wcjfmQ/TQcmYSTo-CI/AAAAAAAAACY/ARp0Riqto3M/s1600/Network%252520Diagram%252520A.jpg[/IMG]

---

### Post by tjw921 on 2011-09-04
Thanks but I feel pretty stupid right now. lol I have a cisco Linksys wrt120n wireless-n home router. Do I put the cable in the input socket or one of the output sockets (one is labled internet and four as just ethernet) And when I do that what do I type in the browser address bar? The default route in the network manager is going to be for the cable modem right? Do i just google what the address is for my specific router?

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> Thanks but I feel pretty stupid right now. lol I have a cisco Linksys wrt120n wireless-n home router. Do I put the cable in the input socket or one of the output sockets (one is labled internet and four as just ethernet) And when I do that what do I type in the browser address bar? The default route in the network manager is going to be for the cable modem right? Do i just google what the address is for my specific router?

Now i feel stupid... Are we dealing with Belkin or Linksys?  I have a desktop tied to my wireless Linksys it runs as ethernet connected, and i zing into it all the time with 
192.168.1.1..

Lost One to Lost Two LOL

Yes you can plug into the ethernet ports and access a wireless router... What are we trying to fix?

---

### Post by josephmills on 2011-09-04
> **tjw921 said:**
> Thanks but I feel pretty stupid right now. lol I have a cisco Linksys wrt120n wireless-n home router. Do I put the cable in the input socket or one of the output sockets (one is labled internet and four as just ethernet) And when I do that what do I type in the browser address bar? The default route in the network manager is going to be for the cable modem right? Do i just google what the address is for my specific router?


:KS:KSYOU ARE AWESOME :KS:KS

google this to see the manuals that are avilable on-line 

```
inurl:Linksys wrt120n filetype:pdf 
``` 

Linksys wrt120n



this will work with ddwrt ?? 

[http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router](http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router)
I dont know if it is will work with yours looks areound 
[http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)

---

### Post by nm_geo on 2011-09-04
> **josephmills said:**
> :KS:KSYOU ARE AWESOME :KS:KS



Linksys wrt120n



this will work with ddwrt ?? 

[http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router](http://lifehacker.com/178132/hack-attack-turn-your-60-router-into-a-600-router)
I dont know if it is will work with yours looks areound 
[http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)

Please do not go there right now Joseph LOL.. dd-WRT is some cool firmware but used incorrectly and your router becomes a brick.. I am trying to get a road warrior VPN going that I can access anywhere in the world back to my home network..  By the way that drawing is much better ..

---

### Post by tjw921 on 2011-09-04
Lol its a linksys by cisco router but the wireless card in the pc is belkin. I dug around and found a second ethernet cable and finally got to the router settings but now I see nothing about wpa wpa2 or wep... What should I change???? I dont really want to change firmware joseph I run 12 machines on this router and dont wanna have to do this for each one! lol thanks again both of you are being really awesome!

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> Lol its a linksys by cisco router but the wireless card in the pc is belkin. I dug around and found a second ethernet cable and finally got to the router settings but now I see nothing about wpa wpa2 or wep... What should I change???? I dont really want to change firmware joseph I run 12 machines on this router and dont wanna have to do this for each one! lol thanks again both of you are being really awesome!

That is what I am telling you..  If you change the wireless security it will affect all devices that run through it.

---

### Post by tjw921 on 2011-09-04
So what do I do to make wireless work on this machine??? lol is ubuntu just not meant for me? *pulls hair out* :P

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> So what do I do to make wireless work on this machine??? lol is ubuntu just not meant for me? *pulls hair out* :P

We need to see what the laptop sees when it scans.

I thought nm-tool would give us that ..

maybe 

```
sudo iwlist scan
```

Did you crop off the nm-tool output?

 I attached a screenshot of my wireless security page (just for information)

---

### Post by josephmills on 2011-09-04
> **nm_geo said:**
> 

 I attached a screenshot of my wireless security page (just for information)
gnome 3 with ddwrt  looking real good bro you ever think about manta as a browers 
[http://www.getmantra.com/](http://www.getmantra.com/)

---

### Post by tjw921 on 2011-09-04
WOW I told you Im stupid!!! lol My security settings are all disabled I thought you guys were talking about something else. I know its not the smartest thing to do but I keep it disabled in case my neighbors dont have internet. No I didnt crop anything I did replace numbers that looked like identifying addresses with *s but thats it. here is the output you asked for: 







sudo iwlist scan
[sudo] password for taylor: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: ***************************
                    ESSID:"cxyk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-33 dBm  Noise level:0 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100

wifi0     Scan completed :
          Cell 01 - Address: ****************************
                    ESSID:"cxyk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-38 dBm  Noise level:0 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100

---

### Post by tjw921 on 2011-09-04
One thing Ive noticed is that when I first boot the machine there is a list of available wireless networks in the network manager but after a few  min that all goes away and the only way I can find to get it to detect networks again is to reboot???????????????????????? Does that mean anything?

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> WOW I told you Im stupid!!! lol My security settings are all disabled I thought you guys were talking about something else. I know its not the smartest thing to do but I keep it disabled in case my neighbors dont have internet. No I didnt crop anything I did replace numbers that looked like identifying addresses with *s but thats it. here is the output you asked for: 







sudo iwlist scan
[sudo] password for taylor: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 68:7F:74:88:86:C1
                    ESSID:"cxyk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-33 dBm  Noise level:0 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100

wifi0     Scan completed :
          Cell 01 - Address: 68:7F:74:88:86:C1
                    ESSID:"cxyk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-38 dBm  Noise level:0 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100

Holy Smokes those are some strong numbers.. You must have it right by the AP huh?   Noise level 0 dBm

---

### Post by tjw921 on 2011-09-04
about two feet away lol what does the 0 noise level mean?

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> One thing Ive noticed is that when I first boot the machine there is a list of available wireless networks in the network manager but after a few  min that all goes away and the only way I can find to get it to detect networks again is to reboot???????????????????????? Does that mean anything?

If you click on the AP in network manager what happens? Does it try to connect?
You have basically a free wireless hotspot can i move in next door LOL

---

### Post by tjw921 on 2011-09-04
Yes it does for maybe 2 minutes then it just says wireless network disconnected.  And you sure can!!! You get free internet I get free IT help!!! hahaha Freedom of information right? :p

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> about two feet away lol what does the 0 noise level mean?
Signal to noise ratio means you have strong signal not much noise.

All kidding aside be sure to set a strong password on that router...
We have children who drive around and change settings on wireless router just for fun.. and that 192.168.1.1 is pretty common.

---

### Post by fdrake on 2011-09-04
> **tjw921 said:**
> 

[COLOR="Red"][B][U]eth1      Scan completed :
          Cell 01 - Address: ***************************[/U][/B][/COLOR]
                    ESSID:"cxyk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-33 dBm  Noise level:0 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100

[COLOR="Red"][B][I]wifi0     Scan completed :
          Cell 01 - Address: ****************************[/I][/B][/COLOR]
                    ESSID:"cxyk"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-38 dBm  Noise level:0 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100

something is not right... i may have missed something from the previous post: does he have 2 wireless card? 
can you please post :
```
lshw -c network
less /var/log/syslog | egrep 'wifi0|eth1|radio|etwork' | tail -200 
```

---

### Post by nm_geo on 2011-09-04
At this junction I would think the aironet card is a maybe going south.  You can pick up one of those USB adapters at Walmart or Radio Shack and we can get it going.

In fact chili555, joseph and I are writing up some wikis on them.. Let me see I can give you some links.

 [https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04](https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04)

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG511v2_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG511v2_Natty_11.04)

I just picked up one on Amazon just to see if I could get it running .. Panda Something and yes it works.. Also Netgear 150N.. it works too

---

### Post by nm_geo on 2011-09-04
> **fdrake said:**
> something is not right... i may have missed something from the previous post: does he have 2 wireless card? 
can you please post :
```
lshw -c network
less /var/log/syslog | egrep 'wifi0|eth1|radio|etwork' | tail -200 
```

Oh I bet he is connected by ethernet and wireless scan right now.

 i believe that is just his very strong wireless N router.. and he has an older b speed aironet card that might be going south.  I am not even sure his router is b compatible but his wireless card is b only.

---

### Post by tjw921 on 2011-09-04
fdrake this is the output from the first line

*-network:0 DISABLED    
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:b8:bb:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:c0800000-c09fffff

there was more for ethernet but figured it was unrelated why does it say disabled? 

and  geo no I will never have a password on my wifi information should be free and if some kids change my settings ill just fix them with the help of awesome folks like you guys ;)

and yeah Im starting to think an adapter would be easier!!! lol

---

### Post by nm_geo on 2011-09-04
tj be sure to pull the ethernet out and try the wireless network manager will not let a wireless work if wired is connected.

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> fdrake this is the output from the first line

*-network:0 DISABLED    
       description: Wireless interface
       product: Cisco Aironet Wireless 802.11b
       vendor: AIRONET Wireless Communications
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 00
       serial: 00:02:8a:b8:bb:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical wireless logical
       configuration: broadcast=yes driver=airo latency=64 maxlatency=4 mingnt=4 multicast=yes wireless=IEEE 802.11-DS
       resources: irq:11 ioport:8000(size=256) memory:c0200000-c0203fff memory:c0400000-c07fffff memory:c0800000-c09fffff

there was more for ethernet but figured it was unrelated why does it say disabled? 

and  geo no I will never have a password on my wifi information should be free and if some kids change my settings ill just fix them with the help of awesome folks like you guys ;)

and yeah Im starting to think an adapter would be easier!!! lol

It has been fun maybe fdrake has an idea I am out bro.. It has been a kick.

---

### Post by tjw921 on 2011-09-04
> **nm_geo said:**
> Oh I bet he is connected by ethernet and wireless scan right now.

 i believe that is just his very strong wireless N router.. and he has an older b speed aironet card that might be going south.  I am not even sure his router is b compatible but his wireless card is b only.

I dont know for sure but my settings are set at mixed (b,g, and N) I think it should work and yes im connected by ethernet its the only way I could get into the router settings not to mention on the internet (should I use another machine for these forums and disconnect the ethernet from this one?) O and dont call me a HE!!!! hahahahaha

---

### Post by tjw921 on 2011-09-04
thanks for all your help geo!!!!

---

### Post by nm_geo on 2011-09-04
> **tjw921 said:**
> I dont know for sure but my settings are set at mixed (b,g, and N) I think it should work and yes im connected by ethernet its the only way I could get into the router settings not to mention on the internet (should I use another machine for these forums and disconnect the ethernet from this one?) O and dont call me a HE!!!! hahahahaha
Sorry.. hehehe.. OUT for sure..

---

### Post by fdrake on 2011-09-04
> **nm_geo said:**
> Oh I bet he is connected by ethernet and wireless scan right now.

 i believe that is just his very strong wireless N router.. and he has an older b speed aironet card that might be going south.  I am not even sure his router is b compatible but his wireless card is b only.

that would not be the case, because they are both scanning on channel 6.:confused:

edit:

can you please post
> 
less /var/log/syslog | egrep 'wifi0|eth1|radio|etwork' | tail -200
iwconfig
ifconfig


and also in the meantime while you are connected can you run those updates:
```

sudo apt-get install --reinstall linux-image-$(uname -r)
sudo apt-get install --reinstall linux-headers-$(uname -r)
sudo apt-get install --reinstall linux-backports-modules-cw-2.6.39-natty-generic
sudo aptitude update
sudo aptitude upgrade

```reboot please.
i don't think is a upadate issue but it's always good to get everything updated.

---

### Post by tjw921 on 2011-09-04
less /var/log/syslog | egrep 'wifi0|eth1|radio|etwork' | tail -200
Sep  4 00:40:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> Scheduling stage 5
Sep  4 00:40:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  4 00:40:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> Done scheduling stage 5
Sep  4 00:40:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  4 00:40:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep  4 00:40:01 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep  4 00:40:01 taylor-ThinkPad-T40 NetworkManager[477]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  4 00:40:01 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) successful, device activated.
Sep  4 00:40:01 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  4 00:40:02 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:40:02 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:40:05 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:40:08 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:40:10 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:40:10 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:40:21 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:40:26 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:40:26 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:40:26 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:40:27 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Sep  4 00:40:29 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:40:29 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 5 -> 3 (reason 39)
Sep  4 00:40:29 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): deactivating device (reason: 39).
Sep  4 00:40:29 taylor-ThinkPad-T40 NetworkManager[477]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  4 00:40:29 taylor-ThinkPad-T40 NetworkManager[477]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  4 00:40:31 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Sep  4 00:40:31 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): deactivating device (reason: 40).
Sep  4 00:40:31 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1980
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) starting connection 'Auto cxyk'
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1/wireless): connection 'Auto cxyk' requires no security.  No secrets needed.
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: added 'ssid' value 'cxyk'
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: added 'scan_ssid' value '1'
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: added 'key_mgmt' value 'NONE'
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: set interface ap_scan to 1
Sep  4 00:40:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:40:36 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:40:41 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:40:41 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:40:44 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:40:50 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:40:50 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:40:53 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:40:57 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:40:58 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:40:58 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:41:01 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:41:06 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:41:06 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:41:09 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:41:13 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:41:14 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:41:14 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:41:17 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:41:22 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:41:22 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:41:25 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:41:30 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:41:30 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:41:30 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:41:33 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <warn> Activation (eth1/wireless): association took too long, failing activation.
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 5 -> 9 (reason 11)
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <warn> Activation (eth1) failed for access point (cxyk)
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <info> Marking connection 'Auto cxyk' invalid.
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <warn> Activation (eth1) failed.
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Sep  4 00:41:34 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): deactivating device (reason: 0).
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): carrier now ON (device state 2)
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) starting connection 'Auto eth0'
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> dhclient started with pid 2050
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep  4 00:41:45 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info>   address 192.168.1.103
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info>   prefix 24 (255.255.255.0)
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info>   gateway 192.168.1.1
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info>   nameserver '209.18.47.61'
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info>   nameserver '209.18.47.62'
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info>   domain name 'austin.rr.com'
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Scheduling stage 5
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Done scheduling stage 5
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  4 00:41:46 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep  4 00:41:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep  4 00:41:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  4 00:41:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) successful, device activated.
Sep  4 00:41:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  4 00:45:43 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Sep  4 00:45:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Sep  4 00:45:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): deactivating device (reason: 40).
Sep  4 00:45:47 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2050
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) starting connection 'Auto cxyk'
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1/wireless): connection 'Auto cxyk' requires no security.  No secrets needed.
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: added 'ssid' value 'cxyk'
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: added 'scan_ssid' value '1'
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: added 'key_mgmt' value 'NONE'
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> Config: set interface ap_scan to 1
Sep  4 00:45:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:02 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:07 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:07 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:10 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:18 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:23 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:46:23 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:23 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:26 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:31 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:31 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:34 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:39 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:46:40 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:40 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:43 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:48 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:48 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:51 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:46:55 taylor-ThinkPad-T40 NetworkManager[477]: <warn> (eth1): link timed out.
Sep  4 00:46:56 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  associating -> disconnected
Sep  4 00:46:56 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  disconnected -> scanning
Sep  4 00:46:59 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): supplicant connection state:  scanning -> associating
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <warn> Activation (eth1/wireless): association took too long, failing activation.
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 5 -> 9 (reason 11)
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <warn> Activation (eth1) failed for access point (cxyk)
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> Marking connection 'Auto cxyk' invalid.
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <warn> Activation (eth1) failed.
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Sep  4 00:47:00 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth1): deactivating device (reason: 0).
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): carrier now ON (device state 2)
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) starting connection 'Auto eth0'
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> dhclient started with pid 2128
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Sep  4 00:47:15 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info>   address 192.168.1.103
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info>   prefix 24 (255.255.255.0)
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info>   gateway 192.168.1.1
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info>   nameserver '209.18.47.61'
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info>   nameserver '209.18.47.62'
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info>   domain name 'austin.rr.com'
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Scheduling stage 5
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Done scheduling stage 5
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  4 00:47:16 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep  4 00:47:17 taylor-ThinkPad-T40 NetworkManager[477]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep  4 00:47:17 taylor-ThinkPad-T40 NetworkManager[477]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  4 00:47:17 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) successful, device activated.
Sep  4 00:47:17 taylor-ThinkPad-T40 NetworkManager[477]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-103 dBm
          Rx invalid nwid:21458  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:314950   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-103 dBm
          Rx invalid nwid:21458  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:314950   Missed beacon:0






ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:60:37:8b:21  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe37:8b21/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11364545 (11.3 MB)  TX bytes:2015778 (2.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:8a:b8:bb:dd  
          inet6 addr: fe80::202:8aff:feb8:bbdd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:9997 dropped:0 overruns:0 frame:9997
          TX packets:16 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3668 (3.6 KB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3712 (3.7 KB)  TX bytes:3712 (3.7 KB)

---

### Post by fdrake on 2011-09-04
> 
rfkill list all
[COLOR="Red"]this didnt produce anything[/COLOR]

-network:0[COLOR="Red"]** DISABLED**[/COLOR]
description: Wireless interface
product: Cisco Aironet Wireless 802.11b
vendor: AIRONET Wireless Communications


can you try and see if this changes something:

```

modprobe -r airo
sudo apt-get install --reinstall linux-image-$(uname -r)
sudo apt-get install --reinstall linux-headers-$(uname -r)
sudo apt-get install --reinstall linux-backports-modules-cw-2.6.39-natty-generic
sudo aptitude update
sudo aptitude upgrade
sudo modprobe -v airo
sudo cat >> /etc/modules
airo <press "enter">
<press "ctrl" + "D">
sudo rfkill unblock all
sudo service network-manager restart

```
you may need a restart.

after rebooting 
```

sudo iwconfig eth1 essid cxyk
sudo iwconfig eth1 channel 6
sudo ip link set eth1 up
sudo dhclient eth1

```

---

### Post by vycas on 2011-10-10
Hey all, I am having the similiar problem on my itronix IX260. Its  a old system. I am running XP and Natty on it. Wireless is working flawlessly on XP and no issues of any kind.

In natty my wireless is enabled and i can see my network. But when i try to connect it, it just tries for like 30 seconds and then says disconnected. 

Following is the output of basic commands:


```
 vycas@vycas-IX260:~$ lspci -nn 
``` 
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #3 [8086:2487] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M6 LY [1002:4c59]
03:05.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
03:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
03:07.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
03:08.0 Network controller [0280]: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b [14b9:a504]
```
vycas@vycas-IX260:~$ lsusb
```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
vycas@vycas-IX260:~$ rfkill list all
```
```
vycas@vycas-IX260:~$ lsmod
```
Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
radeon                900494  3 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
ppdev                  12849  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39671  0 
drm_kms_helper         40745  1 radeon
cryptd                 19801  0 
drm                   184164  5 radeon,ttm,drm_kms_helper
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27230  0 
parport_pc             32111  1 
i2c_scmi               12885  0 
airo                   73165  0 
video                  18951  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 radeon
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
8139too                23208  0 
8139cp                 22497  0 
```
vycas@vycas-IX260:~$ cat /etc/modprobe.d/blacklist.conf
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```
vycas@vycas-IX260:~$ dmesg | grep airo
```
[   13.839077] airo(): Probing for PCI adapters
[   13.839389] airo 0000:03:08.0: PCI INT A -> Link[LNKF] -> GSI 11 (level, low) -> IRQ 11
[   13.839436] airo(): Found an MPI350 card
[   15.299415] airo(eth1): Firmware version 5.41.00
[   15.299420] airo(eth1): WPA supported.
[   15.299426] airo(eth1): MAC enabled *****************
[   15.303032] airo(): Finished probing for PCI adapters
```
vycas@vycas-IX260:~$ nm-tool
```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        ****************

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             10.0.0.1


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            airo
  State:             disconnected
  Default:           no
  HW Address:        ******************

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes

  Wireless Access Points 
    Vycas:           Infra, ******************, Freq 2412 MHz, Rate 11 Mb/s, Strength 100

Please note that ```
rfkill
``` gives no output of whatsoever and if i do ```
sudo modprobe airo
``` 
i get:


vycas@vycas-IX260:~$ sudo modprobe airo
[sudo] password for vycas: 
vycas@vycas-IX260:~$ rfkill list all
vycas@vycas-IX260:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr ***************** 
          inet addr:10.0.0.8  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:45ff:fe0c:8648/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2419 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3418326 (3.4 MB)  TX bytes:310693 (310.6 KB)
          Interrupt:11 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr **************  
          inet6 addr: fe80::20e:9bff:fe25:f084/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:28 dropped:0 overruns:0 frame:28
          TX packets:16 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3574 (3.5 KB)
          Interrupt:11 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1600 (1.6 KB)  TX bytes:1600 (1.6 KB)

vycas@vycas-IX260:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-101 dBm  Noise level=-96 dBm
          Rx invalid nwid:797  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1309   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=-101 dBm  Noise level=-96 dBm
          Rx invalid nwid:797  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1309   Missed beacon:0



Please advise.

Vycas

---

### Post by chili555 on 2011-10-10
May we see:```
sudo iwlist eth1 scan
```How many characters are in your WEP key? Is the result the same with the ethernet cable detached? Network Manager will disallow wireless if wired is available.

---

### Post by vycas on 2011-10-10
> **chili555 said:**
> May we see:```
sudo iwlist eth1 scan
```How many characters are in your WEP key? Is the result the same with the ethernet cable detached? Network Manager will disallow wireless if wired is available.

Thanks for helping me chilli.

I am not using any encryption. I am using MAC address filtering on my router. And yes the result is same with network cable detached. Here is the output for the command:


```
vycas@vycas-IX260:~$ sudo iwlist eth1 scan 
```
eth1      Scan completed :
          Cell 01 - Address: 90:E6:BA:BE:CC:04
                    ESSID:"Vycas"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level=-35 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

vycas@vycas-IX260:~$

---

### Post by chili555 on 2011-10-10
Can you confirm that the address listed in your router are the exact same as:> [ 15.299426] airo(eth1): MAC enabled [COLOR="Red"]*****************[/COLOR]As well as:> eth1 Link encap:Ethernet HWaddr [COLOR="Red"]**************[/COLOR]
inet6 addr: fe80::20e:9bff:fe25:f084/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:28 dropped:0 overruns:0 frame:28Also, I wonder if Network Manager is working with eth1 or wifi0. I'm not sure wifi0 gets a MAC assignment.```
sudo cat /var/log/syslog | grep etwork | tail -n25
```Fascinating.

Does it work without MAC filtering but with WEP? I am puzzled by:> [ 15.299420] airo(eth1): WPA supported.But then:> Device: eth1 -----------------------------------------------------------------
Type: 802.11 WiFi
Driver: airo
State: disconnected
Default: no
HW Address: ******************

Capabilities:

Wireless Properties
WEP Encryption: yesNo WPA???

---


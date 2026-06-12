---
title: "No internet with ADSL USB modem"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by Mdyter on 2009-09-24
Hello To All !

Few days ago purchased an ADSL USB Modem , here it is:
Atlantis Land WebRunner Clipper .[IMG]http://eciadsl.flashtux.org/img/eciadsl/modems/modem_atlantis_land_webrunner_clipper.png[/IMG]

I can't make it work on Ubuntu 9.04 (Jaunty Jackalope). 
It even does not blink with ADSL LED.

had found some info about:
[http://eciadsl.flashtux.org/modems.php?lang=en&modem=90](http://eciadsl.flashtux.org/modems.php?lang=en&modem=90)

EciAdsl Linux driver:
modem Atlantis Land WebRunner Clipper
 
Atlantis Land WebRunner Clipper
Manufacturer:    Atlantis Land
Model:    WebRunner Clipper
Status:      Supported
Driver mini:    0.11
Vid1/Pid1:    0915 / 8104
Vid2/Pid2:    0915 / 8104
Country:    Italy
Provider(s):    Infostrada
VPI.VCI:    8.35
Synch .bin:    gs7470_synch20.bin
Chipset:    GS7470
Synch alt:    0
Pppoeci alt:    0
Info:    -



[COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]**General Informations**[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Compliant with USB specification Rev.1.1 (USB V2.0 Legacy mode)[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Conexant[/FONT][/COLOR][COLOR=#000000][FONT=Arial] Centregate™[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Multi-mode support: ANSI T1.143 Issue 2, ITU-T G.992.1 (G.dmt) and ITU-T G.992.2 (G.lite) compliant[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Interoperable with major DSLAM equipment vendors[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Discrete Multi-Tone (DMT) line encoding scheme[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Full-rate transmission at up to 8 Mbps downstream and 1 Mbps upstream[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]G.lite[/FONT][/COLOR][COLOR=#000000][FONT=Arial] transmission at up to 1.5 Mbps downstream and 512 Kbps upstream[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Supports RFC 2364(PPPoA), RFC 2516(PPPoE), RFC 1483 and RFC 1577[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]“Hot” Plug’n’Play Installation[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Easy GUI program for configuration[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Software upgradable for future feature enhancement[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]Interoperable with major DSLAMs[/FONT][/COLOR][/FONT][/COLOR]
 [COLOR=#000000][FONT=Arial][COLOR=#000000][FONT=Arial]External connector: 1 x RJ11 Telephone socket for ADSL and 1 x USB[/FONT][/COLOR][/FONT][/COLOR]


What things can be done?
 
"Lsusb" shows 'Device 002: ID 0915:8104 GlobeSpan, Inc. DSL-200 Modem' .

i'm new to ubu, and i wish to leave XP behind.
sorry for poor English .

---

### Post by Mdyter on 2009-09-25
can help somebody? or i have no chances with my Ubuntu and I'm forced to use m$ ? ((

---

### Post by t0mppa on 2009-09-25
Did you install the Linux driver for it found [here]("http://eciadsl.flashtux.org/download/debian/etch/eciadsl-usermode_0.12-1_i386.deb")?

Also the download page lists 2.6.20 as the last kernel it has been tested on, where as Jaunty (version 9.04 of Ubuntu) runs on 2.6.28 kernel, so there might be some issues with the driver itself.

---

### Post by Mdyter on 2009-09-25
i installed the driver from above. logged off , logged in. runned "ifconfig -a", "lsusb" and "sudo pppoeconf" command to see if are any changes. unplugged usb cable from modem, plugged in and run commands again. nothing changed. adsl led is still off.

What can be done ? please help me

---

### Post by nigamp on 2009-09-26
if your adsl Led is still off dat means u ve a prob with the adsl router irself ...ubuntu does detect ur adsl in lsusb .... 
try configuring VPN ...n give ur MAC address (u can find the MAC add in ipconfig in winXP OR Properties of ur internet connection)
enter ur user name n passwd of ur ISP ...it shud work ...also configure ur IP manually 
hpe it helps

---

### Post by t0mppa on 2009-09-26
Well, you could try running **lshw -C network** from the terminal, if it shows your interface (not sure if it will, as I've never worked with a USB modem before) it will tell you if the drivers are working. Also consulting syslog or dmesg may give you a clue towards possible issues.

---

### Post by Mdyter on 2009-09-26
Thank you guys. But i read a little and decided to change my usb modem for a router. This type of modem is not supported by kernel . anyway , decided to make the change in favor of a router , this should save me from all these problems and save my nerves too )

---


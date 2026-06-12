---
title: "Zoom 4595/4596 3G USB modem configuration"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by dre12b on 2010-03-30
This is a USB GSM broadband modem I recently purchased and need to set up for use on Kubuntu 9.10.  There are some posts providing information for other hardware models, but nothing step-by-step for beginners like me and nothing on this specific make/model.  I'll be experimenting on my own and will keep this thread updated, but any help is greatly appreciated!

FYI Zoom models 4595 and 4596 are the same hardware marketed with different pre-loaded configuration (4596 is set up for USA AT&T network).

---

### Post by dre12b on 2010-04-03
The software developer for usb_modeswitch says the device is working flawlessly now on all distributions.  Download the latest version [here ]("http://www.draisberghof.de/usb_modeswitch/").  I believe ubuntu packages are offering an outdated version, so follow this link rather than using synaptic.

I'm going to test and report back.

---

### Post by dre12b on 2010-04-06
Installed the latest version of usb_modeswitch, including the updated device profiles data from the website.  Enabled the log file and according to the program the Zoom 4595/4596 is being successfully switched.  I did manage to connect using gnome network manager, but had some problems using only wvdial.  Probably some incorrect settings.  In any case, this Zoom device DOES work on ubuntu 9.10.

---

### Post by alexfish on 2010-04-06
Hi dre12b

the latest Debian pkg is here


[LIST]
[*][SIZE=2]Usb ModeSwitch Latest debian Package [/SIZE]1.1.1-1
[*][SIZE=2]
[/SIZE]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package  ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]

if you are looking for other dial up method try Gnome ppp this is a front end to wvdial

basic setup and details have a look here , although your ISP details may differ the site provides some useful info 

[PPP  Connection Utilities]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][The gnome-ppp  dialer utility]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][User  Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")
[*][Permissions  for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")
[*][Adding  the initial Signal Strength to the gnome-ppp connection log ]("http://www.pcurtis.com/ubuntu-mobile.htm#signal_strength")
[/LIST]
[/LIST]

hope these are of some help

regards

alexfish

---

### Post by dre12b on 2010-04-07
Thanks for the tips and the link to the new deb package!  I am depending on another modem for 3g at the moment, so I won't be able to test until I have some free time.

---

### Post by dre12b on 2010-08-09
I just tried the Zoom 4595 on Lucid 10.04 after working successfully with a Huawei modem for several months...and I'm encountering a problem using usb_modeswitch (version 1.1.3 w/ data file 20100707).  The log file for the program reports a successful switch, but neither network manager or ppp-gnome can find the modem.

There's a [thread]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?p=3046#3046") on the Zoom 4595 over at the USB_modeswitch forum.

---

### Post by dre12b on 2010-08-09
I was just able to connect twice using the Sakig3g script.  Script-o-magic.  No idea why this works, but it does.  Hope this is helpful!

[Link]("http://www.sakis3g.org/") to the Sakis3g script.

***Edit*** On the first connection attempt, sakis3g fails, giving an error because modem-manager has a lock on the device (evidently this is why the device won't work with network manager, the device gets locked in with the wrong port number).  Selecting "more options", then "Switch and setup modem", followed by "Connect to 3g" the device connects correctly.  This has worked for me repeatedly over the last few days.  If you suspend or restart, you'll have to repeat this process.

---


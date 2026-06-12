---
title: "Sony Ericsson MD400 modem only works if first initialized in Windows."
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by MiF on 2009-05-25
I have a somewhat strange problem using Ubuntu 9.04 on my Asus Eee PC 1000 and a 3G USB MD400 modem from Sony Ericsson.

When I plug the modem in it is not recognized for what it is. Instead the disk part of it is mounted automatically.

However, I'm using dual-boot and Win XP as well. If I first connect using Windows XP, then reboot into Ubuntu, the modem is detected and works just fine without any additional magic. 

I guess Windows intitializes it in some way, as I'm not even prompted for the PIN. 

In fact I'm online right now using the very same modem in Ubuntu after following the steps outlined above.

Anyone seen this and is there a better way, without having to boot Windows first?

---

### Post by MiF on 2009-05-31
Solved it. This works:

```

sudo usb_modeswitch -v 0fce -p d0e1 -O 1

```

---

### Post by JesperL on 2009-06-06
Hi,

I used this and it worked for me too. But I am trying to make an automatic fix and do not understand why you are using 

-v 0fce -p d0e1... 

 /etc/usb_modeswitch.conf file I have the following:

########################################################
# Sony Ericsson MD400
#
# This is experimental. Might switch back after some time. Please report!

;DefaultVendor=  0x0fce 
;DefaultProduct= 0xd0e1

;TargetClass=    0x02

;SonyMode=1

Thus different vendor and product? How did you know to put -v 0fce -p d0e1?

---

### Post by perseo68 on 2009-11-02
Hi,im new user just installed ubuntu 9.1 on my pc asus 1000,im tryng to connect with sony md400 but not work,i have also installed usb modeswith but nothing,for use my modem i have to start  on windows before,anyone can help me?ty very much

---

### Post by perseo68 on 2009-11-02
please anyone hepl me??? read this pls

 gianluca@gianluca-laptop:~$ sudo usb_modeswitch -v 0fce -p d0el -o1
[sudo] password for gianluca: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

usb_modeswitch: invalid option -- 'o'

---

### Post by matti.se on 2009-11-02
Hi
I have a simular issue. Has MD400 as mobile modem. Worked fine in 9.04 but when I upgraded to 9.10 it stoped to work... The modem workes fine in XP. Any one? I have tried to activate and start it in the same way as i did for 9.04 with no effect. 

Instructions I used that worked for 9.04 (in Swedish but I hope you still understand)
[http://ubuntu.se/forum/showthread.php?t=4587](http://ubuntu.se/forum/showthread.php?t=4587)

Please help! The girlfriend is starting to talk about V__ta.
 
Thanks!

---

### Post by pdc on 2009-11-02
to all of you: 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

there is a bug in 9.10 that seems to stop mobile broadband;

9.04 works, as does 8.10 seem to work 

new software often brings initial problems; some folks wait for the initial bugs to be sorted

---

### Post by perseo68 on 2009-11-03
I have also upload kernel but not work same,what we ca do?any idea?

---

### Post by brydong on 2010-01-18
any updates on this? I'm able to use mode switch so that the device appears as an available network. When I attempt to connect, it fails. Any advice really appreciated.

I'm running 9.10.

I called rogers support which passed me on to Sony support which answered with sorry, mac or windows only.

---

### Post by pdc on 2010-01-18
if you have successfully flipped the device to be seen as a modem

one can suggest you use the programme wvdial; if you google search on it, you can find explanations

to install

> sudo apt-get install wvdial

it should pull in any dependencies

to configure

> wvdialconf      (I forget if you need sudo wvdialconf)

that creates a file wvdial.conf in the /etc directory

you usually need to edit this and add the APN for Rogers ??

go here 

[http://modmyi.com/wiki/index.php/Carrier_APN_Settings#Rogers](http://modmyi.com/wiki/index.php/Carrier_APN_Settings#Rogers)

to read what they are 

looks like the APN setting is 

> internet.com

so if I paste my /etc/wvdial.conf file here to show you


...... but with your APN settings inserted ............. ok?

you can copy and paste this if you want

> [Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800
Dial Attempts = 1
Username = user
Password = pass
Init1 = ATZ
Init2 = AT&F &D2 &C1
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","internet.com"
Phone = *99#
Stupid Mode = 1

I took it straight from a George Vitas post: he knows a lot about this stuff ...........

so you need to make sure your file looks like this
seemingly Rogers does not need username or password so you could try leaving them blank ..............

**_READ IT_** with 

> gedit /etc/wvdial.conf

**_EDIT IT_** with 

> sudo gedit /etc/wvdial.conf

to dial

> sudo wvdial

hopefully lights, action and connection;

mine takes about 2 secs to connect; the script just tumbles out;

and you need to be a member of the dialout and ...I believe .. dip ...... group

---

### Post by brydong on 2010-01-20
awesome, I'm up and running now! Thanks all! This wvdial.conf file was key, [http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html](http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html)

---

### Post by kapcom01 on 2010-03-19
dmesg gives:
```

[   92.900099] usb 1-2: new high speed USB device using ehci_hcd and address 5
[   93.037509] usb 1-2: configuration #1 chosen from 1 choice
[   93.260145] Initializing USB Mass Storage driver...
[   93.263735] usb-storage: device ignored
[   93.263941] usbcore: registered new interface driver usb-storage
[   93.263954] USB Mass Storage support registered.

```
...but running **sudo usb_modeswitch -v 0x0fce -p 0xd103 -O 1** it gives me:
```

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

Looking for default devices ...
 No default device found. Is it connected? Bye.

```

i have ubuntu netbook remix 9.10 and my md400 doesnt even appear as flash drive. The red light turns on for a few seconds when i plug it and then turns off.

can you help me?

---

### Post by pdc on 2010-03-20
not sure I can give the definitive answer;

but you are using usb_modeswitch 1.0.2

.... maybe give yourself the best chance?

the latest version is up to 1.1.1           ........ ????///

so go here

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

as the newer versions automate things ......

and the file you are running assumes the lsusb listing of your device is as you entered it in the command line ........

.......... maybe do

> lsusb

*and check your device has the product ID: device ID that you assume it ha*s .............

(or tell us what lsusb gives you .................................. )

---

### Post by perham on 2010-03-20
> **perseo68 said:**
> please anyone hepl me??? read this pls

 gianluca@gianluca-laptop:~$ sudo usb_modeswitch -v 0fce -p d0el -o1
[sudo] password for gianluca: 

 * usb_modeswitch: tool for controlling "flip flop" mode USB devices
 * Version 1.0.2 (C) Josua Dietze 2009
 * Works with libusb 0.1.12 and probably other versions

usb_modeswitch: invalid option -- 'o'

you have syntax error. it's -O and not -o

sudo usb_modeswitch -v 0fce -p d0el [COLOR="Red"]-O[/COLOR] 1

---

### Post by kapcom01 on 2010-03-22
> **pdc said:**
> not sure I can give the definitive answer;

but you are using usb_modeswitch 1.0.2

.... maybe give yourself the best chance?

the latest version is up to 1.1.1           ........ ????///

so go here

[http://www.draisberghof.de/usb_modeswitch/#download](http://www.draisberghof.de/usb_modeswitch/#download)

as the newer versions automate things ......

and the file you are running assumes the lsusb listing of your device is as you entered it in the command line ........

.......... maybe do



*and check your device has the product ID: device ID that you assume it ha*s .............

(or tell us what lsusb gives you .................................. )

Thanks. you were right that i was using wrong id.. i used the right one that lsusb gave me. Then the network appears in wireless but i can't connect.. and the led isn't flashing like on windows..

I also uninstalled modeswitch and installed the latest which doesnt need any command to run. It does automatically but still the same result.. i cant connect.. When i click to connect it says "Disconnected" immediately.

---

### Post by pdc on 2010-03-22
wvdial may well work for you, if network manager will not;

see post #11 as they talk of wvdial;

see how you get along reading the link they cite;

if it works: tell us; if it doesn't work, tell us!

so you need wvdial

> sudo apt-get install wvdial

then add the wvdial.conf from Ig's blog

> sudo gedit /etc/wvdial.conf

and that should open blank page; paste in Ig's file; save;close

command from terminal is

> sudo wvdial

and if it connects

 > control-c      disconnects

---

### Post by kapcom01 on 2010-03-23
Wow!
It worked!

Thank you so much!:D:D

---

### Post by pdc on 2010-03-23
pleased to hear it works; wvdial works again!

---

### Post by sesso on 2010-06-02
why dont just use this guide ,,,,, not all that mumbu jumbo

[http://www.sakis3g.org/](http://www.sakis3g.org/) 

it has and video guide so even is you are not in to ubuntu
you can fix it bye you self :)

it took me 5 min from start to finish any it find the modem and all ...

---

### Post by brydong on 2010-06-02
I just tried [http://www.sakis3g.org/](http://www.sakis3g.org/) and it didn't work for me. I'll give it a longer look later.

---

### Post by alexfish on 2010-06-02
> **brydong said:**
> I just tried [http://www.sakis3g.org/](http://www.sakis3g.org/) and it didn't work for me. I'll give it a longer look later.

you need to configure sakis3g for the provider

 there are links here for the wiki site, have a look at post #10
 
[How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")

---

### Post by brydong on 2010-06-07
The instructions here used to work fine for me...

[http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html](http://lorgor.blogspot.com/2010/01/sony-ericsson-md400g-usb-broadband-data.html)

Now when I run...

"usb_modeswitch -v 0x0fce -p 0xd103 -O 1"

It ends with a segmentation fault, any ideas??


"USB description data (for identification)
-------------------------
Manufacturer: Sony Ericsson
     Product: MMC Flash Card
  Serial No.: 3578660212868390
-------------------------
Looking for active driver ...
 No driver found. Either detached before or never attached
Trying to send Sony control message
 OK, control message sent, waiting for device to return ...
#####################Segmentation fault"

---

### Post by brydong on 2010-06-07
I installed latest release of usb-modeswitch(1.1.2) from [http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch) and I'm now posting this from the train on my rogers stick.

I'm guessing that fixed the issue?

---

### Post by Andreas1982 on 2010-07-02
Hi.

I have just tried to install the usb-modeswith package and calling it from prompt for the SE MD400 modem, but it doesn`t show up.

Can someone please help me out with this?
It is for a friend of mine and it is his first run at Ubuntu, so he`s a bit disappointed that it doesn`t work out of the box on 10.04.

---

### Post by pdc on 2010-07-02
> *I have just tried to install the usb-modeswith package*

tell us how you tried;

the usb_modeswitch website 

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

recommends you use a debian package for ubuntu; (and to use the latest one ..)

you should go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

and download 1.1.3-1

as it is being downloaded, your system should ask you if you want to install it (gdebi package installer); no command line needed

____________

> calling it from prompt for the SE MD400 modem

what?

---


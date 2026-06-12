---
title: "[HOWTO] Logitech Quickcam MESSENGER"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by Yoriko on 2006-01-01
Well; I just got it working for the first time, and I can't find anything on it here; 
So it thought I'd post a how-to to give back to the ubuntu community~

[Keep in mind it is 2am and Steps may not be in order]

- Grab the latest sources from [Here]("http://home.mag.cx/messenger/")
- Install the kernel-headers 2.6.10 for i386 from synaptic, and the kernel sources.
- apt-get xawtv if you don't already have it
- apt-get gcc-3.4 if you don't have it, and gcc

-extract the drivers; type into the terminal "export CC=gcc-3.4"

- if you havn't already, set root password "sudo passwd"

-run quickcam.sh, it shouldn't give any errors until "Can't detect webcam"
-Keep ignoring errors after that one~
- run "sudo modprobe quickcam"
- have fun

[I'm not a linux "guru" or anything, just an average user soo... if anything doesn't make sense scold me or something, its pretty straightforward]

[[IMG]http://img371.imageshack.us/img371/1529/webcam9fj.th.jpg[/IMG]](http://img371.imageshack.us/my.php?image=webcam9fj.jpg)

---

### Post by encompass on 2006-01-05
I think I have the same cam... can you do a lsusb and tell me the information you get?

---

### Post by encompass on 2006-01-05
I just got the cam working with your instructions...
I would encourage you to revise your post and we should include our lsusb's so that others with the saem chipsets can fallow your instructs and have success too.  Thanks for your help...
PS... did you get your mic working with the cam too?
> jason@lappy:~$ lsusb
Bus 001 Device 003: ID 046d:08f6 Logitech, Inc.
Bus 001 Device 002: ID 1267:0210 Logic3 / SpectraVideo plc
Bus 001 Device 001: ID 0000:0000
jason@lappy:~$

[[IMG]http://img498.imageshack.us/img498/8560/screenshot5pt.th.png[/IMG]](http://img498.imageshack.us/my.php?image=screenshot5pt.png)

---

### Post by maol62 on 2006-01-06
Ok, my works until I reboot. After reboot I receive "Your webcam uses a palette that this extension does not support yet" when using amsn 0.95, and in Gnomemeeting I get only a green screen instead of the camera.

My lsusb

```
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:08f5 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

---

### Post by maol62 on 2006-01-06
Solved! Found the solution [here]("http://doc.ubuntu-fr.org/materiel/webcam_logitech_msn"). But its french... :)

So here is the solution in english:
First
```
sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam
```
Then create a script and save it as **quickcam** in /etc/init.d/
```
#! /bin/sh
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver.
rmmod quickcam
modprobe quickcam
```
Finally create a symbolic link so the script is launched at boot:
```
sudo ln - S/etc/init.d/quickcam/etc/rcS.d/S99quickcam
```
Now it works after reboot.

---

### Post by encompass on 2006-01-07
I would like to say thanks first off for everyone helping eachother in this forum.  But I think we need to get it all organized a little better.  Lets get all the typo's out of this howto and then I can make a script to install all this automatically for any ubuntu linux install.  I will also be taking some pictures of the cam and getting information pastes of the lsusb of the camera.  It will really help the newbees out there.
Can I get a yes from you guys.  Especially the first guy. Yoriko.. he is the starter.. I has done a great job getting started.

---

### Post by gosh on 2006-01-07
I have trouble running the quickcam.sh script.

It says 

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
Warning: gcc missing
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
[!] Some important programs can not be found on default path.
Probably they aren't installed.
You should install them, for example, by using apt-get or rpm.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

any ideas

---

### Post by philgallagher on 2006-01-07
I'd really appreciate an automatic install for this driver. I'm very keen to get my webcam working as I'm in another country from my girlfreind but I have very little clue with linux. 

Thanks everyone for your help, it's great for ignorants like myself!

---

### Post by encompass on 2006-01-07
[QUOTE=gosh]I have trouble running the quickcam.sh script.

It says 

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
Warning: gcc missing
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
[!] Some important programs can not be found on default path.
Probably they aren't installed.
You should install them, for example, by using apt-get or rpm.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

any ideas[/QUOTE]
do you have gcc 3.4 installed?  To check with a mouse, just open synaptic and look to see if it is installed... if not install it and try again.

and yes.. I need a collection of lsusb outputs to see which cams work and don't with this driver.  I want to submit a success list to the creator of the driver.

---

### Post by encompass on 2006-01-07
> Grab the latest sources from [Here]("http://home.mag.cx/messenger/")
I wonder what the other drivers do... does anyone want to find out?

---

### Post by gosh on 2006-01-07
[QUOTE=encompass]do you have gcc 3.4 installed?  To check with a mouse, just open synaptic and look to see if it is installed... if not install it and try again.

and yes.. I need a collection of lsusb outputs to see which cams work and don't with this driver.  I want to submit a success list to the creator of the driver.[/QUOTE]

oeps, yes sorry, made some mistakes here.
Compiling did work, but webcam still doesn't.
It is an Quickcam Pro 5000. 
Some googleing learned me that it probably isn't supported yet by any driver...

Or does anyone else has a better idea?

---

### Post by encompass on 2006-01-08
I would like to get your lsusb output for this camera, I am making a collection for the howto website I am creating now...

---

### Post by gosh on 2006-01-09
This is the output of lsusb with an older Creative Webcam Go:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1046:9967 Winbond Electronics Corp. [hex] W9967CF/W9968CF WebCam IC
Bus 001 Device 002: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

This is the output of lsusb with Logictech Quickcam Pro 5000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08c5 Logitech, Inc.
Bus 001 Device 002: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

Both are not working. bus 001 Device 002 is my logitech Click optical usb-mouse

---

### Post by encompass on 2006-01-09
[QUOTE=gosh]This is the output of lsusb with an older Creative Webcam Go:

Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1046:9967 Winbond Electronics Corp. [hex] W9967CF/W9968CF WebCam IC
Bus 001 Device 002: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

This is the output of lsusb with Logictech Quickcam Pro 5000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:08c5 Logitech, Inc.
Bus 001 Device 002: ID 046d:c01a Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

Both are not working. bus 001 Device 002 is my logitech Click optical usb-mouse[/QUOTE]
Things don't look so bright for the creative....  I won't personally be looking any further on that one, but you may want to check the spca5xx driver and see if that cam is on their support list.
As for the Quickcam... I don't think this driver was built for your camera... try...[http://www.saillard.org/linux/pwc/]("http://www.saillard.org/linux/pwc/")
That is Probably a good bet...  But I don't thinks your card is going to work with our driver... but I think it will with this other one.

---

### Post by Yoriko on 2006-01-13
Sorry I took so long to reply; -and- gravedigging.

I am in australia now, instead of england. Visiting my girlfriend - I wanted my camera working for similar reasons to that other person ;).

Don't have an ubuntu install here, just her windows so I can't give you my lsusb.

I will be able to.. in 2 weeks though :???: 

So, do as you like with this information I err, threw together >_<.
You have my permission if that is what you were waiting for. :p

---

### Post by encompass on 2006-01-13
Thanks.... I already have a page created... just looking for a nice way to host the information.  If you can... the next chance you get have some pictures taken of the cam... even the box if you can find it.  Be bold and goto the store and get a picture of the box and the UPC and code information around it.  The more information we can find... the better things will be with this forum.  And thanks for you're help... you have lit a fire under alot of us. :)

---

### Post by chele on 2006-01-14
Have you tried this [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") utility? It automagically downloads and builds the latest drivers for many webcams.

---

### Post by gosh on 2006-01-14
[QUOTE=chele]Have you tried this [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") utility? It automagically downloads and builds the latest drivers for many webcams.[/QUOTE]

No I haven't actually.
I'll give it a try.
thnx

---

### Post by gosh on 2006-01-16
[QUOTE=chele]Have you tried this [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") utility? It automagically downloads and builds the latest drivers for many webcams.[/QUOTE]

I tried it, but with both my webcam it says: No camera, or no compatible camera found.

---

### Post by gosh on 2006-01-16
[QUOTE=encompass]Things don't look so bright for the creative....  I won't personally be looking any further on that one, but you may want to check the spca5xx driver and see if that cam is on their support list.
As for the Quickcam... I don't think this driver was built for your camera... try...[http://www.saillard.org/linux/pwc/]("http://www.saillard.org/linux/pwc/")
That is Probably a good bet...  But I don't thinks your card is going to work with our driver... but I think it will with this other one.[/QUOTE]

Doesn't work for the Quickcam. Website says:
Warning: This driver does not support these newer Logitech webcam:
Product Id	Model
0x8C1	Logitech QuickCam Fusion
0x8C2	Logitech QuickCam PTZ (newer version of the sphere)
0x8C3	QuickCam for Notebooks Pro
0x8C5	Logitech QuickCam Pro 5000
0x8CF	Logitech QuickCam UpdateMe

Pro 5000 is mine

As far as the Creative is concerned, I get some results.
I posted a separate thread for this: [http://www.ubuntuforums.org/showthread.php?t=117294](http://www.ubuntuforums.org/showthread.php?t=117294)

---

### Post by encompass on 2006-01-16
[QUOTE=gosh]I tried it, but with both my webcam it says: No camera, or no compatible camera found.[/QUOTE]
Mine said that too... but it worked... then I lost it at reboot and figured out you need to reload the driver every time you boot.  Did that with yet another post here... FYI I am creating a site to take care of this howto too... I will also put any references to other howtos and drivers that you all may know off.
You can see the site and make recommendation and addition through me... they site is here... [http://www.slicehaven.com/ubuntu/index.html]("http://www.slicehaven.com/ubuntu/index.html") REMEMBER... still under construction.

---

### Post by gosh on 2006-01-19
I gave up with my other two webcams (Creative Webcam Go and Logitech Quickcam Pro 5000) and bought myself a Quickcam Messenger.

It worked instantly following this HowTo. Thnx:p 

But, is there a typo in this line?

[QUOTE=maol62]
Finally create a symbolic link so the script is launched at boot:
```
sudo ln - S/etc/init.d/quickcam/etc/rcS.d/S99quickcam
```
Now it works after reboot.[/QUOTE]

---

### Post by drfalkor on 2006-01-19
My webcam worked "out-of-the-box" :p

---

### Post by encompass on 2006-01-19
[QUOTE=drfalkor]My webcam worked "out-of-the-box" :p[/QUOTE]
can you run the lsusb cammand and tell me the output so I can add your cam to the list.  If you have the box still I would like the pictures like I have on the webpage I am working on that is listed in this thread.  PLEASE!

---

### Post by encompass on 2006-01-19
[QUOTE=gosh]I gave up with my other two webcams (Creative Webcam Go and Logitech Quickcam Pro 5000) and bought myself a Quickcam Messenger.

It worked instantly following this HowTo. Thnx:p 

But, is there a typo in this line?[/QUOTE]
Yeah I know... did you figure out the correct command?  I can help if you need it....:smile:

yeah... ln -S I think  I will tell you soon in the website....

---

### Post by encompass on 2006-01-25
[QUOTE=drfalkor]My webcam worked "out-of-the-box" :p[/QUOTE]
That's not very informative... can you tell us the cam.. the lsusb, then you bought it... even some pictures?  I would like to see the cam...  I would also test it... like this
System Selector
camorama
xawtv
gnomeeting
and
xsceensaver with the option to use your cam as the screenshot
any results?

---

### Post by gosh on 2006-01-26
No, I didn't figure it out.
Did you?

---

### Post by andreab on 2006-01-26
I suggest you to take a look to this driver, it is simple to install and work fine with my logitech quickcam messenger!

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

install these packages:
build-essential
bzip2
debhelper
module-assistant

then

$ mv spca5xx-20060101.tar.gz /usr/src/
$ cd /usr/src/
$ tar -zxvf spca5xx-20060101.tar.gz
$ cd spca5xx-20060101
$ modprobe -r spca5xx
$ make
$ make install
$ modprobe spca5xx

to read the README file can be useful!
try gnomemeeting and see what happen...

---

### Post by Jay_Dogg on 2006-01-26
None of your instructions work, I've got a Logitech Quickcam Express, which should be supported by these drivers:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

*Bus 004 Device 002: ID 046d:0928 Logitech, Inc.*

When I try to use the camera my system freezes up completely. However, it isn't a matter of life and death to get it working, since I don't use a webcam. Although, it would be nice...

---

### Post by encompass on 2006-01-30
[QUOTE=Jay_Dogg]None of your instructions work, I've got a Logitech Quickcam Express, which should be supported by these drivers:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

*Bus 004 Device 002: ID 046d:0928 Logitech, Inc.*

When I try to use the camera my system freezes up completely. However, it isn't a matter of life and death to get it working, since I don't use a webcam. Although, it would be nice...[/QUOTE]
Yeah... This driver... that we talk about on this post is the driver for the messenger.  not the express.  and I have no idea about that other driver.  I would try the quickcam driver that is similar to the one in this post.  I haven't the time to look for it right now... but I will start looking.

---

### Post by DRF on 2006-02-08
Just to say I have had some success it seems with the driver in the AMD64 port of ubuntu.

xawtv didn't work for me (not sure if it's my computer or AMD64 distribution in general) and I had to remove and modprobe the module a couple of times but just as I was about to give up I opened camorama and it found the webcam. :-D 

But I've not yet rebooted so not sure if I'll have to go though the remove and modprobe process again (I suspect so). I made the script as shown earlier in this thread but creating the link fails (or came up with an error at least) so wondering where the script should be linked to in order to have it run when the computer starts up automatically.

Not yet tested this on aMSN but it appears in the aMSN config settings (just complains about a router/firewall dispite me setting the port forwarding as suggested). Just need to find someone online to test it with later this week. :-D

Ok the technical stuff as requested, the lsusb command shows my webcam as:

Bus 001 Device 002: ID 046d:08f6 Logitech, Inc.

It's a 'Logitech Quickcam Messenger' brought earlier this week. My computer is running Ubuntu 5.10 (AMD64 version) (re-compiled kernel as I needed to add a patch but still 2.6.12).

Does anyone know if support for the Logitech Quickcam Messengers will make it into the EasyCam package one day or into the ubuntu distribution? The modules seem to work ok but not the easiest process for beginners.

Daniel

---

### Post by encompass on 2006-02-09
GREAT!  Thanks for the report... when I find some time I will add your lsusb and kernel to the website...
About the link... yeah... he missed typed it... 
try this one  and tell me what you get:
> sudo ln -s /etc/init.d/quickcam/etc/rcS.d/S99quickcam
That 'should' fix the issue.
That link makes the script in the init.d directory run at bootup... /at number 99 if I am not mistaken.  Thanks SO MUCH.. for submiting you information to the site.  Keep us posted.(that pun is intended) :P

---

### Post by robfindlay on 2006-02-09
Just thought I'd let everyone know I got the quickcam express 5000 working with these drivers. 

[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

I had my quickcam express configured and just plugged in the 5000 to see what would happen.

Works perfectly.

---

### Post by encompass on 2006-02-10
That is great... can you give us the LSUSB and I will add you cam to the list that works with that driver... and if you have a howto or a reference to a howto that handles that driver pop me the link.  I would love to add that to the support page too.

---

### Post by Toontwnca on 2006-02-12
Well; I did the install as the instructions said.
It did work until reboot, then nothing. I did 
use the script that was posted. Any ideas?

Thanks.

---

### Post by encompass on 2006-02-13
[QUOTE=Toontwnca]Well; I did the install as the instructions said.
It did work until reboot, then nothing. I did 
use the script that was posted. Any ideas?

Thanks.[/QUOTE]
what command did you use to link the file... mine or the older one?

---

### Post by Toontwnca on 2006-02-13
[QUOTE=encompass]what command did you use to link the file... mine or the older one?[/QUOTE]

I did use your command.

---

### Post by DRF on 2006-02-14
Same problem here, it works fine if I remove and modprobe the modules but the script doesn't seem to want to know. Any ideas? (I don't use the webcam that often to be a big hassle but be good if it did work without having to do that each time)

Any ideas anyone?

Daniel

---

### Post by amisi on 2006-02-14
Hi!

I've use [this](http://doc.gwos.org/index.php/ICM532_webcams)  great HOWTO to get my Logitech WEbCam works, and this solve my problem!

Try it, costs nothing!

---

### Post by rory_fireshaper on 2006-02-15
I've not yet restarted... scared to, hehe. I'm waiting for the post of the working script to bootup and have a cam available. Also, encompass, the link on your site to the script keeps giving me an error, something about "no anonymous login".

---

### Post by encompass on 2006-02-15
[QUOTE=rory_fireshaper]I've not yet restarted... scared to, hehe. I'm waiting for the post of the working script to bootup and have a cam available. Also, encompass, the link on your site to the script keeps giving me an error, something about "no anonymous login".[/QUOTE]
I will fix the script soon.. to busy right now.

---

### Post by rory_fireshaper on 2006-02-15
Well, I -had- it working yesterday.. I rebooted and reinstalled the drivers and everything and now it works with Camorama but not with aMSN. I dunno what happened, any ideas?

---

### Post by encompass on 2006-02-16
once the driver is installed it should just be restarted by:```
sudo rmmod quickcam
sudo modprobe quickcam
```
that is what should be in the executable file that is linked to /etc/init.d/... something or other minus the sudo's.
If you do it manually it should still work.  I did that for a long time till I figured t out.  As I have a big exam today I will not be able to help you right now.  I will get on it as soon as I can.

NOTE:  have you tryied checking it with gnomemeeting and multimedia selector for gnome?  Do they give any errors?  BTW  could you give me your kenrel and system specs too... I think it may be an issue with the smp kernel (like I know anything about that stuff).

---

### Post by rory_fireshaper on 2006-02-16
This is my lsusb:

eci@ubuntu:~$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 003: ID 0a5c:200a Broadcom Corp.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:08f0 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000

how do I get the kernel? I'm running a Pentium 4 2.8 gHtz, with Breezy, 1 gig of RAM, and a nvidia geforce 6800 GT.

Edit: I tried testing my cam in Multimedia Systems Selector but when I test v4l I get this:
Failed to construct test pipeline for 'Video for Linux (v4l)'

---

### Post by _Graven on 2006-02-18
Yoriko,

Cheers for the HOWTO. It worked on my box. :) 


Encompass,

Here's my lsusb output:
> 
Bus 001 Device 007: ID 05ac:120a Apple Computer, Inc.
Bus 001 Device 006: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 001 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 004: ID 0603:00f2 Novatek Microelectronics Corp.
Bus 001 Device 003: ID 046d:08f6 Logitech, Inc.
Bus 001 Device 002: ID 2001:f103 D-Link Corp. [hex]
Bus 001 Device 001: ID 0000:0000

---

### Post by encompass on 2006-02-19
FANTASTIC!  And thanks for the lsusb... I will add it to the website as soon as I can.  I am having a few problems with the server and good'ol nvu so it will be a while.  But yes, thank you.\\:D/

---

### Post by larsemil on 2006-02-22
i got it working at first try.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 002: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c211 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 001 Device 001: ID 0000:0000

---

### Post by encompass on 2006-02-24
sorry was is the express that you have working?  and you were using the driver according to this howto?

---

### Post by ottoshafer on 2006-04-24
Ok, here is the complete output of my running of the quickcam.sh file.  Any help would be greatly appreciated.  

-=- Logitech QuickCam USB camera driver installer -=-
Hello! I am the (hopefully) easy-to-use, fully automated
qc-usb driver installation script.
At the moment, this is experimental, and if it doesn't work,
don't hesitate to quit this with Ctrl+C and install the
driver manually.

The driver is provided in source code form, so it has to be
compiled. This should happen automatically, but it does mean
that there are some steps required before installation.

You also need to know "root" user password to test and
install the driver.

Basically you need only to keep hitting Enter whenever you
see this prompt: --->. Sometimes you're asked root password.
Pay special attention to lines beginning with [!].
It means that some trouble has been detected.

To most important location is the path to your kernel source
or headers. This can be guessed, but you can specify it by
giving it as an argument to this script like this:
        ./quickcam.sh LINUX_DIR=/usr/src/linux

If you haven't done it yet, now it would be a good moment to
take a look at file README.

Next I'm going to check if you have some important programs installed
and if they and the kernel are of suitable version.
Press Ctrl+C to quit, Enter to continue --->

Using specified C compiler from environment CC=gcc-3.4
./quickcam.sh
/usr/bin/whoami
/bin/su
/bin/ls
/bin/cat
/usr/bin/gcc-3.4
/usr/bin/gcc
/usr/bin/make
/bin/grep
/bin/egrep
/usr/bin/awk
/bin/sed
/usr/bin/tail
/usr/bin/head
/usr/bin/install
/usr/bin/ld
/bin/uname
/usr/bin/tr
/usr/bin/xawtv
/usr/bin/xdpyinfo
/bin/dmesg
/usr/bin/wc
/bin/readlink
gcc-3.4 version: gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)
gcc version: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Make version: GNU Make 3.80
Linker version: GNU ld version 2.16.1 Debian GNU/Linux
Kernel compiler: gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)[!] Kernel compiler and gcc-3.4 seem to be different versions.
Instead, they should be the same. If you have many compilers
installed, you can specify the correct one with command (in bash)
        export CC=kgcc
before trying to install the driver. Replace kgcc with the command
required for compiling kernels (kgcc is often used in Red Hat systems).
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Looking for more necessary programs...
Found program /sbin/depmod
Found program /sbin/insmod
Found program /sbin/rmmod
Found program /sbin/modprobe
Found program /bin/mount
Found program /usr/sbin/lsusb
depmod version: module-init-tools 3.2-pre7
insmod version: module-init-tools version 3.2-pre7
rmmod version: module-init-tools version 3.2-pre7
modprobe version: module-init-tools version 3.2-pre7
Checking whether we're root... root
[!] Running script as root.
You shouldn't run this script as root. It should work,
but is unsafe. Please run this as an ordinary user.
When root access is really needed, you will be prompted
for the root password.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

Checking for driver source code...
Checking for write permission...

Previous round done. Now checking if you have kernel source installed.
Press Ctrl+C to quit, Enter to continue --->

Kernel source directory: /lib/modules/2.6.16.1-num2/build
Detected kernel version is 2.6.x.
Kernel version name: 2.6.16.1-num2
Kernel source version code: 132624
Driver file name: quickcam.ko
Module install directory: /lib/modules/2.6.16.1-num2
Driver source directory (PWD):         /home/otto/Desktop/qc-usb-messenger-1.2
Kernel source directory (LINUX_DIR):   /lib/modules/2.6.16.1-num2/build
Module install directory (MODULE_DIR): /lib/modules/2.6.16.1-num2
Utility install directory (PREFIX):    /usr/local
User options (USER_OPT):
Driver file name (use with insmod):    quickcam.ko
Kernel version code:                   132624

The QuickCam driver requires other drivers from kernel.
I'll now check if those seem to be loaded.
Press Ctrl+C to quit, Enter to continue --->

Modules loaded into the kernel:
videodev uhci_hcd rfcomm l2cap pcmcia firmware_class container ipv6 af_packet pcspkr rtc yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc shpchp pci_hotplug amd64_agp sis_agp agpgart nls_cp437 ntfs joydev dm_mod psmouse mousedev parport_pc lp parport md_mod ext3 jbd sis900 mii ehci_hcd ohci_hcd usbcore ide_cd cdrom ide_disk ide_generic sis5513 generic ide_core unix vga16fb vgastate cfbimgblt cfbfillrect cfbcopyarea tileblit font

Next round: let's see if you have a supported QuickCam.
Please plug in your USB camera before continuing.
Press Ctrl+C to quit, Enter to continue --->

I can find the following probably compatible devices:
Bus 001 Device 002: ID 046d:0870 Logitech, Inc. QuickCam Express

Another round done. Let's now compile the driver, it takes a while.
This step will also clear old unnecessary files from the directory.
Press Ctrl+C to quit, Enter to continue --->
rm -f *.o qcset input_read show *~ .\#* .*.cmd *.mod.c *.ko
rm -rf .tmp_versions
cd testquickcam ; make clean
make[1]: Entering directory `/home/otto/Desktop/qc-usb-messenger-1.2/testquickcam'
rm -f testquickcam *~ pic.ppm pic.gif
make[1]: Leaving directory `/home/otto/Desktop/qc-usb-messenger-1.2/testquickcam'
make -C "/lib/modules/2.6.16.1-num2/build" SUBDIRS="/home/otto/Desktop/qc-usb-messenger-1.2" modules V=1 USER_OPT=""
make[1]: Entering directory `/usr/src/linux-2.6.16.1'
mkdir -p /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_versions
make -f scripts/Makefile.build obj=/home/otto/Desktop/qc-usb-messenger-1.2
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-driver.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_driver)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-driver.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c
/home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c: In function ‘qc_capt_get’:
/home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c:2378: warning: ‘gn’ may be used uninitialized in this function
/home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.c:2378: warning: ‘ex’ may be used uninitialized in this function
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-vv6450.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_vv6450)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-vv6450.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-vv6450.c
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-formats.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_formats)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-formats.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-formats.c
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.qc-memory.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign -DNOKERNEL   -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(qc_memory)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -c -o /home/otto/Desktop/qc-usb-messenger-1.2/.tmp_qc-memory.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-memory.c
  ld -m elf_i386 -m elf_i386  -r -o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-driver.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-vv6450.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-formats.o /home/otto/Desktop/qc-usb-messenger-1.2/qc-memory.o
  Building modules, stage 2.
make -rR -f /usr/src/linux-2.6.16.1/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-2.6.16.1/Module.symvers vmlinux /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.o
  gcc -m32 -Wp,-MD,/home/otto/Desktop/qc-usb-messenger-1.2/.quickcam.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.0.2/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -ffreestanding -Os     -fomit-frame-pointer -pipe -msoft-float -mpreferred-stack-boundary=2  -march=athlon -Iinclude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign    -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(quickcam)"  -D"KBUILD_MODNAME=KBUILD_STR(quickcam)" -DMODULE -c -o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.mod.o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.mod.c
  ld -m elf_i386 -m elf_i386 -r -o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.ko /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.o /home/otto/Desktop/qc-usb-messenger-1.2/quickcam.mod.o
make[1]: Leaving directory `/usr/src/linux-2.6.16.1'
gcc -Wall -O2 -s qcset.c -o qcset -lm
qcset.c: In function ‘pnm_open’:
qcset.c:383: warning: pointer targets in passing argument 1 of ‘fopen’ differ in signedness
qcset.c: In function ‘main’:
qcset.c:640: warning: pointer targets in passing argument 1 of ‘pnm_open’ differ in signedness
gcc -Wall -O2 -s input_read.c -o input_read
-rw-r--r--  1 root root 120899 2006-04-24 13:55 quickcam.ko

Now everything should be well and the driver compiled.
Let's then try actually loading the fresh driver and testing
if it works.
Press Ctrl+C to quit, Enter to continue --->

To load the driver, I need to know the root password.
=== Entering root mode ===

I will now try to enable the SysRq key.
If your computer crashes, you can try pressing:
        Alt + SysRq + S: Emergency Sync (write everything on hard disk)
        Alt + SysRq + U: Unmount all harddisks
        Alt + SysRq + B: Reboot system immediately
Press Ctrl+C to quit, Enter to continue --->

Now I finally will try to load the module.
If you're unlucky, your computer might crash right now!!!!
Consider long if you really want to continue.
Press Ctrl+C to quit, Enter to continue --->

You decided to do it, here we go...
=== Leaving root mode ===
The driver detected the following supported cameras:
[!] No cameras detected.
Try unloading and reloading the driver manually with
        rmmod quickcam; insmod ./quickcam.ko debug=-1
and then checking whether there are any messages indicating
problems with command
        dmesg
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

I will be using , if there are more cameras I'll not test them.
Press Ctrl+C to quit, Enter to continue --->

Testing if  is correct.
ls: : No such file or directory
./quickcam.sh: line 699: [: too many arguments
ls: : No such file or directory
ls: : No such file or directory
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->


Right now driver is loaded and should be ready to run.
Let's test if user applications can see it, starting with qcset.
Press Ctrl+C to quit, Enter to continue --->

./qcset: can not open /dev/video0 (No such device)
[!] qcset did not found the QuickCam camera
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue --->

If you like, you can quit now and start using the camera -
you have good chances that it works, if no problems were detected.
If you have X Window System running and xawtv installed,
I can now run it automatically for you.
You will then also have opportunity to install the driver permanently.
Press Ctrl+C to quit, Enter to continue --->

Launching xawtv (press q on xawtv window to quit it)...
If the image is not sharp, try focusing it by turning the
wheel around the camera lens.
        xawtv -noscale -noxv -c ""
This is xawtv-3.94, running on Linux/i686 (2.6.16.1-num2)
v4l-conf: option requires an argument -- c
usage: v4l-conf  [ options ]

options:
    -q        quiet
    -d <dpy>  X11 Display     [:0.0]
    -c <dev>  video device    [/dev/video0]
    -b <n>    displays color depth is <n> bpp
    -s <n>    shift display by <n> bytes
    -f        query frame buffer device for info
    -a <addr> set framebuffer address to <addr>
              (in hex, root only, successful autodetect
               will overwrite this address)
    -1        force v4l API
    -2        force v4l2 API
v4l-conf had some trouble, trying to continue anyway
v4l2: open : No such file or directory
v4l2: open : No such file or directory
v4l: open : No such file or directory
no video grabber device available

Well, did it work, did you get a picture?
If you did, you might now want to install the driver
permanently. Just proceed to do that...
Press Ctrl+C to quit, Enter to continue --->

Just an extra warning: the driver (quickcam.ko) and
the utility (qcset) will be now copied into system
directories. If you have already other versions,
they will be overwritten. Verify by giving root password.
=== Entering root mode ===
/usr/bin/install -c -D -m 644 quickcam.ko        /lib/modules/2.6.16.1-num2/misc/quickcam.ko
/usr/bin/install -c -D -m 755 qcset /usr/local/bin/qcset
/sbin/depmod -a

=== Leaving root mode ===
Hopefully the driver is now installed and can be loaded
with command
        modprobe quickcam
as root. You can put this command into some startup
script to do it always automatically at boot.
The exact location depends on distribution, and this
script is yet too dumb to do this automatically.
Press Ctrl+C to quit, Enter to continue --->
Goodbye...

---

### Post by ottoshafer on 2006-05-02
bump... please help

---

### Post by encompass on 2006-05-03
What is your lsusb and the name of your camera?

---

### Post by janformanek on 2006-07-06
Hi!
Im using the QuickCam Messenger. (lsusb-output: 046d:08f5)
camorama works fine after running quickcam.sh but after reboot I get the message; "Could not connect to video device (/dev/video0). Please check connection" when i try to run the formerly mentioned application. I have tried the remedy suggested by 'maol62' in the beginning of this thread, also tried to mknod manually in combination with modprobe manually.

---

### Post by anurag_gupta on 2006-07-08
hi i'm also using da same cam and having the same problem as the above

---

### Post by encompass on 2006-07-09
> **janformanek said:**
> Hi!
Im using the QuickCam Messenger. (lsusb-output: 046d:08f5)
camorama works fine after running quickcam.sh but after reboot I get the message; "Could not connect to video device (/dev/video0). Please check connection" when i try to run the formerly mentioned application. I have tried the remedy suggested by 'maol62' in the beginning of this thread, also tried to mknod manually in combination with modprobe manually.

> **anurag_gupta said:**
> hi i'm also using da same cam and having the same problem as the above
What versions of ubuntu are you running?  is it breezy or dapper...  If dapper, check out this howto for it...
[http://ubuntuforums.org/showthread.php?t=191770](http://ubuntuforums.org/showthread.php?t=191770)
otherwise... not sure if you fallowed his directions... try removing the driver...
```
sudo rmmod quickcam
sudo modprobe quickcam
```

---

### Post by Marco Bresciani on 2006-08-29
Got a 04d6:0928 Logitech QuickCam Express... :-)
 - spca5xx-source installed
 - xawtv          installed
 - camorama       installed and working (only a bit dark)
 - gqcam          installed and working (only not so good colours)
 - aMSN           installed and working

aMSN detects the cam with SPCA561 but tells I'm behind firewall or router (Type: IP-restict-NAT). I've tried to follow FAQ instructions and is says ok for connection... but then it cannot find cam!!! :-)

How can i make aMSN working? :( I have a ADSL connection with ethernet modem... maybe it's its fault... Please help: I need this cam for job! :(

Thank you in advance for any help!

---

### Post by encompass on 2006-09-04
> **Marco Bresciani said:**
> Got a 04d6:0928 Logitech QuickCam Express... :-)

I am sorry but your posting in the wrong place for this.  This thread is only for the Quickcam Messenger.  If anything, by your errors, it sounds like a post about amsn not your camera.  Sorry.

---

### Post by Marco Bresciani on 2006-09-04
Thank you for your reply. I think I've found out the problem: the NAT inside my ADSL modem won't allow me to connect with webcam using any messenger. Also, by deactivating the NAT, I cannot connect to the Internet at all! :-( Any idea?

---

### Post by encompass on 2006-09-10
dude... wrong thread for this question!
I will answer out of the kindness in my heart....
try setting up port forwarding... or to make things simple, try setting up your network with NAT but your computer as a "virtual server"
Please use a different thread for this.

---

### Post by MaximB on 2006-09-13
you are a very smart girl ;)
thank you
you saved my day .

---

### Post by hde on 2006-09-22
Hi

I have a logitech quickcam messenger

My output from lsusb:
Bus 004 Device 002: ID 046d:08f6 Logitech, Inc. 

It works with the quickcam driver as described in the first post, however I had some problems.

It all seemed to work, the camera was found, but trying to get any pictures from it would give error messages like this:

--------------
ioctl: VIDIOC_QUERYCAP(driver="";card="";bus_info="";version=0.0.0;capabilities=0x0 []): Unknown error 515
ioctl: VIDIOCSYNC(int=0): No space left on device
ioctl: VIDIOCSYNC(int=0): No space left on device
ioctl: VIDIOCSYNC(int=0): No space left on device
ioctl: VIDIOCMCAPTURE(frame=0;height=120;width=160;format=15): Invalid argument
can't get rgb24 data
----------------

The solution came from this page:
[http://sourceforge.net/mailarchive/forum.php?thread_id=3913966&forum_id=4334](http://sourceforge.net/mailarchive/forum.php?thread_id=3913966&forum_id=4334)

I had connected the webcam to an usb hub, with other usb devices. Apparently the webcam couldn't get enought "usb bandwith". Connecting the camera to its own usb output solved it.

---

### Post by encompass on 2006-09-24
Some hubs they work... like mine works threw a hub... but glad you figured it out and even better that you posted your solution... kudos to youdos!

---

### Post by noizatu on 2006-09-25
> **chele said:**
> Have you tried this [https://wiki.ubuntu.com/Webcam](https://wiki.ubuntu.com/Webcam) utility? It automagically downloads and builds the latest drivers for many webcams.


Wow! GREAT UTILITY! Thanks so much for this.... Now my Logitech Quick Cam Messenger works very well. :p

---

### Post by encompass on 2006-10-01
Good to here... I will try it to, I am doing another install and will try the cam with this utility then.   Thanks for the advice.
Nope... didn't work for me... both versions.

---

### Post by willnapier on 2006-10-13
Hi all. I am having problems using my new logitech quickcam pro 5000 with Dapper. At first, when I plugged it in out of the box, my kopete setup window showed an entry in 'input'. I could see myself in the test screen. This suggests that I have some level of support already for this camera. However when I upgraded to the latest version of kopete, which has more facilities for webcam sharing, there was no entry in 'input' on the config window, and no video either.

I understand that the QuickCam 5000 (lsusb says 'Bus 010 Device 002: ID 046d:08c5 Logitech, Inc.) uses the uvc standard which goes with v4l2 (Video for Linux 2). I also understand that v4l2 is in the dapper kernel (it is a 2.6 kernel). What I don't understand is what, if anything, I need to do to 'activate' v4l2, or if this is not even my problem.

I have read through the thread and have installed apache, svn and thereby got the latest uvc drivers using:

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
A    trunk/uvcvideo.c
A    trunk/uvcvideo.h
A    trunk/Makefile
A    trunk/v4l2_enumfrmfmt.h
Checked out revision 60.

how do I proceed from here? I would like to know how to incorporate this (compile? install?) into the kernel modules (?). As you can see my knowledge is patchy despite some reading. I would be very grateful for any help to get this running.

when I do 'dmesg' I get multiple lines saying

[17179642.240000] uvcvideo: Failed to query (131) UVC control 7 (unit 2) : -32.
[17179642.412000] uvcvideo: Failed to query (1) UVC control 2 (unit 2) : -32.
[17179642.424000] uvcvideo: Failed to query (135) UVC control 3 (unit 2) : -32.
[17179642.724000] uvcvideo: Failed to query (130) UVC control 3 (unit 2) : -110

etc

with thanks

Will

---

### Post by encompass on 2006-10-16
You don' have the cam that this forum is talking about.
This Forum is for the "Quickcam Messenger" You have the Quickcam pro 5000, you could try the script mentioned earlier.

---

### Post by foxmajik on 2006-11-05
I'm on Ubunty Edgy amd64.  I think my cam is a Quickcam Messenger.  The built-in USB audio device for recording from the mic was already installed by Ubuntu as soon as I plugged the cam into the USB port.

I didn't need to install the driver for the video device either, as it seems it was already loaded for me by Ubuntu.

$ lsusb
...
046d:08ad Logitech, Inc.
...

sudo apt-get install xawtv

sudo nano /etc/group

[added my username 'josh' to the end of the line for the 'video' group but this didn't fix the ownership issue because the device didn't belong to the video group, so I just chowned /dev/video0 to myself since I'm the only one using it for now]

$ sudo chown josh /dev/video0

$ xawtv&

I got various non-destructive errors because I didn't have the expected font which is hardcoded into xawtv, and because I'm running Beryl Manager through direct OpenGL:

$ xawtv&
[1] 25631
josh@winkypop:~$ This is xawtv-3.95, running on Linux/x86_64 (2.6.17-10-generic)
WARNING: Your X-Server has no DGA support.
/dev/video0 [v4l]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOCMCAPTURE(frame=0;height=144;width=176;format=7): Invalid argument
---

Cam works, I can display video and capture frames, etc.

Thanks for the info.

---

### Post by ximian on 2006-11-06
I am trying to do the same with a Logitech Quickcam 5000 Pro,but i don't think it's a permissions problem because this is my output for "sudo ls -al /dev/video*"
lrwxrwxrwx 1 root root      6 2006-11-06 12:03 /dev/video -> video0
crw-rw---- 1 root video 81, 0 2006-11-06 12:03 /dev/video0
and this is what i get from "xawtv&"
 xawtv&
[1] 19939
ximian@celestialsoul:~$ This is xawtv-3.95, running on Linux/i686 (2.6.17-10-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

[1]+  Exit 1                  xawtv
I finally was able to get the camera running in Ekiga yet,have yet to subscribe to the service,and i really don't know anyone who uses Windows NetMeeting.Forget about Amsn or any other camera apllicable chat programs.I would like to be able to configure the camera for almost anything available,but i guess i am just too impatient waiting for uvc which uses v4l2 api which almost everything else doesn't use,they are still stuck on the v4l,i dunno,guess i am just venting some steam,it's only been a few weeks since i bought the camera,yet i am still more an avid linux/ubuntu user than a windows user.

---

### Post by foxmajik on 2006-11-07
Hello,

It looks like xawtv is trying to use direct rendering but you're not running an x server that's capable of direct rendering.

I'm not sure this is the problem but that's my guess.

If you're looking for a video conferencing solution you might try Skype for Linux.  I think you can install it with EasyUbuntu.  Make sure if you're running Edgy that you rename any files in the EasyUbuntu distro that have 'dapper' in them and change that part of the filename to 'edgy' or you'll get errors.

---

### Post by encompass on 2006-11-13
> **ximian said:**
> I am trying to do the same with a Logitech Quickcam 5000 Pro,but i don't think it's a permissions problem because this is my output for "sudo ls -al /dev/video*"
lrwxrwxrwx 1 root root      6 2006-11-06 12:03 /dev/video -> video0
crw-rw---- 1 root video 81, 0 2006-11-06 12:03 /dev/video0
and this is what i get from "xawtv&"
 xawtv&
[1] 19939
ximian@celestialsoul:~$ This is xawtv-3.95, running on Linux/i686 (2.6.17-10-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

[1]+  Exit 1                  xawtv
I finally was able to get the camera running in Ekiga yet,have yet to subscribe to the service,and i really don't know anyone who uses Windows NetMeeting.Forget about Amsn or any other camera apllicable chat programs.I would like to be able to configure the camera for almost anything available,but i guess i am just too impatient waiting for uvc which uses v4l2 api which almost everything else doesn't use,they are still stuck on the v4l,i dunno,guess i am just venting some steam,it's only been a few weeks since i bought the camera,yet i am still more an avid linux/ubuntu user than a windows user.

With your wanting anyone to see you camera thing... don't worry, got you covered... it is called camserv.... feeds your cam over the webbrowser.
If you need help I can get you started with it.

---

### Post by foxmajik on 2006-11-13
That would totally be made of win, I'd love some help getting camserv setup if it's not obvious from reading the docs.

---

### Post by javierfh on 2006-11-19
> **foxmajik said:**
> Hello,

It looks like xawtv is trying to use direct rendering but you're not running an x server that's capable of direct rendering.

I'm not sure this is the problem but that's my guess.

If you're looking for a video conferencing solution you might try Skype for Linux.  I think you can install it with EasyUbuntu.  Make sure if you're running Edgy that you rename any files in the EasyUbuntu distro that have 'dapper' in them and change that part of the filename to 'edgy' or you'll get errors.

What do you mean skype for linux when you talk about video conferencing?
Does skype for linux support video conferencing? and how?
I thought video conference is not supported in skype for linux.

Please let me know about that...i would be very interested if it works.

Javi

---

### Post by Neo40 on 2006-11-30
I just bought a Logitech Quickcam Messenger. Edgy is able to see it correctly:
```
eric@ubuntu:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 046d:08da Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 
```

Now, I followed the steps on the first post of this thread, but I get problem regarding /dev/video0:

```
Testing if  is correct.
ls: : Aucun fichier ou répertoire de ce type
[!] You don't have read/write access to .
On many distributions, you should add yourself into the
"video" group by giving command
        adduser eric video
and then log in again to be able to access the video.
A quick alternative is just to do
        chmod a+rw 
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
Press Ctrl+C to quit, Enter to continue ---> 

ls: : Aucun fichier ou répertoire de ce type
ls: : Aucun fichier ou répertoire de ce type
[!]  major number is .
Usually it should be 81, so there are problems ahead.
WARNING: If you press Enter, I'll try to continue anyway,
but this probably will fail. You SHOULD press Ctrl+C now.
```

Also, if I run xawtv, I get these errors:
```
eric@ubuntu:~$ xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.17-10-386)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65
```

Anyone can help me? I want my webcam up and running! ;)
Thanks!!!

PS: I'm using Edgy 6.10

---

### Post by encompass on 2006-12-04
they driver show work... but you are using an old driver and trying old instructions on a brand new os.  Please try this one...  But skip the deb... it is not very good any more... the new driver is getting a lot better.
Hope it helps.
[http://ubuntuforums.org/showthread.php?t=191770&highlight=quickcam](http://ubuntuforums.org/showthread.php?t=191770&highlight=quickcam)
Please post there is you have questions about my instructions.  I am using edgy and if I remember, I followed my own instructions.

---

### Post by girlfreddy on 2006-12-20
I have done everything short of ](*,) and I still can't get my web cam to work. I am a newbie, so if someone could please help me get this up and running, I would appreciate it. Oh, and please be specific, 'cause I don't know much. 

lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:08da Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

This next part is from [http://ubuntuforums.org/showthread.php?t=191770&highlight=quickcam](http://ubuntuforums.org/showthread.php?t=191770&highlight=quickcam) which I tried to do and as you see, it failed. I've also done the easycam2 and easyspca, which do show up on my system/admin line, but will not work. Easycam wants to help with installation drivers, but the camera is not being detected. Easyspca is the french version and I click install and it just goes wherever. Just not sure what to do here.

~$ sudo dpkg -i qc-usb-messenger-source_1.1-2_all.deb
dpkg: error processing qc-usb-messenger-source_1.1-2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 qc-usb-messenger-source_1.1-2_all.deb
helene@helene-desktop:~$ wget [http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz)
--06:45:05--  [http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz](http://home.mag.cx/messenger/source/qc-usb-messenger-1.3.tar.gz)
           => `qc-usb-messenger-1.3.tar.gz'
Resolving home.mag.cx... 87.227.67.20
Connecting to home.mag.cx|87.227.67.20|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
06:45:06 ERROR 404: Not Found.

helene@helene-desktop:~$ tar -xvf qc-usb-messenger-1.3.tar.gz
tar: qc-usb-messenger-1.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

I really like ubuntu, but it really has tested my patience. Thanx for your help.

---

### Post by encompass on 2006-12-20
Hint: 404 when your surfing the internet means that the site you typed does not exist.  Looks like the link is really old now.  Let me try to fix it....  One moment.
Here you go...
[http://home.mag.cx/messenger/source/](http://home.mag.cx/messenger/source/)
And click on the newest version of the file. 
Sorry for the problem there.  Your cam should work now, when you follow the instructions.
Try these instructions... they may explain better for you and it is a little more up to date.
[http://ubuntuforums.org/showthread.php?t=191770&highlight=quickcam+messenger+encompass](http://ubuntuforums.org/showthread.php?t=191770&highlight=quickcam+messenger+encompass)

---

### Post by joel_gil on 2007-03-08
i get all the steps easily done, only this last one:

> **maol62 said:**
> 

Finally create a symbolic link so the script is launched at boot:

```
sudo ln - S/etc/init.d/quickcam/etc/rcS.d/S99quickcam
```
Now it works after reboot.

when i type it, i get:
sudo: lnc: command not found

im quite new to all linux, so if theres sth obvious im missin please tell me 

thanks in advance ;)

---

### Post by encompass on 2007-03-09
> **joel_gil said:**
> i get all the steps easily done, only this last one:



when i type it, i get:
sudo: lnc: command not found

im quite new to all linux, so if theres sth obvious im missin please tell me 

thanks in advance ;)

Thanks for the question and great explanation of your issue. notice... "sudo: lnc:" you typed the wrong command.
Type ln not lnc
looks like a simple typo.  you'll get there.

---

### Post by robertwoes on 2007-04-24
i made that script and the symbolic link, but it fails to initialize at reboot.  i installed the driver again and it worked great until reboot

robertwoes@robertwoes-desktop:~$ sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam


robertwoes@robertwoes-desktop:/etc/init.d$ sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam


I made the script and everything... what am i doing wrong please help.

#! /bin/sh
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver.
rmmod quickcam
modprobe quickcam
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/init.d/quickcam" 4L, 115C                               1,1           All

---

### Post by jacquesvn on 2007-05-22
> **robertwoes said:**
> i made that script and the symbolic link, but it fails to initialize at reboot.  i installed the driver again and it worked great until reboot

robertwoes@robertwoes-desktop:~$ sudo touch /etc/init.d/quickcam && sudo chmod 755 /etc/init.d/quickcam


robertwoes@robertwoes-desktop:/etc/init.d$ sudo ln -s /etc/init.d/quickcam /etc/rcS.d/S99quickcam


I made the script and everything... what am i doing wrong please help.

#! /bin/sh
# /etc/init.d/quickcam: reload the Logitech Quickcam Messenger driver.
rmmod quickcam
modprobe quickcam
~                                                                                                               
"/etc/init.d/quickcam" 4L, 115C                               1,1           All


As a quick fix you can try this till I can figure it out:

Find the quickcam.ko that is generated by the script and then code the following into your start up script

> 
#! /bin/sh
modprobe quickcam
rmmod quickcam
insmod /home/jacques/qc-usb-messenger-1.6/quickcam.ko  **#!!!# replace with your path!!**


I have not had a chance to look yet but it appears as if some other incompatible module is loaded on my system with the "modprobe quickcam", I did consider just a find and replace however when I do a insmod alone with the newly generated module it complains, so whatever incorrect module is loading is obviously loading something that is required.

Right now this works for me ... but will fix it sooner or later ... will let u know the outcome then.

By the way my lsub details for my camera are:

Bus 001 Device 004: ID 046d:08f6 Logitech, Inc. 

Next stop usb cam microphone - hate the headset :D

---

### Post by ookami on 2007-05-24
I just installed the Quickcam Messenger drivers. I get video but it's in black-and-white (is looks as if the gamma value is way too high). Has anyone had similar problems?
My lsusb;
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

---

### Post by jacquesvn on 2007-05-24
> **ookami said:**
> I just installed the Quickcam Messenger drivers. I get video but it's in black-and-white (is looks as if the gamma value is way too high). Has anyone had similar problems?
My lsusb;
Bus 002 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

Where did u see this ? In Camorama?

My picture in camorama look like that but in asmn its perfect.

---

### Post by ookami on 2007-05-24
> **jacquesvn said:**
> Where did u see this ? In Camorama?

My picture in camorama look like that but in asmn its perfect.

Colours look wierd in Camorama and OpenWengo but they're ok in Ekiga (but instead ekiga crops the image so I can't see all of it, is this fixed in the Ekiga that ships with Feisty?). I've only tried these programs so far. 
I did have the camera running fine on my Dapper install with the same driver, so I tried some older versions of it as well but to no avail.
My goal here is to get it working with OpenWengo.

---

### Post by encompass on 2007-05-25
Sadly I don't run the camera anymore... I can't help to much.  But I have never seen it in black and white before.  That is very interesting.  I would post to the creators website and best of all give a screenshot.  Sounds like a bug to me.

---

### Post by jacquesvn on 2007-05-25
> **ookami said:**
> Colours look wierd in Camorama and OpenWengo but they're ok in Ekiga (but instead ekiga crops the image so I can't see all of it, is this fixed in the Ekiga that ships with Feisty?). I've only tried these programs so far. 
I did have the camera running fine on my Dapper install with the same driver, so I tried some older versions of it as well but to no avail.
My goal here is to get it working with OpenWengo.

Unfortunately I have never used any of these apps, I use a amsn for video and skype for voice (run both at the same time) The reason for this is the people I chat too are Windows users so and they use MSN and Skype.

I am gonna give OpenWengo a try as I would prefer an all in one solution (just something that I never get round too) - so will let you know if I experience the same problems and if I manage to correct them.

---

### Post by ookami on 2007-05-26
I really don't think the main cause of the problem is the driver, I've had the webcam working perfectly (except for the mic for some reason) with earlier versions of Ubuntu and I tried the version of the driver I used then as well but with the same result.
Anyway I mailed the developer behind the driver and asked if had any idea of what might be wrong.

---

### Post by taiyo on 2007-06-05
Thanks for trying to contact him... I also try to get this working again as it worked in earlier ubuntu versions without a problem...

I also try to get my dvd-writer to be recognized regulary and not after some mystical module-loading and kernel-installing (which doesn't always help).

It looks to me as if Feisty broke some things....

---

### Post by dg88 on 2007-06-25
a quick note to the people that use a usb-hub: It will not work! Plug it in to one of the connectors on the chassi and it will work after that.

---

### Post by proffeecom on 2007-07-09
Hey there! I for one, would  appreciate the effort in making all this into an automatic install(if possible) for Logitech notebook cams. From where I come from (Windows country), I have a close-to-nothing knowledge about Ubuntu and Linux in general. Have a strong desire to learn, though :). Untill then, I would need the "basics" done as easy as possible - web cams being one of them. Appreciate the efforts you guys put in, it just gives an example of what a comunity should rally be all about! Thanks and keep up the good work :) e.

---

### Post by encompass on 2007-07-10
I understand how you feel with this webcam issue.
But one thing that windows users are not used to is that fact that the kernel is where the drivers should be.  Eventually you will be able to install a device by, well, plugging it in.  Wouldn't that be nice?  Well it is already a reality for many things.
Sadly, because logitech things it is a bad idea to release information about there devices.  People have to figure out how they work themselves.  That takes ALOT of time.
Fortunately eventually they are finnished and stable enough to place into the kernel.  At that point you will not need this driver.  Infact, for many people that use this type of came, it is comming true.
If you would like this driver to be put into the kernel so you don't have to manually install the driver, like windows users,  I would goto [http://launchpad.net/ubuntu](http://launchpad.net/ubuntu) and regester something called a blueprint.  When you do this... the developers will see it and hopefully be able to put the driver in.
THAT is what we need.  Spending hours and hours figuring out how all the different version of linux work and how to support them so it is easy for everyone is a waiste of time when the problem is that the driver could have been stable and ready as soon as the cam was invented.  Logitech should have made the driver and made it so it could be built into all kernels.  That brings me to step two... you paid for that cam, have logitech provide the service... call them email them and ask them to make a driver for the linux kernel.
I was one of the people that started this post so long ago... I sold the webcam, why? because I got better quality from a webcam with better driver support.  Simple as that.
I plugged in my oher webcam and it worked.  Why should I have to ever worry about the drivers. :D
Thanks for your support.  If you still need help with your driver, you can Personal Message me.... :D

---

### Post by koolkatkiwi on 2008-02-14
> **amisi said:**
> Hi!

I've use [this](http://doc.gwos.org/index.php/ICM532_webcams)  great HOWTO to get my Logitech WEbCam works, and this solve my problem!

Try it, costs nothing!

This link is dead! What a frustrating thread this is! So MANY dead links! And very complex instructions which then turn out to have typos and don't work. Sigh.

---

### Post by Shadyman on 2008-04-07
Works for me!

:guitar:

Quickcam:
```
matthew@ubuntu:~/Desktop/$ lsusb | grep Logitech
Bus 001 Device 002: ID 046d:08f6 Logitech, Inc. 

```

---

### Post by Limulus on 2008-06-25
On my system:

```
**lsb_release -d**
Description:	Ubuntu 8.04

**uname -s -r**
Linux 2.6.24-19-generic

**lsusb**
Bus 004 Device 006: ID 046d:08f6 Logitech, Inc.
```
I can't seem to get [qc-usb-messenger-1.8]("http://home.mag.cx/messenger/source/") to work; has anyone gotten it working in Hardy?

---


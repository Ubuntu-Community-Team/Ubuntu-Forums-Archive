---
title: "Microdia Driver for Webcam"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by mooscape on 2007-03-03
I have recently purchased a new chinese usb webcam (make _Feida_, not that it matters) that uses the microdia hardware.  The quality in the shop looked good, but it only comes with microsoft drivers. Typing "lsusb" in the  Dapper terminal  finds it easily enough:

> Bus 004 Device 002: ID 0c45:613a Microdia


see attached image.

I have gone through the web on google and on the forums but have not managed to find a way to get this to work.   

APPEAL TO THE LINUX GODS !!!! [-o<

---

### Post by Icarosaurus on 2007-03-05
No way for making this cam work for now...
We have to wait that someone writes a driver.

I've been In contact with [Michel Xhaard]("http://mxhaard.free.fr/index.html") who has the driver in his "to do" list, and with [Luca]("http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=253&forum=3") who esplicitly asked to donate a cam.

At this point I think the best solution is to donate a cam to luca... our cam is very cheap and 4 or  5 person could buy it without problems...I think.

Best regards...


EDIT: Luca's driver works with a kernel version >= 2.6.19

---

### Post by GordSellar on 2007-03-06
So if we upgrade our kernel to 2.6.19, we can use his driver? If we do, will the cam work with various apps, or just Ekiga (as someone suggested elsewhere, I think)? 

And if so, honestly, is upgrading to 2.6.19 a risky thing to try? Should I be worried about crippling my install?

Thanks!

---

### Post by Icarosaurus on 2007-03-10
As everything into linux you should know what you'e doing.
Anyway installing a new kernel is not impossible and there are some guides in this forum.
Intalling a new kernel does not implies you have to delete the old one and you can choose the kernel version at boot for testing.
Drivers should work with every application that supports v4l2.

Which distro do you use?
What's the id of your cam?

Michel Xhaard is working on a v4l2 driver, and (maybe) it will support my Microdia 613a... I hope.

---

### Post by Icarosaurus on 2007-06-12
OUR WEBCAM FINALLY SUPPORTED!
here you can find the latest sn9c1xx driver:
[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")
Thanks to Luca Risolia!
\\:D/

---

### Post by jcronkhite on 2007-06-20
I've followed the instructions in the "sn9c102.txt" file.  Unfortunately, I'm not experienced using make.  There are references in the file which are definitely above my knowledge.  Is there a good step by step tutorial for us "noobs" that might make more sense?  I've been searching hi and low with no luck.  Thanks!

---

### Post by Icarosaurus on 2007-06-21
Hello,
the installation of the driver is quite simple...it needs just some hint (I've found them on the forum).
I'll make a little howto for you and for my future reference:
**1)**Download the latest source (sn9c1xx-X.Y.tar.gz) from site:
[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")
**2)**Untar in a folder, and compile.
Make sure you have downloaded the headers for your kernel from repositories.
```
make
sudo make install

```
**3)** start your driver:
```
sudo modprobe compat_ioctl32
sudo modprobe sn9c102

```
**4)**If you want to start your modules upon system startup, just append the modules into /etc/modules
```
sudo gedit /etc/modules

```
add two lines:
```
compat_ioctl32
sn9c102
```

and save.
**5)**Try rebooting the system and see if it works.
typing:
```
dmesg | grep SN9
```
you should see something like this
```
[   37.760287] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[   37.893405] usb 2-3: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613A)
```


I suggest using the "videoview" program you can find in that site.It's a V4L2 program. Unfortunately most of the programs are V4L1 and the camera will not work within them.
I can use the camera in amsn, but I have to change settings with videoview first because amsn can't control the camera (gives some error).

Let me know!
Bye...

---

### Post by jcronkhite on 2007-06-21
Thanks for the step by step!  I'll give this a shot as soon as I can and will post my results here.  Thanks again!

---

### Post by jcronkhite on 2007-06-22
Works great now!  Hope to see more applications support VL2 soon.  Thanks again!

---

### Post by stevespam on 2007-06-26
Hi Icarosauros!

I own an ACER Notebook (Aspire 5050 Series), which has integrated webcam, as LSUSB showed me:

```
Bus 003 Device 002: ID 0c45:6260 Microdia
```

So, i've just followed your tutorial on how to install this device (yes, i've skipped the readme file), since your step-by-step guide worked both for you and jcronkhite, but unfortunately it didn't worked for me...

So, after following all your instructions and typed: 

```
dmesg | grep SN9
```

I get only this:

```
steve@feisty:~$ dmesg | grep SN9
[   33.734742] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
steve@feisty:~$ 
```

Tried to Start CAMorama, but it returns me the error:
```
Could not connect to video device. (/dev/video0).
```

Do you have any idea of what i've been missing?

Just made a quick view of the readme file (doesn't helps to much, because i'm very new to this) and I saw something about "editing your kernel" to support "Video4Linux and USB", do you think this has something to do about my problem?

```
The following options of the kernel configuration file must be enabled and
corresponding modules must be compiled:

	# Multimedia devices
	#
	CONFIG_VIDEO_DEV=m

To enable advanced debugging functionality on the device through /sysfs:

	# Multimedia devices
	#
	CONFIG_VIDEO_ADV_DEBUG=y

On the contrary, to disable the debugging functionality, it's necessary to both
set CONFIG_VIDEO_ADV_DEBUG=n and remove its definition from the Kbuild file
provided with the SN9C1xx driver.

	# USB support
	#
	CONFIG_USB=m

In addition, depending on the hardware being used, the modules below are
necessary:

	# USB Host Controller Drivers
	#
	CONFIG_USB_EHCI_HCD=m
	CONFIG_USB_UHCI_HCD=m
	CONFIG_USB_OHCI_HCD=m

The SN9C103, SN9C105 and SN9C120 controllers also provide a built-in microphone
interface. It is supported by the USB Audio driver thanks to the ALSA API:

	# Sound
	#
	CONFIG_SOUND=y

	# Advanced Linux Sound Architecture
	#
	CONFIG_SND=m

	# USB devices
	#
	CONFIG_SND_USB_AUDIO=m
```

Sorry, i'm a new user to ubuntu, the main reason i'm annoying you with this question... any kind of reply/hint/post will be more than appreciated.

Thanks.

---

### Post by Icarosaurus on 2007-06-26
Well..it seems that your webcam is not yet supported:
[http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6]("http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6")
check section 9. :(
your cam seems to be not supported by the spca5xx driver too:
[URL="http://mxhaard.free.fr/spca5xx.html"]http://mxhaard.free.fr/spca5xx.html
[/URL]

Camorama doesn't work for me too... it's a v4l1 application...
My cam works with "videoview" by the author of the driver.

The README file refers to the compilation of a new kernel... the default ubuntu kernel works out of the box....

So..maybe you have to wait...

---

### Post by stevespam on 2007-06-26
Icarosaurus,

Thanks for your quick reply, and for your kind support.
Unfortunately i'll still have to wait for a new driver... anyway, thanks to you, i'll stay tunned to the linux-projects.com thanks to you.

Now that i know that Ubuntu does not support my webcam yet, i just need to know, how to install my Card Reader... wich i guess might be "unsupported" as well... i just found tutorials teaching how to install the "Texas Instrument 5 in 1 Card Reader", and for some reason i'm pretty sure that i don't have this one in my notebook... :(

Thanks once again Icarosaurus! :D

---

### Post by Icarosaurus on 2007-06-26
You're wellcome!
Sorry, I can't help you on card readers...
but....bad news:
[http://mavor.com/acer5050.html]("http://mavor.com/acer5050.html")
I hope someone made it work... search...search and never give up :)

Anyway try sending a mail to Michael Xhaard or a message in the forum to Luca Risolia (the sites in my previous post).
Probably Xhaard will ask to you a "snoop" and Luca to donate a cam...
hehe I sent a mail to the vendor of my webcam asking to donate Luca some cam...maybe they really donated and Luca solved the problem :)

---

### Post by daverain on 2007-07-07
Hey all,

Suse user for a year or so; trying Ubuntu for my new laptop. Like it great so far.

My webcam is also Microdia, but Oc45:624f (the SN9C201 controller, I read somewhere). I have a couple of leads, but thought I'd post just in case someone knows if a driver is out there already?

Leads are: "the spca50x guys are working on it, check the gspca package." Haven't followed up on it yet, but will soon and will post results to this thread.

---

### Post by daverain on 2007-07-07
So, as far as I can tell, there is no driver available yet, but apparently more than one developer is working on it. See: [https://wiki.ubuntu.com/LaptopTestingTeam/AsusW7J]("https://wiki.ubuntu.com/LaptopTestingTeam/AsusW7J"). We users owe a big debt to these folks who put a lot of time into reverse-engineering drivers for our hardware and the like. Anyway, I suppose the kit (SN9C201 interface) is fairly new, so it might take a little while to get a Linux driver. I hope it comes soon, but until it does, I can manage.


-David

---

### Post by Icarosaurus on 2007-07-08
yes..I think you have to wait, your webcam is quite new.
Unfortunately reverse engineering takes lot of time and there are few people working on webcam drivers.
I had to wait several months for having a working driver.
Try to contact driver designers, maybe they need your help.
Regards.

---

### Post by Icarosaurus on 2007-07-23
Great news!
Luca Risolia has created a deb package for Ubuntu 7.04, including more supported hardware (maybe some webcam on notebook will be supported).
If you followed my instruction to install the driver, just comment out or delete compat_ioctl32 and sn9c102 in /etc/modules:
```

#compat_ioctl32
#sn9c102

```
and install the deb package of 2.01 version of driver you can find in Luca's site:
[http://www.linux-projects.org/modules/mydownloads/]("http://www.linux-projects.org/modules/mydownloads/")
Restart your computer and check that all went good:
```

dmesg | grep sn9

```
you should see something like this:
```

[   38.931257] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[   40.353881] usbcore: registered new interface driver sn9c102
[   40.445862] sn9c20x: V4L2 driver for SN9C20x PC Camera Controllers v1:2.01
[   40.445866] sn9c20x: (C) 2007 Luca Risolia
[   40.445868] sn9c20x: By using this software, you declare that you have read and accepted the LICENSE included in the 'copyright' file accompanying this software.If not, stop using this software.
[   40.506578] usbcore: registered new interface driver sn9c20x

```
Regards!

---

### Post by nol1ght on 2007-07-23
can he create for amd64 too ? =)

---

### Post by oserdavid on 2007-07-23
I installed the driver simply by clicking on the i386.deb file itself. How wrong was this?

For the first time ever (ie in my very few days trying Ubuntu 7.04 Feisty Fawn out) my webcam (Called PCLine) actually lights up. Audio works (tested through Skype) but still no evidence the video is working, despite the red light.

Running the dsmesg  | grep sn9 command results in the following:

:~$ dmesg | grep sn9
[   96.368000] sn9c20x: module license 'Proprietary' taints kernel.
[   96.440000] sn9c20x: V4L2 driver for SN9C20x PC Camera Controllers v1:2.02
[   96.440000] sn9c20x: (C) 2007 Luca Risolia
[   96.440000] sn9c20x: By using this software, you declare that you have read and accepted the LICENSE included in the 'copyright' file accompanying this software.If not, stop using this software.
[   96.540000] usbcore: registered new interface driver sn9c20x

What does 'taints kernel' mean? Sounds very bad indeed. Or is it just a moral judgement - a rapping over the knuckle for using 'Proprietary' software?

But anyhow - does not seem to be working.

Any thoughts? :confused:

---

### Post by Icarosaurus on 2007-07-24
> **nol1ght said:**
> can he create for amd64 too ? =)
Just ask him :p

---

### Post by Icarosaurus on 2007-07-24
> **oserdavid said:**
> 
What does 'taints kernel' mean? Sounds very bad indeed. Or is it just a moral judgement - a rapping over the knuckle for using 'Proprietary' software?

Well it's not a problem, it just tells the kernel that the driver is proprietary.
Did you try to use the "Videoview" utility present in Luca's Site?
Read back in this thread: not all applications are compatible with Video4Linux2 drivers.
My cam works with aMsn.
How's the output of  "lsusb"?
Regards

---

### Post by nol1ght on 2007-07-24
Someone ask him about this at his forum, have to wait...

---

### Post by oserdavid on 2007-07-24
> **Icarosaurus said:**
> 
Did you try to use the "Videoview" utility present in Luca's Site?
Read back in this thread: not all applications are compatible with Video4Linux2 drivers.
My cam works with aMsn.
How's the output of  "lsusb"?
Regards

Thanks for your response Icarosaurus. 

I couldn't install Videoview - it's a tar.gz package - and I'm afraid it just defeated me (I tried by modifying the instructions on the Adobe Flash site for installing their tar.gz update - but it seemed not to work... If you have detailed instructions for me as a *complete* newbie - I might try again...) In the meantime, running lsusb after I completely removed the driver after it failed to get my camera recognised by any of the usual suspects (eg Camorama, Ekiga, Easycam2, etc) shows, among other things: Bus 001 Device 008: ID 0c45:62bb Microdia. That's without the driver. So the system knows it's there, but that's all.

I'll install aMSN and give it another try...
David

---

### Post by oserdavid on 2007-07-24
... Reinstalled driver, apparently successfully; installed aMSN, OK... but does not recognise webcam is installed - suggests it is because I'm behind a firewall or using a router - both true, I hope - but neither of these things stop my webcams working under Windows XP.. so unlikely to be the cause (?). Now using lsusb gets me the same as before: Bus 001 Device 008: ID 0c45:62bb Microdia. I'll try rebooting the computer - just to see if that makes a difference. Will only report back if it does.
David

---

### Post by Icarosaurus on 2007-07-24
Sorry...I did a mistake
The new sn9c2xx package created by Luca Risolia is only for sn9c201 or sn9c202 based cameras.
If you own an sn9c1xx based cam you still have to install the sn9c1xx driver following my little howto in my previous post:
[http://ubuntuforums.org/showpost.php?p=2887628&postcount=7]("http://ubuntuforums.org/showpost.php?p=2887628&postcount=7")
My webcam works because the sn9c1xx driver keeps installed.

**oserdavid**:your cam should be an sn9c1xx based cam, look for 0c45:62bb in this page:
[http://alpha.dyndns.org/ov511/cameras.html]("http://alpha.dyndns.org/ov511/cameras.html") 

But we have a problem: [according to driver documentation]("http://www.linux-projects.org/modules/sections/index.php?op=viewarticle&artid=6") the bridge-sensor combination of your cam (sn9c102-OV7660) is not supported:
```

Image sensor / SN9C1xx bridge      | SN9C10[12]  SN9C103  SN9C105  SN9C120
-------------------------------------------------------------------------------
HV7131D    Hynix Semiconductor     | Yes         No       No       No
HV7131R    Hynix Semiconductor     | No          Yes      Yes      Yes
MI-0343    Micron Technology       | Yes         No       No       No
MI-0360    Micron Technology       | No          Yes      Yes      Yes
OV7630     OmniVision Technologies | Yes         Yes      Yes      Yes
OV7648     OmniVision Technologies | No          No       Yes      Yes
OV7660     OmniVision Technologies |** No   **       No       Yes      Yes
PAS106B    PixArt Imaging          | Yes         No       No       No
PAS202B    PixArt Imaging          | Yes         Yes      No       No
TAS5110C1B Taiwan Advanced Sensor  | Yes         No       No       No
TAS5110D   Taiwan Advanced Sensor  | Yes         No       No       No
TAS5130D1B Taiwan Advanced Sensor  | Yes         No       No       No

```
Well ...according to this...my cam shouldn't be supported too... so...I think documentation has not been updated.
In fact, looking into the files of the source you can find a "sn9c102_ov7660.c" that makes you hope ;)

So, you should compile the sn9c1xx driver following my instructions. reboot, disconnect and reconnect your cam just before typing in a terminal:
```
dmesg
```
at the end of output you should see something like this if driver works
```
[ 1186.339314] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[ 1186.342582] usb 2-3: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613A)
[ 1186.670880] usb 2-3: OV7648 image sensor detected
[ 1187.640962] usb 2-3: Initialization succeeded
[ 1187.641477] usb 2-3: V4L2 device registered as /dev/video0
[ 1187.641556] usb 2-3: Optional device control through 'sysfs' interface ready
[ 1187.641666] usbcore: registered new interface driver sn9c102

```

The output of lsusb shows you a vendor: product id and it's independent from driver.

tar.gz is an archive. In general, you can decompress a tar.gz by typing (in the directory where is yourarchive.tar.gz)
```
tar -xvf yourarchive.tar.gz
```
..or by right clicking on it and choosing "extract here"

You have to compile the source code for getting videoview to work:
just type, in the decompressed videoview directory (I imagine you know how to reach a directory through the terminal):
```

make
sudo cp videoview /usr/bin/videoview

```
if you rebooted your machine after driver compilation and...of course if driver works, typing videoview anywhere should start the application and recognize your cam.

Let me know!

---

### Post by oserdavid on 2007-07-25
> **Icarosaurus said:**
> Sorry...I did a mistake
The new sn9c2xx package created by Luca Risolia is only for sn9c201 or sn9c202 based cameras.
If you own an sn9c1xx based cam you still have to install the sn9c1xx driver following my little howto in my previous post

Thanks Icarosaurus -but my cam is 'sn9c201 & 202' - at least, that's what it says in its documentation.

So I've given up for the time being. I have another cam - a Creative Live! Cam Voice - which is excellent - but also appears to have no drivers available under Linux, at least, not on any of the sites I've tried. 

For the time being I have resigned myself to the fact that Ubuntu is just for playing around and learning - but it's more convenient for me to stay in Windows XP Pro SP2 for most of the time, since I never know when I might want to chat 'face to face' on line with relatives and friends, and I don't want to start rebooting to a different OS to do so...

---

### Post by Icarosaurus on 2007-07-25
Yes... I've been searching around and your webcam is a sn9c202 actually.
Try disconnecting and reconnecting the cam and see the last part of dmesg to see if it works.
Unfortunately, support of notebook mounted webcams is still under heavy development, because they change every day.

Creative Live! cams are supported by Michel Xhaard drivers... they are still V4L1 so they should work with every program. Check if you find your vid : pid here:
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")
You have to compile these drivers too.. 

The problem is not os, the problem is hardware houses not releasing informations for developing drivers. Anyway I was in the same situation before Luca's driver. I resolved by starting windows in VMWARE and playing with messengers full of advertising and tv spots when I needed them :p

I'm an Ubuntu enthusiasts, because I tried different linux distros and this is the simplest, the easiest and focused on making a powerful operating system suitable for people, not only a game for graduating students in informatics. Moreover It has the best internet community in the net, and you'll always find someone helping you..

Never give up! :)

Anyway if you have a licensed copy of windows with licensed software (I think so, because it seems you have a notebook) and you feel better with it, nothing can stop you to use it... you payed for it! ;)

Regards!

---

### Post by oserdavid on 2007-07-25
Mmmm... bit of work to bring in the bread to do. Nothing to do with computers or IT.

But despite what I said earlier I will persevere in free moments.  Will report back in due course. Many many thanks for your enthusiasm and interest. We definitely need more people like you Icarosaurus!
David

PS - re the Creative Live! Cam Voice - the vid certainly is there. Not the pid, unfortunately. But I've previously tried and failed with Michel Xhaard's drivers, anyway. They do nothing for my Creative cam.

---

### Post by oserdavid on 2007-07-25
> **Icarosaurus said:**
> You have to compile the source code for getting videoview to work:
just type, in the decompressed videoview directory (I imagine you know how to reach a directory through the terminal):
```

make
sudo cp videoview /usr/bin/videoview

```
if you rebooted your machine after driver compilation and...of course if driver works, typing videoview anywhere should start the application and recognize your cam.

Let me know!

No, camera is clearly not supported by the installed 201/202 driver. But - hey, at least it does light up, which promises well for the future! 

Downloaded and installed videoview again - this time as per your instructions. Seemed to install OK. At least no Terminal error messages - just quietly went back to the prompt - which I assume was correct. Rebooted. Ran it by typing videoview in Terminal. It opened up and did not detect the camera. So far, so expected.

But three things puzzle me: (1) Why does videoview not appear as an app which can be clicked on to run; only as something accessible from Terminal? (2) Why can I find no trace of videoview either through add/remove or through Synaptic Package manager? (3) How do I uninstall it? (apart from simply deleting its directory sitting on my Desktop? Or is that it? Seems messy to me, coming from Windows). 

Actually, on second thoughts, I think I'll keep videoview for future testing - but where can I move its directory to - seems messy leaving it on the Desktop... :confused:
David

---

### Post by Icarosaurus on 2007-07-25
Hello oserdavid,
I'll reply to your questions, but I think we're going  off-topic.
Sorry that your cam doesn't work...I think it will be supported soon...
(1) Why does videoview not appear as an app which can be clicked on to run; only as something accessible from Terminal?
   Well, the programmer just didn't work on it...and you don't need that someone chooses where to place an icon for you :) 
You simply can create a link to the program "/usr/bin/videoview" (on desktop or in menus) just as you do in windows (I created my own link on the desktop)
 (2) Why can I find no trace of videoview either through add/remove or through Synaptic Package manager?
   You said, they're package managers. Packages are pre-compiled pieces of software with an automated installation. Videoview is not packaged and it's not present in the Ubuntu repositories. We compiled it from source and made it work. If you were an expert programmer, you could modify the sources and compile your own version...this is open source!
 (3) How do I uninstall it? (apart from simply deleting its directory sitting on my Desktop? Or is that it? Seems messy to me, coming from Windows).
  You can quite remove that directory sitting on your desktop. Once compiled and installed, a program is independent from source.
by doing:
```
sudo cp blah blah blah
```
we installed videoview copying this little program in /usr/bin, so it can be accessible from any directory through the terminal.
if you want to uninstall it ...you simply have to delete it:
```

sudo rm /usr/bin/videoview

```

See you!

---

### Post by SqRt7744 on 2007-08-03
I'm actually really annoyed by this driver for its closed sourceness.  It works for me too, but only with the specific version of the kernel he compiled the module for.  I.e. won't work if you use the low latency kernel, won't work if you use the 2.6.22 gutsy kernel, won't work if you're using any sort of custom kernel at all.  And all this because he won't release the source code for reasons I won't understand....  (and yes I have patched drivers before [cypress_m8 to be specific] and told the world about the patches, not quite the same thing as writing one from scratch, but it's the linux way to share your knowledge)

Luckily there is good news: somebody else is also working on a driver and will hopefully release the code, otherwise this driver can never make it into Ubuntu.  I can hardly wait to get rid of this proprietary crapola.

---

### Post by nicholaspaul on 2007-08-06
I have a Dynex webcam . It's proving to be a little pain!

lsusb tells it's a 0c45:60fb Microdia 

I tried installing the sn9c20x Video4Linux1 and Video4Linux2 driver for Ubuntu 7.04 (Feisty) from
- [http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/) 

(actual link is 
-[http://www.linux-projects.org/modules/mydownloads/visit.php?cid=7&lid=48](http://www.linux-projects.org/modules/mydownloads/visit.php?cid=7&lid=48)).

Installation goes fine, but with Camorama my picture looks like this:
[IMG]http://members.shaw.ca/nicholaspaul/stuff/webcamshot.png[/IMG]

When I install the tar.gz version, I get as far as typing 'make' and this is what happens.


[COLOR="DimGray"]nick@ubuntutu:~/sn9c1xx-1.48$ make
**************************************************************************
* Building Video4Linux2 driver v1.48 for SN9C1xx PC Camera Controllers...*
* Official Linux 2.6.19 is the minimum version for this driver.          *
* Read the documentation "sn9c102.txt" for more informations.            *
* Type "make help" for a list of available targets.                      *
**************************************************************************

make -C /lib/modules/`uname -r`/build M=/home/nick/sn9c1xx-1.48 modules
make[1]: Entering directory `/lib/modules/2.6.20-16-386/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.20-16-386/build'
make: *** [modules] Error 2
[/COLOR]

I've installed the latest version of build-essential. What else should I do?

---

### Post by SqRt7744 on 2007-08-06
@Nicholaspaul: There is no source code for the 201 driver, the source you are trying to compile is not for your webcam, it's for the 1XX series.  The driver you installed is working, as you'll see when you try videoview or qcam.  Camorama requires a V4Lv1 driver, and either there is a bug in the V4Lv1 support in the driver you installed, or camorama itself is buggy... hard to say.  Just try a different app.

---

### Post by nicholaspaul on 2007-08-09
So its all about the app that you use? 
I tried videoview but it wouldnt even recognise the camera. 
Shouldn't Camorama work anyways since VL4 is built into Feisty ?

---

### Post by vivalant on 2007-08-28
There's a single binary-only driver for all the SN9C101, 102, 103, 105, 110, 120, 201, 202 webcams. It supports any V4L1+V4L2 applications and replaces the GSPCA driver (regarding the part of the sn9c1xx controllers). The main difference between the SN9C1XX (in the kernel by default) and  the generic SN9CXXX driver (living outside the kernel) is that the latter has more features and supports more hardware.other than applications.

The author's homepage is [http://www.linux-projects.org](http://www.linux-projects.org)

---

### Post by Icarosaurus on 2007-09-03
Thank you.
This is the newest version of Lucas driver.
It's available as a *.deb package and it's closed source.
So..It could not work for a non-default ubuntu kernel.
Works fine for me.

---

### Post by cokhavim on 2007-09-06
nicholaspaul,

i had the same problem as you with the same webcam.  i figured out why.  you don't need the drivers posted here.  the drivers built into the feisty kernel are sufficient.  the reason why camorama and several other webcam programs gave such a distorted picture is because the automatic resolution is not set to the real resolution of the camera (640x480).  whatever program you're using, try to find where the resolution setting is, and set it to the real resolution of the camera.

cokhavim

---

### Post by vivalant on 2007-09-07
The default driver in the Ubuntu kernel is obsolete. Both the opensource and closed-source drivers at the author's homepage are newer and may support the webcams better. Pay attention to the fact that the opensource version SN9C1xx is based on the new Video4Linux2 interface and supports less hardware (your camera IS supported though), so it won't work with old Video4Linux1 applications. Install the closed source version (Generic SN9CXXX) for Ubuntu instead, which works with all the video applications (v4l1 or v4l2), with  the only exception of camorama, which has bugs, according to the FAQ at [http://www.linux-projects.org](http://www.linux-projects.org)

EDIT: it looks like camorama is working with 2.08

---

### Post by zenum on 2007-10-04
SqRt7744: Do you know any more about this open source driver that might be coming out or if there is anywhere I can read about it? Turns out now you have to pay for any type of driver from the linux-projects site.... The driver would end up costing me more then the camera!

Zenum

---

### Post by funpop on 2007-10-04
so no way to get the sn9c1xx-1.48 driver working on gutsy, since its built for a specific kernel ?
well and if it would work, which applications could use it, since its only V4L2 ?
kopete, amsn, are V4L1 ?? ](*,)


i read about trial-versions on this website, damn are we talking about linux here or windows

edit:

i just followed your howto: this left my system unbootable, had to chroot into this install and remove the module

---

### Post by Icarosaurus on 2007-10-04
I just can't understand the driver's author behaviour...
Anyway my camera became unusable under Gutsy... neither 1.48 nor latest packages are working... :(

---

### Post by vivalant on 2007-10-05
From the FAQ, the author wants Sonix (the manufacturer) or who have the money to buy a GPL license for the SN9CXXX driver. Basically, he's pushing the users to send their complaints and requests to SonIx.

---

### Post by padcitou on 2007-10-26
Hi, I am trying to use a Microdia 0C45:613A, OV7640 sensor + SN9C120 bridge.
Also I have just installed Gutsy Gibbon, so I am running 2.6.22 kernel.
I think I have compiled in the right way the module driver from sn9c1xx-1.48 driver, which is supposed to actually support this webcam. However after I plug the webcam, although I see in dmsg that the kernel recognizes the bridge and the sensor and V4L2 creates the /dev/video0 device, an Oops! appears in dmsg and neither lsusb, gqcam, nor ekiga responds at all, and can't remove the module anymore, even after unpluggin the webcam.

I have read at some thread in [www.linux-projects.org](www.linux-projects.org), that the Oops! is caused by a bug in the kernel, and could be avoided by disabling SYSFS support in module driver, at compiling time i guess.
The point is that i have no idea how to do that, and i need any help..  i feel i am very close to make it work!

Thanks since now.
And sorry my bad english
PAD.

---

### Post by Icarosaurus on 2007-10-31
I have the solution for this frustrating situation.
Buy a still cheap Creative or Logitech camera and use good hardware with open source and FREE drivers.
You can buy a decent camera for 20 or 30 euros.

---

### Post by thewump on 2007-11-11
EDIT: Scratch that - it worked once.

OK.. very weird.

I was fighting with skype to get the Microdia 0c45:62c0 to work on an HP dv6000 and it SEEMED to work in that the blue light came on but no picture.

I read somewhere that even with the right drivers installed ( sorry installed a few weeks back and can't remember what I did! ) you should connect to it with Windows to get it to "wake up".. something about it passing some firmware code to it on first use or something.

Anyway - this makes no sense to me, but just for fun I typed cat /dev/video0 in a terminal and it spewed forth a bunch of junk - then I thought I'd give skype one more try and wammo - works fine.

Have I stumbled upon something useful?

Keith

---

### Post by thewump on 2007-11-11
Me again.. I think I've got it now:

microdia webcam on an HP dv6000

Follow this thread for drivers:

[http://ubuntuforums.org/showthread.php?t=280121](http://ubuntuforums.org/showthread.php?t=280121)

Seems stable with skype

Keith

---

### Post by nwadams on 2007-12-24
dmesg output

[165780.236000] usb 1-4: SN9C10[12] PC Camera Controller detected (vid:pid 0x0C45:0x6029)
[165780.408000] usb 1-4: PAS106B image sensor detected
[165781.080000] usb 1-4: Initialization succeeded
[165781.080000] usb 1-4: V4L2 device registered as /dev/video0
[165781.080000] usb 1-4: Optional device control through 'sysfs' interface disabled


i'm getting that

cam still dosen't work, plz help

---

### Post by vasluianuliviu on 2008-04-08
> **nwadams said:**
> dmesg output

[165780.236000] usb 1-4: SN9C10[12] PC Camera Controller detected (vid:pid 0x0C45:0x6029)
[165780.408000] usb 1-4: PAS106B image sensor detected
[165781.080000] usb 1-4: Initialization succeeded
[165781.080000] usb 1-4: V4L2 device registered as /dev/video0
[165781.080000] usb 1-4: Optional device control through 'sysfs' interface disabled


i'm getting that

cam still dosen't work, plz help

my messages are :for a genius videocam Trek v.20
 /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. SONIX sn9c10[1 2]
[   43.954971] usbcore: registered new interface driver gspca
[   43.954974] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   43.987772] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   43.987782] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   43.987789] atl1 0000:03:00.0: version 2.0.7
[   44.050486] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.44
[   44.050509] usbcore: registered new interface driver sn9c102

and the images are or: bi green(some kind of a green mixture) or bi-yellow(some yellow mixtures)
work but bad images, any ideea of driversf newly for her or else?

---

### Post by Geoffl on 2008-04-18
I am a new user of Ubuntu and am trying to get the peripherals that were working on XP to work on Ubuntu.
I have discovered that it is a Microdia with ID 0c45:6128

Is this supported with any known Linux drivers?

I have tried the drivers mentioned on this thread with not a lot of success.

If it is not supported, as has been said, I will need to go out and buy a cheap supported one.
Any recommendations as to which one to buy if a driver is not available for my current one?

---

### Post by Geoffl on 2008-04-18
I found this link that describes some code changes to GSPCA to support my webcam, but I have no idea how to use this.

[http://groups.google.com/group/microdia/browse_thread/thread/bf525967f4a7b735/dc05bae73b54a52e?lnk=raot](http://groups.google.com/group/microdia/browse_thread/thread/bf525967f4a7b735/dc05bae73b54a52e?lnk=raot)

Can anyone lead me through this with a "step-by-step?

---

### Post by Kuzja on 2008-04-25
Has anyone tried this one? [http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/](http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/)

---

### Post by baya_agaa on 2008-04-26
> **stevespam said:**
> Hi Icarosauros!

I own an ACER Notebook (Aspire 5050 Series), which has integrated webcam, as LSUSB showed me:

```
Bus 003 Device 002: ID 0c45:6260 Microdia
```

So, i've just followed your tutorial on how to install this device (yes, i've skipped the readme file), since your step-by-step guide worked both for you and jcronkhite, but unfortunately it didn't worked for me...

So, after following all your instructions and typed: 

```
dmesg | grep SN9
```

I get only this:

```
steve@feisty:~$ dmesg | grep SN9
[   33.734742] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
steve@feisty:~$ 
```

Tried to Start CAMorama, but it returns me the error:
```
Could not connect to video device. (/dev/video0).
```

Do you have any idea of what i've been missing?

Just made a quick view of the readme file (doesn't helps to much, because i'm very new to this) and I saw something about "editing your kernel" to support "Video4Linux and USB", do you think this has something to do about my problem?

```
The following options of the kernel configuration file must be enabled and
corresponding modules must be compiled:

	# Multimedia devices
	#
	CONFIG_VIDEO_DEV=m

To enable advanced debugging functionality on the device through /sysfs:

	# Multimedia devices
	#
	CONFIG_VIDEO_ADV_DEBUG=y

On the contrary, to disable the debugging functionality, it's necessary to both
set CONFIG_VIDEO_ADV_DEBUG=n and remove its definition from the Kbuild file
provided with the SN9C1xx driver.

	# USB support
	#
	CONFIG_USB=m

In addition, depending on the hardware being used, the modules below are
necessary:

	# USB Host Controller Drivers
	#
	CONFIG_USB_EHCI_HCD=m
	CONFIG_USB_UHCI_HCD=m
	CONFIG_USB_OHCI_HCD=m

The SN9C103, SN9C105 and SN9C120 controllers also provide a built-in microphone
interface. It is supported by the USB Audio driver thanks to the ALSA API:

	# Sound
	#
	CONFIG_SOUND=y

	# Advanced Linux Sound Architecture
	#
	CONFIG_SND=m

	# USB devices
	#
	CONFIG_SND_USB_AUDIO=m
```

Sorry, i'm a new user to ubuntu, the main reason i'm annoying you with this question... any kind of reply/hint/post will be more than appreciated.

Thanks.
i got a PCline 300k webcam
only thing that works now is the green led.
i've tried v4l,gspca.can't solve this cam problem pliz help.

Bus 005 Device 002: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 093a:262a Pixart Imaging, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by padeco on 2008-04-28
hi there!
i still need some help. i have the genius videocam look 300k, uses the microdia ID 0c45:60b0 Microdia

i followed the links described previously, particularly the binary installation for sn9cxxxx. since i installed this file, my camera is no longer turning on when i plug in the usb. this is quire weird.

if any one can shed any light on how the get this cam working, please help.

many thanks.
padeco

---

### Post by Kuzja on 2008-04-28
There is a project which is trying to create drivers for Microdia web cams under Linux:
[http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)
It's very promising but they need your help, so join in and lets bring drivers for our cams to Linux together.

---

### Post by btermeli on 2008-05-16
Hey all,

Im a 8.04 newb and  have a webcam with 0C45: 6128 Microdia output...
My problem is I did step by step what u wrote  but didnt work. I use amsn and skype. I study abroad therefore I need this cam to keep in touch.
All suggestions will be great for me :)

---

### Post by Kuzja on 2008-05-16
Visit the website I posted above ([http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/)) and you might be able to get your camera working.

---

### Post by johnthelemon on 2008-06-20
Hi! My cam is 0x0C45:0x613A, sn9c120 bridge, OV7648 sensor (according to the .inf file), in a SERIOUX USB Toy Web Cam (330k)

lsusb result:
```
Bus 003 Device 003: ID 0c45:613a Microdia 
```

dmesg result:
```
[13802.928000] usb 3-1: new full speed USB device using uhci_hcd and address 3
[13803.088000] usb 3-1: configuration #1 chosen from 1 choice
[13803.092000] usb 3-1: SN9C120 PC Camera Controller detected (vid:pid 0x0C45:0x613A)
[13803.196000] usb 3-1: No supported image sensor detected for this bridge
```

Why  does it say no supported image sensor?

Doesn't work with gspca. 
I've also downloaded the free sn9c102 driver from [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2),
and it compiled succesfully but I can't add the module with insmod, it says
Error -1, Unrecognized symbol

---

### Post by Icarosaurus on 2008-06-21
I have your same camera. There's no driver available in linux.. I lose ages searching and trying to make it work. No way.
So I gave up and bought a wonderful cheap Creative cam.

---

### Post by Kuzja on 2008-06-26
Visit this group: [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) and you may start working to get your camera working!

---

### Post by johnthelemon on 2008-06-28
I got my camera working with the open-source driver at [www.linux-projects.org](www.linux-projects.org), a V4l2-only driver.

---

### Post by Kuzja on 2008-06-28
Good for you! Are there any issues? Share your experience with us
If you still feel like contributing to the community you can check that group [http://groups.google.com/group/microdia/](http://groups.google.com/group/microdia/) and help creating support for microdia web cams on linux.

> and it compiled succesfully but I can't add the module with insmod, it says
Error -1, Unrecognized symbol

For those who will look for the solution in this thread, I believe this issue can be resolved using following command:

> sudo modprobe video

and then insmod

---


---
title: "Did your webcam work out of the box?"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by argotnaut on 2007-01-02
Hello,

I've been doing a lot of reading here about getting webcams to work in Ubuntu. Of course, everyone posts when they have problems, so this means that there are few (if any) posts to say, "Hey, I plugged this one in and it worked right away."

I have also looked at the lists of which cameras are supposed to be compatible, but I would like to hear about real-life situations where you were able to get a webcam to work with little or no tweaking/manual configuration (if such a thing exists!).

I'm running Edgy and am looking for a small, portable webcam that will work well with a notebook.

Thanks!

---

### Post by jobezone on 2007-01-02
[Maybe this can help you?]("http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml") My brother bought a cheap USB webcam, and there was no driver for it for linux.

---

### Post by dvarsam on 2007-01-03
[QUOTE=jobezone][Maybe this can help you?]("http://www.linux.com/howtos/Webcam-HOWTO/devices.shtml") My brother bought a cheap USB webcam, and there was no driver for it for linux.[/QUOTE]

I guess that this was not the question...!!!
People want to be able to plug their USB Webcams & either:

1. The USB Webcam works without any fuss - or installation of drivers, OR

2. The USB Webcam works with just an installation of a package-driver (no additional fuss being involved, no use of Terminal commands, etc etc)

Is there a Webcam out there that can work in such a manner?
That was the question...!!!

Thanks.

P.S.> I am also interested for this, so please respond.

---

### Post by argotnaut on 2007-01-10
Nobody, huh? :( 

I don't mind manual configuration and using the terminal and all, but for this, I'd like to just know that it works for sure before I buy something. Things are too busy right now for a lot of fiddling about.

---

### Post by floflooo on 2007-01-10
I'm also interested because it's a hassle to make my old Logitech quickcam Messenger (046d:08f0) work. I'm sick of half-working hardware and I want to give my money for something that works.

Rejoice, someone mentioned [here]("http://ubuntuforums.org/showthread.php?t=55326") a webcam that works apparently out of the box:
> **Daniel Coquette said:**
> 
I've purchased a **Philips ToUCam II Pro** and Ubuntu detect and use it 
out-fo-the-box :). The Image and the sound works great !

---

### Post by tommcd on 2007-01-10
My Kodak cx7330 (low-budget 3.1 megapixel camera that is a couple years old) has always worked fine with breezy, dapper, and now edgy.
See this thread for getting a camera to work:
[http://ubuntuforums.org/showthread.php?t=286730](http://ubuntuforums.org/showthread.php?t=286730)
EDIT: I just noticed this thread was about WEBcams, not cameras. Sorry!

---

### Post by tmatt95 on 2007-01-10
I have got an old Intel webcam that works under Linux (plug and play)
Regards,
Matt

---

### Post by argotnaut on 2007-01-11
Matt, do you have a model # or anything?

> **tmatt95 said:**
> I have got an old Intel webcam that works under Linux (plug and play)

---

### Post by argotnaut on 2007-01-11
Hmmm, I can't find the Philips ToUCam II Pro around here -- might not be available in the U.S., or maybe just discontinued everywhere. Maybe I'll try another Philips model from the local discount store. I know I can return it there if it doesn't work. If not, then I could order the ToUCam from Singapore on eBay. :/

The other thing I'm concerned about is that I've seen several references to webcams that work if you get an older model (e.g., one with USB 1) but not recent models with the same name. So I'm hoping that someone has experience with something that's currently available.

I might just buy some Philips model this weekend and report back here whether or not it works.

> **floflooo said:**
> 
Rejoice, someone mentioned [here]("http://ubuntuforums.org/showthread.php?t=55326") a webcam that works apparently out of the box:

---

### Post by argotnaut on 2007-01-13
Well, for the heck of it, I tried a Philips SPC 610NC. No luck. I tried Easycam2 first, then installed gspca driver (since I misread [this page]("http://www.lavrsen.dk/twiki/bin/view/PWC/WorkingWebcamsWithPWC"), which said to use the spca5xx driver...but that's for the SPC600NC, not the 610. Oops.). I haven't done any in-depth research, but the little I've found seems to indicate this webcam is not supported anywhere.

In case anyone else is looking around for this later, here's the relevant output of lsusb:

[INDENT]Bus 001 Device 002: ID 093a:2601 Pixart Imaging, Inc. [/INDENT]


So maybe I'll quit messing with this and just order the ToUCam from eBay. Too bad -- the 610NC is a neat little portable camera.

---

### Post by argotnaut on 2007-01-14
Oh yeah -- maybe I should mention that I have an old 3Com Home Connect that did work out of the box. Worked with ekiga, aMSN, GyachE Improved, etc., but not camorama.

---

### Post by dabl on 2007-01-14
No.

I got a Logitech Quickcam. There is good news, and the other news.  The good news is, it can be made to work -- mine is working now with Camerama on Kubuntu Edgy.  The other news is, you have to do it by following the following procedure, discovering the newer download file, figuring out the substitute filenames where they appear, etc. etc.  It is possible, but it's not easy for anyone but a native unix speaker.

[http://www.ubuntuforums.org/showthread.php?t=303330](http://www.ubuntuforums.org/showthread.php?t=303330)

:-?

---

### Post by argotnaut on 2007-01-14
Yeah, I decided to get a Logitech since I had already installed tried to install the driver for another camera by following the instructions in that thread. I changed everything to reflect the name of the newest version of the driver. Bought a Logitech QuickCam Communicate STX, plugged it in and everything worked. :)

Certainly not plug-and-play, but at least I got it going. This is definitely an area that will need improvement for the average user.

---

### Post by jonny on 2007-01-14
If you're in that UK, Tesco sells (or sold - I bought mine a couple of months ago) cheap Technika web cams for £10 that work perfectly our of the box on Dapper and Edgy.

---

### Post by dabl on 2007-01-15
This should be the start of a new thread, but since we're talking dysfunctional USB devices, does anyone know of a method to get the various little memory card readers to work?  I happen to have a real cheapie called "Dazzle", that reads SD cards on a Win XP machine.  It would be nice to use it on the Linux box, but I have no clue what it would take.  ?

---

### Post by argotnaut on 2007-01-15
Yep, that should definitely be a new thread. Try searching for *card reader* first -- there's a bunch of stuff here. I think there are proprietary driver issues in some cases, depending on the device.

---

### Post by s57nev on 2007-03-20
Genius Video Cam Messenger 

lsusb :  0c45:602e    works out of the box....the only thing is brightness levels in amsn / others programs doansn't work on spca5xx drivers. Since edgy kernel could support gspca drivers it just could work ok with gspca...I haven't tried that yet...I'd love to get my brightness and contrast to work...

---

### Post by buildid on 2007-03-20
creative webcam nx ultra , working out of the box ............

---

### Post by noah_parkcity on 2007-03-25
NO! My Logictech QuickCam Chat did NOT work out of the box.

Even though the usually incredible forums provide accurate info, right here they say the
combo is supposed to work out of the box!

[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

Can some smart soul help me? I swore off window$, even converted my dad to Ubuntu. However,  I am an enthusiastic noob

Does anyone know a webcam that does work right out of the box? I need first-hand experience, b/c I already consulted the HLC and my webcam is on there.

I use Ubuntu 6.10

jon@jon-desktop:~$ uname -a
Linux jon-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux

jon@jon-desktop:~$ lsusb
Bus 002 Device 003: ID 046d:092e Logitech, Inc. 
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
 
jon@jon-desktop:~$ /sbin/lsmod | grep -i usb
usb_storage            75072  1 
libusual               17040  1 usb_storage
usbcore               134912  5 usb_storage,libusual,ohci_hcd,ehci_hcd
scsi_mod              144648  5 sbp2,usb_storage,sg,sd_mod,libata


I plug it in, nothing happens

Canorama webcam viewer error:

Cannot connect to video device (dev/video0). please check connection.

EasyCam2 error says: No Camera, No Compatible Camera Found

Ekiga is running V4L but does not see the webcam

When I run:

jon@jon-desktop:~$ lsmod | grep -i spca
jon@jon-desktop:~$
I get nothing.

I see people downloading source for a driver but I don't know how to compile yet.

Is there any other way? OR cookbook on how to get that driver to work?

Help Help! All I want is a webcam to work, any webcam, so I can finally say goodbye to MS.

Thank you to all that have helped other people, as Ive been reading about this for a few days now (rainy saturday).

Thanks!

---

### Post by noah_parkcity on 2007-03-25
ATTENTION n00bs like myself!!!!!!!!!!!!!!!!!

You can get a basic webcam working under Ubuntu 6.10

for 29 bucks, i bought a Logictech QuickCam Chat at chumpusa,

and by following this excellent COOKBOOK recipe by a Kbuntu Guru 

I made the darn thing work!!!  all it took was about 10 hours reading up

on which one to buy and then finding out it was NOT plug and play, and 

then reading a whole bunch more and trying several unsuccessful methods 

(maybe i was doing it wrong) i tried this GURU's method, and bingo!

Now, if you just follow HIS way first, you'll have it done in under 5 minutes!!!!!



 Re: [How to] Logitech Quickcam IM/Connect webcam on Kubuntu 6.10 (Edgy Eft)
Hi,

As I am fully reinstalling my system , it is the webcam turn so I shall try to document whatever I do in order to help.
But I am basically cloning the instructions quite well detailed on the first post.
I hope this helps.
======

STEP 1
Not necessary for me, as I knew already I would need it (ekiga/gnomemeeting does not find it as a device).

STEP 2
I downloaded the new driver from the site [http://mxhaard.free.fr/](http://mxhaard.free.fr/). The file name used that time is: gspcav1-20070110.tar.gz
New versions will have different names.
I copied it to a directory in my home folder that I called ~/lib/webcam.driver.

STEP 3
Skipped it, I preferred to use "sudo".
I opened a terminal (by the way I reduce the size and set it to "always on top").

STEP 4
Similar to former instructions - please follow them:
Quote:
sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential
Quote:
sudo apt-get install gcc-4.1
or
Quote:
sudo apt-get install gcc-4.0
Depending on which is available. Remember this for a later instruction.
As my system was fresh installed, I did get only the compile tools.

STEP 5
Here comes the fun! Instead of moving I just copy to avoid a reload next time...
Quote:
cd /usr/src
sudo cp ~/lib/webcam.driver/gspcav1-20070110.tar.gz .
Please do not forget the space-dot at the end in order to properly copy your file.

Now next actions:
Quote:
sudo tar xfvz gspcav1-20070110.tar.gz
cd gspcav1-20070110
STEP 6
Quote:
export CC=gcc-4.1
If gcc-4.1 was not available :
Quote:
export CC=gcc-4.0
STEP 7
Quote:
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build
STEP 8
First prepare and eliminate the former driver:
Quote:
sudo make
sudo modprobe -r spca5xx
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
Then set and load the new one:
Quote:
sudo make install
sudo modprobe gspca
THE END
Type
Quote:
dmesg
And see results at the bottom (specs will depend on your H/W)
Quote:
[17188664.212000] /usr/src/gspcav1-20070110/gspca_core.c: USB SPCA5XX camera found.(SPCA561A)
[17188664.212000] /usr/src/gspcav1-20070110/gspca_core.c: [spca5xx_probe:3983] Camera type S561
[17188664.220000] /usr/src/gspcav1-20070110/gspca_core.c: [spca5xx_getcapability:1189] maxw 352 maxh 288 minw 160 minh 120
[17188664.220000] usbcore: registered new driver gspca
[17188664.220000] /usr/src/gspcav1-20070110/gspca_core.c: gspca driver 01.00.12 registered
Now it seems ready.
Actually I had to review and redo as I made first a mistake building and then calling the new module (gspcav1 instead of gspca ].

Test with ekiga is SUCCESSFUL ! Now waiting for a linux new Skype version (my contacts use all Skype). Good luck !

See 3 screenshots...
Attached Thumbnails
Click image for larger version Name: ekiga_search devices.png Views: 28 Size: 305.8 KB ID: 22932  Click image for larger version Name: ekiga_webcam found&selected.png Views: 27 Size: 316.6 KB ID: 22933  Click image for larger version Name: ekiga_webcam working.png Views: 51 Size: 402.0 KB ID: 22934  
__________________
Salutacions / Atentamente / Kind Regards / Amicalement / Med vänliga hälsningar / Cumprimentos / Mit freundlichen Grüßen
___________________

Carlos Blanquer-Bogacz
Last edited by cblanquer : January 28th, 2007 at 08:59 AM.

---

### Post by lognok on 2007-04-05
Logitech QuickCam Communicate STX works out-of-the-box.
ID 046d:08d7 Logitech, Inc.
Running Feisty Fawn Herd 5
Only negative thing is I can't get resolution higher than 320x240 and only Ekiga can detect and use the built-in mic.
Otherwise nice picture in dark lighting conditions, although a bit too bright in bright conditions (but I guess it can be adjusted in program somewhere).
Kopete and Wengo works fine with Linux-to-Windows communication although Kopete only has picture and no sound. Wengo has both picture and sound, but quality seams lower.

---

### Post by argotnaut on 2007-04-05
Wow, really? That's the same one I have :)

Maybe Feisty is including the gspca drivers by default now -- but I don't have time to check at the moment.

I installed those drivers manually, and like you, have been unable to get anything to work with the built-in mic. I haven't tested it with Ekiga yet, though.

---

### Post by matchstich on 2007-04-26
i have a cheap camera that just works on ubuntu . used it as a web cam on my old xp box.
but haven't a clue how to make it work as a web cam on here.
it's a concord 1500

do i need to install any packages for that?
thanks

---

### Post by SuperAndy on 2007-04-29
Logitch Webcam Instant

Works brilliantly.

---

### Post by argotnaut on 2007-04-29
I guess this will be a lot easier for many webcams now that the gspca driver is included by default in Feisty.  Logitech QuickCam Communicate STX does work out of the box now. :D

---

### Post by Lothas on 2007-05-03
Logitech quickcam web, the one that comes with Lego Mindstorms' Vision Command didn't work out of the box. I've tried many solutions but it's still not working :(

---

### Post by Limon47 on 2007-05-21
My Logitech Note Deluxe works on 64 bit Ubuntu 7.04. Ekiga produced nice picture but comarama gave bluish picture (plug and play). I was also able to get my Logitech Quick Cam Fusion worked on Ekiga following the guide in this forum but not on comarama and MSN. If there a guide to rectify the bluish colour would be much appreciated and would be another milestone for me as I am very new to Linux. My integrated webcam is not working yet. I am taking one step at a time. Thank you for the help.

---

### Post by sloarch07 on 2007-05-26
> **lognok said:**
> Logitech QuickCam Communicate STX works out-of-the-box.
ID 046d:08d7 Logitech, Inc.
Running Feisty Fawn 

I also had this camera running "out of the box" on Dapper and Edgy.  A great little camera and works great with K/Ubuntu!

---

### Post by bodcod on 2007-10-11
Logitech quickcam connect works out the box:tested on amsn.kopote,camorama and vlc
 ID 046d:08d9 Logitech, Inc.
On Fiesty Fawn and Gutsy

---

### Post by NeillHog on 2007-11-01
Plugged in a Logitech Quickcam Messenger and it worked.
Just like that. At least I can see myself in Kopete so I assume that it works.

Later: As I wrote I could see myself in Kopete so the camera works. When I tried using Kopete to an echo service I found that the microphone did not work. If I chose an echo service that did not use Video then the microphone worked so it seems like I can use the camera or the built in microphone but not both.
Having said that I have not yet found some one to try a "live" connection to. Maybe that works.
If any one finds out how to use camera and microphone together then please let me know.

---

### Post by happy-hippo on 2007-11-01
labtec webcam pro works out-of-the-box in Feisty (thanks Michel Xhaard)
# tail /var/log/messages

Nov  1 23:48:25 tintin kernel: [ 6423.572000] usb 3-1: new full speed USB device using uhci_hcd and address 2
Nov  1 23:48:26 tintin kernel: [ 6423.764000] usb 3-1: configuration #1 chosen from 1 choice
Nov  1 23:48:26 tintin kernel: [ 6424.180000] Linux video capture interface: v2.00
Nov  1 23:48:26 tintin kernel: [ 6424.252000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
Nov  1 23:48:26 tintin kernel: [ 6424.632000] usbcore: registered new interface driver gspca
Nov  1 23:48:26 tintin kernel: [ 6424.632000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
Nov  1 23:48:26 tintin kernel: [ 6424.716000] usbcore: registered new interface driver snd-usb-audio

---

### Post by val67 on 2007-11-01
I think Ubuntu has a *BIG* problem using webcams because there is no way (or at least nobody told me how) to record video/audio from the webcam.

Big, big drawback for someone used with Windows ease of use for webcams.

---

### Post by BatPenguin on 2007-11-04
> **NeillHog said:**
> Plugged in a Logitech Quickcan Messenger and it worked.
Just like that. At least I can see myself in Kopete so I assume that it works.

Hi there,

Great to hear that works. What about the microphone on it? Could you please see if that gets recognized too.

I have  Logitech Quickcam Zoom and getting it to work (had it working in Edgy) is simply terrible (have to either patch kernel or install a new module -- which just actually didn't work), so I'm looking for something that just works. Plug in, camera and mic working in Gutsy, that's what I want. 

Would you mind testing the Messenger's mic for me as well? Thanks!

---

### Post by NeillHog on 2007-11-05
As I wrote in my edit further back -
It is camera or microphone but not both.

Why doesn't some one make an "Ubuntu Plug n' Play Webcam"? I would be the first customer :-)

---

### Post by BatPenguin on 2007-11-05
> **NeillHog said:**
> As I wrote in my edit further back -
It is camera or microphone but not both.

Why doesn't some one make an "Ubuntu Plug n' Play Webcam"? I would be the first customer :-)

Sounds good, I'll be the second one in line :)

Can somebody with the Quickcam Communicate STX confirm that the microphone on it works as well? That cam seems to have a few recommendations for it here, it'd be great to hear a "everything works, go get it" type of endorsement from someone who has used it a bit.

---

### Post by Lothas on 2007-11-18
My webcam didn't work out of the box with Feisty but it kinda did with Gutsy. I have a logitech quickcam web that came with the Lego Vision Command set.

The camera is recognized by every program so far but I can't get any video. At least the microphone is working properly...

---

### Post by thewOndErEr57 on 2007-12-27
If anyone has got to this page(page 4 of this thread I believe), then you've already given up hope I imagine.

Possible solution for you:
I have a logitech quickcam chat for skype, and have written a very simple howto on how to get it to run.

It works with ubuntu gutsy, as that is what I'm using.

Howto here:
[http://ubuntuforums.org/showthread.php?p=4023950#post4023950]("http://ubuntuforums.org/showthread.php?p=4023950#post4023950")

---

### Post by RR1991 on 2007-12-29
I've got this webcam: [IMG]http://www.microcash.info/images/PHILIPS_TOUCAMFUNII.jpg[/IMG]

Never got it working....

---

### Post by luvinit on 2008-01-06
Typhoon webshot 2 seems to work fine. It doesn't mention on the box that it has a microphone so I assume there isn't one, but if there is it doesn't work.

---

### Post by mariosx on 2008-01-16
Creative NX PRO :) working out of the box on Ubuntu 7.10, but not working AT ALL on Kubuntu 7.10 :P

---

### Post by wolfen69 on 2008-01-16
> **mariosx said:**
> Creative NX PRO :) working out of the box on Ubuntu 7.10, but not working AT ALL on Kubuntu 7.10 :P

how long have you had it? if it works really well i'll have to put that on the list.

---

### Post by JuhazOne on 2008-01-19
I bought a Logitech QuickCam Messenger (USB id 046d:08da) yesterday while still using 7.04 Feisty. Kubuntu didn't even recognize the the device (didn't see it with the command lsusb). I upgraded today to 7.10 Gutsy and the webcam seems to work fine now. Software using the cam seems to freeze easily though, will see if there's anything I can do about that.

---

### Post by prog101 on 2008-01-21
I have a simple webcam "Webcam for Dummies" that I bought from Rite Aid for $20. It is an Iconcepts webcam, recognized as Pixart Imaging, Inc. 

dmesg will recognize the added hardware added: USB GSPCA camera found. (PAC207)

To install in gutsy

1. download the latest gspca module source from the web: 
the one below is the latest as of Jan 21, 2008 
[http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz) 

2. rename /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko to gspca.ko.old
sudo cp /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko gspca.ko.old


3. make && sudo make install

4.  sudo cp gspca.ko /lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/

5. remove and load gspca module
sudo modprobe -r gspca
sudo modprobe gspca

Voila, hopefully your webcam will work; mine did!

check with camorama,  amsn, etc

---

### Post by zeusalmighty on 2008-01-22
Yey!!! Partial success!!! The webcam works, but only at 320*240 and is very very dark!!!

Example provided (yes, that's a lamp!!!)

EDIT: For reasons I cannot comprehend, it stopped working and I'm getting the same errors as before, cannot connect to /dev/video0
Mine is a Philips SPC500NC, also recognized as Pixart Imaging

EDIT2: If I install the drivers again, it works as before...any advice?

---

### Post by gcastell on 2008-02-01
I bought a Logitech QuickCam Pro for Notebooks, it works flawlessly with Ekiga, Skype, aMSN and Cheese without any configuration or commands, it didn't work with Camorama though.
By the way, does anyone knows of a good webcam software? Similar to the one provided by logitech for windows.

---

### Post by mariosx on 2008-02-02
> **wolfen69 said:**
> how long have you had it? if it works really well i'll have to put that on the list.

the model i have is this one: [http://us.creative.com/products/product.asp?category=5&subcategory=32&product=628](http://us.creative.com/products/product.asp?category=5&subcategory=32&product=628)

i bought the webcamera in 2002-2003, and i had it working with Ubuntu 7.04 with the spca5xx drivers. But in Kubuntu 7.04 and 7.10, it just didn't work. 

With Ubutnu 7.10 it worked without installing any drivers. Just by plugging it in.

(working programs--> aMSN 0.97 (latest version), Camorama, cheese (only photo, no video -> haven't search about that. maybe i need to set something), and skype finds the camera, sometimes it works, sometimes it doesn't !)

---

### Post by kostkon on 2008-02-14
I bought a *Logitech Quickcam Express Plus* web camera, and it works out of the box!

---

### Post by melopsittacus on 2008-02-22
> **JuhazOne said:**
> I bought a Logitech QuickCam Messenger (USB id 046d:08da) yesterday while still using 7.04 Feisty. Kubuntu didn't even recognize the the device (didn't see it with the command lsusb). I upgraded today to 7.10 Gutsy and the webcam seems to work fine now. Software using the cam seems to freeze easily though, will see if there's anything I can do about that.

Hi, JuhazOne! Have you managed to fix the freezings? By the way, which programs have you tried with the camera? Did you try Camorama?

----------------------
[off]
General question: can I use a webcam for notebooks with a desktop computer, or are they equipped with PCMIA connector?

[/off]

---

### Post by melopsittacus on 2008-02-29
Anyone else using QuickCam Messenger?

---

### Post by mjones41 on 2008-03-01
Creative Labs CAM Notebook Pro Webcam (model VF0250) works out of the box with 7.10
working with Skype 2, aMSN, Ekiga 

No drivers, no mucking around, just plug it in, YaY

---

### Post by linuxnoob40 on 2008-03-01
i bought the logitech communicate stx plus it works out of the box with skype but i cannot see incoming video anyone have any ideas on that?

---

### Post by Dave Otter on 2008-03-01
I bought a Logitech Quickcam Express 2 and it worked Plug and Play.
    I am using Gutsy

---

### Post by Jay Jay on 2008-03-01
A while ago I picked up the Genius Videocam Express V2 for next to nothing and it works out of the box with 7.04: I can take grabs from Camorama with ease.

---


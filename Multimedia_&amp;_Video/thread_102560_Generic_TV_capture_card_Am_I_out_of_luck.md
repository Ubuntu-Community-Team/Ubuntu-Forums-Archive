---
title: "Generic TV capture card: Am I out of luck?"
date: 2005-12-12
forum: Multimedia &amp; Video
---

### Post by eaglescout1984 on 2005-12-12
I bought a video and TV capture card for my computer rather than spend money and waste valuble dorm space for a TV. When I got the thing I was running Win XP, and for the purpose of watching TV I still do.
The card is made by "Easy TV," and the full name of the card is "Easy TV MPEG." It has an input for cable, composite video, S-video and FM antenna.
So, I was wondering if it's possible to find a driver and TV program that works with any NTSC-standard capture card, or if I must continue to be a slave to Windows.

---

### Post by mlomker on 2005-12-12
Support seems a bit limited and Hauppauge is the big name.  You might want to check some of the boards/lists related to [MythTV]("http://pvrhw.goldfish.org/tiki-page.php?pageName=pvrhw_tuners").

---

### Post by linuxgrrl on 2005-12-12
yes, try searching here:
[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

someone may have answered your question.  (it took me a while to find that list so I hope this saves you time )
:KS

---

### Post by poptones on 2005-12-12
Have you even tried to install it? From the way you ask this question it sounds as if you bought it but are afraid it won't work so you haven;'t tried.

Most likely it's a card based on the bt8x8 or the philips chipset and both are pretty well supported in linux via the generic drivers that also support the hauppauge cards. I suggest you just give it a go - my bet is it will work.

---

### Post by eaglescout1984 on 2005-12-13
You learn something new everyday. I figured out where the device manager is and I can actually see more info on it:

Vendor: Philips Semiconductors
Device: SAA7130 Video Broadcast Decoder

So, from what I've seen the IVTV driver should support Haupage and according to poptones, Philips. Please correct me if I wrong on that.
If this is correct then I need some help installing IVTV. If you look at the how to page under [Download and Install]("http://ivtvdriver.org/index.php/Howto#Download_and_install"), it lists three commands. The first command worked fine and of course cd worked, however the third command "make && make install" returned "make: command not found." So, any idea what command I should use?

And BTW poptones, I wasn't afraid. I'm brand new to Linux, so I just didn't have a clue. (But at least I've got more of a clue then when I was using Windows!):lol:

Edit: Fixed link.

---

### Post by mlomker on 2005-12-13
[QUOTE=eaglescout1984]returned "make: command not found." So, any idea what command I should use?[/QUOTE]

You need to install the compiler:

```

sudo apt-get install build-essential

```

---

### Post by poptones on 2005-12-13
Install tvtime from the repository and see what it tells you...

---

### Post by eaglescout1984 on 2005-12-13
Okay, this is what tvtime gives me:

```

Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/ivan/.tvtime/tvtime.xml"
I/O error : Permission denied
Cannot change owner of /home/ivan/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces

```

I haven't been able to install IVTV because of some build files required that aren't included in the Ubuntu package list.

---

### Post by poptones on 2005-12-13
Did you run that installer from the command line? Open a command line and delete the .tvtime folder from your home directory (you will probably have to sudo rm -rf it as the tvtime installer running from the command line doesn't always work properly). Then rerun the installer via synaptic and see what you get. 

What kind of video card do you have? How old is it? And is your system up to date so far as the kernel and patches?

---

### Post by eaglescout1984 on 2005-12-14
I got the exact same thing from above after installing from synaptic.

My video card is about a year old and it's an ATi Radeon 9200. I just got through downloading a driver for it to replace the driver that only supports ATi cards up to 8xxx. And I'm pretty sure the system is up to date, I've downloaded the updates that it said I needed.

---

### Post by poptones on 2005-12-14
Hmmm.. well uyou should be able to compile ivtv from what you've told me just by running "make" and then "sudo make install." But given this oddness with tvtime I'm not sure how it will work even if you get it to compile. Give it a shot and let us know what happens.

---

### Post by whitesox on 2005-12-26
I have the same problem. Every tv application I use (kdetv, zapping, xawtv, TVTime) don't work, and, at least with TVTime, I get the same error. For kdetv, and xawtv, I get a blank screen and X freezes.  I have the ati x300, with the official x300 drivers, and that seems to be the problem.  I got it to work by changing back to the generic ati drivers ubuntu shipped with, because the problem seems to lie with the crappy ATI driver.
To change to the generic ati drivers, you have to edit your xorg config file by doing:```
sudo nano /etc/X11/xorg.conf
```
then change the driver in the selection "Device" to "ati" instead of "fglrx"  then do ctrl-o to write and ctrl-x to quit.  Reboot, and tell me if anything changed.

---

### Post by eaglescout1984 on 2006-01-20
Okay, I changed the driver back to ati and tvtime will work. However, it isn't showing my anything except a general menu. I can't change the input and I don't know where to specify what my video capture card is.

---

### Post by mpvano on 2006-01-20
Are you sure you need to build and install a driver? Look in your /lib/modules/2.6.12-10-386/kernel/drivers/media directory - there are 4 different saa7000 series video drivers there. One of them probably works with your card.

If you want to check this properly, download the kernel sources and read what the source files say, but it's a heck of a lot easier just trying to load one manually.

If you are a beginner at video, I suggest installing xawtv and the xawtv-utilities from synaptics. It's not a fancy tv receiver program, but it's one of the oldest and best maintained and nearly always works. I use it with two older cards under breezy and both of them work very well. The only anomaly is that they need the -noxv switch because my video cards are not configured for the xv extension.

If you find a module that works with your card, you'll need to read the xawtv documentation for more help - there's information there about what other modules are needed.

For what it's worth my cards use the bttv driver (your chip is a later generation of this one) and using it pulls in all the following other modules. You'll have to experiment with what your card needs - it's probably a bit different than this...

video_buf , firmware_class, i2c_algo_bit, v4l2_common, btcx_risc, tveeprom, videodev, tuner, tvaudio, msp3400, snd_page_alloc , snd_bt87x

For what it's worth, the bt878 cards like mine were automatically discovered and installed during the ubuntu installation - I'm not sure how to trigger an automatic installation later on, but it's worth trying to find out.

By the way, are you SURE your modules haven't already been installed automatically by hotplug when you boot?

hope this helps....

Mario

---


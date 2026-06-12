---
title: "HOW-TO: webcam installation (Logitech Quickcam)"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by gluonman on 2007-12-16
Aloha.

Okay. After struggling for a long time to figure out how to install my webcam and finding that there is hardly a good how-to out there that will just give it to you straight up, I finally stumbled across an experienced person on IRC's #ubuntu channel. He walked me through a process and my webcam is working fine now. So I just wanted to post this how-to for others in hopes that it will help the poor souls who are trying way too many roads to failure to get their webcam working like I was not long ago. I can't guarantee that this will work for everyone, but it worked for me just fine. And it probably won't work for all webcam models, and maybe not even all Logitech Quickcam models, but it certainly did for my Logitech Quickcam Express. This is designed to be a very, very newb-friendly how-to.

Step 1: Plug your webcam into a USB slot in the back of your laptop/desktop (best if not a USB hub or some indirect connection).

You need to make sure you have the following installed: Module-Assistant, Camorama Webcam Viewer, (optionally) XawTV, gspca-source, spca5xx-source, and qc-usb-source. To do this, follow the steps below:

Step 1: Open a terminal (Applications --> Accessories --> Terminal) and type exactly what's in Step 2.

Step 2: sudo -s

Step 3: enter your password (same as computer login password) and you will be set as root. Then type exactly what's in Step 4.

Step 4: apt-get install module-assistant camorama xawtv gspca-source spca5xx-source qc-usb-source

Once you have done this and made sure all of those programs are installed and ready to go, follow the steps below:

Step 1:In terminal, type exactly what's in Step 2 to open Module-Assistant.

Step 2: m-a

Step 3: When Module-Assistant opens, highlight UPDATE and push enter (the terminal will say "Starting the Dialog UI...").

Step 4: Wait for the terminal to return to Module-Assistant.

Step 5: Highlight PREPARE and push enter (the terminal will begin to download or update whatever needs downloading/updating).

Step 6: Push enter when the terminal prompts you to do so in order to get back to Module-Assistant when it's finished with the preparation.

Step 7: Highlight SELECT and push enter.

Step 8: Scroll down until you reach qc-usb.

Step 9: Mark qc-usb with an x by pushing the 'space' key then push enter.

Step 10: Highlight BUILD and push enter (the terminal will prompt you to push enter to continue to build the qc-usb package).

Step 11: When you return to Module-Assistant highlight INSTALL and push enter (the terminal will begin to install the packages you just built).

Step 12: When you return to Module-Assistant highlight BACK and push enter (this will take you back to the package selection page).

Step 13: Scroll down until you reach spca5xx.

Step 14: Mark spca5xx with an x by pushing the 'space' key then push enter.

Step 15: Highlight BUILD and push enter (the terminal will prompt you to push enter to continue to build the spca5xx package).

Step 16: When you return to Module-Assistant highlight INSTALL and push enter (the terminal will begin to install the packages you just built).

Step 17: When you return to Module-Assistant highlight BACK and push enter (this will take you back to the package selection page).

Step 18: Scroll down until you reach gspca.

Step 19: Mark gspca with an x by pushing the 'space' key then push enter.

Step 20: Highlight BUILD and push enter (the terminal will prompt you to push enter to continue to build the gspca package).

Step 21: When you return to Module-Assistant highlight INSTALL and push enter (the terminal will begin to install the packages you just built).

Okay. Now you can feel free to close the module-assistant and terminal. Now restart your computer. After rebooting, access Camorama Webcam Viewer (Applications --> Graphics --> Camorama Webcam Viewer). When the viewer opens it should display your webcam stream and you can adjust the brightness, contrast, etc. to your liking. At this point you should be all set to use your webcam with Kopete, aMSN, or whatever Linux chat server you use that has a webcam feature.

I should mention that when I completed these steps, rebooted my computer, and opened Camorama, my webcam ran for a random number of seconds and then froze. This kept happening even after several reboots and I simply could not figure out how to fix the problem. Even when I opened Kopete and ran my webcam there it froze all of Kopete. I always had to force quit to get out of it. To be honest, I still never figured out how to fix this problem, but once when I tried opening XawTV (Applications --> Sound & Video --> XawTV) to see if I could view my webcam there, it opened and I saw my webcam stream and waited for it to freeze but it never froze. It kept running. Ever since then it will run freely without freezing in Camorama and in Kopete. I don't know what happened, but at least my cam is working now. So if you experience the freezing like I did, maybe running XawTV once will do the trick. Or maybe not, I have no godly idea. I'm simply reporting my experience.

I hope all of this helps. Let me know if there's anything wrong with any of the steps.

---

### Post by gluonman on 2007-12-16
If anyone happens to know exactly what the deal is with the freezing problem suddenly seeming to correct itself, feel free to shed some light on that because it might help people get past that if they have the same problem but don't seem to get over it as painlessly as I did.

---

### Post by reyasuk on 2007-12-16
I too have spent weeks looking for a solution to get my webcam working, Logitech Orbit, but none of the howtos got it working.  So when I saw your tutorial pop up in my inbox I was filled with hope again!  I got as far as building spca5xx but it failed.  I'm quite new to linux and I haven't done much compiling yet, so I'm stuck again.  If you, or anyone else, can offer me a helping hand I'd really appreciate it. :confused:
This is the end of the log file -

CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26 error: linux/config.
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function 'spca50x_init_
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment f
make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1
make[3]: *** [module /usr/src/modules/spca5xx] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [default] Error 2
make[2]:  Leaving directory `/usr/src/modules/spca5xx'
make[1]: *** [binary-modules] Error 2
make[1]:  Leaving directory `/usr/src/modules/spca5xx'
make: *** [kdist_build] Error 2

---

### Post by rohedin on 2007-12-16
> **reyasuk said:**
> I too have spent weeks looking for a solution to get my webcam working, Logitech Orbit, but none of the howtos got it working.  So when I saw your tutorial pop up in my inbox I was filled with hope again!  I got as far as building spca5xx but it failed.  I'm quite new to linux and I haven't done much compiling yet, so I'm stuck again.  If you, or anyone else, can offer me a helping hand I'd really appreciate it. :confused:
This is the end of the log file -

CC [M]  /usr/src/modules/spca5xx/drivers/usb/spca5xx.o
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:39:26 error: linux/config.
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c: In function 'spca50x_init_
/usr/src/modules/spca5xx/drivers/usb/spca5xx.c:1681: warning: assignment f
make[4]: *** [/usr/src/modules/spca5xx/drivers/usb/spca5xx.o] Error 1
make[3]: *** [module /usr/src/modules/spca5xx] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [default] Error 2
make[2]:  Leaving directory `/usr/src/modules/spca5xx'
make[1]: *** [binary-modules] Error 2
make[1]:  Leaving directory `/usr/src/modules/spca5xx'
make: *** [kdist_build] Error 2

The exact same happened to me :(

---

### Post by iperich on 2007-12-16
My experience with Ubuntu 7.10 is the same of you but my webcam keep freezing with xawtv or any other software i use...

:(

It's weird, i used my webcam with Kubuntu 7.04 and i was happy like the princess at the end of the tale...

Maybe is a Gnome issue????

EDITED:

I tried with and older, cheaper webcam. A piece of junk, actually. It works fine... but my webcam, a Logitech Quickcam for Notebook Deluxe appears to be too much Deluxe for Ubuntu 7.10 :(
maybe a bug??

---

### Post by tatjun on 2007-12-16
I didn't succeed in building and installing spca5xx, but I could still make my Logitech Quickcam work by following the rest of the steps. I'm just a beginner, but I'm inclined to agree with Iperich that it could be a gnome issue.

Thanks gluonman for the clear and easy steps. Your help is appreciated.

---

### Post by GlennW on 2007-12-17
Thanks gluonman for the how-to. I have a Logitech QuickCam Ultra Vision. I've been searching the threads for days looking for the answer. I did manage to get it running but couldn't get it to sync with Skype. Apparently there are many out there in the forums with the same webcam but no one has spilled the beans on how they got it working.

Anyway, I followed you steps and had a successful reboot. However, upon clicking on Camorama, an error pops up: 

[INDENT]Could not connect to video device (/dev/video0). Please check the connection.[/INDENT]

I'm a gutsy/linux noob so please be plain.

Greatly appreciated.

---

### Post by gluonman on 2007-12-19
Okay, GlennW. I had actually had the same issue at first with camorama not detecting /dev/video0/ but for me it seemed almost to correct itself after a couple of reboots. For that reason, at this moment in time, I cannot personally give you a solution if you are still having that issue simply because I don't really know. Maybe I did something but I cannot say what. One thing that I do know is that despite the fact that it has been done that ubuntu users have gotten their webcams to work (usually after much grief), webcams and Linux simply don't seem to get along that well these days.

For those of you who were having difficulty with spca5xx, like tatjun suggested, it may not be completely necessary anyway as long as you have gspca and qc-usb. Since I made my post, I have come across people who managed to get their cam working despite lacking spca5xx. So if you're having difficulty getting spca5xx to install properly, I'd say just see if you can still get your cam working without that step.

---

### Post by GlennW on 2007-12-19
Thanks gluonman for the response. I'll keep on digging, fiddling, and generally not giving up. I've got several nieces and nephews who are dying for an online Christmas with their uncle. 

Thanks again.

---

### Post by gluonman on 2007-12-19
Yeah, I can understand that. I have a romantic interest over in the Philippines who had just been dying and dying to see me somehow. I really hope your nieces and nephews get to see you.

---

### Post by gmh on 2007-12-19
Greetings all

My problem with video was that the video would freeze after 10 to 20 secs but the call would continue. There was no interruption to the audio at all and I could stop and restart the video ok. The video would freeze again after it was restarted (normally within the same time frame).

dmesg | grep cam
[ 19.088000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX)


After much reading (ironically on a windows forum where there seem to be a number of freezing issues with some of the latest Skype releases) and a bit of playing around I discovered that if I remove all other USB devices the video works just fine. The main culprit at this stage seems to be a logitech USB wireless mouse although if I am on a video call and I plug in my ext hardrive the video will freeze as well. Once the drive is plugged in and I restart the video it will continue running just fine.

I have no idea what the reason is but for anyone else having video issues it might be something to check.

Cheers

---

### Post by iperich on 2007-12-28
I have exactly the same issue, after reading your post i tested my logitech webcam for notebooks deluxe without any other usb device (a logitech wireless mouse in my case) and the camera works fine without any problem for hours.

It seems to be a bug, right?

---

### Post by ANNbot on 2007-12-29
> **rohedin said:**
> The exact same happened to me :(

With a little help from the following posting:
[http://ubuntuforums.org/archive/index.php/t-442552.html](http://ubuntuforums.org/archive/index.php/t-442552.html)


I went looking around and found that config.h does not exist. I tried creating a symbolic link to the autoconf.h  fie (see two setps below) which from what I understand the replacement for config.h:

cd /usr/src/linux/include/linux/

sudo ln -s autoconf.h config.h

then I opened m-a again and started at step 14... compiled ok after that:):)

---

### Post by oldHat on 2008-01-11
> **GlennW said:**
> 
<snip!> 

However, upon clicking on Camorama, an error pops up: 

[INDENT]Could not connect to video device (/dev/video0). Please check the connection.[/INDENT]


Greatly appreciated.

If everything else seems ok, and you're only fighting with camorama, here's what worked for me.

I opened Device Manager from the System->Administration menu , then browsed though all the USB devices until i found a USB video device.  On the "advanced" tab, it showed that the device was "registered" at  /dev/video2, which is not the camorama default.  In my case, "camorama -d /dev/video2" was all it took in order to make camorama detect the right video device instead of using the default.

---

### Post by creperum on 2008-01-21
Thanks muchly to gluonman for that thorough, clear, and easy-to-follow post, much appreciated by this relative newbie.  And thanks to ANNbot for the fix for that problem in the compiling, which I had also, but fixed following his/her advice....

c

---

### Post by gottabeandrew on 2008-05-04
> **gluonman said:**
> Step 10: Highlight BUILD and push enter (the terminal will prompt you to push enter to continue to build the qc-usb package).

At this point, it told me that it couldn't do it because i didn't have the source or something like that. What do i do to fix this? Is there a source i need?

---

### Post by zutronius on 2008-06-26
Everytime I try to build the last two packages, it says they fail. ???

---

### Post by Melindrea on 2008-06-26
Second package fails, and can't even find the third module. Though, at least lsusb shows my webcam, so that's a start, no? =)

---

### Post by HuXu on 2008-07-05
I'm on a Dell Latitude D531 and I have a Logitech Quickcam and I'm on Hardy Heron (completely updated) Does this tutorial still work? Because I get to BUILDing qc-usb and i get

error message-  Bad luck, the kernel headers for the target kernel version could  not be found  and you did not specify other valid kernel headers to use.

Im guessing that i need to wait for the qc-usb source to update? if im wrong let me know.

---


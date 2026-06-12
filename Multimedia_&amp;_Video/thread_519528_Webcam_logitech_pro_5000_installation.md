---
title: "Webcam logitech pro 5000 installation"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by abuntu-handicapped on 2007-08-07
I am at a dead end.

I have logitecg pro 5000 in ubuntu. trying to load it. i think i have tried everything and have read over 100 forums but have not been able to solve it.

I have tried installing easycam2, ekiga, camorama, camstream, XAWTV, aMSNeasywebcam.

Easycam2 - No camera, or no compatible camera found
Ekiga - blocked
camorama - could not connect to video device (/dev/video0)
camstream - opens grey windows. i pick device - the device experienced an error - no such device. (I MUST NOTE THAT I CHOSE USB VIDEO CLASS DEVICE.THERE IS NO MENTION OF LOGITECH ANYTHING)
XAWTV - i have a black screen. i can click on capture image or clip and the light on the web cam comes on but nothing is shown.
...anyways...


i have installed spca5xx and as far as i am aware i did it correctly but now im stumped. 

can anyone help?

EDITED:

This looks promising but i am battling to follow the instructions. can somebody please help me with this

Hi
I had the same problem.
I installed the spca5xx module from [http://mxhaard.free.fr/spca50x/Downl...0051001.tar.gz](http://mxhaard.free.fr/spca50x/Downl...0051001.tar.gz)

you have to install the kernel headers
aptitude install linux-headers-2.6.12-9-386

you have to delete the old spca5xx module
cd /lib/modules/2.6.12-9-386/kernel/drivers/usb/media
mv spca5xx spca5xx.bak

then you need the gcc version with which the kernel was compiled:
cat /proc/version
Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu) #1 Mon Oct 10 13:14:36 BST 2005
gcc 3.4

aptitude install gcc-3.4
then untar and go to hte spca5xx directory
then

$ MAKEFLAGS="CC=gcc-3.4" make
$ make install
and at least you can re-do the modules list with:
depmod
depmod -ae

If you want to try the new module, be sure that you don't have loaded the old one with
lsmod |grep spca5xx
if yes, you can do:
modprobe -r spca5xx

then plug you webcam and the module should be loaded automaticaly

I hope you could add this email to the forum thread. ([http://ubuntuforums.org/showthread.php?p=377397](http://ubuntuforums.org/showthread.php?p=377397)) I tried but I could do it. As you see some things are easy for some people and other not

---

### Post by jnorthr on 2007-08-07
Is the camera a USB connection - if it is not, the USB VIDEO CLASS DEVICE may conflict with it. Do you have a windows partition you can boot into ? Perhaps if you can get the webcam working under windows then at least we know the hardware is correctly in place, then we can eliminate the possibility of a hardware glitch and just focus on the driver issues. You will probably not see logitec names (or any other manufacturer) in device driver names - though some do.
Here is a link where someone else is having similar problems : [https://answers.launchpad.net/ubuntu/+question/3743](https://answers.launchpad.net/ubuntu/+question/3743)

---

### Post by abuntu-handicapped on 2007-08-07
Hi jnorthr,

Yes it is a USB webcam. Windows partition? unfortunately not, it is just ebuntu on this machine.

I checked out the link you attached. I have found many people with the same problem and not many people get the problem sorted (t seems) and the people that do get it sorted - their solution does not solve my problem...unfortunately

---

### Post by abuntu-handicapped on 2007-08-07
i managed to get the web cam working in ekiga. i dont know if this is such good news or not because it does not look like i can record or play video clips. Is this correct? i hope not...

still struggling with easycam, camorama, and everything else but if someone can tell me how to record a video clip in ekiga, ill give up on the others.

PS. Is ekiga and ekiga softphone th same thing? i have ekiga softphone

---


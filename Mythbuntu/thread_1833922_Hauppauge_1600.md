---
title: "Hauppauge 1600"
date: 2011-08-26
forum: Mythbuntu
---

### Post by maryhigginsrice on 2011-08-26
[SIZE=2][B]Hi everyone.  I am having a terrible time trying to receive an analog signal in "live Tv" in mythbuntu 11.04.  I am using the Hauppauge 1600(113.  I have configured both halves of the tuner, but I only want to use the analog half of the card.  I fI use the digital half I have to setup a remote, which is another problem.  When I try to view live tv I receive a red screen.  I read in one of the numerous articles and post that the v4l driver is not supported in this kernel.  Is that statement true?  I have searched the gossamer mailing list and could not find any help.  I have Comcast Cable, which the feed is coming from the wall.  I have it attached to the tuner via coax cable.  I have setup the lineups in Schedule Direct and it still fails.  I am lost.  Can someone please help me figure this out.  mary  :(
[/B][/SIZE]

---

### Post by klc5555 on 2011-08-29
First off, make sure the analog 1600 is configured as an "MPEG-2 encoder" (or however it's precisely worded in your mythtv backend setup) and not as a "V4l-analog" card. "V4l-analog" will not work for this card.

Assuming this doesn't fix the problem straight away ...

From your original post it's not quite clear which precise version (of the multitude of them) of this card you have. You'll need to know this. The basic overview of the major card models (though not of all the analog tuner variants they use) is to be found here: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

Of these models, all of the older ones (including those which are listed as not supporting QAM in Windows, which makes them cheap to purchase) now work pretty much out-of-the box (including QAM) with current-ish Linux kernels and vanilla cx18 drivers (say the version of 2.6.38 in Ubuntu 11.04) There are some much newer varieties of the Hauppauge 1600 that apparently require a patched cx18 driver in order to properly identify the precise flavor of Philips analog tuner at bootup and module load. To see what version of tuner the driver believes is there, from a prompt

dmesg | grep cx18

or similar should yield you the bootup messages pertaining to this driver. The cx18 driver should have identified the tuner with a tuner=<some number>, which may (or may not) be the correct one. Or it may kick back a message like "tveeprom not found!" which means you likely found the problem.

Sometimes, however, if you don't have one of the latest revisions of the 1600 card, the problem is simply that the card didn't quite initialize correctly at boot. To test this, you can generally reload the module by hand from a prompt by:

sudo killall mythbackend
sudo rmmod cx18_alsa
sudo rmmod cx18
sudo modprobe cx18
sudo mythbackend -d

and see whether the card can now get something on analog. Assuming Comcast still provides any analog signal whatever to your locale, or you're receiving a channel 3 or channel 4 signal from your cable box.

If, however, you have one of those latest 1600 cards, you may have a bit more of a problem, requiring either compiling your own cx18 driver from the most recent .git source at linuxtv.org, or, if this doesn't resolve the problem, possibly first patching that cx18 source and then compiling your driver. The most recent cx18 patches were too recent for the 2.6.39 kernel tree; I haven't kept track of this issue pursuant to the 3.0 series kernels, since I don't run them yet and my 4 Hauppauge 1600 cards are all older models.

The most recent "red screen" discussions had here in this thread: [http://ubuntuforums.org/showthread.php?t=1720207&highlight=red+screen](http://ubuntuforums.org/showthread.php?t=1720207&highlight=red+screen)
eventually led emunson to obtain patches to the cx18 driver from the driver's developers, which he reports solved his red screen problem. (emunson's relevant discussion with the cx18 developers Andy Walls and Devin Heitmueller is to be found here: [http://www.mail-archive.com/linux-media@vger.kernel.org/msg30106.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg30106.html) )

---

### Post by PatrickD-52761 on 2011-09-04
I had this same issue, and solved it by removing the digital tuner on the cards from my setup. If you're not going to be using the digital tuner (due to the remote issues that you mentioned) I would remove it until a proper solution can be found for all of your issues.  Although I'm not sure if the red screen can be fixed.

Hope this helps, and have a great weekend :)
Patrick.

---

### Post by doogiekd on 2012-01-03
friends, 

i got my hvr-1600 to work by doing the following:

1. download the driver & firmware from: [http://ivtvdriver.org/index.php/Download](http://ivtvdriver.org/index.php/Download)

direct download address of driver: [http://dl.ivtvdriver.org/ivtv/archiv...-0.10.6.tar.gz](http://dl.ivtvdriver.org/ivtv/archiv...-0.10.6.tar.gz)

direct download of firmware: [http://dl.ivtvdriver.org/ivtv/firmwa...irmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmwa...irmware.tar.gz)

2. extract both files by right clicking and selecting "extract" 
an error may appear indicating: 
"this does not look like a .tar archive."

the workaround to extract both the firmware and driver files is:
a. install gunzip. from terminal enter: sudo apt-get install gunzip

b. after gunzip is installed, open terminal and change directory to where both files are - usually desktop. ex: cd \Desktop. 

c. enter in terminal: gunzip filename.tar.gz (replacing file name with the name of driver. enter this command again to do the same for the firmware. ex. sudo gunzip ivtv-firmware.tar.gz & sudo gunzip ivtv-0.10.6.tar.gz

d. change permissions of both files by entering in terminal:
sudo tar xvzf filename.tar - replacing filname with both the driver file and firmware file as described above.

e. once extracted, in terminal change to the directory of the driver file (usually cd \Desktop\ivtv-0.10.6.tar.gz

f. enter sudo build. program will install. let finish and do not interrupt the process.

g. install the firmware. in terminal enter sudo nautilus. be careful, errors doing sudo nautilus can be deadly to your system. (gksu did not work for me here).

h. the root file manager will open. move all files AS INDIVIDUAL FILES (not the folder) from the FIRMWARE directory to \lib\firmware. some firmware files are the same in both the ivtv driver and ivtv firmware folders. just copy all of them as individual files and choose replace when prompted. yes, the ivtv driver will contain some firmware files.

i. close the terminal and nautilus.

j. open the app: STARTUP APPLICATIONS.

K. in startup applications, click ADD. 

l. enter "tv tuner card detect" in the DESCRIPTION field.

m. enter the following in the command field:
ivtv-tune -t us-bcast -c 3 -d /dev/video0

you may have another location for your tv tuner card - video1, ect...

n. shut down your computer.

o. add a coaxial splitter from the output of your cable box. one end will connect to your tv, the other end will connect to the ANALOG input of your tv tuner card.

p. turn on the computer. your tv tuner card should now work. try first in movie player and vlc.

q. go to /dev/video0 (or video1, ect), right click on the tv tuner card and select open with movie player.

r. yes, you will only receive the channel that the cable box is currently set to only.

s. tv-viewer in my opinion is the best app for single recording. add the tv-viewer ppa to your software sources. in terminal type:
sudo deb [http://ppa.launchpad.net/blueyed/ppa/ubuntu](http://ppa.launchpad.net/blueyed/ppa/ubuntu) oneiric main

t. update software sources by entering in terminal: 
sudo apt-get update

u. install tv-viewer from synaptic.

v. IMPORTANT: you will probably have to repeat most of these steps after EVERY kernel update.

enjoy, doogiekd.

---


---
title: "HVR-1600 Red Screen"
date: 2011-04-03
forum: Mythbuntu
---

### Post by emunson on 2011-04-03
I have the capture card being recognized properly by the kernel, but when I try and watch live TV, all I get is a RED 4:3 square on my TV.  I cannot seem to get it to select any digital channels either (I have a mix of analog and digital channels available and have coax running to both inputs on the card).  I have tried removing all the capture cards and video source information (I use SchedsDirect) from the backend and re-adding it but nothing is helping.  What is causing this problem?

---

### Post by emunson on 2011-04-03
Missing some info there.  I am running Mythbuntu 10.10 with mythTV 0.24.0+fixes.20110330

I am running the stock kernel, but had to build the cx18 drivers from source to recognize the hvr-1600 at all

---

### Post by klc5555 on 2011-04-03
Sometimes the cx18 doesn't load quite correctly at bootup. Usually when that happens, showing a variety of symptoms including no picture, degraded audio, etc., this can be fixed (until the next reboot) by unloading and reloading the cx18 module.

To test this, stop the mythtv back end. (Mythbuntu is annoying in that it requires this before playing with the cx18 module) 
Then:
 sudo rmmod cx18_alsa
 sudo rmmod cx18

Then: 
 sudo modprobe cx18

Now restart the backend. See whether the 1600 tuner now operates more-or less normally.

---

### Post by emunson on 2011-04-03
That did not help, I still only get a red screen off of the analog input.  DVB works fine on this card.

---

### Post by klc5555 on 2011-04-03
Then it could be that the cx18 has mis-identified the precise analog tuner, since Hauppauge uses so many different ones in this card; or it could possibly be one of the tuner varieties that the cx18 developers have only recently patched support for. At least two newer varieties, I believe, the 74301 and the 74321 are only scheduled for proper support beginning with 2.6.39 series kernels. According to [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600)

So you may have to obtain the exact info on your card and contact the cx18 developers over at linuxtv.org

---

### Post by emunson on 2011-04-03
Their advice was to build the drivers from source, which seemed to work (dmesg shows that the card is initialized properly).  Just to be sure, I started running 2.6.39-rc1 and the problem still occurs.

---

### Post by klc5555 on 2011-04-03
Sorry then. If cx18 developer Andy Walls and company can't help you with this card, then certainly I can't. 

The only thing I might recommend is to return this particular card (if possible) and replace it with one of the older and better-supported 1600 variants.

---

### Post by emunson on 2011-04-03
Thanks for your help, I will post a solution if I find one.

---

### Post by emunson on 2011-05-09
The solution is several kernel patches that are now in the linux-media kernel and should go upstream for .40.  I can post pointers to the patches that fixed the issue if anyone wants them.

---

### Post by oregonbob on 2011-05-12
I have a Hauppauge HVR 1600 that worked fine on 10.04 and 10.10 but under 11.04 I can't get any application to work. dmesg shows it loads cx18 ok. I normally use Kaffeine to watch ATSB digital TV in USA.

I would like links to the patches you found.

---

### Post by nowhere@cox.net on 2011-06-02
emunson: Could you please post the links to the kernel patches? I'm having the same issue with the analog tuner.

Thanks!
Eric

---

### Post by fireflymoon on 2011-06-04
Hi, I have the 74301 model also...would be interested in knowing patches also. Thanks!

---

### Post by emunson on 2011-10-16
Sorry I missed these requests, here is the post I made to the ubuntu bug on this issue:
> 
They are not yet in Linus' tree, but Andy Walls (the cx18 maintainer) has them in his tree. The three that made the difference are here:

[http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=bb4307140fc3e91ca2d36d6bb54dc3f0266ec481](http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=bb4307140fc3e91ca2d36d6bb54dc3f0266ec481)
[http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=ff8af8319fe3d6d42e2814d6e01cc35a32d58d3b](http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=ff8af8319fe3d6d42e2814d6e01cc35a32d58d3b)
[http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=a61bc93554afc9074d08aeb015cf395c7a26ea14](http://git.linuxtv.org/awalls/media_tree.git?a=commit;h=a61bc93554afc9074d08aeb015cf395c7a26ea14)

These three actually add support for the newest HVR-1600 model, there are five bug fixes that I applied as well to make the tuner work more reliably:

[http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/5b5bb17be43d](http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/5b5bb17be43d)
[http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/74abea7eeba8](http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/74abea7eeba8)
[http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/722df4fda0a7](http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/722df4fda0a7)
[http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/4e703f422fae](http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/4e703f422fae)
[http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/68dcec20b6e9](http://kernellabs.com/hg/~mkrufky/tda18271-fix/rev/68dcec20b6e9)

The first three enable the hardware, the last five made it reliable.


---

### Post by doogiekd on 2012-01-03
friends, 

i got my hvr-1600 to work by doing the following:

1. download the driver & firmware from: [http://ivtvdriver.org/index.php/Download](http://ivtvdriver.org/index.php/Download)

direct download address of driver: [http://dl.ivtvdriver.org/ivtv/archive/0.10.x/ivtv-0.10.6.tar.gz](http://dl.ivtvdriver.org/ivtv/archive/0.10.x/ivtv-0.10.6.tar.gz)

direct download of firmware: [http://dl.ivtvdriver.org/ivtv/firmware/ivtv-firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/ivtv-firmware.tar.gz)

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


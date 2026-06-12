---
title: "Hauppauge WinTV-HVR 1600 TV card"
date: 2010-07-13
forum: Mythbuntu
---

### Post by kkimes on 2010-07-13
I have this card in my PC and have added a dual-boot for Ubuntu 10.04.  Do I have to install Mythbuntu in order to be able to use the card?  Or can I get it to run under Ubuntu?  I wasn't even worrying about the card when I installed Ubuntu 10.04, but it would be nice to be able to use it if possible.

---

### Post by LowSky on 2010-07-13
Mythbuntu is a derivitive of Ubuntu, the only difference is it come preinstalled with a program called MythTV.

You can add mythtv easily from the software center or synaptic on your current install.

see this link to help get it to work
[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

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

### Post by chuckrp on 2012-03-03
I have this card working in a Dell computer. I am running Mythtv and it is working at recording TV from the antenna. I can set it to record shows on different channels at different times with no problems. I problem I am having is the sound level. It is recording shows with a low sound level. I can watch the TV only with a volume of 20-25. I can go online using the Chrome browser in the computer and watch Youtube, etc with the same volume. When I watch recorded shows from the card I have to turn the tv up to 85-90 to get volume from the shows. Does anyone have any suggestions?
Thanks

---

### Post by nickrout on 2012-03-03
> **chuckrp said:**
> I have this card working in a Dell computer. I am running Mythtv and it is working at recording TV from the antenna. I can set it to record shows on different channels at different times with no problems. I problem I am having is the sound level. It is recording shows with a low sound level. I can watch the TV only with a volume of 20-25. I can go online using the Chrome browser in the computer and watch Youtube, etc with the same volume. When I watch recorded shows from the card I have to turn the tv up to 85-90 to get volume from the shows. Does anyone have any suggestions?
Thanks

analogue or digital recording?

---

### Post by chuckrp on 2012-03-21
I am using an antenna and recording the digital channels.

---

### Post by nickrout on 2012-03-21
> **chuckrp said:**
> I am using an antenna and recording the digital channels.

Its just because the digital audio is usually lower than the analogue audio you are used to.

---


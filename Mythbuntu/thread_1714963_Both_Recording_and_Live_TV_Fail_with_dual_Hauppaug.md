---
title: "Both Recording and Live TV Fail with dual Hauppauge HVR-1600 cards installed"
date: 2011-03-26
forum: Mythbuntu
---

### Post by PatrickD-52761 on 2011-03-26
I'm not sure exactly what to say here.  I have a homebuilt computer with an AMD Athalon XP 1800+ processor and 2 GB of RAM (and an ATI Radeon 9550 Video Card).  In the computer, I have two Hauppauge HVR-1600 tuners which are connected to my cable provider via analog (yes they still support it).

The cards are shown correctly in dmesg and in mythbackend. I have them configured to use my cable provider (via scheduledirect) and have the guide downloaded and updated in my MySQL database.  However, when I attempt to record a program, or watch TV through the mythfrontend, it fails.  When watching a program, I get the screen which says "Please Wa...." and then it goes back to the menu.  When I try to record, it starts, and then comes up with an error about the bit rate on my audio being wrong, and stops.

I had to clear out my logs completely in order to paste them through the Log grabber.  So, the logs at [http://mythbuntu.pastebin.com/xtP9HaU2](http://mythbuntu.pastebin.com/xtP9HaU2) just contain the latest attempt at watching TV (however, I'm more than happy to update my guides and try to record something to get more information).

Also, I have another Linux computer, which has XBMC installed. I connected it to my mythbackend, and attempted to watch TV through it.  It shows me the guide, and when I click on a channel, the screen flickers for a bit and then comes up with an error.

I have no idea what more information is necessary, but I'll be more than happy to answer any questions and provide anything.  I will say that I have NOT tried to compile my own drivers/firmware using the linuxtv information. I'm using the stock drivers/firmware that comes with Ubuntu 10.10 (and any updates).  I did add the vmalloc=192M to my GRUB, because originally I was getting an error about that (suggesting that I modify page.h, which I didn't do per the mythtv wiki pages).

Thanks for any help, and have a great day:)
Patrick.

---

### Post by klc5555 on 2011-03-26
By "shown correctly" in mythbackend, you mean "MPEG-2 encoder card (PVR-x50, PVR-500)"? If you have the analog set up as "Analog V4L capture card", they won't work.

You should not have to recompile the cx18 driver; the one in 10.10 is plenty recent enough for analog. Digital too, in most cases.

---

### Post by PatrickD-52761 on 2011-03-26
> **klc5555 said:**
> By "shown correctly" in mythbackend, you mean "MPEG-2 encoder card (PVR-x50, PVR-500)"? If you have the analog set up as "Analog V4L capture card", they won't work.

You should not have to recompile the cx18 driver; the one in 10.10 is plenty recent enough for analog. Digital too, in most cases.

The options that I have in Mythbackend are Analog V4L Capture Card, MJPEG capture card (Matrox G200, DC10), IVTV MPEG-2 encoder card, H.264 encoder card (HD-PVR), DVB DTV capture card (v3.x) (doesn't show my card), Firewire Box (doesn't show my card), USB MPEG-4 encoder box (Plextor ConvertX, etc), HD Homerun Box, Network Recorder, and Import Recorder.  So, I'm not sure which one to set it up as (I would guess the IVTV MPEG-2 card, but I want to be sure first).  Currently they're both set up as V4L Capture Cards.

Ok, I tried the MPEG-2 option and I have TV now :D  And I have Picture-in-Picture, which is something that I never had in Windows Media Center (so that alone makes this better, IMHO).  One more question though.  In my options, it only shows Tuner1.  Or, it shows Tuner1, S-Video1, Composite 1, S-Video2, Composite2 (but no Tuner2).  If I connect a cable to Tuner2 on the cards, will it show up then? (I'm asking because I may set it up with both Analog and OTA Digital at some point in the future, plus someone else may want to try this).

I'll mark this as solved.  Thank you very much :D

Have a great day:)
Patrick.

---

### Post by klc5555 on 2011-03-26
"Tuner1" on each card refers to the analog tuner you have just connected via coax and set up. The other coax input on each card (assuming you don't have one of the flavors of the 1600 that has 3 coax inputs, when the 3rd one is for FM) will be for digital. The backend setup should recognize them as "Samsung" something or other, and will set up the digital as though it were a card completely separate from the analog one. (That is, not "Tuner2") If you splitter your cable and connect to these digital coax inputs on your cards, you should be able to set them up in the backend, then scan for and receive whatever clear QAM digital signals your cable provider is sending along with the analogs. Usually the locals (probably also in HD).

I say "should be able" because the digital setup with these cards in Linux can be a bit fussy, particularly regarding signal strength, depending on the precise version of the 1600 you have (there are a lot of them) and the vintage of the cx18 driver (the one in 10.10 should be fine).

---

### Post by PatrickD-52761 on 2011-03-26
> **klc5555 said:**
> "Tuner1" on each card refers to the analog tuner you have just connected via coax and set up. The other coax input on each card (assuming you don't have one of the flavors of the 1600 that has 3 coax inputs, when the 3rd one is for FM) will be for digital. The backend setup should recognize them as "Samsung" something or other, and will set up the digital as though it were a card completely separate from the analog one. (That is, not "Tuner2") If you splitter your cable and connect to these digital coax inputs on your cards, you should be able to set them up in the backend, then scan for and receive whatever clear QAM digital signals your cable provider is sending along with the analogs. Usually the locals (probably also in HD).

I say "should be able" because the digital setup with these cards in Linux can be a bit fussy, particularly regarding signal strength, depending on the precise version of the 1600 you have (there are a lot of them) and the vintage of the cx18 driver (the one in 10.10 should be fine).

Thanks for the information. I have the Model 1183, which apparently (according to the box at least) has the 3 coax connectors.  Which means that I need another splitter, as I'll be watching OTA Digital and listening to the radio on the same antenna.

Thanks, and have a great day:)
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


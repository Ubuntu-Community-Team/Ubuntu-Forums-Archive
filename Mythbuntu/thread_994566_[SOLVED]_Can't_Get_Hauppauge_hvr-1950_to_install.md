---
title: "[SOLVED] Can't Get Hauppauge hvr-1950 to install"
date: 2008-11-26
forum: Mythbuntu
---

### Post by ACGarib on 2008-11-26
Hi, I bought a USB tv tuner (hvr-1950) to use with mythbuntu that I installed on my ubuntu laptop.

I plugged the tuner in and opened up mythbuntu, but it doesn't detect my tuner.

I did a lot of research and found out i needed to install some firmware to /lib/firmware/[uname -r]

I did that and now none of my USB stuff works anymore.

lsusb now just hangs until I close the terminal

If I unplug the tuner, restart the computer, and retry typing lsusb, I get output, but as soon as I plug the tuner in again, I get non functional USB.

Also, when I go to /dev, I don't see anything that pertains to my tuner.

Anybody have any suggestions?

I have read that this tuner works with mythbuntu, but I can't figure out how to get it to work.

Thanks,
Andrew Garibian

---

### Post by hairfarmer88 on 2008-11-30
The newer kernel broke something in the driver.  Check out this site:

[http://www.isely.net/pvrusb2/pvrusb2.html](http://www.isely.net/pvrusb2/pvrusb2.html)

There is a setting you need to add I think it was something like initusb or such.

---

### Post by ACGarib on 2008-12-01
Thanks. I did the workaround: 

Quote from [http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html](http://www.isely.net/pipermail/pvrusb2/2008-October/001918.html) :

Alternatively, putting the following into a file anywhere under 
/etc/modprobe.d/ should work even better:
  options pvrusb2 initusbreset=0


I did this and I now get /dev/video0
doing ```
 gmplayer /dev/video0 
``` or using VLC now works (about 25% of the time). When it doesn't work, I have to run a script I made that stops LIRC, mythtv-backend, pvrusb2, then starts pvrusb2, LIRC, and mythtv-backend. ```
sudo /etc/init.d/lirc stop
sudo /etc/init.d/mythtv-backend stop
sudo rmmod pvrusb2
sudo modprobe pvrusb2
sudo /etc/init.d/lirc start
sudo /etc/init.d/mythtv-backend start
``` I have a feeling mythtv-backend is behind the instability because not restarting it makes things a lot more stable. Whenever the backend is running, LIRC will inevitably freeze.

Using "watch tv" in mythbuntu almost always resulted in a black screen for half a second then I am back at the main menu. After a lot of tinkering around, I found out that when I check /var/log/messages by doing: ```
tail -f /var/log/messages
``` I see mythtv-backend requesting some firmware and never receiving it. Simply restarting mythtv-backend clears this up and "watch tv" suddenly works.

So now the basic cable is viewable in mythbuntu, mplayer, and VLC.

I also receive 9 HD QAM256 channels that I want to view, so I hit 'm' to bring up the menu while I'm watching TV, and go to select a different input, but there is no option for it. I then go to view the status of the tuners, and it says the DVB tuner is not available.

I decided to try using mplayer, so I did: ```
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-Cable-Standard-center-frequencies-QAM256 > channels.conf
``` to generate a channels.conf, which I moved to .mplayer in my home directory. I then did: ```
gmplayer dvb://
``` to get channel 3.

So now I get HD in mplayer.

This is where I am now, and I have no idea how to get HD working in mythbuntu, how to change channels in mplayer,how to enable deinterlacing in mplayer, or how to get VLC to play HD.

Any ideas?

Thanks,
Andrew

---

### Post by ACGarib on 2008-12-02
After a few more hours of messing around, I finally got mythbuntu working!:)

What I did was go to the backend configuration, select the dvb tuner card, go to recording options, and check the open on demand option and uncheck the use the card for EIT option.

I can't remember if that step added the option to select a different tuner in the menu while watching TV, but somehow this happened. Selecting the digital tuner brought up errors and a black screen for about 30 seconds.

I rescanned the channels, but I still had problems with multiplexing, so I changed the channel numbers of the digital channels to ones that aren't also NTSC cable channels. (For example, KYW-DT was 31, which MTV is on basic cable) I just reassigned the channel number to 3.1 so it is next to the analog version of the channel as I flip through the channels.

This got live tv working!

Feeling confident, I tried to enable the remote by selecting the option "Hauppauge TV card" under the Mythbuntu Control Centre.

Now my remote works! (sort of) Sometimes pressing the buttons doesn't register and one time I hit the channel up button and froze mythbuntu. Otherwise it works.

So now I have a Hauppauge HVR-1950 TV tuner's NTSC, QAM, and remote working with Mythbuntu 8.10. :guitar:

I don't get any ATSC signals here, but that should work if the QAM works. I also didn't test the SVideo and composite inputs yet. the PVRUSB2 driver doesn't support FM yet.




My only question now is: I am getting an external HDD that will be NTFS. I am planning on putting backups and recorded videos on it. Windows will also need to use every now and then. It is my understanding that NTFS doesn't do permissions, yet mythbuntu requires the recordings to be owned by mythtv and be part of the mythtv group. Since I can't change the permissions from my username to mythtv, how can I get the recordings to the HDD? (I don't want to use my ubuntu partition to store a recording then transfer it over because my partition is only 10 GB.)

EDIT: Nevermind about the question. I tried using my external ntfs drive and it worked. I guess the recordings folder doesn't need to be owned by mythtv and part of the mythtv group after all. Some other misconfiguration must have been causing the problems. I guess everything is working now.




Feel free to ask questions.



resources:
[http://www.mail-archive.com/pvrusb2@isely.net/](http://www.mail-archive.com/pvrusb2@isely.net/)         this contains info on the driver
[http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards](http://www.mythtv.org/wiki/index.php/Adding_QAM_Channels_For_HDTV_Tuner_Cards)           this helped me set up a channels.conf for mplayer 
[http://ubuntuforums.org/showthread.php?t=577854](http://ubuntuforums.org/showthread.php?t=577854)           this also helped set up a channels.conf
changing channels in mplayer: h and k

---

### Post by williamts99 on 2009-09-27
I was wondering if you tried the s-video and composite inputs yet.

---

### Post by deadland on 2009-10-12
Hello guys,

I have problems get LIRC with the HVR 1950 running correcly. It would be great if you could post your working hardware.conf.

Thanks in advanced.

---

### Post by greenwom on 2010-03-07
I can't get any of this to work....

the card is recognized, I am using the latest firmware from the dev (noted above).

I can't even scan for channels........

---


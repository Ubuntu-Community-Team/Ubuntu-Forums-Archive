---
title: "KWorld ATSC 115 Setup"
date: 2007-04-25
forum: Multimedia &amp; Video
---

### Post by Zero7 on 2007-04-25
I am total newbie to linux . I  have gone through several threads in thi forum and others to find out "how to set up" KWorld 115 in Feisty.
This is the output for "lspci" command.
> 00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G965 Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
02:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
02:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
04:01.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


I have followed all the steps from [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) guidelines and have the dvb_firmware nxt2004 firmware copied to location /lib/firmware.

Here is the results for command "cat /var/log/mythtv/mythbackend.log"
> 2007-04-25 20:17:13.721 Using runtime prefix = /usr
2007-04-25 20:17:14.215 New DB connection, total: 1
2007-04-25 20:17:14.476 Connected to database 'mythconverg' at host: localhost
2007-04-25 20:17:15.112 Current Schema Version: 1160
Starting up as the master server.
2007-04-25 20:17:16.922 New DB connection, total: 2
2007-04-25 20:17:17.612 Connected to database 'mythconverg' at host: localhost
2007-04-25 20:17:18.069 EITHelper: localtime offset -7:00:00 
2007-04-25 20:17:18.478 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2007-04-25 20:17:19.052 ChannelBase(3) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2007-04-25 20:17:19.152 EITHelper: localtime offset -7:00:00 
2007-04-25 20:17:19.215 TVRec(4) Error: Problem finding starting channel, setting to default of '3'.
2007-04-25 20:17:19.249 ChannelBase(4) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-04-25 20:17:19.254 Main::Starting HttpServer
2007-04-25 20:17:19.354 Main::Registering HttpStatus Extension
2007-04-25 20:17:19.473 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-25 20:17:19.625 Enabled verbose msgs:  important general
2007-04-25 20:17:20.067 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2007-04-25 20:17:20.166 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2007-04-25 20:24:29.867 Using runtime prefix = /usr
2007-04-25 20:24:29.890 New DB connection, total: 1
2007-04-25 20:24:29.895 Connected to database 'mythconverg' at host: localhost
2007-04-25 20:24:29.897 Current Schema Version: 1160
Starting up as the master server.
2007-04-25 20:24:29.902 New DB connection, total: 2
2007-04-25 20:24:29.903 Connected to database 'mythconverg' at host: localhost
2007-04-25 20:24:29.905 EITHelper: localtime offset -7:00:00 
2007-04-25 20:24:29.909 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2007-04-25 20:24:29.910 ChannelBase(1) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2007-04-25 20:24:29.911 EITHelper: localtime offset -7:00:00 
2007-04-25 20:24:29.913 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2007-04-25 20:24:29.914 ChannelBase(2) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
2007-04-25 20:24:29.915 EITHelper: localtime offset -7:00:00 
2007-04-25 20:24:29.917 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2007-04-25 20:24:29.917 ChannelBase(3) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2007-04-25 20:24:29.920 Main::Starting HttpServer
2007-04-25 20:24:29.921 New DB connection, total: 3
2007-04-25 20:24:29.922 Connected to database 'mythconverg' at host: localhost
2007-04-25 20:24:29.925 Main::Registering HttpStatus Extension
2007-04-25 20:24:29.930 mythbackend version: 0.20.20060828-3 [www.mythtv.org](www.mythtv.org)
2007-04-25 20:24:29.930 Enabled verbose msgs:  important general
2007-04-25 20:24:29.931 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2007-04-25 20:24:29.934 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min


If some one could help me getting this card working it will be highly appreciated.
[LIST=1]
[*]How do I check if the card is installed correctly?
[*]How do I check if th MythTV is installed Correctly?
[*] I have TV time television viewer and Xaw TV also installed. But they do not show any output on the screen  or do not show the Tuner card under setup
[/LIST]

---

### Post by newlinux on 2007-04-26
Are you able to scan stations in mythtv-setup? Have you created and input and assigned an input to the card? Do you have any other cards setup?

---

### Post by Zero7 on 2007-04-26
Thanks for the reply. Finally I was able to scan analogue channels in TV time television viewer and Xaw TV, but not in mythtv.
> **newlinux said:**
> Are you able to scan stations in mythtv-setup?  
 I was not able to scan the channels in MythTV setup. When I try to scan the channels, I see a message, error opening the card or similar one.
> **newlinux said:**
> Have you created and input and assigned an input to the card? 
I am not clear on this portion. I have only one tuner card and under mythtv set up, it shows it as Kworld 110 (not 115). I have added it multiple times under Analogue, Digital etc. I am not in front the m/c now and do not remember exact names.
> **newlinux said:**
> Do you have any other cards setup?
No. Only this card.


Please help me with setting up the card in mythTV.

---

### Post by newlinux on 2007-04-26
> **Zero7 said:**
> Thanks for the reply. Finally I was able to scan analogue channels in TV time television viewer and Xaw TV, but not in mythtv.
 
 I was not able to scan the channels in MythTV setup. When I try to scan the channels, I see a message, error opening the card or similar one.
 
I am not clear on this portion. I have only one tuner card and under mythtv set up, it shows it as Kworld 110 (not 115). I have added it multiple times under Analogue, Digital etc. I am not in front the m/c now and do not remember exact names.

No. Only this card.


Please help me with setting up the card in mythTV.

I don't have a kworld 115, but it should work just like a 110 from what I've seen from others. Sounds like you just haven't assigned an source to the card, but other than that the card is working. 

What you want to do is follow this:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O#head-84f0869db0546e10c7d6e35b21f40081205ff1e2](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop_O#head-84f0869db0546e10c7d6e35b21f40081205ff1e2)

and setup a video source, and assign it to an input, and then try scanning. If you do this and still have problems let us know.

If you want to use it for QAM or ATSC set it up as a DVB card.  If you have problems with it as a DVB card, try setting it up as V4L (analog) defining another video source for analog stations, assigning that input and then scanning for channels. If this works and the QAM/ATSC doesn't, there is probably something setup wrong with the DVB driver.

---

### Post by newlinux on 2007-04-26
make sure you stop your backend before running mythtv-setup.

---

### Post by Zero7 on 2007-04-26
Cool, the link you have provided looks better compared to [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend) for new users like me.. more GUI based  :)

I will try tonight and update here.

---

### Post by Zero7 on 2007-04-27
NewLinux, you were right.Thank You!
I was able to scan analogue and ATSC channels after setting up Video Source. I have few more problems now... 

[LIST=1]Analogue Channels do not scan beyond Channel 13 [/LIST]
[LIST=1]No Audio yet- haven't spent time checking all the steps again... will have to try...[/LIST]
[LIST=1]I am not able to change from Analogue to ATSC in mythtv front end. As per myth guide, i should be able to do it by typing C on keyboard![/LIST]
[LIST=1]HD Channel did not display anything or I am not able to change the channel from there... I am not sure if it is the On board video (Intel GMX3000) - 965G chipset.I may need a better graphics card..[/LIST]

---

### Post by newlinux on 2007-04-27
I don't immediately have ideas on most of these, except that I'm not sure how well intel video plays with myth for now... My intel graphic based laptop does the same thing, but it is less powerful than the 965G, I believe.

How did you set up the analog and digital portions? Did you setup two different cards? Or did you get an analog options button?

---

### Post by Zero7 on 2007-04-27
> **newlinux said:**
> 

How did you set up the analog and digital portions? Did you setup two different cards? Or did you get an analog options button?
I set it as two cards. One Analogue and one DVB.
Is there a way to get QAM and ATSC scanned & saved? I read NOT, but as per Kworld QAM and NTSC is same input and ATSC is the other.

---

### Post by newlinux on 2007-04-27
> **Zero7 said:**
> I set it as two cards. One Analogue and one DVB.
Is there a way to get QAM and ATSC scanned & saved? I read NOT, but as per Kworld QAM and NTSC is same input and ATSC is the other.

It won't work properly if set up as 2 cards, and the current version of myth in repositories doesn't allow you to properly set it up as one card with an analog and dvb input. See the end of [http://ubuntuforums.org/showthread.php?p=2536735](http://ubuntuforums.org/showthread.php?p=2536735) for more info on how to do it in the repo build. It will require some tweaking of the database, and is still has a little issue.

If you don't want to do that, until there is an updated myth with the svn fix in the ubuntu repos, you'll have to choose between having it as an ATSC/QAM tuner or an NTSC tuner. In windows, the QAM and NTSC are the same input and ATSC is the other, however in Linux the driver makes the ATSC/QAM tuner the same input and the NTSC input separate. More info about that is in the thread I linked above too.

---

### Post by Zero7 on 2007-05-01
> **newlinux said:**
> I don't immediately have ideas on most of these, except that I'm not sure how well intel video plays with myth for now... My intel graphic based laptop does the same thing, but it is less powerful than the 965G, I believe.



Yesterday I installed WinXp home by replacing the hard disks and installed total media player that came with Kworld TV Tuner. I had to remove the tuner card to install WinXP or it would not get installed. I installed WinXP home, service pack 2, McAfee AV, Total Media player, Intel graphic Media accelerator. Before installing Intel GMA software, CPU usage was as high as 40 to 50% and after enabling graphic media acceleration, CPU usage fell down below 5% in HD. 

Somehow I feel that Ubuntu still does not support the 965 chipset and can't use the hardware capabilities. There may be workarounds for experts:(

---

### Post by biker19 on 2007-05-03
I'm in the same boat - my Vista set up seems OK and I can't get the Ubuntu set up. I can't get HDMI sound working and support for anything ATI is iffy.

---

### Post by syntheticexctasy on 2007-05-08
I'm pretty new to linux myself, and am having a really tough time getting this card to work. I've scanned NTSC channels and can get them to work in tvtime and mythtv (without sound), but I can't get what I really want which is atsc/qam.

Any ideas?

btw, I get a lot of "invalid arguments" during scanning as a dvb card with atsc/qam.

---

### Post by Zero7 on 2007-05-10
> **syntheticexctasy said:**
> I'm pretty new to linux myself, and am having a really tough time getting this card to work. I've scanned NTSC channels and can get them to work in tvtime and mythtv (without sound), but I can't get what I really want which is atsc/qam.

Any ideas?

btw, I get a lot of "invalid arguments" during scanning as a dvb card with atsc/qam.

Did you follow the [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) guide? DO NOT miss any line. 
I think you will not be able to use NTSC and Digital at same time as of now in Linux.. I am still not done with the setup till now :(

---

### Post by newlinux on 2007-05-10
> **Zero7 said:**
> Did you follow the [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) guide? DO NOT miss any line. 
I think you will not be able to use NTSC and Digital at same time as of now in Linux.. I am still not done with the setup till now :(

I posted a link earlier that will allow you to use the card as analog and digital at the same time, however it requires you to directly modify the mysql database. Make sure you go through those directions thorughly, including the unmuting the card commands. Take a look at your alsa mixer, you may just have the sound for this device way down or muted. If you want to use it as a digital device, you'll want to change your analog settings (to dvb driver, and using a different video source) to digital settings, and then try rescanning. Make sure you let the scan complete, sometimes all the stations are lumped in one location.

Also, if the scan doesn't find anything, try connecting the cable up to the other input on the Kworld card.

---

### Post by maxvall on 2007-09-27
Hi.
I try to setup my Kworld ATSC 115 TV card on my Ubuntu Festy pc by folowing the next howto:
[http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110)
but i have problems in steps 3 & 4.1
Step 3 saids textually: "Edit your /etc/modules file and insert an 'saa7134-dvb' right after the saa7134 entry that should already exist in the file. This will cause the module to load during boot.", but my /etc/modules file do not have a saa7134 entry.
My /etc/modules file:
----------------------------------------------------------------------------------------
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
----------------------------------------------------------------------------------------
What to do now????? Shall i add a saa7134?????

Now then, Step 4 says textually: "If you are using a kworld 115, you need to force proper recognition by adding the following lines to /etc/modprobe.conf" But i dont have a /etc/modprobe.conf file!!!!!  What to do???? HELP!!!!

---

### Post by newlinux on 2007-09-29
yes, add saa7134 and saa7134-dvb

I'm pretty sure you can just create the /etc/modprobe.conf file and add those lines. Alternatively you could create a file under /etc/modprobe.d/ and add the options there. There should already be examples there. This way helps you to organize your options better.

```

man modprobe.conf

```
for me details

---


---
title: "ATI Radeon HDMI output - not full screen, no sound"
date: 2012-12-14
forum: Multimedia Software
---

### Post by dplmartin on 2012-12-14
Hi,

My screen resolution is set to 1920 x 1080 @ 50Hz but when I view the HDMI output on my Panasonic Viera 50", I get a thick black border around the picture. So the desktop does not reach to the edges of the TV. I also don't appear to get any sound through the link and I can't see an option of an additional sound output in the sound settings.

Here are my system details:
Ubuntu 12.04.1 LTS 64bit
Graphics reported by system as VESA RV730
AllSettings > Displays says Panasonic Industry Company 32"
Graphics card ATI Radeon HD 4650
Running ATI/AMD proprietary FGLRX graphics driver
AMD Catalyst Control Centre 2.14 installed
There is a soundcard installed with both Analogue and Digital sound ouputs. I can get that to work


CCC seems to report the TV as being a projector. It does not give me access to any settings that would enable me to stretch the picture or enable underscan/overscan. There are no settings on the TV that would make the picture fit properly.

Also, like I said, I'm not sure how I'm supposed to command the system to output sound through the HDMI connection.

Does anyone else have this Card/OS combo and have got it working successfully. I can post xorg.conf file if required.

---

### Post by dannyboy79 on 2012-12-14
install pavucontrol and check one of the tabs for the HDMI audio. also, make sure it isn't muted within alsamixer, you can select the device with one of the F keys, just look in the upper right corner of alsamixer.

as far as overscan, I am not sure there. My TV has settings for aspect, 1:1, zoom x2, stretch, fill, etc. You're saying you don't have anything like that or they don't make a difference?

Try these suggestions: [http://www.linuxquestions.org/questions/linux-hardware-18/ati-radeon-57xx-using-hdmi-overscan-issue-centos-5-5-x86_64-a-861545/](http://www.linuxquestions.org/questions/linux-hardware-18/ati-radeon-57xx-using-hdmi-overscan-issue-centos-5-5-x86_64-a-861545/)

---

### Post by dplmartin on 2012-12-15
The TV does have zoom settings but it does too much. You start to lose parts of the picture. There are no options for stretching the picture.

I'll try what you said to get the audio working.

---

### Post by dplmartin on 2012-12-18
Bump. Nobody has any clue about how to sort out CCC so that I can get the image positioned correctly?

---

### Post by GuiGuy on 2013-01-28
> **dplmartin said:**
> Bump. Nobody has any clue about how to sort out CCC so that I can get the image positioned correctly?

Hi
I have a similar problem, but found that I can get a full image on the screen by changing the screen refresh rate in Catalyst. I changed from 50hz to 60hz and get a full screen.

However, as we've come to expect with Linux, solving one problem introduces at least one new one. Now when I exit from playing a video the screen freezes and I have to cold start the display :(

Ubuntu (linux) is driving me crazy... maybe it's time to look out of the Window again.

---

### Post by Sweetdaddydong on 2013-02-02
I am also having the same screen issue with my setup. The driver thinks the TV is a project and does not produce an overscan option. I have a Panasonic TCP-50U50

I am not having any issues with the sound though. I was originally but once I installed the fglx video driver I had no issues when set to HDMI. 

Fun fact, the CCC sees the TV just fine in Windows and gives me an overscan option, but I don't want to go back to Windows. Anyway this is proof that it is a software bug and not a hardware issue.

---

### Post by plansk on 2013-10-08
As far as not getting full screen, this worked for me:

sudo aticonfig --tv-overscan=on

In CCC, I think this is the same as putting Display Manager > DTV (1) > Adjustments > Scaling Options to 0% Overscan, assuming you can see that option.

---

### Post by dogfood454 on 2013-12-23
Found a fix for this: 
I have ATI HD7950 - connected with HDMI to - 42" Panasonic.
Found the answer here: [https://wiki.archlinux.org/index.php/AMD_Catalyst#Configuring_X](https://wiki.archlinux.org/index.php/AMD_Catalyst#Configuring_X)
**Not using fullscreen resolution at 1920x1080 (underscanning, black borders around the screen)**

 This usually happens when you use a HDMI connection to connect your monitor/TV to your computer. 
Using the amdcccle GUI you can select the display, go to  adjustments, and set Underscan to 0% 
(My TV shows up as Projector so no options only info. tab)

For newer version (for example, 12.11), if Catalyst control center repeatedly fails to save the overscan setting, edit /etc/ati/amdpcsdb like so: 
 /etc/ati/amdpcsdb 

TVEnableOverscan=V0     ( line 12 on my file changed from V1 to V0 that's it.) 

Then logout and login. 
After a reboot everything worked for me.

---


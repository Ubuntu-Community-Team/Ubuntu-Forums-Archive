---
title: "Microphone doesn't work in Asus 1215t netbook"
date: 2011-01-07
forum: Multimedia Software
---

### Post by joehill on 2011-01-07
Hello everyone,

I just installed Maverick on an Asus Seashell 1215T netbook with an AMD/ATI chipset. The sound output is working fine (with the exception that I have to manually set output to either speakers or headphones rather than just plugging in headphones), but neither the internal microphone nor external microphones plugged in through the mic jack work. I do have the sound device set to the internal sound (rather than HDMI) and the volume level set appropriately. Apparently neither microphone is being recognized. Any ideas on what could be wrong?

Here is the relevant section from lspci -v:


00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 841c
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fbbf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

I've submitted a bug ([here]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697383")) but have had no response so far. I've looked around and tried various things suggested by other threads but nothing has worked so far.

Thanks!

---

### Post by BicyclerBoy on 2011-01-08
Simple first:

gnome-menu system preferences sound: tab input

Unmute & crank up the gain/volume

Observe the vu meter, select different input devices & make some noise...

Do any of them work ?

install gnome-alsa-mixer
check inputs not muted, check the gain..

aplay -l
aplay -L

---

### Post by lidex on 2011-01-09
More info would be helpful. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6]("http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6")

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6]("http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6")

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6]("http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6")

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6]("http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6")

---

### Post by rocatorreon on 2011-01-20
> **lidex said:**
> More info would be helpful. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]


Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6]("http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6")

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6](http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6)

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6](http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6)

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6]("http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6")

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6](http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6)

---

### Post by rocatorreon on 2011-01-20
Hi, Im also having the same problem on the same netbook with ubuntu 10.10

This is the link that terminal came up with:
[http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6](http://www.alsa-project.org/db/?f=2d1d5f32a75a55f65fe4e9abfab3dea4d63cf3a6)

---

### Post by rocatorreon on 2011-01-20
Sorry about all the posts, I don't know how that happened.

---

### Post by lidex on 2011-01-20
@rocatorreon
Alsa doesn't seem to recognize your codec well. Try updating your alsa-driver-modules. Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

As for multiple posts, only click the submit button one time regardless of the progress on-screen.

---

### Post by rocatorreon on 2011-01-20
Ok, just did that and is still not working, I maxed up all the leves, and the indicator on the input tab on the sound preferences doesn't move.

---

### Post by lidex on 2011-01-21
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by spoiled-tv on 2011-02-07
I am having the same issue, I have followed all steps, capture and mic levels are almost maxed, the mic isnt muted anywhere I can find. Any additional help would be appreciated. 

[http://www.alsa-project.org/db/?f=ef099a63136f9c12dbce615dbbec1c6debfba400](http://www.alsa-project.org/db/?f=ef099a63136f9c12dbce615dbbec1c6debfba400)

---

### Post by lidex on 2011-02-09
> **spoiled-tv said:**
> I am having the same issue, I have followed all steps, capture and mic levels are almost maxed, the mic isnt muted anywhere I can find. Any additional help would be appreciated. 

[http://www.alsa-project.org/db/?f=ef099a63136f9c12dbce615dbbec1c6debfba400](http://www.alsa-project.org/db/?f=ef099a63136f9c12dbce615dbbec1c6debfba400)

Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by spoiled-tv on 2011-02-09
> **lidex said:**
> Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Done, still not working:

[http://www.alsa-project.org/db/?f=1b9ebe0b84e202a7a70eaea09767b2a0d3ac4ff5](http://www.alsa-project.org/db/?f=1b9ebe0b84e202a7a70eaea09767b2a0d3ac4ff5)

Thank you for working with me on this.

---

### Post by lidex on 2011-02-09
Have a look here:
[http://art.ubuntuforums.org/showthread.php?t=1607552](http://art.ubuntuforums.org/showthread.php?t=1607552)
This codec is newer and seems to have limited alsa support.

---

### Post by spoiled-tv on 2011-02-18
> **lidex said:**
> Have a look here:
[http://art.ubuntuforums.org/showthread.php?t=1607552](http://art.ubuntuforums.org/showthread.php?t=1607552)
This codec is newer and seems to have limited alsa support.


Installed HDA-VERB 0.3 and now my speakers don't work. My Mic still not working either.

[http://www.alsa-project.org/db/?f=9365c997bb510d311cb815752535902f8d91f73f](http://www.alsa-project.org/db/?f=9365c997bb510d311cb815752535902f8d91f73f)

---

### Post by spoiled-tv on 2011-02-26
When I am in sound preferences and I go to hardware>internal audio>test speakers and I click test nothing happens, however sound works for mp3s, youtube, etc...

---

### Post by lidex on 2011-03-01
You should report a bug.Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by walkkenn1 on 2011-03-02
I had the same problem earlier and fixed it.  Now we have had an update in software and the problem is back.   (I have an ASUS 1001pxd and have had problems with the microphones since I've had it.

I have followed all the steps that mention here, but, one thing I have noticed when I try to use:

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

I get this response:

E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic


What do I do about that?:confused:

Thanks for your help.

---

### Post by vkanth on 2011-03-06
> **walkkenn1 said:**
> I had the same problem earlier and fixed it.  Now we have had an update in software and the problem is back.   (I have an ASUS 1001pxd and have had problems with the microphones since I've had it.

I have followed all the steps that mention here, but, one thing I have noticed when I try to use:

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

I get this response:

E: Couldn't find package linux-alsa-driver-modules-2.6.32-29-generic


What do I do about that?:confused:

Thanks for your help.


Not sure if you've fixed the problem, but I had the exact same issue  since I last performed an automatic update. After much struggle I ran  the following command:

 [COLOR=RoyalBlue]sudo aptitude --purge reinstall  linux-sound-base alsa-base alsa-utils linux-image-`uname -r`  linux-ubuntu-modules-`uname -r` libasound2[/COLOR]

Found this in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)  where they talk about all customizations being removed. Please use the  above at your own risk. Worked for me, doesn't mean it will work for  you. Good luck.

---

### Post by windeguy on 2011-03-07
> **vkanth said:**
> Not sure if you've fixed the problem, but I had the exact same issue  since I last performed an automatic update. After much struggle I ran  the following command:

 [COLOR=RoyalBlue]sudo aptitude --purge reinstall  linux-sound-base alsa-base alsa-utils linux-image-`uname -r`  linux-ubuntu-modules-`uname -r` libasound2[/COLOR]

Found this in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)  where they talk about all customizations being removed. Please use the  above at your own risk. Worked for me, doesn't mean it will work for  you. Good luck.

I have an Acer9410Z laptop. with running 10.04.  After an update, my mic does not work at all.   I just tried your command line fix, but it did not change anything. Oh well.  I hate to have to re-install and then block further updates. Perhaps another interim update will fix the problem?

---

### Post by spoiled-tv on 2011-03-08
> **windeguy said:**
> I have an Acer9410Z laptop. with running 10.04.  After an update, my mic does not work at all.   I just tried your command line fix, but it did not change anything. Oh well.  I hate to have to re-install and then block further updates. Perhaps another interim update will fix the problem?

I just installed updates it worked, I installed skype and then I noticed I had my speakers muted so I unmuted them and mic no longer works. I havent been able to get it to work again.

[http://www.alsa-project.org/db/?f=4b5efd7151d0ca3484821c9f87ba3add2f5e2e49](http://www.alsa-project.org/db/?f=4b5efd7151d0ca3484821c9f87ba3add2f5e2e49)

After that I did:

> **vkanth said:**
> Not sure if you've fixed the problem, but I had  the exact same issue  since I last performed an automatic update. After  much struggle I ran  the following command:

 [COLOR=RoyalBlue]sudo aptitude --purge reinstall   linux-sound-base alsa-base alsa-utils linux-image-`uname -r`   linux-ubuntu-modules-`uname -r` libasound2[/COLOR]

Found this in [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)   where they talk about all customizations being removed. Please use the   above at your own risk. Worked for me, doesn't mean it will work for   you. Good luck.

still no change

[http://www.alsa-project.org/db/?f=63b52d1ebb07d04dea27fccc6a19be628adb65ac](http://www.alsa-project.org/db/?f=63b52d1ebb07d04dea27fccc6a19be628adb65ac)

---

### Post by spoiled-tv on 2011-03-08
> **spoiled-tv said:**
> I just installed updates it worked, I installed skype and then I noticed I had my speakers muted so I unmuted them and mic no longer works. I havent been able to get it to work again.

[http://www.alsa-project.org/db/?f=4b5efd7151d0ca3484821c9f87ba3add2f5e2e49](http://www.alsa-project.org/db/?f=4b5efd7151d0ca3484821c9f87ba3add2f5e2e49)

After that I did:



still no change

[http://www.alsa-project.org/db/?f=63b52d1ebb07d04dea27fccc6a19be628adb65ac](http://www.alsa-project.org/db/?f=63b52d1ebb07d04dea27fccc6a19be628adb65ac)


Walked away from computer and came back to it, it seems to work now (went into hibernate and I woke it)

[http://www.alsa-project.org/db/?f=80599a5e8cff4494b5a2ad15cc0a8f27d39745f2](http://www.alsa-project.org/db/?f=80599a5e8cff4494b5a2ad15cc0a8f27d39745f2)

---

### Post by windeguy on 2011-03-08
spoiled-tv,  I have noticed that sometimes after a reboot the audio system will behave differently.  I can only guess that the Realtek Audio chip family is difficult to program because of the almost random behavior I have seen lately.  I was running just fine for several months until some recent updates that have caused a step backwards.  Hopefully your mic will stay on.  Meanwhile I will look at some "work-around" fixes.

---

### Post by spoiled-tv on 2011-03-11
[http://www.alsa-project.org/db/?f=46b728aa9818f45f034283d61a49e1ded1898a60](http://www.alsa-project.org/db/?f=46b728aa9818f45f034283d61a49e1ded1898a60)

and again no worky :(

---

### Post by jairopa on 2011-03-14
> **spoiled-tv said:**
> [http://www.alsa-project.org/db/?f=46b728aa9818f45f034283d61a49e1ded1898a60](http://www.alsa-project.org/db/?f=46b728aa9818f45f034283d61a49e1ded1898a60)

and again no worky :(
I had the same problem anf lucky me it was a dummy issue (actually not an issue) 3 stepes left click on Souns Icon (see picture 1) and then -> Sound Preferences...[IMG]http://img9.imageshack.us/i/49801424.png/[/IMG]

Then Input Tab -> and "De"mute or "Un" Mute with marking out checkbox (I'm very sorry for my english)[IMG]http://img155.imageshack.us/i/22784664.png/[/IMG]
I left the output preferences just as they were [IMG]http://img840.imageshack.us/i/26152360.png/[/IMG] 
That's all folks (I probe it with Skype 2.1 for linux, ans it worked, before it did not work) 
I hope you can do it!

[http://img155.imageshack.us/i/22784664.png/](http://img155.imageshack.us/i/22784664.png/)
[http://img840.imageshack.us/i/26152360.png/](http://img840.imageshack.us/i/26152360.png/)

---

### Post by windeguy on 2011-03-15
> **jairopa said:**
> I had the same problem anf lucky me it was a dummy issue (actually not an issue) 3 stepes left click on Souns Icon (see picture 1) and then -> Sound Preferences...[IMG]http://img9.imageshack.us/i/49801424.png/[/IMG]

Then Input Tab -> and "De"mute or "Un" Mute with marking out checkbox (I'm very sorry for my english)[IMG]http://img155.imageshack.us/i/22784664.png/[/IMG]
I left the output preferences just as they were [IMG]http://img840.imageshack.us/i/26152360.png/[/IMG] 
That's all folks (I probe it with Skype 2.1 for linux, ans it worked, before it did not work) 
I hope you can do it!

[http://img155.imageshack.us/i/22784664.png/](http://img155.imageshack.us/i/22784664.png/)
[http://img840.imageshack.us/i/26152360.png/](http://img840.imageshack.us/i/26152360.png/)

The image you are showing is, I believe, part of the interface to Pulse Audio.  I had removed Pulse Audio from my system after reading about problems it was causing.  I had no problems at all with audio until there was a normal update and then I lost the function of my mic.  It looks like I may have to re-install pulse audio and see if that turns my mic on because of a bug in the current version of Ubuntu Studio.

---

### Post by mattasus on 2011-03-15
I have an ASUS x50z with a realtec ALC662 LSI sound card, my mic is unmuted, and changed the settings in alsamixer, alsamixer tells me I have HDA ATI SB soundcard. 
I tried sudo apt-get install linux-alsa-driver-modules-$(uname -r), the install worked. But still no sound from my mic. Speakers are fine!

I also did the command: unbuntu report bug

From another similar topic in this forum I tried replacing the file; snd-hda-codec-conexant.ko but it won't allow me because of a permission issue

Any ideas anyone? Thanks

---

### Post by windeguy on 2011-03-16
> **mattasus said:**
> I have an ASUS x50z with a realtec ALC662 LSI sound card, my mic is unmuted, and changed the settings in alsamixer, alsamixer tells me I have HDA ATI SB soundcard. 
I tried sudo apt-get install linux-alsa-driver-modules-$(uname -r), the install worked. But still no sound from my mic. Speakers are fine!

I also did the command: unbuntu report bug

From another similar topic in this forum I tried replacing the file; snd-hda-codec-conexant.ko but it won't allow me because of a permission issue

Any ideas anyone? Thanks

For me, this is the most challenging problem I have run across in Linux. I have yet to find a solution.

---

### Post by sara jon on 2011-03-16
thanx you man

---

### Post by lidex on 2011-03-18
> **mattasus said:**
> I have an ASUS x50z with a realtec ALC662 LSI sound card, my mic is unmuted, and changed the settings in alsamixer, alsamixer tells me I have HDA ATI SB soundcard. 
I tried sudo apt-get install linux-alsa-driver-modules-$(uname -r), the install worked. But still no sound from my mic. Speakers are fine!

I also did the command: unbuntu report bug

From another similar topic in this forum I tried replacing the file; snd-hda-codec-conexant.ko but it won't allow me because of a permission issue

Any ideas anyone? Thanks
I'm going to answer to this but please, in the future open a new thread when you have an issue.
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**
This applies to your hardware, not the 1215t.

---

### Post by unboogyman on 2011-03-27
Has a solution been found?  I have the same netbook and neither the microphone works nor any headphones (which is worse)

---

### Post by h.lyakhovich on 2011-04-01
Hello everyone.
I have the same issue with microphone on 1215T, it's not working. I have two devices in Sound Preferences/Hardware tab: Internal Audio and RS880 Audio Device [Radeon HD 4200]. As far as I've understood we're dealing with Internal Audio. Analog Stereo Duplex mode turned on, speakers are working properly. In Input tab volume is 100%, not muted, sound input device is Internal Audio Analog Stereo (which is the only one there). I've tried all the things written here including alsamixer (everything's not muted and up to the max), gnome-alsamixer (the same). I also used pavucontrol in many ways. Everything's fine there.

I've almost gave up but found something that looks like possible solution. After updating Alsa modules and reboot, gnome-alsamixer showed the particular installed sound card models. They are Realtek ALC269VB and ATI RS690/780 HDMI. So we're looking at Realtek. Googling this issue using Realtek's model I found [_this bugreport_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732445") on Launchpad and it's status is "Fix commited". Someone there wrote "This has now been committed as 584c0c4c359bdac37d94157f8d7fc513d26c8328 to sound-2.6". Googling it I found [_this page_]("http://www.mail-archive.com/stable@linux.kernel.org/msg06336.html") showing that the issue is solved in 2.6.37 (I just understood it like this). The problem is my Ubuntu 10.10 has kernel no. 2.6.35-28-generic and I have no idea how to update it. Maybe it's possible somehow to install this particular patch to my system?

I would be glad if anyone solved if this is a solution and if it is, explained in details how to install the patch. I'm an absolute Linux beginner, thx in advance for your help.

---

### Post by lidex on 2011-04-01
@h.lyakhovich
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by unboogyman on 2011-04-02
> **lidex said:**
> @h.lyakhovich
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Still doesn't recognize the internal microphone.

---

### Post by h.lyakhovich on 2011-04-02
@lidex
I was writing such a long message and forgot the main thing: I've already tried everything from this thread. The update you've supposed is also on page number 2. Anyway, I've tried it again. The result is no recognizing, as @unboogyman has written. Sigh.

---

### Post by h.lyakhovich on 2011-04-02
bump

What about that alsa patch?

---

### Post by lidex on 2011-04-02
> **h.lyakhovich said:**
> bump

What about that alsa patch?

Can't help you with the patch as I've no experience. See about a later kernel here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by winecurmudgeon on 2011-04-07
Have had the same exact same problems, running Xubuntu 10.10. Tried all the suggestions here, and the best I could do with the internal mic with the 1215T was a lot of static. My solution? A Samson Go Mic, which worked out of the box with Skype (and everything else). Skype even let me choose it as the mic.

---

### Post by spoiled-tv on 2011-04-23
If I shut my laptop then open it my mic will work.

---

### Post by machinemovement on 2011-04-23
I'm having the same trouble with the mic as OP - same model netbook running 10.10.

Any suggestions would be *greatly* appreciated; thanks guys!

---

### Post by unboogyman on 2011-05-04
> **h.lyakhovich said:**
> bump

What about that alsa patch?

Okay, so now that 11.04 is out and the updated kernel with the patch is what it uses, the mic should be working...

Here is the weird thing.  From a 11.04 live cd, the internal mic works fine OFTB, but when I install 11.04 to my HDD, it no longer works.

Does anyone have an idea why this may be???

---

### Post by r_mano on 2011-11-30
Could be this the same problem as [http://ubuntuforums.org/showthread.php?p=11500623#post11500623?](http://ubuntuforums.org/showthread.php?p=11500623#post11500623?) 

If yes, I have added a bug here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/898081](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/898081)

---

### Post by r_mano on 2011-11-30
In my 1005P, I tried [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) and it worked for me.

---


---
title: "Upgrade to ALSA 1.0.19?"
date: 2009-01-28
forum: Mythbuntu
---

### Post by scudderwagg on 2009-01-28
Hey folks, new guy here with a question for those with much more knowledge and experience than myself.  Just setup my first MythTV system last month using Mythbuntu 8.10 and have worked out nearly all the kinks except I cannot get digital sound out of the optical SPDIF.  No light or anything coming from the port.  Here are my system specs:

Motherboard: Asus M3A78
CPU: AMD Athlon 64 X2 5050e (2.6 GHz, 45W)
RAM: 1GB
Video Card: ASUS GeForce 6200LE 512MB
Sound Card: Integraded Sound VIA VT1708B Chipset
HD: Segate 750 GB and 320 GB drives
Tuners: HD Homerun
Country: US
TV provider: Comcast Digital Cable
TV signal type: QAM (and hopefully firewire in the future)
TV: Panasonic Viera TH-42PZ77U, 42" 1080p Plasma
Mythbuntu 8.10 AMD64 Version

Currently I can get analog sound from the line out but would much prefer true AC3 and DTS audio output to my Onkyo receiver.  Based on the information here ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/306131)) there appears to be a bug with Mythbuntu 8.10 for 64bit with this sound chipset.  Some have reported that upgrading to ALSA 1.0.19 has eliminated the problem.  According to this information ([http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)) I have to update using a special script, not with Synaptic.  Basically my question is, will upgrading to ALSA 1.0.19 break anything or prevent me from upgrading in the future.  I definitely want to upgrade to later versions of Mythbuntu once VDPAU and MythTV 0.22 are available so I don't want to cause these future upgrades to be a royal PITA.

Also, while I do not have the code to post right now, just to clarify I get no SPDIF or iec958 cards listed from the output of aplay -L or aplay - l.  Thanks for helping a noob.

---

### Post by itlarson on 2009-01-28
somewhere in mythtv settings there is an ac3 to spdif passthrough checkbox which must be selected.  This will then send the digital signal to the spdif out AND the line out.  Slightly anoying since the remote speakers/ second source on onkyos requires analog input, but at least you have digital surround in the main listening/viewing area.  Hope this helps.

---

### Post by scudderwagg on 2009-01-28
I have tried all the internal MythTV settings, including checking the boxes for AC3 and DTS pass through and all the different ALSA output options.  That's not the problem.  The problem is that ALSA isn't even recognizing that a digital output exists.  MythTV can't output to the SPDIF if ALSA doesn't know it exists.

---

### Post by itlarson on 2009-01-28
Sorry- Thought it sounded like that was it.  Other than looking at settings in alsamixer, (which you probably have done) that's all I've got.

---

### Post by rodercot on 2009-01-28
Well is sound like to me, your upgrade did not take on the first go round.  Which Model board do you have there are a few M3A78 models.

 If you are using the script found within the ubuntu forums then I have had to run that a couple times myself as well. 
 
 I have an M3N78-VM board in one of my mahcines and I am sure it is the same chipset. 

 Your alsamixer once upgraded should be rev 1.0.19 as well if it not then your upgrade did not work. 

 Once that is done I think you will likely need to find that you need to add the option 

 options snd-hda-intel model=6stack-dig, This is just an example and I am not sure if it will work for your board, this does work on an Asus P5N7A-VM.  you can find which setting you need to set in yours by searching the alsa-site and in a file in your 1.0.19 alsa directory you downloaded via the script. I am sorry I just cannot remeber which file.

 This option should be appended to the end of your 

 sudo vim /etc/modprobe.d/alsa-base and this should activate your spdif output for you.

 in myth you are setting up the general tabs to 

 ALSA:spdif and then select iec958 in the next box and then check the dd and dts checkboxes. 

 Dave

---

### Post by scudderwagg on 2009-01-28
Dave,
Thanks for the info.  To clarify, I have not actually upgraded yet.  Part of my question is to determine whether upgrading the ALSA will cause any problems down the road if I want to upgrade to Mythbuntu 9.04 or, more precisely, whatever Mythbuntu version appears in the future with MythTV 0.22 and VDPAU.  Basically what I want to know is if I should just wait for 9.04 or a later version that will include updated ALSA.  Being a noob here, I'm just afraid of screwing something up such that it will make for bigger headaches down the line.  Thanks.

---

### Post by rodercot on 2009-01-28
> **scudderwagg said:**
> Dave,
Thanks for the info.  To clarify, I have not actually upgraded yet.  Part of my question is to determine whether upgrading the ALSA will cause any problems down the road if I want to upgrade to Mythbuntu 9.04 or, more precisely, whatever Mythbuntu version appears in the future with MythTV 0.22 and VDPAU.  Basically what I want to know is if I should just wait for 9.04 or a later version that will include updated ALSA.  Being a noob here, I'm just afraid of screwing something up such that it will make for bigger headaches down the line.  Thanks.

 Well I cannot for sure answer that BUT you can always roll back or upgrade again later if need be. I keep a windows local copy of all the scripts and zip up the alsa required files for 2 revs back every time I upgrade them. 

 NVIDIA is easy I never use the glx or the included myth drivers I always install the latest from the NVIDIA site current is 180.22 I believe. Those I also store locally for roll back if needed and if it does not waork it is quite easy to remove this way. you need to be in run level one to install NVIDIA drivers this way I hit escape at the grub boot menu then select drop to shell then login and type
 
 cd /path/to/the/dir/you dwnlded the nvidia driver to/

 sudo sh NVIDIA-Linux-x86-180.22-pkg1.run (to install) or

  sudo sh NVIDIA-Linux-x86-180.22-pkg1.run --uninstall (to remove) of course the 180.22 can be any version you dwnld ie 180.11, 180.16, 177.80, 177.82 etc..

 Dave

---

### Post by Dewey_Oxberger on 2009-01-29
I've found if I manually update something (i.e. didn't use apt-get or synaptic to update it) a kernal update will require the manual update be done again.

The easy way to update the alsa stuff is the script found in these forums. 

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

And 1.0.19 is nice :)

The easy way to update the video driver is to follow the wiki subject NVidiaManual.

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

As for the Spdif - did you enable it in bios?

If so, do a

aplay -l

and 

aplay -L

and post the results back here.

---

### Post by scudderwagg on 2009-01-29
Hey guys,
Thanks for all the info.  Had to teach last night so I didn't have time to try to install the new ALSA drivers yet.  I have checked the BIOS settings and there is no specific toggle for the SPDIF but I did mess with all the sound settings there before, to no avail.  I'll post my aplay -l and aplay -L before and after driver upgrades, hopefully tonight.

Are the new NVIDIA drivers that much better overall?  Would I see an improvement by upgrading to 180.22?  I couldn't use VDPAU since my video card isn't up to snuff for that.  I would like to try VDPAU in the future (once I get a new card) but am hesitant to do so now as I've read there are problems displaying HDHomerun recordings.

---


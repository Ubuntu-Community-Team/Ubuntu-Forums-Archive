---
title: "P5N7A-VM MYTH/XBMC Hdmi Audio Working"
date: 2009-01-27
forum: Mythbuntu
---

### Post by rodercot on 2009-01-27
Hey All,

 Thought I would post this tidbit for anyone with issues or incase you have issues. 
 
 I run a Asus P5N7A-VM with Mythbuntu 8.10 and XBMC via ppa.

 I setup my system yesterday and spent a while on hdmi audio, I now have hdmi and spdif both working for myth and xbmc.

 I basically updated to the latest Alsa 1.0.19 complete via the script found here

 [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

 run with -d and then with -i then reboot and run alsamixer first make sure the mixer version is now 1.0.19 or you will have to run the above script again once correct unmute all your iec958 channels.

 Then I edited

 sudo vim /etc/modprobe.d/alsa-base

 (if you are not use to vim (open file with above command and press i to insert (edit mode) then edit away - then hit esc to get out of insert mode.
 now to save the file type ":wq" (without the quotes) enter. if you make a mistake the to get out of the file without changing type ":q" or ":q!" (without the quotes))

 scroll to the end of the above file and paste this in

 options snd-hda-intel model=6stack-dig

 save the file. This enables the spdif output as well as hdmi.

 now in mytbuntu setup under general I changed 

 Sorry cannot remeber the box name but the first one at the top
 from ALSA:default to ALSA:hdmi 
 
 And change the next box below that from 

 default or iec958 to hdmi
  
 spdif output dts and dd are selected.  leave the rest as is

 in xbmc go to audio properties in setting - system - audio and if you are hooked to a rcvr then

 digital
 dts on
 dd on
 hdmi
 hdmi

if using tv then

 digital
 dts off
 dd off
 hdmi
 hdmi

 Hope this can help you out if you are having issues. I played around for a couple hours playing with this. 

 I do not use an asound or asoundrc config file for myth or xbmc and everything passes to my rcvr with xbmc less (multi-channel LPCM cureently I am still playing with this though.)

 *UPDATE* I set up my slave machine finally with the same board and just using my V7 Konka 32" LCD (JUNK by the way) no rcvr. Anyhow same setup as above only I turned off output of dts and dd as it is passed to the TV via the hdmi connector and all plays fine. Now I just have to fiddle my xorg.conf file for that TV as there are NO settings in the TV for overscan options anywhere, I wish I have bought another Sharp instead. 

 Have Fun!

 Dave

---

### Post by jowilkin on 2009-02-07
Thanks for the info.  It took me several hours of struggling to finally get audio over HDMI working on the same board (working for most things).

In addition to your steps I had to make a file name ~/.asoundrc with the contents "pcm.!default hdmi".

This is on standard Ubuntu.

---

### Post by thibaudeaua on 2009-02-10
I have the same board, but I don't see all three devices.  Just the analog and the spdif digital, but no HDMI using aplay -l.  Any suggestions.  Using 7.10 with NVIDIA driver 180.22 and alsa 1.19.

---

### Post by rodercot on 2009-02-11
> **thibaudeaua said:**
> I have the same board, but I don't see all three devices.  Just the analog and the spdif digital, but no HDMI using aplay -l.  Any suggestions.  Using 7.10 with NVIDIA driver 180.22 and alsa 1.19.


 when you run alsamixer what rev does it say it is? Did you add options snd-hda-intel model=6stack-dig to /etc/modprobe.d/alsa-base?

 If your rev is not 1.0.19 on alsamixer you will need to rerun the alsa install script and also you need to check your uname -r, if you are running kernel 2.6.24-(1 to 24 and/or generic) or around there you will need to run the install script for alsa with -d first then -snap and finally -i for install. 1.0.19 will not compile on the 2.6.24 kernel properly.

 If you already installed with the script with the -d the you already have the Alsa 1.0.19 files in your /usr/src directory so you only need to run the script with -snap first and then -i to install. 

 If none of this works I would assume that you need to be running at least 8.04 and most likley 8.10 or upgrade your kernel 2.6.27-11 which is the upgrade from 2.6.27-7 in 8.10 is beaking certain things like Suspend/Resume check the latest bug reports.

 Dave

---

### Post by thibaudeaua on 2009-02-12
I upgraded the kernel and it seemed to go smoothly.  Rebooted successfully, but I don't see my network cards and sound card which was working out of the box prior.  I don't see the rt61.ko module any more.  Any thoughts?

thanks.

---

### Post by rodercot on 2009-02-12
> **thibaudeaua said:**
> I upgraded the kernel and it seemed to go smoothly.  Rebooted successfully, but I don't see my network cards and sound card which was working out of the box prior.  I don't see the rt61.ko module any more.  Any thoughts?

thanks.


 did you include your existing .config file in the new kernel build you would have also had to include the hda-snd-intel (complete section) from the kernel configuration screen I think from the snd, pci, sections.

 If you did not you could reconfigure the kernel using dpkg I believe and if you used your exsiting configuration for building you should be good. I would have backed up required files and just installed Mythbuntu 8.10 then use synaptic to upgrade to the latest kernel.

 Dave

---

### Post by jowilkin on 2009-02-15
My sound was actually still not fully functional, the advice in this thread: [http://xbmc.org/forum/showthread.php?t=42183](http://xbmc.org/forum/showthread.php?t=42183)

Helped me get it in much better working order.  Basically the thread has you upgrade to the newest nvidia driver (180.xx), the newest alsa, and make a ~/.asoundrc file that contains ```
pcm.dmixer {
   type dmix
   ipc_key 1024
   ipc_key_add_uid false
   ipc_perm 0660
   slave {
      pcm "hw:0,3"
      rate 48000
      channels 2
      format S32_LE
      period_time 0
      period_size 1024
      buffer_time 0
      buffer_size 4096
   }
}

pcm.!default {
   type plug
   slave.pcm "dmixer"
}
```

---

### Post by deey001 on 2009-03-26
> general I changed 

 Sorry cannot remeber the box name but the first one at the top
 from ALSA:default to ALSA:hdmi 
 
 And change the next box below that from 

 default or iec958 to hdmi
  
 spdif output dts and dd are selected.  leave the rest as is
Where are these setting?

---

### Post by deey001 on 2009-03-27
I have followed all the steps and cannot get the audio to work.

I have a few questions.

1. If you go to the sound options and run a test does the audio work?

2. Does the audio work in every application?

My setup goes as follows:

Ubuntu 8.04 Hardy
NVidia Driver is installed.
Alsa has been upgrade to 19
Bios Rev:0504

.asoundrc has been created in the /home/'profile'/ directory.

Any help would be greatly appreciated.

Thanks

Danny

---

### Post by jingo_man on 2009-12-12
hello to all

i ran the AlsaUpgrade script today, in order to get the HDMI audio working on my Ubuntu PC (same P5N7A-VM board as the OP)

there was a lot of other apps that required updating or installing as pre-reqs (full details in the install.log file attached) but it seemed to go through without a hitch.

rebooted the system, and tried the various "aplay" and "speaker-test" commands to see what happened. "aplay -l" reports the 3 expected devices, analog/digital/hdmi. basically, the analog source still works as expected, however i get nothing from the HDMI (i have both HDMI cable plugged in, so can see my desktop on HDTV, and the stereo cable plugged into the green audio jack, for Front speakers). i did notice that when i run the "aplay -Dplughw:0,0 -fcd" it plays white noise through the speakers and not a definitive sound - wasnt sure if there was an issue here, or if this was expected. when select hdmi as the source, the command line app cycles through the 6-channels ok (as in no errors in the terminal) but no sound is made.

am guessing you will have all the required info in the output from the alsa-info.sh file (AlsaUpgradeRev-1.0.21-4-121209-13.14.log) but for extra info, i have no /etc/asound.conf or ~/.asoundrc files. tried creating the second - no joy. edited the /modprobe.d/alsa-base.conf with the "options snd-hda-intel model=6stack-dig" and rebooted - no joy. all other things seem to be as expected, and am happy to run any tests people suggest to help resolve the issue (though specific commands to run would be appreciated!)

analog seems to work as it did previously, and current config for mythtv seems unaffected, so atleast its still operable,  but would appreciate any help others can provide.

regards

jingo_man

---

### Post by jingo_man on 2009-12-13
ok, i found the fix for the no sound - it seems that the hdmi channel was muted... apologies - i feel so silly...

however, in alsamixer, this device was listed as "S/PDIF 1", which i wasnt expecting. it had value of "MM". with the item highlighted, pressing the m key toggles mute on/off, and is replaced with 00. testing sound then worked. but i thought S/PDIF was the multi-stereo connection terminals on the back of the motherboard, and that HDMI was a totally different type of digital connection...?

anyways - its up and running, though occassionally i get a frequently repeating crackle noise that sounds like interference from the motherboard. has this been noticed by others? is there a fix? is it inherent? does it point to a fault on the board?

also, i am unable to control the volume with the remote within mythtv now, as its not being controlled by the system's volume... any clues for a fix here?

regards

jingo_man

---


---
title: "Sound Problems 10.04"
date: 2010-04-30
forum: Multimedia Software
---

### Post by eigenadam on 2010-04-30
I just upgraded to Lucid from Koala on my Dell Inspiron 13. It looks great and everything seems to be running so far, but I'm having some sound issues.

At first no sound worked. I tried reinstalling pulseaudio and this did nothing. I reconfigured ALSA (alsaconf) and now I can hear sounds played in Ubuntu (system sounds, MP3s etc.) However, sounds do not work when played in Firefox (i.e. YouTube). Also, my microphone does not appear to work.

---

### Post by ajgreeny on 2010-04-30
Try ```
alsamixer
``` in terminal. Use the cursor keys to move sideways and to raise and lower levels, "M" to mute/unmute, tab to move from Playback to Capture to All, and Esc to save and quit.

Make sure nothing is muted or set too low, which seems often to be the way it is setup by default.

---

### Post by dino99 on 2010-04-30
install gnome-alsamixer and paprefs
tweak gnome-alsamixer (apps sound)

---

### Post by eigenadam on 2010-04-30
I've already tried checking the levels in alsa-mixer, pulseaudiomixer and gnome-volume-control. All the levels are fine. No channels are muted. I know sound works because I can play music files locally.

---

### Post by eigenadam on 2010-04-30
I fixed the Firefox issues. It was a flash issue. I purged all flash and installed adobe-flashplugin.

---

### Post by Bill Randell on 2010-04-30
I have installed Karmic on MSI ms.1314 after original motherboard was replaced under warranty. I have read all the forums ect,:( tried many so called fixes but no, sound recorder will record a few words then lock up. So shut down again to get rid of sound recorder. So today after weeks of looking at the problem, I have done a new install of Lucid, looks and goes great, audio out is good, but still no sound recorder.
Also when I try to open sound preferences as soon as the mouse hits it, it dissapears.
So please? is there a fix as I want it work on Skpe when travelling.
Bill.

---

### Post by marcin_ose on 2010-05-07
Same problem here. Sound playback works, but I have not gotten any sound capture to work. I'd also like to be able to use Skype.

---

### Post by geodanny on 2010-05-08
I had the same problem (my computer had sound but FF did not). To resolve, I had to remove and reinstall adobe flash. Then I played with the pull down under hardware in the sounds menu. The incorrect profile was set. 

BTW: for whatever reason, Lucid also failed to include gnome-volume-control-applet in the top menu bar. I had to add it to applications that start with the computer.

update: it seems this problem reappears with every restart. Sound works on the computer except FF. Removing and reinstalling adobe flash corrects this and FF has sound again. Odd.

---

### Post by Blue2BlackOps on 2010-05-08
[FONT="Georgia"]64 bit Lucid:

Something I found out with my new Vaio with i3 processor. When I uninstalled both alsa and pulse, I still got the same low volume. Exactly the same. That seems a tad bizarre. Only time volume changes (even lower) is when I drop down master and pcm after I reinstall alsa.

Also the 100% (read many others) usage on two cpu's was taken care of when I killed the pulse process. I only tried that because I will be fresh installing again. Crazy stuff.[/FONT]

---

### Post by Blue2BlackOps on 2010-05-09
Lucid 64 bit:

The following link worked for my **Sony Vaio laptop**. Having proper audio again is fantastic! I chose the **easy** solution. Go slow, be sure.

[http://ubuntu42.blogspot.com/2010/05/fixing-sound-issue-on-sony-vaio.html](http://ubuntu42.blogspot.com/2010/05/fixing-sound-issue-on-sony-vaio.html)

---

### Post by tubunu on 2010-05-09
After enabling everything in alsamixer, check your Input and Hardware settings in System/Preferences/Sound Preferences.

---

### Post by Bobhuber on 2010-05-10
> **eigenadam said:**
> I just upgraded to Lucid from Koala on my Dell Inspiron 13. It looks great and everything seems to be running so far, but I'm having some sound issues.

At first no sound worked. I tried reinstalling pulseaudio and this did nothing. I reconfigured ALSA (alsaconf) and now I can hear sounds played in Ubuntu (system sounds, MP3s etc.) However, sounds do not work when played in Firefox (i.e. YouTube). Also, my microphone does not appear to work.
Ok here you go.After hours of research there is a known bug in Lucid.When this happens you can got to sound preferences on the top panel - applications and you will find the volume control down to 0 for the plugin app.If you slide it up you will hear the sound.
Rather than having to do that every time you open a page with sound here is the fix (or workaround). From a normal  terminal prompt (do not use gksu or sudo) type the following.
gconftool --type int --set /apps/totem/volume 100

---

### Post by roh8880 on 2010-05-29
Ok, i've followed all of the walk-thus, fixes and the stuff on [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I can only get sound if my sound preferences window is open, after I close it, the sound goes away.

What am I doing wrong?

when I type 
> wget -O alsa-info.sh [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh
it put my alsa info on [http://www.alsa-project.org/db/?f=52cdca1422d53bcf3b40aeea06bb7f522f514802](http://www.alsa-project.org/db/?f=52cdca1422d53bcf3b40aeea06bb7f522f514802)

---

### Post by lidex on 2010-05-30
> **roh8880 said:**
> Ok, i've followed all of the walk-thus, fixes and the stuff on [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
I can only get sound if my sound preferences window is open, after I close it, the sound goes away.
What am I doing wrong?
when I type 
it put my alsa info on [http://www.alsa-project.org/db/?f=52cdca1422d53bcf3b40aeea06bb7f522f514802](http://www.alsa-project.org/db/?f=52cdca1422d53bcf3b40aeea06bb7f522f514802)

Your alsa install is borked. Try this. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

Anything? Next upgrade your alsa using the alsa-upgrade link in my sig.

---

### Post by roh8880 on 2010-07-05
> ghost@ghost:~$ rm -r ~/.pulse ~/.asound* 
rm: cannot remove `/home/ghost/.asound*': No such file or directory
ghost@ghost:~$ sudo rm /etc/asound.conf
[sudo] password for ghost: 
rm: cannot remove `/etc/asound.conf': No such file or directory

Here is what I get . . .

---

### Post by lidex on 2010-07-05
That's fine, some config files only exist if you created them. Did you logout or reboot to see if that helped? Next step is the alsa upgrade.

---

### Post by spit-the-dog on 2010-07-15
I'm with geodanny on this, mp3's on local HDD would play but no sound on iplayer youtube spotify etc. Also lost the gnome desktop login and logout tones.
In "sound preferences" the hardware profile had shifted and I swear that was down to a batch of updates to 10.04 in the last few weeks. I tried a few settings and everything I've tested so far works with "Analog Surround 5.1 output + Analog stereo input". It had shifted to 1 of the digital input profiles. I've re-booted tonight and iplayer sound is fine.
For the people that know about this stuff:
I have integrated Intel ich7 5.1 sound on a Gigabyte mother board:
# Ubuntu-9:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
Ubuntu-9:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Hope this helps somebody
Cheers
Spit the dog (Lucid 10.4 LTS)

---

### Post by zerohunt on 2010-07-15
I get very por sound in ubuntu 10.04. Only my microphone works ,, laptops built in speaker are not working.Can anyone help plz

---

### Post by lidex on 2010-07-16
> **zerohunt said:**
> I get very por sound in ubuntu 10.04. Only my microphone works ,, laptops built in speaker are not working.Can anyone help plz
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by eigenadam on 2010-08-02
As per my origonal problem, built in Mic not working on Dell Inspiron 13 under Ubuntu 10.04, I have resolved the issue. I ended up doing a clean install for various reasons, but still the Mic didn't work.

I added the following to /etc/modprobe.d/alsa-base.conf 

options snd-hda-intel model=dell-bios power_save=10 power_save_controller=N

After a reboot and switching the input to Microphone1 in pavucontrol, everything worked fine.

---

### Post by malangaman on 2010-09-18
I have spent 36 hours of fumbling around Google following similar threads with no joy.
Finally today it is fixed!
I think the last update had an ALSA fix and that's why I am up and running with Sound Capture of all types. Audacity works like a charm. Thanks everyone who helped correct the problem.

---

### Post by lkjoel on 2010-09-25
> **eigenadam said:**
> I just upgraded to Lucid from Koala on my Dell Inspiron 13. It looks great and everything seems to be running so far, but I'm having some sound issues.

At first no sound worked. I tried reinstalling pulseaudio and this did nothing. I reconfigured ALSA (alsaconf) and now I can hear sounds played in Ubuntu (system sounds, MP3s etc.) However, sounds do not work when played in Firefox (i.e. YouTube). Also, my microphone does not appear to work.
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---


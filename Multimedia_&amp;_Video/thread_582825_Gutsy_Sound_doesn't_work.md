---
title: "Gutsy Sound doesn't work"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by davbren on 2007-10-20
Hey, I just did a clean install of Gutsy, overall I'm thrilled with it the only thing that doens't work is the sound, I get nothing at all. I'm using a Soundblaster Audigy 2 ZS. The sound worked fine in Feisty so why no does it choose not to work??

This is lspci:

00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1e.0 ISA bridge: ALi Corporation Unknown device 1575
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8)
00:1f.1 IDE interface: ALi Corporation ULi M5288 SATA (rev 10)
01:10.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
01:11.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:11.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:11.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
01:12.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:12.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:13.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:14.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
03:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
04:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
04:00.1 Display controller: ATI Technologies Inc R520 [Radeon X1800] (Secondary)

---

### Post by cwrann on 2007-10-21
Having the same problem with Creative sound blaster audigy SE. Worked in Gutsy not in Fiesty. I get the same results from the upgrade as I do with the clean install.

```
 lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
01:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 03)
07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)

```

---

### Post by NilsE on 2007-10-21
Try this

In a terminal run: asoundconf list

This should return a list of cards.

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then again with sudo: sudo asoundconf set-default-card xxxxx
 
This will set the defaults for the card and create a config file. 

Replace   xxxxx  with the name you found in list.

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can to show up in the panel. Make sure none are muted.

---

### Post by holodad on 2007-10-21
I had the same problem and solved it with this:

*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

Cheers

---

### Post by cwrann on 2007-10-21
> **NilsE said:**
> Try this

In a terminal run: asoundconf list

This should return a list of cards.

Replace   xxxxx  below with the name you found in list. I believe it is case sensitive.

In a terminal run: asoundconf set-default-card xxxxxx

Then again with sudo: sudo asoundconf set-default-card xxxxx
 
This will set the defaults for the card and create a config file. 

Replace   xxxxx  with the name you found in list.

In sound preferences "ALSA - Advanced Linux Sound Architecture" should be the choice

In the volume control turn on as many options as you can to show up in the panel. Make sure none are muted.

When I run asoundconf list I get:
```

Names of available sound cards:
NVidia
CA0106

```

CA0106 is the sound blaster audigy sound card so I replaced you xxxxx with that. I then followed all of the steps but I still have no sound.

**holodad:**

I tried following your advice but when I got to 
```
sudo m-a prepare
```

I am told to reinsert my gutsy installation CD. When I do this I am told that it is not the right CD and to try again.

---

### Post by NilsE on 2007-10-21
> sudo m-a prepare

I am told to reinsert my gutsy installation CD. When I do this I am told that it is not the right CD and to try again.

Go into System/Administration/Software Sources and uncheck the CD then redo the build. This will skip the CD and go to the repos which is where you want to be.

---

### Post by davbren on 2007-10-21
Cheers for the help, but I haven't got anywhere, I'm still not getting sound, its odd coz it worked under Feisty...

---

### Post by cwrann on 2007-10-21
> **davbren said:**
> Cheers for the help, but I haven't got anywhere, I'm still not getting sound, its odd coz it worked under Feisty...

same goes for me. when I enter preferences/sound and try the test buttons I get:

```
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
```

---

### Post by davbren on 2007-10-21
Yh I got that too for some of the sound options, I changed all mine to multichannel coz on test I was getting a tone. I dunno whther thats a good thing or not...

---

### Post by cwrann on 2007-10-21
I got the sound to work by going into volume control/ edit/ preferences and clicking all of the options on. I then jacked all of the volumes on them up. still nothing happened until I unchecked IEC958 under switches. After I did that I got sound. I played with the volume controls to find the ones that are actually doing things. The analog sound controls were the ones controlling things. My new question is how do I know that my sound card is being used to the fullest potential, should it be analog or something else and what does IEC958 do?

---

### Post by davbren on 2007-10-21
Yh I tried that and sound still doesn't work...I really don't want to downgrade coz the rest of the OS is amazing.

---

### Post by J-Morris on 2007-10-21
> **holodad said:**
> I had the same problem and solved it with this:

*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

Cheers

Props! This worked for me, I just had to use alsamixer to increase the PCM volume and the sound is back for everything so far.

---

### Post by tashmooclam on 2007-10-23
Gusty totally did not work at all on my older Compaq laptop, the screen was 4" tall  the icons looked like a Jackson Pollock job. That will stay as 7.04 
This one is an HP pavilion zt1000. 7.1 Gusty runs OK but my sound is very faint. 
How I miss the awesome sound I got from my old iMac Graphite!

---

### Post by davbren on 2007-10-23
if its anything like mine its the pcm front and centre channels that need to be raised to 100%. I'm a real n00b when it comes to this stuff, I can't believe i was that dumb!

---

### Post by free10 on 2007-10-24
> **holodad said:**
> I had the same problem and solved it with this:

*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

Cheers

This worked for me to get sound back for the flash videos in my Firefox browser after upgrading it to Gutsy. After the upgrade sound notification in Thunderbird was not working or for flash videos in Firefox (didn't check other sound type files in browser then) or mouse overs or for some small wav files which now sound scratchy and distorted. Movies or videos and larger sound files worked though in Movie Player.I am using a SB 512 card. Well at least I have my sound back in Firefox now so thanks--Dwight

PS Gutsy is way slow on booting but once booted it seems faster and looks a little nicer.

---

### Post by relgar on 2007-10-28
I lost digital out on my Audigy 2 ZS overnight for some reason (regular output to 2.1 speakers were still working).  I upgraded to Gutsy from Feisty a few days ago, but I'd stop fiddling with it since then.  The module-assistant instructions posted earlier didn't work, nor did downgrading the various alsa libraries.

Ended up purging alsa with "m-a purge" and uninstalling alsa-base and alsa-oss with apt; this uninstalled gdm and xubuntu-desktop as dependencies.  Reboot, login as root via the console, reinstall alsa-base and alsa-utils, use alsamixer to set the Master volume from zero, and it was all working again.

Installed gdm and xubuntu-desktop back afterwards, of course.  Might have been just a configuration issue, but I don't remember doing any sound-related changes between when the sound worked and when it didn't.

Funny how happy it feels to get magical sound coming from once silent speakers.  :)

---

### Post by gtdaqua on 2007-10-29
> **holodad said:**
> I had the same problem and solved it with this:

*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

Cheers

Previously my sound card was not even detected. running asoundconf returned nothing!

Followed the above commands and now I can see the sound option enabled. I am downloading gstreamer and restricted extras to see if I can hear the audio in AVI files.

btw, am using Kubuntu Gutsy 32 bit.

---

### Post by gtdaqua on 2007-10-29
> **gtdaqua said:**
> Previously my sound card was not even detected. running asoundconf returned nothing!

Followed the above commands and now I can see the sound option enabled. I am downloading gstreamer and restricted extras to see if I can hear the audio in AVI files.

btw, am using Kubuntu Gutsy 32 bit.

Yes! Sound works now!

Thanks!

---

### Post by cwrann on 2007-10-29
Pardon me for asking a question twice but because this thread is still active I thought I would give it a shot. 

I had to switch to analog sound to get any sound at all. I have a sound blaster audigy SE sound card. Would the quality be batter in digital, if so, any suggestions on getting digital to work? Also what is IEC950 and do I want it or not?

---

### Post by yalarad on 2007-11-02
> **holodad said:**
> I had the same problem and solved it with this:

*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

Cheers

This worked for me - thank you.

---

### Post by Orius on 2007-11-13
Had sound immediately after install from live CD, but somehow after running updates, lost sound.

So, I did as instructed above:
> *  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* RebootBut wasn't quite sure what settings I was meant to change.
> setup your sound settingsSince I am a newb with Ubuntu/Linux I didn't want to fiddle with a bunch of settings and screw something up.  Any specific changes I should be looking to make?
My laptop hardware (listing what might be important for sound)
Asus Z96J
Intel 945GM + ICH7-M Chipset
RealTek HDA/AC97 Audio

Any help would be appreciated.

---

### Post by cwrann on 2007-11-14
The sound options you want to fiddle with depends on your speaker set-up.
 Right click on the volume control icon and select open volume control. Fiiddle with the settings until you find the one that works for you. If none of those volume controls do anything look under preferences in volume control and select more options.

---

### Post by wootah on 2007-12-25
> >I had the same problem and solved it with this:

>* sudo apt-get install module-assistant
>* sudo m-a update
>* sudo m-a prepare
>* sudo m-a a-i alsa
>* Reboot and setup your sound settings

>Cheers


**************


Fixed problem for me! nVidia MCP55 High Def Audio stopped working after an upgrade to Ubuntu Gusty 7.10. Couldn't figure out what happened between the update to cause the problem. I lost sound and all that was recognized was my webcam's microphone (red X on the speak icon in the 'tray'). Thx very much to poster: Holodad! Good job!

~Jaymes

---

### Post by Leo the Lion on 2008-01-11
> **wootah said:**
> **************


Fixed problem for me! nVidia MCP55 High Def Audio stopped working after an upgrade to Ubuntu Gusty 7.10. Couldn't figure out what happened between the update to cause the problem. I lost sound and all that was recognized was my webcam's microphone (red X on the speak icon in the 'tray'). Thx very much to poster: Holodad! Good job!

~Jaymes

I'm on a HP dv2000 and all of a sudden I lost sound. I did what HOLODAD suggested but nothing happened. 
Any thoughts?

---

### Post by jjnguy13 on 2008-02-10
> **holodad said:**
> I had the same problem and solved it with this:

*  sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

Cheers

Worked for me!

Creative soundblaster.

---


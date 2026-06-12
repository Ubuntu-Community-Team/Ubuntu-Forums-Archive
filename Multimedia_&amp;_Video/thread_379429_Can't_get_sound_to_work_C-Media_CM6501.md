---
title: "Can't get sound to work: C-Media CM6501"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by haider254 on 2007-03-08
I can't get the sound to work :(, I've gone through the comprehensive sound guide. My windows installation just went kaput and my main PC is also my HTPC,  so problems galore!  If I can get this sound to work proplerly I'll take kubuntu on full time!

I Managed to get the sound half working (played MP3s, online content clean,  but avis were just messy) at one point on ubuntu... I have no idea what I did though.

I'm kurrently running kubuntu (hot of the press)...


My motherboard, uses the onboard sound card:
[http://www.asrock.com/mb/overview.asp?Model=939Dual-VSTA&s=](http://www.asrock.com/mb/overview.asp?Model=939Dual-VSTA&s=)

---

### Post by becominglumberg on 2007-03-18
I have a c-media card as well, onboard my mobo.

I don't know if you have serious desktop preferences, but I have always found that my c-media chip works much better under a GNOME environment. I do not know why. Also, I have never gotten volume control to work through main, I have to control it through the PCM.

There is a driver for it on the c-media website, but I have never been able to get it to go. Perhaps you will have a better time of it, but I think the driver in the kernel is good enough.

---

### Post by Lord Illidan on 2007-03-18
Regarding the OP..what is your exact problem, please? Sound works or doesn't works? Or it used to work under GNOME and now doesn't work in KDE?

About KDE and GNOME, you might have to disable the KDE sound server...Do it from kcontrol or else type 

```
killall artsd
```

Artsd, the soundserver is quite a bunch of sh**...and is due to be replaced in KDE 4 and only provides the beeps and whistles that come with kde, not mp3s, etc.

---

### Post by jamyskis on 2007-03-27
I figured out a rather unorthodox solution for this - apparently the sound chipset goes over the USB buses, which you'll see if you type lsusb in the terminal. If you're using Edgy, go to the multimedia preferences and select USB audio for all the outputs and inputs. It should work then.

---

### Post by gcrawford3 on 2007-04-20
Thank you so much - USB settings solved everything.

---

### Post by samborambo on 2007-08-19
OK, so I got this CM6501 sound chip on my M2N-E SLI board to work but I can't get mplayer or mythtv to control the volume. Has anyone got this working? How about PCM, DTS and AC-3 passthrough for SPDIF?

Cheers,

Sam.

---

### Post by zeroconf on 2007-08-22
> I figured out a rather unorthodox solution for this - apparently the sound chipset goes over the USB buses, which you'll see if you type lsusb in the terminal. If you're using Edgy, go to the multimedia preferences and select USB audio for all the outputs and inputs. It should work then.

Where is this in KDE? I'm using Kubuntu 7.04 and [Asus M2N-E SLI](http://www.asus.com/products4.aspx?modelmenu=2&model=1419&l1=3&l2=101&l3=370&l4=0) motherboard and no sound. But Amarok, mplayer, etc. will play but no sound is heard :(
This CM6501 theme is also spoken [here](http://ubuntuforums.org/showthread.php?p=3232242). [It seems](http://www.qbik.ch/usb/devices/showdev.php?id=3925) like in Ubuntu 7.10 [is ALSA 1.0.14](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=gutsy&release=all), which has full support for CM6501 chipset.
```
cat /proc/asound/version
``` will show the ALSA version.

Also [here](http://www.linuxquestions.org/questions/showthread.php?t=508691) is one forum about that.
[Here](ftp://dlsvr02.asus.com/pub/ASUS/misc/audio/c-media/) is new versions of CM6501 drivers for Windows and some older versions for Linux.
[Here](http://www.cmedia.com.tw/forums/viewtopic.php?t=807) is the forum at CMedia webpage about CM6501.

Also this trick didn't help, that if you create ~/.asound file wich contains this:
```

pcm.usb-audio {
type hw
card 0
}

ctl.usb-audio {
type hw
card 0
}

```

One trick is also disable USB legacy support in BIOS....

At the command line:
```
$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device
```
```
$ lsmod | grep snd
snd_usb_audio          79744  1
snd_pcm_oss            44544  0
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_dummy           4740  0
snd_seq_oss            32896  0
snd_seq_midi            9600  0
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
usbcore               134280  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
```
```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
```
```
$ uname -r
2.6.20-16-generic
```

---

### Post by Unavoidable on 2007-08-28
> **jamyskis said:**
> I figured out a rather unorthodox solution for this - apparently the sound chipset goes over the USB buses, which you'll see if you type lsusb in the terminal. If you're using Edgy, go to the multimedia preferences and select USB audio for all the outputs and inputs. It should work then.

I tried this solution, which gave me sound in most of my music and video files. I'm still having trouble with sound in Flash though.

I'm on an Asus M2N-E SLI mobo with that on-board sound card.

Without the USB solution I still get no sound at all. Any help?

---

### Post by WA_Mozart on 2007-09-05
I have an Asrock AM2NF3 motherboard with the CM6501 soundcard. 

Fixed the problem like this:

System - Preferences - Sound

Select USB Audio everywhere, instead of ALSA

---

### Post by silentsunami on 2007-09-13
i got the sound to play mp3s. But i miss the the login sound of ubuntu, anyone can help me. There are really no solutions for this?

---

### Post by Handssolow on 2007-09-13
Same problems here. I've made some progress with the C-Media CM6501 on-board sound chip on my Asrock 939Dual-Vsta motherboard, login logout sounds are played but the main volume control has a mind of it's own and only one set of speakers work when I play music CDs

aplay -l reports this-

**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but lspci -v shows nothing I or Ubuntu recognises as a sound card or soundchip.

sudo modprobe snd- 

gives the following answer-

FATAL: Module snd_ not found.

The onboard CM6501 sound chip seems to be recognised as part PnP and part USB device so it appears to show up as two sound devices. Initially I selected USB in System>Preferences>Sound and was able to play most of the test sounds except the Login and Logout sounds which were silent.

An interesting series of posts from Forum members  [here](http://ubuntuforums.org/showthread.php?t=498772&highlight=no+system+sounds) suggested that I needed to tell Ubuntu that my soundchip was called "default".

Inputting
asoundconf set-default-card default 
enabled the Login and Logout sounds though some of the other desktop sounds options seem mostly clicks or very short beeps, no Siren or Boing.

alsamixer seems partially functional, I can only get one set of speakers working. Also a separate microphone input works with Skype but not the microphone on my Logitec webcam's microphone. Applications>Sound & Video> Sound Recorder doesn't yield any recorded sounds.

Any other suggestions?

---

### Post by Crafty Kisses on 2007-09-13
I just kinda scanned through this post, but can you post the lspci output?

---

### Post by Handssolow on 2007-09-13
lspci gives just the following -

00:00.0 Host bridge: ALi Corporation M1695 K8 Northbridge [PCI Express and HyperTransport]
00:01.0 PCI bridge: ALi Corporation PCI Express Root Port
00:02.0 PCI bridge: ALi Corporation PCI Express Root Port
00:03.0 PCI bridge: ALi Corporation PCI Express Root Port
00:04.0 Host bridge: ALi Corporation M1689 K8 Northbridge [Super K8 Single Chip]
00:05.0 PCI bridge: ALi Corporation AGP8X Controller
00:06.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:07.0 ISA bridge: ALi Corporation M1563 HyperTransport South Bridge (rev 70)
00:07.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:11.0 Ethernet controller: ALi Corporation ULi 1689,1573 integrated ethernet. (rev 40)
00:12.0 IDE interface: ALi Corporation M5229 IDE (rev c7)
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)
05:07.0 USB Controller: NEC Corporation USB (rev 41)
05:07.1 USB Controller: NEC Corporation USB (rev 41)
05:07.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

---

### Post by davedosch on 2007-11-14
I just fixed mine.  I have the ASUS M2N-E SLI motherboard with the C-Media CM6501 and couldn't get the sound to work at all.  What eventually worked was doing:

asoundconf set-default-card default

then doing the complete uninstall/reinstall of the sound on my system by:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils  *(Uninstall sound, also uninstalls the gdm and desktop for some reason in the GNOME Ubuntu)*
sudo apt-get install linux-sound-base alsa-base alsa-utils   *(Reinstall sound)*
sudo apt-get install gdm ubuntu-desktop   *(Necessary on the GNOME Ubuntu)*

*Note: if you tried the ~/.asound file configuration listed in the earlier post of this thread, in my experience you need to remove the .asound file first or you will end up with no USB audio device.*

Entering the* asoundcof set-default-card default* may be all that's needed to get the cmedia usb audio working, when I made that entry the alsa mixer seemed to work, but when I rebooted the .asound file took the snd_usb_audio out of the system, requiring the uninstall/reinstall.  If your like me, you've probably been messing with the audio for a while, and doing the complete install is probably a good idea anyway.

---

### Post by Handssolow on 2007-11-14
Unfortunately davedosch  I've not detected any difference after following your instructions.
To repeat my few observations about implementation of the CM6501 on my Asrock 939Dual VSTA mobo-. Surprisingly asoundconf list reports two sound cards, PnP and USB based as shown here-

Names of available sound cards:
U0x46d0x8b2
default

If I select PnP or "default" as it seems to be named with 
asoundconf set-default-card default
Mostly I can play all the tests sounds including Login Logout sounds in Preferences>Sound and then if I select the USB options, though beep, siren,click and boing sound - but not in keeping with their descriptions. Two USB devices are shown in sound capture which I assume are the microphone socket and my USB Logitech webcam's microphone. (With Skype I have to use  a separate microphone because the inbuilt microphone doesn't seem to be supported)

If I select Sound capture I get feedback and the error message-
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'

If I choose instead the "other" sound card!! with-
asoundconf set-default-card U0x46d0x8b2
Things are worse, I can play the test sounds but not the  Login Logout sounds 

I think I've got only basic stereo audio available and several of  my mobo's 7.1 channel audio sockets don't produce any output. I can use Alsamixer  but it's only partially implemented. Apart from being unable to use my webcam's microphone, my biggest gripe is that I have no easy access to a sound volume control on my desktop, only a microphone control  shows. If I play a music CD or play internet audio I have to use my monitor's remote control to adjust the sound level.

Regrettably I only see a solution available in Ubuntu if many more users had this CM6501 audio chip or if I knew more about programming in Linux.

---

### Post by Yellow Pasque on 2007-11-14
If you boys & girls get tired of trying to fix ALSA, see my signature.

---

### Post by Handssolow on 2007-11-15
Temüjin, does OSSv4 support the C-Media CM6501 sound chip, I couldn't see it listed in your link.
Any reports available of using OSSv4 with the CM6501 based sound system?

---

### Post by Yellow Pasque on 2007-11-17
Not that I know of, but it could possibly be supported as USB audio since that's the bus it uses. I've created a post for you in the OSS support forum and the developers are very good about responding to questions about their product.
[http://www.4front-tech.com/forum/viewtopic.php?p=6675#6675](http://www.4front-tech.com/forum/viewtopic.php?p=6675#6675)

---

### Post by Handssolow on 2007-11-17
To recap, I can play a CD and hear streamed video but not with RealPlayer where I either hear nothing or get an error message. I have no volume control on the desktop just a microphone control unless I double click. Alsamixer only partially works.
lspci
shows nothing I can identify as related to my CM6501 sound chip's either as PnP or USB.

asoundconf list what seems to be two sound cards hence-
Names of available sound cards:
U0x46d0x8b2
default

asoundconf set-default-card default seems better than choosing asoundconf set-default-card U0x46d0x8b2
If I select the latter I only get a microphone control in alsamixer.

I found advice on a Gentoo Forum suggesting that because the CMI6501 chip sits on USB,  ohci driver for the bus and usb-audio driver for the chip are required.

As lspci shows nothing relevant linking USB to anything audio, so is the problem a missing ohci, a driver issue or both? How do I do the checks?

---

### Post by Handssolow on 2007-11-20
I've not much progress but I've been looking into microphone function recently.
Using the application Sound Recorder I can use the microphone on my Logitech QuickCam Pro 4000 if  in Preferences>Sound Sytem I select OSS Open sound system for audio capture. It still worked if I selected  asoundconf set-default-card default or asoundconf set-default-card U0x46d0x8b2, though as posted before with the latter choice I lose loggin loggout sounds and get limited alsamixer function.

Under Skype Alsa and OSS are shown as available. Despite selecting many different options in Skype>Sound Devices, at no time using test calls did I hear my own voice.

Very strange, why can I use my webcam's microphone with Sound Recorder but not under Skype?

---

### Post by Handssolow on 2007-11-21
Skype (Beta) Version 2.0.0.13 is out with wecam support and I've got my Logitech Quickcam's microphone working with the following "Sound Devices" selections-
Sound in.... USB Device  U0x46d:0x8b29 (hw: U0x46d0x8b2,0)
Sound out...Default
Ringing ...... Default

---

### Post by zeroconf on 2007-11-26
> **davedosch said:**
> I just fixed mine.  I have the ASUS M2N-E SLI motherboard with the C-Media CM6501 and couldn't get the sound to work at all.  What eventually worked was doing:

asoundconf set-default-card default

then doing the complete uninstall/reinstall of the sound on my system by:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils  *(Uninstall sound, also uninstalls the gdm and desktop for some reason in the GNOME Ubuntu)*
sudo apt-get install linux-sound-base alsa-base alsa-utils   *(Reinstall sound)*
sudo apt-get install gdm ubuntu-desktop   *(Necessary on the GNOME Ubuntu)*

*Note: if you tried the ~/.asound file configuration listed in the earlier post of this thread, in my experience you need to remove the .asound file first or you will end up with no USB audio device.*

Entering the* asoundcof set-default-card default* may be all that's needed to get the cmedia usb audio working, when I made that entry the alsa mixer seemed to work, but when I rebooted the .asound file took the snd_usb_audio out of the system, requiring the uninstall/reinstall.  If your like me, you've probably been messing with the audio for a while, and doing the complete install is probably a good idea anyway.

It's amazing!!! I got my sound work! God bless all of you! Even my microphone works! I installed Audacity and choosed from preferences ALSA USB PnP device for playback and recording and it works! Also Skype 2.0.0.13 beta works - both: microphone and listening. I use Kubuntu 7.10 and all updates all done.

---

### Post by DrMilo on 2007-12-03
My problem seems to be crummy sound on some .avi files. You can hear everything but it sounds like everyone is inhaling helium. Not all .avi files, some work fine. I have every codec that automatix and easyubuntu provide and all these files worked fine before I migrated my hard drives to a new motherboard and CPU.

---

### Post by maxter on 2007-12-05
this fix all problem
reported from:

[http://ubuntuforums.org/showthread.php?t=312929](http://ubuntuforums.org/showthread.php?t=312929)

---------------

Okay, after much digging and probing ("thanks" everybody for helpful advices -  ) I found out that, in fact, Ubuntu prevents USB audio from becoming device 0:

Code:

sudo nano /etc/modprobe.d/alsa-base

And we have right at the end:
Code:

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

As you can see, you just have to put your specific soundcard as index=0 (in my case, it was snd-usb-audio). Now everything works yay

---

### Post by Handssolow on 2007-12-06
> **maxter said:**
> this fix all problem
reported from:
[http://ubuntuforums.org/showthread.php?t=312929](http://ubuntuforums.org/showthread.php?t=312929)

---------------

Okay, after much digging and probing ("thanks" everybody for helpful advices -  ) I found out that, in fact, Ubuntu prevents USB audio from becoming device 0:

Code:

sudo nano /etc/modprobe.d/alsa-base

And we have right at the end:
Code:

# Prevent abnormal drivers from grabbing index 0
snd-bt87x index=-2options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

As you can see, you just have to put your specific soundcard as index=0 (in my case, it was snd-usb-audio). Now everything works yay

My Asrock 939Dual-VSTA mobo and C-Media CM6501 audio has  
asoundconf list showing two parts to my audio system, default and U0x46d0x8b2
My audio seemed optimised if I selected default rather than  U0x46d0x8b2
asoundconf set-default-card default
What did you do with this maxter?

Selecting default I've got Skype Beta working with my USB Logitech webcam's microphone and can record my voice with Sound Recorder but what I haven't got is anything other than simple front stereo. I'm not sure how I could test my system further but there's no audio  output from my mobo's sockets other than front stereo.

I've played around altering my /etc/modprobe.d/alsa-base file with
options snd-usb-audio index=-2 to =0
However, I  lose quality of my recorded voice using a test call with Skype and my USB Quickcam Pro webcam's microphone so I've gone back to =-2 
I'm not sure if I should alter options snd-usb-usx2y index=-2

Please will posters report what they've chosen with asoundconf set-default-card xxxxxx
What settings you've chosen in System>Preferences>Sound?
What improvements in functionality you've achieved.
Does Sound Recorder work for you?
Does Skype?

---

### Post by kamshi on 2008-03-15
> Okay, after much digging and probing ("thanks" everybody for helpful advices - ) I found out that, in fact, Ubuntu prevents USB audio from becoming device 0:

Code:

sudo nano /etc/modprobe.d/alsa-base

And we have right at the end:
Code:

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2

As you can see, you just have to put your specific soundcard as index=0 (in my case, it was snd-usb-audio). Now everything works yay

Since I changed '/etc/modprobe.d/alsa-base', I'm getting constantly a Kernel Panic. Sometimes at bootup, but most likely after login. The system freezes and the keyboard-LEDs are blinking. I wrote down the sys-message which occured while I booted the system:

```
[  69.404000] EIP: [<f8ad0437<] update_wstats+0x87/0xd0[at76_usb] SS:ESP0068:df839da4 [  69.408000]
Kernel panic - not syncing: fatal exception in interrupt
```

Any ideas? I can hardly work on my Ubuntu 'cause after some minutes the system freezes. So I'm forced to temporarily using my old Win-XP :(. Disabling sound may fix the problem, but I want to hear my beloved music-collection while coding ;). Sys-specs are the following:

```
Computer:
      Computer Type                                     ACPI-Multiprocessor-PC

Motherboard:
      CPU Type                                          AMD X2 BE2350 AM2 2100 2000 1MB, 2100 MHz
      Motherboard Name                                  ASRock AM2NF3-VSTA
      Motherboard Chipset                               nVIDIA nForce3 250, AMD Hammer
      System Memory                                     2528 MB  (Registered DDR SDRAM)
      BIOS Type                                         AMI (07/16/07)
      Communication Port                                Communication Port (COM1)
      Communication Port                                ECP-Printer Port (LPT1)

Display:
      Video Adapter                                     SAPPHIRE Radeon X1550 Series Secondary  (256 MB)
      Video Adapter                                     SAPPHIRE Radeon X1550 Series  (256 MB)
      Monitor                                           HP w2207h  (CZD74802YX)

Multimedia:
      Audio Adapter                                     C-Media CM6501 Like Sound Device

Storage:
      IDE Controller                                    NVIDIA nForce3 250 Parallel ATA Controller (v2.6)
      IDE Controller                                    NVIDIA nForce3 250 Serial ATA Controller (v2.6)
      SCSI/RAID Controller                              SCSI/RAID Host Controller
      Floppy Drive                                      Floppy Drive
      Disk Drive                                        SAMSUNG HD400LD  (372 GB, IDE)
      Disk Drive                                        Maxtor 6Y160P0  (160 GB, 7200 RPM, Ultra-ATA/133)
      Optical Drive                                     HL-DT-ST DVDRAM GSA-H10N
      Optical Drive                                     HL-DT-ST DVD-ROM GDR8161B  (16x/48x DVD-ROM)
      Optical Drive                                     NA5149M HEF081E SCSI CdRom Device
      SMART Hard Disks Status                           OK

Partitions:
      C: (FAT32)                                        69984 MB (513 MB free)
      D: (FAT32)                                        61044 MB (1869 MB free)
      G: (NTFS)                                         25258 MB (6021 MB free)
      H: (NTFS)                                         40962 MB (14739 MB free)
      J: (NTFS)                                         40962 MB (13494 MB free)
      Total Size                                        232.6 GB (35.8 GB free)
```

Greetings kamshi

---

### Post by Yellow Pasque on 2008-03-15
kamshi, perhaps you could use a LiveCD to edit your alsa-base file, or you could try disabling the onboard audio and/or USB in the BIOS.

---

### Post by kamshi on 2008-03-16
That's not the problem. I COULD if I wanted to do so, but I want to enable sound and get a stable system. I can't use any media with no sound... Does anybody know how I can get sound working without this disturbing bug? Are there any linux modules out there for this soundchip? I couldn't find any, neither via google or the [official c-media website]("http://www.cmedia.com.tw"). Is it possible to use a windows driver (although I don't like it that way...)? Or do I have to install the alsa packages (alsa-firmware, alsa-tools, alsa-utils)? Think I'll try to do so...

Greetings kamshi

edit: got it to work :).I don't know WHY it's working after I changed the line 'options snd-usb-audio index=-2' back to 'options snd-usb-audio index=0', but who cares... maybe because the three alsa-packages were missing?!?

---

### Post by Yellow Pasque on 2008-03-16
kamshi, I just meant that you would temporarily disable the audio to get your system to boot and fix the alsa-base file.

---


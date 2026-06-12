---
title: "No video out and audio out in Skype"
date: 2011-12-15
forum: Multimedia Software
---

### Post by pierreu1 on 2011-12-15
Okay! Should I update to 11.10 like update manager insists I do?

Initially, I had no problem with audio out, but some of the fixes given in a [thread]("http://ubuntuforums.org/showthread.php?t=1886199&goto=newpost") that I started eradicated my audio out in Skype as well. My audio and video work well outside of Skype.

I have posted another mpost under here with detailed info from an alsa script:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

PLease check the second post and please tell me what I should do. Thank you



My cam is a usb rocketfish and my headphone is RCA (it connects to the headphone and mic jacks of the computer).

Codec: Realtek ALC861
Codec: LSI Si3054

ALC861/660
==========
  3stack        3-jack
  3stack-dig    3-jack with SPDIF I/O
  6stack-dig    6-jack with SPDIF I/O
  3stack-660    3-jack (for ALC660)
  uniwill-m31   Uniwill M31 laptop
  toshiba       Toshiba laptop support
  asus          Asus laptop support
  asus-laptop   ASUS F2/F3 laptops
  auto          auto-config reading BIOS (default)


The properties of the launcher icon is ... bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

I am told in the other thread that I should install libv4l-0:i386, but I could not find this in synaptic not could I install it in terminal.

Maybe I need to install the default audio and video settings, if that can be done?

I have been told that pulseaudio and skype don't seem to work well, so I tried to switch to use the alsa plug=ins in the multimedia selector (that is what I have set it to). But, in Skype, there is no alsa option in the audio. I am pretty sure that skype should be using Alsa, but then I KNOW NOTHING, so bear with me. I hope this kinds of make sense to you! :)

Thanks for your help.

lsusb returns this:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 2222:3085 MacAlly 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


Thanks.

-Loaded Modules-
nls_utf8
isofs
binfmt_misc
parport_pc	 : PC-style parallel port driver
ppdev
dm_crypt	 : device-mapper target for transparent encryption / decryption
snd_usb_audio	 : USB Audio
snd_hda_codec_si3054	 : Si3054 HD-audio modem codec
snd_usbmidi_lib	 : USB Audio/MIDI helper module
snd_hda_codec_realtek	 : Realtek HD-audio codec
arc4	 : ARC4 Cipher Algorithm
snd_hda_intel	 : Intel HDA driver
iwl3945	 : Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
snd_hda_codec	 : HDA codec core
snd_hwdep	 : Hardware dependent layer
snd_seq_midi	 : Advanced Linux Sound Architecture sequencer MIDI synth.
snd_rawmidi	 : Midlevel RawMidi code for ALSA.
iwlcore	 : iwl core
gspca_sn9c20x	 : GSPCA/SN9C20X USB Camera Driver
gspca_main	 : GSPCA USB Camera Driver
snd_atiixp_modem	 : ATI IXP MC97 controller
snd_seq_midi_event	 : MIDI byte &lt;-&gt; sequencer event coder
videodev	 : Device registrar for Video4Linux drivers v2
snd_via82xx_modem	 : VIA VT82xx modem
snd_intel8x0m	 : Intel 82801AA,82901AB,i810,i820,i830,i840,i845,MX440; SiS 7013; NVidia MCP/2/2S/3 modems
mac80211	 : IEEE 802.11 subsystem
snd_ac97_codec	 : Universal interface for Audio Codec &apos;97
snd_seq	 : Advanced Linux Sound Architecture sequencer.
ac97_bus
pcmcia	 : PCMCIA Driver Services
snd_pcm	 : Midlevel PCM code for ALSA.
joydev	 : Joystick device interfaces
snd_timer	 : ALSA timer interface
snd_seq_device	 : ALSA sequencer device management
ipt_REJECT	 : Xtables: packet &quot;rejection&quot; target for IPv4
ipt_LOG	 : Xtables: IPv4 packet logging to syslog
xt_limit	 : Xtables: rate-limit match
xt_tcpudp	 : Xtables: TCP, UDP and UDP-Lite match
ipt_addrtype	 : Xtables: address type match for IPv4
xt_state	 : ip[6]_tables connection tracking state match module
yenta_socket
cfg80211	 : wireless configuration support

---

### Post by pierreu1 on 2011-12-16
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Fri Dec 16 08:20:24 UTC 2011
After doing ... wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

I got  ...

[http://www.alsa-project.org/db/?f=4d0b827a7ecf99f5b7b829290b3e7495e9c632a8](http://www.alsa-project.org/db/?f=4d0b827a7ecf99f5b7b829290b3e7495e9c632a8)

OR


!!Linux Distribution
!!------------------

Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite A100
Product Version:   PSAA8C-SK400E


!!Kernel Information
!!------------------

Kernel release:    2.6.38-13-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         i686
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.24.2


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b40000 irq 44
 1 [default        ]: USB-Audio - USB20 Camera    
                      USB20 Camera     at usb-0000:00:1d.7-4, high speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:27d8 (rev 02)
	Subsystem: 1179:ff10


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2

Shortened because it was irrelevant.

---

### Post by gordintoronto on 2011-12-16
In my experience, every release improves the handling of sound on notebook computers. At least try a LiveCD or LiveUSB of the latest release. Multisystem can produce a "persistent" USB drive, so you can install programs such as Skype.

I have read many horror stories about upgrading. I always do a fresh install, which is a lot easier if you have separate root and /home partitions. I also have excellent backup, thanks to a large USB hard drive.

---

### Post by pierreu1 on 2011-12-16
> **gordintoronto said:**
> In my experience, every release improves the handling of sound on notebook computers. At least try a LiveCD or LiveUSB of the latest release. Multisystem can produce a "persistent" USB drive, so you can install programs such as Skype.

I have read many horror stories about upgrading. I always do a fresh install, which is a lot easier if you have separate root and /home partitions. I also have excellent backup, thanks to a large USB hard drive.

EUREKA (for the audio setting)!

I found it! See attachment #4 for the answer!

Still no video though! RRRR!

I suspected that if the default did not work in audio, then the Intel ALC861 analog (which I saw in the diagnostics).

Oh! Thanks, Gord! Right? 

I actually couldn't handle not upgrading and did it. I made sure that I had updated Natty first though, as I think I read that this could be an issue.

It went well, but it was long: 6 hours.

I was hoping that it would solve the video and audio issue, but I think --during the install-- I chose the wrong choice (of basically keeping my system as it was before). The language was a bit unclear (I think it talked about "maintainer version or not"!  I assumed it meant "maintained"! Then, I tried to insert D, but it did not, and it used Y, instead, when I clicked somewhere else. SO, I wanted to try a fresh version, but the "forces" did not let me. :) 

BTW, my video and sound outside of Skype works!, but still no luck within Skype!

I have attached a few screenshots to let you know where I am at.

I did the alsa test again  and the dsmeg which returned this, respectively:

Check at [http://www.alsa-project.org/db/?f=e37e57842c8988803dc0f9d44b5c4db2bd21007c](http://www.alsa-project.org/db/?f=e37e57842c8988803dc0f9d44b5c4db2bd21007c)

(I noticed that it returned this:

[COLOR="Blue"]!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b40000 irq 44
 1 [Camera         ]: USB-Audio - USB20 Camera
                      USB20 Camera at usb-0000:00:1d.7-4, high speed[/COLOR]

But, it seems to indicate that there is audio out of my camera, but there isn't. I have a regular audio.mic jacks combo (Cyber Acoustics headphone/mic headset) which is inserted into the front headphone/mic jacks). Maybe that is the issue. Could that be?

---

### Post by gordintoronto on 2011-12-17
According to this web site: [http://www.rocketfishproducts.com/products/computer-accessories/RF-WEB2C.html](http://www.rocketfishproducts.com/products/computer-accessories/RF-WEB2C.html)
the Rocketfish has a microphone.

When you run Cheese, and select Edit/Preferences, I assume there is a greyed-out "video" entry which says /dev/video0? It's possible you need to run Skype by entering the Terminal command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

---

### Post by pierreu1 on 2011-12-17
> **gordintoronto said:**
> According to this web site: [http://www.rocketfishproducts.com/products/computer-accessories/RF-WEB2C.html](http://www.rocketfishproducts.com/products/computer-accessories/RF-WEB2C.html)
the Rocketfish has a microphone.

When you run Cheese, and select Edit/Preferences, I assume there is a greyed-out "video" entry which says /dev/video0? It's possible you need to run Skype by entering the Terminal command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

Hi Gord,

Ah! I think we are getting somewhere. I wish I could be a bit more perspicacious though! I am really sorry, but when you think one way, it is sometimes hard to deprogram!

Thanks for helping me out. Well! You made me doubt myself, which is good, because upon searching this webcam, I found out that indeed it has a microphone. I did not know, but when I looked at it, it had a little hole, which indicated to me that maybe it had. The specs conforms this.

[http://www.rocketfishproducts.com/products/computer-accessories/RF-NBCAM.html](http://www.rocketfishproducts.com/products/computer-accessories/RF-NBCAM.html)

I do have that command, with an extra ' at the end though. That isn't working. I will try without the ', but I am pretty sure that was a typo. Right?

So, the headset mic. is working now. Not sure about the cam mic, but I suspect it could if I were to select the appropriate item in the audio settings in SKype which might fix the webcam video. I am not too sure how those things work. Maybe things will work if I leave the analog headset out. I will experiment and get back to you.

Yes! In the video settings there is USB20 Camera (/dev/video0)

I do use the icon on my desktop which has the command, as specified. I then enter my password and then I am in. But, still, no video out.

I found a read me file in a Microdia folder. It looks like this is the Rocketfish cam (as indicated above:  Bus 001 Device 002: ID 0c45:6288 Microdia PC Camera with Microphone (SN9C202 + OV9655), as returned by lsusb)

Here is what it states.

"SN9C20x USB 2.0 Webcam Driver
==============================

This driver is essentially a fork of the Syntek Webcam drivers for Linux
by Nicolas Vivien, specifically to accomodate SN9C20x chipset based Webcams.

The driver currently supports the latest version of Video For Linux i.e
V4L2. V4L1 is deprecated, and applications like Camorama that use only V4L1 will
only work with libv4l ("v4l1compat.so").

This driver currently supports Skype v2.x, Ekiga v2.x & even aMSN

Warning :
The SN9C20x USB 2.0 Webcam Driver for SN9C20x chipset based Webcams is
currently under development. Using this driver can result in damage and data
loss to your system. Use this driver only if you know what you are doing.

Table of contents :

1. Requirements
 1.1 Kernel module
 1.2 Documentation
 1.3 Decoder

2. Available Packages

3. Compilation
 3.1 Kernel module
 3.2 Documentation

4. Testing

5. Installation

6. Usage

7. Status of project

8. Documentation & References

9. Contact

10. Licence

11. Disclaimer

--------------------------------------------------------------------------------

1. Requirements

 1.1 Kernel module

   To compile the driver you need :
     Kernel 2.6.22 or higher
     Kernel headers
     make
     gcc

 1.2 Documentation

   To compile the documentation you need :
     doxygen
     graphviz

 1.3 Decoder

   Most video applications do not support the image encoding SN9C20x-based
   webcams offer. Such applications need to have the image stream converted
   for them. This can be done using "libv4l", which is pre-loaded between the
   application and the video resource and translates the image stream into a
   usable format.

   Most distributions offer precompiled packages. If yours does not, the
   sources are available here :
     [http://freshmeat.net/projects/libv4l/](http://freshmeat.net/projects/libv4l/)

   Consult libv4l's README for usage details.

--------------------------------------------------------------------------------

2. Available Packages

  There are packages for various distributions available here :
    [http://repo.or.cz/w/pkgmicrodia.git](http://repo.or.cz/w/pkgmicrodia.git)

--------------------------------------------------------------------------------

3. Compilation

 3.1 Kernel module

   To build the kernel module ("driver") :
     $ make
     (This will create the kernel object file called "sn9c20x.ko".)

 3.2 Documentation

   To build the documentation :
     $ make doc
     $ make cleandoc

--------------------------------------------------------------------------------

4. Testing

  To load the driver, follow these steps (as root) :
    # modprobe videodev
    # modprobe compat-ioctl32  // Only required for 64-bit Linux OS
    # make insmod

  Note: Most applications require libv4l for image format decoding (see "1.3
  Decoder"). Consult libv4l documentation for full usage details. Here is an
  example for a common usage :
    $ LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so mplayer tv:// -tv \
      driver=v4l2:width=640:height=480:fps=25:device=/dev/video0 -vo xv

--------------------------------------------------------------------------------

5. Installation

  $ strip -g sn9c20x.ko
  And as root :
  # cp sn9c20x.ko /lib/modules/`uname -r`/kernel/drivers/media/video/usbvideo/
  # depmod -a

--------------------------------------------------------------------------------

6. Usage

  We recommend using v4l2ucp to adjust and improve image quality.
    [http://sourceforge.net/projects/v4l2ucp/](http://sourceforge.net/projects/v4l2ucp/)

  We are also developing our own GUI, available here :
    [http://repo.or.cz/r/guimicrodia.git](http://repo.or.cz/r/guimicrodia.git)

--------------------------------------------------------------------------------

7. Status

  The kernel module is currently under active development.

  The full list of supported webcams can be found here :
    [http://groups.google.com/group/microdia/web/project-status](http://groups.google.com/group/microdia/web/project-status)

--------------------------------------------------------------------------------

8. Contact

  To request support, please contact us on Microdia Mailing List :
    [https://groups.google.com/group/microdia/](https://groups.google.com/group/microdia/)
    [email]microdia@googlegroups.com[/email]

--------------------------------------------------------------------------------

9. More Documentation & References

  All documentation and references for microdia webcam driver can be found at
    [http://groups.google.com/group/microdia/web](http://groups.google.com/group/microdia/web)

  Latest version of this driver is usually available at the following location
    [http://repo.or.cz/w/microdia.git](http://repo.or.cz/w/microdia.git)

--------------------------------------------------------------------------------

10. Licence

  SN9C20x USB 2.0 Webcam Driver is distributed under the GPL licence version 2
  or later (GPLv2+)."

I hope this helps!

---

### Post by pierreu1 on 2011-12-19
If you insert this line of code after right clicking on the Skype icon and going to properties and entering it in the command section, then the test in the video section of Skype will work for the Rocketfish USBCAM.

sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype "$@"'&#65279;&#65279;

I will test in a few days to see if it is stable in a call, as I have had many instances of video-in crashing and dropping after a few minutes of use. I suspect my video card cannot handle that much work. Some people claim that Compiz and Cairo-dock might overload the video card (which, in my case, is a cheap embedded intel).

I will get back to you soon.
__________________

---

### Post by gordintoronto on 2011-12-19
I've found that Skype places heavy demands on the CPU. What one does your computer have? (It runs just fine on my Phenom II X2 at 3.1 GHz, but that's a fairly powerful processor.)

---

### Post by pierreu1 on 2011-12-19
> **gordintoronto said:**
> I've found that Skype places heavy demands on the CPU. What one does your computer have? (It runs just fine on my Phenom II X2 at 3.1 GHz, but that's a fairly powerful processor.)

Ya! I think you are right! 

I have attached a screenshot of my system processes with % of CPU. I am surprised to see 4 or 5 Skype (albeit sleeping) processes being reported, consuming significant % of CPU share when I have NOT opened Skype! Is this normal? 

I also notice that with just Skype opened in a test mode configuration, I have peeks of 90% CPU load (average is 70%, range is 40 to 90%). When I open Skype and Chrome, the test area does not work all the time (looks like the video card is overloaded), but does work 2/3 times (see last attachment #4). Just Chrome opened returns maxes of 80% and lows of 40%. Is there any way (apart from not using Chrome) to reduce the CPU load and ensure that video + audio in Skype is not going to overtax the system (apart from buying another computer)! Would more ram help?

I restested things in a call and here are the results:

If you insert this line of code after right clicking on the Skype icon and going to properties and entering it in the command section, then the test in the video section of Skype will work for the Rocketfish USBCAM.

sh -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so /usr/bin/skype "$@"'&#65279;&#65279;

(found here: [http://community.skype.com/t5/Linux/...ight/true#M377](http://community.skype.com/t5/Linux/...ight/true#M377))

I will test in a few days to see if it is stable in a call, as I have had many instances of video in crashing and dropping after a few minutes of use. I suspect my video card cannot handle that much work. Some people claim that Compiz and Cairo-dock might overload the video card (which, in my case, is an cheap embedded intel).

After testing it in a call, the video lasted maybe a few minutes. It worked, but then I couldn't get it back after many trials. I could get the video feed from the other person though! I noticed that I had loads of Chrome programs and other stuff cluttering in my system, grabbing a share of the CPU, which shot up faster that to 100% a few times. The test video did not work either. I then rebooted it and tried the video test in Skype and it worked again. I noticed that I had way fewer stuff grabbing a share of my CPU. I will try next time to do a fresh boot and not open any other app and see if that makes a diff. I suspect it will.

1.86 GHz, single core, 1 GB RAM,... Open GL NO

[http://ark.intel.com/products/27243](http://ark.intel.com/products/27243)

Not sure exactly what I have in terms of integrated graphic card because I see so many different #s below. Maybe you would know. I have included in the attachment the specs of some, but not sure which is mine. I know I have a core solo, but there are many like that.

So, do you think the graphic card could be struggling during Skype calls, which might explain why video calls crashes, but not just audio calls? Do you think the CAiro dock/Compiz issue is something I should investigate? Do you think it could be a bandwith issue? I have up to 256 Kbps upload speed.

-PCI Devices-

Host bridge		: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

VGA compatible controller		: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])

Display controller		: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by gordintoronto on 2011-12-21
Your computer is roughly equivalent to today's netbooks, and videoconferencing in Skype has heavy demands, perhaps more than the CPU and video card can handle over a long call.

If you want to see what is using the CPU, I suggest you open a terminal and enter the command top, which uses less resources than System Monitor.

How old is your machine? The command sudo lshw > myconfig.txt will generate a text file with complete details about your computer. In particular, it will show the date of the BIOS, which is really your computer's "birthday."

---

### Post by pierreu1 on 2011-12-23
> **gordintoronto said:**
> Your computer is roughly equivalent to today's netbooks, and videoconferencing in Skype has heavy demands, perhaps more than the CPU and video card can handle over a long call.

If you want to see what is using the CPU, I suggest you open a terminal and enter the command top, which uses less resources than System Monitor.

How old is your machine? The command sudo lshw > myconfig.txt will generate a text file with complete details about your computer. In particular, it will show the date of the BIOS, which is really your computer's "birthday."

Oh! Thanks for that! System monitor uses a lot of "resources"?

My Machine is 4 years old. The code returned just:

PCI (sysfs)

---

### Post by gordintoronto on 2011-12-23
Sorry, I left out a command. If you open a terminal and enter the command:
gedit myconfig.txt
you will see all the details about your computer.

The previous command created a text file.

Sometimes System Monitor uses a lot of memory and CPU. I do not understand what causes this.

---


---
title: "troubleshooting input settings in Audacity"
date: 2014-01-25
forum: Multimedia Software
---

### Post by Drone4four on 2014-01-25
I am trying to get record my voice with my mic and Audacity.  But I can't seem to configure the right input settings.  I've tried every option available, but nothing seems to work.  See [here]("http://i.imgur.com/QPEjShr.png") for an image of the Pulse Audio Volume Control utility showing that my mic is working.  The pic also demonstrates 18 different input options to choose from in Audacity.  I've tried every single one of them without success even with 'Set as Fallback' option set for both input devices (CM108 and Analog).  

What else could I try?  Is there any other information that I could provide to continue troubleshooting?

Thanks for your attention.

---

### Post by nosbor73 on 2014-02-01
analog mic's are tricky to get working. you could just buy an usb audio card (some are cheap on ebay) save you time and hassle.

---

### Post by Drone4four on 2014-02-02
What&#8217;s interesting is that pulseaudio can detect input from my mic when it is plugged into my analog port at the front of my PC.  So for certain it the analog mic works just fine.  It&#8217;s just configuring it to work with Audacity that I am having trouble with.

I forgot to mention in my initial post that I have had a usb audio card plugged into my computer but haven&#8217;t been able to get it working with my mic either.  But thanks to your reminder, **nosbor73**, I Googled &#8216;usb audio input ubuntu&#8217; and came across some helpful documentation named, [UbuntuStudio/UsbAudioDevices]("https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices").

The guide is prefaced with, >  This document describes a method of maintaining ALSA device numbers for USB devices, including MIDI devices. It is not intended for beginning users, as the configuration is relatively arcane.    It&#8217;s dense and I don&#8217;t understand exactly how it could help me.  But for what it&#8217;s worth, here is some output from various commands they recommend.

Here is evidence that my usb audio card is connected and detected by ALSA:
```

(gnull@raring)-(0)-(11:22 PM Sat Feb 01)->
m-(~)-(56 files, 17Mb)--> cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdfff8000 irq 45
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xddffc000 irq 17
 2 [Device         ]: USB-Audio - USB PnP Sound Device
                      C-Media Electronics Inc. USB PnP Sound Device at usb-0000:00:1a.1-1, full speed

(gnull@raring)-(0)-(11:23 PM Sat Feb 01)->
m-(~)-(56 files, 17Mb)--> 

```

Here is lsusb briefly:

```

(gnull@raring)-(0)-(11:23 PM Sat Feb 01)->
m-(~)-(56 files, 17Mb)--> lsusb
Bus 003 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 004 Device 002: ID 0d8c:013c C-Media Electronics, Inc. CM108 Audio Controller
Bus 005 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(gnull@raring)-(0)-(11:23 PM Sat Feb 01)->
m-(~)-(56 files, 17Mb)--> 
```

Here is the same command with verbose
```

(gnull@raring)-(0)-(11:46 PM Sat Feb 01)->
m-(~)-(56 files, 17Mb)--> sudo lsusb -v | less >>lsusb.txt
[sudo] password for gnull: 

(gnull@raring)-(0)-(11:47 PM Sat Feb 01)->
m-(~)-(57 files, 17Mb)-->

```
And the pastebin for the contents of lsusb.txt here:  [http://pastebin.com/viFR9wC4](http://pastebin.com/viFR9wC4)

Here are the contents of /etc/modprobe.d/alsa-base.conf: 
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


```

With Google I also came across some documentation for [USB mics on Linux]("http://wiki.audacityteam.org/index.php?title=USB_mic_on_Linux") courtesy of the Audacity project.  The documentation explains:

> USB-microphones in OSS are usually setup as /dev/dsp1 under Linux.
The 1.2.x version of Audacity will not find /dev/dsp1 unless there is also a device called /dev/dsp0. (This is a bug in PortAudio that should be fixed in a future version.)
To work around this bug, try setting the AUDIODEV environment variable (at a terminal):
```
   $ AUDIODEV=/dev/dsp1 audacity 
```
or try running
```
   # ln -s /dev/dsp /dev/dsp0 
```

Before creating a symbolic link or env variable, I checked to see if /dev/dsp exists, which it apparently doesn&#8217;t.
Here is a further command as per this guide for audacity```

(gnull@raring)-(0)-(12:11 AM Sun Feb 02)->
m-(~)-(57 files, 17Mb)--> lsmod | grep snd
snd_hda_codec_hdmi     36855  4 
snd_usb_audio         140732  2 
snd_usbmidi_lib        24938  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hda_codec_realtek    78445  1 
snd_hda_intel          39619  10 
snd_hda_codec         136498  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_rawmidi            30180  2 snd_usbmidi_lib,snd_seq_midi
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                97451  8 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  32 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd

(gnull@raring)-(0)-(12:11 AM Sun Feb 02)->
m-(~)-(57 files, 17Mb)--> 

```

I&#8217;m sorta at a loss here of what all this information means and how it could help me.  As noted in the Ubuntu guide in the preface, this isn&#8217;t a problem easily solved by a newbie like myself. Maybe someone can see something in the data I shared here that I could alter or modify to get Ubuntu to recognize my mic that is now plugged into my USB sound card?

---

### Post by tgalati4 on 2014-02-02
OSS is an old audio framework that predates ALSA so don't use it and generally ignore the tutorials that use it.

Sometimes turning off the onboard sound using BIOS will help when using discrete sound cards or USB sound devices.  Run *alsamixer* in a terminal and make sure your gains are turned up to 70% across the board.  Run *pavucontrol* to make sure your gains are also set.  Then try all of the input selections in sequence until you see the meters in audacity come to life.  You need to right-click and select "monitor" on the microphone icon to see the meter levels.

---

### Post by Bucky Ball on 2014-02-02
> **tgalati4 said:**
> OSS is an old audio framework that predates ALSA so don't use it and generally ignore the tutorials that use it.

^^^
This. Steer clear. We can't help with an obsolete package that will possibly override alsa and pulseaudio settings.

Open terminal, type 'alsamixer' and check nothing is muted. Hit F6 and check other sound devices ...

---

### Post by nosbor73 on 2014-02-02
some mic's need external power so even if you set the correct gains in alsamixer it might not be enough to be heard.
you can try installing jackd2 (sudo apt-get install jackd2). then you can set it up as loop back test (mic to ear piece, speak or tap mic while you have headset on) and while that is running play around with the alsamixer (open up another terminal to run alsamixer go to the capture menu). might be easier than trying to debug audacity.
as root in a bash script
///////////////////////////
```

#!/bin/bash
killall -9 jackd
killall -9 jack_metro
jackd -dalsa -dhw:0 -r44100 &
sleep 4
jack_connect system:playback_1 system:capture_1

```
///////////////////////////////////////////////////////////////////////////

so you will need to connect your headset to the green slot on pc, and mic to pink slot.
from info above your default audio card is the intel (-dhw:0). if you wanted to test your usb run same jack server command as aboe but use -dhw:2

if you want to verify you can get audio via jack. this can be used
///////////////////////////////////
```

#!/bin/bash
killall -9 jackd
killall -9 jack_metro
jackd -dalsa -dhw:0 -r44100 &
sleep 4
jack_metro -b120 &
jack_connect metro:120_bpm system:playback_1

```
//////////////////////////////////////////////////////////////////////////

last time i worked in jack project they used powered mic's, and we used ubuntu 12.04 server, don't recall just sticking a non powered mic into mic socket every working properly.

---

### Post by Drone4four on 2014-02-03
I appreciate the time and care you put into your post, nosbor73, but I am not going tell my superuser to run a script with all sorts of commands - - commands which I have no clue as to what they do.  It’s also a bit disconcerting to be hearing all this from a forum user with less than 5 posts, not to mention some bizarre usage of forward slashes. I'm sorry but it's all too suspcisious.  You're intentions are probably not malicious.  I am not asking you to explain what each command does. I’m just gonna troubleshoot this problem from a different approach. 

> **tgalati4 said:**
> Run alsamixer in a terminal and make sure your gains are turned up to 70% across the board.  Run pavucontrol to make sure your gains are also set. Then try all of the input selections in sequence until you see the meters in audacity come to life.

I ran alsamixer and noticed that front mic and rear mic had their gains at 0%.  I bumped them up to 100% (to match all the other gains across the board). I ran pavucontrol which indicated that my CM108 Audio Controller Analog Mono was set to 100%. Then in Audacity I tried all 18 input selections. The meters didn't come to life. No dice.

> You need to right-click and select "monitor" on the microphone icon to see the meter levels. I see two microphone icons in Audacity and tried right clicking on and around them without seeing anything related to a monitor.

> Sometimes turning off the onboard sound using BIOS will help when using discrete sound cards or USB sound devices. 
I will now reboot my computer and will flip the switch to the discrete sound card to the USB sound device.  I will report back here after trying this.

---

### Post by Drone4four on 2014-02-03
I looked through every option in my BIOS for an audio-related switch without success. I triple checked everything.  

Is there anything else I could try?

---

### Post by nosbor73 on 2014-02-05
its up to you. jack is tricky to get working as a non root user, only because it try's to get too much memory.
if you install jack via the repo it does ask about memory allocation, but it must be some legacy bug where even still you have to run it as root for it to start. there are ways around it, but it means editing your security settings just to allow jack to run as higher priority / real time and take more memory.
the scripts just kill any remaining jack/ jack clients then start a jack server, sleep for 4 seconds before connecting the input and output ports (mic and ear). 
i worked on jack / alsa / embedded audio professionally, so don't take any meaning from me having only 5 posts (6 now).

---

### Post by Drone4four on 2014-02-05
I tried testing my usb sound card with the jack server script you suggested with sudo.  I used this script:
```

#!/bin/bash
killall -9 jackd
killall -9 jack_metro
jackd -dalsa -dhw:0 -r44100 &
sleep 4
jack_metro -b120 &
jack_connect metro:120_bpm system:playback_1

```
Here was the output:
```

(gnull@raring)-(0)-(09:40 PM Wed Feb 05)->
m-(~)-(64 files, 23Mb)--> sudo bash jackd-nosbor73.sh 
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio2
creating alsa driver ... hw:2|hw:2|1024|2|44100|0|0|nomon|swmeter|-|32bit
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/gnull/gvfs
      Output information may be incomplete.


ATTENTION: The playback device "hw:2" is already in use. The following applications  are using your soundcard(s) so you should  check them and stop them as necessary before  trying to start JACK again:

pulseaudio (process ID 2429)

Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
Cannot connect to server socket err = Connection refused
Cannot connect to server socket err = Connection refused
Cannot connect to server request channel
Cannot connect to server request channel
jack server is not running or cannot be started
jack server is not running or cannot be started
JACK server not running?
JACK server not running?

(gnull@raring)-(0)-(09:51 PM Wed Feb 05)->
m-(~)-(65 files, 23Mb)--> 

```
Is this message saying that the USB card is in use and jackd therefore can’t tell it to make a noise?

Then I plugged my mic into the pink jack on the front of my PC.  I used this script:
```
#!/bin/bash
killall -9 jackd
killall -9 jack_metro
jackd -dalsa -dhw:0 -r44100 &
sleep 4
jack_metro -b120 &
jack_connect metro:120_bpm system:playback_1

```
Here was the output:
```

(gnull@raring)-(0)-(09:51 PM Wed Feb 05)->
m-(~)-(65 files, 23Mb)--> sudo bash jackd-nosbor73.sh 
jackd: no process found
jack_metro: no process found
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2013 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/gnull/gvfs
      Output information may be incomplete.


ATTENTION: The capture device "hw:0" is already in use. The following applications  are using your soundcard(s) so you should  check them and stop them as necessary before  trying to start JACK again:

pulseaudio (process ID 2429)
jackd (process ID 1444
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
Cannot connect to server socket err = Connection refused
Cannot connect to server request channel
Cannot connect to server socket err = Connection refused
Cannot connect to server request channel
jack server is not running or cannot be started
JACK server not running?
jack server is not running or cannot be started
JACK server not running?

(gnull@raring)-(0)-(10:06 PM Wed Feb 05)->
m-(~)-(65 files, 23Mb)-->

``` 

It's a similar error message, although it doesn't mean anything to me.

What are we trying to accomplish with these 2 scripts?  Are we testing if my onboard sound card and usb sound card work?

---

### Post by Bucky Ball on 2014-02-05
> **nosbor73 said:**
> ... it must be some legacy bug where even still you have to run it as root for it to start.

Use QJackctl. I've never had to jump through the hoops you're describing, nor do I need to run as root. It is as simple as hitting QJackctl, a GUI for jack,  and hitting start. That's it, jack's running ... :-)

---

### Post by nosbor73 on 2014-02-06
it looks like pulse audio has taken over your audio. 
the goal was to try to get your mic working by running a simple loop back test.  
are you sure audacity or any other audio program is closed. just boot up and use those scripts only. when i installed ubuntu 13.10 it does install pulse audio, but i also installed jackd manually and my jackd has no problem starting up.

---

### Post by Bucky Ball on 2014-02-06
Yep. Jack will over-see everything. In Audacity, 'Audio Host' drop down at top left choose jack and set the in and out devices to 'system'. Jack should have connected the ins and outs behind the scenes for you ... hopefully.

As I say, the GUI to use for jack control is ... QJackctl.

---

### Post by tgalati4 on 2014-02-06
Make sure that OSS is removed from your system if you installed it previously:

```
apt-cache policy oss4-base
```

---

### Post by Drone4four on 2014-02-06
Heya fellas, I found a solution.  I got my mic working.  The solution was to plug my mic jack into the front of my PC and trying all six HDA Intel: ALC892 Analog (hw:0,2) options.  I tried this before.  I don’t know why it is working right now.  

All the hoops I jumped through were apparently unnecessary.  I’m sorry for making things overly complicated, attracting so much unnecessary attention and wasting everyone’s time.

---

### Post by Bucky Ball on 2014-02-06
Not a waste of time. Others can learn from your hoop jumping! Please mark thread as 'solved' to help them to do so. Thanks. ;)

---


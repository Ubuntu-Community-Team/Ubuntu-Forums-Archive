---
title: "No sound: Intel 82801aa and 9.04"
date: 2009-10-28
forum: Multimedia Software
---

### Post by mrmhead on 2009-10-28
in a Dell Optiplex GX110.

I followed through the sticky up top.  
aplay lists the right card.
lspci shows it.
Mixer sees it.
Listen plays - but I don't know if that would matter....
But I don't hear it!!

I checked the volume and mute buttons.  I've tried playing Flash from Youtube and a CD.  ... nada ,,,

I didn't see any other threads listing this card/machine.
I tried a few other things that didn't seem too dangerous, to no avail.

I downloaded alsa-driver-snapshot-tar.bz2 , but not real sure what to do with it.  The thread I got the info from was for a hp machine.  so I didn't want to run any commands.

Also thinking - since this is only my 3rd day in Xubuntu, should I wait a few more days and get Koala ...?
(2nd day was spent chasing a Flash issue)

a few hurdles, but looks promising...

Thanks
m

---

### Post by Ulysses361 on 2009-10-29
Please execute step 1, reboot and then send us output from step 3 and step 4 here:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by mrmhead on 2009-10-29
Thanks for the reply!
Here it goes:
[FONT=monospace]me@me-desktop:~$ wget -O alsa-info.sh [http://212.20.107.51/alsa-info.sh](http://212.20.107.51/alsa-info.sh)
--2009-10-29 21:08:49--  [http://212.20.107.51/alsa-info.sh](http://212.20.107.51/alsa-info.sh)
Connecting to 212.20.107.51:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2009-10-29 21:08:49--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 212.20.107.51
Reusing existing connection to 212.20.107.51:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 26,584      85.0K/s   in 0.3s    

2009-10-29 21:08:51 (85.0 KB/s) - `alsa-info.sh' saved [26584]

<<<and>>>
me@me-desktop:~$ bash alsa-info.sh --pastebin
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
Automatically upload ALSA information to pastebin? [y/N] : 


Your ALSA information is in /tmp/alsa-info.txt.pUyrnKRivA

me@me-desktop:~$ 
<<<<<<<<<<
The instructions said to use the arrow keys to select UPLOAD / SHARE - but it didn't do anything...
[/FONT]
Is this really what you want??:
>>>>>>>>>>>>

me@me-desktop:~$ cat /proc/asound/cards;  sudo aptitude install gnome-alsamixer asoundconf-gtk alsa-utils flashplugin-nonfree-extrasound;  asoundconf list;  aplay -l;  sudo lshw -C sound;  ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl;  lsmod | grep snd 
 0 [I82801AAICH    ]: ICH - Intel 82801AA-ICH
                      Intel 82801AA-ICH with AD1881A at irq 10
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "gnome-alsamixer"
Couldn't find any package whose name or description matched "asoundconf-gtk"
Couldn't find any package whose name or description matched "flashplugin-nonfree-extrasound"
Couldn't find any package whose name or description matched "gnome-alsamixer"
Couldn't find any package whose name or description matched "asoundconf-gtk"
Couldn't find any package whose name or description matched "flashplugin-nonfree-extrasound"
The following packages will be REMOVED:
  flashplugin-installer{u} gstreamer0.10-ffmpeg{u} 
  gstreamer0.10-plugins-ugly{u} liba52-0.7.4{u} libasound2-plugins{u} 
  libavcodec52{u} libavformat52{u} libavutil49{u} libid3tag0{u} 
  libmpeg2-4{u} libpostproc51{u} libpulse0{u} libschroedinger-1.0-0{u} 
  libsidplay1{u} libswfdec-0.8-0{u} libswscale0{u} libtwolame0{u} 
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
0 packages upgraded, 0 newly installed, 19 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 92.6MB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 132466 files and directories currently installed.)
Removing flashplugin-installer ...
Removing gstreamer0.10-ffmpeg ...
Removing gstreamer0.10-plugins-ugly ...
Removing liba52-0.7.4 ...
Removing libasound2-plugins ...
Removing libavformat52 ...
Removing libavcodec52 ...
Removing libswscale0 ...
Removing libpostproc51 ...
Removing libavutil49 ...
Removing libid3tag0 ...
Removing libmpeg2-4 ...
Removing libpulse0 ...
Removing libschroedinger-1.0-0 ...
Removing libsidplay1 ...
Removing libswfdec-0.8-0 ...
Removing libtwolame0 ...
Removing linux-headers-2.6.28-11-generic ...
Removing linux-headers-2.6.28-11 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Names of available sound cards:
I82801AAICH
**** List of PLAYBACK Hardware Devices ****
card 0: I82801AAICH [Intel 82801AA-ICH], device 0: Intel ICH [Intel 82801AA-ICH]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
  *-multimedia            
       description: Multimedia audio controller
       product: 82801AA AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
total 0
crw-rw----+  1 root audio 116, 33 2009-10-29 20:52 timer
crw-rw----+  1 root audio 116,  1 2009-10-29 20:52 seq
crw-rw----+  1 root audio 116, 25 2009-10-29 20:52 pcmC0D1c
crw-rw----+  1 root audio 116, 24 2009-10-29 20:52 pcmC0D0c
crw-rw----+  1 root audio 116,  0 2009-10-29 20:52 controlC0
drwxr-xr-x   2 root root      160 2009-10-29 20:52 .
crw-rw----+  1 root audio 116, 16 2009-10-29 20:53 pcmC0D0p
drwxr-xr-x  16 root root     3940 2009-10-29 21:23 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux me-desktop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Intel 82801AA-ICH with AD1881A at irq 10

Audio devices:
0: Intel 82801AA-ICH (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1881A
00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801AA SMBus Controller [8086:2413] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 02)
01:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
/usr/sbin/alsactl
snd_intel8x0           38684  4 
snd_ac97_codec        112676  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  2 snd_pcm_oss
snd_pcm                83716  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14496  0 
snd_rawmidi            29984  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  3 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    67236  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  2 snd
snd_page_alloc         17032  2 snd_intel8x0,snd_pcm
me@me-desktop:~$ 
<<<<<<<<<<<<<,

Is it supposed to work yet?

Thanks
m

---

### Post by Ulysses361 on 2009-10-30
No, it is not supposed to work yet. I am first trying to gather enough info. 

The instructions state "use the arrow keys to select " UPLOAD / SHARE " and then hit <enter> to make sure the script actually runs."

So select UPLOAD / SHARE using the arrow keys and then hit <enter> and send us the pastebin URL.

The info you gave "Your ALSA information is in /tmp/alsa-info.txt.pUyrnKRivA" is not a URL, so we cannot see the ALSA info....

Thanks,

Mark

---

### Post by mrmhead on 2009-10-30
So it's actually answer "y" to the Upload question:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>
-desktop:~$ bash alsa-info.sh --pastebin
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
ALSA Information Script v 0.4.58
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'alsa-info.sh --help' for command line options.

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
Automatically upload ALSA information to pastebin? [y/N] : y
Uploading information to [www.pastebin.ca](www.pastebin.ca) ...  Done!

Your ALSA information is located at [http://pastebin.ca/1649863](http://pastebin.ca/1649863)

Please inform the person helping you.

<<<<<<<<<<<<<<<<

Is that what you are looking for?

Thanks for the help
m

---

### Post by Ulysses361 on 2009-10-31
@mrmhead: there are at least 2 issues with your sound configuration:

First one is this:

# Sound Servers on this system
# ----------------------------
#  
# No sound servers found.

This means both the ESD and pulseaudio sound servers are not installed.

The output should normally look like this:

# Sound Servers on this system
# ----------------------------
#  
# Pulseaudio:
#      Installed - Yes (/usr/bin/pulseaudio)
#      Running - Yes
#  
# ESound Daemon:
#      Installed - Yes (/usr/bin/esd)
#      Running - No


Second issue is with the alsamixer configuration:

Output shows the following:

# Simple mixer control 'PCM',0
#  Capabilities: pvolume pswitch pswitch-joined
#  Playback channels: Front Left - Front Right
#  Limits: Playback 0 - 31
#  Mono:
#  Front Left: Playback 0 [0%] [-34.50dB] [off]
#  Front Right: Playback 0 [0%] [-34.50dB] [off]

So your PCM volume channel is set to 0% and muted. Please unmute and increase to 77% volume.

Once you have fixed the PCM issue, I recommend executing the following procedure to make sure pulseaudio is removed and replaced by ESD:

[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)

After that, reboot and retest sound.

If sound is still not working (play a few MP3's and video's to be sure), then please resend us output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by mrmhead on 2009-10-31
Thanks!
Not sure what did it:
The instructions aren't quite right - Maybe because of Xubuntu? - I don't have Preferences under System.  I still haven't found that Devices/Sound dialog box.  There is something similar in Mixer ... ?

Under MuliMedia is aumix which is an ascii-type "display" in terminal.  I didn't give it a close look before, but this time I did notice PCM was set to 0.  I turned it up.

I also ran the command lines and got back that pulseaudio and esound were not installed (though, you knew that)

I wen through synaptic to uninstall and reinstall esound and its related components, and then it worked!

And my video looks better too - not sure if it's related.

Or maybe because it heard me fire up my other machine, ready to downloand 9.10 ;)

Oh - there were auto-updates downloaded too (i don't think they were related)

Thanks Again!!
m

---


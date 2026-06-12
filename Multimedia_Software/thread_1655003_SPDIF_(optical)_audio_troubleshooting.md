---
title: "S/PDIF (optical) audio troubleshooting"
date: 2010-12-29
forum: Multimedia Software
---

### Post by xubuntu84 on 2010-12-29
I know that this topic has been covered multiple times, but after a few days of going through all the troubleshooting efforts available via these forums, I am still without sound.

If anyone could please help me out, it would be much appreciated, as it is the last step of getting my media center up and running.

My setup:
Intel DP55KG motherboard with integrated sound
  -HDA Intel Realtek 889
This is going via optical cable to a Sony A/V Receiver
I can see a red light at the end of the cable that connects to the receiver, so I know that the board is atleast supplying power to the optical port.

Output of aplay -l:
```
benmctee@ubuntu-server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Applicable output of lspci -v:
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Intel Corporation Device 0031
	Flags: bus master, fast devsel, latency 0, IRQ 49
	Memory at f6320000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
......
01:00.1 Audio device: nVidia Corporation Device 0be9 (rev a1)
	Subsystem: eVga.com. Corp. Device 1450
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f6000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```
The nVidia device is my graphics card that has an HDMI out, for some reason it recognizes this as an audio device.

I got nothing from sudo modprobe snd-hda-intel, so I "got the alsa drivers from a fresh kernel", per the sticky:
```
benmctee@ubuntu-server:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  alsa-base* alsa-utils* linux-sound-base*
0 upgraded, 0 newly installed, 3 to remove and 2 not upgraded.
After this operation, 2,712kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 156956 files and directories currently installed.)
Removing alsa-base ...
Purging configuration files for alsa-base ...
Removing alsa-utils ...
Purging configuration files for alsa-utils ...
Removing linux-sound-base ...
Purging configuration files for linux-sound-base ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...

...

benmctee@ubuntu-server:~$ sudo apt-get install linux-sound-base alsa-base alsa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  alsa-base alsa-utils linux-sound-base
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/1,457kB of archives.
After this operation, 2,712kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package linux-sound-base.
(Reading database ... 156845 files and directories currently installed.)
Unpacking linux-sound-base (from .../linux-sound-base_1.0.23+dfsg-1ubuntu4_all.deb) ...
Selecting previously deselected package alsa-base.
Unpacking alsa-base (from .../alsa-base_1.0.23+dfsg-1ubuntu4_all.deb) ...
Selecting previously deselected package alsa-utils.
Unpacking alsa-utils (from .../alsa-utils_1.0.23-2ubuntu3.4_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up linux-sound-base (1.0.23+dfsg-1ubuntu4) ...
Setting up alsa-base (1.0.23+dfsg-1ubuntu4) ...
Setting up alsa-utils (1.0.23-2ubuntu3.4) ...

```

When running , I got the following errors:
```
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                     &#9474;                  from /usr/src/modules/alsa-driver/include/adriver.h:25,     
                     &#9474;                  from /usr/src/modules/alsa-driver/acore/hwdep.c:1:          
                     &#9474; /usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
                     &#9474; "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
                     &#9474; ./include/generated/autoconf.h:2099: note: this is the location of the       
                     &#9474; previous definition                                                          
                     &#9474; In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                     &#9474;                  from /usr/src/modules/alsa-driver/include/adriver.h:25,     
                     &#9474;                  from /usr/src/modules/alsa-driver/acore/hwdep.c:1:          
                     &#9474; /usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
                     &#9474; "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
                     &#9474; ./include/generated/autoconf.h:2099: note: this is the location of the       
                     &#9474; previous definition                                                          
                     &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/memory_wrapper.o 
In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                     &#9474;                  from                                                        
                     &#9474; /usr/src/modules/alsa-driver/include/alsa-autoconf.h:4,                      
                     &#9474;                  from                                                        
                     &#9474; /usr/src/modules/alsa-driver/acore/memory_wrapper.c:1:                       
                     &#9474; /usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
                     &#9474; "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
                     &#9474; ./include/generated/autoconf.h:2099: note: this is the location of the       
                     &#9474; previous definition                                                          
                     &#9474;   CC [M]  /usr/src/modules/alsa-driver/acore/memalloc.o                      
                     &#9474; In file included from /usr/src/modules/alsa-driver/include/config.h:6,       
                     &#9474;                  from                                                        
                     &#9474; /usr/src/modules/alsa-driver/include/alsa-autoconf.h:4,                      
                     &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:1,     
                     &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1: 
/usr/src/modules/alsa-driver/include/config1.h:175: warning:                 
                     &#9474; "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined                                   
                     &#9474; ./include/generated/autoconf.h:2099: note: this is the location of the       
                     &#9474; previous definition                                                          
                     &#9474; In file included from include/linux/pci.h:58,                                
                     &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,    
                     &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:       
                     &#9474; /usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error:         
                     &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory    
                     &#9474; compilation terminated.                                                      
                     &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1         
                     &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                    
                     &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                  
                     &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'        
                     &#9474; make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'                    
                     &#9474; make[1]: *** [build-stamp] Error 2                                           
                     &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                    
                     &#9474; make: *** [kdist_image] Error 2
```

Now using sudo modprobe snd-hda-intel OR sudo modprobe snd-hda-codec-realtek gives me nothing in return.

I'm going to continue troubleshooting tonight, but if anyone reads this thread and knows exactly what the problem is, please let me know.

---

### Post by xubuntu84 on 2010-12-29
Update:
I have since installed a Creative Soundblaster SB0880 with SPDIF out, with the same problems.  I opened my case and can see there is an HD audio plug on the motherboard:
XXX X
XXXXX
and an S/PDIF out:
XX X

I am able to get sound when I plug the headphones into the jack on both the motherboard and the sound card.  However, I can't seem to get audio out of the optical port.

Previously (prior to installing the sound card), I had the cable from my front panel running to the motherboard on the HD audio pins.  Since installing that card, I have unplugged that, and the Soundblaster is plugged into the PCIE slot next to the graphics card.

---

### Post by lidex on 2010-12-29
Have a look here:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
[http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo](http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo)

---

### Post by xubuntu84 on 2011-01-01
> **lidex said:**
> Have a look here:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)
[http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo](http://www.knoppmythwiki.org/index.php?page=DigitalAudioHowTo)

Thanks for the response.

Another update, I bought a Soundblaster xFI card with optical ports.  So my updated aplay -l:
```
benmctee@ubuntu-server:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 1: ctxfi [Surround]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 2: ctxfi [Center/LFE]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 3: ctxfi [Side]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: XFi [Creative X-Fi], device 4: ctxfi [IEC958 Non-audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

One weird thing is that Card 0 Device 4 says that it is non-audio.  Not sure why that is.

I followed the instructions from the first link.  When trying to play a file over the sound card, I get:
```
benmctee@ubuntu-server:~$ aplay -D hw:0,4 Music/test.wav
Playing WAVE 'Music/test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
aplay: set_params:1116: Unable to install hw params:
ACCESS:  RW_INTERLEAVED
FORMAT:  S16_LE
SUBFORMAT:  STD
SAMPLE_BITS: 16
FRAME_BITS: 32
CHANNELS: 2
RATE: 44100
PERIOD_TIME: (125011 125012)
PERIOD_SIZE: 5513
PERIOD_BYTES: 22052
PERIODS: 4
BUFFER_TIME: (500045 500046)
BUFFER_SIZE: 22052
BUFFER_BYTES: 88208
TICK_TIME: 0
```

When trying to play it on the motherboard it looks like it is playing, but I get no sound out:
```
benmctee@ubuntu-server:~$ aplay -D hw:1,1 Music/test.wav
Playing WAVE 'Music/test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
^CAborted by signal Interrupt...
```

So I followed the dmix plugin, and attempted to put the appropriate settings in .asoundrc, but it still will not work:
```
benmctee@ubuntu-server:~$ cat .asoundrc
pcm.ossmix {
    type dmix
    ipc_key 1024
    slave {
    pcm "hw:0,4"
        period_time 0
        period_size 1024
        buffer_size 4096 # buffer size < 6653, but pow(x, 2)
        rate 44100 # we want to play CDs only
        format S32_LE # needed in alsa 1.0.10 for some reason
    }
    bindings {
        0 0
        1 1
    }
}
# Everything shall be dmixed, so redefine "default":
pcm.!default {
    type plug
    slave.pcm "ossmix"
}
# OSS via aoss should d(mix)stroyed:
pcm.dsp0 {
    type plug
    slave.pcm "ossmix"
}
ctl.mixer0 {
    type hw
    card 0
}
```

It seems like aplay is not reading the .asoundrc file when attempting to play test.wav because the buffer setting is not 4096.

Anything obviously wrong in my .asoundrc file?  How can I get it to read it when playing?

---

### Post by lidex on 2011-01-02
When you installed the new card did you wipe all your previous tweaks? Also have you tried disabling onboard audio in bios?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by xubuntu84 on 2011-01-04
> **lidex said:**
> When you installed the new card did you wipe all your previous tweaks? Also have you tried disabling onboard audio in bios?

I completely wiped alsa and pulseaudio, then reinstalled alsa, thinking pulse might be the problem.

> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Wow, that is an impressive script.  My output:
[http://www.alsa-project.org/db/?f=50fb8aa4122d419665f88f2c9a85fd9650a4f3a9]("http://www.alsa-project.org/db/?f=50fb8aa4122d419665f88f2c9a85fd9650a4f3a9")

---

### Post by lidex on 2011-01-04
dmesg is showing:
```
[ 6507.148529] ctxfi: PLL initialization failed!!!
[ 6507.148533] ctxfi: Preparing pcm playback failed!!!
```
I've not seen that before so not sure what it means. Let's try this. Rename your ~/.asoundrc file, reboot and post these outputs:
```
aplay -l
aplay -L 
```

---

### Post by mischi3f on 2011-05-22
Hello,

I am having the exact same issue with my sound. Currently sound works however I get time where the sound randomly stops for a short second and then resumes if I am watching a video or something. I also have the issue when my system boots up cleanly it will freeze on a purple screen until I hard reset and restart. I did not think this had any correlation to the sound until I did about 30 - 45 mins of reading through these and other forums. 

I get the exact same error in my "dmesg." I have the sound running fiber to my home theater system. I have onboard sound and a Creative Labs Sound Blaster XFi Titanium both running and I have tried each one seperatly as well as both together. I get the same results. Unfortunately I am only as good as linux as google searches allow me to be at the moment lol. Any help would be greatly appreciated. Thanks!

---


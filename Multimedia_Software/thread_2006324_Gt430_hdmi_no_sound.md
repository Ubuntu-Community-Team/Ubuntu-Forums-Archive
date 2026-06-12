---
title: "Gt430 hdmi no sound"
date: 2012-06-19
forum: Multimedia Software
---

### Post by linuxhtpc on 2012-06-19
Ubuntu 12.04 64-bit.

**PROBLEM: I am getting no sound of any kind  over HDMI to a Pioneer SC-57 Receiver with 5.1 speakers connected.**

Video works great and it is passing 1920x1080 through the SC-57 into a Panasonic PT-AE7000 projector onto a big screen.

This is the system:

Intel Q9450
ASUS Rampage
8GB RAM
NVIDIA GT430

[B]I have installed the proprietary NVIDIA driver but under system details it says "Graphics unknown"

and I get nothing from sound testing.[/B]


When I type "aplay -l" in the terminal this is the result:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[B]What is incredibly ironic is that I had a RADEON 6970 in this machine and had the common fglrx tearing/skipping audio sync issues.

So I Googled what is the best possible HTPC linux HDMI card - multiple posts saying - NVIDIA GT430 - and now no sound in Ubuntu, xbmcbuntu or LinuxMint!!

_I am a noob and need it spelled out._

Please help - I am trying ever so hard to make the switch to Linux!!  This is all foreign and I have stuck with it but I am getting very frustrated at this point - two video cards, 3 distros and cannot get working simple 1080p with sound playback!
[/B]

---

### Post by linuxhtpc on 2012-06-19
I have tried the "generic" fixes and read tons of threads on hdmi.

So many people said get GT430 if I wanted hassle free HTPC and that is not happening....

I have been hassling with the terminal for three days trying things from other threads

Can someone please help me get this working? (24+ hour bump due to no response and no PMs).

---

### Post by BicyclerBoy on 2012-06-19
Have you disabled the on-board mobo sound card ? Just it is odd that the only audio device is the GT430...

You could find/run the alsa debugging script..

This is the HDMI audio bible..
[http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#](http://http.download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#)

speaker-test -l 4 -c 2 -r 48000 -D hw:0,9
speaker-test -l 4 -c 2 -r 48000 -D hw:0,8
speaker-test -l 4 -c 2 -r 48000 -D hw:0,7
speaker-test -l 4 -c 2 -r 48000 -D hw:0,3

The default alsa shipping in Ubuntu 12.04 should find all your HDMI audio sub-devices..you need to select the one that works.

You can not use the system display tool with AMD/nVidia proprietary drivers.
The std distro sound control tool is terrible..install "pavucontrol"
sudo apt-get install pavucontrol

Problem could be reported ELD is incorrect..i.e. reporting projector & not HT amp.
dmesg | grep HDA
cat /proc/asound/card0/eld#0.3

---

### Post by linuxhtpc on 2012-06-21
thank you for your help!

I am reading over the NVIDIA HDMI guide you linked.

I also installed pavucontrol.

when i run the commands suggested I get:

Rampage-Formula:~$ dmesg | grep HDA
[   12.668096] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input5
[   12.669560] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input6
[   12.669615] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input7
[   12.669669] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input8

-and-

-Rampage-Formula:~$ cat /proc/asound/card0/eld#0.3
cat: /proc/asound/card0/eld#0.3: No such file or directory


any other ideas - still not working - I will read the HDMI guide and update.

Thank you again for responding, I appreciate it.  Anyone have any other thoughts for first time Linux user?

---

### Post by linuxhtpc on 2012-06-21
some more testing: I tried 0,3 - 0,7 - 0,8 - 0,9

this is the output of each one can anyone comment?




Rampage-Formula:~# speaker-test -l 4 -c 2 -r 48000 -D hw:0,7

speaker-test 1.0.25

Playback device is hw:0,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

---

### Post by linuxhtpc on 2012-06-21
more data from terminal:

-Rampage-Formula:~# cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe7fc000 irq 17

lspci gives:

01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)

[B]interestingly recognizes the Pioneer SC-57 Receiver modes:

[/B]Rampage-Formula:~# cat /proc/asound/card0/eld#3.0
monitor_present        1
eld_valid        1
monitor_name        SC-57
       
connection_type        HDMI
eld_version        [0x2] CEA-861D or below
edid_version        [0x3] CEA-861-B, C or D
manufacture_id        0x2f41
product_id        0x0
port_id            0x20000
support_hdcp        0
support_ai        0
audio_sync_delay    0
speakers        [0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count        8
sad0_coding_type    [0x1] LPCM
sad0_channels        2
sad0_rates        [0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad0_bits        [0xe0000] 16 20 24
sad1_coding_type    [0x1] LPCM
sad1_channels        8
sad1_rates        [0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad1_bits        [0xe0000] 16 20 24
sad2_coding_type    [0x2] AC-3
sad2_channels        6
sad2_rates        [0xe0] 32000 44100 48000
sad2_max_bitrate    640000
sad3_coding_type    [0x7] DTS
sad3_channels        7
sad3_rates        [0x6c0] 44100 48000 88200 96000
sad3_max_bitrate    1536000
sad4_coding_type    [0x9] DSD (One Bit Audio)
sad4_channels        6
sad4_rates        [0x40] 44100
sad5_coding_type    [0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad5_channels        8
sad5_rates        [0xc0] 44100 48000
sad6_coding_type    [0xb] DTS-HD
sad6_channels        8
sad6_rates        [0x1ec0] 44100 48000 88200 96000 176400 192000
sad7_coding_type    [0xc] MLP (Dolby TrueHD)
sad7_channels        8
sad7_rates        [0x1ec0] 44100 48000 88200 96000 176400 192000

---

### Post by linuxhtpc on 2012-06-21
**tried procedure below it still does not work **- any expert care to take a crack at this because I am close to giving up on Linux as unstable...

> Edit or create a /etc/modprobe.d/sound.conf file. Type the following in a terminal:

gksudo gedit /etc/modprobe.d/sound.conf (add the proper options snd-hda-intel probe_mask line to this file)

options  snd-hda-intel probe_mask=0x108 (Save the file and update the initramfs  to make sure this change will be used upon reboot.)

sudo update-initramfs -u

exit terminal reboot or just sudo reboot in terminal

---

### Post by BicyclerBoy on 2012-06-21
Sorry made a typo with the eld#0.3 3.0 file name..

Don't use a probe_mask & certainly not one that is an incorrect value (according to the hdmi-bible).

The later alsa/pulseaudio (ubu 12.04) should not need the probe_mask to work out-of-the-box..

Did you try?
speaker-test -l 4 -c 2 -r 48000 -D hw:0,9

Check your "user" is a member of the audio group..

Your "dmesg | grep HDA" did not show any hot-plug events..was the AVR/HT-amp plugged in & turned on?

The eld file looks okay..

Use pavucontrol & select the right most tab configuration, select the fourth hdmi device listed..(I think).


HDMI audio has worked in linux for some  years but there have been lots of changes/improvements/regressions.

---

### Post by linuxhtpc on 2012-06-25
This is what I am getting:

Rampage-Formula ~ # speaker-test -l 4 -c 2 -r 48000 -D hw:0,9

speaker-test 1.0.25

Playback device is hw:0,9
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

I think this is key to the problem:
[B]Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

I am doing this as root and completely baffled at this point.

I can get HDMI sound on the same computer by switching an ATI card I have but then I get all the tearing issues that come with ATI....
[/B]

---

### Post by BicyclerBoy on 2012-06-26
AFAIK
You should not be running anything as root user..
AFAIK
The sudoers file/list can be used to allow certain scripts/processes to do stuff (like shutdown etc).

---

### Post by meathdeath on 2012-06-26
This is very odd as i have the same video card and have no problems what so ever with the sound.

---

### Post by efflandt on 2012-06-27
I don't know if anything changed in recent Ubuntu versions to make this more automatic, because I normally use an analog 2.1 speaker system with DVI to HDMI cable to my HDTV (as monitor).

There was a rather long thread figuring out nvidia HDMI audio in Maverick beginning with GeForce 210 through a GT 220 I had, then GT 430.

Full thread is [http://ubuntuforums.org/showthread.php?t=1317408&highlight=gt+430+sound](http://ubuntuforums.org/showthread.php?t=1317408&highlight=gt+430+sound)

But the part where I figured out the GT 430 [http://ubuntuforums.org/showpost.php?p=10273109&postcount=40](http://ubuntuforums.org/showpost.php?p=10273109&postcount=40)

Or this is another thread I answered at the time that says solved: [http://ubuntuforums.org/showpost.php?p=10367062&postcount=5](http://ubuntuforums.org/showpost.php?p=10367062&postcount=5)

But like I said, that was all back in Maverick, so not sure if things have changed for enabling nvidia HDMI sound now.

My GT 430 made by a Chinese company (Galaxie) started freezing after its 1 year warranty expired.  So now I have a faster EVGA card with 3 year warranty.

---

### Post by dorkboy on 2012-07-19
I had the same problem in Ubuntu 11.10 with the Nvidia GT430. 

First I had to disable the on-board sound device on my motherboard in the bios. 

Then I ran 'system settings' from the dash and chose 'sound', hit the 'hardware' tab and at the bottom kept trying different profile selections and hitting the test speaker button until I heard sound. That worked for me. 

Hope this helps.

---


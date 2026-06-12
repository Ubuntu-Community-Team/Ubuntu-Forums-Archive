---
title: "MPD on Ubuntu Server 12.10 with USB Audio Fails to start"
date: 2013-04-16
forum: Multimedia Software
---

### Post by harshdev on 2013-04-16
Hi All I am trying to install mpd on ubuntu server 12.10 with USB audio but mpd is unable to start because of following issue:

[B]mixer: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM

[/B]aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Device
    Generic USB Audio Device, USB Audio
    Default Audio Device
front:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    Front speakers
surround40:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    Direct sample mixing device
dsnoop:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    Direct sample snooping device
hw:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Device,DEV=0
    Generic USB Audio Device, USB Audio
    Hardware device with all software conversions

----------------

lsusb:
Bus 002 Device 002: ID 1bcf:05ce Sunplus Innovation Technology Inc. 
Bus 003 Device 002: ID 0d8c:000e C-Media Electronics, Inc. Audio Adapter (Planet UP-100, Genius G-Talk)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


-----------------

Audio Output in /etc/mpd.conf
audio_output {
    type        "alsa"
    name        "My ALSA Device"
    device        "plughw:CARD=Device,Dev=0"    # optional
    format        "44100:16:2"    # optional
    #mixer_device    "Device"    # optional
    #mixer_control    "PCM"        # optional
    #mixer_index    "0"        # optional
}


----------------

Verbose log for mpd:

Apr 16 07:55 : state_file: Loading state file /var/lib/mpd/state
Apr 16 07:55 : inotify: initializing inotify
Apr 16 07:55 : inotify: watching music directory
Apr 16 07:55 : client: [0] opened from 192.168.11.24:55750
Apr 16 07:55 : client: [0] process command "commands"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "notcommands"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "outputs"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "stats"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "lsinfo "/""
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "outputs"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : mixer: Failed to read mixer for 'My ALSA Device': no such mixer control: PCM
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:55 : client: [0] process command "plchanges "0""
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:55 : client: [0] process command "status"
Apr 16 07:55 : client: [0] command returned 0
Apr 16 07:55 : client: [0] process command "idle"
Apr 16 07:55 : client: [0] command returned 1
Apr 16 07:56 : state_file: Saving state file /var/lib/mpd/state
Apr 16 07:56 : client: [0] closed
Apr 16 07:56 : listen: listen_global_finish called
Apr 16 07:56 : db_finish took 0.000000 seconds
Apr 16 07:56 : state_file: Loading state file /var/lib/mpd/state
Apr 16 07:56 : inotify: initializing inotify
Apr 16 07:56 : inotify: watching music directory

---

### Post by tgalati4 on 2013-04-16
Plug the USB sound device into a desktop linux computer and bring up the sound control panel and look for "PCM" slider control.  It's possible that your device driver does not have one, although "dsnoop"--digital snoop looks like it would be similar to PCM.

Look in your /dev/snd directory for PCM devices (files):

tgalati4@Mint14-Extensa /dev/snd $ ls
by-path  controlC0  hwC0D0  hwC0D1  pcmC0D0c  pcmC0D0p  pcmC0D2c  seq  timer
tgalati4@Mint14-Extensa /dev/snd $ ls -la
total 0
drwxr-xr-x   3 root root      220 Apr  1 17:11 .
drwxr-xr-x  16 root root     4280 Apr 16 08:08 ..
drwxr-xr-x   2 root root       60 Apr  1 17:11 by-path
crw-rw---T+  1 root audio 116,  7 Apr  1 17:11 controlC0
crw-rw---T+  1 root audio 116,  6 Apr  1 17:11 hwC0D0
crw-rw---T+  1 root audio 116,  5 Apr  1 17:11 hwC0D1
crw-rw---T+  1 root audio 116,  4 Apr  1 17:12 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 Apr 15 20:06 pcmC0D0p
crw-rw---T+  1 root audio 116,  2 Apr  1 17:11 pcmC0D2c
crw-rw---T+  1 root audio 116,  1 Apr  1 17:11 seq

Mine is for on-board, Intel sound on an Acer laptop.  If you are missing the "pcm*" devices then ALSA can't control it and mpd requires that control.

There is a switch to alter ALSA behavior on this page:  [http://www.musicpd.org/doc/user/ch05s05.html#idp5650208](http://www.musicpd.org/doc/user/ch05s05.html#idp5650208)

---

### Post by harshdev on 2013-04-16
this is how ls -la /dev/snd looks like | also can you please help me am a new bie so unsure what i am supposed to do.

drwxr-xr-x  4 root root      180 Apr 16 21:20 .
drwxr-xr-x 16 root root     4200 Apr 16 21:20 ..
drwxr-xr-x  2 root root       60 Apr 16 21:20 by-id
drwxr-xr-x  2 root root       60 Apr 16 21:20 by-path
crw-rw---T  1 root audio 116,  4 Apr 16 21:20 controlC0
crw-rw---T  1 root audio 116,  3 Apr 16 21:20 pcmC0D0c
crw-rw---T  1 root audio 116,  2 Apr 16 21:20 pcmC0D0p
crw-rw---T  1 root audio 116,  1 Apr 16 21:20 seq
crw-rw---T  1 root audio 116, 33 Apr 16 21:20 timer

---

### Post by tgalati4 on 2013-04-16
Try putting *dsd_usb yes* in the *alsa* section of mpd.conf.  Then try restarting mpd.

---

### Post by harshdev on 2013-04-17
Gives me following error

**Apr 17 07:08 : config: option 'dsd_usb' on line 208 was not recognized**

---

### Post by tgalati4 on 2013-04-17
Did you follow the instructions according to:  [http://www.musicpd.org/doc/user/ch03s06.html](http://www.musicpd.org/doc/user/ch03s06.html)

Post the output of your /etc/mpd.conf.

---


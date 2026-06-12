---
title: "Canonocal update to 22.10 of 5 January 23 killed the sound on my laptop"
date: 2023-01-07
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-01-07
Mandatory update of 22.10 that occurred on 5 JAN 2023 killed the sound on my Dell Precision 7720 laptop.  One of the previous updates had gotten the sound working.  I am traveling this week, so the only way to do applications that require sound is to reboot said laptop into win 11.

IS THIS REALLY WHAT THOSE AT CANONICAL WANT TO HAPPEN?

John

---

### Post by ian-weisser on 2023-01-07
My 22.10 system had no "mandatory" update on that date, so it's unclear which package(s) you might be referring to.

You have been around long enough to know how to read your apt logs.

---

### Post by cigtoxdoc on 2023-01-07
Thank you for your reply.

Please let me know correct format (odt, pdf, ?) for posting output of $ cat /var/log/syslog* | grep -i pulse .  The text, "Can't find xdg-portal" appears in several lines of the output.

John

---

### Post by ajgreeny on 2023-01-07
Run command ```
grep -i " upgrade " /var/log/dpkg.log
``` and it will list all packages that were upgraded recently in date order so you should be able to see all those of 5 January 2023 which may give some clues as to what the problem might be.

---

### Post by cigtoxdoc on 2023-01-07
Thank you for your reply.

Please let me know correct format (odt, pdf, ?) for posting output of $ cat /var/log/syslog* | grep -i pulse .  The text, "Can't find xdg-portal" appears in several lines of the output.

John

---

### Post by cigtoxdoc on 2023-01-07
Thank you.  Output of grep -i " upgrade " /var/log/dpkg.log

```
<pre><font color="#26A269"><b>john@john-Precision-7720</b></font>:<font color="#12488B"><b>~</b></font>$ grep -i &quot; upgrade &quot; /var/log/dpkg.log
2023-01-05 10:35:48<font color="#C01C28"><b> upgrade </b></font>firefox:amd64 108.0.1+build1-0ubuntu0.22.10.1~mt1 108.0.2+build1-0ubuntu0.22.10.1~mt1
2023-01-05 10:35:49<font color="#C01C28"><b> upgrade </b></font>libksba8:amd64 1.6.0-3ubuntu1 1.6.0-3ubuntu1.1
2023-01-05 10:35:49<font color="#C01C28"><b> upgrade </b></font>libnautilus-extension4:amd64 1:43.0-1ubuntu1 1:43.0-1ubuntu2.1
2023-01-05 10:35:49<font color="#C01C28"><b> upgrade </b></font>nautilus-data:all 1:43.0-1ubuntu1 1:43.0-1ubuntu2.1
2023-01-06 06:03:22<font color="#C01C28"><b> upgrade </b></font>libcurl3-gnutls:amd64 7.85.0-1ubuntu0.1 7.85.0-1ubuntu0.2
2023-01-06 06:03:22<font color="#C01C28"><b> upgrade </b></font>libcurl4:amd64 7.85.0-1ubuntu0.1 7.85.0-1ubuntu0.2
2023-01-06 08:37:49<font color="#C01C28"><b> upgrade </b></font>gnome-remote-desktop:amd64 43.0-0ubuntu1 43.2-0ubuntu1
2023-01-06 08:37:53<font color="#C01C28"><b> upgrade </b></font>linux-generic:amd64 5.19.0.26.23 5.19.0.28.25
2023-01-06 08:37:53<font color="#C01C28"><b> upgrade </b></font>linux-image-generic:amd64 5.19.0.26.23 5.19.0.28.25
2023-01-06 08:37:57<font color="#C01C28"><b> upgrade </b></font>linux-headers-generic:amd64 5.19.0.26.23 5.19.0.28.25
2023-01-06 08:37:58<font color="#C01C28"><b> upgrade </b></font>linux-generic-hwe-22.04:amd64 5.19.0.26.23 5.19.0.28.25
2023-01-06 08:37:58<font color="#C01C28"><b> upgrade </b></font>linux-image-generic-hwe-22.04:amd64 5.19.0.26.23 5.19.0.28.25
2023-01-06 08:37:58<font color="#C01C28"><b> upgrade </b></font>linux-headers-generic-hwe-22.04:amd64 5.19.0.26.23 5.19.0.28.25
2023-01-06 08:37:58<font color="#C01C28"><b> upgrade </b></font>linux-libc-dev:amd64 5.19.0-26.27 5.19.0-28.29
<font color="#26A269"><b>john@john-Precision-7720</b></font>:<font color="#12488B"><b>~</b></font>$ 
</pre>
```

---

### Post by #&amp;thj^% on 2023-01-07
Do you remember if it removed kernel 5.15?
Also show:
```
ps -e | grep wireplumber
### Mine below
   2124 ?        00:00:00 wireplumber
```
Also show 
```
inxi -A
```

---

### Post by ajgreeny on 2023-01-07
I don't think the 4 packages updated on Jan 5 would have had any effect on sound so I'm afraid you need to look for other answers
```
2023-01-05 10:35:48<font color="#C01C28"><b> upgrade </b></font>firefox:amd64 108.0.1+build1-0ubuntu0.22.10.1~mt1 108.0.2+build1-0ubuntu0.22.10.1~mt1
2023-01-05 10:35:49<font color="#C01C28"><b> upgrade </b></font>libksba8:amd64 1.6.0-3ubuntu1 1.6.0-3ubuntu1.1
2023-01-05 10:35:49<font color="#C01C28"><b> upgrade </b></font>libnautilus-extension4:amd64 1:43.0-1ubuntu1 1:43.0-1ubuntu2.1
2023-01-05 10:35:49<font color="#C01C28"><b> upgrade </b></font>nautilus-data:all 1:43.0-1ubuntu1 1:43.0-1ubuntu2.1
```

---

### Post by cigtoxdoc on 2023-01-08
Thank you for your reply.

Please let me know correct format (odt, pdf, ?) for posting output of $ cat /var/log/syslog* | grep -i pulse .  The text, "Can't find xdg-portal" appears in several lines of the output.

John

---

### Post by cigtoxdoc on 2023-01-08
In reply to 1fallen:

john@john-Precision-7720:~$ ps -e | grep wireplumber
### Mine below
   2124 ?        00:00:00 wireplumber
   1064 ?        00:00:01 wireplumber
2124: command not found
john@john-Precision-7720:~$ inxi -A
Audio:
  Device-1: Intel CM238 HD Audio driver: snd_hda_intel
  Device-2: NVIDIA GP104 High Definition Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.19.0-28-generic running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes
john@john-Precision-7720:~$

---

### Post by QIII on 2023-01-08
@cigtoxdoc

The best way to communicate lengthy terminal results is to use [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) and post the url back.

---

### Post by #&amp;thj^% on 2023-01-08
> **QIII said:**
> @cigtoxdoc

The best way to communicate lengthy terminal results is to use [https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/) and post the url back.
+1 Thanks for that, I'm surprised more users don't quite understand, and this is not directed @cigtoxdoc personally.
> **cigtoxdoc said:**
> In reply to 1fallen:

john@john-Precision-7720:~$ ps -e | grep wireplumber
### Mine below
   2124 ?        00:00:00 wireplumber
   1064 ?        00:00:01 wireplumber
2124: command not found
john@john-Precision-7720:~$ inxi -A
Audio:
  Device-1: Intel CM238 HD Audio driver: snd_hda_intel
  Device-2: NVIDIA GP104 High Definition Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.19.0-28-generic running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes
john@john-Precision-7720:~$

cigtoxdoc do you have the nvidia driver installed?
Also please update and upgrade today and check sound again please.....I know the frustration you may have as of now....but cooler heads prevail. ;)

---

### Post by cigtoxdoc on 2023-01-12
I am not an IT professional, but I want to wrap this up with some findings.  Checking the sound after a warm or cold boot and logging into Ubuntu 22.10 generally, but not always results in no sound.  Start-up apps include Nemp, Numlock, SpiderOakONE, SSH Key Agent, and xapp-sn-watcher.  Sometimes starting up Firefox (non-snap) and going to a website that has streaming internet radio (wcpe.org, wqxr.org) will start the sound.  Waiting four or five minutes after logging into Ubuntu sometimes results in success, but only if Firefox is loaded and a streaming Internet radio station is running.

Sound with a USB headset seems to work all the time.  Booting into Win 11 instead of Ubuntu 22.10 always give sound.

If there are diagnostic routines I should run, please provide the command lines I need to run.

Thank you,

John

---

### Post by #&amp;thj^% on 2023-01-14
As of Ubuntu 22.10 it states that; Pipewire is introduced as the default audio server.
Some folks have better luck with the old pulseaudio:
Suggested try out:
```
sudo apt remove pipewire
```
Now check if  enabled:
```
systemctl --user --now enable pulseaudio.service pulseaudio.socket
```
If already enabled,  start it, to start pulse audio
```

systemctl --user start pulseaudio.service
systemctl --user start pulseaudio.socket
```
If you try this please keep us updated here,

---

### Post by cigtoxdoc on 2023-01-15
Thank you.  I executed the commands you suggested.  Result was no sound whatsoever.  I then reversed the commands reinstalling pipewire.  Again, no sound.  Synaptic shows pipewire was reinstalled.  Do I need to run other commands to get pipewire going?

John

---

### Post by cigtoxdoc on 2023-01-18
Is anyone else using 22.10 with non-snap version of Firefox?  Everything was dead on sound until I opened a new window ([https://www.firstcoastnews.com/](https://www.firstcoastnews.com/)) and clicked on a weather forecast with an announcer.  Then sound (built-in audio) came on.  Also, sound test under Sound on system settings started working.

John

---

### Post by #&amp;thj^% on 2023-01-18
I'm using strictly Devel Repos, so yes I'm using the newest of everything..(testing) 
Sounds about right, sound has been a real bugger to triage with 22.04 and up.
Thanks for the update. ;)

---

### Post by cigtoxdoc on 2023-01-18
Thank you.  What does the following mean?
<pre>$ pactl info
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 257
Tile Size: 65472
User Name: john
Host Name: john-Precision-7720
Server Name: PulseAudio (on PipeWire 0.3.58)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_1f.3.analog-stereo
Default Source: alsa_input.pci-0000_00_1f.3.analog-stereo
Cookie: 383b:2dc2

I got that command line from [https://wiki.archlinux.org/title/PipeWire#Usage](https://wiki.archlinux.org/title/PipeWire#Usage).

John

---

### Post by #&amp;thj^% on 2023-01-18
pactl info, reads the session manager used, and in this case your using "PipeWire"
The rest just shows pipewire settings used for your current session for your various sound slots.
Mine:
```
Server String: /run/user/1000/pulse/native
Library Protocol Version: 35
Server Protocol Version: 35
Is Local: yes
Client Index: 110
Tile Size: 65472
User Name: me
Host Name: kaisenlinux
Server Name: PulseAudio (on PipeWire 0.3.63)
Server Version: 15.0.0
Default Sample Specification: float32le 2ch 48000Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51
Default Source: alsa_input.pci-0000_06_00.6.pro-input-0
Cookie: fb6c:161c

```
You also can look at wireplumber, I'm not sure if you have it installed?
```
apt policy wireplumber
wireplumber:
  Installed: 0.4.13-1
  Candidate: 0.4.13-1
  Version table:
 *** 0.4.13-1 100
        100 /var/lib/dpkg/status


```
you will see the likes of:
```
 wpctl status
PipeWire 'pipewire-0' [0.3.63, me@kaisenlinux, cookie:4218164764]
 &#9492;&#9472; Clients:
        31. pipewire                            [0.3.63, me@kaisenlinux, pid:2424]
        32. WirePlumber                         [0.3.63, me@kaisenlinux, pid:2423]
        33. WirePlumber [export]                [0.3.63, me@kaisenlinux, pid:2423]
        76. xfce4-pulseaudio-plugin             [0.3.63, me@kaisenlinux, pid:2637]
        77. xdg-desktop-portal                  [0.3.63, me@kaisenlinux, pid:9109]
        78. Firefox                             [0.3.63, me@kaisenlinux, pid:9]
        79. Strawberry device finder            [0.3.63, me@kaisenlinux, pid:2]
        89. Strawberry                          [0.3.63, me@kaisenlinux, pid:2]
        94. wpctl                               [0.3.63, me@kaisenlinux, pid:646186]

Audio
 &#9500;&#9472; Devices:
 &#9474;      42. HDA NVidia                          [alsa]
 &#9474;      43. UOEOS Laptop Dock                   [alsa]
 &#9474;      44. Family 17h/19h HD Audio Controller  [alsa]
 &#9474;      45. Built-in Audio                      [alsa]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;      35. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  *   48. UOEOS Laptop Dock Analog Surround 5.1 [vol: 0.45]
 &#9474;      50. Built-in Audio Mono                 [vol: 0.40]
 &#9474;      71. HDA NVidia Digital Stereo (HDMI)    [vol: 0.40]
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   49. Family 17h/19h HD Audio Controller Pro [vol: 1.00]
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:
        86. Strawberry                                                  
             80. output_FL       > UOEOS Laptop Dock:playback_FL	[active]
             81. output_LFE      > UOEOS Laptop Dock:playback_LFE	[active]
             83. output_RL       > UOEOS Laptop Dock:playback_RL	[active]
             84. output_FC       > UOEOS Laptop Dock:playback_FC	[active]
             87. output_FR       > UOEOS Laptop Dock:playback_FR	[active]
             90. output_RR       > UOEOS Laptop Dock:playback_RR	[active]

Video
 &#9500;&#9472; Devices:
 &#9474;      40. Integrated Camera                   [v4l2]
 &#9474;      41. Integrated Camera                   [v4l2]
 &#9474;  
 &#9500;&#9472; Sinks:
 &#9474;  
 &#9500;&#9472; Sink endpoints:
 &#9474;  
 &#9500;&#9472; Sources:
 &#9474;  *   46. Integrated Camera (V4L2)           
 &#9474;  
 &#9500;&#9472; Source endpoints:
 &#9474;  
 &#9492;&#9472; Streams:

Settings
 &#9492;&#9472; Default Configured Node Names:
         0. Audio/Sink    alsa_output.usb-DisplayLink_UOEOS_Laptop_Dock_4307293310436-02.analog-surround-51
         1. Audio/Source  alsa_input.pci-0000_06_00.6.pro-input-0



```

One more mention I need to add is, There's no easy way to set the buffersize or sample rate when using flatpaks right now. So this issue is important.
You mentioned snap free firefox, so more of a heads up is all. (back pocket use)

---

### Post by cigtoxdoc on 2023-01-22
Today, same command gave:

john@john-Precision-7720:~$  ps -e | grep wireplumber
   1053 ?        00:00:00 wireplumber
udio:
  Device-1: Intel CM238 HD Audio driver: snd_hda_intel
  Device-2: NVIDIA GP104 High Definition Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.19.0-29-generic running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes
john@john-Precision-7720:~$ 

There is no sound this morning.  

Nothing on pc changed.

---

### Post by #&amp;thj^% on 2023-01-22
Can you test this for me:
```
systemctl --user restart pipewire.service
```
Now check sound.

---

### Post by cigtoxdoc on 2023-01-22
Thank you.  Ran command as you suggested.  Sound did not return.  John

---

### Post by #&amp;thj^% on 2023-01-22
I'm glad your here, one more please:
```
systemctl --user restart pipewire-pulse.service
```

---


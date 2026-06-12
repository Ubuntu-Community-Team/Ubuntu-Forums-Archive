---
title: "No sound in Ubuntu 11.04"
date: 2011-06-26
forum: Multimedia Software
---

### Post by fatteralbert on 2011-06-26
I get no sound. Not even the little signature tune you're suppose to get when you start up ubuntu. 

So I have looked at this guide, [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449). 

When I go 
```
aplay -l
```I get: 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I guess this means that the sound card is there. 

Then I tried the alsamixer just too make sure that the speakers was not muted. 
```
alsamixer
```The last thing I tried was adding my user name to the /etc/group. Before it was ```
audio:x:29:pulse
```, but now it says ```
audio:x:29:myusername
```My questions are two: is where some bullet proof way to test the sound card? Now I'm running some random mp3 which might have some fault in itself. 

The second question is, what must I do to get the sound to work?

---

### Post by lidex on 2011-06-26
Use the alsa-info-script to provide detailed information. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by fatteralbert on 2011-06-27
Maybe I did something wrong, but I can't see any link in the output. This was the information I got after running the script: 

```
--2011-06-27 09:49:47--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org]("http://www.alsa-project.org/")... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80]("http://www.alsa-project.org%7C77.48.224.243%7C/")... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh) [following]
--2011-06-27 09:49:48--  [http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh](http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh)
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to [www.alsa-project.org:80]("http://www.alsa-project.org/").
HTTP request sent, awaiting response... 200 OK
Length: 27247 (27K) [text/plain]
Saving to: `alsa-info.sh'

100%[======================================>] 27,247       166K/s   in 0.2s    

2011-06-27 09:49:48 (166 KB/s) - `alsa-info.sh' saved [27247/27247]

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
ALSA Information Script v 0.4.60
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

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Automatically upload ALSA information to [www.alsa-project.org?]("http://www.alsa-project.org/?") [y/N] : y
Uploading information to [www.alsa-project.org]("http://www.alsa-project.org/") ...  Done!

Your ALSA information is located at 
Please inform the person helping you.
```

---

### Post by fatteralbert on 2011-06-27
Thanks for trying to help. 

Don't ask me to explain it, but all of a sudden the sound works fine. 

I have a dock where I put the laptop to connect to an external monitor, etc. The dock doesn't seem to output sound but when I plugged in the cable in the laptop it works. That's good enough for me right now. I've got bigger fish to fry. Like Spotify crashing on me. 

See you in another thread. Cheers.

---


---
title: "&quot;waiting for sound system to respond&quot; problem"
date: 2010-05-08
forum: Multimedia Software
---

### Post by burakvarhan on 2010-05-08
Hi everybody,

I have this problem regarding the sound controls. I just installed ubuntu 10.04 although everything works fine I have a problem related to sound, When I click Preferences/Sound I get the message "waiting for sound system to respond" and actually it does not respond at all. Although, I have downloaded, compiled and installed linux drivers from realtek website it did not fix the problem. I tried a suggestion on internet which is simply deleting .pulse folder and restarting it didnt work either.

At the moment I am using terminal alsamixer for controlling sound level but even the maximum attainable volume is too low.

I would appreciate any help.
Thanks

---

### Post by lidex on 2010-05-08
Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by burakvarhan on 2010-05-09
Thank you for the answer lidex

I tried it unfortunately it did not solve my problem. It is a shame that realtek does not provide up-to-date and compatible linux drivers for their products.

---

### Post by lidex on 2010-05-10
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by greggler on 2010-05-10
i have the exact same issue, everything has worked fine on this hardware since dapper drake and it even worked great on 10.04 for a while.  then, i did the latest update and poof no sound.

tried removing ~/.pulse and removing/reinstalling pulse but no effect.

---

### Post by windfix on 2010-05-10
Same problem, here's the output from mine...

paul@paul-laptop:~$ uname -a
Linux paul-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
paul@paul-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@paul-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
paul@paul-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: IDT 92HD71B7X

Any insights appreciated

Added info:  Rhythmbox actually will play my .mp3 files... but gnome-sound-control continues to return "waiting for sound system to respond"

---

### Post by burakvarhan on 2010-05-11
Thank you for your time lidex. My laptop is ASUS G51VX and I have 64 bits Ubuntu 10.04 installed. Below are the outputs of the commands you asked for

root@pi:~# uname -a
Linux pi 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
root@pi:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
root@pi:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May  7 2010 for kernel 2.6.32-22-generic (SMP).
root@pi:~# head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC663

---

### Post by lidex on 2010-05-11
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m42  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by greggler on 2010-05-12
my problem was a failure to load the pulse-lirc module.  will have to pursue that on another thread.  once that module was removed, the sound system did start but i still have no volume control in the indicator applet.

---

### Post by windfix on 2010-05-12
Solved mine.  Completely "out there" issue.  I'd recently put my home directory on an ntfs partition (hoping to share files with Windows7) - BAD idea.  All file ownerships got changed to root.  There are files in /home that must be writable by the logged in user, and that caused the errors for me.

I've moved everything back to an EXT3 partition, changed ownerships, and everything is hunky dory. Thanks for listening.

---

### Post by ozkhalsa on 2010-05-16
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Hi I have the same problem now on 10.04 after fresh update. The output file is enclosed as per your code. Can you advise me a solution also.
```

  suprit@ubuntudesktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
suprit@ubuntudesktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
suprit@ubuntudesktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
 
```

---

### Post by greggler on 2010-05-16
looks like my issue was a goof-up having an old locally compiled version of lirc in /usr/local interfering with a few things.  removed that and reinstalled the official lirc and all is well.

---

### Post by ozkhalsa on 2010-05-16
> **ozkhalsa said:**
> Hi I have the same problem now on 10.04 after fresh update. The output file is enclosed as per your code. Can you advise me a solution also.
```

  suprit@ubuntudesktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
suprit@ubuntudesktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
suprit@ubuntudesktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
 
```


I have already tried the earlier solution using the dell M-42 line , but still no solution. The volume icon on the top panel is also missing and did not install right from the first upgrade install and boot

---

### Post by lidex on 2010-05-16
ozkhalsa,
I would suggest an alsa upgrade. Use the upgrade link in my sig.

---

### Post by m2dodd on 2010-05-20
lidex,
 
I appreciate your post. It appears to have fixed most of my audio problems.
 
However, along with the "waiting for sound system to respond" problem, my volume control applet has quit functioning since my upgrade from 9.10 to 10.04 on my Dell M1330. The volume was appeared to be &#8220;stuck&#8221; at a low setting. I could adjust the applet and any other mixer control, but the volume did not change.

Since I applied the alsa upgrade script, I now have volume control when I use the Gnome ALSA Mixer. However, I still have the message "waiting for sound system to respond" issue and volume applet still does not function. Do you have any suggestions on how I can restore function to the volume applet in the Gnome panel? Thanks.

---

### Post by Yellow Pasque on 2010-05-20
A lot of people have issues with the hidden files pulseaudio stores in the user's home directory. Deleting them should force pulse to generate fresh ones:
```
cd ~/
rm -rf .pulse*
pulseaudio --kill
pulseaudio --start -D #pulseaudio autospawns by default, so only use this command if you disabled autospawn
```

---

### Post by m2dodd on 2010-05-20
Thanks Temüjin, that appears to have fixed the problem.

---

### Post by rupert160 on 2010-05-25
_

---

### Post by rupert160 on 2010-05-25
> **windfix said:**
> Solved mine.  Completely "out there" issue.  I'd recently put my home directory on an ntfs partition (hoping to share files with Windows7) - BAD idea.  All file ownerships got changed to root.  There are files in /home that must be writable by the logged in user, and that caused the errors for me.

I've moved everything back to an EXT3 partition, changed ownerships, and everything is hunky dory. Thanks for listening.

windfix: This is actually a really important post of yours. As what you found was likely the cause of this problem for me and a number of other ones. I've reinstalled again and mounted home to ext4 and am looking to link it to the existing documents directory in the ntfs area. Once I solve this I'll post back...

---

### Post by m2dodd on 2010-06-02
Well... the code that Temüjin supplied fixed my problem until I rebooted the system. I now have the same problem and the code no longer corrects the problem. Do you have any other ideas? Thanks.

---

### Post by moonstar on 2010-08-28
> **rupert160 said:**
> windfix: This is actually a really important post of yours. As what you found was likely the cause of this problem for me and a number of other ones. I've reinstalled again and mounted home to ext4 and am looking to link it to the existing documents directory in the ntfs area. Once I solve this I'll post back...

this fixed it for me too.  pretty common people having wubi installs and needing more space.  

once i copied my home dir back from windows ntfs to the ubuntu file system, i simply did

```

sudo chown -R myuser /home/myuser 
sudo chgrp -R myuser /home/myuser 

```

where myuser is whatever your username is.

---

### Post by fallenshadow on 2010-08-29
Im getting insanely frustrated with PulseAudio... makes me want to hurt the developer!! However that wouldn't solve anything. :D

I keep having problems with PulseAudio not starting/responding. I have tried many different fixes and tweaks but nothing works.

When I tried this command:

```
sudo pulseaudio --start -D
```

I get the following:

> 
E: core-util.c: Home directory /home/myname not ours.
W: lock-autospawn.c: Cannot access autospawn lock.
E: main.c: Failed to acquire autospawn lock


Does this mean anything to anybody? Is there some fix for this?

---

### Post by lidex on 2010-08-29
> **fallenshadow said:**
> Im getting insanely frustrated with PulseAudio... makes me want to hurt the developer!! However that wouldn't solve anything. :D
I keep having problems with PulseAudio not starting/responding. I have tried many different fixes and tweaks but nothing works.
When I tried this command:
```
sudo pulseaudio --start -D
```
I get the following:
Does this mean anything to anybody? Is there some fix for this?

Check the ownership/permissions on your ~/user directory and delete ~/.pulse as well as ~/.pulse-cookie

---

### Post by Yellow Pasque on 2010-08-29
Don't use sudo for pulseaudio command..
I fixed the above post where I did.

---

### Post by fallenshadow on 2010-08-30
I decided to upgrade PulseAudio and ALSA using a ppa.

I don't have problems with PulseAudio starting anymore. However I don't have any sound for the login screen and for logging in. :D

Im not sure is there anything I can do to fix that but it doesn't bother me that much.

---

### Post by Yellow Pasque on 2010-08-30
See if installing libcanberra-pulse package fixes system sounds. If so, you may need this fix for apps that use the ALSA library: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by Ubuk2008 on 2010-10-18
Without running any codes in terminal, what helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone

---

### Post by qianian on 2010-10-27
@Ubuk2008, amazing, thank you! 

Running 10.10 on a lenovo Thinkpad R61i

---

### Post by norm.h on 2010-10-29
I was trying to overcome an echo problem in Skype.

If I disabled PulseAudio and its autospawn, the echo disappeared, but so did my Volume Control icon.
If I created an icon ("Send Launcher to Panel" from System - Preferences - right-click Sound), I got the "waiting for sound system to respond" message.

Your procedure worked a treat, many thanks

---

### Post by Mystery777 on 2010-11-30
> **Temüjin said:**
> A lot of people have issues with the hidden files pulseaudio stores in the user's home directory. Deleting them should force pulse to generate fresh ones:
```
cd ~/
rm -rf .pulse*
pulseaudio --kill
pulseaudio --start -D #pulseaudio autospawns by default, so only use this command if you disabled autospawn
```


Excellent solution! It worked like a charm for me too!!!:popcorn:

---

### Post by bvanaerde on 2011-06-25
> **Ubuk2008 said:**
> Without running any codes in terminal, what helped me was the following:

1. Go to 'Home' folder by clicking the 'Places' menu
2. press Ctrl + H to reveal hidden folders
3. delete the '.pulse' folder
4. restart

Hope this helps someone

It sure helped me...
I've been having audio problems when using VLC lately (audio lag, audio dropping after 10 minutes, ...). I'm using Ubuntu 10.04 LTS. I guess it started after applying the latest updates a few weeks ago. Removing the .pulse folder solved it.

---


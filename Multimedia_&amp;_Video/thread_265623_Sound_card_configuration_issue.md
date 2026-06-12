---
title: "Sound card configuration issue"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by wittyguysuku on 2006-09-26
> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

> No volume control GStreamer plugins and/or devices found.

Above are the error messages that I got when I tried adjusting my sound settings.

So I could not play any music files. But one strange thing I found is, I could play the music when opening xmms as root.

What should I do to resolve this issue? Any sort of help would be greatly appreciated.

thanks,

---

### Post by Gotterdammerung on 2006-09-26
do you have ALSA modules compiled for your kernel?

---

### Post by wittyguysuku on 2006-09-26
> **Gotterdammerung said:**
> do you have ALSA modules compiled for your kernel?

I installed Ubuntu from Live CD. So didn't change anything on kernel.

---

### Post by Kateikyoushi on 2006-09-26
What is the result if you type this command ?

aplay -l

---

### Post by wittyguysuku on 2006-09-26
> **Kateikyoushi said:**
> What is the result if you type this command ?

aplay -l

From root terminal:
> root@rsukumar:/home/rsukumar# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

whereas from a user terminal who doesn't have root privileges:
> [rsukumar@rsukumar] ~
$ aplay -l
aplay: device_list:221: no soundcards found...

This is the difference I observed.

---

### Post by Kateikyoushi on 2006-09-26
Is the user member of the audio group ?
Seems to me like a permission issue.

---

### Post by wittyguysuku on 2006-09-26
How to check that? How to add this user to audio group then?

---

### Post by Kateikyoushi on 2006-09-26
System >> administration >> users and groups.
There select the user then properties and user privilages.

You can also use the adduser command in terminal, 

```
sudo adduser USERNAME audio
```

Type "adduser -h" for additional help.

---

### Post by wittyguysuku on 2006-09-26
Thanks Kateikyoushi for the fast reply!
Do I need to reboot the system? Coz still the problem persists :(

---

### Post by Kateikyoushi on 2006-09-26
Honestly I do not remember it was a long time ago when this happened to me. :confused: 
Try to reboot.
Was the user member of the audio group ?

---

### Post by wittyguysuku on 2006-09-26
> **Kateikyoushi said:**
> Honestly I do not remember it was a long time ago when this happened to me. :confused: 
Try to reboot.
Was the user member of the audio group ?

Thanks Kateikyoushi!!!
Thanks for your memory too!!

It worked after I reboot!

Thanks again for such a quick help!

--Wg-:D

---

### Post by Gotterdammerung on 2006-09-26
> **wittyguysuku said:**
> Thanks Kateikyoushi for the fast reply!
Do I need to reboot the system? Coz still the problem persists :(

If something like this happens again, you'll just have to update the user session, i.e., logout+login.

---

### Post by Gotterdammerung on 2006-09-26
It may happen with games (the group is games) like americas army, which is installed in /opt.

---

### Post by wittyguysuku on 2006-09-27
> **Gotterdammerung said:**
> It may happen with games (the group is games) like americas army, which is installed in /opt.

Gotterdammerung,
Could you please tell me the significance of the filesystem/partition? How should I partition for an effective linux os? How much memory should be allocated for swap?

---

### Post by Kateikyoushi on 2006-09-27
You can answers to these common questions in the ubuntu docs.

[Partitioning]("https://help.ubuntu.com/community/HowtoPartition").

[Filesystems]("https://help.ubuntu.com/community/LinuxFilesystemsExplained?highlight=%28filesystem%29").

[Swapfaq]("https://help.ubuntu.com/community/SwapFaq?highlight=%28swap%29").

Which filesystem to use ?
You can esily end up reading and thinking about which filesystem to use than the benefits would mean to you in terms of speed.
Like XFS is faster with big files JFS with small ones, reiserfs is slightly faster than the default ext3 of Ubuntu.

You might end up getting different recommendations from people so just stick to the default you won't miss anything and you can change it anytime.

---

### Post by mtn on 2007-11-15
I'm having the same problem (no sound) running the game Americas Army on Gutsy 7.10

This is the terminal output I get.

```
username@A120:~/armyops$ sudo ./armyops
Cheat protection disabled
open /dev/[sound/]dsp: Device or resource busy
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Defaulting to false
```

Any ideas what the problem is?

---


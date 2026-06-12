---
title: "Switch headset -&gt; speaker via command line ?"
date: 2010-10-17
forum: Multimedia Software
---

### Post by zsugiart on 2010-10-17
Hey all, 

I'm still on UBUNTUO 9.04 atm - I'm getting myself a Logitech USB headset. I plugged it in, and immediately I see this in dmesg

[ 7015.732141] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.3/input/input11
[ 7015.732234] generic-usb 0003:046D:0A0B.0006: input,hidraw3: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1a.1-2/input3
[ 7280.088017] usb 1-3: reset high speed USB device using ehci_hcd and address 3

Which is fantastic. Tested this on all kind of audio and I can hear them fine. So headset is working wonders. 

Except, everytime I want to switch the output from between the speaker and the headset, I have to go 

System > Preference > Sound > output tab > click on the switch. 

Which is fine, but the switching procedure via GUI is very arduous. 

Is there a way to to do this via the command line, if so I can bind it to a hotkey and therefore with one hotkey I will be able to switch between headset vs my speaker?

Cheers,
Z

---

### Post by zsugiart on 2010-10-17
Found an interesting link here
[http://superuser.com/questions/89164/how-to-make-sound-profiles-on-ubuntu-9-10](http://superuser.com/questions/89164/how-to-make-sound-profiles-on-ubuntu-9-10)
but didn't work. Tried the following:

1) set sound pref to use headset
alsactl -f profile.headset store

2) set sound pref to use speaker
alsactl -f profile.speaker store

3) compare the two
vimdiff profile.headset profile.speaker

Looks good so far, but if I try the restore command, nothing happened. 

alsactl -f profile.headset restore; or
alsactl -f profile.speaker restore

it doesn't seem like the restore command works or has any bearing on my system.

---

### Post by grepcat on 2010-10-20
Hi,

I used to use asoundconf, but it's been [removed from Ubuntu since Karmic ]("http://https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/376024")(seems to be a bit controversial, what ho...)

The launchpad thread linked above suggests using the following (comment 27):

```

$ pacmd list-sinks | less
$ pacmd set-default-sink [index number]
```I'm on a laptop with one sound sink at the moment, so can't test this, but let me know how you get on.

It should be quite easy to set up a desktop shortcut as well.

GL

---

### Post by zsugiart on 2010-10-24
Hi, 

thanks thanks very much for your tip. 

"pacmd" (pulse audio cmd) is definitely the shiz. I was trying to use alsactl and asoundconf, but forgetting the whole pulse thing. 

Within a few seconds googling I found this EXCELLENT script
[http://ubuntuforums.org/showthread.php?t=1370383](http://ubuntuforums.org/showthread.php?t=1370383)

I've now wired this to a hotkey in my keyboard, and I can now switch comfortably between the sinks. 

Prior to this I don't even know what keyword to search, now I know the concept of "sinks" and I discovered pacmd. Awesomelicious. 

I modded the script a bit to better suit my need, but the script on that thread works straight off, it's very impressive!

---

### Post by grepcat on 2010-10-24
Awesomlicious indeed!  

Cheers for the link to the script - as usual someone else has done the legwork for me!

---


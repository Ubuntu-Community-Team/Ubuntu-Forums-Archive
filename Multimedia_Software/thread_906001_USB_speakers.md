---
title: "USB speakers"
date: 2008-08-30
forum: Multimedia Software
---

### Post by cipher99 on 2008-08-30
I have usb speakers and Hardy.
Following boot, "USB Audio (not connected)" appears on Pref/Sound/Devices.  If I unplug and replug the speaker usb connector, a piece of Ubuntu login plays and then USB Audio is connected.

Is the usb driver not loading at boot?  How to get it loaded at boot?

---

### Post by minky311 on 2008-08-31
Could you please post the output when you type the following in terminal
```
cat /proc/asound/modules
```

---

### Post by cipher99 on 2008-08-31
cat /proc/asound/modules      returns
0 snd_hda_intel
1 snd_usb_audio

This is after boot when Pref/Sound/Devices is showing "USB Audio (not connected) is displayed.

---

### Post by minky311 on 2008-08-31
Go into the terminal and type the following to change your default soundcard
```
sudo nano /etc/modprobe.d/alsa-base
```

Once there head down to the bottom of the text and change snd_usb_audio index=<some number here> to 0.

Then change snd_hda_intel index=<some number here> to 1.
Then exit by pressing control and x. It will then ask you what you would like to name it. Keep it how it is and press enter.
Reboot.

---

### Post by cipher99 on 2008-08-31
That would probably work if snd-usb-audio were still present.  Now when I reboot and cat /proc/asound/modules, all I get is snd-hda-intel.  How do I get snd-usb-audio to load as before?

---

### Post by minky311 on 2008-08-31
Have you tried 
```
sudo nano /etc/modprobe.d/alsa-base
```

And then changing snd_usb_audio back to 1 and changing snd_hda_intel back to 0?

---

### Post by cipher99 on 2008-08-31
Yep, that's exactly what I did, and it works. Thanks. Actually I commented both lines out first and those were the priorities that got assigned so I entered them that way in alsa-base.  Great now I have music.

Now about the system sounds...
I have not had system sounds at any point since connecting the usb speakers.

---

### Post by minky311 on 2008-08-31
I also have that problem of not being able to hear system sounds in system->preferences->sound and then going into sounds. Everything I try to play in there I can't hear. The only system sound I hear is when I first get to the login screen I hear bongos. I haven't found a solution yet.

---

### Post by erikthedrink on 2009-09-08
I've got logitech usb speakers. In Terminal, type

[FONT=Georgia][SIZE=4]asoundconf set-default-card 1[/SIZE][/FONT]

Then close and re-open your browser (Mozilla Firefox) or restart your system.
:P
Note, if you unplug your usb speakers, your laptop speakers will take over.  In order to re-establish contact with the usb speakers, you will need to (plug them back in) restart the system.

---


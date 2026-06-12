---
title: "Headphone is not working"
date: 2015-11-21
forum: Multimedia Software
---

### Post by frederic4 on 2015-11-21
Hallo, I have Windows and Linux on my Laptop. Under windows the headphone output is working. Under Linux the headphone is not working.
 Here is Info about my System: [http://www.alsa-project.org/db/?f=0d66c77c8d5816ad730b3e583f9dabaa07c8e9f9](http://www.alsa-project.org/db/?f=0d66c77c8d5816ad730b3e583f9dabaa07c8e9f9)

Thank you for any help

---

### Post by Yellow Pasque on 2015-11-21
You're running Ubuntu 11.04.  It's EOL/unsupported.
EDIT: Actually, it says the script was run in July. You may have given the wrong link...

---

### Post by frederic4 on 2015-11-22
Thanks for the answer. You are right, that was the wrong info. Here is the right one: [http://www.alsa-project.org/db/?f=12ba9e70a023d2a4b81a5cfd53ffbd6e8d8fd443](http://www.alsa-project.org/db/?f=12ba9e70a023d2a4b81a5cfd53ffbd6e8d8fd443)

---

### Post by Yellow Pasque on 2015-11-23
I'm guessing it's caused by or related to:
```
[    4.474332] sound hdaudioC2D0: ignore pin 0x1b with mismatching assoc# 0x3 vs 0x2
```

Try this:
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```

See if the headphones are detected at the next (re)boot.

---

### Post by frederic4 on 2015-11-24
Sorry, is still not working. But i have had trouble with this code. After all I added in my alsa-base.conf  just    options snd-hda-intel model=auto     in the last line
Is that what you want me to do? But this doesn't work. Sorry, I'm am new to Linux.

---

### Post by Yellow Pasque on 2015-11-24
> **frederic4 said:**
> Sorry, is still not working. But i have had trouble with this code. After all I added in my alsa-base.conf  just    options snd-hda-intel model=auto     in the last line
Is that what you want me to do? But this doesn't work. Sorry, I'm am new to Linux.

Yes, that was I wanted you to do. However, since it did not work, you can remove the line.

The next thing to try is manually retasking the troublesome pin (0x1b) as a headphone. You may need to check the "show unconnected pins" box:
```
sudo apt-get install alsa-tools-gui
hdajackretask  #I can't remember if this needs root/sudo permissions
```

---

### Post by frederic4 on 2015-11-24
I opened hdajackretask and select a codec Realtek ALC892 and set Black line out, rear side Pin Id :0x1b to override as a headphone and pres Apply now. Then it says : tee: /sys/class/sound/hwC2D0/reconfig: Das Gerät oder die Ressource ist belegt

---

### Post by Yellow Pasque on 2015-11-24
I guess you need to stop pulseaudio first:
```
echo autospawn = no >> ~/.pulse/client.conf
killall pulseaudio
```
Then, you can restart it when you are finished with hdajackretask:
```
pulseaudio -D
```

---

### Post by frederic4 on 2015-11-24
I've stopped Pulse audio, tried hdajackretask , but same problem as before. I stopped alsa and jack with cadence and tried again, but the same problem.

---

### Post by Yellow Pasque on 2015-11-25
I only have two more suggestions:
1. Try latest kernel sound code: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS) (You would use the oem-audio-hda-daily-lts-vivid package)
2. File a bug against Drivers/Sound(ALSA) on [https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)   Remember to include the correct link to your alsa info and also mention that you have tried the latest kernel module

---

### Post by frederic4 on 2015-11-26
Thanks a lot for helping. Sorry, it still do not work. I have reported the bug.

---

### Post by Yellow Pasque on 2015-11-27
I realize that I gave outdated command:
```
echo autospawn = no >> ~/.pulse/client.conf
```
should have been:
```
echo autospawn = no >> ~/.config/pulse/client.conf
```

---


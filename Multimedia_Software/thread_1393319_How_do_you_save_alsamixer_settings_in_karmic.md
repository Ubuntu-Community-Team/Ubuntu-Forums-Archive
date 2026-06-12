---
title: "How do you save alsamixer settings in karmic"
date: 2010-01-29
forum: Multimedia Software
---

### Post by garvinrick4 on 2010-01-29
In karmic my settings are not retained, have to unmute in sound preferences or open alsamixer
and raise master and speaker in Terminal. What is fix to save settings using 9.10 with card below.

id:multimedia
                description: Audio device              product: 82801I (ICH9 Family) HD Audio Controller              vendor: Intel Corporation              physical id: 1b
              bus info: pci@0000:00:1b.0
              version: 03              width: 64 bits              clock: 33MHz              capabilities: bus_master cap_list               configuration: driver=HDA Intel latency=0              resources: irq:29 memory:d4500000-d4503fff

---

### Post by lijcam on 2010-01-29
Make your changes with the mixer then do

```
sudo alsactl 0
```

The 0 refers to which sound card on your system you are saving. If you only have one than it is safe to assume the device is 0.

---

### Post by garvinrick4 on 2010-01-30
Found this bug report below and used: Now sound does not reset to muted on reboot. 9.10
[André Gaul]("https://launchpad.net/%7Eandrenarchy")             wrote             on 2009-12-13:                                                             [ #77]("https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732/comments/77")                                                        This issue may be a problem in pulseaudio. I managed to get it to work as expected by replacing the line
 load-module module-device-restore
 in /etc/pulse/default.pa with
 #load-module module-device-restore
 Perhaps you have to logout, kill all pulseaudio daemons, login, adjust volumes, logout and login again to see if it works.

        


[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/352732)

---

### Post by owenspa on 2010-04-08
> **lijcam said:**
> Make your changes with the mixer then do

```
sudo alsactl 0
```

The 0 refers to which sound card on your system you are saving. If you only have one than it is safe to assume the device is 0.

The command should be

```
sudo alsactl store 0
```

However it doesn't work for me, I'm running 9.04 UNR.
It used to work fine, something has changed.

---

### Post by lidex on 2010-04-08
> **owenspa said:**
> The command should be

```
sudo alsactl store 0
```

However it doesn't work for me, I'm running 9.04 UNR.
It used to work fine, something has changed.

See post #3...

---


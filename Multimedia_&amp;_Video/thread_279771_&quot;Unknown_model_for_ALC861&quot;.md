---
title: "&quot;Unknown model for ALC861&quot;"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by cronholio on 2006-10-18
A friend of mine has an ASUS laptop and cannot get any sound in Dapper. I tried updating the ALSA drivers to the latest version, I also tried the official driver from the Realtek website and still no sound. He keeps getting this message "Unknown model for ALC861" in syslog, even though the drivers are said to work for this card.

The mixer and everything is displayed, the sound is not muted and all the devices are there. Only there is no sound output. Any ideas?

---

### Post by Kateikyoushi on 2006-10-18
Someone managed to make it work in [this thread]("http://ubuntuforums.org/showthread.php?t=264196&highlight=alc861") as him how did he do that. The others seem to have the same problem as you.

---

### Post by didobuntu on 2006-10-19
> **cronholio said:**
> A friend of mine has an ASUS laptop and cannot get any sound in Dapper. I tried updating the ALSA drivers to the latest version, I also tried the official driver from the Realtek website and still no sound. He keeps getting this message "Unknown model for ALC861" in syslog, even though the drivers are said to work for this card.

The mixer and everything is displayed, the sound is not muted and all the devices are there. Only there is no sound output. Any ideas?

This driver is now taken into account in the last alsa release, the 1.0.13 version.

Enjoy !!

---

### Post by NaitoNeko on 2006-10-29
I am having the same problem. I build the new alsa drivers and I compiled them. I add the modules and all seems to work fine, but it seems that nothing happens. It seems that my version of alsa stills been the old one. I dont know why my system does not recognize the new alsa drivers. Any ideas ?:confused:

---

### Post by cronholio on 2006-10-29
If you follow all the steps in the "INSTALL" file you should now run the new ALSA version. If not, try a reboot (even if it makes you feel like a Windows user. ;)

This will show you the version of your current driver if you are unsure:

```
cat /proc/asound/version
```

---

### Post by cronholio on 2006-10-29
By the way, it still didn't work for me with the new drivers. I am not sure if the card is recognized correctly. This is what lspci has to say:

```
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 1338
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]
```

This is from syslog sometime into the boot process:

```
hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
```

But in /proc it tells me the card is a:

```
Realtek ALC660
```

So why does it think it is an ALC861 if it is in fact a 660, or is it the other way around? :confused:

---


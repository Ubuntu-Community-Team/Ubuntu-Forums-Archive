---
title: "How to choose right sound card ?"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by daneka on 2007-05-17
Hello, I have some problem with choosing my sound card and I still cant solve that.

I read this topic: [http://ubuntuforums.org/showthread.php?t=114551]("http://ubuntuforums.org/showthread.php?t=114551") . I try to change position v /etc/modprobe.d/alsa-base but i wasnt successfull.

Here is my alsa-base:
```


# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
# install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-emu10k1x index=0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
#options snd-via82xx-modem index=1
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


```

```


$ cat /proc/asound/modules
 0 snd_via82xx
 1 snd_mpu401
 2 snd_emu10k1


```

```


$ cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC655 at 0xed00, irq 20
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10
 2 [Audigy         ]: Audigy - Audigy 1 ES [SB0160]
                      Audigy 1 ES [SB0160] (rev.3, serial:0x521102) at 0xe000, irq 21


```

I want my Audigy sound card to be loaded us default, not my integred VIA sound card.

May somebody help me please ? Thank you.

---

### Post by dbd on 2007-05-20
You'll probably need to disable the on board audio in the BIOS. Have a look around, it should be pretty straightforward (just don't change anything else :)). If you can't work it out then your motherboard's manual will let you know how.

---

### Post by daneka on 2007-05-21
Ubuntu doesnt use BIOS. I am suprised that you dont know that. Anyway I already tried that.

---

### Post by dbd on 2007-05-21
> **daneka said:**
> Ubuntu doesnt use BIOS. I am suprised that you dont know that. Anyway I already tried that.
I'm almost certain that you're wrong. If the on board audio is disabled in the BIOS then no matter what operating system you are using it won't even be aware that you have anything on board.

Anyway, had a quick search for "sound card" on the wiki and came up with this, it looks like exactly what you are looking for:
[https://wiki.ubuntu.com/SelectDefaultSoundCardInKubuntu?](https://wiki.ubuntu.com/SelectDefaultSoundCardInKubuntu?)

---

### Post by daneka on 2007-05-25
Thak you very much, it helped me.
But Ubuntu use BIOS just for mounting file-system, myby clock.

---

### Post by zouhair on 2007-11-28
```
zouhair@gutzy:~ (22.065 MB) $ asoundconf list
Names of available sound cards:
IXP
Modem
Audigy2
zouhair@gutzy:~ (22.065 MB) $ asoundconf set-default-card Audigy2

```

Then restart.

---

### Post by sirdilznik on 2007-11-28
I'm glad to see you got that resolved.  Just as a FYI, it can also be done a different way(assuming you don't plan to use the other sound cards).  You could simply blacklist the drivers of the other two devices thus only loading the emu10k1 driver.

---

### Post by fenian on 2007-11-28
> But Ubuntu use BIOS just for mounting file-system, myby clock.
[URL="http://en.wikipedia.org/wiki/BIOS"]
Look here for info on what the BIOS is[/URL].It' works strictly with the settings for your moherboard and doesn't really have much to do with operating systems.

---


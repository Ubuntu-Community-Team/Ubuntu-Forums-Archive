---
title: "Soundcard configuration with ICH5 and 5.1 Soundsystem"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by mixx000 on 2006-09-28
hi all,

recently, i buyed a 5.1 soundsystem from creative (inspire t6060).
My soundcard is a intel ich5, 8 channel.
There is a triple stereo-audio line-in cable, with the following colors: black, orange and lime-green.
The sound's playing but the center-speaker doesn't work(Under win it works very well).
I tried around but it really doesn't work.
And in the gnome volume control, the master is for the frontspeakers and the PCM is for the rear speakers.. surround works correctly.

Informations:

```

$ cat /proc/asound/cards
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with ALC850 at 0xfebff800, irq 209
1 [Bt878          ]: Bt87x - Brooktree Bt878
                     Brooktree Bt878 at 0xefeff000, irq 217
2 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x300, irq 10

```

```
$ lspci|grep Multimedia
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
0000:02:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:02:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

```

$ cat /etc/asound.conf
#i got this from the german ubuntuforums..but doesnt work anyway
pcm.ch40dup {
    type route
    slave.pcm surround40
    slave.channels 4
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 0
    ttable.1.3 0
}

pcm.via82xx
{
    type hw
    card 0
    device 1
}
ctl.via82xxb
{
    type hw
    card 0
}
pcm.!default{
    type route
    slave.pcm surround51
    slave.channels 6
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1 #
    ttable.0.4 1 # should i comment out them, because i only have three connectors?
    ttable.1.5 1 #

}

```

thanks for replys.

-mix

---

### Post by mixx000 on 2006-09-29
no ideas? :(

---


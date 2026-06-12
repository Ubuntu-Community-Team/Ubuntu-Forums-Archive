---
title: "HDMI audio stops working - suggestions for debugging?"
date: 2014-06-30
forum: Mythbuntu
---

### Post by cedyathome on 2014-06-30
My HDMI audio in the front-end will occasionally stop working (after working fine for days!). It happened this morning and a reboot didn't fix it. I had to power off / on the system to get it to work again.

I'm using mythtv v0.27 and a GEForce GT610 card. I used the mythbuntu 14.04 ISO to build the system.

I'd appreciate any pointers on how to debug this issue.

---

### Post by blm-ubunet on 2014-07-01
Stop working while using it ?
Or only stopping working after power on/cycle?
nVidia driver or nouveau?
Can you cure the problem by re-scanning/testing audio devices in FE?
Can you cure it with "pavucontrol" (desktop)?

The sequence of the power on to different devices in chain was a problem in the recent history of HDMI audio in linux.
The required sequence **was** TV --> HTamp --> computer.

But support of hot-plug events should have fixed that.

Next time audio fails make a copy of output of "dmesg".

---

### Post by khPWXxF on 2014-07-03
Possibly related to"blank screen after tv has been off"?  Sorry cant give url using phone.
Phil

---

### Post by cedyathome on 2014-07-03
Thank you all for your suggestions.
It happened again today and I had time to debug...

Turns out that it has something to do with the HDMI connection to my TV (Samsung). My TV is connected via toslink to an amplifier.

If I use the TV's speakers, it works!! I then switched off the tv speakers (back to the amplifier) and it didn't work. I then changed TV inputs to OTA and then back to the my myth computer and voila! It started working. Which leads to to suspect the HDMI connection, but I have no idea of how to verify/debug that.

I also have a roku conncected to the TV via HDMI and I have not experienced this issue there.

Now to figure out why this is happening. I'll chase the "blank screen after tv has been off" to see if there's anything there.

Any suggestions?

---

### Post by blm-ubunet on 2014-07-04
If it starts working after you select TV speakers then I would guess it is a TV problem.

You could provide output of "dmesg" when this happens.

The Toslink connection from TV to amp does not support ELD/EDID reporting.
And it only supports AC3 (pass thru') or stereo PCM.
It is possible your TV reports greater capability than those two but it can **not** transcode anything of them to AC3 (non-free codec)

The best audio connection is PC -->amp (av) -->TV (v) because then the audio ELD of amp is reported to PC.

---

### Post by cedyathome on 2014-07-05
I've determined that the toslink has nothing to do with it. Just switching TV inputs between the HDMI inputs brings the audio back. This makes me think it has something to do with the HDMI link - probably EDID.

I had to add these lines to xorg.conf to get the characters big enough for me to see on the screen. Otherwise the text is teeny.
    Option "UseEdidDpi" "False"
    Option "DPI" "100 x 100"

I have edited out the "UseEdidDpi" "False" line and the text is still the right size - and I have not had the audio problem. But I'm not sure that it is solved yet.

My boot.log and dmesg have some issues which I have to understand & debug. I'm including them here. Any help is appreciated.

```
#$ dmesg | grep terminated
[    3.333189] init: plymouth-upstart-bridge main process (171) terminated with status 1
[    3.337653] init: plymouth-upstart-bridge main process (182) terminated with status 1
[    3.341496] init: plymouth-upstart-bridge main process (184) terminated with status 1
[    3.344995] init: plymouth-upstart-bridge main process (186) terminated with status 1
[    3.349416] init: plymouth-upstart-bridge main process (187) terminated with status 1
[    3.353584] init: plymouth-upstart-bridge main process (189) terminated with status 1
[   11.645316] init: avahi-cups-reload main process (704) terminated with status 1
[   19.435208] init: samba-ad-dc main process (1060) terminated with status 1
[   23.441147] init: udev-fallback-graphics main process (1457) terminated with status 1
[   23.556949] init: plymouth-splash main process (1479) terminated with status 1
[   23.762426] init: plymouth-stop pre-start process (1505) terminated with status 1
[   24.178642] init: nvidia-persistenced main process (1514) terminated with status 1

```

```

#$ cat /var/log/boot.log | grep fail
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated                                                             [fail]
 * Starting remote control daemon(s) :                                   [fail]

```

---


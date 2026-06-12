---
title: "mcirophone not working at all on Ubuntu 6.06 on Dell Inspiron 1300"
date: 2006-08-01
forum: Multimedia &amp; Video
---

### Post by vevak on 2006-08-01
I read the Detailed sound guide and various other guides on this forum but none has been helpful in giving life to my microphone; unable to record sound or use any telephony applet though can use headphone and my laptop internal speakers are working absolutely fine. Some of the guides mentioned about howto correct gnome sound problem which I did as it said. Tried to install ALSA 1.0.12 rc1 drivers but that damaged my installation and had to reinstall again. Please help me out regarding this issue...........

See if these output are helpful.....

vevak@gouki:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG (rev 05)


vevak@gouki:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


vevak@gouki:~$ lsmod | grep sound
soundcore              10208  1 snd


vevak@gouki:~$ cat /proc/asound/modules
0 snd_hda_intel


vevak@gouki:~$ cat /etc/esound/esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
vevak@gouki:~$ cat /etc/asound.conf
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}


vevak@gouki:~$ cat /etc/libao.conf
default_driver=alsa09

---

### Post by osaeris on 2006-08-07
Hi there,

Have you tried using the Mic Boost +20db switch. It may be that your mic is working fine but there's not enough signal. In the volume applet (gnome) under preferences make sure the mic boost +20db box is ticked then go back to the volume control under the switches tab and select it. 

I wouldn't recommend wearing headphones when you tick the box for the first time!

Hope this helps

steve

---

### Post by trukker on 2006-08-08
I have the same problem.... Sound works fine under ALSA but I cannot record....

One thing I noticed was when using alsamixergui ..... I couldn't change the volume setting on the mic....

---

### Post by extremecarver on 2006-08-11
see page 3 on this thread. A change to modprobe will solve it.
[http://www.ubuntuforums.org/showthread.php?t=206606&highlight=microphone](http://www.ubuntuforums.org/showthread.php?t=206606&highlight=microphone)

---


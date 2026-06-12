---
title: "Mythbuntu 12.05 IR PVR-150 not working"
date: 2012-06-10
forum: Mythbuntu
---

### Post by matthys on 2012-06-10
Hello,

I just moved from a Gentoo MythTV box to Mythbuntu 12.04.
But for some reason the IR of the Hauppauge PVR-150 is not working.

In Gentoo I didn't use Lirc as it's part of the new kernel now days. But I used the ir-keytable instead. But I get the feeling Mythbuntu is still using lirc, right? Even if the kernel is:
Linux mythbuntu 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

When I try to start lirc I get:
 * Loading LIRC modules                       [ OK ]
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf

The hardware.conf shows for the remote control part:
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

If I check dmesg for lirc I see:
[   66.207307] lirc_dev: IR Remote Control driver registered, major 250

So what do I need to do to get my Hauppauge PVR-150 IR remote working under Mythbuntu 12.04?

---

### Post by Lester_Burnham on 2012-06-11
Hi,

You pretty much have two paths you can try. Use lirc directly or use lirc with devinput.
If you stop lirc and run:
```
sudo ir-keytable -t
```
Does it return any keystrokes?

Lester

---

### Post by matthys on 2012-06-11
I removed lirc as there is no use of it.

When I try ir-keyrable I get:
ir-keytable -t
/sys/class/rc/: No such file or directory

Seems it's no detected and added as device, why would that be?
Is the  Hauppauge PVR-150 in the current kernel not supported?

---

### Post by Lester_Burnham on 2012-06-11
> **matthys said:**
> I removed lirc as there is no use of it.

When I try ir-keyrable I get:
ir-keytable -t
/sys/class/rc/: No such file or directory

Seems it's no detected and added as device, why would that be?
Is the  Hauppauge PVR-150 in the current kernel not supported?

Is ir-keytable installed?
I have no idea if pvr-150 is supported.

---

### Post by matthys on 2012-06-11
Yes, ir-keytable is installed, but looking for device which is not there.
Only the kernel lirc part for PVR-150 seems not to work.
The video part (ivtv) is working fine, meaning I can record without problems.
But as I use Mythbuntu it would be great to have the IR remote working as well.

---

### Post by blauSquirrel on 2012-06-12
I had the same problem with my pvr-350. I followed the steps listed by [jdroflet]("http://ubuntuforums.org/member.php?u=563228") in [http://ubuntuforums.org/showthread.php?t=1856731&page=2](http://ubuntuforums.org/showthread.php?t=1856731&page=2) and it worked for me.

---

### Post by matthys on 2012-06-12
Indeed some progress here :-)

modprobe -v ir-kbd-i2c
insmod /lib/modules/3.2.0-24-generic/kernel/drivers/media/video/ir-kbd-i2c.ko

tail -n 10 /proc/bus/input/devices
N: Name="i2c IR (Hauppauge WinTV PVR-150"
P: Phys=i2c-2/2-0071/ir0
S: Sysfs=/devices/virtual/rc/rc0/input4
U: Uniq=
H: Handlers=kbd event4
B: PROP=0
B: EV=100013
B: KEY=10afc312 214201700000000 0 118000 41a800004801 9e16c000000000 10000ffc
B: MSC=10

YES !!!

ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
        Driver ir-kbd-i2c, table rc-hauppauge
        Supported protocols: RC-5
        Enabled protocols: RC-5
        Repeat delay = 500 ms, repeat period = 125 ms

It's working, only need the correct keys to load because some are not OK. But I guess this has to do with the correct (or modified) keytable.

So far I added **ir-kbd-i2c to /etc/modules** and works fine (no need of lirc).

PS .. I should add this info as well, part of the Xorg.0.log (needs evdev to use IR remote as keyboard)

[    29.689] (II) config/udev: Adding input device i2c IR (Hauppauge WinTV PVR-150 (/dev/input/event4)
[    29.689] (**) i2c IR (Hauppauge WinTV PVR-150: Applying InputClass "evdev keyboard catchall"
[    29.689] (II) Using input driver 'evdev' for 'i2c IR (Hauppauge WinTV PVR-150'
[    29.689] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.689] (**) i2c IR (Hauppauge WinTV PVR-150: always reports core events
[    29.689] (**) evdev: i2c IR (Hauppauge WinTV PVR-150: Device: "/dev/input/event4"
[    29.689] (--) evdev: i2c IR (Hauppauge WinTV PVR-150: Vendor 0 Product 0
[    29.689] (--) evdev: i2c IR (Hauppauge WinTV PVR-150: Found keys
[    29.689] (II) evdev: i2c IR (Hauppauge WinTV PVR-150: Configuring as keyboard
[    29.689] (**) Option "config_info" "udev:/sys/devices/virtual/rc/rc0/input4/event4"
[    29.689] (II) XINPUT: Adding extended input device "i2c IR (Hauppauge WinTV PVR-150" (type: KEYBOARD, id 10)

---

### Post by matthys on 2012-06-12
One last update .. for those who wonder how I changed keytable.

Created a new /etc/rc_keymaps/hauppauge-pvr150
Modified /etc/rc_maps to load above file instead of /lib/udev/rc_keymaps/hauppauge

Some examples of keys I changed (need to be mapped with the correct keyboard KEY, keep in mind I use this for MythTV):
0x1e25 KEY_ENTER        # KEY_OK
0x1e1f KEY_ESC          # KEY_EXIT      (Back/Exit)
0x1e0d KEY_M            # KEY_MENU      (i)
0x1e10 KEY_VOLUMEUP
0x1e11 KEY_VOLUMEDOWN
0x1e12 KEY_PAGEDOWN     # KEY_PREVIOUS  (Prev.Ch)
0x1e0f KEY_F9           # KEY_MUTE
0x1e20 KEY_UP           # KEY_CHANNELUP
0x1e21 KEY_DOWN         # KEY_CHANNELDOWN
0x1e37 KEY_R            # KEY_RECORD
0x1e36 KEY_ESC          # KEY_STOP
0x1e32 KEY_LEFT         # KEY_REWIND
0x1e35 KEY_P            # KEY_PLAY
0x1e34 KEY_RIGHT        # KEY_FASTFORWARD
0x1e24 KEY_Q            # KEY_PREVIOUSSONG (Replay)
0x1e30 KEY_P            # KEY_PAUSE
0x1e1e KEY_Z            # KEY_NEXTSONG  (Skip)

---


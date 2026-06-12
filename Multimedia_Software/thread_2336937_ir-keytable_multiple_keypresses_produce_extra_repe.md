---
title: "ir-keytable multiple keypresses produce extra repeats"
date: 2016-09-12
forum: Multimedia Software
---

### Post by mshipek on 2016-09-12
Greetings,  I searched the forum and multiple others for a solution to this, but I can't seem to find one that addresses this issue directly for ir-keytable.  Most seem to refer to lirc installations.

I do NOT have lirc installed, but it exists natively in Ubuntu 16.04 kernel.  I’m using Ubuntu LTS 16.04.  ir-keytable is configured using the NEC driver for the MCE/Xbox One remote I configured mappings for.  What is happening, is that when I press a key, it emulates the keyboard properly without any issues and it works as designed.  However, if I press the same key more than once in succession within about 250 ms, it will repeat the key about 20 times incredibly fast.  I have dumps of the ir-keytable -t as well as the status and configuration I’m using.  I also have confirmed that the remote sending the keypresses is NOT sending any sustain or repeats (RTI environment).  I have also confirmed lirc is NOT installed by searching the config directories don't exist and irw doesn't exist.  I have also tried to change the default Repeat delay and repeat period, but it takes and changes them, they just aren’t persistent after a reboot.  It doesn’t seem to help anyway, I’ve changed them to 1000 and 50 respectively and tested but it doesn’t change the behavior.  This is happening in Plex Home Theater.  Any ideas?  Thank you in advance.
 
Hardware: Intel NUC6i5SYH with latest BIOS.
IR onboard and configured in BIOS.  Confirmed working reliably.
 
root@nuc:~# ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event7) with:
        Driver ite-cir, table rc-rc6-mce
        Supported protocols: unknown other lirc rc-5 jvc sony nec sanyo mce-kbd rc-6 sharp xmp
        Enabled protocols: lirc nec rc-6
        Name: ITE8713 CIR transceiver
        bus: 25, vendor/product: 1283:0000, version: 0x0000
        Repeat delay = 500 ms, repeat period = 125 ms
root@nuc:~#
 
~~First three lines of /etc/rc_maps.cfg~~
#driver table                    file
*       *                        xbox_remote
*       rc-adstech-dvb-t-pci     adstech_dvb_t_pci
*       rc-alink-dtu-m           alink_dtu_m
 
root@nuc:~# ir-keytable -c -p RC-6,NEC -w /etc/rc_keymaps/xbox_remote
 
 
root@nuc:~# ir-keytable -s rc0 -r
scancode 0x80d801 = KEY_1 (0x02)
scancode 0x80d802 = KEY_2 (0x03)
scancode 0x80d803 = KEY_3 (0x04)
scancode 0x80d804 = KEY_4 (0x05)
scancode 0x80d805 = KEY_5 (0x06)
scancode 0x80d806 = KEY_6 (0x07)
scancode 0x80d807 = KEY_7 (0x08)
scancode 0x80d808 = KEY_8 (0x09)
scancode 0x80d809 = KEY_9 (0x0a)
scancode 0x80d80e = KEY_0 (0x0b)
scancode 0x80d813 = KEY_Q (0x10)
scancode 0x80d814 = KEY_F (0x21)
scancode 0x80d815 = KEY_R (0x13)
scancode 0x80d819 = KEY_X (0x2d)
scancode 0x80d81e = KEY_UP (0x67)
scancode 0x80d81f = KEY_DOWN (0x6c)
scancode 0x80d820 = KEY_LEFT (0x69)
scancode 0x80d821 = KEY_RIGHT (0x6a)
scancode 0x80d822 = KEY_ENTER (0x1c)
scancode 0x80d823 = KEY_ESC (0x01)
scancode 0x80d865 = KEY_C (0x2e)
scancode 0x80d866 = KEY_P (0x19)
scancode 0x80d867 = KEY_H (0x23)
scancode 0x80d868 = KEY_O (0x18)
scancode 0x80d86e = KEY_I (0x17)
scancode 0x80d86f = KEY_M (0x32)
scancode 0x80d870 = KEY_SPACE (0x39)
Enabled protocols: lirc nec rc-6
root@nuc:~#
 
 
root@nuc:~# ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1473634552.241175: event type EV_MSC(0x04): scancode = 0x80d821
1473634552.241175: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634552.241175: event type EV_SYN(0x00).
1473634552.251813: event type EV_MSC(0x04): scancode = 0x80d821
1473634552.251813: event type EV_SYN(0x00).
1473634552.376940: event type EV_MSC(0x04): scancode = 0x80d821
1473634552.376940: event type EV_SYN(0x00).
1473634552.484285: event type EV_MSC(0x04): scancode = 0x80d821
1473634552.484285: event type EV_SYN(0x00).
1473634552.495393: event type EV_MSC(0x04): scancode = 0x80d821
1473634552.495393: event type EV_SYN(0x00).
1473634552.695346: event type EV_MSC(0x04): scancode = 0x80d821
1473634552.695346: event type EV_SYN(0x00).
1473634552.738179: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634552.738179: event type EV_SYN(0x00).
1473634552.866084: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634552.866084: event type EV_SYN(0x00).
1473634552.946080: event type EV_KEY(0x01) key_up: KEY_RIGHT(0x006a)
1473634552.946080: event type EV_SYN(0x00).
1473634555.090156: event type EV_MSC(0x04): scancode = 0x80d821
1473634555.090156: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634555.090156: event type EV_SYN(0x00).
1473634555.100966: event type EV_MSC(0x04): scancode = 0x80d821
1473634555.100966: event type EV_SYN(0x00).
1473634555.301295: event type EV_MSC(0x04): scancode = 0x80d821
1473634555.301295: event type EV_SYN(0x00).
1473634555.550080: event type EV_KEY(0x01) key_up: KEY_RIGHT(0x006a)
1473634555.550080: event type EV_SYN(0x00).
1473634555.952914: event type EV_MSC(0x04): scancode = 0x80d821
1473634555.952914: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634555.952914: event type EV_SYN(0x00).
1473634555.963546: event type EV_MSC(0x04): scancode = 0x80d821
1473634555.963546: event type EV_SYN(0x00).
1473634556.081871: event type EV_MSC(0x04): scancode = 0x80d821
1473634556.081871: event type EV_SYN(0x00).
1473634556.189804: event type EV_MSC(0x04): scancode = 0x80d821
1473634556.189804: event type EV_SYN(0x00).
1473634556.200727: event type EV_MSC(0x04): scancode = 0x80d821
1473634556.200727: event type EV_SYN(0x00).
1473634556.401026: event type EV_MSC(0x04): scancode = 0x80d821
1473634556.401026: event type EV_SYN(0x00).
1473634556.450099: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634556.450099: event type EV_SYN(0x00).
1473634556.578094: event type EV_KEY(0x01) key_down: KEY_RIGHT(0x006a)
1473634556.578094: event type EV_SYN(0x00).
1473634556.650094: event type EV_KEY(0x01) key_up: KEY_RIGHT(0x006a)
1473634556.650094: event type EV_SYN(0x00).
^C

---

### Post by mshipek on 2016-09-22
Bump.

---

### Post by krauser2 on 2017-07-19
> **mshipek said:**
> Bump.

Hi, did you manage to get the xbox one remote working? I have the same problem. All the buttons are correctly mapped, but the keypresses are way too imprecise. 

(Sorry for bumping an old post)

---


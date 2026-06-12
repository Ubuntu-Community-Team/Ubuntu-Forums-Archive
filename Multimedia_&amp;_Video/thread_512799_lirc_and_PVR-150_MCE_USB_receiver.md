---
title: "lirc and PVR-150 MCE USB receiver"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by unkemptwolf on 2007-07-29
Alright, I've been banging my head against a wall for about a week now trying to get this IR receiver to work. Its the MCE IR receiver that comes with the PVR-150 MCE from Newegg. Ive followed [one]("https://help.ubuntu.com/community/Install_Lirc_Edgy#head-61b516764f233bff0f43ac2ac97bb18db14ad2be") or [two]("http://www.mythtv.org/wiki/index.php/Ubuntu_lirc_install") different guides, which both seem to be more or less the same, but I tried them both anyway just in case. This has been tried in both Dapper (with which I am most familiar) and Feisty. After following the guides the new lirc_mceusb2 modprobes fine (I think), but /dev/lirc never shows up. Nor does /dev/lirc0 or /dev/lirc/0. In fact, the only thing I get in /dev/ is lircd. I know the module is loading because dmesg tells me so:

```
user@mythtvbox:~$ dmesg |grep lirc
[17179606.776000] lirc_dev: IR Remote Control driver registered, at major 61
[17179606.788000] lirc_mceusb2: no version for "lirc_unregister_plugin" found: kernel tainted.
[17179606.792000] lirc_mceusb2: USB remote driver for LIRC v0.22
[17179606.792000] lirc_mceusb2: Martin Blatter <martin_a_blatter@yahoo.com>
[17179606.796000] usbcore: registered new driver lirc_mceusb2

```

I know its picked up on the USB, because it shows up in lsusb:

```
user@mythtvbox:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
**Bus 003 Device 002: ID 0609:0334 SMK Manufacturing, Inc.**
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 05e3:1205 Genesys Logic, Inc. Afilias Optical Mouse H3003
Bus 002 Device 002: ID 045e:00dd Microsoft Corp.
Bus 002 Device 001: ID 0000:0000

```

And yet there seems to be no connection, because it never shows up in /dev/

```
user@mythtvbox:~$ ls /dev/li*
/dev/lircd

```

I am open to any suggestions at all. I've googled until my hands hurt and nothing seems to help. I am certain this is comething simple, and I don't seem to be the only one having the problem, I just cant figure out how to fix it. I will be happy to provide any additional information if it would help.

Thanks!

---


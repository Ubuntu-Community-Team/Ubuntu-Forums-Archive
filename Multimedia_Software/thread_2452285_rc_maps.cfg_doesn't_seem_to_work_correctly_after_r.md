---
title: "rc_maps.cfg doesn't seem to work correctly after recent upgrades"
date: 2020-10-19
forum: Multimedia Software
---

### Post by jbirdjavi2 on 2020-10-19
I recently rebooted after upgrading to the 5.4.0-51 kernel and found that my IR remote was no longer working correctly. Some buttons are working right, but my custom keymap doesn't appear to be loaded.  (To be clear, I'm not blaming the kernel update, it could have been something else, but that's when I noticed it.  It was working prior to this reboot.)

Here are the relevant lines in /etc/rc_maps.cfg:

```
#driver table                    file
mceusb  rc-rc6-mce               rc6_mce_custom.toml
#*      rc-rc6-mce               rc6_mce.toml

```

/etc/rc_keymaps/rc6_mce_custom.toml:

```
[[protocols]]
name = "rc6_mce"
protocol = "rc6"
variant = "rc6_mce"
[protocols.scancodes]
scancode 0x800f0400 = KEY_0
...

```

When I run ir-keytable --read, the output matches /lib/udev/rc_keymaps/rc6_mce.toml, which is commented out in /etc/rc_maps.cfg, so I'm highly confused as to what's going on.

---

### Post by jensk on 2020-10-21
I experience the same thing. It is like rc_keymap just load a default rc6_mce.toml definition out of nothing.
I have tried to remove all .toml files except the one that i have defined. They are removed from both /etc/rc_keymaps and from /lib/udev/rc_keymaps

Stil it loads a default keymap file with this content:
```
root@xxxxx-NUC7PJYH:~# ir-keytable --read
scancode 0x800f0400 = KEY_NUMERIC_0 (0x200)
scancode 0x800f0401 = KEY_NUMERIC_1 (0x201)
scancode 0x800f0402 = KEY_NUMERIC_2 (0x202)
scancode 0x800f0403 = KEY_NUMERIC_3 (0x203)
scancode 0x800f0404 = KEY_NUMERIC_4 (0x204)
scancode 0x800f0405 = KEY_NUMERIC_5 (0x205)
scancode 0x800f0406 = KEY_NUMERIC_6 (0x206)
scancode 0x800f0407 = KEY_NUMERIC_7 (0x207)
scancode 0x800f0408 = KEY_NUMERIC_8 (0x208)
scancode 0x800f0409 = KEY_NUMERIC_9 (0x209)
scancode 0x800f040a = KEY_DELETE (0x6f)
scancode 0x800f040b = KEY_ENTER (0x1c)
scancode 0x800f040c = KEY_SLEEP (0x8e)
scancode 0x800f040d = KEY_MEDIA (0xe2)
scancode 0x800f040e = KEY_MUTE (0x71)
scancode 0x800f040f = KEY_INFO (0x166)
scancode 0x800f0410 = KEY_VOLUMEUP (0x73)
scancode 0x800f0411 = KEY_VOLUMEDOWN (0x72)
scancode 0x800f0412 = KEY_CHANNELUP (0x192)
.......

```

My only toml file on the system is like this:
```
name = "rc6_mce"
protocol = "rc6"
variant = "rc6_mce"
[protocols.scancodes]
0x00 = "KEY_NUMERIC_0"
0x5c = "KEY_ENTER"
0x01 = "KEY_NUMERIC_1"
0x02 = "KEY_NUMERIC_2"
0x03 = "KEY_3"
0x04 = "KEY_4"
0x05 = "KEY_5"
0x06 = "KEY_6"
0x07 = "KEY_7"
0x08 = "KEY_8"
0x09 = "KEY_9"
0x6d = "Key_d"
0xd2 = "KEY_M"
0x6f = "KEY_I"
0x20 = "KEY_PAGEUP"
0x21 = "KEY_PAGEDOWN"
0x2c = "KEY_P"
0x37 = "KEY_R"
0x30 = "KEY_P"
0x31 = "KEY_ESC"
0x58 = "KEY_UP"
0x59 = "KEY_DOWN"
0x5a = "KEY_LEFT"
0x5b = "KEY_RIGHT"
0x0a = "KEY_ESC"

```

My /etc/rc_maps.cfg is like this:
```
*              rc-rc6-mce        /etc/rc_keymaps/rc6_mce.toml

```

If i manuallly load the rc6_mce.toml file with:
```
ir-keymap -c -w /etc/rc_keymaps/rc6_mce.toml
```
I can get the right definitions and all my keypresses on the remote when i test with ir-keymap -t and evtest. 
But mythtv-frontend will not recognise keypresses that originally was above decimal 256 so only e few key are passed on to mythtv

So where does the first definition of the RC6 keypresses come from since it is in no definition file?
system is 20.04 with kernel 5.4.0.51-generic

---

### Post by jensk on 2020-10-21
I think I have found a solution.
As sudo ```
sudo -i
```
I have made at file /usr/local/bin/ir_keytable_load.sh containing
```
#!/bin/bash
/usr/bin/ir-keytable -c -w /etc/rc_keymaps/rc6_mce.toml
```
Make it executable with:
```
chmod +x /usr/local/bin/ir_keytable_load.sh
```

Make a systemD servicefile /etc/systemd/system/ir_keytable_load.service containing
```
After=network.service

[Service]
ExecStart=/usr/local/bin/ir_keytable_load.sh

[Install]
WantedBy=default.target
```

Enable the service witk:
```
systemctl enable ir_keytable_load
```

Test the service with:
```
systemctl status ir_keytable_load
```
This solved my problem. Now the right keymapping is loaded on upstart

---

### Post by steven-openmedia on 2020-11-04
I've got the same issue after a recent update on 20.04. My custom map was being loaded correctly before I upgraded the kernel etc.

Going to try the suggested fix above, but there must be a better workaround.

---

### Post by oldright on 2020-12-11
> **jensk said:**
> I think I have found a solution.
As sudo ```
sudo -i
```
I have made at file /usr/local/bin/ir_keytable_load.sh containing
```
#!/bin/bash
/usr/bin/ir-keytable -c -w /etc/rc_keymaps/rc6_mce.toml
```
Make it executable with:
```
chmod +x /usr/local/bin/ir_keytable_load.sh
```

Make a systemD servicefile /etc/systemd/system/ir_keytable_load.service containing
```
After=network.service

[Service]
ExecStart=/usr/local/bin/ir_keytable_load.sh

[Install]
WantedBy=default.target
```

Enable the service witk:
```
systemctl enable ir_keytable_load
```

Test the service with:
```
systemctl status ir_keytable_load
```
This solved my problem. Now the right keymapping is loaded on upstart

Hi. Are you saying this work-around fixed the problem with mythtv? How is loading the keydefs via upstart different than loading it manually like you did in your previous post? I thought that mythtv didn't work in that case. I will try this but I'd like to understand why loading the definitions file works with upstart but not manually. Thanks!

---

### Post by fnu2 on 2021-03-05
I do face that issue also since kernel versions above 5.4.0-48. My actual workaround is to stay at 5.4.0-48 ...

My investigations on my HTPCs lead to the point that the UDEV rule
```
/lib/udev/rules.d/60-ir-keytable.rules
```
is obviuously not issued correctly with the newer kernels, but I don't find the reason why ...

I can manually issue
```
sudo /usr/bin/ir-keytable -a /etc/rc_maps.cfg
```
It does issue my custom rc-rc6-mce mapping and custom keytable correctly.

---

### Post by fnu2 on 2021-03-10
Spended even more time into investigation, trying to debug, why that udev rule (/lib/udev/rules.d/60-ir-keytable.rules) part of the "ir-keytable" package is not issued correctly or even at all not with kernels version > 5.4.0-48.

Unfortunately I still don't find an answer, but maybe someone else do find it and will post it here.

Above mentioned workaround is for my taste to specific, to tailored, not flexible enough. But mapping something into systemd is a good base/idea.

The IMHO root causing udev rule does contain that:
```
htpc1-user:/home/user> cat /lib/udev/rules.d/60-ir-keytable.rules
# Automatically load the proper keymaps after the Remote Controller device
# creation.
# The keycode tables rules should be at /etc/rc_maps.cfg

ACTION=="add", SUBSYSTEM=="rc", RUN+="/usr/bin/ir-keytable -a /etc/rc_maps.cfg -s $name"
```
Command can be called everytime manually after HTPC is up and running, to provide correct mapping on the fly:
```
htpc1-user:/home/user> sudo /usr/bin/ir-keytable -a /etc/rc_maps.cfg
alte Schlüsseltabelle geleert
45 Schlüsselcode(s) wurden in den Treiber geschrieben.
Protokolle geändert in rc-6
```
To make that happen on every reboot, I created a systemd service:
```
htpc1-user:/home/user> cat /etc/systemd/system/my_ir_keytable_load.service
[Unit]
Description="Reload of my custom ir_keytable due to broken udev rule."
After=udev.service lircd.service inputlirc.service

[Service]
Type=oneshot
RemainAfterExit=true
ExecStart=/usr/bin/ir-keytable -a /etc/rc_maps.cfg

[Install]
WantedBy=multi-user.target
```
Enabled it:
```
htpc1-user:/home/user> sudo systemctl enable my_ir_keytable_load.service
```
After calling it manually or after next reboot:
```
htpc1-user:/home/user> sudo systemctl status my_ir_keytable_load.service
&#9679; my_ir_keytable_load.service - "Reload of my custom ir_keytable due to broken udev rule."
   Loaded: loaded (/etc/systemd/system/my_ir_keytable_load.service; enabled; vendor preset: enabled)
   Active: active (exited) since Wed 2021-03-10 12:01:07 CET; 43s ago
  Process: 661 ExecStart=/usr/bin/ir-keytable -a /etc/rc_maps.cfg (code=exited, status=0/SUCCESS)
 Main PID: 661 (code=exited, status=0/SUCCESS)

Mär 10 12:01:07 htpc1 systemd[1]: Starting "Reload of my custom ir_keytable due to broken udev rule."...
Mär 10 12:01:07 htpc1 ir-keytable[661]: alte Schlüsseltabelle geleert
Mär 10 12:01:07 htpc1 ir-keytable[661]: 45 Schlüsselcode(s) wurden in den Treiber geschrieben.
Mär 10 12:01:07 htpc1 ir-keytable[661]: Protokolle geändert in rc-6
Mär 10 12:01:07 htpc1 systemd[1]: Started "Reload of my custom ir_keytable due to broken udev rule.".
```
Proof you key mapping using:
```
htpc1-user:/home/user> sudo ir-keytable -r
```

Implemented that way it doesn't depend on a very specific configuration, it does work with any later change in "rc_maps.cfg" and/or key mappings.

It also doesn't harm if the UDEV rule "/lib/udev/rules.d/60-ir-keytable.rules" will work again one day in the future ...

---


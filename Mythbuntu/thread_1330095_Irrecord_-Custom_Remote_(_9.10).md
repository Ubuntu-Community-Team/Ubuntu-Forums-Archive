---
title: "Irrecord -Custom Remote ( 9.10)"
date: 2009-11-18
forum: Mythbuntu
---

### Post by Chewiesw on 2009-11-18
I am trying to create a custom lircd.conf for my STB remote that I plan to use in conjunction with my IR Transmitter. Below is my /lirc/hardware.conf

```
/etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev lirc_mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""
 
#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Sky Satellite Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_mceusb2"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="sky/general.conf"
TRANSMITTER_LIRCD_ARGS=""
```

This is the command I am using:

root@pvrbox:~# irrecord --driver=devinput --device=/dev/lirc0 ~/lircdtest2.conf

I then get asked to "Hold down an arbitrary button"

I then get loads of the the following errors.

```
irrecord: error reading '/dev/lirc0'
.irrecord: error reading '/dev/lirc0'
irrecord: error reading '/dev/lirc0'
.irrecord: error reading '/dev/lirc0'
.irrecord: error reading '/dev/lirc0'
.irrecord: error reading '/dev/lirc0'
irrecord: error reading '/dev/lirc0'
.irrecord: error reading '/dev/lirc0'
..irrecord: error reading '/dev/lirc0'
irrecord: error reading '/dev/lirc0'
irrecord: error reading '/dev/lirc0'
.irrecord: error reading '/dev/lirc0'
..irrecord: error reading '/dev/lirc0'
```
 
Then finally

Found gap length: 2985
Now enter the names for the buttons

After entering all the names for all the buttons. I finally have a lircdtest2.conf. **BUT** it is all wrong, see below. Most of the buttons have excatly the same values.

```
begin remote
 
  name  /root/lircdtest2.conf
  bits           16
  eps            30
  aeps          100
 
  one             0     0
  zero            0     0
  post_data_bits  16
  post_data      0x0
  gap          2985
  toggle_bit_mask 0x0
 
      begin codes
          key_1                    0x02EE
          key_2                    0x02EE
          key_3                    0x02EE
          key_4                    0x0320
          key_5                    0x02EE
          key_6                    0x02BC
          key_7                    0x02EE
          key_8                    0x02EE
          key_9                    0x02EE
          key_0                    0x02EE
          key_volumeup             0x02EE
          key_volumedown           0x02EE
          key_mute                 0x0320
          key_left                 0x02EE
          key_right                0x02EE
          key_up                   0x02BC
          key_down                 0x02EE
          key_play                 0x02EE
          key_pause                0x02EE
          key_rewind               0x02EE
          key_stop                 0x02BC
          key_forward              0x02EE
          key_record               0x02EE
          key_channelup            0x0320
          key_channeldown          0x02BC
          key_exit                 0x02EE
          key_info                 0x02BC
      end codes
 
end remote
```

What amd I doing wrong and I also need to know if I am using the right IR Transmitter. I have a MCE usb remote RC6 (pvr 150).

---

### Post by azmyth on 2009-11-18
I'm not familiar with the remote but from looking at the sample devinput.conf it says it was generated with devinput.sh versus irrecord.

[http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput)

---

### Post by concordfta on 2009-11-18
did you try /dev/lirc/0 instead of /dev/lirc0 ??

---

### Post by Chewiesw on 2009-11-20
> **azmyth said:**
> I'm not familiar with the remote but from looking at the sample devinput.conf it says it was generated with devinput.sh versus irrecord.

[http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput](http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput)

I don't understand is there a difference between devinput.sh and irrecord? what should the command be if I want to use irrecord.

---

### Post by concordfta on 2009-11-20
can you do a:

ls /dev/lirc*

and list that...

---

### Post by Chewiesw on 2009-11-23
> **concordfta said:**
> can you do a:

ls /dev/lirc*

and list that...

root@pvrbox:~# ls /dev/lirc*
/dev/lirc0 (in yellow)

root@pvrbox:~# cd /dev/lirc0 
-bash: cd: /dev/lirc0: Not a directory

root@pvrbox:~# ls -l /dev/lirc*
crw-rw-rw- 1 root root 61, 0 2009-11-23 10:11 /dev/lirc0

---


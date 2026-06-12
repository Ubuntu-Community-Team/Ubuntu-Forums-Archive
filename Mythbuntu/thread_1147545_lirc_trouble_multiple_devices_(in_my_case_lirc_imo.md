---
title: "lirc trouble: multiple devices (in my case lirc_imon and Commandir II)"
date: 2009-05-03
forum: Mythbuntu
---

### Post by rune.evjen on 2009-05-03
Note: This problem is now solved, see last post in thread

Hardware setup:

- lsusb excerpt:
Bus 002 Device 003: ID 10c4:0003 Cygnal Integrated Products, Inc. 
Bus 003 Device 002: ID 15c2:0038 SoundGraph Inc.            

1st device is a commandir II, second is a lcd panel in an Antec Black Media Centre cabinet, which uses the lirc_imon driver.

- uname -a
Linux m-stue 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux (jaunty)

What is working: With the Commandir PPA lirc package, the Commandir II device works fine, but unfortunately it seems that my Soundgraph LCD device (which needs lirc_imon module) is not working.

But after reading this post: [http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2008/10/8_LIRC_to_work_with_Antec_Fusion_Remote_Black.html](http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2008/10/8_LIRC_to_work_with_Antec_Fusion_Remote_Black.html)
and patching the lirc source, I am able to modprobe lirc_imon, restart lirc, restart gdm and get a fully-funtional mythfrontend with commandir as well as getting the LCD device to display useful information using LCDd and lcdproc.

So all is well until a reboot.
After reboot the same lircd instances is started by the init script, the lirc_imon and lcdproc is working but the commandir is not working.
Starting irw from the command line gives no commandir response.

ps aux | grep lirc gives (both before reboot where everything is working and after reboot):

root     19059  0.0  0.0   3116   696 ?        S<s  20:59   0:00 /usr/sbin/lircd --driver=commandir --device=/dev/lirc0 --output=/dev/lircd --listen
root     19064  0.0  0.0   3164   788 ?        S<s  20:59   0:00 /usr/sbin/lircd --driver=commandir --output=/dev/lircd1 --connect=localhost 8765 --pidfile=/var/run/lircd1.pid
root     19065  0.1  0.0   3116   696 ?        S<   20:59   0:00 /usr/sbin/lircd --driver=commandir --device=/dev/lirc0 --output=/dev/lircd --listen

So what is happening ? 

This is reproducible, removing lirc-modules-source, reinstalling lirc, reinstalling the source and patching it and doing a modprobe and restarting lirc gives a working setup again until the next reboot.

Can anybody help with getting the two lirc devices working again ?

Regards,

Rune

---

### Post by rune.evjen on 2009-05-04
After reviewing my lirc processes, I adjusted my /etc/lirc/hardware.conf to the following:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CommandIR Multi-IR Transceiver (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Soundgraph iMon IR/LCD"
TRANSMITTER_MODULES="lirc_dev lirc_imon"
TRANSMITTER_DRIVER="default"
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_LIRCD_CONF="/etc/lirc/lirc1.conf"
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

This resulted in the following lircd processes:
```
root      5230  0.0  0.0   3116   668 ?        Ss   23:46   0:00 /usr/sbin/lircd --driver=commandir --device=/dev/lirc0 --output=/dev/lircd --listen
root      5232  0.0  0.0   3116   720 ?        S    23:46   0:00 /usr/sbin/lircd --driver=commandir --device=/dev/lirc0 --output=/dev/lircd --listen
root      5236  0.0  0.0   3116   596 ?        Ss   23:47   0:00 /usr/sbin/lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid
```

This seems more accurate, as the driver argument for the second remote (or lcd device) should not be commandir. Note that even though there are two lirc processes for commandir, I only started one instance of lirc for commandir!

But still, the setup is not working, commandir does not seem to respond (red diode on device, no response from irw).

After manually stopping lirc and starting the first process (i.e /usr/sbin/lircd --driver=commandir --device=/dev/lirc0 --output=/dev/lircd --listen ) commandir responds to irw. If I then either starts the second lirc process (i.e root      5236  0.0  0.0   3116   596 ?        Ss   23:47   0:00 /usr/sbin/lircd --driver=default --device=/dev/lirc1 --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid) OR restarts gdm which autostarts mythtv-frontend, commandir no longer responds to irw (and does not work in mythtv).

Can anybody spot the configuration error ? Or is there an issue with using commandir with a userspace driver and the lirc_imon device together ?

Rune

---

### Post by rune.evjen on 2009-05-04
I realize answering myself twice seems strange, but anyway:

Ater testing som more and googling I came along this post:

I then tested manually using these commands:
```
sudo /usr/sbin/lircd --driver=commandir --device=/dev/lirc --pidfile=/var/run/lirc.pid --listen=9988
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --listen=9987
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lirc0.pid --connect=localhost:9988 --connect=localhost:9987
```


This led to the following output of ps aux | grep lirc:
```
root      6536  0.0  0.0   3116   696 ?        Ss   00:15   0:00 /usr/sbin/lircd --driver=commandir --device=/dev/lirc --pidfile=/var/run/lirc.pid --listen=9988
root      6538  0.0  0.0   3116   720 ?        S    00:15   0:00 /usr/sbin/lircd --driver=commandir --device=/dev/lirc --pidfile=/var/run/lirc.pid --listen=9988
root      6540  0.0  0.0   3116   664 ?        Ss   00:16   0:00 /usr/sbin/lircd --driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --listen=9987
root      6681  0.0  0.0   3164   816 ?        Ss   00:17   0:00 /usr/sbin/lircd --driver=default --device=/dev/lirc0 --output=/dev/lircd --pidfile=/var/run/lirc0.pid --connect=localhost 9988 --connect=localhost 9987
```

But it is still not working.

Any help appreciated.

Rune

---

### Post by phroman on 2009-05-04
Ok, this is a long shot but check your /etc/lirc/lircd.conf file.  I noticed that you must list the devices here in the same order as you do in your /etc/lirc/hardware.conf file.  ie. first your remote, and then your blaster, or however you have things arranged.  For me, if I don't order them this way, nothing works.  I'm researching a semi-similar problem, so I'll post back if I find anything.  Good luck.

---

### Post by rune.evjen on 2009-05-12
After getting support from the commandir vendor, I added the following to /etc/modprobe.d/blacklist.conf:
```

blacklist commandir
blacklist lirc_cmdir
```

This solved the problem with my commandir in conjuction with the lirc_imon kernel module.

The setup now works using the following lirc commands:
```
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc0 --pidfile=/var/run/lirc0.pid --listen=9988 /etc/lirc/lirc0.conf
sudo /usr/sbin/lircd --driver=default --device=/dev/lirc1 --pidfile=/var/run/lirc1.pid --listen=9987 /etc/lirc/lirc1.conf
sudo /usr/sbin/lircd --driver=commandir --device=/dev/lirc  --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:9988 --connect=localhost:9987 /etc/lirc/lircd.conf
```

Rune

---

### Post by SiliconFiend on 2009-05-28
I have nearly the same setup (lirc_imon with a CommandIR II) but I can't get this to work. I'm using lirc 0.8.5 as the CommandIR II website recommends. I don't have those blacklisted kernel modules anywhere but I keep getting an extra instance of lircd running anyway. Could you post more details of your config, like what's in your lirc0.conf, lirc1.conf and lircd.conf? Also, what's attached to /dev/lirc1? (I assume your imon is on /dev/lirc0). I'm running Gentoo so I don't have an /etc/lirc/hardware.conf but it just looks like a control file for the lircd service control script.

---

### Post by rune.evjen on 2009-05-28
> **SiliconFiend said:**
> I have nearly the same setup (lirc_imon with a CommandIR II) but I can't get this to work. I'm using lirc 0.8.5 as the CommandIR II website recommends. I don't have those blacklisted kernel modules anywhere but I keep getting an extra instance of lircd running anyway. Could you post more details of your config, like what's in your lirc0.conf, lirc1.conf and lircd.conf? Also, what's attached to /dev/lirc1? (I assume your imon is on /dev/lirc0). I'm running Gentoo so I don't have an /etc/lirc/hardware.conf but it just looks like a control file for the lircd service control script.


My working setup:
lirc0.conf 

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4(default) on Sat Oct 18 02:21:26 2008
#
# contributed by Jean-Yves Avenard
#
# brand:                       Antec Fusion Remote
# model no. of remote control: MX200
# devices being controlled by this remote:
#

begin remote

  name  mx200
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          195997
  toggle_bit   0

      begin codes
          Up                       0x1008000
          Left                     0x1000080
          Right                    0x100007F
          Down                     0x1007F00
          Enter                    0x2000028
          LClick                   0x1010000
          RClick                   0x1020000
          ESC                      0x2000029
          1                        0x200001E
          2                        0x200001F
          3                        0x2000020
          4                        0x2000021
          5                        0x2000022
          6                        0x2000023
          7                        0x2000024
          8                        0x2000025
          9                        0x2000026
          0                        0x2000027
          *                        0x2200025
          #                        0x2200020
      end codes

end remote
```

lircd1.conf
```

# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.4(default) on Sat Oct 18 02:21:26 2008
#
# contributed by Jean-Yves Avenard
#
# brand:                       Antec Fusion Remote
# model no. of remote control: MX200
# devices being controlled by this remote:
#

begin remote

  name  mx200
  bits           32
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  gap          195997
  toggle_bit	   0
      begin codes
          Button-                  0x01000000
          Button+                  0x00010000
          Play                     0x2A8115B7
          Record                   0x298115B7
          Eject                    0x29B195B7
          Rewind                   0x2A8195B7
          Pause                    0x2A9115B7
          Forward                  0x2B8115B7
          Prev                     0x2B9115B7
          Stop                     0x2B9715B7
          Skip                     0x298195B7
          Mute                     0x2B9595B7
          Timer                    0x2B8395B7
          AppExit                  0x288195B7
          Power                    0x289115B7
          Zoom                     0x29A595B7
          FullScreen               0x2AA395B7
          Go                       0x2AB195B7
          Switch                   0x2A9395B7
          Eject2                   0x299395B7
          AppLaunch                0x29B715B7
          Vol-                     0x28A595B7
          Vol+                     0x28A395B7
          Prog-                    0x288795B7
          Prog+                    0x289395B7
          Red                      0x2B8515B7
          Green                    0x299195B7
          Blue                     0x2BA115B7
          Yello                    0x28A515B7
          DVD                      0x29A395B7
          Menu                     0x2BA395B7
          Subtitle                 0x298595B7
          Audio                    0x2B8595B7
          Bookmark                 0x288515B7
          Thumbnail                0x2AB715B7
      end codes

end remote


```

/etc/lirc/lircd.conf includes all the remotes I use with commandir
I based my setup on the following:
- [http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2008/10/9_RM200_remote_with_LIRC.html](http://www.avenard.org/media/Patches_%26_Add-Ons/Entries/2008/10/9_RM200_remote_with_LIRC.html)
- [http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html](http://mythtvblog.blogspot.com/2008/04/getting-imon-0038-lcd-working-with-lirc.html)

In the last post, the IMON device is described:
> The iMON pad remote acts like a mouse/keyboard in addition to a remote. In the old version, it was my understanding that this was all handled through one LIRC device. However, the 0038 version splits it into 2 devices. All of the mouse/keyboard related keys come through the lirc0 device (the directional pad, left click, enter, the number button, ect....however NOT including the Mouse/Keyboard toggle button). Everything else comes through the lirc1 device (play, eject, colored buttons, zoom, etc...plus the Mouse/Keyboard toggle button). Finally, if you have front panel button, they will also come through the lirc1 device (at least they do on the DH-101).

So the IMON device is using both /dev/lirc0 and /dev/lirc1 in my setup.

I found that it was necessary to blacklist the "old" commandir modules, as otherwise these were loaded at startup (and unloaded again), and this messed up the commandir.

I am not using hardware.conf to setup the lirc, as the ubuntu setup only allows for 2 lirc devices and I need 3.

I have the modprobe setup and lirc setup as described in [http://ubuntuforums.org/showpost.php?p=7267904&postcount=5](http://ubuntuforums.org/showpost.php?p=7267904&postcount=5), and all lirc devices is available through /dev/lircd

With this setup, the commandir works as well as all the buttons on the  imon remote as well as the volume knob.

Best Regards,

Rune

---

### Post by SiliconFiend on 2009-05-30
Thanks for the reply. It turns out my problem was apparently a buggy USB on my Asus A8N-VM CSM motherboard. Putting the CommandIR II on a USB hub which was then plugged into the motherboard solved that Error -110 problem.

---


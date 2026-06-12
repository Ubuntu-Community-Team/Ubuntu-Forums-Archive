---
title: "Problems with configuring LIRC."
date: 2011-10-28
forum: Multimedia Software
---

### Post by Coctus on 2011-10-28
I got some problems with configuring lirc. I installed it from repository with no problems but I just don't get irw to work. It launches but gives no output.

I got responses if I hit the the remote control buttons with ```
sudo mode2
```

What is wrong with my system? I have Xubuntu 11.10 but it wasn't working on 11.04 either.

```
cocktus@cocktus-htpc:~$ dmesg |grep lirc
[   20.097484] lirc_dev: IR Remote Control driver registered, major 249
[   20.127941] lirc_serial: module is from the staging directory, the quality is unknown, you have been warned.
[   21.028060] lirc_serial: auto-detected active low receiver
[   21.028145] lirc_serial lirc_serial.0: lirc_dev: driver lirc_serial registered at minor = 0

```

```
cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Home-brew (16x50 UART compatible serial port)"
REMOTE_MODULES="lirc_dev lirc_serial"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
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

---

### Post by Jose Catre-Vandis on 2011-10-28
Could this be the problem?

TRANSMITTER="None"

---

### Post by Coctus on 2011-10-29
I do not have IR transmitter. I just have a remote control and a IR receiver.

---

### Post by dyathinkesaurus on 2011-10-29
Try installing the latest lirc codecs, see the link below.

[https://launchpad.net/~oferchen/+archive/xbmc-git/+sourcepub/1842903/+listing-archive-extra](https://launchpad.net/~oferchen/+archive/xbmc-git/+sourcepub/1842903/+listing-archive-extra)

After installing the codec you will be given the option of choosing your remote receiver.
Choose 'none' for transceiver

Depending on your remote, you may have to amend the key mapping afterwards.

I had a similar problem when looking for a way to remotely control XBMC.

---

### Post by s13_mills on 2011-10-29
Hi There,

What kind of remote are you using?

Do you get gibberish when you run irw and press buttons or nothing at all?

Can you run:

```
sudo ir-keytable
```

And then:

```
sudo ir-keytable -t
```

Press a few buttons and see if anything at all changes (it should, given that you got output with mode2).

Once you have done that it might just be a matter of picking the right remote from the rc_keymaps available in 11.10 and hopefully it will work!

---

### Post by Coctus on 2011-10-29
I'm using Logitech Harmony 515. Actually I just got irw to work. I didn't get output at all with irw but mode2 gave me some pulses when I pressed buttons of my remote control. But now it's working as I got my lircd.conf file set up properly.

After 8 freaking hours of configuring I finally got my remote control working with XBMC. Next time may be a little shorter. Thanks buddies!

---


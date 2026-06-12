---
title: "Should an MCE Blaster still work on 12.10?"
date: 2013-03-05
forum: Mythbuntu
---

### Post by acodring on 2013-03-05
Hi there,
I upgraded to 12.10 recently and have lost use of my MCE remote, and the blaster it came with.
I'm pretty sure it was partially working right after the upgrade, I saw the settop box having it's channel changed and I could drive my mythtv frontend.
Not long after the wheels fell off. I'm suspicious of the rc modules, but can't prove anything.
I've tried following various howto's but most do not mention the blaster. 
I did see glimmers of hope when trying ir-keytable to receive commands from the remote, but nothing from the blaster.
irsend throws various errors.

Any tips appreciated.

 
I'll post a bunch of relevant info below.

Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-25-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

2 packages can be updated.
0 updates are security updates.

Last login: Fri Jan 18 07:58:19 2013 from mythgym
acodring@mythbackend:~$ lsusb
Bus 001 Device 003: ID 2040:4902 Hauppauge HD PVR
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 004 Device 002: ID 0471:0815 Philips (or NXP) eHome Infrared Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
acodring@mythbackend:~$ lsmod | grep mce
ir_mce_kbd_decoder     12724  0 
rc_rc6_mce             12503  0 
mceusb                 17885  0 
rc_core                22331  11 ir_lirc_codec,ir_mce_kbd_decoder,ir_sanyo_decoder,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,rc_rc6_mc,mceusb
edac_mce_amd           23304  0 
acodring@mythbackend:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Linux input layer (/dev/input/eventX)"
REMOTE_MODULES=""
REMOTE_DRIVER="devinput"
REMOTE_DEVICE="/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Kuh5-event-if00"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="devinput/lircd.conf.devinput"
REMOTE_LIRCD_ARGS="--driver=devinput --device=/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Kuh5-event-if00"

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
#DISABLE_KERNEL_SUPPORT="true"

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
acodring@mythbackend:~$ irsend -LIST "" ""
irsend: invalid option -- 'L'
acodring@mythbackend:~$ ir-keytable -LIST "" ""
ir-keytable: invalid option -- 'L'
Try `ir-keytable --help' or `ir-keytable --usage' for more information.
acodring@mythbackend:~$ irsend LIST "" ""
irsend: could not connect to socket
irsend: Connection refused

---

### Post by acodring on 2013-03-06
Found this page and thought I'd hit the jackpot since it mentioned mce transmitter support:
[http://www.lirc.org/html/table.html](http://www.lirc.org/html/table.html)
Tried the settings there and only noticed it hadn't been updated in 4 years after lircd failed to load again.

Then this para:
> Note: Originally there were two modules lirc_mceusb and lir_mceusb2. These were later merged into a single lirc_mceusb driver. More recently (2.6.35 kernel and lirc-0.8.7) the module was known as just mceusb. You need to adjust all the configuration examples below depending on exactly how the module is named.
from [here]("http://www.mythtv.org/wiki/MCE_Remote") sounded very helpful. I'd been there before but didn't notice it covered transmit too.

Based on that I disabled the in kernel support, used mceusb as module, removed the crazy 'event'/ir-keytable stuff, and explicitly set lirc args.

Restarted lirc service, tried "irsend SEND_ONCE SAE8000 ch+" and didn't get an error. I also got a yell from my wife in the next room - "who changed the channel?!?" - so I'm optimistic I've moved things forward.
Will need to wait until I can get back to the TV to test fully.

Current hardware.conf:
acodring@mythbackend:$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Microsoft Windows Media Center V2 (usb) : Remote"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="--driver=default --device=/dev/lirc0"

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER="default"
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS="--driver=default --device=/dev/lirc1"

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
DISABLE_KERNEL_SUPPORT="true"

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

---

### Post by acodring on 2013-03-09
Harumpf.
Sorry to troubleshoot out loud...

I can get it to work, but it doesn't survive a reboot yet.

After reboot I need to:

```
sudo chmod 666 /dev/lirc0
sudo service lirc restart
irw
```
[a few key presses]
[exit mythfrontend, relaunch it]

All good until next reboot - both the blaster and remote work.

A next step for me is to figure out where the /dev/lirc0 device creation is controlled. Maybe udev?

Lirc devices:
```
acodring@mythbackend:~$ ls -al /dev/li*
crw-rw-rw- 1 root root 250, 0 Mar  8 08:05 /dev/lirc0
lrwxrwxrwx 1 root root     19 Mar  8 08:10 /dev/lircd -> /var/run/lirc/lircd
lrwxrwxrwx 1 root root     20 Mar  8 08:10 /dev/lircd1 -> /var/run/lirc/lircd1

```
Current hardware.conf:
```
acodring@mythbackend:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Microsoft Windows Media Center V2 (usb) : Remote"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER="default"
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="--driver=default --device=/dev/lirc0"

#Chosen IR Transmitter
TRANSMITTER="Microsoft Windows Media Center V2 (usb) : Scientific Atlanta Cable box"
TRANSMITTER_MODULES="lirc_dev mceusb"
TRANSMITTER_DRIVER="default"
TRANSMITTER_DEVICE="/dev/lirc1"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="scientificatlanta/general.conf"
TRANSMITTER_LIRCD_ARGS="--driver=default --device=/dev/lirc1"

#Disable kernel support.
#Typically, lirc will disable in-kernel support for ir devices in order to
#handle them internally.  Set to false to prevent lirc from disabling this
#in-kernel support. 
DISABLE_KERNEL_SUPPORT="true"

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

### Post by donb21 on 2013-03-10
I just finished getting my mce-usb to work on 12.04 (I had a completely different problem); I ran across a couple of threads claiming an upgrade broke lirc (not sure which version they applied-to).  People were unintalling and reinstalling lirc to fix it.  Also, this thread talks about changes in 0.26; might be worth a quick look.

[http://www.mythtv.org/wiki/LIRC#Ubuntu](http://www.mythtv.org/wiki/LIRC#Ubuntu)


Excerpt:
[COLOR=#000000][FONT=sans-serif]As of 2.6.36, some infrared receiver drivers have been removed from LIRC and into the kernel. The following drivers are no longer available in lirc:[/FONT][/COLOR]

[LIST]
[*]mceusb
[*]streamzap
[*]it8x
[*]ene0100
[/LIST]

---

### Post by acodring on 2013-03-16
Thanks for chiming in donb21. I am using the mceusb module. It's not in lirc now, but it's built into the kernel directly now.

I'm always hesitant to do a victory lap with my linux configurations, but I think I've resolved my issue.
I won't say I've figured it out, because I don't know why it worked.

I considered messing with udev, but couldn't figure out which device names to use.
Then I tried blacklisting a few ir_ and rc_ modules. 

In the end it was simpler. 
I saw a few people talking about start order of lirc and inputlirc services causing problems and inconsistencies.
Above I mentioned that restarting lirc worked, so I added "service lirc restart" to /etc/rc.local and confirmed the rc.local file was executable.

Now both the remote control and rc blaster work after reboot. Well, it's survived two reboots anyway...

---

### Post by acodring on 2013-03-30
After a quiet week of proper IR blasting I accidentally booted into a different kernel and the wheels fell off again. It wouldn't work even when I went back to the correct kernel.

I struggled with it again for a while. I uninstalled inputlirc and lirc (including config files), then reinstalled lirc but I think what got it working again was a few "sudo rmmod" of mceusb, rc_rc6_mce, maybe others. Then a "sudo modprobe mceusb" and a reboot. I did not end up needing to edit the hardware.conf files at all - the defaults work fine.

I really wish there was a little less black art voodoo required... :-)

---


---
title: "irblaster stopped working after Maverick upgrade"
date: 2010-10-30
forum: Mythbuntu
---

### Post by mocha on 2010-10-30
I have a generic IR blaster hooked to my serial port (ttyS0) that's been working for years with Ubuntu and lirc.  I only use the blaster, no other remote controls.

I'm confused about these new lirc changes.  Which module(s) are supposed to be loaded for an IR blaster serial device?  If lirc_serial is no longer used, then why does dpkg-reconfigure lirc put "lirc_serial" back into the TRANSMITTER_MODULES line of the config file?!?

When I load lirc_serial, it creates a /dev/lirc0 and irsend commands go though without error, but it doesn't actually send IR out of the device.  If I blacklist lirc_serial, then /dev/lirc0 doesn't get created and irsend errors out.

Any tips would be appreciated.

/etc/lirc/hardware.conf
```
REMOTE="None"
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"[COLOR="Red"]  #Why does reconfiguring lirc put lirc_serial here?!?[/COLOR]
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="directtv/general.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
```

lsmod |grep lirc  [COLOR="Red"]#This is with lirc_serial blacklisted[/COLOR]
```
ir_lirc_codec           3092  0 
lirc_dev                9393  1 ir_lirc_codec
ir_core                14654  8 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,bttv,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,ir_common
```

ls -al /dev/lir*  [COLOR="Red"]#This is with lirc_serial blacklisted[/COLOR]
```
lrwxrwxrwx 1 root root 19 2010-10-30 17:42 /dev/lircd -> /var/run/lirc/lircd
```

---

### Post by syphr42 on 2010-10-31
I'm having the same issue. Unfortunately, I don't have much help at this point, but there does appear to be a bug filed for the problem: [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663497](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/663497)

---

### Post by mocha on 2010-11-01
It seems like this one is also relevant, [https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512]("https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/655512")  I don't get a /dev/lirc0 device either even though I'm only dealing with a blaster rather than a receiver.

---

### Post by mocha on 2010-11-02
I got it working.  Keep in mind this is for a serial port IR blaster setup only, but I'm sure a similar procedure will work for a remote receiver.  The general procedure is rather simple:

Install lirc-modules-source.
Setup /etc/lirc/hardware.conf to load the modules.
Reboot.

/etc/lirc/hardware.conf

```
REMOTE=""
REMOTE_MODULES=""
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS=""
TRANSMITTER="Serial Port (UART) : Direct TV Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES="true"
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

```

This procedure escentially causes only lirc_dev and lirc_serial modules to load.  Those new lirc modules with names like ir_... don't load anymore.

My system is still trying to load the new ir_lirc_codec module but errors out on a symbol mismatch error, which is good in my case.  However I can't figure out what to blacklist to make this go away.  Blacklisting ir-lirc-codec or ir_lirc_codec doesn't have any effect.  Any thoughts would be appreciated.

---


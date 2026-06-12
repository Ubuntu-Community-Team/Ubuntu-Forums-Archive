---
title: "MCE Remote lirc 11.10"
date: 2012-04-13
forum: Mythbuntu
---

### Post by Crowie on 2012-04-13
After an upgrade to mythtv 0.25 I later upgraded mythbuntu 11.10 from 11.04.

Since doing so ive been unable to get the mce remote (real mce not keyboard HID job) working.  Ive read a few comments about problems with lirc in this ubuntu release.

Does anyone know how to get this working or can point me in the right direction.

Ive tried reinstalling lirc, generating configs with mythbuntu control centre but no joy and I dont get any out put from irw.

Thanks

---

### Post by wyliecoyoteuk on 2012-04-13
try this:
[http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/](http://wyliecoyoteuk.wordpress.com/2012/01/30/how-to-forget-lirc-for-mythtv-remotes/)

---

### Post by Crowie on 2012-04-13
Cool thanks i'll have a go tommorow when my brains not frazzled.

Is this what we have to do now lirc is included in the kernel?

Is anywork being done on mythbuntu lirc generator?

---

### Post by wyliecoyoteuk on 2012-04-14
You can still use LIRC, but this seems like a more permanent solution to me, less hoops to jump through.
Eventually it will all "just work", I guess.

---

### Post by Crowie on 2012-04-14
I had a go at this but wasnt able to get any output from the remote if i did ir-keytable -t

Oddly enough the remote started working this morning with LIRC and mythtv.  Tested with irw and I have output  But after a hard reboot it fails to work again.

I dont know if a module is failing to load or not loading in the correct order.

Or possibly the device location changes /dev/input/event*

---

### Post by Crowie on 2012-04-14
If found that if the mce remote gets mapped to /sys/class/rc/rc0/ it works fine (regardless of /dev/input/event* number although it usually gets mapped to event4)
I tried the command

```
sudo sed -i '$i echo lirc > /sys/class/rc/rc0/protocols' /etc/rc.local

```

and even tried that for rc1 but it makes no difference.  Is there a way to permanently map the mce to rc0.  Alternatively disable the hauppauge which is a usb tv tuner with remote sensor built in.

When it doesnt work:

```
shabba@shabba:~$ ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
	Driver cx88xx, table rc-hauppauge
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
Found /sys/class/rc/rc1/ (/dev/input/event4) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
```

When it does work:

```
shabba@shabba:~$ ir-keytable
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>
Found /sys/class/rc/rc1/ (/dev/input/event5) with:
	Driver cx88xx, table rc-hauppauge
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: LIRC 
	Extra capabilities: <access denied>

```

```
shabba@shabba:~$ ls /dev/lirc*
/dev/lirc0  /dev/lirc1  /dev/lircd
```

Modules appear to be loading to

```
lsmod | grep mceusb
mceusb                 17602  0 
rc_core                25797  13 rc_hauppauge,rc_rc6_mce,dvb_usb,mceusb,ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,cx88xx
```

---

### Post by Crowie on 2012-04-14
ok getting somewhere

/sys/class/rc/rc0/ and /sys/class/rc/rc1/ uses lirc0 and lirc1 respectively.

in my hardware.conf

```
REMOTE_DEVICE="/dev/lirc0"

```

If the remote doesnt work as its against rc1, If I change to lirc1 and restart lirc the remote workss fine.

Im a bit out of my depth here.  Does anyone have any ideas how to get this to work permanently on each reboot.

Thanks for your help

---

### Post by nickrout on 2012-04-14
udev rules?

---

### Post by wyliecoyoteuk on 2012-04-14
Oddly enough, I have a similar setup, and both remotes work.
The first is the MCE remote (attached to a USB combined wifi/ir/bluetooth/LCD display), is using the mceusb driver and the RC-6 protocol.
The second is my Hauppuage remote, which is not using a driver at all, using RC-5 and basically functions as a keyboard.

ir-keytable -t only reports the MCE events, the others actuall function as the relevant keys.

```
lee@media1:~$ sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event5) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC 
	Enabled protocols: RC-6 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event7) with:
	Driver (null), table rc-dib0700-rc5
	Supported protocols: NEC RC-5 RC-6 
	Enabled protocols: RC-5 
	Repeat delay = 500 ms, repeat period = 125 ms

```

I am sure that was not the case when I set it up, as I used ir-keytable -t to check the scancodes on the Hauppuage.
So it would seem that the two have been swapped, but continued to work, so I didn't notice!

I do not have LIRC installed at all.

---

### Post by wyliecoyoteuk on 2012-04-14
> **nickrout said:**
> udev rules?
Yup, that would be the way to go.

I used to use this one to tie my hauppuage remote to /dev/input/irremote

added this line to /etc/udev/rules.d/60-symlinks.rules
```

# Create /dev/input/irremote symlink for Nova-T 500
KERNEL=="event*", ATTRS{name}=="IR-receiver inside an USB DVB receiver", SYMLINK+="input/irremote"

```

or you could blacklist the Hauppuage remote with a rule in /usr/share/hal/fdi/preprobe/20thirdparty

this makes the kernel ignore it, I think:
```

<?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="IR-Receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>

```

---

### Post by Crowie on 2012-04-14
Cheers for your help on this.  Ive done udev rules for my tv cards in the past to get them in the correct order and then pointed myth to the symlinks ie /dev/dvb/adapter100.  

However say we create a udev rule for the mce remote to /dev/input/irremote but how to I get that to stick to rc0?

Thanks again

lirc slowly loosing its appeal

---

### Post by Crowie on 2012-04-14
ok got it, then symlink /dev/input/irremote to /dev/input/event3 

Thanks for your help with this much appreciated :)

---

### Post by Crowie on 2012-04-14
Ok the udev rules doesnt seem to work.  How do i get this to stick to rc0 each time?  at present irremote seems to move to different event numbers in /dev/input/event*

---

### Post by wyliecoyoteuk on 2012-04-14
As I understand it, the udev rule looks for something in the kernel messages, and then whatever event the device is matched with is linked to /dev/irremote, which you then point lirc at in the hardware.conf.

so do a dmesg | grep mce, and you will see what can be used to match it.
the one I posted identifies the Hauppuage remote by the string 
"IR-receiver inside an USB DVB receiver"

---

### Post by Crowie on 2012-04-14
Sorry the udev rule works fine

```
udevadm info -a -p $(udevadm info -q path -n /dev/input/event3)
```

Gave me the info to setup the rule and it matches fine
 so I have /dev/input/irremote

Problem is there is no ouput if i put /dev/input/irremote in hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/irremote"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
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

but it works fine with /dev/lirc0 or whatever lirc1 - depending on what rc0 or rc1 it matches up to

As a side to this, the /usr/share/hal/fdi/preprobe/20thirdparty/lirc.fdi file does indeed block IR for lirc.  Ive noticed it is in fact not my usb tuner IR but the one on my cx88 nova-t pci tuner which is not being blocked for some reason.

```
?xml version="1.0" encoding="UTF-8"?>

<deviceinfo version="0.2">
  <device>
     <match key="info.product" contains_ncase="saa7134 ir">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="IR-Receiver">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="cx88 IR">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="bttv IR">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
     <match key="info.product" contains_ncase="Budget-CI dvb ir receiver saa7146">
        <merge key="info.ignore" type="bool">true</merge>
     </match>
  </device>
</deviceinfo>


```

---

### Post by dheianevans on 2012-04-16
Wylie,

Just started following this thread but have been reading your blog too.

Did these issues/changes just start in 11.10? As I mentioned on your blog, I just moved to 11.04 and my MCE programmed Harmony was just fine.

So am I correct in thinking I'll only have to face this moving to either 11.10 or 12.04? At least it gives me some breathing room.

---

### Post by wyliecoyoteuk on 2012-04-16
Yes, replied on the blog too.
As I recall, I had problems going from 10.10 to 11.10.
It does seem that some remotes now have LIRC kernel drivers, while others have not yet been transferred.
Not very satisfactory, but it is a transitional thing.

---

### Post by wyliecoyoteuk on 2012-04-16
For /dev/input/irremote to work, you need to specify

REMOTE_DRIVER="devinput"

Not sure, but you might have to stop the modules from loading as well.

---


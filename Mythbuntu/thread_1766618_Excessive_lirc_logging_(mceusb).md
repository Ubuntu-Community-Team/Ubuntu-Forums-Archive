---
title: "Excessive lirc logging (mceusb)"
date: 2011-05-24
forum: Mythbuntu
---

### Post by kilowhisky on 2011-05-24
For some reason lirc (or the drivers lirc_dev/mceusb) has been dumping constant crap into my log files. So much so that they are rotating out every few hours. I configured the remote with mythbuntu-control-centre and it works just fine but I can't seem to figure out how to quiet lirc down.
 
I get two types of log messages in my log file.  

This one just constantly appears in my log files. 

```
134658.219550] mceusb 4-2:1.0: processed IR data, calling ir_raw_event_handle
[134658.220537] mceusb 4-2:1.0: Storing pulse with duration 650000
[134658.220541] mceusb 4-2:1.0: Storing space with duration 500000

```

From what i can tell this type of log entry appears every time my ir receiver detects any type infrared signal.

```

May 20 09:26:47 MythTV kernel: [150610.670328] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll called
May 20 09:26:47 MythTV kernel: [150610.670333] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll result = 65
May 20 09:26:47 MythTV kernel: [150610.670354] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll called
May 20 09:26:47 MythTV kernel: [150610.670358] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll result = 65
May 20 09:26:47 MythTV kernel: [150610.670364] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll called
May 20 09:26:47 MythTV kernel: [150610.670369] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll result = 65
May 20 09:26:47 MythTV kernel: [150610.670375] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): read called
May 20 09:26:47 MythTV kernel: [150610.670380] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): read result = <ok> (0)
May 20 09:26:47 MythTV kernel: [150610.670387] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll called
May 20 09:26:47 MythTV kernel: [150610.670391] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll result = 65
May 20 09:26:47 MythTV kernel: [150610.670397] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): read called
May 20 09:26:47 MythTV kernel: [150610.670401] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): read result = <ok> (0)
May 20 09:26:47 MythTV kernel: [150610.670407] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll called
May 20 09:26:47 MythTV kernel: [150610.670412] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll result = 0


```

So far googling has come up with nothing on the matter. I've tried specifying the log file to go to /dev/null but it won't let me do that for some reason. I've also tried rebuilding the kernel modules for lirc. 

Here is my hardware.conf

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS="-r"

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

I am using the default mceusb config file at 
/usr/share/lirc/remotes/mceusb/lircd.conf.ceusb

---

### Post by novinick on 2011-05-24
modinfo lirc-sir

parm:           io:I/O address base (0x3f8 or 0x2f8) (int)
parm:           irq:Interrupt (4 or 3) (int)
parm:           threshold:space detection threshold (3) (int)
parm:           debug:Enable debugging messages (bool)

try to add debug parametar in /etc/modprobe.d/ to ... false ? or 0?

what exact to add ?
i do not have mceusb compiled currently
sometimes i have 
'lirc detected spike ' in logs

---

### Post by superm1 on 2011-05-24
both the modules used (mceusb) and (lirc-dev) support a debug parameter.  Did you ever turn them on?

---

### Post by kilowhisky on 2011-05-25
I did not turn them on but i did try turning them off by placing the file lirc_dev.conf under /etc/modprobe.d/

```
options lirc_dev debug=0
options mceusb debug=0
options lirc_mceusb debug=0

```

It does not appear this has done anything to help the issue.

---

### Post by ian dobson on 2011-05-26
Hi,

What do you see in dmesg for your remote? 

Regards
Ian Dobson

---

### Post by novinick on 2011-05-26
>  May 20 09:26:47 **MythTV kernel:** [150610.670369] rc rc0: lirc_dev (ir-lirc-codec (mceusb)[0]): poll result = 65hi , i just now noticed , this is not logged from linux kernel driver?
this header of line would be difrent if from kernel driver

this is from mythtv kernel, which resides in userspace , i would guess?

i might be wrong about this

there was also some paramater that sets verbosing of kernel debug in global level?

[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
[http://linux.die.net/man/8/klogd](http://linux.die.net/man/8/klogd)
[http://elinux.org/Kernel_Debugging_Tips#Log_levels](http://elinux.org/Kernel_Debugging_Tips#Log_levels)
i havent actually used this ooption
```
klogd
```

---

### Post by kilowhisky on 2011-05-26
> **ian dobson said:**
> Hi,

What do you see in dmesg for your remote? 

Regards
Ian Dobson

dmesg is constantly being overrun with the output i posted earlier but i also found this in the dmesg log. 

```
134658.219550][   29.844986] mceusb 4-2:1.0: mceusb_dev_probe called
[   29.844990] mceusb 4-2:1.0: acceptable outbound endpoint found
[   29.844992] mceusb 4-2:1.0: acceptable inbound endpoint found
[   29.892217] mceusb 4-2:1.0: receive request called (size=0x20)
[   29.892222] mceusb 4-2:1.0: receive request FAILED! (res=-22)
[   29.892224] mceusb 4-2:1.0: receive request called (size=0x20)
[   29.892226] mceusb 4-2:1.0: receive request FAILED! (res=-22)
[   29.892231] mceusb 4-2:1.0: receive request called (size=0x2)
[   29.892248] mceusb 4-2:1.0: receive request complete (res=0)
[   29.892250] mceusb 4-2:1.0: receive request called (size=0x20)
[   29.892255] mceusb 4-2:1.0: receive request complete (res=0)
[   29.892258] mceusb 4-2:1.0: receive request called (size=0x2)
[   29.892260] mceusb 4-2:1.0: receive request complete (res=0)
[   29.892262] mceusb 4-2:1.0: receive request called (size=0x20)
[   29.892264] mceusb 4-2:1.0: receive request FAILED! (res=-22)
[   29.892266] mceusb 4-2:1.0: receive request called (size=0x2)
[   29.892268] mceusb 4-2:1.0: receive request complete (res=0)
[   29.892270] mceusb 4-2:1.0: receive request called (size=0x20)
[   29.892272] mceusb 4-2:1.0: receive request FAILED! (res=-22)
[   29.892274] mceusb 4-2:1.0: receive request called (size=0x2)
[   29.892277] mceusb 4-2:1.0: receive request complete (res=0)
[   29.892278] mceusb 4-2:1.0: receive request called (size=0x20)
[   29.892280] mceusb 4-2:1.0: receive request FAILED! (res=-22)
[   29.892283] mceusb 4-2:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver on usb4:2
[   29.892329] usbcore: registered new interface driver mceusb
[   29.893018] mceusb 4-2:1.0: callback called (status=0 len=2)
[   29.894016] mceusb 4-2:1.0: callback called (status=0 len=2)
[   29.894022] mceusb 4-2:1.0: setup answer received 4 bytes
[   29.894024] mceusb 4-2:1.0: processed IR data, calling ir_raw_event_handle
[   29.895002] mceusb 4-2:1.0: callback called (status=0 len=2)
[   29.895008] mceusb 4-2:1.0: processed IR data, calling ir_raw_event_handle
[   29.895844] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   29.895848] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   29.895918] usbcore: registered new interface driver lirc_mceusb
[   29.896017] mceusb 4-2:1.0: callback called (status=0 len=2)
[   29.896027] mceusb 4-2:1.0: processed IR data, calling ir_raw_event_handle
[   29.897008] mceusb 4-2:1.0: processed IR data, calling ir_raw_event_handle

```

```
[   29.893819] lirc_dev: IR Remote Control driver registered, major 61 
[   29.895844] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   29.895848] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   29.895918] usbcore: registered new interface driver lirc_mceusb
[   29.954556] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[   29.954754] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[   29.954835] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[   29.954838] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[   29.954941] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[   29.955022] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[   29.955092] ir_lirc_codec: disagrees about version of symbol lirc_register_driver
[   29.955094] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[   29.955262] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)

```


novinick, MythTV is the hostname for my system. Is that what you are talking about? 
 I will investigate klogd but i don't think it will help me much.

---

### Post by ian dobson on 2011-05-26
Hi,

This to me looks really strange

```

[   29.893819] lirc_dev: IR Remote Control driver registered, major 61 
[   29.895844] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
[   29.895848] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dconti@acm.wwu.edu>
[   29.895918] usbcore: registered new interface driver lirc_mceusb
[   29.954556] ir_lirc_codec: Unknown symbol lirc_dev_fop_poll (err 0)
[   29.954754] ir_lirc_codec: Unknown symbol lirc_dev_fop_open (err 0)
[   29.954835] ir_lirc_codec: disagrees about version of symbol lirc_get_pdata
[   29.954838] ir_lirc_codec: Unknown symbol lirc_get_pdata (err -22)
[   29.954941] ir_lirc_codec: Unknown symbol lirc_dev_fop_close (err 0)
[   29.955022] ir_lirc_codec: Unknown symbol lirc_dev_fop_read (err 0)
[   29.955092] ir_lirc_codec: disagrees about version of symbol lirc_register_driver
[   29.955094] ir_lirc_codec: Unknown symbol lirc_register_driver (err -22)
[   29.955262] ir_lirc_codec: Unknown symbol lirc_dev_fop_ioctl (err 0)

```

It looks as if you have a missmatch somewhere in your driver/modules.

Regards
Ian Dobson

---

### Post by superm1 on 2011-05-26
You've got lirc-modules-source installed.  Remove it, it's not needed anymore.

---

### Post by kilowhisky on 2011-05-26
> **superm1 said:**
> You've got lirc-modules-source installed.  Remove it, it's not needed anymore.

I installed lirc-modules-source in order to try manually building the modules. I have since removed them and it hasn't done anything..

---


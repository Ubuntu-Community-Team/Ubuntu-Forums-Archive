---
title: "CommandIR on MythBuntu X64 -110 Problems"
date: 2009-07-27
forum: Mythbuntu
---

### Post by commandir on 2009-07-27
There's a recurring issue with CommandIR on MythBuntu 9.04 64 that I haven't been able to duplicate on my 64 system; hopefully a little discussion with the affected users can get us get to the core of the problem.

My Test system that Works run MythBuntu 9.04 AMD/64 on:

ASUS M2A-VM HDMI Motherboard

root@mythbuntu904amd64:/mnt/sda1/mattwork# more /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4400+
stepping        : 1
cpu MHz         : 2299.745
cache size      : 512 KB

root@mythbuntu904amd64:/mnt/sda1/mattwork# dpkg -s lirc|grep Version
Version: 0.8.4a-1ubuntu0

root@mythbuntu904amd64:/mnt/sda1/mattwork# more /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CommandIR Multi-IR Transceiver (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

What motherboards / CPU's are on the systems with -110 problems?  Does a USB hub solve it?

---

### Post by sadale_1270 on 2009-07-27
I'm not sure what -110 problem means, exactly.  I haven't seen any real error messages.  But I do know that I get no response from my CommandIR II on my mythbox.  It worked fine on my 8.04 x86 box, and my CommandIR Mini works on the x64 9.04 box, though it retains the problem I upgraded from in the first place, which is that sending an irsend to one transmitter actually sends it to all of the transmitters.

I have not tried a USB hub but will do so.

(Fixing either of these problems would solve me.)

I don't know what the mobo is off the top of my head, but it's an EVGA board and it has HDMI.

root@livingroom:~# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 107
model name      : AMD Athlon(tm) Dual Core Processor 4850e
stepping        : 2
cpu MHz         : 1000.000
cache size      : 512 KB

root@livingroom:~# dpkg -s lirc | grep Version
Version: 0.8.4a-1ubuntu0

root@livingroom:~# cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CommandIR Multi-IR Transceiver (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Motorola Cable box"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER="commandir"
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="/etc/lirc/lircd.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

### Post by commandir on 2009-07-27
-110 Is a USB level E_TIMEOUT error.  It happens when libusb can't get data from the target USB device within the timeout period, which includes:

* If the usb device is in use by another process
* If the usb device is in use by a kernel module (commandir.ko, old driver)
* If the program (lircd) doesn't have permission to access the usb device (rare, it's root on MythBuntu)
* If the USB hardware can see but not query the target usb device (some motherboards)

So there must be one more cause that I'm missing that is the problem on MythBuntu 9.04/64, because I know some people have gone through these three possibilities.

---

### Post by cwoodworth on 2009-07-27
I'm getting the -110 error which you can see when you launch lircd via "lircd --driver=commandir -n' and then run 'irw' in a separate terminal

Motherboard is an EVGA 680i SLI. I also tested on an EVGA 780i SLI and Intel E8400 with the same results.
I have tried using a USB hub but it didn't help. I'll try a powered USB hub next.

```

cwoodworth@htpc:~$ sudo lircd --driver=commandir -n
lircd-0.8.4a[24172]: lircd(commandir) ready
lircd-0.8.4a[24172]: accepted new client on /dev/lircd
lircd-0.8.4a[24172]: CommandIR driver initialized
lircd-0.8.4a[24174]: Child Initializing CommandIR Hardware
lircd-0.8.4a[24174]: Product identified as CommandIR II
lircd-0.8.4a[24174]: Unable to read version request - Is CommandIR busy? Error -110

```
```

cwoodworth@htpc:~$ dpkg -s lirc | grep Version
Version: 0.8.4a-1ubuntu0

```
```

cwoodworth@htpc:~$ more /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping        : 6
cpu MHz         : 2133.295
cache size      : 2048 KB

```
```

cwoodworth@htpc:~$ cat /etc/lirc/hardware.conf
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="CommandIR Multi-IR Transceiver (userspace)"
REMOTE_MODULES=""
REMOTE_DRIVER="commandir"
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Command IR : Dish Receiver"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="false"

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

### Post by sadale_1270 on 2009-08-02
It turns out that using a USB hub does indeed let me CommandIR II work.  However it occasionally stops responding until I unplug the USB and replug it. 

The hub I am using is currently an unpowered hub.  I may try a powered hub to see if it makes a difference.

Am I to understand that I would not be having these problems if I were running the 32-bit version?

---

### Post by cwoodworth on 2009-08-03
I tried another USB hub, powered and unpowered, with new USB cables and still have the same result.

If it's a motherboard specific issue, would installing a PCI, USB card help ([_like this one_]("http://www.monoprice.com/products/product.asp?c_id=103&cp_id=10304&cs_id=1030401&p_id=48&seq=1&format=2"))?

---

### Post by commandir on 2009-08-04
> **sadale_1270 said:**
> It turns out that using a USB hub does indeed let me CommandIR II work.  However it occasionally stops responding until I unplug the USB and replug it. 

The hub I am using is currently an unpowered hub.  I may try a powered hub to see if it makes a difference.

Am I to understand that I would not be having these problems if I were running the 32-bit version?

I have not heard of anyone with the problem on the 32-bit version, but also everyone with /64 hardware may just use the 64 bit version.


> **cwoodworth said:**
> I tried another USB hub, powered and unpowered, with new USB cables and still have the same result.

If it's a motherboard specific issue, would installing a PCI, USB card help ([_like this one_]("http://www.monoprice.com/products/product.asp?c_id=103&cp_id=10304&cs_id=1030401&p_id=48&seq=1&format=2"))?

I'm surprised the externally powered USB hub didn't work for you.  If it doesn't work, then I'd guess there's a different problem than the motherboard issue (or possibly that plus another).  

Is there anything else that could have possibly claimed the CommandIR as a USB device? I know you've eliminated the lirc_cmdir and commandir kernel modules, the usual culprits, and checked for stray lircd processes / zombie's.

---

### Post by cwoodworth on 2009-08-05
I've check for zombie processes with "ps -el | grep 'Z'" with nothing showing. How can I check for a stray lircd process? I've tried doing a "killall lircd", if that's even the proper way to kill a stray process.

---

### Post by dmcauslan on 2009-08-20
I'm seeing (what I think is) the same issue.  Did you find a fix?

---


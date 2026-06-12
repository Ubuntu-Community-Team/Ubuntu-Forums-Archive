---
title: "Modem doesn't work"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by RogerDavis on 2012-11-06
Modem info: (OBVIOUSLY FOUND...)
 *-pci 
description: PCI bridge 
product: Integrated Technology Express, Inc. 
vendor: Integrated Technology Express, Inc. 
physical id: 0 bus info: pci@0000:03:00.0 
version: 30 width: 32 bits clock: 33MHz 
capabilities: pci pm subtractive_decode bus_master cap_list 
resources: ioport:d000(size=4096) 
memory:f7d00000-f7dfffff 

  *-communication 
description: Serial controller product: 56K FaxModem Model 5610 
vendor: 3Com Corp, Modem Division 
physical id: 1 bus info: pci@0000:04:01.0 
version: 01 width: 32 bits clock: 33MHz 
capabilities: pm 16550 cap_list 
configuration: driver=serial latency=0 
resources: irq:17 ioport:d000(size=8 )

BUT
roger@roger-desktop:~$ sudo wvdialconf
[sudo] password for roger: 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.
Modem Port Scan<*1>: S0   S1   S2   S3   
ttyS4<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS4<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS4<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S5   S6   S7   S8   
Modem Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16  
Modem Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24  
Modem Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  
Sorry, NO MODEM WAS DETECTED!  Is it in use by another program?  -  (my caps)
Did you configure it properly with setserial?
Please read the FAQ at [http://alumnit.ca/wiki/?WvDial](http://alumnit.ca/wiki/?WvDial) (this gets me a blank page, but [http://wiki.debian.org/Wvdial](http://wiki.debian.org/Wvdial) at least loads, but no help.)

OK, so Ubuntu finds the modem, but doesn't find it !?!?!?  Which is correct ?!?

I'm almost ready to believe it's a kernel problem, except not by intent. I can't imagine anyone would intentionally screw that up thinking it's best for the world...

I'm NOT trying to connect to an ISP right now, I want to use it with eFax-GTK.  Later it would be good to reach an ISP if needed.

---

### Post by gregintexas on 2012-11-06
I don't think it's a kernel problem, per se'. I'm using a modem right now. It's a USB, not a serial, but still a modem. Network manager, unfortunately, doesn't deal with modems any more. You have to deal with it yourself. But you're not trying to reach an ISP anyway ...

---

### Post by RogerDavis on 2012-11-06
It worked on 12.04 before one of the later updates which included Ubuntu segments as well as others.  Then it just quit...

So:
1) Why can Ubuntu find the modem, then can't?
2) ANY ideas on how to fix it?

---

### Post by gregintexas on 2012-11-07
Well ... can you tell where it is? IE, what tty it's assigned to, where in udev ... etc?

---

### Post by RogerDavis on 2012-11-07
I can see it's ttyS4 from other info I have.
----------------------------
roger@roger-desktop:~$ dmesg | grep tty gets
[ 0.000000] console [tty0] enabled
[ 1.448980] 0000:04:01.0: ttyS4 at I/O 0xd000 (irq = 17) is a 16550A
-------------------------
I'm not with the Ubuntu machine right now, I'll have to check the udev question tomorrow.  
----------------------------
Is there anything else you can point me to that would shed more light on this problem, so I can get even more info together?
----------------
Thanks!

---

### Post by Plumtreed on 2012-11-07
I'm not sure what you are trying to do but I used Sakis3g to sort out and resolve my USB broadband problems.........so far it has proven to be far more effective than any previous arrangement.

It may not be so 'automagical' but it is certainly rock solid!

Google it and how to do it....

---

### Post by RogerDavis on 2012-11-08
Regarding udev :
====================
I find this at /etc/udev/rules.d
-------
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:4d:7c:7b:eb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
-------
I guess this is my ethernet card?
==============
at /lib/udev I find no mention of a modem or serial, about 40 items present
/lib/udev/devices is empty
================

Does this mean Ubuntu is ignoring the modem?

If so, how do I wake it up?

---

### Post by RogerDavis on 2012-11-08
My modem is an internal serial device, so Sakis3g doesn't appear to be useful for that type of modem.

---

### Post by RogerDavis on 2012-11-08
lspci gets me :

04:01.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)

which is my modem.
================================
Also
roger@roger-desktop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/roger/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=roger)
roger@roger-desktop:~$ 

Note udev is listed here, but no modem
==================================================
roger@roger-desktop:~$ sudo lshw
[sudo] password for roger: 
roger-desktop             
    description: Desktop Computer
    product: (To be filled by O.E.M.)
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=desktop family=To be filled by O.E.M. sku=To be filled by O.E.M. uuid=876A4EBE-6FBD-11E1-BD11-0011118582DC
------------------- LOTS of other stuff between-----------------
*-pci
                description: PCI bridge
                product: Integrated Technology Express, Inc.
                vendor: Integrated Technology Express, Inc.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 30
                width: 32 bits
                clock: 33MHz
                capabilities: pci pm subtractive_decode bus_master cap_list
                resources: ioport:d000(size=4096) memory:f7d00000-f7dfffff
              *-communication
                   description: Serial controller
                   product: 56K FaxModem Model 5610
                   vendor: 3Com Corp, Modem Division
                   physical id: 1
                   bus info: pci@0000:04:01.0
                   version: 01
                   width: 32 bits
                   clock: 33MHz
                   capabilities: pm 16550 cap_list
                   configuration: driver=serial latency=0
                   resources: irq:17 ioport:d000(size=8 )

---

### Post by alexfish on 2012-11-08
winmodem , 

did you install third party software to enable this device prior to upgrading ?

if so then can try to reinstall the drivers. see what happens.

also noted;
  > Is it in use by another program?possible modem manager hanging on to the device.

from the terminal try
```
sudo killall modem-manager
```then call wvdial immediately
also check you are a member of dial out 
```
id
```
alexfish

---

### Post by RogerDavis on 2012-11-08
roger@roger-desktop:~$ sudo killall modem-manager
[sudo] password for roger: 
roger@roger-desktop:~$ wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
roger@roger-desktop:~$ 

There is a ttyS4  (0 bytes), shows root as owner - user

I am a member of dialout
roger@roger-desktop:~$ id
uid=1000(roger) gid=1000(roger) groups=1000(roger),0(root),1(daemon),4(adm),5(tty),6(disk),9(news),10(uucp),13(proxy),20(dialout),21(fax),22(voice),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),33(www-data),37(operator),39(irc),43(utmp),44(video),46(plugdev),100(users),107(scanner),109(lpadmin),113(netdev),124(sambashare),126(clamav),1001(earlleen)
roger@roger-desktop:~$

It seems to initialize the modem ok, and will answer an incoming call (can't check for connect, just a call), but not respond at all to any further commands or communication from the computer after initialization.

No third party software or drivers.

---

### Post by RogerDavis on 2012-11-09
Does this help any?
======================================
04:01.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01) (prog-if 02 [16550])
	Subsystem: 3Com Corp, Modem Division USR 56K Internal V92 FAX Modem (Model 5610)
	Flags: medium devsel, IRQ 17
	I/O ports at d000 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: serial
===========================================
Almost EVERYTHING in this long list shows "access denied"

---

### Post by alexfish on 2012-11-09
Looks like possible serial port permissions,

can try chmod command to set permisions 

EG:
```
chmod 555 /dev/ttyS0
```or whichever port the modem resides on
if this works then can write a udev rule to set permissions

also , are you calling wvdial from root ?

normally the PPD is set to use the serial ports,

so  also worth trying ppd direct to see what happens , this can be configured, from the terminal, 
```
sudo pppconfig
```note while configuring the ppd remember to set the user. in permissions

once configured then ppp can be called using the pon command

```
pon <your isp>
```alexfish

---

### Post by RogerDavis on 2012-11-09
- chmod 555 /dev/ttyS4   made no difference except to lock the port unless using sudo until restart, then no sudo needed.

- PPP does me no good, I'm not trying to get online with an ISP, just to talk to the modem, like in minicom or Efax-gtk.

- Right now, the modem just does not respond to input at all after initialization except to try to answer an incoming call.  No actions, no echo, no nothing...  

- I'm beginning to think something is goofy within the guts of Ubuntu.  Is there any way to refresh the serial code portions without reinstalling?

- Again, this modem works just fine on this same machine in Windoze, and is NOT a Winmodem, it's just like a Sportster except it's internal.

- How do I reinstall the modem in 12.04, except to physically remove and replace it?

---

### Post by alexfish on 2012-11-10
only thing can think of , look through the syslog to see if the device is been probed at boot and by what ,also try to see what state the ports are in , if seen as a modem then can us grep command, 

```
cat /var/log/syslog | grep modem
```

---

### Post by RogerDavis on 2012-11-10
roger@roger-desktop:~$ cat /var/log/syslog | grep modem
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  ModemManager (version 0.5.2.0) starting...
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin SimTech
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin MotoC
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Ericsson MBM
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin ZTE
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Linktop
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin AnyData
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Option High-Speed
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Wavecom
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Sierra
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Samsung
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Novatel
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Generic
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Huawei
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Longcheer
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin X22X
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Nokia
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Option
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  Loaded plugin Gobi
Nov  9 13:26:47 roger-desktop modem-manager[919]: <info>  (ttyS4) opening serial port...
Nov  9 13:26:47 roger-desktop NetworkManager[932]: <info> modem-manager is now available
Nov  9 13:26:59 roger-desktop modem-manager[919]: <info>  (ttyS4) closing serial port...
Nov  9 13:26:59 roger-desktop modem-manager[919]: <info>  (ttyS4) serial port closed
Nov  9 13:26:59 roger-desktop modem-manager[919]: <info>  (ttyS4) opening serial port...
Nov  9 13:27:05 roger-desktop modem-manager[919]: <info>  (ttyS4) closing serial port...
Nov  9 13:27:05 roger-desktop modem-manager[919]: <info>  (ttyS4) serial port closed
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  ModemManager (version 0.5.2.0) starting...
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin SimTech
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin MotoC
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Ericsson MBM
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin ZTE
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Linktop
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin AnyData
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Option High-Speed
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Wavecom
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Sierra
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Samsung
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Novatel
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Generic
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Huawei
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Longcheer
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin X22X
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Nokia
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Option
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  Loaded plugin Gobi
Nov  9 17:32:07 roger-desktop modem-manager[934]: <info>  (ttyS4) opening serial port...
Nov  9 17:32:07 roger-desktop NetworkManager[943]: <info> modem-manager is now available
Nov  9 17:32:19 roger-desktop modem-manager[934]: <info>  (ttyS4) closing serial port...
Nov  9 17:32:19 roger-desktop modem-manager[934]: <info>  (ttyS4) serial port closed
Nov  9 17:32:19 roger-desktop modem-manager[934]: <info>  (ttyS4) opening serial port...
Nov  9 17:32:25 roger-desktop modem-manager[934]: <info>  (ttyS4) closing serial port...
Nov  9 17:32:25 roger-desktop modem-manager[934]: <info>  (ttyS4) serial port closed
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  ModemManager (version 0.5.2.0) starting...
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin SimTech
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin MotoC
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Ericsson MBM
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin ZTE
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Linktop
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin AnyData
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Option High-Speed
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Wavecom
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Sierra
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Samsung
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Novatel
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Generic
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Huawei
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Longcheer
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin X22X
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Nokia
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Option
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  Loaded plugin Gobi
Nov  9 17:41:31 roger-desktop modem-manager[932]: <info>  (ttyS4) opening serial port...
Nov  9 17:41:31 roger-desktop NetworkManager[944]: <info> modem-manager is now available
Nov  9 17:41:43 roger-desktop modem-manager[932]: <info>  (ttyS4) closing serial port...
Nov  9 17:41:43 roger-desktop modem-manager[932]: <info>  (ttyS4) serial port closed
Nov  9 17:41:43 roger-desktop modem-manager[932]: <info>  (ttyS4) opening serial port...
Nov  9 17:41:49 roger-desktop modem-manager[932]: <info>  (ttyS4) closing serial port...
Nov  9 17:41:49 roger-desktop modem-manager[932]: <info>  (ttyS4) serial port closed
Nov 10 00:39:36 roger-desktop AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
Nov 10 00:39:41 roger-desktop AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Nov 10 00:42:07 roger-desktop AptDaemon: INFO: RemovePackages() was called: 'dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s'))'
Nov 10 00:42:08 roger-desktop AptDaemon.Worker: INFO: Committing packages: dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'modem-manager-gui')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
roger@roger-desktop:~$

---

### Post by RogerDavis on 2012-11-10
There is no third party software in use.

I am member of both dialout and dip as well as tty.

sudo killall modem-manager locks up minicom with a "Device or resource busy" unless I use sudo or reboot.

roger@roger-desktop:~$ sudo killall modem-manager
[sudo] password for roger: 
roger@roger-desktop:~$ minicom
minicom: cannot open /dev/ttyS4: Device or resource busy
roger@roger-desktop:~$ 

Either way, minicom still does NOTHING.

---


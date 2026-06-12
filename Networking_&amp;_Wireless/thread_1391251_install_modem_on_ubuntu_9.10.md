---
title: "install modem on ubuntu 9.10"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by tah_206207 on 2010-01-26
hello my dial up modem is motorola sm56
plz help me to install my modem on ubuntu 9.10
i can install this mode on ubuntu 8.10 and i can connect to internet with this modem on ubuntu 8.10 but i can install this modem on ubuntu 9.10 and when i want to connect to internet modem can't connect to internet and in the wvdial out write no carrier 
in the setup file of this modem on  ubuntu 8.10 there is a script that write these
```

taher@taher-desktop:~/Public/slamr-2.6.27-7-generic$ sudo ./setup
installing drivers for kernel version 2.6.27-7-generic
driver=slamr

Installing the Debian packages supporting autoloading
(Reading database ... 99833 files and directories currently installed.)
Preparing to replace sl-modem-daemon 2.9.10+2.9.9d+e-pre2-5ubuntu4 (using sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu4_i386.deb) ...
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Unloading modem driver from kernel ... slamr.
Unpacking replacement sl-modem-daemon ...
Setting up sl-modem-daemon (2.9.10+2.9.9d+e-pre2-5ubuntu4) ...
The system user `Slmodemd' already exists. Exiting.
update-rc.d: warning: /etc/init.d/sl-modem-daemon missing LSB style header
Starting SmartLink Modem driver for: slamr0.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.


Copying over newer files
Making folder /lib/modules/2.6.27-7-generic/extra
Copying drivers to /lib/modules/2.6.27-7-generic/extra
Checking driver install
slamr.ko  ungrab-winmodem.ko
Copying newer slmodemd to /usr/sbin/
Checking slmodemd version. Should be 2.9.11
SmartLink Soft Modem: version 2.9.11 Apr 26 2009 23:23:54
Finished installs.
Informing the System

Starting function tests, loading drivers:
Running diagnostic:

[ 1515.093678] slamr: module license 'Smart Link Ltd.' taints kernel.
[ 1515.109102] slamr: SmartLink AMRMO modem.
[ 1515.110067] slamr: probe 1057:3052 SL1900 card...
[ 1515.110129] slamr 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1515.386405] slamr: slamr0 is SL1900 card.
[ 1832.247597] slamr 0000:00:0a.0: PCI INT A disabled
[ 1834.577013] slamr: SmartLink AMRMO modem.
[ 1834.581246] slamr: probe 1057:3052 SL1900 card...
[ 1834.581395] slamr 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 1834.674402] slamr: slamr0 is SL1900 card.
echo  "ports should be created by:"
echo slmodemd -c USA /dev/slamr0
/usr/sbin/slmodemd -c USA /dev/slamr0

echo "Checking for success"
if test -L /dev/ttySL0 ; then
  echo Running wvdialconf
  wvdialconf  /etc/wvdial.conf
  if [ -f /etc/wvdial.conf ] ; then
    echo Modem detection successful
    sleep 2
    echo "Carrier check = no" >>  /etc/wvdial.conf
    echo "Read wdial.txt"
    echo "Then edit /etc/wvdial.conf  with:"
    echo "sudo gedit /etc/wvdial.conf"
    echo "at the lines beginning with ; and deleting the ; < >  "
    echo "Then dialout with:"
    echo "    sudo wvdial"
    echo "Running setup again is NOT necessary. Only for dialout the:"
    echo "    sudo wvdial"
  else
    echo "wvdialconf failed"
  fi
else
  echo "Port creation with slmodemd failed."
fi
echo "Read the Slamr.txt record, other *.txt files and the sample wvdial.conf ."
echo
# END


```
in this script there is a line that says  echo "Carrier check = no" >>  /etc/wvdial.conf but in the setup file of this modem on ubuntu 9.10 don't check these.
i download my modem drivers from :
[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/)
in the link follow what ungrub is for ubuntu 9.10?
[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
plz help me to install my modem on ubuntu 9.10
THX

---

### Post by t4thfavor on 2010-01-26
Give this a read, he managed to get it working just yesterday.

[http://ubuntuforums.org/showthread.php?t=1383273](http://ubuntuforums.org/showthread.php?t=1383273)

---

### Post by tah_206207 on 2010-01-26
Note that i say i can install my modem on ubuntu 9.10 but i can't to use my modem to connect to internet when i want to connect to internet the error was occoured is no carrier
how can i to solve this problem?
this following code :
```

aher@taher-desktop:~$ sudo plog
Jan 11 06:01:33 taher-desktop chat[4293]: send (ATDT9715302^M)
Jan 11 06:01:33 taher-desktop chat[4293]: expect (CONNECT)
Jan 11 06:01:33 taher-desktop chat[4293]: ^M
Jan 11 06:01:33 taher-desktop chat[4293]: ATDT9715302^M^M
Jan 11 06:01:33 taher-desktop chat[4293]: NO CARRIER
Jan 11 06:01:33 taher-desktop chat[4293]:  -- failed
Jan 11 06:01:33 taher-desktop chat[4293]: Failed (NO CARRIER)
Jan 11 06:01:33 taher-desktop pppd[4291]: Script /usr/sbin/chat -v -f /etc/chatscripts/isp finished (pid 4292), status = 0x5
Jan 11 06:01:33 taher-desktop pppd[4291]: Connect script failed
Jan 11 06:01:34 taher-desktop pppd[4291]: Exit.
taher@taher-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Modem: Motorola SM56 Data Fax Modem (rev 04)
00:0b.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


```

---

### Post by tah_206207 on 2010-01-28
Hello i installed my modem on ubuntu 9.10 and install wvdial 
```

taher@taher-desktop:~/Public/Programs/slamr-2.6.31-14-generic$ sudo ./setup
installing drivers for kernel version 2.6.31-14-generic

LogFile created
installing drivers for kernel version 2.6.31-14-generic

Writing record to ./Slamr.txt
    Installing the Debian packages supporting autoloading: sl-modem-daemon 

Copying over newer files
Making folder /lib/modules/2.6.31-14-generic/extra
Copying drivers to /lib/modules/2.6.31-14-generic/extra
Checking driver installs for slamr.ko and ungrab-winmodem.ko
slamr.ko
ungrab-winmodem.ko
Checking slmodemd version. Should be 2.9.11
SmartLink Soft Modem: version 2.9.11 Dec  3 2009 16:59:30
Finished installs.
Informing the System

Starting function tests, loading drivers:
Running diagnostic:

[   24.021735] slamr: module license 'Smart Link Ltd.' taints kernel.
[   24.033382] slamr: SmartLink AMRMO modem.
[   24.033518] slamr: probe 1057:3052 SL1900 card...
[   24.033554] slamr 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.339338] slamr: slamr0 is SL1900 card.
ports should be created by:
slmodemd -c USA /dev/slamr0
Checking for success
A file /etc/wvdial.conf already exists, first renaming to /etc/wvdial.201003010703
Running wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
/etc/wvdial.conf<Warn>: Can't open '/etc/wvdial.conf' for reading: No such file or directory
/etc/wvdial.conf<Warn>: ...starting with blank configuration.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
Modem detection successful

Read wdial.txt
Then edit /etc/wvdial.conf  with:
$ sudo gedit /etc/wvdial.conf"
at the lines beginning with ; and deleting the ; < >  symbols.

If not in the USA, get your COUNTRY spelling with:
$ slmodemd --help
$ slmodemd --countrylist

Then replace the default USA setting with:
$ sudo gedit /etc/default/sl-modem-daemon

Inform the system with a modem reset:
$ sudo /etc/init.d/sl-modem-daemon
This reset will likely be necessary between successive dialouts.

Then dialout with:
$ sudo wvdial"

Running setup again is NOT necessary. Only for dialout the:
$ sudo wvdial

Once online under Linux do:
$ sudo apt-get update
$ sudo apt-get install dkms
$ sudo apt-get install sl-modem-source
Thereafter, driver updates will augomagically follow kernel updates, thanks to dkms.
But it is necessary that linux-headers-version for the new kernel-version are also installed.
It is thus recommended that the new kernel-version and its linux-headers-version be
concurrently installed, or you will find yourself 
OFFLINE upon reboot into the new kernel.

Read the Slamr.txt record, other *.txt files and the sample wvdial.conf .


```
but when i want to connect to internet carrier check = no
wvdial show no carrier
how can i solve this problem
why you don't help me to solve this problem?

---

### Post by tah_206207 on 2010-01-28
Hello i installed my modem on ubuntu 9.10 and install wvdial 
```

taher@taher-desktop:~/Public/Programs/slamr-2.6.31-14-generic$ sudo ./setup
installing drivers for kernel version 2.6.31-14-generic

LogFile created
installing drivers for kernel version 2.6.31-14-generic

Writing record to ./Slamr.txt
    Installing the Debian packages supporting autoloading: sl-modem-daemon 

Copying over newer files
Making folder /lib/modules/2.6.31-14-generic/extra
Copying drivers to /lib/modules/2.6.31-14-generic/extra
Checking driver installs for slamr.ko and ungrab-winmodem.ko
slamr.ko
ungrab-winmodem.ko
Checking slmodemd version. Should be 2.9.11
SmartLink Soft Modem: version 2.9.11 Dec  3 2009 16:59:30
Finished installs.
Informing the System

Starting function tests, loading drivers:
Running diagnostic:

[   24.021735] slamr: module license 'Smart Link Ltd.' taints kernel.
[   24.033382] slamr: SmartLink AMRMO modem.
[   24.033518] slamr: probe 1057:3052 SL1900 card...
[   24.033554] slamr 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.339338] slamr: slamr0 is SL1900 card.
ports should be created by:
slmodemd -c USA /dev/slamr0
Checking for success
A file /etc/wvdial.conf already exists, first renaming to /etc/wvdial.201003010703
Running wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
/etc/wvdial.conf<Warn>: Can't open '/etc/wvdial.conf' for reading: No such file or directory
/etc/wvdial.conf<Warn>: ...starting with blank configuration.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
Modem detection successful

Read wdial.txt
Then edit /etc/wvdial.conf  with:
$ sudo gedit /etc/wvdial.conf"
at the lines beginning with ; and deleting the ; < >  symbols.

If not in the USA, get your COUNTRY spelling with:
$ slmodemd --help
$ slmodemd --countrylist

Then replace the default USA setting with:
$ sudo gedit /etc/default/sl-modem-daemon

Inform the system with a modem reset:
$ sudo /etc/init.d/sl-modem-daemon
This reset will likely be necessary between successive dialouts.

Then dialout with:
$ sudo wvdial"

Running setup again is NOT necessary. Only for dialout the:
$ sudo wvdial

Once online under Linux do:
$ sudo apt-get update
$ sudo apt-get install dkms
$ sudo apt-get install sl-modem-source
Thereafter, driver updates will augomagically follow kernel updates, thanks to dkms.
But it is necessary that linux-headers-version for the new kernel-version are also installed.
It is thus recommended that the new kernel-version and its linux-headers-version be
concurrently installed, or you will find yourself 
OFFLINE upon reboot into the new kernel.

Read the Slamr.txt record, other *.txt files and the sample wvdial.conf .


```but when i want to connect to internet carrier check = no
wvdial show no carrier
how can i solve this problem?
why you don't help me to solve this problem?

---


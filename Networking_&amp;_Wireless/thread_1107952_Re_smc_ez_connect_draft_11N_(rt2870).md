---
title: "Re: smc ez connect draft 11N (rt2870)"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by t_virus on 2009-03-27
i installed the latest driver from [www.smc.com](www.smc.com) but even so i cant get it working:

mauro@mauro-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SMC"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:F7:80:B3:72   
          Bit Rate:36 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=9/70  Signal level=-87 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:""  Nickname:""
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mauro@mauro-laptop:~$ sudo su
[sudo] password for mauro: 
root@mauro-laptop:/home/mauro# ifconfig ath0 down
root@mauro-laptop:/home/mauro# wlanconfig ath0 destroy
root@mauro-laptop:/home/mauro# wlanconfig ra0 create wlandev wifi0 wlanmode sta
ra0
root@mauro-laptop:/home/mauro# wlanconfig ra0 list scan
ioctl[unknown???]: Network is down
wlanconfig: unable to get scan results
root@mauro-laptop:/home/mauro# wlanconfig ra create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Input/output error
root@mauro-laptop:/home/mauro# wlanconfig ra0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Input/output error
root@mauro-laptop:/home/mauro# wlanconfig ra0 destroy
wlanconfig: ioctl: Network is down
root@mauro-laptop:/home/mauro# modprobe 
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
root@mauro-laptop:/home/mauro# modprobe ra0 config
FATAL: Module ra0 not found.
root@mauro-laptop:/home/mauro# lsusb
Bus 004 Device 003: ID 083a:a618 Accton Technology Corp. SMC EZ Connect N Draft 11n Wireless Adapter
Bus 004 Device 002: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 04f3:0213 Elan Microelectronics Corp. 
Bus 003 Device 004: ID 174f:5a35 Syntek 1.3MPixel Web Cam - Asus G1s
Bus 003 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@mauro-laptop:/home/mauro# wlanconfig ra0 destroy
wlanconfig: ioctl: Network is down
root@mauro-laptop:/home/mauro# modprobe ra0 -ae
modprobe: invalid option -- 'e'
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
root@mauro-laptop:/home/mauro# modprobe ra0 -a
WARNING: Module ra0 not found.
root@mauro-laptop:/dev# wlanconfig ra0 destroy
wlanconfig: ioctl: Network is down
root@mauro-laptop:/dev# wlanconfig ath0 create wlandev wifi0 wlanmode sta
wlanconfig: ioctl: Input/output error

has u can see the smc is there but i cant put it in sta mode, and when i try this i can no longer activate the ath0.
any idea to help me?

---


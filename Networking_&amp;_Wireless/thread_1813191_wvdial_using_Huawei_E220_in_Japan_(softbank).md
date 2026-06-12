---
title: "wvdial using Huawei E220 in Japan (softbank)"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by bah26 on 2011-07-27
I have been unsuccessfully trying to configure my Mobile Broadband provided by Softbank in Japan using Ubuntu 10.04.2 LTS (kernel 2.6.32-32-generic). Based upon the following I believe I have a Huawei E220.

```
bah@x31:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```I have tried to use NetworkManager, but I couldn't get it to work. So I moved to the command line to try to find out why. I've been using the following config file with *wvdial*.

```
[Dialer Defaults]
Modem = /dev/ttyUSB0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = *99#
Username = ai@softbank
Password = softbank
Stupid Mode = yes
Carrier Check = no
```And when I execute *sudo wvdial *I get the following output.

```
bah@x31:~$ sudo wvdial 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Jul 28 00:02:04 2011
--> Pid of pppd: 2820
--> Using interface ppp0
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> pppd: &#65533;&#65533;&#65533;[08]&#65533;&#65533;&#65533;[08]
--> Disconnecting at Thu Jul 28 00:02:06 2011
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
...
```I have checked */var/log/messages *to reveal the following.

```
bah@x31:~$ cat /var/log/messages
...
Jul 28 00:02:11 x31 pppd[2824]: pppd 2.4.5 started by root, uid 0
Jul 28 00:02:11 x31 pppd[2824]: Using interface ppp0
Jul 28 00:02:11 x31 pppd[2824]: Connect: ppp0 <--> /dev/ttyUSB0
Jul 28 00:02:11 x31 pppd[2824]: CHAP authentication succeeded
Jul 28 00:02:11 x31 pppd[2824]: CHAP authentication succeeded
Jul 28 00:02:13 x31 pppd[2824]: Modem hangup
Jul 28 00:02:13 x31 pppd[2824]: Connection terminated.
Jul 28 00:02:13 x31 pppd[2824]: Exit.
```I would be grateful if someone could solve this problem!

---


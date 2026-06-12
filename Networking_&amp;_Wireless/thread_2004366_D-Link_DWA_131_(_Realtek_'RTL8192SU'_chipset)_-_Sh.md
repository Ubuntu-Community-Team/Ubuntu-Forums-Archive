---
title: "D-Link DWA 131 ( Realtek 'RTL8192SU' chipset) - Should be &quot;N&quot;  but is not"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by Jugurtha on 2012-06-15
Hello, Forum ..

I recently bought a DWA 131 (Wireless N Nano USB Adapter). The box states N wireless.

I am able to connect to the internet using it, and all is fine. I'm on my Desktop computer running Ubuntu 11.10.

```
jugurtha@Jugurtha-Box:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 125f:c82a A-DATA Technology Co., Ltd. 
Bus 001 Device 004: ID 07d1:3303 D-Link System DWA-131 802.11n Wireless N Nano Adapter(rev.A1) [Realtek RTL8192SU]

```So far, so good. (It concurs with the box saying H/W Ver.:A1). The box says F/W Ver.:1.00.

However:

```
jugurtha@Jugurtha-Box:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Speed"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:XX:XX:XX:XX:XX   
          Bit Rate:54 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-****-****   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=42/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```You see that it's **IEEE 802.11bg**,  there is no "n" in the end like it should be (I think).

Furthermore..

```
jugurtha@Jugurtha-Box:~$ iwlist modulation
lo        no modulation information.

eth0      no modulation information.

wlan0     unknown modulation information.

```The "unknown modulation information." ticks me.

For the configuration:

```
jugurtha@Jugurtha-Box:~$ sudo iwlist wlan0 event
wlan0     Wireless Events supported :

```When I go to 

/lib/firmware/

There is no RTL8192SU directory.

Although there is RTL8192SE. But I want the SU thing. 

I know that in previous versions, the files were placed in the wrong directory

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/595455](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/595455)

When I do :

```
jugurtha@Jugurtha-Box:/lib/firmware/RTL8192SE$ sudo dmesg | grep rtl
[   27.801346] r8712u: register rtl8712_netdev_ops to netdev_ops
[   29.133060] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"

```So going to /lib/firmware/rtlwifi

```
jugurtha@Jugurtha-Box:/lib/firmware/rtlwifi$ ls
rtl8192cfw.bin  rtl8192cufw.bin  rtl8192defw.bin  rtl8192sefw.bin  rtl8712u.bin

```I don't see a nice rtl8192su.bin or something.

Now, I don't know if the 8712u is "better" .. But it doesn't seem to make the DWA 131 work as it should. (chose modulation, etc...).

How should I go about this, knowing that :

- Realtek's site to download the driver for RTL8192SU doesn't work (none of the mirrors does).

- D-Link's ftp site to download the driver for the DWA 131 doesn't work either.

Some people complained about that to Realtek, got send the driver, put it in a website and shared the link.. These link are all "404".

Some stupid site offering Linux drivers on a .exe file.

What do you suggest ? Especially about the 8712 thingy.

--
~Jugurtha Hadjar,

---


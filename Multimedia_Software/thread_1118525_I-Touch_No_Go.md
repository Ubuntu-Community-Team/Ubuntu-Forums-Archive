---
title: "I-Touch No Go"
date: 2009-04-07
forum: Multimedia Software
---

### Post by Paul Vega on 2009-04-07
I have been trying (unsuccessfully) to get my I-Touch going with my Hardy OS for 4 months now. I have encountered several issues that have been enormously difficult given my scant knowledge and my time restrictions. I am asking anyone who seems to be knowledgeable to assist me. As my system does not have anything other than Ubuntu Hardy Heron 8.04 on it. I do not have any MS programs or the ability (let alone the inclination) to run them. That gave me BIG issues with trying to initiate the Pod and I ended up going to an internet cafe and setting it up through there. I then tried to 'jailbreak' it and again resorted to getting outside help, eventually paying a Computer Shop $200 to do the job. My PC does not see the pod even though I can see that it is docking. I have attached the relevant data that shows this happening. Can you please offer any suggestions on how to get this up and running? I have posted these cries for help on two previous and related threads but I seem to have joined too late as no body has responded.

1)  Re: HOW-TO iPod with (Ubuntu) Linux
Kia Ora

I have followed the instructions but encounter the following error on trying to mount my itouch;
paul@paul-desktop:~$ sudo mount /dev/sda2
[sudo] password for paul:
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
missing codepage or helper program, or other error
(aren't you trying to mount an extended partition,
instead of some logical partition inside?)
In some cases useful info is found in syslog - try
dmesg | tail or so
I had my itouch jail-broken at a trusted Computer store in my home town.I am running ubuntu 8.04 (hardy). Can someone please offer suggestions to help?

Paul Vega


Further information

On running Code: $ dmesg, I get the following lines of relevence when my itouch is plugged in:

[ 404.008118] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 404.010828] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 404.011984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 408.991393] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 408.994166] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 408.994677] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 422.639648] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 422.642403] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 422.643836] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 447.383263] eth1: no IPv6 routers present
[ 2295.019630] FAT: bogus number of reserved sectors
[ 2295.019647] VFS: Can't find a valid FAT filesystem on dev sda2.
[ 3117.874580] usb 5-1: USB disconnect, address 2
[ 3127.560370] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 3127.694849] usb 5-1: configuration #1 chosen from 3 choices

I then get the following lines of relevence when my itouch is not plugged in:
[ 404.008118] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 404.010828] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 404.011984] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 408.991393] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 408.994166] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 408.994677] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 422.639648] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 422.642403] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[ 422.643836] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 447.383263] eth1: no IPv6 routers present
[ 2295.019630] FAT: bogus number of reserved sectors
[ 2295.019647] VFS: Can't find a valid FAT filesystem on dev sda2.
[ 3117.874580] usb 5-1: USB disconnect, address 2
[ 3127.560370] usb 5-1: new high speed USB device using ehci_hcd and address 7
[ 3127.694849] usb 5-1: configuration #1 chosen from 3 choices
[ 3587.280771] usb 5-1: USB disconnect, address 7
Last edited by Paul Vega; 6 Days Ago at 08:37 PM.. Reason: Further information: On running Code: $ dmesg, I get the following lines of relevence: 

2)  Re: [all variants] HowTo Ipod on Hardy
I am getting the following reply to my serial no. search. The first output is with the ITouch disconnected, the second is with it connected.

paul@paul-desktop:~$ sudo lsusb -v | grep -i Serial
iSerial 1 0000:00:1d.7
iSerial 3 00027216B9CD
iSerial 1 0000:00:1d.3
iSerial 1 0000:00:1d.2
iSerial 3 0016e3fc3280
iSerial 3 BROD7F957378
iSerial 1 0000:00:1d.1
iSerial 1 0000:00:1d.0
paul@paul-desktop:~$ sudo lsusb -v | grep -i Serial
iSerial 3 459625aef8a5f6835708434384941ad42d07fa34
iSerial 1 0000:00:1d.7
iSerial 3 00027216B9CD
iSerial 1 0000:00:1d.3
iSerial 1 0000:00:1d.2
iSerial 3 0016e3fc3280
iSerial 3 BROD7F957378
iSerial 1 0000:00:1d.1
iSerial 1 0000:00:1d.0

Is it possible that this is the serial no.? It looks totally unlike anything you have suggested;
iSerial 3 459625aef8a5f6835708434384941ad42d07fa34

Your help or suggestions would be greatly appreciated - Paul Vega

---


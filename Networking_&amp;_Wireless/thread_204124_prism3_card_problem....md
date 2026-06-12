---
title: "prism3 card problem..."
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by sveronese on 2006-06-26
Hi. I have kubuntu 6.06 with kernel 2.6.15-25-386.
I have a prism3 PC card. This is the output of 

$ sudo cardctl ident
Socket 0:
  product info: "WLAN", "PRISM3", "37101P", "Revision C2"
  manfid: 0x50c2, 0x0011
  function: 6 (network)

The system have hostap and linux-wlan-ng package installed but when I plug into the card the system do nothing.
I've tried to load the kernel module by hand with the command

$ sudo modprobe hostap_cs
$ dmesg
[17182731.272000] pccard: PCMCIA card inserted into slot 0
[17182731.272000] pcmcia: registering new device pcmcia0.0
[17182834.488000] hostap_cs: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)

The system cannot recognize the card plugged in, I think.

Well... at this point I've tried with linux-wlan-ng with this command:

$ sudo rmmod hostap_cs
$ sudo modprobe prism2_cs 
$ dmesg
[17183357.364000] prism2cs_init: prism2_cs.o: 0.2.2 Loaded
[17183357.364000] prism2cs_init: dev_info is: prism2_cs

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1     radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=off   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eth1 is the integrated wireless card.

Another mystery is:

$ modprobe  p80211
$dmesg
[17183357.360000] kobject_register failed for p80211 (-17)
[17183357.360000]  [<c01d9df3>] kobject_register+0x43/0x60
[17183357.360000]  [<c0136c80>] mod_sysfs_setup+0x50/0xb0
[17183357.360000]  [<c013800c>] load_module+0x8cc/0xa30
[17183357.360000]  [<c01381e7>] sys_init_module+0x47/0x1d0
[17183357.360000]  [<c010304b>] sysenter_past_esp+0x54/0x79

Anyone Help?
Thank you!

---


---
title: "extra wireless interfaces -- no connection, little help please"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by audacity on 2006-06-19
Hey all, 
    First time ubuntu user. I have installed xubuntu on an old ibm t20 laptop with an orinoco card. At first, I couldn't find any information on setting up the card, and I therefore mistakenly installed additional drivers (hostap). I realized later that orinoco_cs was built into the kernel, and I uninstalled the hostap module. Now I have  this problem:
insert the card and go:
```
[100284.064911] pccard: PCMCIA card inserted into slot 0
[100284.064936] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[100284.072276] pcmcia: registering new device pcmcia0.0
[100284.328272] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[100284.353027] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[100284.435927] eth1: Hardware identity 0001:0001:0004:0002
[100284.436629] eth1: Station identity  001f:0001:0007:001c
[100284.436959] eth1: Firmware determined as Lucent/Agere 7.28
[100284.437268] eth1: Ad-hoc demo mode supported
[100284.437548] eth1: IEEE standard IBSS ad-hoc mode supported
[100284.437853] eth1: WEP supported, 104-bit key
[100284.438213] eth1: MAC address 00:02:2D:3B:95:B0
[100284.438588] eth1: Station name "HERMES I"
[100284.439291] eth1: ready
[100284.440048] eth1: index 0x01: Vcc 5.0, irq 3, io 0x0100-0x013f
[100284.538162] ieee80211_crypt: registered algorithm 'NULL'
logan@skeletor:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth2      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated
          Bit Rate:11 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

eth2 doesn't work even when set up correctly through iwconfig or network-admin. Any idea how to get rid of eth2/make eth1 the actual wireless interface? Any guidance is appreciated.
Thanks!

---


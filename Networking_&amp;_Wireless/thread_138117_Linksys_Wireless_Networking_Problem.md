---
title: "Linksys Wireless Networking Problem"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by peschkaj on 2006-03-01
I have a Linksys wireless card that uses the orinoco_cs kernel module.

The output of cardctl ident looks like this:

```

Socket 0:
  product info: "The Linksys Group, Inc.", "Instant Wireless Network PC Card", "ISL37300P", "RevA"
  manfid: 0x0274, 0x1613
  function: 6 (network)

```

Here's what's going on.  Up until two days ago I was able to get an IP from my home router.  The router was power cycled and since then I have not been able to get an IP from the router on this wireless card.  All of the other computers in the house are able to get a connection.

I have re-entered the router info in the network configuration UI, but this has had no effect.

Any help would be greatly appreciated.

Thanks,

jeremiah

---

### Post by peschkaj on 2006-03-01
Another piece of info, which may or may not help others, when I run sudo dhclient eth1 I get the following output:

```

 sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:06:25:16:24:f3
Sending on   LPF/eth1/00:06:25:16:24:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Here's the output of iwconfig:

```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"2WIRE913"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:88:9C:B0:B1
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity:1/3
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=86/92  Signal level=5/153  Noise level=121/153
          Rx invalid nwid:0  Rx invalid crypt:1564  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by Lambert on 2006-03-01
Notice your iwconfig output.

> 
Rx invalid crypt
              Number  of packets that the hardware was unable to decrypt. This
              can be used to detect invalid encryption settings.



What kind of encryption are you using?

---

### Post by peschkaj on 2006-03-01
I had noticed that before, but I wasn't sure what was going on and I forgot to mention it.

I'm using WEP with a Plain (ASCII) key.  My windows machine tells me that the Network Authentication is set to 'Simple'.

---

### Post by peschkaj on 2006-03-03
Would it be helpful for me to switch to the wlan_ng drivers instead of the orinoco drivers for this card?

---

### Post by djroadrash on 2006-03-05
did u make sure that the key is correct?, maybe you type it wrong by mistake, are u doing this on sys/adm/networking or on terminal?
do this
sudo iwconfig eth1 essid [yournetworkname] mode managed key s:[yourpassword]
all one line and notice the spacing and dont use [] ; 
then 
sudo dhclient eth1


good luck
:KS

---

### Post by peschkaj on 2006-03-06
I've tried this both from the command line and from sys/adm/networking, and neither one gets me any results.

The password is the default password that was supplied with my router from the manufacturer.  As a last resort, I might attempt to change it, but I'm curious if there is some issue with my card and the orinoco_cs drivers vs the wlan_ng drivers that I should be aware of.  Or, perhaps, should I make use of the native win32 drivers and ndiswrapper them?

Any thoughts?

---

### Post by Lambert on 2006-03-07
It might be a simple setting that needs to be changed rather then switch drivers but switching drivers might help.

try adding these settings from terminal.

sudo iwconfig eth1 key restricted
or 
sudo iwconfig eth1 key open
or 
sudo iwconfig eth1 key on


You said simple setting. Do you know if it's an open or shared key setting. I'm wondering if simple=open.

---

### Post by peschkaj on 2006-03-07
Sorry for the ambiguity.  The WEP is set to an open key setting on the router.

---

### Post by peschkaj on 2006-03-24
First, thanks to everyone for their help.  I eventually got everything working by resetting the password on the router and entering the new password in the Network Connection tool.  Everything works fine now.

---


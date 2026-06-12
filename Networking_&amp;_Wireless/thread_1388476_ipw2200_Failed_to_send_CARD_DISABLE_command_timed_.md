---
title: "ipw2200: Failed to send CARD_DISABLE: command timed out."
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by sarlaccpit on 2010-01-23
Hi All,
 
I cannot connect my Sony Viao laptop to wireless.
It just will not [SIZE=2]seem[/SIZE] to connect. I am a bit of a n00b i am afraid so go easy on me  ;)
I have been through /sys/bus/pci/drivers/ipw2200 does exist.
 
The Wireless has connected before but it has just seemed to have stopped. I have tried a few suggestions made in the forums and edited my interfaces config.
 
Any ideas?
[FONT=Nimbus Roman No9 L][FONT=Times New Roman][SIZE=2][/SIZE][/FONT][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]```
[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2]auto lo[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2]iface lo inet dhcp[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]auto eth1[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2]iface eth1 inet dhcp[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2]wireless-essid NETGEAR [/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2]
```[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]The dmesg error which i think is to be the cause:[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]```
 [/SIZE]
[FONT=Nimbus Roman No9 L][SIZE=2]ipw2200: Failed to send CARD_DISABLE: Command timed out.[/SIZE][/FONT]
[SIZE=2]
```[/SIZE][/FONT][FONT=Nimbus Roman No9 L][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]Other useful information posted below.[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]```
[/SIZE][FONT=Nimbus Roman No9 L][SIZE=2] [/SIZE]
[SIZE=2]root@evil:~# lsb_release -d[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]Description:            Ubuntu 9.10[/SIZE]
[/FONT][SIZE=2]
```[/SIZE][SIZE=2][/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]```
[/SIZE][FONT=Nimbus Roman No9 L][SIZE=2] [/SIZE]
[SIZE=2]root@evil:~# uname -mr[/SIZE]
[SIZE=2][/SIZE]
[FONT=Nimbus Roman No9 L][SIZE=2]2.6.31-17-generic i686[/SIZE][/FONT][/FONT]
[SIZE=2]
```[/SIZE]
[SIZE=2][/SIZE][/FONT][FONT=Nimbus Roman No9 L] 
[FONT=Nimbus Roman No9 L][EMAIL="root@evil"][SIZE=2]```
 [/SIZE]
[FONT=Nimbus Roman No9 L][/EMAIL][EMAIL="root@evil"][SIZE=2]root@evil[/SIZE][/EMAIL][EMAIL="root@evil"][SIZE=2]:~# 06:0a.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)[/SIZE][/FONT]
[SIZE=2]
```[/SIZE][/EMAIL]
[SIZE=2][/SIZE][/FONT][FONT=Nimbus Roman No9 L][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]```
[/SIZE][FONT=Nimbus Roman No9 L][SIZE=2] [/SIZE]
[SIZE=2]root@evil:~# lsmod | grep 'ipw2200'[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]ipw2200               140292  0 [/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]libipw                 43148  1 ipw2200[/SIZE]
[SIZE=2][/SIZE]
[FONT=Nimbus Roman No9 L][SIZE=2]lib80211                6432  2 ipw2200,libipw[/SIZE][/FONT][/FONT]
[SIZE=2]
```[/SIZE][/FONT][FONT=Nimbus Roman No9 L][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2][/SIZE][/FONT] 
[FONT=Nimbus Roman No9 L][SIZE=2]```
[/SIZE][FONT=Nimbus Roman No9 L][SIZE=2] [/SIZE]
[SIZE=2]root@evil:~# dmesg | grep 'ipw2200'[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][   21.120773] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][   21.120777] ipw2200: Copyright(c) 2003-2006 Intel Corporation[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][   21.120873] ipw2200 0000:06:0a.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][   21.120954] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][   21.121007] ipw2200 0000:06:0a.0: firmware: requesting ipw2200-bss.fw[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][   21.668641] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][ 1394.604043] ipw2200: Failed to send CARD_DISABLE: Command timed out.[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][ 1593.708081] ipw2200: Failed to send CARD_DISABLE: Command timed out.[/SIZE]
[SIZE=2][FONT=Nimbus Roman No9 L][ 1727.840112] ipw2200: Failed to send CARD_DISABLE: Command timed out.[/FONT] [/SIZE]
[/FONT][SIZE=2]
```[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2] [/SIZE][SIZE=2]```
 [/SIZE]
[SIZE=2]iwlist scan[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2] lo        Interface doesn't support scanning.[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2] eth0      Interface doesn't support scanning.[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2] eth1      Scan completed :[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]**edit: omitted irrelevent networks piced up**[/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]Cell 02 - Address: 00:09:5B:D7:64:74[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    ESSID:"NETGEAR"[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    Protocol:IEEE 802.11bg[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    Mode:Master[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    Frequency:2.462 GHz (Channel 11)[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    Encryption key:on[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                              36 Mb/s; 48 Mb/s; 54 Mb/s[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                    Quality=98/100  Signal level=-25 dBm  [/SIZE]
[SIZE=2][/SIZE]
[SIZE=2][FONT=Nimbus Roman No9 L]                    Extra: Last beacon: 184ms ago[/FONT] [/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]
```[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2] 
[/SIZE][FONT=Nimbus Roman No9 L][SIZE=2]```
 [/SIZE]
[FONT=Nimbus Roman No9 L][SIZE=2]root@evil:~# /etc/init.d/networking restart[/SIZE][/FONT]
[SIZE=2] [/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]Listening on LPF/eth1/00:13:ce:ad:6c:1a[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]Sending on   LPF/eth1/00:13:ce:ad:6c:1a[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]Sending on   Socket/fallback[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]No DHCPOFFERS received.[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]No working leases in persistent database - sleeping.[/SIZE]
[SIZE=2][/SIZE]
[SIZE=2]                                                                                                                                                      [ OK ][/SIZE]
[SIZE=2][/SIZE]
[SIZE=2] [/SIZE]
[SIZE=2]
```[/SIZE][/FONT][/FONT][FONT=Nimbus Roman No9 L][/FONT][/FONT]

---

### Post by chili555 on 2010-01-23
> Cell 02 - Address: 00:09:5B:D7:64:74

                    ESSID:"NETGEAR"

                    Protocol:IEEE 802.11bg

                    Mode:Master

                    Frequency:2.462 GHz (Channel 11)

                    [COLOR="Red"]Encryption key:on[/COLOR]
This looks like WEP encryption. How or where are you supplying the key? The usual way is in *interfaces*:```
auto lo
iface lo inet dhcp
 
auto eth1
iface eth1 inet dhcp
wireless-essid NETGEAR 
wireless-key 012345etc.
```Please clarify.

---

### Post by sarlaccpit on 2010-01-23
Thanks for your reply :)
 
I have now added the hex password to *interfaces *but still can't connect. It still fails. When i restart the network i get the following:
 
 
```
 
root@evil:~# /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                                                       There is already a pid file /var/run/dhclient.eth1.pid with pid 3216

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.1.2

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/

 
 
Listening on LPF/eth1/00:13:ce:ad:6c:1a

Sending on   LPF/eth1/00:13:ce:ad:6c:1a

Sending on   Socket/fallback

Internet Systems Consortium DHCP Client V3.1.2

Copyright 2004-2008 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/

 
 
Listening on LPF/eth1/00:13:ce:ad:6c:1a

Sending on   LPF/eth1/00:13:ce:ad:6c:1a

Sending on   Socket/fallback

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11

No DHCPOFFERS received.

[FONT=Nimbus Roman No9 L][SIZE=1]No working leases in persistent database - sleeping.[/SIZE][/FONT]

```

---

### Post by vinke on 2010-01-23
I think ipw is deprecated.
the iwl firmware works fine for me.
try the firmware-iwlwifi package with apt.

// Im sorry. iwl is for newer cards

---

### Post by chili555 on 2010-01-23
> I have now added the hex password to interfaces but still can't connect.Is Network Manager working against you? Is it removed completely or do you still need it? You might also do:```
sudo apt-get install linux-backports-modules-karmic-generic
```There is apparently a better *ipw2200 *in there.

---

### Post by sarlaccpit on 2010-01-23
[SIZE=2]Gah! apt isn't working due to proxy (which i am not behind at present and can't seem to remove from the settings completely). So will re-try these when i am back in teh office on Monday.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]I have tried with network manager and manually editing the interfaces file. Niether way does it seem to want to connect.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]Logically speaking, if the laptop can see the wifi network - it should be able to connect to them as long as the authentication is there right? And *iwlist scan* shows the wifi network.[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE]

---

### Post by chili555 on 2010-01-23
> Logically speaking, if the laptop can see the wifi network - it should be able to connect to them as long as the authentication is there right? Yes. Where are you putting the key in Network Manager? 40/128-bit key, I hope?

---

### Post by sarlaccpit on 2010-01-23
> **chili555 said:**
> Yes. Where are you putting the key in Network Manager? 40/128-bit key, I hope?

It will not except the hex or the ASCII in 40/128-bit key only a 128 bit passphrase. Again i have tried the real password and the hex... neither work. Below is a copy of the config from Network Manager.

```

[connection]
id=netgear
uuid=0b2e78fd-3138-44e3-b297-a3b8eda9bff7
type=802-11-wireless
autoconnect=true
timestamp=0

[802-11-wireless-security]
key-mgmt=none
wep-tx-keyidx=0
auth-alg=open
wep-key0=** ** ** ** ** ** ** ** **
wep-key-type=2

[ipv4]
method=auto
ignore-auto-routes=false
ignore-auto-dns=false
dhcp-send-hostname=false
never-default=false

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false

[802-11-wireless]
ssid=78;69;84;71;69;65;82;
mode=infrastructure
channel=0
rate=0
tx-power=0
mtu=0
security=802-11-wireless-security


```

---

### Post by chili555 on 2010-01-23
> t will not except the hex or the ASCII in 40/128-bit key only a 128 bit passphrase. Again i have tried the real password and the hex... neither work.WEP keys are either HEX or ASCII. I am not aware of how you can convert one to the other or successfully use one in place of the other.

HEX are either 10 or 26 characters using 0-9 and a-f. ASCII are either 5 or 13 characters using every alphanumeric character. I have never seen a WEP password work successfully; that is, a converter on the web or in a router's configuration that converts a password to a key. If you put a password in the router's configuration, such as 'ilovecoldbeer' and it converted it to a WEP key, such as 012a345b67, then you must use the key; the password never works.

Does this help?

---

### Post by sarlaccpit on 2010-02-22
Just replying to hold up my n00bish hands and say that wireless works fine. It is just my inlaws wireless which seems to be a little shoddy. Wireless works fine on any other network.

Thanks for the help everyone.

---

### Post by sarlaccpit on 2010-02-22
Changing subject to solved

---


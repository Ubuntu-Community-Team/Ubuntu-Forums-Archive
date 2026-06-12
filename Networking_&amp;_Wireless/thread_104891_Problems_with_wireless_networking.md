---
title: "Problems with wireless networking"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by [knap] on 2005-12-17
Hello, i have a D-Link DWL-G520+ pci adapter and a Linksys WRT54G router, ubuntu loaded the drivers for my pci card but i can't get a ip, i'm using DHCP in the router and i don't want to change this because i also use windows. I take some screenshots to help

PCI card

[IMG]http://clientes.netvisao.pt/jflaviop/linux/wifi2.JPG[/IMG]

[IMG]http://clientes.netvisao.pt/jflaviop/linux/wifi3.JPG[/IMG]

terminal commands

[IMG]http://clientes.netvisao.pt/jflaviop/linux/iwconfig.JPG[/IMG]

[IMG]http://clientes.netvisao.pt/jflaviop/linux/ifconfig.JPG[/IMG]

[IMG]http://clientes.netvisao.pt/jflaviop/linux/dhclient.JPG[/IMG]

and later i tried with wifi-radar

[IMG]http://clientes.netvisao.pt/jflaviop/linux/wifi-radar.JPG[/IMG]

can you help me?
Thanks ;)

---

### Post by Lambert on 2005-12-17
run these commands and post output

sudo iwlist wlan0 scan
(replace wlan0 with your inteface name if different)

iwconfig
ifconfig

---

### Post by [knap] on 2005-12-17
Hi

```
luis@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

```
luis@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"linksys"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eth0      no wireless extensions.
```

```
luis@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:XXX.XXX.XXX.XXX  Bcast:XXX.XXX.XXX.XXX  Mask:XXX.XXX.XXX.X
          inet6 addr: XXXX::XXX:XXX:XXXX:XXXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5300248 (5.0 MiB)  TX bytes:489995 (478.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6936151 (6.6 MiB)  TX bytes:6936151 (6.6 MiB)

wlan0     Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet6 addr: fe80::213:46ff:feb0:43f1/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17

```

I'm using my modem connected by usb to have internet now, i replaced the mac adreess by XX.

---

### Post by Lambert on 2005-12-17
Currently you're not even associated with the ap, so obtaining an ip through dhcp is secondary. This line is what tells me this.
Frequency:2.412 GHz Access Point: 00:00:00:00:00

[FONT=monospace]So, what channel is your ap broadcasting on? 2.412 is channel 1  

So try this command from a terminal.

sudo iwconfig wlan0 essid linksys channel _ mode managed commit

I assume your essid is linksys, replace that with actual essid if it's different
Add the channel where I put _ and don't put _ in the command. If you're not sure of the channel try putting auto in there.

Then rerun iwconfig to see if access point: changes from all zeros to the mac address of the router.

If yes then

sudo dhclient wlan0
[/FONT]

---

### Post by [knap] on 2005-12-17
[QUOTE=Lambert]Currently you're not even associated with the ap, so obtaining an ip through dhcp is secondary. This line is what tells me this.
Frequency:2.412 GHz Access Point: 00:00:00:00:00

[FONT=monospace]So, what channel is your ap broadcasting on? 2.412 is channel 1  

So try this command from a terminal.

sudo iwconfig wlan0 essid linksys channel _ mode managed commit

I assume your essid is linksys, replace that with actual essid if it's different
Add the channel where I put _ and don't put _ in the command. If you're not sure of the channel try putting auto in there.

Then rerun iwconfig to see if access point: changes from all zeros to the mac address of the router.

If yes then

sudo dhclient wlan0
[/FONT][/QUOTE]

My AP (router) is broadcasting in channel 6 and the essid is linksys i tried your command and the output was

```
luis@ubuntu:~$ sudo iwconfig wlan0 essid linksys channel 6 mode managed commit
Password:
luis@ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"linksys"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

eth0      no wireless extensions.
```

Still no luck, what is going on?
Thanks for the help

---

### Post by Lambert on 2005-12-18
Your router is not letting you associate with it. Are you using any encryption or mac filtering on the router?

Also what protocol is your router broadcasting in? G

A link where you might find help.

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

### Post by [knap] on 2005-12-18
[QUOTE=Lambert]Your router is not letting you associate with it. Are you using any encryption or mac filtering on the router?

Also what protocol is your router broadcasting in? G

A link where you might find help.

[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)[/QUOTE]

I disabled encryption and mac filtering, my router is broadcasting in mixed mode b/g could be this?

I would like to solve this problem but i instaled nvidia drivers by synaptic and x isn't working anymore, oh boy... :(

Thanks for the link i'm going to read it.

---


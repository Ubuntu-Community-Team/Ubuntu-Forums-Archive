---
title: "Bridge"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by furiouscoffee on 2013-06-08
[COLOR=#323C46][FONT=MuseoSans]I want to setup a bridge but i want to avoid getting disconnected from the internet, could you provide me with some assistance and just let me know basically what im doing wrong.[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]Here is how my /etc/network/interfaces looks like right now :[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]auto lo[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]iface lo inet loopback[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]auto eth0[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:0[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:1[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:2[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:3[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:4[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:5[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:6[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:7[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:8[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:9[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]auto eth0:10[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]iface eth0 inet static[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]address 192.11[/FONT][/COLOR][COLOR=#323C46][FONT=MuseoSans]x.xx.xxx[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]netmask 255.255.255.252[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]gateway 192.11[/FONT][/COLOR][COLOR=#323C46][FONT=MuseoSans]x.xx.xxx[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]broadcast 192.11[/FONT][/COLOR][COLOR=#323C46][FONT=MuseoSans]x.xx.xxx[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]dns-nameservers 8.8.8.8[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]DNS1 8.8.8.8[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]DNS2 8.8.4.4[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]iface eth0:0 inet static[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]address 192.19[/FONT][/COLOR][COLOR=#323C46][FONT=MuseoSans]x.xx.xxx[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]netmask 255.255.255.240[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]iface eth0:1 inet static[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]address 192.19x.xx.xxx[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]netmask 255.255.255.240[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]Like mentioned above i would like to setup a bridge, must i simply just completly erase the one above and replace it with :[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]auto br0[/FONT][/COLOR]

[COLOR=#323C46][FONT=MuseoSans]iface br0 inet dhcp[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]bridge_ports eth0[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]bridge_stp off[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]bridge_maxwait 0[/FONT][/COLOR]
[COLOR=#323C46][FONT=MuseoSans]bridge_fd 0[/FONT][/COLOR]


[COLOR=#323C46][FONT=MuseoSans]Any support on how todo this would be helpful or any tips.[/FONT][/COLOR]


[COLOR=#323C46][FONT=MuseoSans]Thanks allot for your effort ,[/FONT][/COLOR]

---


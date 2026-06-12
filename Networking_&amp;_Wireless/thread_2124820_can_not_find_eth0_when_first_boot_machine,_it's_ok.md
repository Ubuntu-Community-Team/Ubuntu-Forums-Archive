---
title: "can not find eth0 when first boot machine, it's ok when reboot the system, help!"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by zjykzk on 2013-03-12
[COLOR=#333333][FONT=Ubuntu Beta]some commad's results are following:[/FONT][/COLOR][COLOR=#000000][FONT=song]

spci -k|grep -i -A2 net[/FONT][/COLOR]
[COLOR=#000000][FONT=song]00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 06)[/FONT][/COLOR]
[COLOR=#000000][FONT=song]Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard[/FONT][/COLOR]
[COLOR=#000000][FONT=song]Kernel modules: e1000e
[/FONT][/COLOR]
[COLOR=#000000][FONT=song]ifconfig -a[/FONT][/COLOR]
[COLOR=#000000][FONT=song]lo Link encap:&#26412;&#22320;&#29615;&#22238; [/FONT][/COLOR]
[COLOR=#000000][FONT=song]inet &#22320;&#22336;:127.0.0.1 &#25513;&#30721;:255.0.0.0[/FONT][/COLOR]
[COLOR=#000000][FONT=song]inet6 &#22320;&#22336;: ::1/128 Scope:Host[/FONT][/COLOR]
[COLOR=#000000][FONT=song]UP LOOPBACK RUNNING MTU:16436 &#36291;&#28857;&#25968;:1[/FONT][/COLOR]
[COLOR=#000000][FONT=song]&#25509;&#25910;&#25968;&#25454;&#21253;:32 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#24103;&#25968;:0[/FONT][/COLOR]
[COLOR=#000000][FONT=song]&#21457;&#36865;&#25968;&#25454;&#21253;:32 &#38169;&#35823;:0 &#20002;&#24323;:0 &#36807;&#36733;:0 &#36733;&#27874;:0[/FONT][/COLOR]
[COLOR=#000000][FONT=song]&#30896;&#25758;:0 &#21457;&#36865;&#38431;&#21015;&#38271;&#24230;:0 [/FONT][/COLOR]
[COLOR=#000000][FONT=song]&#25509;&#25910;&#23383;&#33410;:2624 (2.6 KB) &#21457;&#36865;&#23383;&#33410;:2624 (2.6 KB)
[/FONT][/COLOR]
[COLOR=#000000][FONT=song]lsmod | grep e1000e[/FONT][/COLOR]
[COLOR=#000000][FONT=song]e1000e 156693 0 [/FONT][/COLOR]

[COLOR=#000000][FONT=song]cat /etc/network/interfaces [/FONT][/COLOR]
[COLOR=#000000][FONT=song]auto lo[/FONT][/COLOR]
[COLOR=#000000][FONT=song]iface lo inet loopback

ps : the motherboard is [/FONT][/COLOR]ASUS SABERTOOTH X79, and the update the nework adapter does not work!

thanks

---


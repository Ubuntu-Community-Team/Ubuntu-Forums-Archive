---
title: "Network connections keep dropping"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by mongr31 on 2010-01-30
Here is the layout of my network:

My cable modem plugs into eth0 on my ubuntu server which acts as a firewall (shorewall) and dhcp server to my lan. A dd-wrt access point is plugged into eth1 and then a bridge connecting my xbox360 and another bridge connecting a desktop computer.

Everything works pretty well, except a few times a day, my network will just shut down. The wireless on my macbook and my wife's laptop will just shut down, and if my xbox is running, it will lose connectivity. It will be down for maybe a minute or two, and then come back up like nothing ever happened.

I never had this problem when I had just a dd-wrt router running everything instead of my server.

When I ssh into my server afterwards and run dmesg, this is what I will get:
```
 
[398598.251548] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398598.251565] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398606.243875] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398606.243888] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398613.251592] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398613.251607] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398616.241482] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398616.241499] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398624.387341] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[398626.272072] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398626.272089] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398628.285606] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398628.285622] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398636.277201] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398636.277214] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398643.283427] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398643.283442] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398646.278102] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398646.278118] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398656.303779] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398656.303796] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398658.319908] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398658.319921] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398666.312442] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398666.312455] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398673.314495] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398673.314507] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398676.316225] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398676.316240] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398686.346297] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398686.346312] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398688.354495] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398688.354510] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398696.354864] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398696.354881] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398703.355453] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398703.355467] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398706.356737] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398706.356752] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398716.398382] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398716.398396] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398718.406969] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398718.406986] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398726.406507] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398726.406520] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398733.408220] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398733.408235] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398736.409877] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398736.409890] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398746.447000] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398746.447015] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398748.458055] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398748.458074] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398756.453375] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398756.453389] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398763.460542] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398763.460557] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398766.452281] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398766.452296] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398776.480713] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398776.480728] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398778.495749] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398778.495762] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398786.481982] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398786.481997] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398793.497538] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398793.497553] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398796.482105] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398796.482123] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398806.512718] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398806.512732] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398808.529815] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398808.529829] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398816.514013] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398816.514028] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398823.524535] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398823.524549] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398825.752417] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=50097 DF PROTO=TCP SPT=33722 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[398826.518906] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398826.518920] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398828.858921] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=50105 DF PROTO=TCP SPT=33722 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[398834.981178] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=50117 DF PROTO=TCP SPT=33722 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[398836.378708] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.46 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[398836.550088] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398836.550105] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398838.553600] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398838.553612] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398846.553948] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398846.553961] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398853.562484] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398853.562499] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398856.556555] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398856.556569] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398866.590120] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398866.590137] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398868.595542] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398868.595555] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398876.591718] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398876.591733] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398883.597671] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398883.597685] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398886.595086] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398886.595102] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398895.734887] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=50451 DF PROTO=TCP SPT=33706 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[398896.627907] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398896.627920] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398898.638152] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398898.638167] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398898.754918] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=50466 DF PROTO=TCP SPT=33706 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[398904.769138] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=50493 DF PROTO=TCP SPT=33706 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[398906.632376] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398906.632393] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398913.640895] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398913.640911] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398916.630632] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398916.630650] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398926.661286] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398926.661303] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398928.671394] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398928.671411] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398936.668614] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398936.668627] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398939.177059] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[398939.215930] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[398943.670115] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398943.670128] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398946.673641] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398946.673653] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398956.703093] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398956.703110] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398958.717360] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398958.717374] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398966.703701] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398966.703719] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398973.711293] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398973.711308] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398976.711375] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398976.711388] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398986.738246] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398986.738260] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398988.745974] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[398988.745986] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[398989.955372] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[398996.733807] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[398996.733821] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399003.743048] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399003.743063] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399006.738874] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399006.738892] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399016.771143] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399016.771156] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399018.775314] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399018.775331] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399026.765506] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399026.765521] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399033.784113] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399033.784128] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399036.773596] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399036.773610] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399046.816619] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399046.816634] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399048.826929] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399048.826942] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399056.824640] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399056.824656] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399063.826979] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399063.826995] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399066.758591] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=51054 DF PROTO=TCP SPT=33770 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[399066.823690] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399066.823699] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399069.705779] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=51083 DF PROTO=TCP SPT=33770 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[399075.734824] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=98.211.77.79 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=112 ID=51230 DF PROTO=TCP SPT=33770 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0 
[399076.853829] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399076.853843] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399078.858017] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399078.858034] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399086.856822] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399086.856834] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399093.865140] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399093.865155] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399096.868516] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399096.868531] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399106.900106] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399106.900121] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399108.916622] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399108.916635] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399116.901485] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399116.901499] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399123.911618] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399123.911633] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399126.902206] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399126.902219] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399136.937906] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399136.937923] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399138.951414] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399138.951432] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399146.939540] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399146.939553] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399153.951889] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399153.951904] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399156.933509] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399156.933523] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399166.964470] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399166.964488] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399168.972778] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399168.972793] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399176.974112] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399176.974126] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399183.975266] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399183.975279] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399186.982621] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399186.982635] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399197.015600] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399197.015614] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399199.026228] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399199.026244] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399207.022750] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399207.022764] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399214.027491] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399214.027504] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399217.016956] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399217.016973] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399227.047246] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399227.047259] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399229.058465] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399229.058479] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399237.055170] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399237.055184] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399244.062836] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399244.062848] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399247.053299] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399247.053313] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399257.079104] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399257.079119] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399259.088852] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399259.088866] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399267.082555] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399267.082567] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399274.088881] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399274.088897] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399277.080298] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399277.080310] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399287.110771] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399287.110786] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399289.121097] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399289.121113] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399297.117806] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399297.117819] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399304.124753] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399304.124769] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399307.117192] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399307.117209] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399317.148323] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399317.148340] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399319.152601] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399319.152613] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399319.887995] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=204.236.211.224 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=115 ID=256 DF PROTO=TCP SPT=12200 DPT=1080 WINDOW=8192 RES=0x00 SYN URGP=0 
[399327.152592] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399327.152606] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399334.152515] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399334.152528] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399337.155407] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399337.155424] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399347.184323] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399347.184341] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399349.193160] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399349.193178] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399356.454852] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[399356.506803] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[399357.188718] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399357.188731] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399364.194028] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399364.194043] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399367.191951] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399367.191968] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399377.217128] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399377.217141] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399379.239751] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399379.239764] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399387.216561] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399387.216574] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399394.236505] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399394.236519] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399397.219159] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399397.219174] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399407.253762] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399407.253774] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399409.257338] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399409.257355] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399417.248523] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399417.248535] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399424.257651] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399424.257667] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399427.249322] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399427.249336] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399437.284874] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399437.284887] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399439.294386] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399439.294399] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399446.355949] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[399446.395102] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[399447.280143] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399447.280157] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399454.297608] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399454.297622] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399457.281187] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399457.281201] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399467.315333] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399467.315346] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399469.320382] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399469.320396] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399477.317828] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399477.317841] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399484.328042] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399484.328057] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399487.319962] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399487.319978] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399497.360594] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399497.360609] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399499.383742] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399499.383757] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399507.354861] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399507.354873] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399514.388228] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399514.388245] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399517.357032] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399517.357049] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399527.387282] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399527.387297] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399529.394024] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399529.394039] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399537.392208] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399537.392223] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399544.394688] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399544.394705] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399547.392928] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399547.392943] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399557.418896] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399557.418911] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399559.431237] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399559.431250] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399567.418605] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399567.418623] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399574.426455] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399574.426468] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399577.417845] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399577.417863] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399587.448674] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399587.448687] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399589.463801] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399589.463814] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399597.455133] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399597.455149] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399604.466680] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399604.466698] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399607.449473] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399607.449487] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399617.480119] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399617.480134] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399619.495288] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399619.495301] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399627.487096] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399627.487112] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399634.496003] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399634.496019] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399637.481350] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399637.481367] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399647.517570] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399647.517588] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399649.527590] martian source 169.254.1.255 from 169.254.1.33, on dev eth1
[399649.527605] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399657.513704] martian source 255.255.255.255 from 169.254.1.33, on dev eth1
[399657.513719] ll header: ff:ff:ff:ff:ff:ff:00:23:69:3d:b1:82:08:00
[399670.589299] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=95 TOS=0x08 PREC=0x60 TTL=110 ID=147 PROTO=UDP SPT=18730 DPT=57422 LEN=75 
[399674.623707] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=234 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399676.166282] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=263 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399679.156040] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=327 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399685.173235] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=428 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399692.657625] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=536 DF PROTO=TCP SPT=56989 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[399695.702616] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=569 DF PROTO=TCP SPT=56989 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[399697.956458] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=585 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399701.708213] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=677 DF PROTO=TCP SPT=56989 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[399720.139118] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[399720.192498] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[399789.490858] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=5745 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399792.525199] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=5876 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[399951.023331] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=14110 DF PROTO=TCP SPT=57914 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[399953.973660] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=14235 DF PROTO=TCP SPT=57914 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[399960.009043] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=14382 DF PROTO=TCP SPT=57914 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[400052.956506] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[400077.021424] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=18736 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[400078.522711] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=18819 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[400081.532560] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=18888 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[400087.539530] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=61 TOS=0x08 PREC=0x60 TTL=110 ID=19012 PROTO=UDP SPT=18730 DPT=57422 LEN=41 
[400089.661129] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[400222.034170] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=27468 DF PROTO=TCP SPT=58493 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[400231.034575] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=188.48.154.35 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=27929 DF PROTO=TCP SPT=58493 DPT=57422 WINDOW=65535 RES=0x00 SYN URGP=0 
[400309.575576] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=109.111.14.86 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=113 ID=37758 DF PROTO=TCP SPT=1276 DPT=4899 WINDOW=65535 RES=0x00 SYN URGP=0 
[400452.570931] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[400506.005260] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.46 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[400817.034225] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[400850.174928] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[400850.216206] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[400958.682073] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.156.168 DST=72.174.156.22 LEN=60 TOS=0x08 PREC=0x60 TTL=63 ID=8979 DF PROTO=TCP SPT=3835 DPT=23 WINDOW=5840 RES=0x00 CWR ECE SYN URGP=0 
[400961.669220] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.156.168 DST=72.174.156.22 LEN=60 TOS=0x08 PREC=0x60 TTL=63 ID=8980 DF PROTO=TCP SPT=3835 DPT=23 WINDOW=5840 RES=0x00 CWR ECE SYN URGP=0 
[401183.147408] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[401202.140513] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.46 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[401306.844080] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=69 TOS=0x08 PREC=0x60 TTL=63 ID=2698 PROTO=UDP SPT=50852 DPT=161 LEN=49 
[401307.674428] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=69 TOS=0x08 PREC=0x60 TTL=63 ID=2805 PROTO=UDP SPT=50852 DPT=161 LEN=49 
[401329.849774] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=3705 DF PROTO=TCP SPT=59117 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[401331.868011] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=3828 DF PROTO=TCP SPT=59117 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[401337.826174] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=4071 DF PROTO=TCP SPT=59117 DPT=80 WINDOW=8192 RES=0x00 SYN URGP=0 
[401351.864443] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=4476 DF PROTO=TCP SPT=59117 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[401352.851464] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=4572 DF PROTO=TCP SPT=59117 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[401358.900929] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=4835 DF PROTO=TCP SPT=59117 DPT=8080 WINDOW=8192 RES=0x00 SYN URGP=0 
[401395.949305] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[401395.995911] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=221.192.199.48 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=113 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[401412.949674] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=7427 DF PROTO=TCP SPT=59117 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[401415.927433] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=7537 DF PROTO=TCP SPT=59117 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[401421.902072] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=7765 DF PROTO=TCP SPT=59117 DPT=3389 WINDOW=8192 RES=0x00 SYN URGP=0 
[401433.929036] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=8275 DF PROTO=TCP SPT=59117 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[401436.909687] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=8407 DF PROTO=TCP SPT=59117 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[401442.909578] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=8677 DF PROTO=TCP SPT=59117 DPT=5900 WINDOW=8192 RES=0x00 SYN URGP=0 
[401456.852737] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=9226 DF PROTO=TCP SPT=59117 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
[401457.937096] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=9331 DF PROTO=TCP SPT=59117 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
[401465.859260] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=72.174.157.73 DST=72.174.156.22 LEN=48 TOS=0x08 PREC=0x60 TTL=63 ID=9632 DF PROTO=TCP SPT=59117 DPT=40080 WINDOW=8192 RES=0x00 SYN URGP=0 
[401917.249187] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0 
[401917.294089] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8090 WINDOW=8192 RES=0x00 SYN URGP=0 
[402161.898661] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=190.234.162.66 DST=72.174.156.22 LEN=60 TOS=0x08 PREC=0x60 TTL=49 ID=30446 DF PROTO=TCP SPT=4742 DPT=23 WINDOW=5808 RES=0x00 SYN URGP=0 
[402277.409200] Shorewall:net2fw:DROP:IN=eth0 OUT= MAC=00:80:ad:7f:d1:b3:00:0d:66:21:cc:01:08:00 SRC=222.45.112.59 DST=72.174.156.22 LEN=40 TOS=0x08 PREC=0x60 TTL=111 ID=256 DF PROTO=TCP SPT=12200 DPT=8085 WINDOW=8192 RES=0x00 SYN URGP=0
```

I noticed alot of "martian source" in there. Could that be the problem? Like a DoS on my lan? Looks like it is coming from a 169 address which might indicate a problem with my dhcp server?

Sorry my post was so long

---

### Post by mongr31 on 2010-01-31
bump

---

### Post by JetPack on 2010-02-19
It's probably a port scan from the internet - probably not your DNS server. I suggest you look at the TCP and IP information on the Cable Modem (if it has a log) and it will probably show something like port 12200 being scanned. Then just block the source address on the Cable Modem.

If you can't do this on the Cable Modem then re-arrange your network to put a firewall/router between the Cable Modem and the Ubuntu server. Then you can block bad traffic there without it affecting the LAN/WiFi performance.

---


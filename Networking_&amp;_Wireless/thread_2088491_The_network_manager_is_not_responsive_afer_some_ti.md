---
title: "The network manager is not responsive afer some time"
date: 2012-11-26
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2012-11-26
I've noticed the following issue with my Ubuntu 12.04 installation. After some time while the laptop is working the network manager becomes not responsive at all. For example: I can see the available wireless networks, but I can't disconnect from the current SSID and connect to another SSID, or I can't connect using my USB 3G modem. 
Loging out and than back loging into the session solve this. Any idea?

P.S. During all the time when I'm connected, I don't have issues with the connectivity.

---

### Post by lz1dsb on 2012-11-27
Hm... any idea where I should look for clues when this happens. I found that it's reproducible. Where's the log of the Network Manager?

---

### Post by lz1dsb on 2012-12-07
Just to give you an idea how it looks like when it hangs. The screenshot shows that at this moment,  the VPN sub menu is not available anymore. Instead of options, I just see a small grey rectangle. Also, when this happens I can't disconnect from the SSID I'm connected to (the connectivity itself isn't affected at all), practically the whole menu isn't responding at all. 
I noticed that this happens only when I'm using an external USB device for connectivity (I use DWA-131 and a Huawai 3G USB modem).
When I use the embedded wifi card, no issues...

---

### Post by steeldriver on 2012-12-07
Hmm... mine's been doing something similar - I think it's not network-manager itself, it's the nm-applet - I've resorted to restarting it when it misbehaves (it's just a user process, part of the gnome session I think):

```
pkill nm-applet
nm-applet 2>/dev/null &
```FWIW my version is

```
$ apt-cache policy network-manager-gnome
network-manager-gnome:
  Installed: 0.9.4.1-0ubuntu2
  Candidate: 0.9.4.1-0ubuntu2
  Version table:
 *** 0.9.4.1-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
```

This is on a laptop running an internal Intel card (driver=iwl4965)

---

### Post by lz1dsb on 2012-12-07
Looks like I have the same version, the only difference is that mine is 64 bit.
```
$ apt-cache policy network-manager-gnome
network-manager-gnome:
  Installed: 0.9.4.1-0ubuntu2
  Candidate: 0.9.4.1-0ubuntu2
  Version table:
 *** 0.9.4.1-0ubuntu2 0
        500 http://bg.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by alexandari on 2012-12-07
&#1047;&#1076;&#1088;&#1072;&#1089;&#1090;&#1080; &#1087;&#1080;&#1095;! &#1040;&#1079; &#1080;&#1084;&#1072;&#1093; &#1090;&#1086;&#1079;&#1080; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084; &#1087;&#1088;&#1077;&#1076;&#1080; &#1084;&#1085;&#1086;&#1075;&#1086; &#1074;&#1088;&#1077;&#1084;&#1077; &#1080; &#1084;&#1080;&#1089;&#1083;&#1103; &#1095;&#1077; &#1075;&#1086; &#1086;&#1087;&#1088;&#1072;&#1074;&#1080;&#1093; &#1082;&#1072;&#1090;&#1086; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1093; WICD netowork manager-&#1072;. &#1055;&#1088;&#1086;&#1073;&#1074;&#1072;&#1081;,&#1084;&#1086;&#1078;&#1077; &#1080; &#1076;&#1072; &#1080;&#1084;&#1072; &#1088;&#1077;&#1079;&#1091;&#1083;&#1090;&#1072;&#1090;&#1080; :)

---

### Post by lz1dsb on 2012-12-07
That's quite amazing. I think you've actually nailed this. Executing 
```
pkill nm-applet
nm-applet 2>/dev/null &
```
solves it! And you're right, it's not the Network Manager itself, it's just the nm-applet that is hanging. Throughout the execution of the above commands I haven't lost connectivity at all. 
Do you have any idea why this is happening, obviously this is a way to overcome it, but... can we avoid it from happening at all?

---

### Post by lz1dsb on 2012-12-07
> **alexandari said:**
> &#1047;&#1076;&#1088;&#1072;&#1089;&#1090;&#1080; &#1087;&#1080;&#1095;! &#1040;&#1079; &#1080;&#1084;&#1072;&#1093; &#1090;&#1086;&#1079;&#1080; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084; &#1087;&#1088;&#1077;&#1076;&#1080; &#1084;&#1085;&#1086;&#1075;&#1086; &#1074;&#1088;&#1077;&#1084;&#1077; &#1080; &#1084;&#1080;&#1089;&#1083;&#1103; &#1095;&#1077; &#1075;&#1086; &#1086;&#1087;&#1088;&#1072;&#1074;&#1080;&#1093; &#1082;&#1072;&#1090;&#1086; &#1080;&#1085;&#1089;&#1090;&#1072;&#1083;&#1080;&#1088;&#1072;&#1093; wicd netowork manager-&#1072;. &#1055;&#1088;&#1086;&#1073;&#1074;&#1072;&#1081;,&#1084;&#1086;&#1078;&#1077; &#1080; &#1076;&#1072; &#1080;&#1084;&#1072; &#1088;&#1077;&#1079;&#1091;&#1083;&#1090;&#1072;&#1090;&#1080; :)
&#1040;&#1084;&#1080; &#1076;&#1072;, &#1076;&#1086; &#1090;&#1086;&#1074;&#1072; &#1077; &#1076;&#1088;&#1091;&#1075; &#1087;&#1072;&#1082;&#1077;&#1090; &#1079;&#1072; &#1091;&#1087;&#1088;&#1072;&#1074;&#1083;&#1077;&#1085;&#1080;&#1077; &#1085;&#1072; &#1084;&#1088;&#1077;&#1078;&#1086;&#1074;&#1080;&#1090;&#1077; &#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;&#1080;, &#1073;&#1080; &#1090;&#1088;&#1103;&#1073;&#1074;&#1072;&#1083;&#1086; &#1076;&#1072; &#1088;&#1077;&#1096;&#1080; &#1090;&#1086;&#1079;&#1080; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;. &#1058;&#1088;&#1103;&#1073;&#1074;&#1072; &#1076;&#1072; &#1075;&#1086; &#1087;&#1088;&#1086;&#1073;&#1074;&#1072;&#1084; &#1085;&#1103;&#1082;&#1086;&#1081; &#1087;&#1098;&#1090;, &#1082;&#1086;&#1075;&#1072;&#1090;&#1086; &#1080;&#1084;&#1072;&#1084; &#1074;&#1088;&#1077;&#1084;&#1077;. &#1041;&#1083;&#1072;&#1075;&#1086;&#1076;&#1072;&#1088;&#1103; &#1079;&#1072; &#1080;&#1076;&#1077;&#1103;&#1090;&#1072; ;)

---


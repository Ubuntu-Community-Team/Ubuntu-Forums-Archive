---
title: "No connections, wired or wireless."
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Danz D Man on 2010-07-14
So, I have tried both Ubuntu Lucid Lynx (I believe that's the new name. 10.04) as well as Karmic Koala on a new Toshiba Satellite L645D-S4030, and neither of these have been able to successfully get me onto the internet. On 10.04, it is apparently able to connect to the wireless network, but there isn't any internet when I try to use Firefox. When I try to use a wired connection, nothing happens.

I'm not too new to Ubuntu, but I still don't know how much of it works. Any help would be appreciated.

---

### Post by DjSesso on 2010-07-14
If you go to command line and type "ifconfig" what does it show? Im guessing thats the command but I came from Rhat. I am installing ubuntu soon. If not someone will correct me.

---

### Post by Danz D Man on 2010-07-14
I'll do that when I get the new version installed, It's about finished now.

---

### Post by sethupathy on 2010-07-14
have any 'network proxy'...?

---

### Post by Danz D Man on 2010-07-14
Huh. Everything worked for a second (I was able to get online) but then it stopped.
Anyways, here's what is showing up.

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:12 errors:0 dropped:0 overruns:0 frame:0
TX Packets: 12 errors: 0 dropped: 0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

Wlan
Link encap:Ethernet HWaddr 20:7c:8f:02:f2:b3
inet6 addr: fe80::227c:8fff:fe02:f2b3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX Packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:220 (220.0 B)
Interrupt:16 Memory:ffffc90002830000-ffffc90002830100


I had to type all that. Fun.


EDIT: Oh, and Seth, not that I know of.

---

### Post by Danz D Man on 2010-07-14
Sorry for the bump, but I posted this late at night and didn't get an answer.

---

### Post by scottyb888 on 2010-07-24
Exact same problem. Toshiba Satellite L645D running Ubuntu 10.04. Same problems as you described exactly. Anyone??

---

### Post by Rhodie on 2010-08-18
Same problem here.  Anybody know how to resolve it?  ifconfig eth1 reports device not found.

---

### Post by Rhodie on 2010-08-18
I seem to have fixed it by downloading and installing the AR81Family linux driver from [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

---

### Post by meitetsuman on 2010-08-24
I entered ifconfig on the terminal, and got exactly what Danz got: lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:12 errors:0 dropped:0 overruns:0 frame:0
TX Packets: 12 errors: 0 dropped: 0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

I've been entering various things in the System / Preferences / Network Connections screens. Sometimes it tells me I'm connected, but Firefox can't connect to the internet. I have a Wubi installation, and I can access the internet without any problem via Windows Vista from the same computer. I'm trying to get my wired connection working.

I also had the same experience: it worked at first, then stopped working. Also my control bar at the bottom was doing weird stuff. My shut down button disappeared for a while and I don't have a Firefox icon. Changing my System / Preferences / Appearance got my shut down button back.

"ifconfig inet addr" on the terminal gave me "addr: Unknown host". "ifconfig HWaddr" gave me "HWaddr: error fetching interface information: Device not found"

---


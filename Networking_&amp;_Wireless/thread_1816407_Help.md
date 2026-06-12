---
title: "Help?"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by Missconfiguration on 2011-08-01
So I'm currently trying to fix my IBM think pad and well i posted a question early about this and didn't get much help from it so i've type in ifconfig -a and got the output of this eth0 link encap:ethernet HWaddr 00:09:6b:53:00:31BROADCAST MULTICAST MTU:1500 Metric:1RX packets:0 errors:0 dropped:0 overruns:0 frame:0TX packets:0 errors:0 dropped:0 overruns:0 frame:0collisions:0 txquelen:1000RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) irda0 Link encap:IrLAP HWaddr 00:00:00:00NOARP MTU:2048 Metric:1RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0collisions:0 txqueuelen:8 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) Lo Link encap: Local Loopback inet addr:127 .0.0.1 Mask:255.0.0.0inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1RX packets:12 errors:0 dropped:0 overrunes:0 frame:0 TX packets:12 errors:0 dropped:0 overrunes:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)so what now?

---

### Post by jal on 2011-08-02
Would you post that again please? Put the ifconfig output inside
CODE delimiters so we can read it without going cross-eyed?

I don't see an 'UP' in there for your eth0, or an IP address, try 
```
sudo ifconfig up 192.168.0.xxx
```

also, look in the system->Administration->network tools dialogue?

---

### Post by Missconfiguration on 2011-08-03
eth0 link encap:ethernet HWaddr 00:09:6b:53:00:31
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txquelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 

irda0 Link encap:IrLAP HWaddr 00:00:00:00
NOARP MTU:2048 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:8 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 

Lo Link encap: Local Loopback 
inet addr:127 .0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overrunes:0 frame:0 
TX packets:12 errors:0 dropped:0 overrunes:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)
 
 
Sorry about that , also i look there and notice that Using a modem to connect to the internet wasn't checked so i re-checked it and it didn't do much but i can't really find the network setting i don't think there are any besides the ones in firefox about the proxy settings which are already set to auto detect sorry for the late response

---

### Post by Missconfiguration on 2011-08-03
Also when i put in sudo ifconfig 182.168.0.xxx 
 
 
The output:
 
lo          link encap:loacl loopback 
            inet addr:1.0.0.1 Mask : 255.0.0.0
            inet6 addr: : : 1/128 Scope:Host 
            UP LOOPBACK RUNNING MTU:16436 Metric:1 
            RX packets : 8 errors :0 dropped:0 overruns:0 frame:0 
            TX packets : 8 errors :0 dropped:0 overruns:0 carrier:0 
            collisions :0  txqueuelen:0 
            RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

---

### Post by jal on 2011-08-04
> **Missconfiguration said:**
> Also when i put in sudo ifconfig 182.168.0.xxx 
 


My apologies, that command would not have worked. Try this instead:
```
ifconfig eth0 up 192.168.0.50
```

then do another ifconfig.

I'm not a network expert, these are just things that have worked for me.

I presume you have the cable in and there are lights flashing next to the cable ports?

---

### Post by jal on 2011-08-04
> **Missconfiguration said:**
> 
 
Sorry about that , also i look there and notice that Using a modem to connect to the internet wasn't checked so i re-checked it and it didn't do much but i can't really find the network setting i don't think there are any besides the ones in firefox about the proxy settings which are already set to auto detect sorry for the late response


I was referring to the Gnome System menu, on my Maverik setup it's in the bar at the top of the screen on the left 
there is the gnome symbol, then 
Applications Places System
and under System is Administration -> Network tools

ifconfig changes are temporary, this is a place to set up the network to work between restarts.

---

### Post by Missconfiguration on 2011-08-04
> **jal said:**
> I was referring to the Gnome System menu, on my Maverik setup it's in the bar at the top of the screen on the left 
there is the gnome symbol, then 
Applications Places System
and under System is Administration -> Network tools
 
ifconfig changes are temporary, this is a place to set up the network to work between restarts.
 Yes one is a green like then a flashy orange one , what do i do after iconfig? and i looked all i have is user and groups no admin

---

### Post by varunendra on 2011-08-06
Hi! Hope you haven't given up on it yet. Please post back the current result of the command:
```
ifconfig -a
```

Also-
```
lsb_release -a
```

and
```
sudo dhclient
```

A screenshot of your desktop may help us determine the position of correct icons/menus.

**Important: **Whenever you post an output of a terminal command, just copy the output selecting it with your mouse cursor, paste it in your new post here, then select only the pasted output and click on the # icon at the top of the box in which you type a new post. Doing this will automatically create [ code] and [ /code] tags around the selected text.

This makes your post tidy and the output more readable. Consider this as an important step.

---


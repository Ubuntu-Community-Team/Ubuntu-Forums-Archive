---
title: "failure to connect to internet occurs only at home"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by noamb on 2010-08-14
hello all, i have a problem connecting to the internet at home, but have no problem connecting to the internet in other places. My computer connect ot the router but does not receive a connection to the internet form the router. this happens both wireless and ethernet. at the same time everybody elses computers (using windows) connect to the internet in my home.  i have tried switching between two wireless cards, had the same problem. this makes me think it has something to do with the router itself. i use  a Planet WRT-413 router. thanks
noam

---

### Post by Elmer Fudd on 2010-08-14
First lets check for a DNS problem
Hook up to your router with an ethernet cable to eliminate possible wireless problems.

Do a traceroute to Yahoo.com


```
traceroute 98.137.149.56
```

post the results

---

### Post by noamb on 2010-08-14
when i write traceroute... i get the responce " the program 'traceroute' can be found in teh following packages 
* traceroute
* traceroute-nanog
unfortunately i can't get these without the internet connection working on the computers, unless there is a way i can get them on one of these other computers and use a flash drive to install it, but i don't really know how to do that.

---

### Post by grahammechanical on 2010-08-14
This is the only help I can offer. Do you have access privileges to connect to the internet? Go to System - Administration - Users and Groups. What account type are you listed as having? Go to advance settings - User privileges. Is there a check mark against Connect to internet using a modem, Connect to wireless and ethernet networks, or Use modems? You may not be set up as Administrator with all user privileges. You may be set up as "Custom"  with some privileges not checked.

regards.

---

### Post by Iowan on 2010-08-14
From a terminal (Applications>Accessories>Terminal), check **ifconfig -a** to verify the interface gets IP address. Then check **route -n** to see if the default route (usually bottom line - marked with UG) uses your router/gateway.

---

### Post by noamb on 2010-08-14
so i did both those things including pinging a few websites and trying to log into FTPs through terminal. my computer is communicating to some extant with tthe internet but not able to read the information properly. for instance after logging into a secured FTP, i wrote the command dir and it replied 200 POR command sucssesful but never wrote supplied the list of folders or files on the server. when i pinged yahoo it sucsessfuly communicated but the firefox browser never managed to do anything.
the software cener was unable to download sources (i thought maybe it has osmething to do with fire fox so i wanted to donwnload chromium). and skype reports after a few minuts of trying to connect that server connection failed. here are the results  thanks. noam
 
 
[RIGHT][/RIGHT]
[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][RIGHT]Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT]192.168.0.0 0.0.0.0 255.255.255.0 [/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]U 2 0 0 wlan0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT]169.254.0.0 0.0.0.0 255.255.0.0 [/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]U 1000 0 0 wlan0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT]0.0.0.0 192.168.0.1 0.0.0.0 [/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]UG 0 0 0 wlan0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT]
 [/RIGHT]
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][RIGHT]noam@noam-laptop:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:26:2d:b9:1c:69[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][FONT=Times New Roman] [/FONT]
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]UP BROADCAST MULTICAST MTU:1500 Metric:1[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]collisions:0 txqueuelen:1000[/SIZE][/FONT][/SIZE][/FONT][SIZE=2] 
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B[/SIZE][/FONT][/SIZE][/FONT][SIZE=2])
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]Interrupt:27 Base address:0xc000[/SIZE][/FONT][/SIZE][/FONT][SIZE=2] 
[/RIGHT]
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][RIGHT]lo Link encap:Local Loopback[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][FONT=Times New Roman] [/FONT]
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]inet addr:127.0.0.1 Mask:255.0.0.0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]inet6 addr: ::1/128 Scope:Host[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]UP LOOPBACK RUNNING MTU:16436 Metric:1[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]RX packets:340 errors:0 dropped:0 overruns:0 frame:0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]TX packets:340 errors:0 dropped:0 overruns:0 carrier:0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]collisions:0 txqueuelen:0[/SIZE][/FONT][/SIZE][/FONT][SIZE=2] 
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]RX bytes:10232 (10.2 KB) TX bytes:10232 (10.2 KB[/SIZE][/FONT][/SIZE][/FONT][SIZE=2])
[/RIGHT]
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][RIGHT]wlan0 Link encap:Ethernet HWaddr 00:13:02:2d:b2:43[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][FONT=Times New Roman] [/FONT]
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]inet addr:192.168.0.4 Bcast:192.168.0.255 Mask:255.255.255.0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]inet6 addr: fe80::213:2ff:fe2d:b243/64 Scope:Link[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]UP BROADCAST RUNNING MULTICAST MTU:1396 Metric:1[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]RX packets:2100 errors:0 dropped:0 overruns:0 frame:0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]TX packets:635 errors:0 dropped:0 overruns:0 carrier:0[/RIGHT]
[/SIZE][/FONT][/SIZE][/FONT][SIZE=2][RIGHT][/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]collisions:0 txqueuelen:1000[/SIZE][/FONT][/SIZE][/FONT][SIZE=2] 
[/SIZE][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2]RX bytes:677139 (677.1 KB) TX bytes:77967 (77.9 KB[/SIZE][/FONT][/SIZE][/FONT][SIZE=2])

 [/RIGHT]
[/SIZE]

---

### Post by Iowan on 2010-08-14
Unfortunately, the formatting made the post quite difficult to read.

Sometimes MTU can cause problems. Somewhere in [this]("http://ubuntuforums.org/showthread.php?t=1376506") thread is information about checking/setting MTU.

Finally found it  - looks like MTU for wireless is lower, but wired might still benefit.

---

### Post by noamb on 2010-08-15
sorry for ignorance, what is MTU and how should i change the settings of it?

---

### Post by Iowan on 2010-08-15
[Here]("http://en.wikipedia.org/wiki/Maximum_transmission_unit") is the Wikipedia page on MTU. This [link]("http://ubuntuforums.org/showthread.php?t=1376506") covers checking/changing.

---

### Post by noamb on 2010-08-15
thanks so much for the help and for the patiance. so i think i got the MTU subject, and i did the tests following the thred, it all looked very similar except after i found my "proper" mtu which was 1472, i adjusted it, and and tried surfing, and the result is the same. did hte same tests, and found that the "proper mtu was actually lower, and adjusted it to the right one agin, every step of the way checking for the right mtu (being the highest that will result in 1 package transmitted 1 pacage received 0 errors) and each time i adjusted it, the "proper mtu became lower than the one i adjusted it to. i checked the router MTU and its set to 1500, so it should be good to be on anything lower than say 1450 right? but now i am on lower than 1300 and its not working.

---

### Post by noamb on 2010-08-15
also another piece of information that might be useful is that when i typed the seconf command line (after "sudo ifconfig eth0 mtu 1372") "ifconfig | grep MTU" i got three lines instead of the two the person in the other thred got
instead of getting only 
 "up broadcast  running multicast mtu:1372 Metric:1" 
 "up broadcast  running mtu:16436 Metric:1" i got a third one which was the same as the original except it repeated the original MTU number which in this particular test was
"up broadcast  running multicast mtu:1424 Metric:1"

---

### Post by Elmer Fudd on 2010-08-18
Please confirm:
Your access to the net works well at multiple other locations. Not just at work.
Multiple computers can simultaneously access the net through your WRT-413 at the same time that you have trouble. 

Can you post the computer model, wireless hardware, any restricted network drivers and Ubuntu version/kernel for the computer on which you are having trouble.

Do you dual boot windows? If so, does Windows work with home wireless?

Are you able to log into the WRT-413 config/status pages?
From your browser it will be 192.168.0.1 with a blank password if you have not changed it.

Lets find out if you:
-are using encryption (which - wep, wpa)
-have it set up for mixed mode (b , bg)
-can see what clients are hooked up while win clients are using the WRT

---

### Post by noamb on 2010-08-20
i do have access to the internet through a large variety of wierless connections. my home router corrently works on daily bases with at least 4 other computers, 2 as  wireless and 2 as land line but on the occasional appearance f a guest it works for them as well. my computer model is presario cq60-4615DX, though i use a different wierless card than the original. i use the one from my old laptop because it has a longer range. (the problem is the same with bot cards. i don't have windows instaslled but i ahve to distributions installed, lucid and karmic. again problem percists regarless.

when using anthe rcomputer i can access the router(i do have password) router is set up WEP ecurity mode, both b and g  are enabled. and i can see all computer that are hooked up in including my laptop(which again, connects to router, but does not actuallty connect to internet).

thanks again
N

---

### Post by noamb on 2010-08-22
thanks for all the help, i ended up opting for the easiest option, i changed my router and it got sorted out. thanks for the help any way.

---


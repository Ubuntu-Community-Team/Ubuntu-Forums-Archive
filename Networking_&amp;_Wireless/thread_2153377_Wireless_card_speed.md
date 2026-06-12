---
title: "Wireless card speed"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by stribor40 on 2013-06-10
I was hoping someone will help me understand this. I have router Linksys EA4200 that supports up to 300 Mbps.
My cable modem is plugged into router. My download speed from ISP is 20Mbps. I tested that speed and it is what I am getting. 
Speed on link (router to wireless client) as I am aware depends on many factors (client wireless card,distance,walls,interferance etc). I know that speed I should be getting should not be anywhere near 300Mbps but when I run this command ```
sudo iwconfig wlan0
``` I get following output 
```
wlan0     IEEE 802.11bgn  ESSID:"My Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:47:0E:DF   
          Bit Rate=58.5 Mb/s   Tx-Power=14 dBm   (occasinaly I would get Bit rate 65 mb/s)
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2981  Invalid misc:70   Missed beacon:0

```

I am concerned here about excessive retries and invalid misc. I also read that power management should be set to off. 
Can anyone maybe offer some suggestions as why is my bit rate so low and what can I do to imporove it. This is my router setting on the band that I am connected to...

```
[TABLE="class: FUNCTION_MAIN"]
[TR]
[TD="class: TITLE2"]2.4 GHz Wireless Settings[/TD]
[TD="class: TITLE_IMG"][/TD]
[TD="class: FUNNAME2"] [FONT=Arial]Network Mode: [/FONT][/TD]
[TD="class: FUNFIELD"]  Mixed [/TD]
[/TR]
[TR]
[TD="class: TITLE2"][/TD]
[TD="class: TITLE_IMG"][/TD]
[TD="class: FUNNAME2"] [FONT=Arial]Network Name (SSID): [/FONT][/TD]
[TD="class: FUNFIELD"]My Network
[/TD]
[/TR]
[TR]
[TD="class: TITLE2"][/TD]
[TD="class: TITLE_IMG"][/TD]
[TD="class: FUNNAME2"] [FONT=Arial]Channel Width: [/FONT][/TD]
[TD="class: FUNFIELD"]  20 Mghz only[/TD]
[/TR]
[TR]
[TD="class: TITLE2"][/TD]
[TD="class: TITLE_IMG"][/TD]
[TD="class: FUNNAME2"] [FONT=Arial]Channel: [/FONT][/TD]
[TD="class: FUNFIELD"]  Auto[/TD]
[/TR]
[TR]
[TD="class: TITLE2"][/TD]
[TD="class: TITLE_IMG"][/TD]
[TD="class: FUNNAME2"] [FONT=Arial]SSID Broadcast: [/FONT][/TD]
[TD="class: FUNFIELD"]         [TABLE]
[TR]
[TD]**Enabled**[/TD]
[TD][/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: TITLE2"][/TD]
[TD="class: TITLE_IMG"][/TD]
[TD="class: FUNNAME1, colspan: 2"][/TD]
[/TR]
[/TABLE]

```

Can anyone suggest what and how to improve this speed.

Thank you

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by stribor40 on 2013-06-10
Sorry I should have put the security there. Security Mode is WPA2 Personal
I changed the channel to "Auto (20 or 40 Mghz)" but speed is still  Bit Rate=58.5 Mb/s

---

### Post by ahallubuntu on 2013-06-10
~

---

### Post by stribor40 on 2013-06-11
Yes it is AES. Regarding the speed 
Shouldnt speed from outside internet to my router be 20mbps max(which i have). 
Speed from router to wireless client should be up to 300mbps.  What is the speed that should be from router to client? Speed advertised for the router or speed from isp which is 20mbps

---


---
title: "Wireless Lan problem"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by xx001880 on 2010-09-29
I have a wireless lan with internet conection in my home. I recently installed ubuntu and i can connect to the internet by wireless but when i do it, after some seconds, the wireless lan seems to go down.. i say this because the internet in my brother's pc goes down to. i installed the driver for the modem hardware by the code install sl-modem-daemon that i saw somewhere in a forum in the internet but the problem remains. this only happens in ubuntu,i use windows to and i don't have this issue. any help please? 
thanks

---

### Post by FluidBlow on 2010-09-29
Well, many problems can cause this trouble. I think the first thing to check is the log viewer. (System > Administration > Log file viewer) and check if a message appear when your connection crash.
Second thing is type "iwconfig" in a terminal (and post the result here) and do the same with "ifconfig wlan0" .

---

### Post by xx001880 on 2010-09-29
> **FluidBlow said:**
> Well, many problems can cause this trouble. I think the first thing to check is the log viewer. (System > Administration > Log file viewer) and check if a message appear when your connection crash.
Second thing is type "iwconfig" in a terminal (and post the result here) and do the same with "ifconfig wlan0" .

  	 	 	 	p { margin-bottom: 0.21cm; }  

 Sep 29 18:56:29 ubuntu kernel: [  591.667442] wlan0: direct probe to AP 00:0c:f6:37:00:40 (try 1) 
 Sep 29 18:56:29 ubuntu kernel: [  591.671734] wlan0: direct probe responded 
 Sep 29 18:56:29 ubuntu kernel: [  591.671744] wlan0: authenticate with AP 00:0c:f6:37:00:40 (try 1) 
 Sep 29 18:56:29 ubuntu kernel: [  591.673566] wlan0: authenticated 
 Sep 29 18:56:29 ubuntu kernel: [  591.673609] wlan0: associate with AP 00:0c:f6:37:00:40 (try 1) 
 Sep 29 18:56:29 ubuntu kernel: [  591.675819] wlan0: RX AssocResp from 00:0c:f6:37:00:40 (capab=0x411 status=12 aid=2) 
 Sep 29 18:56:29 ubuntu kernel: [  591.675826] wlan0: AP denied association (code=12) 
 Sep 29 18:56:29 ubuntu kernel: [  591.675850] wlan0: deauthenticating from 00:0c:f6:37:00:40 by local choice (reason=3)
 

 wlan0     Link encap:Ethernet  Endereço de HW 00:1c:bf:3d:b5:3b   
           inet end.: 192.168.0.101  Bcast:192.168.0.255  Masc:255.255.255.0 
           endereço inet6: fe80::21c:bfff:fe3d:b53b/64 Escopo:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Métrica:1 
           pacotes RX:759 erros:0 descartados:0 excesso:0 quadro:0 
           Pacotes TX:768 erros:0 descartados:0 excesso:0 portadora:0 
           colisões:0 txqueuelen:1000  
           RX bytes:514545 (514.5 KB) TX bytes:169814 (169.8 KB) 
 

 lo        no wireless extensions. 



  
 eth0      no wireless extensions. 



  
 wlan0     IEEE 802.11abg  ESSID:"Sitecom"   
           Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0C:F6:37:00:40    
           Bit Rate=54 Mb/s   Tx-Power=13 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off 
           Power Management:off 
           Link Quality=70/70  Signal level=-29 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0


  
 pan0      no wireless extensions. 



here is what appears

---

### Post by FluidBlow on 2010-09-29
Well, there is something strange...
The log tells you " AP denied association (code=12)" so it is the reason that you cannot connect proprely, and as we can see later, "deauthenticating from 00:0c:f6:37:00:40 by local choice (reason=3)" whereas the *iwconfig* says "Access Point: 00:0C:F6:37:00:40".
In the few seconds you are connected, can you load webpages ? (or ping a server) I mean, is this a true connection or this is just the network manager telling you are connected ?

---

### Post by xx001880 on 2010-09-30
i really can access web pages,but just for a short period of time.

---


---
title: "Wireless connection requires router reboot"
date: 2011-02-11
forum: Networking &amp; Wireless
---

### Post by Cloud7734 on 2011-02-11
I was having an issue with my wireless connection last week, and sometimes even my hardwired connection. It had seemed like every time my PC went into standby, or any low-power mode, the WiFi would stop working. I used the "power off" command and got it back and running. This week it's a whole new problem, lol. 

When I boot up the computer in the morning, I am unable to connect until I reset the wireless router. Unfortunately, I did not have the presence of mind to get iwconfig first thing in the morning, but I did reboot the laptop and grabbed iwconfig before I connected and after I connected. Now, for some reason, the router worked when I rebooted, but I had to reset it this morning. Any ideas? iwconfig below:

****Before Connect****
jake@jake-laptop:~$ sudo iwconfig eth1
[sudo] password for jake: 
eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

****After Connect****
jake@jake-laptop:~$ sudo iwconfig eth1
eth1      IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:A8:2D:DE   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-37 dBm  Noise level=-57 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by grahammechanical on 2011-02-11
First, it is a feature not a fault. The machine is designed to switch off the wireless adapter when it goes into low power or standby mode, otherwise it would not be low power mode. It would become flat battery mode.

Second, why do you think that the operating system is at fault when you need to reset the router in order to get a connection?

A router reset will initiate a broadcast that will be detected by Network Manager, which will then make a connection. Is the connection set to connect automatically? If not then you will need to activate the connection for Network Manager to scan for a wireless network to connect to.

Regards.

---

### Post by Cloud7734 on 2011-02-11
I guess I should've explained my actions a little huh? Lol. I diagnosed the power-off feature as a hunch. I don't have hard evidence, but I believe eth1 was failing to power on after coming out of standby mode. It seemed to do the trick for a couple days.

I am suspecting the OS and not the router because my fiance has a Mac that is able to connect any time of the day and I've connected with my Android phone. The Linux box is the only one having this issue.

I disabled auto connect during the troubleshooting process and haven't re-enabled it. I have been connecting manually by selecting the router from the drop-down list in Network Manager.

Thanks for responding graham!

---

### Post by ajgreeny on 2011-02-11
Go back to a right click on Network manager ->Edit connections, and make sure both "Available to all users" and Connect automatically" are selected.  That should do it, but if not come back once again.

---

### Post by Cloud7734 on 2011-02-11
Neither settings were selected so I did so. Rebooted my laptop and it came right up. Tomorrow morning will be the real test. Thanks aj! I'll follow up tomorrow.

---

### Post by Cloud7734 on 2011-02-11
K, I closed my laptop and it went into standby mode. I've done this a few times without fail today, but the last time my connection dropped again. I checked the settings and everything was fine. I tried the "power off" command and still nothing. Rebooted the computer and nothing. Tested the internet on other computers and was Tx/Rx'ing. Cycled power to the router and the connection came back. So my question is, what exactly happens during a router reboot? The only difference I see is that the access point is assigned when I'm connected. Is it possible that either my router or Network Manager are failing to assign the access point? If so, what options do I have?

---

### Post by Cloud7734 on 2011-02-12
I noted the access point while connected and am planning on trying to set it manually and see if that helps. Can anyone shed some light on this situation? If manually entering the access point does the trick, what could be stopping it from automatically setting it and how could I remedy that?

---

### Post by Cloud7734 on 2011-02-15
Can anyone please help me with this issue? I've had to reset the router everyday since my last post. Is there anyone who can give me some other tips on fixing this?

---

### Post by Cloud7734 on 2011-02-19
K, here's a question someone might be able to actually answer: What is this forum for exactly? I thought it was for support but obviously I was mistaken. Is it a less flashy facebook or what? 

Seriously, can no one help me? I've been watching a couple other threads as well, also from Ubuntu noobs, and no answers. I've had people outside of the forum tell me to switch back to Windows. I'm starting to wonder if that's a good move.

---


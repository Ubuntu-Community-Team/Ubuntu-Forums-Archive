---
title: "SOS: Ethernet not work"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by zaid alaa on 2010-06-05
hi 
i was instelling ubuntu 8.10 on my laptop type HP (nx6110) but the Ethernet and the wireless are not work.
i was used the *nm-tool *on terminal
the code is 


zaid@zaid-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            NULL(info.linux.driver)
  State:             unavailable
  Default:           no
  HW Address:        00:12:79:C4:F3:00

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Settings


- Device: wlan0 --------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            NULL(info.linux.driver)
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Supported:       yes

  Wireless Settings
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points



plese...someone help me to solve the problem 

thank you

---

### Post by Detonate on 2010-06-05
See my post #7 in this thread.

[http://ubuntuforums.org/showthread.php?t=1494628](http://ubuntuforums.org/showthread.php?t=1494628)

---

### Post by zaid alaa on 2010-06-05
hi 
can you tell me how to get my network card up and running

---

### Post by Detonate on 2010-06-05
Open a terminal and run:
```
ifconfig -a
```

and copy the results and post in a reply to this message.

---

### Post by zaid alaa on 2010-06-06
hi
i was run *ifconfig *and the results are

 ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

and  i was run the *ifconfig -a*

zaid@zaid-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:12:79:c4:f3:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)

pan0      Link encap:Ethernet  HWaddr 96:9c:75:9f:a3:92  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:ad:db:19  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-AD-DB-19-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

and i was run ths *kdesudo kate /etc/network/interfaces*

zaid@zaid-laptop:~$ kdesudo kate /etc/network/interfaces
The program 'kdesudo' is currently not installed.  You can install it by typing:
sudo apt-get install kdesudo
bash: kdesudo: command not found
zaid@zaid-laptop:~$ sudo apt-get install kdesudo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kdesudo

---

### Post by Detonate on 2010-06-06
Are you using Ubuntu or Kubuntu?

If you are using Ubuntu the command would be 

```
gksu gedit /etc/network/interfaces
``` to edit the interfaces file.

---

### Post by zaid alaa on 2010-06-06
hi 
i was do all the step in your post #7 but till now the ethernet not work

---

### Post by Detonate on 2010-06-06
Did you restart the network?  What does ifconfig show now?

---


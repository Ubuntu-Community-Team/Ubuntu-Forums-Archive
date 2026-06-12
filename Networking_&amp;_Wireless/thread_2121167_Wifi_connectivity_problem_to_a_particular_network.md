---
title: "Wifi connectivity problem to a particular network"
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by jovin555 on 2013-03-01
i have a WiFi connectivity problem to a particular network in ubuntu12.04 in my Laptop(HPpavilion g6).i can connect to WiFi at my home.but at my office it doesn't connect.i have entered the right password but still it just shows connecting and then shows wireless disconnected.the wifi device is detected and then it asks for password.but it doesn't connect.My friends laptop is getting connected.Can anyone help me to solve this problem?

---

### Post by bellaseem on 2013-03-01
This happened to me once. I think it's a glitch in the network manager... but not sure why. Anyway what I did is I clicked the Network button on the top right, then clicked edit connections, then deleted the network settings that were saved, and tried to connect again, and it worked (the automatic connection was not able to connect on its own). I don't know if the manger saves the network in your case... Also are you sure that no MAC filtering is enabled at your work that prevents you from connecting? You might also want to try connecting using WICD instead of the default network manager that comes with ubuntu. If you have windows, try connecting using windows to see if this is possibly a driver problem. If you have an old card, maybe it doesn't support all encryption types (try installing hwinfo and type in hwinfo --netcard to see what encrpytion types your card supports). I hope I'm right on this and that this helps.

---

### Post by jovin555 on 2013-03-01
i tried WICD.but it also ddnt work.i have windows 7 and wifi is working in it perfectly.i also tried what you said by deleting all networks.but then also it ddn't work

---

### Post by turvalyon on 2013-03-01
i have a WiFi connectivity problem like yours .I've awus036nhr using  8192cu driver .I could see & connect to ap but no internet access even  the pass was true.And Now prompting pass box eachtime and I cant connect If you can find a way man please share here thnx

---

### Post by bellaseem on 2013-03-01
Ok, since it's working on windows 7, then use ndiswrapper to install the windows driver on Ubuntu... Look up a tutorial on how to install the driver of your particular wireless lan card online (there are many). There's also a comprehensive troubleshooting guide on this forum that you should look at if you run into any problems...

---

### Post by turvalyon on 2013-03-01
First of all thank you very much for your post.Before reading your post something happened : I reinstall ubuntu 12.10 .I tried to connect to the Ap it's ok but if you make it manally otherwise prompts begin.When I connected first -sudo apt-get update- while it was updating it failed before completed.My wifi behaves half-heartedly but in windows they make love.
        > iwconfig
  wlan0   IEEE 802.11bgn  ESSID:"TP-LINK_463640"  

            Mode:Managed  Frequency:2.412 GHz  Access Point: 90:F6:52:46:36:40   

            Bit Rate=150 Mb/s   Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
            Power Management:off
            Link Quality=69/70  Signal level=-41 dBm  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:66   Missed beacon:0
   
  lo        no wireless extensions.
   
  [FONT=&amp]eth0      no wireless extensions.[/FONT]  
> :~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:06:5f:b2 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:229 errors:0 dropped:0 overruns:0 frame:0


 Now I read your post and go for ndiswrapper...

---


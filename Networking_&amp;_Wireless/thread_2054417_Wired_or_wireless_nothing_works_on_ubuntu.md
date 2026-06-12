---
title: "Wired or wireless nothing works on ubuntu"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by enezx on 2012-09-07
I recently installed ubuntu 12.04 on my "new" dell inspiron with dual boot - both windows and now ubuntu.
But internet does not work on ubuntu - wired and wireless both. It works fine on windows but not on ubuntu. 
What to do? I'm tired of switching to windows everytime I want to use internet

---

### Post by chili555 on 2012-09-07
Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by LiamOS on 2012-09-07
It might also be helpful to post the output of 
```
ifconfig -a
```

---

### Post by enezx on 2012-09-08
**lspci -nn | grep -e 0200 -e 0280:-**
  02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
  03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
   
   
   
   
  **rfkill list all:-**
  0: dell-wifi: Wireless LAN
              Soft blocked: no
              Hard blocked: no
  1: dell-bluetooth: Bluetooth
              Soft blocked: no
              Hard blocked: no
              
              
              
  **ifconfig -a:**-
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:156 errors:0 dropped:0 overruns:0 frame:0
            TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0
            RX bytes:11904 (11.9 KB)  TX bytes:11904 (11.9 KB)

---

### Post by chili555 on 2012-09-08
Woo hoo! Congratulations! This is your luck day! We just won the lotto!!! You have two unsupported devices. Because there is no easy way to get one working, it is difficult to get the other working.

Your wired ethernet uses the elusive driver *alx*. I just worked on a similar case and the poster reports success and here is a link. I know it is an arduous process but it can be done. Once it's finished, we can tackle the even harder wireless!

[http://ubuntuforums.org/showpost.php?p=12206899&postcount=6](http://ubuntuforums.org/showpost.php?p=12206899&postcount=6)

Post back if you get stuck.

---

### Post by enezx on 2012-09-09
I got the build essential. It came 64-bit so I donwloaded that one.
As for the generic header package - I dont know what to do. There is no option for 3.2.0-23-generic.

Its really tough switching from windows to ubuntu time to time!!!

---

### Post by chili555 on 2012-09-09
Please check here: [http://packages.ubuntu.com/precise/devel/linux-headers-3.2.0-23-generic](http://packages.ubuntu.com/precise/devel/linux-headers-3.2.0-23-generic)

> Its really tough switching from windows to ubuntu time to time!!! In my opinion, networking is the toughest but once it's fixed, things get a lot smoother. As well, I expect that both of your devices will be supported soon. Then Ubuntu will be so easy it's almost boring. It just works for most of us.

Post back if you are stuck. I'm ready to help.

---


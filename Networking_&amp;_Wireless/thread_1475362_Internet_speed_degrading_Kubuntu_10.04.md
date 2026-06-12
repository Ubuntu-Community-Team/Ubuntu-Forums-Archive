---
title: "Internet speed degrading Kubuntu 10.04"
date: 2010-05-06
forum: Networking &amp; Wireless
---

### Post by loki993 on 2010-05-06
Ive been having an issue with Kubuntu. I'm currently running 10.04, but I had the same problem with 9.10 as well. 

What happens is Ill startup and I can check the speed and its fine, averages 5.10mbps. After I start downloading stuff Ill notice a significant speed drop and it seems like it starts to take forever to download anything. Ill stop all downloads and check the speed again and it will be hovering around 1.2 mbps. I suspect its actually even slower while downloading though. Restart the computer and the speed is good again. What could cause this? 

I'm on a laptop using an atheros wireless card running madwifi drivers. Ive done the same thing with a windows install and I experience no speed loss so its definitely isolated to my Kubuntu load. 

Any ideas?

---

### Post by loki993 on 2010-05-07
Think I got this one figured out. Ill try it out again tonight to be sure.

---

### Post by EricDP on 2010-05-08
If you solved it, please post your solution. I have the same problem.

---

### Post by loki993 on 2010-05-08
Well first think I did was change my MTU to 1400.

 sudo ifconfig ethX mtu 1400. ethx is the is whatever interface you want to change, ath is wireless probably. 

I though this worked and it seemed to the first night, but last night I had the same problem. Last night it didnt matter what MTU I used, so that wasnt my problem

My problem is distance from the router. In my living room I'm fine I get full speed. When I go in my bedroom it drops to 1.2. 

so I'm back at square one. This doesnt happen with windows, just linux. 

Anybody have any ideas?

---


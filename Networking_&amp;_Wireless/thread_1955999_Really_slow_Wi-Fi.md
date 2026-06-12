---
title: "Really slow Wi-Fi"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by Jaxke on 2012-04-10
Greetings gents.

I did a clean install on Ubuntu couple days ago, and was freaked out how slow my internet was. When I go to my Windows partition, the internet speed is blazing fast(Firefox) and pages load in one or two second at tops. But now, when I go to internet with Ubuntu(Chromium & FF), I sometimes(randomly, not always) have to wait literally tens of seconds. Well, usually it's not that slow, maybe five seconds or so.

I'm using wireless, and my router is up-to-date. I tried [this]("http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/"), but it didn't fix anything. 

And also, it's not just pages loading, it's also downloading files. I'm currently downloading 173mb file and it's already taken 17 minutes and one to come. 

Any help appreciated! I really don't wanna go back to Windows :D

---

### Post by raja.genupula on 2012-04-10
please post the  output of this 

```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep -i wlan
ifconfig -a
iwconfig
rfkill list all
```

---

### Post by sffvba[e0rt on 2012-04-10
*Thread moved to **Networking & Wireless**.*


404

---

### Post by Jaxke on 2012-04-10
> **raja.genupula said:**
> please post the  output of this 

```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
dmesg | grep -i wlan
ifconfig -a
iwconfig
rfkill list all
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TP-LINK"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F8:D1:11:31:1F:63   
          Bit Rate=270 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

---

### Post by jadtech on 2012-04-10
really you concider 5 or 10second to load slow ??? 

as far as packages from the software center and software upgrades they are not only loading but they are installing and cleaning up as well before they finish ...

---

### Post by raja.genupula on 2012-04-10
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```

do them

---

### Post by Jaxke on 2012-04-10
> **raja.genupula said:**
> ```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up

```do them
Thanks. Ran 'em all. Let's hope I'll get better speeds. :guitar:

---

### Post by raja.genupula on 2012-04-10
you tried them ?

---

### Post by Jaxke on 2012-04-10
> **raja.genupula said:**
> you tried them ?
Yeah. No difference :(

---

### Post by wildmanne39 on 2012-04-14
Hi, sorry it has taken me so long to reply I was out of town all week. 

Please post the out put of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by RvShaitan on 2012-04-14
I don't know if he resolved his problem but I am having the same one! Does this info help? or should I start a new thread?

```
wlan0     IEEE 802.11abgn  ESSID:"ATT792"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:A2:DD:75:20   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:0   Missed beacon:0

```

---

### Post by RvShaitan on 2012-04-14
I don't know if he resolved his problem but I am having the same one! Does this info help? or should I start a new thread?

```
wlan0     IEEE 802.11abgn  ESSID:"ATT792"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:A2:DD:75:20   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:0   Missed beacon:0

```


Sorry for double post. Having loading/dns issues related to the problem.

---

### Post by wildmanne39 on 2012-04-15
Hi RvShaitan, post the output from the commands in my last post.
Thanks

---


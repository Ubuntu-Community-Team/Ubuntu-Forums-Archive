---
title: "My internet keeps dropping randomly."
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Cheater87 on 2010-01-04
I'm using Ubuntu 9.04 64 bit on an Asus laptop and the wireless connection disconnects randomly for a while and keeps searching for the signal. When it finds it I have to put in my WEP key again to get it to connect sometimes only once or sometimes 2 or 3 times. This is getting quite annoying. What can I do to stop this?

---

### Post by Cheater87 on 2010-01-05
bump

---

### Post by jonaskarlsson on 2010-01-05
You could make it connect automatically, doesn't solve the problem but is not as inconvenient at least.

---

### Post by Cheater87 on 2010-01-05
It does connect automatically when I turn on the laptop. The problem is having it staying connected.

---

### Post by mvalenti on 2010-01-05
Had that happen to me. It was an issue with cordless phones close to the same bandwidth. Try changing the router channels until it gets better. Hope this helps.

---

### Post by Cheater87 on 2010-01-05
I do have cordless phones down and upstairs so that might be it. How do I change the router channels?

---

### Post by Kevbert on 2010-01-05
Please post the output of 
```
iwconfig
```
as soon as you are connected. It may be signal strength (or interference as stated earlier). What is the make/manufacturer/model of the router that you are connecting to ?  Can you connect to it via a cable (in order to change the channel) ?

---

### Post by Cheater87 on 2010-01-05
dan@dan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"ZSRC3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:F2:A5:D8   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dan@dan-laptop:~$

---

### Post by shairozan on 2010-01-05
What kind of router do you have? If it's a linksys you'll have to log into it and change it in the wireless settings. The RSM wireless band only has three channels that don't overlap, 1, 6, and 11. 

I would recommend changing the router to use channel 1 and see if that helps anything. It'll rule out the phone interfering with the signal.

---

### Post by Cheater87 on 2010-01-05
*Knocks on wood* I have not had it disconnect today so far. ^_^ Its Verizon.

---

### Post by Kevbert on 2010-01-06
Signal (link) quality seems a little poor. How far away is the Verizon router/source ? Are you using the PC in a different room ? If you can do it an external aerial for the wireless may help at either the router or PC end.
Take a look at [[COLOR="Red"]this[/COLOR]]("http://www.overstock.com/Electronics/Eforcity-2-pack-Wi-Fi-Wireless-Antenna-Router-Signal-Booster/4486174/product.html?cid=133635").

---

### Post by Cheater87 on 2010-01-10
I'm usually 2 rooms away when downstairs or upstairs in my room when it happens. I tried disconnecting the wireless phones from the receivers and that seemed to help a bit or maybe its just a coincidence. What if I aimed the antennae to the direction I am? Right now IIRC its to the right and i'm always to the left of it.

---

### Post by Cheater87 on 2010-01-16
Got 5 disconnections in a row last night. I looked up wireless signal dropping in Ubuntu 9.04 on google and it seems a pretty good amount of people have this and its a bug. I hope it gets fixed in the next release.

---


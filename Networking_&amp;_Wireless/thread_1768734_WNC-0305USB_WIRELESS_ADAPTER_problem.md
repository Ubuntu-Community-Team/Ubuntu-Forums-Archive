---
title: "WNC-0305USB WIRELESS ADAPTER problem"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by leonidas300 on 2011-05-27
I'm using WNC-0305USB WIRELESS ADAPTER because my acer aspire 1520 card doesn't work. There was a problem with the adapter to see wireless networks. I fix it using (which I should run it every time I log on) :
```
rfkill unblock wifi
rfkill list
sudo ifconfig wlan0 up
```
Then I managed to see my wireless network but I didn't manage to connect.
I used the following commands but It didn't return any message or error.
```
sudo iwconfig wlan0 essid CONNX
sudo iwconfig wlan0 key s:1234567890123
sudo dhclient wlan0
```
What is going wrong? How can I connect?

There is a thread in greek ubuntu forum where you can see some information (results from dmesg, lsmod etc.) for my laptop:[http://forum.ubuntu-gr.org/viewtopic.php?f=39&t=18422]("http://forum.ubuntu-gr.org/viewtopic.php?f=39&t=18422")

---


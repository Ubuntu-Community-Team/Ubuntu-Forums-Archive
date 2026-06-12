---
title: "Cannot connect to local network"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Ad1217 on 2011-08-08
Hello, I have been having this problem for a while. I can connect to the internet through wifi, but I cannot connect to anything on my network. I have a printer and a NAS, so I would really like for this to work again. I have a dell laptop with a Broadcom card. Thank you!

---

### Post by Ad1217 on 2011-08-08
anyone?

---

### Post by lkjoel on 2011-08-09
Install Wireshark 1.6.0 ([http://wp.me/p1EtsL-1l](http://wp.me/p1EtsL-1l)), and see if you can see your printer and your NAS there.

---

### Post by Ad1217 on 2011-08-09
well... I cannot ping/be pinged by any other computer on the network.

---

### Post by lkjoel on 2011-08-09
Run Wireshark, capture on all interfaces (interface name should be: any), let it run for 5-10 minutes, stop the capture, then click on Save.
Then could you attach the saved file?

---

### Post by fdrake on 2011-08-09
i think you have to run with sudo ???(@lkjoel correct me if am wrong.)   otherwise it wont's show up your interfaces.
```

sudo wireshark
```

---

### Post by lkjoel on 2011-08-09
> **fdrake said:**
> i think you have to run with sudo ???(@lkjoel correct me if am wrong.)   otherwise it wont's show up your interfaces.
```

sudo wireshark
```
This tutorial: [http://wp.me/p1EtsL-1l](http://wp.me/p1EtsL-1l) actually lets you use Wireshark without sudo.

---

### Post by Ad1217 on 2011-08-09
here it is!
At 213, 216, and 220, I tried to ping the access point.

---

### Post by Ad1217 on 2011-08-09
anyone?

---

### Post by fdrake on 2011-08-09
> **Ad1217 said:**
> here it is!
At 213, 216, and 220, I tried to ping the access point.

suggestion: delete the part that says about your login info on the forum. Your pass (hash) is there . i would delete that section you never know.

open your file with gvim/or emacs and delete that area.

---

### Post by lkjoel on 2011-08-09
Wireshark shows many activities in your network, including pings. So this means that your computer is recognizing different activities happening in your network.

I'd suggest that you un-attach the capture file now.

---

### Post by fdrake on 2011-08-09
i just sent a request of removal of the file to the mods, since he/she is off-line ate the moment.

---

### Post by Ad1217 on 2011-08-09
thank you!
any suggestions? I get
```
From 192.168.1.1 icmp_seq=4 Destination Host Unreachable
```
when I try to ping stuff on my local network

---

### Post by Ad1217 on 2011-08-10
anyone?

---

### Post by Ad1217 on 2011-08-11
anyone?

---

### Post by lkjoel on 2011-08-11
Try this in a Terminal window:
```
system-config-printer

```
A window should pop up. Click on the Server->Settings.
There should be an option to see other printers. Check it, click OK, click on the Refresh icon, and you should see your online printers.

---

### Post by lmarmisa on 2011-08-11
Maybe your are not connected to your wifi but to a neighbor.

Type these two commands and post the results:

```

iwconfig
ifconfig

```

Check the field ESSID on the result of the first command. Is that ESSID correct?.

---

### Post by Ad1217 on 2011-08-11
I am absolutely sure that I am connected to the correct Access Point.

I cannot see any printers.

I already know it is broken; I cannot ping/be pinged by any other computer. I get "Destination Host Unreachable" whenever I try.

---

### Post by Ad1217 on 2011-08-11
however, iwconfig does look odd
```
lo        no wireless extensions.

eth2      no wireless extensions.

eth0      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:202  Noise level:199
          Rx invalid nwid:0  invalid crypt:157  invalid misc:0
```

---

### Post by lmarmisa on 2011-08-11
Click on the network icon of the upper panel and check if you see the ESSID of your wifi and  try to connect to it.

---

### Post by Ad1217 on 2011-08-11
I assure you, I am connected. I can access the internet just fine, but nothing on the local network.

---

### Post by lmarmisa on 2011-08-11
According to the command **ifconfig**, what is the IP address of the wlan interface?. Does that address belong to the same subnet of your printer and NAS?.

---

### Post by Ad1217 on 2011-08-21
yet again, I have already checked that I am on the same network. Also, I cannot connect to things aaon other networks either

---

### Post by lmarmisa on 2011-08-21
Could you post the output of this command?

```

nm-tool

```

---

### Post by lkjoel on 2011-08-21
Could you run the Network Info script (in my signature), and attach the generated file?

---


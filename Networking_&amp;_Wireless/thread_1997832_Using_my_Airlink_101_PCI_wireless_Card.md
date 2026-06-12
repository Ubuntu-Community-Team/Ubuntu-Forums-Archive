---
title: "Using my Airlink 101 PCI wireless Card"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by LaJuan on 2012-06-05
Hi,

I had to transfer my system into a Dell Precision 370 running 12.04, 4GB RAM, and two 400GB HDD. My last system I did a clean install of 12.04 but, it was an AMD and it found the driver during the installation for my AirLink PCI Wireless N Card. Model: AWLH6075. Will this card work with 12.04? If so, what methods do I need to to install the drivers and get my wireless working?

Thanks,

---

### Post by chili555 on 2012-06-05
> Model: AWLH6075. Will this card work with 12.04? Probably. Tell us more. Please open a terminal and run and post:```
lspci -nn | grep 0280
```Thanks.

---

### Post by LaJuan on 2012-06-05
Hey Doc!!!

Here is my finding:

04:01.0 Network controller [0280]: Ralink corp. RT2760 Wireless 802.11n 1T/2R [1814:0701]

---

### Post by chili555 on 2012-06-05
> Ralink corp. RT2760 Wireless 802.11n 1T/2R [[COLOR="Red"]1814:0701[/COLOR]]This device uses the driver rt2800pci that's built in to 12.04. No extra steps are needed. Post back if you need additional assistance.```
$ modinfo rt2800pci | grep 0701
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]0701[/COLOR]sv*sd*bc*sc*i*
```

---

### Post by LaJuan on 2012-06-05
I'm still stupid when it comes to Ubuntu. I ran that what you posted. Is there anything else needed active my wireless?

---

### Post by chili555 on 2012-06-05
Let's make sure the module is loaded:```
sudo modprobe rt2800pci
```Did it create a wireless interface; ideally wlan0?```
iwconfig
```Does it see networks?```
sudo iwlist wlan0 scan
```If so, can you click the Network Manager icon and connect? If not, let's see if there are any informative messages:```
dmesg | grep rt2
```Please post your findings.

---

### Post by LaJuan on 2012-06-05
williams@williams-Precision-WorkStation-370:~$ sudo modprobe rt2800pci
williams@williams-Precision-WorkStation-370:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

After this, the wireless option was there for me and I'm good!!!!!!!! Thanks again for the speedy replies and useful knowledge about Ubuntu!!!:guitar::guitar::guitar::guitar:

---

### Post by chili555 on 2012-06-05
Glad to hear it. Awesome! Have fun!

---


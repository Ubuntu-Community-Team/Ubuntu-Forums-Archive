---
title: "problem changing modulation type of WLAN"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by pvraviteja on 2010-03-29
Hi,
I am new to using ubuntu. I am trying to play with my WLAN by changing its modulation, power, bitrate, channel etc. When I am trying to change the modulation type i had an error like this 
# iwconfig wlan0 modu 11g
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.
so i checked for different modulation types my WLAN supports this produced an error like this.
# iwlist wlan0 modulation
wlan0     unknown modulation information.
I even cannot access the power types my WLAN supports. I am using Intel wireless wifi link 5100. 
Can i change the modulation type and power for my WLAN?
If so pls help me...

Thank you in advance.

---

### Post by chili555 on 2010-03-29
> Can i change the modulation type and power for my WLAN?Maybe. It depends on the card. Please do:```
sudo iwlist wlan0 event
```You will get a list of the operations that are supported. Here is an example:> $ sudo iwlist eth1 event
eth1      Wireless Events supported :
          0x8B04 : Set Frequency/Channel (kernel generated)
          0x8B06 : Set Mode (kernel generated)
          0x8B13 : Spy threshold crossed
          0x8B15 : New Access Point/Cell address - roaming
          0x8B19 : Scan request completed
          0x8B1A : Set ESSID (kernel generated)
          0x8B2A : Set Encoding (kernel generated)

eth1      Scanning capabilities :
		- ESSID
		- Type
As you can see, my card and driver combination do not support modulation changes.

---

### Post by pvraviteja on 2010-04-02
Thank you for the reply,

i did not get modulation type in the wireless supported list.
So what do i need to do, to change the modulation type for my device.

Thank you in advance.

---

### Post by chili555 on 2010-04-02
Do I understand your question correctly? Are you saying, "My card and driver *will **not*** change modulation. How can I change modulation?"

If so, the answer is, you can't. Maybe there is a different driver available. There are also different cards available.

---


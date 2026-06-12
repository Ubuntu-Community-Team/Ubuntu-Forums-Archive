---
title: "Wireless help."
date: 2012-07-13
forum: Networking &amp; Wireless
---

### Post by dagroves on 2012-07-13
I have a TP-LINK TL-WN727N wireless USB adapter and I am trying to get online with it using Xubuntu. Xubuntu does not recognize it and I cannot do anything since there is no internet access. TP-LINK does not have a driver for linux on their website. What should I do in order to use my wireless?

---

### Post by Cheesehead on 2012-07-13
Happily, this has been asked before.
See [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715) for the solution.

---

### Post by dagroves on 2012-07-14
> **Cheesehead said:**
> Happily, this has been asked before.
See [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715) for the solution.

See I tried this and it worked the first time, but then I rebooted and it does not work. I have even tried typing in the suggested stuff into the terminal again and it still does not work. Ralink provides a driver for it but I have no idea how to work with a .bz2 file.

---

### Post by dagroves on 2012-07-14
Now I am back online after doing this AGAIN... but when I reboot my wireless will be off. What am I doing wrong?

---

### Post by dagroves on 2012-07-14
***bump***

---

### Post by chili555 on 2012-07-14
Please reboot and confirm that you *ARE* offline. If so, please do:```
sodu modprobe rt2870sta
```Did your wireless spring to life? If so, let's tell the system to load it automagically:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Now is it working as expected?

---

### Post by dagroves on 2012-07-15
> **chili555 said:**
> Please reboot and confirm that you *ARE* offline. If so, please do:```
sodu modprobe rt2870sta
```Did your wireless spring to life? If so, let's tell the system to load it automagically:```
sudo su
echo rt2870sta >> /etc/modules
exit
```Now is it working as expected?

Sadly no, I have no idea what to do now. I am starting to get upset...

---

### Post by chili555 on 2012-07-15
Oops! I made a mistake; I'm sorry. I meant:```
[COLOR="Red"]sudo[/COLOR] modprobe rt2870sta
```Let's do a diagnostic. Reboot so you are offline. Run this command, and I'll proofread my spelling!!```
lsmod | grep rt2
```Is rt2870sta listed as being a loaded module? If not, please do:```
sudo modprobe rt2870sta
```Does that help? If not, please let me see:```
iwconfig
```Thanks.

Sorry for my mistake.

---

### Post by dagroves on 2012-07-15
> **chili555 said:**
> Oops! I made a mistake; I'm sorry. I meant:```
[COLOR=Red]sudo[/COLOR] modprobe rt2870sta
```Let's do a diagnostic. Reboot so you are offline. Run this command, and I'll proofread my spelling!!```
lsmod | grep rt2
```Is rt2870sta listed as being a loaded module? If not, please do:```
sudo modprobe rt2870sta
```Does that help? If not, please let me see:```
iwconfig
```Thanks.

Sorry for my mistake.

Okay sir let me try that, I really appreciate you sticking with me and helping me. I will be back and I will post my results. Hang tight! =-]

---

### Post by chili555 on 2012-07-15
> **dagroves said:**
> Okay sir let me try that, I really appreciate you sticking with me and helping me. I will be back and I will post my results. Hang tight! =-]I'm here for you; anxiously awaiting your success.

---

### Post by dagroves on 2012-07-15
> **chili555 said:**
> Oops! I made a mistake; I'm sorry. I meant:```
[COLOR=Red]sudo[/COLOR] modprobe rt2870sta
```Let's do a diagnostic. Reboot so you are offline. Run this command, and I'll proofread my spelling!!```
lsmod | grep rt2
```Is rt2870sta listed as being a loaded module? If not, please do:```
sudo modprobe rt2870sta
```Does that help? If not, please let me see:```
iwconfig
```Thanks.

Sorry for my mistake.

Okay so I just reinstalled Ubuntu so I can have a fresh slate to work on. After the install, no wireless of course, then I did this in the terminal:

```

echo 'install rt2800usb modprobe --ignore-install rt2800usb ; /bin/echo "148f 5370" > /sys/bus/usb/drivers/rt2800usb/new_id' | sudo tee /etc/modprobe.d/rt2800usb.conf

```

After that I did this in the terminal:

```

sudo modprobe -v rt2800usb

```

The wireless sprang to life, but if I restart, the wireless goes off and does not start with Ubuntu. So I am going to reboot, then do the 
```

lsmod | grep rt2

```

and then I will do 
```

sudo modprobe rt2800usb

```

If that does not work, I will do 
```

iwconfig

``` 
and post back here.

---

### Post by dagroves on 2012-07-15
Okay so after a reboot, nothing, no wireless. I typed in 
```

lsmod | grep rt2

```
and nothing came up. So I then typed in
```

iwconfig

```
and I got this:
```

lo       no wireless extensions
eth0   no wireless extensions

```
BUT if I type 
```

sudo modprobe -v rt2800usb

``` 
my wireless comes back on, but after reboot it is off again.

---

### Post by dagroves on 2012-07-15
> **dagroves said:**
> Okay so after a reboot, nothing, no wireless. I typed in 
```

lsmod | grep rt2

```and nothing came up. So I then typed in
```

iwconfig

```and I got this:
```

lo       no wireless extensions
eth0   no wireless extensions

```BUT if I type 
```

sudo modprobe -v rt2800usb

```my wireless comes back on, but after reboot it is off again.

So I am currently typing this on Ubuntu using the WiFi, but if I reboot it goes away, how do I make it permanent?

---

### Post by chili555 on 2012-07-15
Please do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```Now does it work?

---

### Post by dagroves on 2012-07-15
> **chili555 said:**
> Please do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```Now does it work?

You my friend, are awesome. It works!! But I have one more minor problem. My wireless connectivity is not as good as it is in Windows 7. On Windows I had full bars, on Ubuntu, I have 2 bars. Why is that?

---

### Post by chili555 on 2012-07-15
> On Windows I had full bars, on Ubuntu, I have 2 bars. Why is that?In some, but not all cases, it's because the driver doesn't read the bars correctly! What does this tell you?```
iwconfig
```For example:> wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: xx:13:10:62:8D:xx   
          [COLOR="Red"]Bit Rate=54 Mb/s[/COLOR]   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
If you are maxed out, then I wouldn't worry. Are download and upload speeds as expected?

---

### Post by dagroves on 2012-07-15
> **chili555 said:**
> In some, but not all cases, it's because the driver doesn't read the bars correctly! What does this tell you?```
iwconfig
```For example:If you are maxed out, then I wouldn't worry. Are download and upload speeds as expected?


I guess I am fine then! I really appreciate your help on this! Thank you so much!
David!

---


---
title: "Wireless Problems"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by db0822 on 2012-11-23
Please bear with me - I am new to all this!

I installed Lubuntu 12.10 and love it.  Unfortunately I can not get the wireless networking operational.  

The Laptop is a PAckard Bell R1935 with a Ralink rt61 PCI Wireless adapter.

I have also tried a Realtek 8188CUS USB adapter which I have.

The enable wireless option is greyed out in Lubuntu - I am not sure why.

I have tried to use ndiswrapper to install drivers and get the error message: Module NDISWRAPPER not found.

In desperation I have tried the following OS: Lubuntu, Xubuntu, Slitaz and Puppy. None got the wireless working.  

The closest to success I got was in Xubuntu which had the correct drivers installed but reported a hardware switch was off.  However, there is no wireless switch on the laptop and the enable key is FN-F1 (which doesn't work).

I have googled endlessly, tried all sorts of suggested solutions and got nowhere.  At some point I input code which reported there was a Hard Block on but I couldn't kill it.

lsusb results are below:

administrator@administrator-Packard-Bell-EasyNote:~$ lsusb
Bus 001 Device 003: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 002 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
administrator@administrator-Packard-Bell-EasyNote:~$ 

I am a complete Linux novice and desperate to get this solved - I have been on it solid for a week now.

If anyone is happy to help you need to make any instructions as basic as possible.  I am a novice and it is hard to learn without an internet connection!

Any assistance very gratefully received - I'm getting desperate.

---

### Post by mr.suchy on 2012-11-23
Hi @db0822

I don't known but I think You should read this article: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Then try use Ndiswrapper. I use it every day and I don't have any problem with it. Check this and gave a sign if it would help You. Sorry for my language.

Best regards

---

### Post by db0822 on 2012-11-24
Thanks for taking the time to reply.  

Unfortunately I have looked through this and tried to follow the instructions but I am still getting the error - module ndiswrapper not found.

---

### Post by db0822 on 2012-11-25
More information:

My wlan appears to be hard-blocked.  

Lubuntu says the wireless network is disabled by a hardware switch.

My laptop is a Packard Bell Easy Note R1935 and it does not have a switch to switch wireless on and off.

To toggle wireless on / off you are supposed to use fn-f1.  These combination (along with every other one I have tried!) doesn't work.

Any more suggestions gratefully received.

Many thanks

---

### Post by thebeest on 2012-11-25
Try:

```
sudo rfkill list
```

To check what kind of block it is.


There isn't a wifi setting in the BIOS that could be disabling it is there? I have come across such a thing before where drivers are installed fine but the card itself needs to be enabled in the BIOS.

---


---
title: "AWLL5088 Airlink 101 installation help"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by cerion knowles on 2012-07-24
Hi everyone ,

So I recently obtained a USB WiFi card, an Airlink 101 AWL5088 Ultra mini USB device. When I attach it to my Ubuntu system it is recognized by the network manager and it can see my wifi network - however it is unable to connect. When I enter the passcode for my wifi it spins trying to connect and then spits it back to me telling me I need to reenter the password after a few moments - I am 100% sure the password is correct.

I am running lubuntu 12.04 on a desktop with an antiquated wireless facility, I've tried the realtek drivers but it still does not work

I have tried the Hardware Support Components and followed the directions but still nothing.

Please help and thanks in advance

---

### Post by cerion knowles on 2012-07-27
Hello anyone, please any help would be appreciated

---

### Post by cerion knowles on 2013-01-03
[QUOTE=cerion knowles;12127319]Hi everyone ,

So I recently obtained an Airlink 101 AWL5088 Ultra mini USB device. When I attach it to my lubuntu system it is recognized by the network manager and it can see my wifi network - however when it connects the wifi is slow, flaky
and unstable and i lose the connection,I don't think i need to install any drivers because they are already inbuilt and I am running lubuntu 12.04 desktop. Can anyone help please i've been waiting since july

---

### Post by aleksandrwho on 2013-01-04
+1 I have the same problem as you mate. With a AWLL5099 They use the same Linux driver.

I was interestingly enough able to get it to connect to my HTC Android for T-Mobile (running cyanogemod) to tether a connection and it worked for a bit.

It seems to be a driver problem. What you're suppose to do is download the driver file. Extract it to /use/src/ and then run the install.sh within. When I try to do that I get a man error 2 message that the drivers didn't install.

Nice to know someone else is in the hole with me. Can anyone else help? "Is there anybody out there?"

---

### Post by aleksandrwho on 2013-01-04
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsAirlink101#USB)

There you go.

if you wanna extract them to /usr/src/ you have to download and extract them somewhere on your computer and then copy them into usr/src/ you have to use the command: 

```
sudo cp -r [directory] usr/src/ 
```

I'm still working on installing the drivers because of that code 2 error but i believe the method is to run the install.sh

```
sudo sh usr/src/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh
```

try it maybe you will be luckier then i am.:D

---

### Post by aleksandrwho on 2013-01-04
[HTML]alex@ubuntu:~$ sudo bash /usr/src/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh
[sudo] password for alex: 
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
/usr/src/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/install.sh: line 17: cd: driver: No such file or directory
Decompress the driver source tar ball:
    
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
Desktop
Documents
Downloads
examples.desktop
Music
Pictures
Public
Templates
Tether
Ubuntu One
Videos
Authentication requested [root] for make clean:
make: *** No rule to make target `clean'.  Stop.
Authentication requested [root] for make driver:
make: *** No targets specified and no makefile found.  Stop.
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
alex@ubuntu:~$ 
[/HTML]

help? by the way fun fact: apparently relteck doesnt know how to spell "November"

---

### Post by aleksandrwho on 2013-01-04
wait no im wrong...drivers work for you...thats my problem actually..

well we still have the same problem.. if you have an android phone try wifi tethering and tell me if it works.

---

### Post by cerion knowles on 2013-01-04
thanks a lot for replying ....turns out that the driver is already pre-installed in 12.04 and variants, the issue here is that the internet connection works but it is really unstable and flaky....I guess the title was misleading sorry.

---


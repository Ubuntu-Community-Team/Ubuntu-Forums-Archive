---
title: "USB Adapter problems"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by vivakh on 2011-08-06
Hi there,
 
I currently have a Nexxt Lynx 150 Wireless USB adapter attatched to one of my home destops to recieve my wifi signal, however, i have run into a speed bump in terms of getting it connected to my ubuntu 11.04. 
This adapter works perfectly in windows and on the ***ubuntu live cd***, but, when i install ubuntu to my hard drive and try to connect to my network, it just takes a very long time, then says, disconnected. My signal is WPA2-Personal protected.
Here is a link to the adapter's home page > [http://www.nexxtsolutions.com/dpg/ntProducts.aspx?ctg=14&sctg=83](http://www.nexxtsolutions.com/dpg/ntProducts.aspx?ctg=14&sctg=83)
 
It seems to me that this is a driver problem. The cd that my adapter came with has drivers for linux on it, but i havent the slightest clue how to use them. Can someone please shine some light onto this for me?
 
Thank you all very much,
Vivakh.

---

### Post by chili555 on 2011-08-06
Please insert the device, open a terminal and and run and post:```
lsusb
lsmod | grep -e rt2 -e rt3
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by vivakh on 2011-08-07
Thanks for responding. Here is the information you requested:
 
lsusb
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0951:1603 Kingston Technology DataTraveler 1GB/2GB Pen Drive
Bus 002 Device 002: ID 1058:0730 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
 
lsmod | grep -e rt2 -e rt3
```
rt2870sta 450556 0 
rt2800usb 18235 0 
rt2800lib 45181 1 rt2800usb
crc_ccitt 12667 2 rt2870sta,rt2800lib
rt2x00usb 20330 1 rt2800usb
rt2x00lib 49235 3 rt2800usb,rt2800lib,rt2x00usb
mac80211 294370 3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211 178528 2 rt2x00lib,mac80211
```

---

### Post by chili555 on 2011-08-07
The doctor has seen these cases before. The good news is that I believe we can save this patient! Please open the terminal and do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by vivakh on 2011-08-08
Thanks much. I'm at work now, when i get home i will try it and post.

---

### Post by vivakh on 2011-08-08
I did everything you said and i'm now posting this from the computer that was not getting connected. Thank you so much for solving this for me.

If you don't mind, can you explain what was the problem? I am fairly new to linux, but i hope one day i can be able to do things like this. 
From what i gathered from your commands used, there was something installed that was conflicting the files needed in order for the device to function properly. So you added the conflicting file to some type of blacklist? :)

Thanks so much again,
Vivakh.

---

### Post by chili555 on 2011-08-08
> If you don't mind, can you explain what was the problem? I am fairly new to linux, but i hope one day i can be able to do things like this.
From what i gathered from your commands used, there was something installed that was conflicting the files needed in order for the device to function properly. So you added the conflicting file to some type of blacklist?Yes, indeed. There are two drivers that claim your device, rt2870sta and rt2800usb. The sta driver is what is referred to as 'staging.' It is being developed to be included in the mainline driver package rt2800usb. That's why there are two different conflicting drivers that claim one device.

From my experience, I know that rt2870sta works well and rt2800usb doesn't. Therefore, we add rt2800usb to a blacklist file. The system then won't load the not-working but conflicting rt2800usb.

I didn't explain it carefully because many users just want to know what they have to do to get it all working; they don't really care why. I'm on your side; I want to know what and why. Please post back if I can help you further.

---

### Post by vivakh on 2011-08-08
> **chili555 said:**
> I didn't explain it carefully because many users just want to know what they have to do to get it all working; they don't really care why. I'm on your side; I want to know what and why. Please post back if I can help you further.
 
Im glad you explained it, it makes perfect sense. Getting stuff to work is one thing, but i like to understand why i am doing this and for what reason. That way i learn, so the next time i encounter this problem, or encounter one of similar nature, my knowledge will help me to overcome it, instead of running for help straight away.
 
Before i posted here, i was researching how to add the linux drivers that were provided on the CD, but i wasnt really getting anywhere, i was getting some errors in the terminal. So i decided to post here. Thanks again for all your help.
 
Another thing i want to ask you, i want to pursue CompTIA's Linux+ Exams ([http://certification.comptia.org/getCertified/certifications/linux.aspx](http://certification.comptia.org/getCertified/certifications/linux.aspx)), i dont know if you've heard of it, but if you have, do you know if it will enable me to be more versed in linux and give me the tools i need to handle support and troubleshooting, etc.? Would you recomend it?

---

### Post by chili555 on 2011-08-09
> **vivakh said:**
>  
Another thing i want to ask you, i want to pursue CompTIA's Linux+ Exams ([http://certification.comptia.org/getCertified/certifications/linux.aspx](http://certification.comptia.org/getCertified/certifications/linux.aspx)), i dont know if you've heard of it, but if you have, do you know if it will enable me to be more versed in linux and give me the tools i need to handle support and troubleshooting, etc.? Would you recomend it?I am familiar with the courses and exams. They are quite well respected and will certainly help you be more versed in Linux and more able to give support.

As to whether (to ask the obvious question) this will make you more employable, I can't say. I have arduously avoided employment for many years and I'm not at all familiar with IT employment here or in your country. If employment is your objective, I'd suggest a letter or email to several IT managers in your area asking them for guidance as to what they consider the minimum educational requirement to gain employment in their firm.

I have seen and responded to a few questions from people actually employed in the IT field on this forum.

---

### Post by vivakh on 2011-08-09
Employment is my aim, yes, but i don't want to pursue Linux+ primarily for employment reasons. Its more of a personal objective than a professional requirement. 
I want to learn more about it, so im going to go after it. Maybe it will prove useful in the future (employment wise), maybe it wont, main thing is that i would've satisfied my desire to learn.

Thanks much for all you help. I really appreciate it :)

---

### Post by furieh on 2011-08-11
Hello everyone, I am experiencing a problem with this device and thought I'd rather not open another thread. 
It connects fine but the speed is really frustrating if you compare it with Win XP.
Here is my lsusb and lsmod results.
lsusb ->
```
Bus 003 Device 002: ID 093a:262c Pixart Imaging, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bb4:0c1f High Tech Computer Corp. 
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```lsmod ->
```
rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211

```Thank you very much in advance!

And my Ubuntu is 11.04

---

### Post by chili555 on 2011-08-11
The problem and solution is exactly as outlined above. > The doctor has seen these cases before. The good news is that I believe we can save this patient! Please open the terminal and do:
Code:

sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit

Reboot and let us have your report. 

---

### Post by furieh on 2011-08-11
Oops, I think I should've said this before, but I actually tried the aforementioned solution only to end up without connectivity. ¿Any other clues?
Thanks!

---

### Post by chili555 on 2011-08-11
Please try it again. After you reboot, please run and post:```
dmesg | grep -i rt2
uname -r
```Thanks.

---

### Post by furieh on 2011-08-11
I'll try again, thanks for your help :D

---

### Post by furieh on 2011-08-11
Yes!! It worked! Thank you very very much Chilli555!
Here is the dmesg output:
```
13.734565] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   14.344572] usbcore: registered new interface driver rt2870
[   18.385414] <==== rt28xx_init, Status=0
[   19.730150] <==== rt28xx_init, Status=0
```

And uname output as well:
```
2.6.38-8-generic
```

My internet is working as it should again :D

---

### Post by chili555 on 2011-08-11
> Yes!! It worked! Thank you very very muchGlad it's working! Have fun.

---

### Post by mevik on 2011-12-01
Hello, I just started using Linux again (this time Debian, as I'm trying to decide which one to use) and I tried your solution, typed the code you gave and it still not working, its strange as I have made it to work with Ubuntu (10.10 and natty narwhal) and with Fedora. Now, I also noticed that the light on top of the device doesn't blink anymore, it just stays on. I wish i could get some help from you guys.

---

### Post by chili555 on 2011-12-02
> **mevik said:**
> Hello, I just started using Linux again (this time Debian, as I'm trying to decide which one to use) and I tried your solution, typed the code you gave and it still not working, its strange as I have made it to work with Ubuntu (10.10 and natty narwhal) and with Fedora. Now, I also noticed that the light on top of the device doesn't blink anymore, it just stays on. I wish i could get some help from you guys.Please run and post:```
lsusb
lsmod | grep rt2
uname -r
modinfo rt2870sta
```Thanks.

---


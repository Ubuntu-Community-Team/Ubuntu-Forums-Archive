---
title: "Help installing DIGITAZZ wirless dongle."
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by ouija1979 on 2013-02-21
Every other dongle I have had was simply plug and play, but I have bought a Digitazz one and I cannot get xUbuntu to recognize it. Is there any drivers I can install from the terminal. I am still a fairly new user and I prefer codes instead to using tarballs, they scare me. please help.

---

### Post by chili555 on 2013-02-21
Please run and post:```
lsusb
```Thanks.

---

### Post by ouija1979 on 2013-02-21
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:5372 Ralink Technology, Corp. 
xubuntu@ubuntu:~$

---

### Post by chili555 on 2013-02-21
The most recent versions of Ubuntu drive this device with *rt2800usb*. Which version are you running?```
lsb_release -d
```Is *rt2800usb* loading?```
lsmod | grep rt2
iwconfig
rfkill list all
dmesg | grep rt2
```

---

### Post by ouija1979 on 2013-02-21
Ok, hope I am doing this correctly...

Description:    Ubuntu 12.04.2 LTS
xubuntu@ubuntu:~$ lsmod | grep rt2
rt2800usb              22373  0 
rt2800lib              53298  1 rt2800usb
crc_ccitt              12627  1 rt2800lib
rt2x00usb              20099  1 rt2800usb
rt2x00lib              48875  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              436493  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178877  2 rt2x00lib,mac80211
xubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

xubuntu@ubuntu:~$ rfkill list all
xubuntu@ubuntu:~$ dmesg | grep rt2

---

### Post by chili555 on 2013-02-21
Something's funny here, obviously. Please do:```
dmesg > ouija.txt
```Find the file ouija.txt in your user directory and paste it here and give us the link.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by ouija1979 on 2013-02-21
> **chili555 said:**
> Something's funny here, obviously. Please do:```
dmesg > ouija.txt
```Find the file ouija.txt in your user directory and paste it here and give us the link.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)


I am sorry I don't understand 
dmesg > ouija.txt in terminal? please explain step by step for me.

---

### Post by ouija1979 on 2013-02-21
My name isn't ouija in xubuntu, it is just xubuntu. and when I try either, nothing is happening in terminal.

---

### Post by chili555 on 2013-02-21
When you run the command:```
dmesg
```...it produces dozens and dozens of lines of output. You can't easily copy and paste all that in the forum. Even if you did, you'd end up with a post that was very long. That's referred to as flooding the forum and is frowned upon. So how can we see a file that's 100 lines long? By using pastebin, a site that's specifically made for floods.

The terminal produces no output because your command was accepted without error or warning; just what we want. But, it undoubtedly produced the needed text document. Please look in your user directory and open it with gedit. Click Edit > Select All and Copy. Open the website for pastebin and paste it in. A link will be created and we need that to see your text.

It doesn't matter to you what the file is named. You could call it ouija.txt or dmesg.txt or ilovechocolate.txt. It only matters to me so I can refer back to files I have on MY computer and relate them to the poster in question. I answer many posts a day here and on other forums, so it helps to separate your dmesg from another person's dmesg.

Please see attached. Here is an example bill.txt.

---

### Post by ouija1979 on 2013-02-21
Thanks :) that really helps me. I was getting really confused .

---

### Post by ouija1979 on 2013-02-21
Ok I think thats it :)

---

### Post by chili555 on 2013-02-21
It appears you forgot to give me the pastebin link in your reply like this: [http://paste.ubuntu.com/1700850/](http://paste.ubuntu.com/1700850/)

---


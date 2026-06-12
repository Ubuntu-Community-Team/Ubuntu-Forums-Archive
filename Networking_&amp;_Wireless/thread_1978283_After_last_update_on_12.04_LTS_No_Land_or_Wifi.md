---
title: "After last update on 12.04 LTS No Land or Wifi"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by blackangelpr on 2012-05-11
Greetings i was trying to make my grandma wifi laptop computer  work that is integrated on it since on the beta versions i had no trouble but after the last update on the LTS either the LAN or Wifi Works.... can some one plase give a helping hand :confused: 

here are the specs:

Computer: Dell Inspiron B120   
Memory: 1 gbg 
Processor: intel Celeron M 1.40 Mghz
OS: Ubuntu 12.04 LTS 32 bits
HDD: space: 40.00 gig 
Wifi: W1370 802.11 b/g wireless network mini-pci card for LAPTOP / Notebooks

---

### Post by blackangelpr on 2012-05-11
Just had runned on the terminal:

```
 lspci -nn | grep 0280 
```

and it retuned the following:

02:03.0 network Controller [0280]: Broad Corporation BCM4318 [AirForce One 54g] 802.11g Wireless Lan Controller [14e4:4318] (rev 02)

Thanks to Chili555 for the code previously

now what else i should do?

---

### Post by chili555 on 2012-05-11
Grandma's wireless needs firmware and a helping hand from you. Here is a file you can download and put on a USB key. Drag and drop it from the USB key to her Desktop. Right-click it and select *Extract Here*. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Is it working now? Hug Grandma from old Chili and tell her to enjoy her Facebook!

---

### Post by blackangelpr on 2012-05-11
> **chili555 said:**
> Grandma's wireless needs firmware and a helping hand from you. Here is a file you can download and put on a USB key. Drag and drop it from the USB key to her Desktop. Right-click it and select *Extract Here*. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Is it working now? Hug Grandma from old Chili and tell her to enjoy her Facebook!


You are a genious my friend :) thanks a lot she will be very happy when i give her laptop back :) actually i was in need to create another account in english and i make her a standard user so in the next 5 years of the LTS i do not need to worry much for the laptop again :) thank you very very much :guitar:

---

### Post by chili555 on 2012-05-11
Will you be kind enough to use thread tools at the top to Mark Solved?

---

### Post by blackangelpr on 2012-05-11
> **chili555 said:**
> Will you be kind enough to use thread tools at the top to Mark Solved?

already done (^_~)  thanks again

---

### Post by blackangelpr on 2012-05-11
> **chili555 said:**
> Grandma's wireless needs firmware and a helping hand from you. Here is a file you can download and put on a USB key. Drag and drop it from the USB key to her Desktop. Right-click it and select *Extract Here*. Now open a terminal and do:```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo modprobe -r b43
sudo modprobe b43
```Is it working now? Hug Grandma from old Chili and tell her to enjoy her Facebook!


I am at my grandma house and the Wifi disappear again lucky the terminal saved the the command so i just follow it and it worked again ... but in any chance this change could be make permanent?

---

### Post by blackangelpr on 2012-05-11
just rebooted and the wifi was not found so i quantify the findings :) hehe still after 
changing the folder and doing sudo modprobe b43 everything works until you restart or shut down the computer

---

### Post by blackangelpr on 2012-05-11
screen shot

---

### Post by chili555 on 2012-05-11
Please try this:```
sudo su
echo b43 >> /etc/modules
exit
```Now does it work after a reboot?

---

### Post by blackangelpr on 2012-05-11
It woks thans again this problem is close :guitar: you rock also how do you gain so much knowledge and what I need to do to learn since all things around I found are basic stuff to read  :confused:

---

### Post by chili555 on 2012-05-11
> how do you gain so much knowledge I read the forums; I copy methods that work from others here on the forum and I keep good notes. I have a 'Forum' folder on my desktop that's just a tiny, slim little 1.8 GB. The pci.id or the usb.id and Google tell everything.

Mostly, it's years and years of experience.

Thanks for your kind words.

Don't forget to hug Grandma!

---

### Post by ira miles on 2012-05-29
This worked for me as well, though I wanted to know what to do with the b43 file on the desktop when I am done. Can I chuck it?
Thanks. I'm pretty rusty and a general noob, so thanks.
Ira

---

### Post by chili555 on 2012-05-29
> **ira miles said:**
> This worked for me as well, though I wanted to know what to do with the b43 file on the desktop when I am done. Can I chuck it?
Thanks. I'm pretty rusty and a general noob, so thanks.
IraYou can. However, if you ever need to reinstall, you might be glad if you transferred it to a CD and filed it away.

---

### Post by ozPATT on 2012-06-05
This hasn't worked for me :( 

```
lspci -nn |grep 0280
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

I do have a STA driver in the additional drivers bit but this is not activated. I tried activating it as well to see if that made any difference but it didn't. 

Any ideas?

Thanks

Patrick

---

### Post by chili555 on 2012-06-05
> Broadcom Corporation BCM4312 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]] (rev 01)There is some question as to the best way to get your specific device going. Here is my best shot:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and tell us if it's working.

---

### Post by packetsmasher on 2013-02-09
When i attempted this after the last line of sudo modprobe b43 the terminal lists a bunch of stuff and i have to basically power the laptop down to be able to use it again.  Am i missing something?

---

### Post by chili555 on 2013-02-09
> **packetsmasher said:**
> When i attempted this after the last line of sudo modprobe b43 the terminal lists a bunch of stuff and i have to basically power the laptop down to be able to use it again.  Am i missing something?Do you have the same device?> Broadcom Corporation BCM4312 802.11b/g LP-PHY [[COLOR="Red"]14e4:4315[/COLOR]] (rev 01) We won't know what the problem is until we see the 'bunch of stuff.' Can you please reboot and show us:```
dmesg | grep b43
```

---


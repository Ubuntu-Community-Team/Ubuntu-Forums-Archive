---
title: "Bcm wireless driver"
date: 2012-11-20
forum: Networking &amp; Wireless
---

### Post by leg on 2012-11-20
I recently upgraded my laptop to 11.10 and as usual the commercial wireless driver I need was removed. I had forgotten that my wired connection is broken and I was relying on the wireless for network access. When I try to activate the driver it fails.

Can anyone tell me where and how to download and install the bcm driver manually?

---

### Post by Bucky Ball on 2012-11-20
Posted in error.

---

### Post by leg on 2012-11-20
Yes but my wired network port isn't working. That is my point. I will need to download it on another machine and then place it on the laptop and install it. At least that is my thinking. I need to know where to get it from so I can do that.

---

### Post by Bucky Ball on 2012-11-20
Got you, my mistake.

---

### Post by westie457 on 2012-11-20
@leg

Do you know which wifi chip you have?


Edit -----------------
If you need the b43 driver follow this post. [http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)

---

### Post by Bucky Ball on 2012-11-20
Please open a terminal and:

```
iwconfig
sudo lshw -C network
```

... one at a time. Post the outputs back here. That will give us your details. ;)

---

### Post by leg on 2012-11-20
> **Bucky Ball said:**
> Got you, my mistake.
No Problem.

---

### Post by leg on 2012-11-20
> **westie457 said:**
> @leg

Do you know which wifi chip you have?


Edit -----------------
If you need the b43 driver follow this post. [http://ubuntuforums.org/showpost.php?p=11860231&postcount=8](http://ubuntuforums.org/showpost.php?p=11860231&postcount=8)
Not off hand but I will check when I get home. I know the driver is BCM something.

---

### Post by leg on 2012-11-20
> **Bucky Ball said:**
> Please open a terminal and:

```
iwconfig
sudo lshw -C network
```

... one at a time. Post the outputs back here. That will give us your details. ;)
Will do when I get home. Thanks

---

### Post by leg on 2012-11-20
Hi all. The additional drivers app says it is the Broadcom STA proprietry wireless driver that I require. Includes BCM 4311, 4312, 4313, 4421, 4322, 43224 etc.

---

### Post by wildmanne39 on 2012-11-20
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by leg on 2012-11-20
I need the BCM4312

---

### Post by wildmanne39 on 2012-11-20
Hi, there is more then one 4312 if you will not post the output asked for we can not help you.
Thanks

---

### Post by leg on 2012-11-20
> **Wild Man said:**
> Hi, there is more then one 4312 if you will not post the output asked for we can not help you.
Thanks

Well its a bit difficult to post terminal output without my metwork connection. I am posting from my phone. I will give it a go.

---

### Post by wildmanne39 on 2012-11-20
HI, I see that does make it hard, you have have another computer with internet you can take the results and out them on a flash drive then post them here.
Thanks

---

### Post by leg on 2012-11-20
> **Wild Man said:**
> Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you
Ok way too much to type out on my phone but hopefully this is enough for someone to tell where to download what I need. 

Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]

---

### Post by wildmanne39 on 2012-11-20
Hi, this should work if you have not installed any other drivers:

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

---

### Post by leg on 2012-11-20
> **Wild Man said:**
> Hi, this should work if you have not installed any other drivers:

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Thanks

Thank you Wildman I am now on my laptop posting this. Much appreciated.

---

### Post by wildmanne39 on 2012-11-20
Hi, your welcome!
Enjoy

---

### Post by leg on 2012-11-25
When I restart my laptop I now have to re run the modprobe command to get on the internet. I tried to activate the driver through system settings but this disconnects. How do I set this so that wireless is working when the machine starts.

---

### Post by wildmanne39 on 2012-11-25
Hi, please do:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by leg on 2012-11-25
Once again thank you Wildman.

---

### Post by wildmanne39 on 2012-11-25
Your welcome! I just wonder what happened to make it start not coming on at boot, I guess that file got corrupted but the question is how.
Enjoy

---


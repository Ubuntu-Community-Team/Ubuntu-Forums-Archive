---
title: "RT5390 - Need help."
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by teskuz on 2011-12-29
Ok, let me start off by saying this: 
This is my first day using any linux distro, I've been doing some research around this problem and it seems fairly common. 
I've been reading a lot of good threads and most of them have been solved by people who call themselves "noobs"... But i assume i'm even more of a noob than them. 

Anyways, i didn't manage to find the drivers that was linked by Chili555 if i recall. 
But instead i downloaded the RT539x PCIe from [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

Now my problem is that i have absolutely no clue on how to install them, the readme file that is provided in the download file seems very outdated. 

So now, i would appreciate if someone could tell me how to install those drivers step by step. 

I hope that someone manages to help me and don't get too frustrated at my lack of knowledge.

Regards
-Teskuz

---

### Post by praseodym on 2011-12-29
Hi,

try this installation via dkms, cable connection, and copy/paste:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/3473742/Ralink_5390sta-2.5.0.3_dkms.tar.gz
sudo tar xvf Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3
sudo modprobe -v rt5390sta
```
Check after that:

```
uname -a
iwconfig
sudo iwlist scan
```

---

### Post by BC59 on 2011-12-29
The procedure followed [here]("http://ubuntuforums.org/showthread.php?t=1608095&highlight=zew1690") is similar. Just change driver type.

---


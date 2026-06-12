---
title: "WLAN problem with easy peasy"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by mhuisenga on 2009-07-31
Easy peasy is not recognizing my wireless card.  I just installed and have no way of connecting with a LAN cable so i can't download any recent update that may have addressed this.

Any ideas?

Lenovo IdaPad S10e
Easy Peasy 1.1

---

### Post by hibliss on 2009-07-31
Do you have another machine with a connection to the web? What is the make and model of the wireless card?

---

### Post by mhuisenga on 2009-07-31
ya i'm able to use windows on the other partition to get online.

the network card is a Broadcom BCM4312

---

### Post by hibliss on 2009-07-31
What kernel version are you using with Easy Peasy?

They have a driver here - [http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

Install instructions here - [http://ubuntuforums.org/showthread.php?t=896713]("http://ubuntuforums.org/showthread.php?t=896713")

Download it on your Windows partition and put it on a flash drive, then follow the instructions, it may help to save them to a txt file so you can open that in Easy Peasy.

---

### Post by mhuisenga on 2009-08-02
thanks ill give this a shot

---

### Post by hibliss on 2009-08-02
Let us know how it goes. If it does not work, you have some other options.

---

### Post by mhuisenga on 2009-08-11
Sorry, I haven't had time recently to mess with this.

But I'm working on it now and can't seem to build the LKM

when i type 
make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

Using my kernel, which is 2.6.27-8-eeepc, I get this in response:

"bash: 2.6.27-8-eeepc: No such file or directory"
 
and I have tried with numerous variations of the kernel. Please confirm that I should be typing

make -C /lib/modules/<2.6.27-8-eeepc>/build M='pwd' 

into the directory containing the make file

thanks
Mike

---


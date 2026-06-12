---
title: "RTL8188SU Issues"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by Ntr09 on 2013-05-04
Hello,

Before I get started with my problem, I'd just like to let you know I am by no means a linux n00b, but like everyone, I have a lot to learn.

And on to the problem.

For several months now, dating back to the release of ubuntu 12.10, my usb wireless adapter has been acting up. Sudden slowdown of connection speed after running for a while was the norm.

A reboot would fix the problem for a while and life would carry on. 

Up until recently I was thinking of replaceing the adapter, but after testing it on other ubuntu systems, I found no fault with it.

Shortly after I upgraded to 13.04, it stopped working entirely, but was recognized when "lsusb" was run. 

After more testing on other systems, I found the adaper to be working flawlessly. But it still will not work on my main system.

So, with that, here I am. Stuck. 

Here is the link to a paste of my "netinfo" file generated with the "wireless_script" I found here on the forums: [http://pastebin.com/gu4tSuXp](http://pastebin.com/gu4tSuXp)

Hope y'all can help.

Thanks ahead of time,

NR

---

### Post by ahallubuntu on 2013-05-04
~

---

### Post by Ntr09 on 2013-05-04
Alright, I seem to think ordering a new (and more linux friendly) card may be the best thing to do here. 

Although it seems very weird to me that this adapter works fine on other systems such as mint 14 and an ubuntu 13.04 live usb. 

Just want to make sure nothing is wrong with my system before I go and buy $20 worth of hardware.

Thanks for your help,

-NR

---

### Post by ahallubuntu on 2013-05-05
~

---

### Post by Ntr09 on 2013-05-05
Yeah, I know that much. I just want to make sure nothing is wrong with my system before I go and buy anything. 

I dont have another wi-fi card laying around, so what should I do to make for certain that there is nothing I can fix?

Thanks for your time,

-NR

---

### Post by varunendra on 2013-05-06
> **Ntr09 said:**
> so what should I do to make for certain that there is nothing I can fix?

Your adapter is detected in lsusb output (0bda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter), so I don't think there is any hardware problem.

However, it is a bit mysterious to me why the appropriate driver wasn't loaded for it, as 13.04 does have it. While the adapter is plugged in, please try -
```
sudo modprobe -v r8712u
```
See if you get any errors. If not, does the adapter come to life?

---

### Post by Ntr09 on 2013-05-06
That worked! Connected to the network now. 

Here is the output:

```
neil@Xsys:~$ sudo modprobe -v r8712u
[sudo] password for neil: 
insmod /lib/modules/3.8.0-19-generic/kernel/drivers/staging/rtl8712/r8712u.ko 
neil@Xsys:~$ 

```

Thanks again!

-NR

---

### Post by varunendra on 2013-05-06
> **Ntr09 said:**
> That worked! Connected to the network now.

That's great!! Thanks for your feedback :)

If it doesn't load automatically at every boot, add the driver's name (r8712u) to your **/etc/modules** file. The command-line way to do that -
```
echo "r8712u" | sudo tee -a /etc/modules
```

Enjoy! And please consider marking the thread as [Solved] if you find the connection satisfactory. Thanks.

---

### Post by Ntr09 on 2013-05-06
Thanks guys!

I'll make a script with your code and have it to run at startup if it doesn't load.

-NR

---

### Post by Ntr09 on 2013-05-06
Or I could actually read your post and I wouldn't have to do that. xD

-NR

---

### Post by varunendra on 2013-05-06
> **Ntr09 said:**
> Or I could actually read your post and I wouldn't have to do that. xD

-NR

^^ :lolflag:

Don't forget the marking as [Solved] part ;)

---


---
title: "Wireless Disabled by Hrdware Switch - Sony Vaio"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by sixtydegrees on 2011-08-28
Hi, i have a Sony Vaio VPCY2 and i am trying to run Ubuntu 11.04 from a USB drive, however my wireless is having a similar problem to a lot of others (see thread title).

I also tried installing it within Windows 7 last night but had the same problem. 

The wireless light is on and everything is fine with the network in Windows (router etc), it's just with Ubuntu i'm having this problem. 

I'm pretty new to Ubuntu and have tried it in the past but had to give up on it for too many little bugs like this, BUT Windows 7 is absolutley awful, so i really want to make this work. My laptop is only months old and shoudl be great with Ubuntu, if i can get this to work.

COuld someone help guide me through troubleshooting this please?

Thanks in advance.

---

### Post by bkratz on 2011-08-28
> **sixtydegrees said:**
> Hi, i have a Sony Vaio VPCY2 and i am trying to run Ubuntu 11.04 from a USB drive, however my wireless is having a similar problem to a lot of others (see thread title).

I also tried installing it within Windows 7 last night but had the same problem. 

The wireless light is on and everything is fine with the network in Windows (router etc), it's just with Ubuntu i'm having this problem. 

I'm pretty new to Ubuntu and have tried it in the past but had to give up on it for too many little bugs like this, BUT Windows 7 is absolutley awful, so i really want to make this work. My laptop is only months old and shoudl be great with Ubuntu, if i can get this to work.

COuld someone help guide me through troubleshooting this please?

Thanks in advance.


the place to start would be to go to the terminal and copy/paste the output of 

rfkill list all

back here. It should show the state

---

### Post by sixtydegrees on 2011-08-28
> **bkratz said:**
> the place to start would be to go to the terminal and copy/paste the output of 

rfkill list all

back here. It should show the state

Thanks bkratz, here you go:

0: sony-wifi: Wireless LAN 
    soft blocked: yes
    hard blocked: no
1: sony-bluetooth: Bluetooth
    soft blocked: no
    hard blocked: no
2: phy0: Wireless LAN 
    soft blocked: yes
    hard blocked: yes
3: acer-wireless: Wireless LAN 
    soft blocked: yes
    hard blocked: no
3: hci0: Bluetooth
    soft blocked: no
    hard blocked: no

Edit: 

By using

rfkill unblock all
sudo rfkill unblock all

I have now managed to unblock all apart from the acer-wireless which is still soft block

---

### Post by bkratz on 2011-08-28
> **sixtydegrees said:**
> Thanks bkratz, here you go:

0: sony-wifi: Wireless LAN 
    soft blocked: yes
    hard blocked: no
1: sony-bluetooth: Bluetooth
    soft blocked: no
    hard blocked: no
2: phy0: Wireless LAN 
    soft blocked: yes
    hard blocked: yes
3: acer-wireless: Wireless LAN 
    soft blocked: yes
    hard blocked: no
3: hci0: Bluetooth
    soft blocked: no
    hard blocked: no

Edit: 

By using

rfkill unblock all
sudo rfkill unblock all

I have now managed to unblock all apart from the acer-wireless which is still soft block



As far as I know no one has ever figured out why the acer thingy is even there.

Try,

sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all


This would just be temporary (until the next boot), but this is just to see. We will make it permanent if it helps.

---

### Post by sixtydegrees on 2011-08-28
> **bkratz said:**
> As far as I know no one has ever figured out why the acer thingy is even there.

Try,

sudo rmmod -f acer-wmi
sudo rfkill unblock all
rfkill list all


This would just be temporary (until the next boot), but this is just to see. We will make it permanent if it helps.

Hi bkratz, i've just found that on another forum and it has unblocked it :) 

The soluton they give for making it permenant is:

sudo su echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf exit

I have just tried this but i get a 'permission denied' message!

Can you help?

---

### Post by bkratz on 2011-08-28
> **sixtydegrees said:**
> Hi bkratz, i've just found that on another forum and it has unblocked it :) 

The soluton they give for making it permenant is:

sudo su echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf exit

Does that sound ok to you?

Thanks for youe help

This is the way I am used to seeing it, but the whitespace should not matter, so yes!

sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit

---

### Post by bkratz on 2011-08-28
Just noticed your edit, perhaps it does matter!

---

### Post by sixtydegrees on 2011-08-28
> **bkratz said:**
> Just noticed your edit, perhaps it does matter!

Right, i've managed to get permission but now it says:

Unkown id: echo

What am i doing wrong?!

---

### Post by bkratz on 2011-08-28
> **sixtydegrees said:**
> Right, i've managed to get permission but now it says:

Unkown id: echo

What am i doing wrong?!



I really don't know, could you possibly have put an extra character when typing and had to backspace?  I am googlubuntu.com ing for a solution, may take a bit.

---

### Post by sixtydegrees on 2011-08-28
> **bkratz said:**
> I really don't know, could you possibly have put an extra character when typing and had to backspace?  I am googlubuntu.com ing for a solution, may take a bit.

Hi Bkratz, i've fixed it! 

By following your formatting/input, it worked great. I have rebooted and it has remained permenant. Just seemed to be a problem when on one line.

Thanks for all your help

---

### Post by bkratz on 2011-08-28
Post 4 of this thread tells what happened.

[http://ubuntuforums.org/showthread.php?t=1527119](http://ubuntuforums.org/showthread.php?t=1527119)

basically the first way you tried sudo su echo... tried to change ownership to a user named echo. We would have had to add escapes (\) before the file names.

if you never got to the exit command, perhaps you are still in the mode. anyway, I think I would just reboot and repeat the steps again to make sure where we are.

---

### Post by bkratz on 2011-08-28
> **sixtydegrees said:**
> Hi Bkratz, i've fixed it! 

By following your formatting/input, it worked great. I have rebooted and it has remained permenant. Just seemed to be a problem when on one line.

Thanks for all your help



Thanks to you too!  I got to learn something. Anyway, glad you got it working--congratulations! did not notice whether you went to the tools and marked the thread as solved, if not please do so.

---

### Post by sixtydegrees on 2011-08-28
> **bkratz said:**
> Thanks to you too!  I got to learn something. Anyway, glad you got it working--congratulations! did not notice whether you went to the tools and marked the thread as solved, if not please do so.

First day on the forum so i didn't know about that, i'll mark it answered :)

On a side note (and this may be another thread), my wireless is painfully slow in Ubuntu, i mean, so slow it really isn't worth the point.

---

### Post by bkratz on 2011-08-28
> **sixtydegrees said:**
> First day on the forum so i didn't know about that, i'll mark it answered :)

On a side note (and this may be another thread), my wireless is painfully slow in Ubuntu, i mean, so slow it really isn't worth the point.



I think I would start another thread with a descriptive title. but it may be interesting to see the output of 

ifconfig
and 
iwconfig

they tend to show a lot of info.

---

### Post by Ruisou on 2011-08-30
This thread should be required reading for anyone installing ubuntu on a sony vaio. This fix, along with installing the compat-wireless-3.1-rc1-1.tar.bz2 ,are the holy grail for getting an E-series laptop's wifi to work. 
Saved me hours. Thanks

---


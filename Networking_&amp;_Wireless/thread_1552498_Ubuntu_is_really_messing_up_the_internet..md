---
title: "Ubuntu is really messing up the internet."
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by xBiocorex on 2010-08-13
Hello there, I noticed recently that sometime the internet will slowly begin to completely shut down. First, the web browser will be unable to connect anywhere, and if I let that go for too long, aMSN logs out. Once aMSN is logged out, the internet is just gone for good, and the only way to fix it is a hard reboot of the router, or in more severe cases, a hard reboot of the radio (we get our internet connection through a radio on the roof). It was recently repaired to boost the signal strength and it was running amazingly, but now it's slowly getting worse, and it is definitely my computer running on Ubuntu 10.4 that is killing the connection.

I've looked at a few other threads, but they don't seem to be having the exact problem I am. Just logging into aMSN today killed it, and it froze upon attempting to reconnect. I feel like Ubuntu has internet leprosy or something.

---

### Post by sidzen on 2010-08-13
> **xBiocorex said:**
> 
I've looked at a few other threads, but they don't seem to be having the exact problem I am. Just logging into aMSN today killed it, and it froze upon attempting to reconnect. I feel like Ubuntu has internet leprosy or something.

Flip the coin over -- exactly the opposite is more likely the case -- aMSN could despise Linux in general and be doing what Windoze did to its former superior in the word processing arena, wordPerfect.

Why use MS at all?  Why dual boot?  Wake up!

---

### Post by wojox on 2010-08-13
Try disabling ipv6

```
gksudo gedit /etc/default/grub
```

Change

```
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
```

To

```
GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”
```

Save and exit 

```
sudo update-grub
```

Reboot.

---

### Post by grahammechanical on 2010-08-14
So, Ubuntu is really messing up the internet, is it? That is a give away. You really are Bill Gates or Steve Bulmer, are you not? I am just joking. 

Have you checked the cables that connect you to the "radio" on the roof? Are they damaged? Are they shielded to prevent degradation of the signal? Have you thought that others may be using the connection at the same time as you and this is causing the slow down? Are you browsing websites that send a lot of data - videos? Do you have too many programs running at once? How fast is your CPU and video card? How much memory do you have?

My sister's laptop is very slow connecting to the internet. This is because the home page of Internet Explorer is the website the ISP which is also provides TV programs by cable. The home page downloads video samples of TV programs and it uses up too much of the CPU and memory. My sister has given up using email (webmail) because of the time she has to wait. A Ubuntu live CD runs great and is fast in comparison. Cut the clutter.

Regards

---

### Post by xBiocorex on 2010-08-14
Sorry it took so long to respond, had my computer disconnected from the router for safety reasons. I called up my router's company and they got me to lower the WAN port speed from Auto to 10Mbps, and I will see how it goes for 24 hours. 

I really thought it was Ubuntu at first, because the issues DID pop up after I installed it, but today I was on my PS3, my computer was disconnected, and the internet still died, so it's either the router or my ISP.

@sidzen:

By "back on XP" I meant back when I used it, not that I have both on my system. I am 100& Ubuntu.

Does aMSN purposely do something to Ubuntu? I never really researched it, I just used it because I heard it can import all your Windows Live accounts, and it was right there when searching "MSN" in software center. I'll try pidgin or something.

@wojox:
I'll try that if fixing the router/ISP doesn't work

@grahammechanical:
YES, I'M STEVE JOBS! ;D

I would suspect high-bandwith sites like that, if it weren't for the fact that the issue is very recent, and that the internet has been running very well the whole time we've had it (other than when a tree grew in the way of the signal, warranting the "fixing" mentioned at the top of the page). I can't say I know if the cables have been shielded from degradation, but I'm going to be pretty ticked if such a professional-seeming ISP can't remember to do that. If the signal even causes degradation, again, I'm not familiar with the technology.

I am using a Dell Vostro 200 with 3 gigs of RAM, a 500MB hard drive (Ubuntu is here), a secondary 1 terabyte hard drive (for all my games), my graphics card is an NVIDIA GeForce GeForce 9800 GT with 33MHz, 64 bits width. Intel Core2 Duo CPU E4500 @ 2.20GHz.

---

### Post by xBiocorex on 2010-08-19
Sorry for the double-post, but I guess this issue can be marked as solved now, it was anything in this house at all. My ISP was having some issues around the time I posted this, and they are solved now. It was just a coincidence that I had also switched to Ubuntu while they were having problems. O_o

---

### Post by pricetech on 2010-08-19
So it was in fact  your ISP who conspired to destroy the web !!  And you tried to blame Ubuntu.

---


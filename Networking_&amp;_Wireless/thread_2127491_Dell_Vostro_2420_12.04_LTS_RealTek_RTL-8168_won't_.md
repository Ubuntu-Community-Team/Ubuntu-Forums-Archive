---
title: "Dell Vostro 2420 12.04 LTS RealTek RTL-8168 won't pick up a wireless signal"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by ubaldo1991 on 2013-03-20
Kind of cherry on the Linux world, I'm in Afghanistan, so all I can get is wireless signals through the ****** internet services here, so I can't connect with a wired connection.

The only driver I have installed is RealTek RTL-8168 Gigabit Ethernet driver which is useless without being able to get a wired connection, I tried to activate Broadcom STA wireless driver, but I can't download it without internet connection. I'm pretty sure this happened because of the latest updates.  

Dell-wifi is not soft or hard blocked, I know the wireless signal works hence why I'm on the internet now, I tried a lot of tricks by browsing for the last 3 hours but I think it's time to ask for help. Maybe I can just download the driver on this laptop and then transfer it with an USB memory stick? 

lspci
Network controller: Broadcom Corporation Device 4365
Ethernet controller: Realtek Semiconductor Co., Ltd. TRL8111/8168B PCI Exprexx Gigabit Ethernet controller

iwconfig
lo no wireless extensions.
eth0 no wireless extensions  

rfkill list
dell-wifi: Wireless LAN
soft blocked: no
hard blocked: no

I appreciate the help.

---

### Post by varunendra on 2013-03-20
Welcome to the forums ubaldo !

Onto your problem-

Please post outputs of-
```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by ubaldo1991 on 2013-03-20
I apologize, I could blame the infantry for my language, but is ultimately my fault. 

Ok.

ubaldo@ubaldo-Vostro-2420:~$ lspci -nnk | grep -iA2 net
07:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Dell Device [1028:0556]
    Kernel driver in use: r8168

---

### Post by ubaldo1991 on 2013-03-20
[IMG]http://i.imgur.com/TRpkng9.png[/IMG][IMG]http://i.imgur.com/leGtirK.png[/IMG]

---

### Post by chili555 on 2013-03-20
My friend Varun will, no doubt, want to see this: [http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)  Note the device ID is the same: 14e4:4365.

Note that the process and the package to be downloaded is different in 12.04 from 12.10. Now we return you to your regularly scheduled guru!

---

### Post by varunendra on 2013-03-20
> **chili555 said:**
> Now we return you to your regularly scheduled guru!
...who is just a 'mostly stupid' student of yours :)

Thanks for spoon-feeding me doc :P I already stole that link once, but now I'll remember this ID better.

@ ubaldo1991

I think this is the post that you are interested in : [http://askubuntu.com/a/175115](http://askubuntu.com/a/175115)
If you don't know whether your system is 32 bit or 64 bit, just run -
```
arch
```
If it returns x86_64, it is 64 bit, else it is 32 bit.

Download the relevant package and double-click to install. Post back if there are any dependency or other type of errors.

**PS:**
You can copy the terminal output with your mouse and paste it in your post like normal text. No need to take the trouble of screenshots :)

---

### Post by ubaldo1991 on 2013-03-20
It's 64 bit, I'll try this and will update you, I would copy and paste but my laptop running ubuntu can't connect to the internet, I'm using another laptop that does connect to the internet, so screenshot thumb drive and then here, so I still have to download and then transfer it to the ubuntu laptop. Hopefully it is simple
Thanks you!

---

### Post by ubaldo1991 on 2013-03-20
it conflicted with another package so I unistalled it and then tried to install and wouldn't allow me through the ubuntu software center, so I opened system settings, then additional drivers, selected Broadcom STA wireless driver, activate and @#$&%$# it worked :D Thank you guys, now I can go eat and enjoy my meal :)

---

### Post by varunendra on 2013-03-20
Hope it stays like that :)

---


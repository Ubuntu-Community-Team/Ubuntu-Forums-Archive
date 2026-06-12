---
title: "Internet is nomore"
date: 2012-12-20
forum: Networking &amp; Wireless
---

### Post by sandave003 on 2012-12-20
Hello! I have installed ubuntu; latest edition. I have a Huawei modem and general Wifi based internet at home, the thing is when inserted modem into linux system my modem started blinking, confirming that, it has been detected by the system. I made a network setup which was guided by one these forums only and started using internet happily, this is about day 1. Day2 when I booted to linux system some popup was saying "NETWORK DISCONNECTED, YOU ARE NOW OFFLINE"(I didn't do any operation concering network) I just don't know what to do, but tried creating new connection nothing helped and went to System settings and tried to do what I could but... no use.

Help me in figuring out this issue.

regards):P

---

### Post by UltimateCat on 2012-12-20
You said you have a Huawei modem. That's the make; see if you can find out what model # that might help to help you.
The manual is here on the manufacturer's page:
[http://www.huaweidevice.com/worldwide/faq.do?method=index&directoryId=50](http://www.huaweidevice.com/worldwide/faq.do?method=index&directoryId=50)

Can you ping in your terminal?
```
ping www.Google.com

```

Post here what the output is.

If your connection is wireless you will need to set up your Network Manager which is in the upper right hand corner of your Gnome Desktop.
Once you set that up (with mine) you have to put in your passphrase in order to connect. It's WEP for wireless and it's a most likely a WEP 40/128 bit key.

You might need a driver for your network interface card inside of your computer-
Open the terminal and run:
```
lspci

```

And post the output here in the forum so we can take a look at it.
That command helps to not only see pci buses but helps when your having problems. I'm not the expert at this but I'm not new to Linux either-

Are you using a usb adapter along with the modem to pick up the signal?

In my case I had to use a usb adapter because my wireless modem is way down the hall from my computer room. Than I had to install a driver for the adapter to aid the process.

If you have time read these pages they might be of some help to you.
[http://beginlinux.com/twitter/1096-ubuntu-wireless-setup](http://beginlinux.com/twitter/1096-ubuntu-wireless-setup)
[http://seogadget.com/how-to-setup-wireless-in-ubuntu/](http://seogadget.com/how-to-setup-wireless-in-ubuntu/)
[http://www.youtube.com/watch?v=m03RcFkSIA8](http://www.youtube.com/watch?v=m03RcFkSIA8)

---

### Post by sandave003 on 2012-12-25
Hello pal, I was so late to reply :( , I'm sorry. Thing is, when i tried googling from terminal, " unknown host". Once again I will explain, I was using wifi connection with security and I was using Huawei modem by creating a new connection with the name of my present ISP, and everything was working pretty well. I shutdown my linux and when I was back a pop up popped saying, YOU ARE DISCONNECTED FROM NETWORK AND YOU YOU ARE OFFLINE NOW. When I tried by pressing top right's button related to network, no sign of modem, wifi network's name nothing. In windows term, I could guess that something got disabled!

Please help

regards

---

### Post by lisati on 2012-12-25
What model Huawei modem do you have? The reason we have asked for this information is that the solution for a problem can be different even for devices from the same manufacturer.

---

### Post by sandave003 on 2012-12-26
It's E1731.

---


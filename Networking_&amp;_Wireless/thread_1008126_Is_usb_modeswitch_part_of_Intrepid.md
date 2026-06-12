---
title: "Is usb_modeswitch part of Intrepid ?"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-11
It seems that common ground for solving wireless networking problems is to install [usb_modeswitch]("http://www.greenhughes.com/content/using-huawei-e169g-usb-mobile-internet-modem-eee") , as wireless modems are (usually) USB, and getting Ubuntu to work properly with USB can be a task.

Is usb_modeswitch , part of Intrepid ? If so, will there be a backport of it, to Hardy ?

---

### Post by el Buffo on 2008-12-11
> **oygle said:**
> Is usb_modeswitch , part of Intrepid ? If so, will there be a backport of it, to Hardy ?

I think it's not part of Intrepid.
But here is a deb (Netbook Remix), don't know if it will work on Hardy... [https://forge.betavine.net/frs/?group_id=12&release_id=200](https://forge.betavine.net/frs/?group_id=12&release_id=200)

Greetings!
el Buffo

---

### Post by liamgh on 2008-12-19
I put together a small deb to get the Huawei E169G modem working on Ubuntu, it also includes a version of usb_modeswitch: [http://www.greenhughes.com/content/huawei-e169g-easy-way]("http://www.greenhughes.com/content/huawei-e169g-easy-way"). The package works on Hardy. On Intrepid I found that the modem would work with the Network Manager, and no other utility was needed.

---

### Post by oygle on 2008-12-20
Thanks liamgh. :)

Do you know if there are any plans by the Ubuntu team, to make usb_modeswitch part of Intrepid ? I just upgraded one comptuer to 8.10, and usb_modeswitch doesn't seem to be a part of it.

---

### Post by yadhav on 2008-12-29
Hi, following all these steps and many more, I had been able to connect my Huawei e169G Modem in Ubuntu. I made a blog where all the steps from A to Z have been mentioned. I'm 100 % sure that if you follow it properly, yours will be connected to. Here it is:
[http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/](http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/)

---

### Post by oygle on 2008-12-29
> **yadhav said:**
> Hi, following all these steps and many more, I had been able to connect my Huawei e169G Modem in Ubuntu. I made a blog where all the steps from A to Z have been mentioned. I'm 100 % sure that if you follow it properly, yours will be connected to. Here it is:
[http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/](http://crazyaboutubuntu.wordpress.co...ick-on-ubuntu/)

Okay thanks. I guess that link should be [Huawei e169G HSDPA USB Stick on Ubuntu &laquo; CRAZY ABOUT UBUNTU]("http://crazyaboutubuntu.wordpress.com/huawei-e169g-hsdpa-usb-stick-on-ubuntu/")

Are you using this on Intrepid, and does it work for 64-bit ?

Also, are you using the E169 modem as a USB dongle (directly attached to computer), or on a router ?

I assume you are using wvdial for this, and not Network Manager. I see there is a [bug]("https://bugs.launchpad.net/ubuntu/+bug/301248") for salutis connect.

Oygle

---


---
title: "Wireless connection with Asus eeepc 4G (700)"
date: 2008-12-05
forum: Networking &amp; Wireless
---

### Post by yvesbaja on 2008-12-05
Dear Kubuntu or Ubuntu users:

I have just installed Kubuntu 8.10 on a Mobile HD (120 GB) from my ASUS eee PC 4G (700)., 

When trying to connect to the Internet, I hit a severe roadblock:

MY ASUS eee PC is mounted with an Atheros Communications Inc. AR8007EG 802.11 b/g Wireless PCI Express Adapter, designed for ath0 wireless connections. My Kubuntu is geared only to the use of eth0 and my machine cannot detect my wireless network. With the ASUS provided Xandros linux, I have no difficulty connecting.

Any idea about how to resove this problem?

Thanks in advance


Yves Bajard

---

### Post by MarblePanther on 2008-12-05
I have an Asus 900A and this is what I did to get Ubuntu to work on it:

Just follow the directions on this site to add a custom eeepc Ubuntu kernel to your sources list.  This custom kernel includes fully-working support for the Atheros wireless.  It works flawlessly on mine.  Good luck!

[http://www.array.org/ubuntu/setup-intrepid.html](http://www.array.org/ubuntu/setup-intrepid.html)

Reboot and hit "Esc" at the countdown before Ubuntu boots and choose the eeepc kernel from the GRUB list

---

### Post by snowpine on 2008-12-05
I agree, the array.org kernel has worked out really well on my eee pc 900ha.

To add something to the conversation, a great resource for Kubuntu on the eee is this forum: [http://forum.eeeuser.com/viewforum.php?id=43](http://forum.eeeuser.com/viewforum.php?id=43)

Good luck!

---

### Post by yvesbaja on 2008-12-07
Thanks to Marble Panther and snowpine for their rapid responses.

I have checked the references you gave me and see the light at the end of the tunnel. Yet, I do not feel at ease with the  directions given in the FAQ on this site to add a custom eeepc Ubuntu kernel to my sources list. 

I can easily go to [http://www.array.org/ubuntu/setup-intrepid.html](http://www.array.org/ubuntu/setup-intrepid.html) .
However, as I can download the files only when operating in Xandros, I am not sure that Ht I can use that file when I get off Xandros and reboot in Kubuntu.

More precisely, I think that I should download the kernel into /dev/sdb10, which is a common Kubuntu-Xandros folder where I store my current work, data and software packages in distinct sub-folders. 

Then, when rebooting in Kubuntu, and hitting esc before making a choice, does the process continue in x-window or in command line with sudo commands? If in command line, what typical commands should I type?

Thanks in advance for further advice.

all the best

Yves Bajard

---

### Post by MarblePanther on 2008-12-07
This distro is best for using ubuntu on the eee:

main page:
[http://ubuntu-eee.com](http://ubuntu-eee.com)

download:
[http://ubuntu-eee.com/wiki/index.php5?title=Get_Ubuntu_Eee](http://ubuntu-eee.com/wiki/index.php5?title=Get_Ubuntu_Eee)

It has support for atheros in their custom kernel.

Use this to have a better experience with ubuntu on an eee

---


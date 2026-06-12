---
title: "Why is wireless networking in ubuntu 12.04 so slow"
date: 2012-08-28
forum: Networking &amp; Wireless
---

### Post by O2Blevel on 2012-08-28
I have ubuntu 12.04 installed on my laptop along with windows vista. Using the same wireless card and downloading the same file from the internet, windows vista is nearly twice as fast as ubuntu 12.04.

I also have ubuntu 11.10 on an old desktop and it too is nearly twice as fast as ubuntu 12.04. The only changes I've made to networking is removing network-manager from both machines. Anyone have an idea as to what I could do to increase my networking speed in ubuntu 12.04?

---

### Post by moribashi on 2012-08-28
And what kind of laptop do you have? I had a lot of problems with my Acer (Atheros card)...

---

### Post by O2Blevel on 2012-08-28
My laptop is a Dell e1505 and I'm using a usb TI card with the  acx100 driver.

You may want to look at this thread:

[http://ubuntuforums.org/showthread.php?t=1877120]("http://ubuntuforums.org/showthread.php?t=1877120")

I saw several references to the atheros card.

---

### Post by Szor3n on 2012-08-28
Is it by any chance a wireless N card?  Because there is a known kernel issue with N and certain cards.

---

### Post by O2Blevel on 2012-08-28
No not an N card. I don't think it's the wireless card, I think it may be network settings. I tried disabling IPv6, but that didn't help.

---

### Post by dnukumamras on 2012-12-20
[B]In case you are facing slow wireless speeds in ubuntu 12.04 try this

Open a terminal (alt+ctrl+t)
type
 sudo rmmod -f iwlwifi

then
[/B] [B]sudo modprobe iwlwifi 11n_disable=1

now check if the speeds have improved. if yes lets make it permanent

type
[/B][B]gksudo gedit /etc/modprobe.d/iwlwifi_disable11n.conf

add the line

[/B]**options iwlwifi 11n_disable=1**

[B]to the end of the file.save and quit!!!:grin:


in-case you get an error like

ERROR: Removing 'iwlwifi': No such file or directory

replace iwlwifi with iwlagn in the above commands and try again.[/B]

---


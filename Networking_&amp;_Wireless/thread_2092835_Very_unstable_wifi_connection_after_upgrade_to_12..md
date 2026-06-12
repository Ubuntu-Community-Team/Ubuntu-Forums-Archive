---
title: "Very unstable wifi connection after upgrade to 12.04(Atheros AR9287)"
date: 2012-12-09
forum: Networking &amp; Wireless
---

### Post by cleopatra on 2012-12-09
my laptop is acer aspire 4743G, wireless connection is ok for windows 7;

used to be ok for ubuntu 10.04, and very instable after an update to 12.04. And the wifi problem only happens at home...

$ lspci -nn | grep 0280
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)

could you help me? :):) I am so distressed that I am thinking of buying mac for paid linux...

---

### Post by johnycsf on 2012-12-09
Upgrading to Ubuntu 12.10 might fix it.

---

### Post by cleopatra on 2012-12-09
> **johnycsf said:**
> Upgrading to Ubuntu 12.10 might fix it.

so have you experienced this?

---

### Post by johnycsf on 2012-12-09
Yes I did. Which is why I recommended the update.
The latest version of the OS will have the most up to date drivers but if you don't want that you can try to find a driver for your wifi card straight from the manufacturer website instead of a generic driver.

---

### Post by ninovolador on 2012-12-09
Had problems with Atheros wireless card, 

entered > sudo -s
echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf at terminal

Magically solved

now have other problems, but lasted a while ;)

---

### Post by cleopatra on 2012-12-10
> **johnycsf said:**
> Yes I did. Which is why I recommended the update.
The latest version of the OS will have the most up to date drivers but if you don't want that you can try to find a driver for your wifi card straight from the manufacturer website instead of a generic driver.

Hi, thanks johnycsf! I updated to 12.10; I tried a few times, and the connection has been ok. I will report if the connection once again becomes instable.

---

### Post by kurt18947 on 2012-12-10
> **cleopatra said:**
> Hi, thanks johnycsf! I updated to 12.10; I tried a few times, and the connection has been ok. I will report if the connection once again becomes instable.

I am running the gnome version of 12.10.  I found that ninovolador's fix seemed to help with stability.  The ath9k support does not seem as good on 12.04/12.10 as it was in 11.04./11.10 IME.

---

### Post by cleopatra on 2012-12-12
> **kurt18947 said:**
> I am running the gnome version of 12.10.  I found that ninovolador's fix seemed to help with stability.  The ath9k support does not seem as good on 12.04/12.10 as it was in 11.04./11.10 IME.

never tried 11.x, connection on 12.10 is so-far-so-good. Is gnome version of 12.10 same as the 12.10 I talk about?

---

### Post by kurt18947 on 2012-12-12
> **cleopatra said:**
> never tried 11.x, connection on 12.10 is so-far-so-good. Is gnome version of 12.10 same as the 12.10 I talk about?

I'm glad to hear it's working. The gnome version I referred to is a remix of Ubuntu 12.10.  It uses Gnome 3 as the default desktop rather than Unity and is still somewhat new.

---

### Post by cleopatra on 2012-12-15
sorry to say, that when I switch back from windows 7 to ubuntu 12.10, the wireless network once again becomes unstable!

---

### Post by lurgee on 2012-12-15
Define unstable.  I had an issue where I had to manually reload the driver every time I turned on the computer, using a wired connection to do so.  Is that anything like what you are experiencing?  Is there any discernible pattern to when it works / falls over?

---


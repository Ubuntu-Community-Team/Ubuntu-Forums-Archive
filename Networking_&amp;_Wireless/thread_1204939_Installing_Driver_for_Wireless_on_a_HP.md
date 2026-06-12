---
title: "Installing Driver for Wireless on a HP"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by Lunar Vixen on 2009-07-05
I have just successfully installed a Dual Boot of Ed/Ubuntu and Vista on my HP Pavilion dv 9310. I have a wireless network card in it as well, but do not have a way of turning it on, within Ubuntu. I've searched for directions on what to do, however, what I have found does not make sense to my stay-at-home mom brain. IE: it was too high-techy for me to understand.

Is there anyone who can help me out in simple speak? This is my first time using Ubuntu, let alone any other Linux derived system, and I attribute my successful first time installation to pure dumb luck.

Thanks in advance.

---

### Post by Bucky Ball on 2009-07-05
If you have an ethernet cable, plug it in and boot up the computer. You will probably be offered the restricted third party hardware drivers after you get online and download updates for the first time.

No, not dumb luck. If your hardware is compatible, all should be pretty smooth. 9.04 or 8.04?

---

### Post by Lunar Vixen on 2009-07-05
D'oh.. I should have mentioned that! I've installed 9.04 (it's called Jaunty Jackalope right?).

I'm currently wired on the LAN, and nothing's come up so far, but I will try a restart and see what happens.

---

### Post by Bucky Ball on 2009-07-05
Open a terminal (Applications->Accessories->Terminal) and paste this in:

```
sudo apt-get update
```

Also, check in System->Administration->Hardware Drivers

What have you got there?

Also in a terminal, paste this:

```
lspci
```

Somewhere near the bottom you will find your wireless card. Post that back here.

---

### Post by paul_be on 2009-07-05
:(

---

### Post by Lunar Vixen on 2009-07-05
Here I am on the internet!

After your post, I did a restart but nothing came up. So I thought maybe I had to find a way to initiate it to realise it needed a driver. So I click on System, Administration, and saw Hardware Drivers. Once I clicked on that, it started searching and immediately came up with the Wireless (Broadcom) and the option to activate it. So I activated it, it downloaded and installed a driver, told me to restart. And a little fiddling in the network connections to set up my wireless network connection and voila! It's working!

Thanks!

---

### Post by Bucky Ball on 2009-07-05
Excellent! That's what we were looking for! The Broadcom cards were a nightmare but the new drivers have been developed to make it that easy. Welcome and have fun. Don't forget to post back with any probs. :)

---


---
title: "Eee 1005ha Wireless not working in 10.04"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by jlandaw on 2010-04-30
Here is the problem...  I upgraded my Eee pc 1005ha from 9.10 to 10.04 today. I cannot get the wireless card to work at all... I installed the backports the same as on 9.10, but nothing happens... HELP

[B]SOLVED: 2 easy steps to get your wifi working on you 1005ha in 10.04

1. Turn on your wifi in your BIOS...

[INDENT]Press f2 at start up and change your onboard settings.... (might as well do this for your camera and Bluetooth too... if you wnat to use them)[/INDENT]

2. enable the backports:

[INDENT]Either go to your synaptic package manager and look for 

     linux-backports-modules-wireless-lucid-generic .. or

in a terminal put: 

```
sudo apt get install linux-backports-modules-wireless-lucid-generic
```

enter your password and follow instructions...[/INDENT]

you may have to restart... that will take care of the wifi issue![/B]

---

### Post by drblast on 2010-04-30
I'm having the same trouble with my 1005ha.  I upgraded which broke a number of things including wireless, and then I tried installing from scratch.  No dice.

Installed wireless backports and "sudo ifconfig wlan0 up" gives the following error:

Unknown error 132

Wireless led won't even turn on.  Wireless hardware is Atheros AR9285 (rev 1) if that helps anyone.

---

### Post by jlandaw on 2010-04-30
SOLVED!!!

you need to enable your wifi in the BIOS...(while you are there might as well enable your Bluetooth and camera if you plan on using them...) 

I do think you need to enable the backports too... but check the BIOS first...

Im going to uninstall the backports and get post the results on this thread, then i will say it is solved totally...

---

### Post by CharlesA on 2010-04-30
I had no problems with wifi on my Asus 1005HA. Worked fine with a default install. :)

---

### Post by www271828 on 2010-05-07
Thanks jlandaw for your posting.

I had the same problem on my EeePC 1005HAE.  (Both wire-line ethernet & WIFI does not work after I upgraded to Ubuntu 10.04.)  I changed my default BIOS setting according to your posting & eth0 & WIFI now both work ok!

---

### Post by chapman.s87 on 2010-05-18
thanks, the bios enable fixed everything. KK worked from install so i was wondering what happened to LL.

---

### Post by sabjap on 2010-08-19
Thanks an awful lot for the solution and for naming it appropriately so all in need can find it !! Best regards

---

### Post by barrieluv on 2010-08-20
This issue only seems to affect those who upgrade from 9.10 to 10.04.
Wireless worked perfectly on my 1005HA and 1005P out of the box with fresh installs of 10.04.
It is, however, always advisable to check  that wireless (along with other bits) is enabled in the BIOS on first boot.

---

### Post by energichen on 2010-08-23
I have similar problem with my eee pc 1005ha, everything from posts above have done but still no internet. I using cable internet with wireless ruter in my desktop, when i plug in cable in eeepc i have internet but after unpluged no internet is there some solution for this?
Do i need to create new internet connection?

---

### Post by finnbuntu on 2010-08-23
> **barrieluv said:**
> This issue only seems to affect those who upgrade from 9.10 to 10.04.
Wireless worked perfectly on my 1005HA and 1005P out of the box with fresh installs of 10.04.
It is, however, always advisable to check  that wireless (along with other bits) is enabled in the BIOS on first boot.
On my Eee PC 901, you have to install the package, even on a clean install.
finnbuntu

---

### Post by pwolfinger on 2010-12-18
None of the proposed solutions have worked for me on my 1005ha (technically 1005hab, but it's just a black version of the 1005ha). I'm 99% certain I've enabled it in the BIOS (it looks so but I'm not entirely sure what I should be seeing there). I'm actually on 10.10 Maverick and it didn't find the package after telling it to install the Lucid wireless. It actually didn't find the Maverick version in Terminal either so I looked it up in Synaptic and it showed that I had already installed the packages I need. Any ideas?

---

### Post by dawtier on 2010-12-25
> **pwolfinger said:**
> None of the proposed solutions have worked for me on my 1005ha (technically 1005hab, but it's just a black version of the 1005ha). I'm 99% certain I've enabled it in the BIOS (it looks so but I'm not entirely sure what I should be seeing there). I'm actually on 10.10 Maverick and it didn't find the package after telling it to install the Lucid wireless. It actually didn't find the Maverick version in Terminal either so I looked it up in Synaptic and it showed that I had already installed the packages I need. Any ideas?

Im in the same situation. Can anyone help?

---


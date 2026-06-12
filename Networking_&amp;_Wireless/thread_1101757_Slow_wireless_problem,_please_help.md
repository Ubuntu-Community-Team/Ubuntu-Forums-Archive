---
title: "Slow wireless problem, please help"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by black.flame on 2009-03-20
Hello all,

I am running ubuntu 8.10 and am experiencing very slow wireless internet connection.

When I had XP I was experiance DL rates of 300kb/s+ and under ubuntu I get 10.5 kb/s if I even get a rate

It says I'm connected and the speed is 54mb/s and I'm using the rtl8187 driver using as Rosewill RNX-G1 wireless usb 2.0 adapter on my desktop computer

when I first connect to the network I can browse the internet for a few second then it just stops

I searched tons of forums but nothing helped

I am very new to linux so please give as much detail as you can

thanks in advance

---

### Post by Utgaard Loki on 2009-03-23
I also had problems with terrible dull surfing speed after upgrading to 8.10
This worked for me:

in the terminal

gksudo gedit /etc/modprobe.d/aliases

find the line 
"alias net-pf-10 ipv6"

and replace it with the two lines:

alias net-pf-10 off
alias net-pf-10 off ipv6

Then check your host names by typing (in terminal)

sudo gedit /etc/hosts

change the two first lines so its says:

127.0.0.1	localhost
127.0.1.1	localhost


Hope its works for you 2!

---

### Post by black.flame on 2009-03-23
I tried that and it didn't help thanks for trying though,

What I ended up doing was blacklisting my rtl8187 driver then using the ndiswrapper to install my old windows driver for it and it worked like a charm

but one interesting thing that i found was that my windows driver for it is actually based on a (not necessarily the linux default one) rtl8187 driver

but none the less my solution worked perfectly and have had no problem with internet since

flash and installing my nvida driver is another story, but that is a headache for another day

---

### Post by sabre2th on 2009-06-08
> **black.flame said:**
> I tried that and it didn't help thanks for trying though,

What I ended up doing was blacklisting my rtl8187 driver then using the ndiswrapper to install my old windows driver for it and it worked like a charm

but one interesting thing that i found was that my windows driver for it is actually based on a (not necessarily the linux default one) rtl8187 driver

but none the less my solution worked perfectly and have had no problem with internet since

flash and installing my nvida driver is another story, but that is a headache for another day
I've got one of those and I had some trouble initially, too.  I don't know if it applies to Intrepid, but there's a known issue with Jaunty for our adapter.  Installing linux-backports-modules-jaunty fixed it for me.

Anyway, I guess you don't need me if it's working now, but maybe it'll help someone...

---


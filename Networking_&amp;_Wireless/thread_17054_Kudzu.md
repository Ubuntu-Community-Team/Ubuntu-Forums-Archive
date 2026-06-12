---
title: "Kudzu"
date: 2005-02-25
forum: Networking &amp; Wireless
---

### Post by lao_V on 2005-02-25
Hi Guys,

I'm trying to install a PCMCIA US robotics wireless card on my Warty through Kudzu.

However, I get the following error:

/usr/sbin/netconfig: no such file or directory

Can anyone help?

Thanks!

---

### Post by alastair on 2005-02-25
Kudzu? - I thought that might have been a Redhat/Fedora thing only ...

But it does look like /usr/sbin/netconfig is not on Ubuntu. It does exist on Fedora though - so Redhat only perhaps?

---

### Post by az on 2005-02-25
sudo dpkg-reconfigure etherconf

or

sudo apt-get install etherconf


Maybe that is what yo uare lookig for?

---

### Post by Xanthous on 2005-07-24
[QUOTE=lao_V]Hi Guys,

I'm trying to install a PCMCIA US robotics wireless card on my Warty through Kudzu.

However, I get the following error:

/usr/sbin/netconfig: no such file or directory

Can anyone help?

Thanks![/QUOTE]

Where you able to get your network card to work?  I also need to get a US Robotics pcmcia wireless card to work on a Dell Latitude CPX.   :-k

---

### Post by lao_V on 2005-07-26
[QUOTE=Xanthous]Where you able to get your network card to work? I also need to get a US Robotics pcmcia wireless card to work on a Dell Latitude CPX. :-k[/QUOTE]

It works on Hoary out of the box only when the network in not encrypted. The card uses the TI ACX 100 chipset. I think you can now get drivers for it which works with encrpyted networks.

---


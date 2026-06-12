---
title: "Wireless works with Ubuntu 8.10 but not with Kubuntu 8.10"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by manilaph on 2009-02-05
I know this sounds or feels strange... but wireless works flawlessly with Ubuntu 8.10. 

I wanted to try out Kubuntu 8.10 and so I tried the LiveCD but it could not connect to the wireless WEP-secured network. It could only detect it. 

I wanted to install Kubuntu because I am attracted to KDE but thought otherwise since wireless connectivity is an issue.

Why is this so? Why flawless with Ubuntu but problematic with Kubuntu?

This is the same exact machine Compaq Presario V3000 Centrino Duo.

Thanks!

---

### Post by manilaph on 2009-02-06
I've noticed a lot of "wireless problem issues" with Kubuntu and not as much with Ubuntu.

Kubuntu can't connect wireless but Ubuntu can.

Is this strange or normal?

Is it a Gnome / KDE thing?

---

### Post by jolx on 2009-02-06
if it's working fine atm, then why not just install the 'kubuntu-desktop' package. Then log out, select a kde session and log back in, then see if it is still working.

---

### Post by phaello on 2009-03-14
Yes this is really a pain to me, Since Ubuntu 8.10, only gnome has been able to connect to wireless without a problem, but KDE does not.  I finally installed KDE desktop on gnome, and that way all the time I switch on the machine I would have to log on to the gnome first and establish a wireless connection; then logout and go to KDE, that way I would have wireless connection on KDE.  my wireless connection uses WEP 40/128-bit Key, and with gnome all I had to do at the beginning was to type the key, and I was connected.  on the kde side, security appears as passphrase or Hex key, and passphrase is always the default one, even if one tries to change to Hex key, it reverts back to passphrase.  I have been trying the different alpha releases of Jaunty - 9.04, up to the latest one - alpha 6, the same problem persists.  It is even worse with 9.04 because even if I have kde desktop installed on ubuntu, having connection on the gnome side and then logging off to log on the kde side does not give any connection of the kde desktop to wireless.  Can anyone help here, I would love to use KDE, but the inability to connect to wireless puts me off.  I must say with a wired connection there is not problem with kde.

phaello

---

### Post by manilaph on 2009-03-14
i think the best solution is to remove **networkmanager** from Kubuntu and just install **wicd**.

there must be something buggy about the kubuntu-networkmanager connection.

wicd can run in other desktop environments while the networkmanager is gnome-based.

am i correct?

---


---
title: "I broke network-manager"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by mpc350 on 2009-04-08
Using eeebuntu on my eee pc.  This is totally my fault.  I got to thinking... how well do other wireless configuration utilities work instead of network-manager?  So I installed Wicd, and it worked to the point that it could see other networks but would never connect.  I said eh... I'll just go back to network-manager, and reinstalled it.  Upon finishing, network-manager seems to work fine for wired connections, but will not see my wireless card.  There is no option for "enable wireless networks"  

It worked fine before, and I broke it.  Oh well.  It's how I learn.  

Anyone know how to get the card to recognize?

Thanks in advance
Matt

---

### Post by Michael.Godawski on 2009-04-08
hey mpc350, 

I was just wondering if this is a problem of the actual network-manager which is somewhat broken after the re-installation, or if the manager is working fine, and something was messed up with the wireless drivers of your card.

Was there an "enable wireless networks" option before the experiment?

What is your wireless card?
Please post the output of:
```
sudo lshw -C network
lspci -nn
iwconfig

```

---


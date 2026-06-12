---
title: "New to ubuntu.."
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by Kayuu on 2011-01-15
Hey, so I'm totally new to ubuntu so I thouhgt I'd give it a try yesterday. I used the Ubuntu 10.10 live install CD whilst in windows XP and install it alongside so my PC is now able to dual boot into either distro. 

I ran into problems when I was trying to install my belkin wireless USB adapter F6d4050. I've read around forums and tried various things but I've had no luck even though it is possible it seems. 

I've tried to install ndiswrapper-common, ndiswrapper-utils-1.9 and ndisgtk but I'm not sure they're installing properly? First of all, the synaptic package manager would NOT mount the ubuntu CD when I tried to add that, when I went into repositries and added it as a source I got various W: fetch errors, they seem to be trying to connect to webpages (I have no internet connection obviously), so I updated and searched for "ndis" (still in SPM) I found them and tried to install them but only ndiswrapper-common installed, installation of the other two didn't go ahead as the SPM couldn't locate them even though I found them in the path it was specifying, on the CD.

So I tried install them from the CD itself using the software center thing, it seemed to work as Windows wireless drivers turned up in adminstration, but everytime I try to run the program it hangs and I have to foce quit, it's really frustrating as I have no idea what to do now.

[Side notes] Ubuntu can see my device as it turns up in lsusb in terminal, I've followed some advice in the post of another OP using gedit to add a command strings for network_drivers.rules & network_drivers.conf but it doesn't seem to have done anything? >< rt2870sta 050d?

---


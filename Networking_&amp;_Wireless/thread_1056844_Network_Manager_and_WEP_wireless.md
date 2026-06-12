---
title: "Network Manager and WEP wireless"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by anlag on 2009-02-01
I just did a clean install of Intrepid and notice the included (with possible updates from repositories) Network Manager, v 0.7.0, does not list the wireless network at my girlfriend's house. It's a WEP encrypted network with 128-bit passphrase. The list is not empty; there are three other secured wireless networks, but not the one I need. I've tried logging on to it as if it were a hidden network, but with no luck.

Now, the network itself is working fine, since if I boot into Win XP instead it discovers the desired network fine and also connects fine when I enter the passphrase. It also worked fine from my Hardy installation, although I do remember having to tweak the settings a little the first time I set that up (I think changing manually from TKIP to whatever the other option is, or the other way around.)

The current installation works fine in my home where I have a WPA secured wireless, so it's not completely broken.

The only real idea I have is that same setting in encryption I had to do manually when I configured this network for Hardy. But the problem is, in this version of Network Manager, the TKIP/?? setting does not seem to be available - at least not in the GUI which is what I use.

My machine is a Thinkpad T61 and the wifi card is:

> $ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Any suggestions?

---

### Post by anlag on 2009-03-03
This issue still remains. I tried installing WiCD instead, to see if it would make a difference but it also cannot even see the WEP network. This makes me think it might be an issue with the wireless driver, but I don't really know how to proceed from this. 

It's a rather troublesome one though, since many older and public networks are stuck with these kinds of encryptions and not being able to use them under Ubuntu is a big nuisance.

---

### Post by anlag on 2009-09-17
Revisiting this thread simply to say that after dist-upgrading to 9.04 a couple of months ago, the laptop connected fine to the same network without any further ado.

---


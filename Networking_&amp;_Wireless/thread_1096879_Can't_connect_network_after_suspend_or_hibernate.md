---
title: "Can't connect network after suspend or hibernate"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by larryma on 2009-03-15
I am using a Dell precision M60 laptop and a Level One PCMCIA wireless adapter card with an Atheros AR5001X inside. OS is Ubuntu 8.10. During normal bootup, networking is fine in that the desktop opens, then the NetworkManager Applet 0.7.0 connects to the network easily and without intervention.

However, if I suspend or hibernate the machine, upon startup the wireless network is not connected. With suspend, the network icon spins for about 60 seconds, but cannot connect. Left clicking on the icon shows that it sees the network, but for some reason can't connect to it.

After hibernate, the machine asks for the network passcode and left clicking shows that it sees the network, but again it doesn't connect to the network.

For another data point, if I right click the icon, then disable/enable the wireless, the system no longer sees any network for some reason.

So there seems to be a difference when starting from a clean reboot versus starting from a suspend or hibernate with respect to the network manager. I currently handle this by either leaving the laptop on all the time, or if I need to save power, shutdown and then do a full reboot when needed again. Not a very good situation.

Any help would be appreciated.

Larry

---

### Post by inobe on 2009-03-15
that's funny' i just got an update for network manager related to udevadm trigger....

fixes a bug in network manager on a system using dkms

---

### Post by larryma on 2009-03-15
thanks! Do you think this update will solve the problem? How should I get in and install it?

Larry

---

### Post by inobe on 2009-03-15
larry' i am uncertain, i received the update when i replied to your post.


here is the page [https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/320200](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/320200)

i installed the update' but didn't experience the bug since i am not on a laptop' but on a desktop with wireless.

it's obviously some sort of power management bug' that's why i mentioned the update, i hope it solves what ever is wrong.

as far as downloading it' you should have received the update by now from synaptic, if you havent' run this command in terminal' let it do it's thing, once done close terminal and wait for the update prompted in the upper right corner.

```
sudo apt-get update
```

that will refresh your sources

---

### Post by larryma on 2009-03-16
No luck, unfortunately. 

I am fully updated, according to the update manager. I ran your command for good measure. Still have the same issue after suspend or hibernate.

Any other ideas?

Larry

---

### Post by larryma on 2009-03-19
Any other suggestions by anyone? Is there an alternate power management/hibernate routine I could load?

Larry

---

### Post by akudewan on 2009-03-31
Hi,

I had a similar  problem with my wired connection. NetworkManager would show my connection as *disconnected* after resuming from suspend. I found the solution on this blog: [http://penguinparens.blogspot.com/2008/11/fixing-your-ubuntu-suspendresume.html](http://penguinparens.blogspot.com/2008/11/fixing-your-ubuntu-suspendresume.html)

Perhaps you could try that, replacing *forcedeth* with whatever driver the wireless adapter uses...

---

### Post by larryma on 2009-04-06
Akudewan,

That fix worked like a charm and was so easy! Thank-you for the great find which improves my laptop 100%.

Larry

---


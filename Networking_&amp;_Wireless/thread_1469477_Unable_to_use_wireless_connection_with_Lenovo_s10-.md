---
title: "Unable to use wireless connection with Lenovo s10-2"
date: 2010-05-02
forum: Networking &amp; Wireless
---

### Post by allp on 2010-05-02
Hi

I've got a Lenovo S10-2 which used to see and connect to wireless networks, but after updating to Ubuntu Netbook Edition 10.4, it is unable to see any wireless networks.

Apter running lspci, it appears that I have 
Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

I have also installed and activated the wireless Broadcom STA driver.
bcmwl-kernel-source is installed too.

What can I do? Thanks for your help

---

### Post by Rifester on 2010-05-02
I also have the netbook.   The easiest thing to do is plug it into an ethernet cable.   Run the update manager, and then System->Hardware Drivers, Activate the Broadcom STA driver, reboot, and you are done!

---

### Post by sirwhiteout on 2010-05-20
I also have the S10, and I am experiencing the same problem.

Using the proprietary driver works, but the wireless network functions poorly. The range is very short and the connection is unstable. I have had a hard time getting a simple Skype conversation going, and even being 1 m away from the access point, it kept disconnecting on me every few minutes.

Is there any way to revert to the Karmic driver which worked perfectly?

---

### Post by agentsands on 2010-05-24
Have you been updating from karmic to lucid? Wireless worked perfectly with karmic on my S10-2. I experienced problems after updating to lucid. The connection got lost every few minutes, after restarting it was even worse until a connection has been established.
 
In my case, the problem was a conflict between wicd / wicd-client and the built-in wireless manager. (wasn't a problem on karmic though)
They get mixed up trying to get a connection established, but each tool seems to make the wlan adapter busy. I didn't get deeper into the actual reason, but after removing wicd, everything worked nicely:
 
```
 
sudo apt-get remove wicd
sudo apt-get remove wicd-client
sudo apt-get autoremove

```
 
I guess it works everything fine when installing from scratch?? (of course, you have to enable the broadcom driver manually)

---

### Post by sirwhiteout on 2010-05-24
> **agentsands said:**
> I guess it works everything fine when installing from scratch?? (of course, you have to enable the broadcom driver manually)

Unfortunately, no. Actually, at first I upgraded from Karmic and the wireless worked perfectly, but I had [other problems]("https://bugs.launchpad.net/window-picker-applet/+bug/248324") with the Gnome session, so I installed from scratch. That's when the problems with the wireless started.

Since my technical knowledge with Linux is very limited, I tried the Windows-like solution (removing and reinstalling the Broadcomm driver), and so far it hasn't caused me any major headaches, although the range is still annoyingly short.

---

### Post by sirwhiteout on 2010-07-20
I have bug-reported the range problem on Launchpad, for bcmwl-kernel-source 5.60.48.36

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/607762](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/607762)

What was the version of this driver on Karmic? Is there a way to revert to it on Lucid?

---


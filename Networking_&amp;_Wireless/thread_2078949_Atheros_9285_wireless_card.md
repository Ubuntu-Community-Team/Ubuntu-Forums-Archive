---
title: "Atheros 9285 wireless card"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by Maheriano on 2012-11-01
Every website I look at says it's blacklisted and won't work, then they offer work arounds, all of them which I've unsuccessfully tried. The device I'm using is a [MSI Windpad]("http://www.memoryexpress.com/Products/MX37383") which I've installed Ubuntu 12.10 on and everything seems to work fine except the wireless, I can't even view any wireless networks with it. It doesn't work at all. Does anyone have a sure fire way of getting the wireless to work with this chipset?

---

### Post by chili555 on 2012-11-01
Hmmmm. I love a challenge. Please run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by Maheriano on 2012-11-02
I actually got it. Ubuntu is a little behind in their kernel releases, they're only on 3.5 right now because they modify the kernel and then release their custom version of it. The current stable release is at 3.6 which Ubuntu hasn't yet released so going to [www.kernel.org](www.kernel.org) and downloading the newest kernel. Installing that caused wireless and multitouch to work out of the box.

---

### Post by leunam12 on 2012-12-03
> **Maheriano said:**
> I actually got it. Ubuntu is a little behind in their kernel releases, they're only on 3.5 right now because they modify the kernel and then release their custom version of it. The current stable release is at 3.6 which Ubuntu hasn't yet released so going to [www.kernel.org]("http://www.kernel.org") and downloading the newest kernel. Installing that caused wireless and multitouch to work out of the box.I,m going to try this. I have a lot of problems with this wireless card.

Here a link that I found of a script that automates the kernel installation process
[http://www.liberiangeek.net/2012/10/install-upgrade-to-linux-kernel-3-6-0-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/10/install-upgrade-to-linux-kernel-3-6-0-in-ubuntu-12-04-precise-pangolin/)

I don't know if it works, I haven't tried it yet.

---

### Post by leunam12 on 2012-12-04
> **leunam12 said:**
> I,m going to try this. I have a lot of problems with this wireless card.

Here a link that I found of a script that automates the kernel installation process
[http://www.liberiangeek.net/2012/10/install-upgrade-to-linux-kernel-3-6-0-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/10/install-upgrade-to-linux-kernel-3-6-0-in-ubuntu-12-04-precise-pangolin/)

I don't know if it works, I haven't tried it yet.I installed the newest stable kernel from kernel.org and that did not solve the problem.

**Edit 12/05/2012: **After I rebooted the second time after installing the kernel wireless seems to be working normally.

---

### Post by wiligelmo on 2012-12-04
i've got the same problem

---

### Post by chili555 on 2012-12-04
And I have the same request. Please run and post:```
lspci -nn | grep 0280
rfkill list all
```

---

### Post by godgone on 2012-12-04
Ok, I got a problem with my atheros 9287 card, it can connect everywhere else but can't seem to connect to WPA2 protected networks.

---

### Post by ITProInTraining on 2012-12-04
I don't know if it will help you, but I had to use ndiswrapper to make the drivers for an Encore Electronics wifi card work.  You may be able to use something similar.

---

### Post by wiligelmo on 2012-12-10
the result of the two commands are ... nothing! no answer!

```
marconicole@desktop:~$ lspci -nn | grep 0280
marconicole@desktop:~$ rfkill list all

```

---

### Post by chili555 on 2012-12-10
> **wiligelmo said:**
> the result of the two commands are ... nothing! no answer!

```
marconicole@desktop:~$ lspci -nn | grep 0280
marconicole@desktop:~$ rfkill list all

```Let's dig deeper:```
sudo lshw -C network
lsusb
```

---

### Post by Maheriano on 2013-03-04
Actually I lied, updating the kernel did not fix it. The problem was these tablets have a hardware lock on the Wi-Fi adapter and the only way to unlock it is to boot into Windows and run the MSI specific unlocking software which comes with the tablet. Then once the adapter is unlocked, you can install Ubuntu and it will work.

I have 10 of these tablets here and I installed Ubuntu onto one of them before I figured this out so I'm actually in the process of getting an external DVD reader so I can reinstall Windows, unlock it, then reinstall Ubuntu. I have no idea why MSI did this.

---

### Post by chili555 on 2013-03-04
> I can tell you something about a turntable.
I have two of them.
Where it's at.Amen, brotha! A Rega and a Linn.

I am likewise stunned by MSI's actions. The conspiracy theorists among us will smell something funny here. I won't name names, but its initials are MSFT (NASD: 28.15).

We look forward to your report.

---

### Post by Maheriano on 2013-03-07
Just went through all 7 tablets that I have here, all of them were the same. Wi-Fi was hardware locked so I had to boot into Windows, run the MSI hardware unlocker, reboot and install Ubuntu. I've seen few things dumber than this.

---


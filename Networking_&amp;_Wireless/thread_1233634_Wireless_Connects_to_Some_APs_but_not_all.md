---
title: "Wireless Connects to Some APs but not all"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by zboot on 2009-08-06
I had xubuntu running on my machine and had the exact same issue.

Pretty much I've noticed that my wireless connects to some APs but not others. At the moment, I have connected to a secured (WEP) AP and several unsecured ones. The unsecured APs are essentially basic home routers.

The APs I have not been able to connect to have all been unsecured. Two of them is a public wifi service provided by a coffee shop (pretty much the same setup as the unsecured wifi at home) and the other is a university AP - unsecured, but they do redirects based on mac address registration.

I've noticed (based on a casual reading of several threads here) that other people have experienced this problem, though due to only having to connect to one or two APs, their conclusion is that the network manager applet or their drivers are to blame.

I though drivers were the issue, my card is a miniPCI atheros 5008. However, I've used both the default driver as well as ndiswrapper with the same result. I am dual booting windows 7 (and a couple months ago, windows vista (and about a year ago, windows xp)). All of those windows variants had/have no problems with any of the said APs.

My question is what sort of information should I try to collect on the APs that would be useful in determining the cause of the issue.

Also, I've seen stuff about other network managers. Is it possible that the network manager (NM) applet that defaults with Ubuntu may have bugs?

Perhaps there are known issues with the NM that occur with specific types of APs?

---

### Post by zboot on 2009-08-07
So, one thing that I've been doing (which I didn't mention) is spoofing my mac address (both in Windows and GNU/Linux)

I'm spoofing the mac for both the wired and wireless cards. Wired - no problem. Wireless - problem until I revert back to the original.

This is whether I revert by rebooting (and commenting out changes in /etc/network/interfaces) or revert by using ifconfig to change the mac address back to the original.

This is interesting because I had a similar problem in Windows 7 where I was unable to spoof the mac address of a wireless card. My current install of windows 7 and my current wifi card work fine with spoofing now, so I'm unable to investigate it further beyond that.

I will confirm whether the unspoofed wifi works where it was not previously. Now that I'm using ndiswrapper, I think there are other methods for spoofing the card's mac and will try those as well.

---

### Post by zboot on 2009-08-13
I've determined it is a driver issue.

In windows 7, I am using the windows xp atheros driver for my wifi card. If I update to newer vista or windows 7 drivers, I lose the ability to change the mac address. This applies with the latest microsoft or atheros drivers.

Likely there is a similar issue with the linux ones. I'll try ndiswrapper with the xp drivers and see if that solves the problem.

---


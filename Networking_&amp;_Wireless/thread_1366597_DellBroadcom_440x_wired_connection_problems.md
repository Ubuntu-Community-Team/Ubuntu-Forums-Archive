---
title: "Dell/Broadcom 440x wired connection problems"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by HarryvdB on 2009-12-28
Recently I installed Kubuntu 8.04 on a Dell Dimension 2400 desktop, dual booting with WinXP. This computer, and two other non-Dells that also run Kubuntu 8.04, access the 'net through the same wired router.

But, I can't get the Dell to access the 'net for more than a short period of time (less than 1 minute) after a reboot, and sometimes not at all under Kubuntu. However, it connects normally under WinXP. Apparently the hardware is functioning properly.

I tried a different distro (Xubuntu 8.10) with the same results, so I assume this is a Linux/Dell/Broadcom software issue.

Any help would be most appreciated,
Harry

---

### Post by lexfridman on 2010-02-08
Hey, have you found a solution to this problem?

I have the exact same problem. I tried other Linux OS's and it's the same. However, things are working perfectly on Linux.

---

### Post by HarryvdB on 2010-02-08
> **lexfridman said:**
> Hey, have you found a solution to this problem?

I have the exact same problem. I tried other Linux OS's and it's the same. 
I have given up for the moment because no one here seems to be able to help. Consequently, that computer continues to operate under Windows, much to my chagrin.

> However, things are working perfectly on Linux.I'm not sure I understand. You just wrote you have the same problem, which I assume means you were able to successfully install Linux on a Dell, but can't access the Internet because of problems communicating with the NIC.

And now you write, "... things are working perfectly on Linux." Do you mean everything else works  properly, except for accessing a network through the NIC?

Harry

---

### Post by lexfridman on 2010-02-09
Hey Harry,

Sorry, I meant to say everything is working perfectly on WINDOWS just like in your case.

All Linux OS's I tried (OpenSUSE, Ubuntu, Fedora, Knopixx) have the same problem, which is very strange since I haven't always had this problem. It just came up in the last month.

I'll keep trying to figure it out. Let me know if you get any leads.

---

### Post by HarryvdB on 2010-02-24
> **lexfridman said:**
> Hey, have you found a solution to this problem? 
I installed an old PCI NIC, disabled the onboard one, and booted the computer. Kubuntu found the card and configured it without me having to do anything.

It now works like it should both in Windows as well as Linux.

Harry

---


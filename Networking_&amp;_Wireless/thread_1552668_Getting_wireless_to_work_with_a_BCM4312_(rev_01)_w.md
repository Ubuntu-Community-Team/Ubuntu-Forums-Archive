---
title: "Getting wireless to work with a BCM4312 (rev 01) wireless adapter."
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by IYellalot on 2010-08-13
Hi, I'm new to linux, and I just installed Ubuntu on my laptop. Problem is, I can't seem to get the internet to work. I have a Broadcom Corporation BCM4312 (rev 01) wireless adapter, and I can't connect with it. I *do* have ndiswrapper, I just don't know what to do with it.

Does anyone have a solution that doesn't require an existing net connection?

---

### Post by snowpine on 2010-08-14
There are some good instructions on the Ubuntu wiki, including what to do if you can't use a wired connection.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by IYellalot on 2010-08-14
I tried that, but now whenever I click on the wireless icon, it doesn't show the option to connect to a wireless network.

---

### Post by snowpine on 2010-08-14
> **IYellalot said:**
> I tried that

What is "that"? 

Please be specific about what you have tried, copy & paste the output of the terminal commands so we can help you.

---

### Post by IYellalot on 2010-08-14
> **snowpine said:**
> What is "that"? 

Please be specific about what you have tried, copy & paste the output of the terminal commands so we can help you.

Well, I installed the bcmwl-kernel-source package, and I followed the instructions for installing the BCM43xx drivers, but I can't copy an and paste my terminal because I'm on a diferent computer from the one I'm using Ubuntu on.

...Did I mention that I'm totally a n00b when it comes to Linux? I really don't have any idea what I'm doing...

---

### Post by snowpine on 2010-08-14
> **IYellalot said:**
> Well, I installed the bcmwl-kernel-source package, and I followed the instructions for installing the BCM43xx drivers...

That's probably the issue right there; the drivers are an either/or proposition... You should install *either* b43/sta (wl) or b43, but not both.

Try:

```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
```

Does that work?

---

### Post by IYellalot on 2010-08-14
When I try that, it says "FATAL: Module wl not found."

---

### Post by snowpine on 2010-08-14
> **IYellalot said:**
> When I try that, it says "FATAL: Module wl not found."

This suggests bcmwl-kernel-source was not successfully installed.

---

### Post by JBAlaska on 2010-08-14
> **IYellalot said:**
> Hi, I'm new to linux, and I just installed Ubuntu on my laptop. Problem is, I can't seem to get the internet to work. I have a Broadcom Corporation BCM4312 (rev 01) wireless adapter, and I can't connect with it. I *do* have ndiswrapper, I just don't know what to do with it.

**Does anyone have a solution that doesn't require an existing net connection?**

Put the LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a term and do:

Code:
```
sudo apt-get update
```

Then:

Code:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the STA driver. in System, Administration, Hardware Drivers

---

### Post by IYellalot on 2010-08-14
> **JBAlaska said:**
> Put the LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a term and do:

Code:
```
sudo apt-get update
```Then:

Code:
```
sudo apt-get install bcmwl-kernel-source
```Now reboot and select the STA driver. in System, Administration, Hardware Drivers

Alright, that worked! I'm online now.

---


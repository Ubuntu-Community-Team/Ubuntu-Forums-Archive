---
title: "HP Pavillion dv2419us with Ubuntu only; no wireless detection"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by prettynerdygirl on 2010-03-06
I've tried it all so please don't direct me unless it's specifically for my model and with ridiculously easy directions, please.

I've got an HP Pavillion dv2419us laptop. I had Windows 7 Beta on it originally, but the trial went out. The cheaper alternative being Ubuntu.  Everything went smooth on the install (no partitioning), but I don't get a wireless icon, let alone a wireless signal.  I've tried it all. Downloading the Broadcom STA Wireless driver, downloading the B43 driver, script after script, and I don't get anything.  I finially tried going into the Hardware Drivers. The first few times I did this, there was nothing in the list. After the updates, all of my drivers showed up for installation.  The NVIDIA graphics card installed with no problem. Went for the Broadcom driver and the kernal freaked out with the Caps and Scroll lock lights blinking.  I did a manual shut down and powered it back up with no errors or issues.  Went back to the drivers and tried broadcom again. Now I get this message: 
> Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

If only I knew where that was located and if it would even help me at all...

I've only had Ubuntu installed on my computer for 3 days, no joke. Installed it Thursday night and I've been only working on getting the wireless to work.  I'm trying to start an online business with only a few weeks till launch and I have no computer to work with. Your help is appreciated.  Please be kinda and go easy on me. I'm new at this and I even bought the textbook, but nothing's helping.  I'm available to provide any information needed to solve this issue.

---

### Post by lidex on 2010-03-06
Go to your main menu "Applications>System>Administration>Log File Viewer". You'll be able to see jockey log with that.

What is the terminal output of this command:
```
sudo lshw -C network
```
Please post it here using code tags. Find a terminal: "Applications>Accessories>Terminal". Enter your user password where prompted.

If you could post this as well (terminal command):
```
uname -a
```

---

### Post by lidex on 2010-03-06
I have Dv7 but didn't have wireless issues so not my area of expertise. I have tried to condense info specific to HP notebooks and these are two links I find useful. I will help you where I can:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing]("http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html#installing")
Never mind the second one-for audio only.

---


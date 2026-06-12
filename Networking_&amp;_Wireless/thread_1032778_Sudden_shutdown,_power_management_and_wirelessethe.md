---
title: "Sudden shutdown, power management and wireless/ethernet driver headache of DOOM"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by solomonhomicz on 2009-01-06
I've been running 8.04 in Vbox for awhile now, worked fine, so I dual-booted with XP and it seemed to work fine, but I had no dial-up, after some hairpulling I installed sl-modem-daemon, which only works if I execute a restart command, then I started getting sudden shutdown problems.

I decided to hit a wifi spot and download all the updates before troubleshooting. Major headache, network manager showed available networks, but no connect. Suddenly I obtained connection after a reboot I went to install wifi-radar when I opened it checked for package dependcies, obtained a connection and started downloading. Thought everything was cool, didn't have time to finish downloading as I'd spent hours getting wifi connection.

I returned to the wifi today I started up with the wifi switch on, checked the wifi radar had a connection. Started updating went well at first left for an hour came back the connection speed was way down. Checked the wifi radar there was another network right next door with a much stronger signal, so I got brave and hit disconnect, then attempted to connect to the other network, no luck tried to switch back no luck, so I tried a restart. Tried to connect three times could not acquire an ip address then sudden shutdown, restart, network manager had the "!" icon opened it no wireless, checked my hardware drivers to make sure they were srill enabled the atheros wireless and ethernet drivers both clean gone,then sudden shutdown, restart, one minute, sudden shutdown - noticed charge light switched to amber indicating battery charging right before shutdown then immediately back to green (AC power-fullcharge-what it should be)after shutdown.

Went home started up went to hit dial up connection, sudden shutdown repeatedly five times no longer than a minute after logon. The power light switches to amber EVERYTIME, a second or two before shutdown then back to green.

I'm an engineering student and I use gfortran and qcad quite extensively, if I can't get these issues resolved before school starts I'll just have to go back to Vbox and sacrifice 3d acceleration.

My computer: Toshiba Satellite M35X-S149, intel celeron m 1.5ghz, 1g RAM, Atheros wifi

---

### Post by dmizer on 2009-01-07
I had this problem with my Atheros card early on in Hardy, but it is no longer a problem. Get the updates, and you should be okay after that. If not, try different drivers (ie. NDISwrapper).

Output lshw would be helpful:
```
lshw -C network
```

Also try booting with "pci=routeirq" added to your kernel boot line.

P.S.
Please do not create duplicate threads and cross post. This makes it impossible to follow troubleshooting, and actually creates more work for both you and the people trying to help you.

Also, since this is a networking issue, I am moving this thread to the networking and wireless section. ;)

---

### Post by solomonhomicz on 2009-01-07
I used sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5ubuntu4_i386.deb to get my modem working, this is after I had already installed SLMODEMD.gcc4.2.tar.
After this was the first time I experienced sudden shutdown, is it possible I set up a driver conflict?
As of right now ubuntu will only run about a minute after the logon screen first appears, not much time to do anything. It wasn't this bad until I stopped it in the middle of updating. I'm going to do reinstall, get the dialup working and wait to update until I can procure a high speed connection and do a complete update.
Any reccomendations on a clean first time wifi connection?
Toshiba M35X, Atheros AR5004G

---

### Post by iSKUNK! on 2009-11-11
> **solomonhomicz said:**
> sudden shutdown repeatedly five times no longer than a minute after logon.

Try upgrading the BIOS. The M35X shipped with a buggy ACPI implementation, causing the sudden-shutdown behavior and a lot of other power-related issues. See [this bug report](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242400) for more details.

---


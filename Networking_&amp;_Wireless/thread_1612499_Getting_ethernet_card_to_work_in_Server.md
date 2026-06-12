---
title: "Getting ethernet card to work in Server"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2010-11-03
Hey guys, I've got one of those atom motherboards with a realtek gigabit card on it and I can't get it to work.

This computer doesn't have a cdrom on it, so I installed Ubuntu server to the hard drive from another machine and swapped the hard drive back to my little atom computer.

Everything works but the ethernet card.

I'm not extraordinarily savvy on networking in the command line but here is what I did try.

Tried to configure the /etc/network/interfaces file.  lo was the only thing that was there so I added

auto eth0
iface eth0 inet dhcp


That didn't work.  when I restarted the network it just said unknown device.

So I did an lspci | grep Ethernet and found the hardware.  Then, I did a modprobe r8169.

Didn't work either.

I've restarted the computer a few times and really didn't get anywhere.  I could just set it up so that I could reinstall Ubuntu, but then I wouldn't learn anything would I? :)

I'm not sure if maybe I did the modprobe wrong or I'm just missing some step.  

Thanks.

---

### Post by chili555 on 2010-11-03
You probably need:```
**sudo** modprobe r8169
```You can see what's going wrong with:```
dmesg | grep -e 8169 -e eth0
```

---

### Post by pepsifx357 on 2010-11-03
> **chili555 said:**
> You probably need:```
**sudo** modprobe r8169
```You can see what's going wrong with:```
dmesg | grep -e 8169 -e eth0
```

Thank you, dmesg did the trick.  It told me that the eth0 got renamed to eth1, so I went and changed the interfaces file to reflect that. Restarted the network and dhcp got its IP.  SWEET!

Did it rename it because I manually entered an auto eth0 before using modprobe?

Also what is dmesg and what does it do?

---

### Post by chili555 on 2010-11-03
SWEET indeed! I'm glad it's working.

I don't know why it got changed; sometimes it's changed when a NIC card is changed. It can manually be changed back, but if it's working fine now, why mess with success. 

dmesg logs a somewhat limited list of kernel messages. It starts fresh every time you boot, although older logs are kept for four more boots. The file /var/log/syslog is more complete. 

You can pipe the file through grep to search for problems; for example:```
dmesg | grep -i acpi
```The -i switch makes grep search for ACPI and acpi, etc. You therefor see:> [   19.182673] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_[COLOR="Red"]acpi[/COLOR]/input/input6
[   19.205375] radeon 0000:01:00.0: power state changed by [COLOR="Red"]ACPI[/COLOR] to D0When you have a problem, it's often helpful to search for errors or warnings:```
dmesg | grep -i warn
dmesg | grep -i error
```

---

### Post by pepsifx357 on 2010-11-03
When searching for a problem do most people just run /var/log/syslog, dmesg or does it just depend?

---

### Post by chili555 on 2010-11-03
I am probably not like most people. I grep dmesg and if the answer is there, I try to solve it. If I read the relevant parts of dmesg and wish I could know more, I move on to syslog.

There are a variety of logs kept; please check:```
ls /var/log
```Access to these logs is for privileged users only, so do:```
**sudo** cat /var/log/syslog | grep yourproblem
```

---

### Post by pepsifx357 on 2010-11-03
Thanks!

---


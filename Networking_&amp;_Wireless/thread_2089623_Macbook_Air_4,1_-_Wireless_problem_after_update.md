---
title: "Macbook Air 4,1 - Wireless problem after update"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by cryptoparrot on 2012-11-29
Hi everyone,

I'e had my Macbook Air dual booted with Ubuntu for a few months now and it's always worked pretty much flawlessly out of the box. I made a few recommended tweaks after the install RE power saving. 

I booted into my Ubuntu partition today for the first time in a month or so. I ran my updates and after the restart my Wireless has crapped out. It's not showing anymore as a network interface when I run ifconfig. 

I'm guessing that some of the updates somewhere messed up the proprietary Broadcom driver I had installed. In the software updates GUI I could see the checkbox for the Broadcom proprietary driver was still selected, indicating it should be used. 

I followed the instructions in here: [http://www.intervigil.net/ubuntu-on-the-macbook-air-41](http://www.intervigil.net/ubuntu-on-the-macbook-air-41) to try and re-install my driver from the tar. 

When I ran the make command in the terminal I get this error: 
make: *** /lib/modules/"release"/build: No such file or directory. Stop.

Then I tried to grab the packages necessary for compiling the driver: 

# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

I wasn't hopeful without a network connection and my hunch was right, it won't work. 

Is there any way I can fix this without having a network connection? I really don't have to want to re-install my Ubuntu partition yet again. I don't suppose there's any way to roll back the packages that I updated, I can see the changes list in Software Updates but I have no idea which package killed my Wireless card. 

Any ideas? 

Thanks for reading.

---

### Post by astemark on 2013-03-17
Hello.

I have pretty much the same problem. Installed Ubuntu 12.10 on my new MacBook Air 11". Everything worked fine until I installed updates. Wifi is now dead. What should I do?

/a

---

### Post by Hadaka on 2013-03-17
Hi,please post the following..

```
rfkill list all
lsmod
lspci -nn | egrep '0200|0280'
```
thanks

---

### Post by cryptoparrot on 2013-03-19
This command fixed it for me: sudo modprobe brcmsmac  (I had a reply at another forum I frequent). 

A permanent fix was to create a file in /etc/modprobe.d/ and add brcmsmac to it. I called it brcmsmac.conf but I don't think the name matters.

---

### Post by Hadaka on 2013-03-19
Great ! glad you got it working...
please use thread tools and mark
this SOLVED
thanks.

---


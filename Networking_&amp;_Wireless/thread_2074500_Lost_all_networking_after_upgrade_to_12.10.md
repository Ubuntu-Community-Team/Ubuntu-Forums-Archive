---
title: "Lost all networking after upgrade to 12.10"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by KFwLsKvVAs on 2012-10-21
Hello,

I upgraded from 12.04 to 12.10 yesterday or the day before.  I assumed that there would be some hiccups since it's such a new release, but I did not expect to completely lose my ability to get online.  

Immediately after I upgraded, I was connecting to a wireless network, and things worked fine.  I don't know what the state of the wired connection was at the time since I wasn't using it.  When I got home and tried connecting to a wired connection, I noticed that there was no option for a wired connection and nothing happened when the cable was plugged in.  A simple problem, I thought, one which has happened quite a few times in the past: somehow my wired driver was lost and I had to go through the process of entering into the compat-wireless (the specific driver for my card, which I had downloaded once initially to get my connection working) folder, make, sudo make install, sudo modprobe alx, afterwards I had expected my wired connection to function properly.  

Well things did not work as expected.  When running sudo modprobe alx, I got some error message like module not found, or something (I'm on my Win8 partition, so I don't know exactly what the error was).  I decided to reboot, thinking it must have been some intermittent problem and that maybe after a reboot I would be able to sudo modprobe alx and things would be good.  Unfortunately, that was not the case.  After a reboot, sudo modprobe alx still failed, and my wireless connection stopped functioning also.  sudo modprobe eth0, eth1, and wlan0 all returned with the same module not found or no module exists or something error.  

And so here I am, frustratingly posting this from my Win8 partition, hoping and praying that somebody will be able to help me get this sorted out.  I can run any commands and get the results of any commands, but it'll take me a little while since I need to reboot between every post/response.  My wired network card is an Atheros 8161 I believe, and it worked correctly up until the upgrade (with the exception of occasionally losing the driver, thus making me go through the aforementioned process of make, sudo make install, sudo modprobe alx to get it working again).  I don't recall of the top of my head what kind of wireless card I have.  If need be I can boot into Ubuntu and post the results of lspci, but since I'll have to reboot I was hoping to get a list of commands to run to be efficient.  

Thanks in advance.

---

### Post by KFwLsKvVAs on 2012-10-21
I have a separate partition which I am going to do a fresh install of 12.10 on shortly to see if I can get any network connections to work on that, but I would really like to fix my current install rather than migrate everything over to a new one.

---

### Post by KFwLsKvVAs on 2012-10-21
Posting this from my fresh 12.10 install.  After installation, I followed these steps to get my wired connection working:
```
sudo apt-get install linux-headers-generic build-essential
wget http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.5/compat-wireless-3.5.1-1-snpc.tar.bz2
tar -xf compat-wireless-3.5.1-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```

props to chilli555 for the original answer in [this thread]("http://ubuntuforums.org/showthread.php?t=2050126")

So now the question still is, what can I do to restore my network connections on my other Ubuntu partition?

---

### Post by KFwLsKvVAs on 2012-10-23
Still need help restoring networking on my other partition.  Anybody?

---


---
title: "Lucid: Accessing samba shares incredibly slow from Win7"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2010-05-16
Since "upgrading" (ha!) to lucid I have had a number of problems that I am working my way through. 

The latest is accessing samba shares from a Win7 PC. It takes minutes to open the requested share from the Windows 7 PC. File transfers, once the directory is accessed, can be measured in bytes. It is an absolute trickle. 

AFAIK the smb.conf is unchanged and, in any case, there is no problem accessing the shares from another linux PC.

Any ideas that might help save my sanity?

Cheers

---

### Post by Zathuras on 2010-05-16
Having similar problem.  Definitely noticing it now in 10.04 where I didnt have the problem in 9.10.

Windows 7 64bit client sends/receives at around 1MB/s (anywhere from 1 to 1.2) to a Ubuntu 10.04 Linux server (64bit) running smbd.  Same configuration appeared to work for much higher transfers under 9.10.

Some notes:
- Both have realtek RTL8111/8168B PCIe gigabit (on-board) and are attached to a Netgear gigabit switch (GS108.)  

- I've installed the kernel module built from realtek's software release on the Linux server and that didn't help.  see:
 [http://art.ubuntuforums.org/showthread.php?t=1022411]("http://art.ubuntuforums.org/showthread.php?t=1022411")

- Both seem to be able to independently connect to the internet just fine and can download at much higher rates.

- I carried over the samba configuration file from 9.10 to 10.04 thinking that it shouldn't change.  Then I noticed the problem and started tweaking, but nothing helped.

- I had changed out my server hardware a few months before the upgrade and hadn't noticed a difference in the share, but there is a very *small* chance that the problem was pre-existing under 9.10.

In any case, I've also posted about this on this thread:

[http://art.ubuntuforums.org/showthread.php?p=8363178]("http://art.ubuntuforums.org/showthread.php?p=8363178")

---

### Post by GuiGuy on 2010-05-16
> **Zathuras said:**
> Having similar problem.  Definitely noticing it now in 10.04 where I didnt have the problem in 9.10.


Many thanks. 

I think I'll move the system back to Karmic.

---

### Post by GuiGuy on 2010-05-16
To eliminate any cabling issues I tried a wireless connection. Exactly the same performance issues despite wireless monitoring at both ends reporting good signal levels. 

Have also tried alternative router and cabling. No good.

I'm pretty much convinced the problem has been brought on by Lucid.

---

### Post by GuiGuy on 2010-05-17
> **GuiGuy said:**
> 
I think I'll move the system back to Karmic.

Done! Network performance is back to where it should be.

---

### Post by Zathuras on 2010-05-17
Hmm may have to downgrade myself.  Thats sad.  Is there anyway to do it in place without digging up a cd?

I tested out Ubuntu 10.04 64-bit as a client (same machine as my windows 7 64-bit but running my linux installation instead) with the same slow down.  

I also tested a laptop running Ubuntu 10.04 64-bit with a Intel wireless device (forgot the exact hardware and I'm not anywhere near it right now to get that information) connected through a netgear wireless access point at 54Mbit to the netgear switch and it also had similar problems.  The speed was actually slightly faster at around 1.5MB/s over wireless than it was over GigE...

---

### Post by dtfinch on 2010-05-17
Downloading large files from my Lucid desktop to my Windows 7 laptop over wireless, I had my transfer rate jump from 200kb/s to 2mb/s when I turned off Microsoft Security Essentials' realtime protection on the laptop.

---

### Post by gladroger on 2010-05-18
I have the exact same problem, Samba worked perfectly under Karmic. Now the speed are very slow (1-2 mb/s)

My system is a Asus P5N9300 Barebone with integrated Realtek 8111/8168 gigabyte adapter.

I have tried to install the latest driver from Realtek for linux but it didnt help.

---

### Post by Zathuras on 2010-05-18
Anyone know if there is a open bug on 10.04 on this?  I've not had any luck finding anything ( but I haven't searched that hard either.)

---

### Post by gladroger on 2010-05-24
The same problem is also discussed this thread: [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by CapedCrusader on 2010-05-26
Same problem with XP. 

However, what i noticed was that it had worked OK before I installed all the upgrades from update manager. I was able to play a movie from the Ubuntu computer on XP computer (wifi) without freezes. Maybe it was just momentary...

If anyone has a fresh install before updates, you can try. If this was so, that would mean one of the updates is responsible.

---

### Post by Zathuras on 2010-05-31
I resolved my issue.  I'm embarrased to say it was not an Ubuntu or Linux issue and I should have caught it sooner.  Turns out the Realtek network interface on my non-samba machine has become flaky.  First time I've run into the situation where it fails to negotiate connections at 1Gps and falls back to 10Mbs.  I've replaced the on-board Realtek NIC with a PCI-E x1 Intel NIC and everything is much better.  

So my samba server is running great on 10.04 with a Realtek 8111/8168 using the default 10.04 driver.  Considering the bad luck with the other Realtek NIC, I might just replace it preemptively with an Intel NIC too.

---

### Post by GuiGuy on 2010-05-31
> **Zathuras said:**
> I resolved my issue.  I'm embarrased to say it was not an Ubuntu or Linux issue and I should have caught it sooner.  Turns out the Realtek network interface on my non-samba machine has become flaky.  First time I've run into the situation where it fails to negotiate connections at 1Gps and falls back to 10Mbs.  I've replaced the on-board Realtek NIC with a PCI-E x1 Intel NIC and everything is much better.  

So my samba server is running great on 10.04 with a Realtek 8111/8168 using the default 10.04 driver.  Considering the bad luck with the other Realtek NIC, I might just replace it preemptively with an Intel NIC too.

hmmmm... I have a similar controller onboard. It works fine with Karmic. It misbehaves under Lucid. 

But seeing your post, out of curiosity I plugged in another NIC, disabled the onboard Realtek and re-booted into Lucid. 

Guess what? It Works! 

Lucid problem?

---

### Post by SuperCurro on 2010-11-29
After one day surfing over internet.... lots of posts read...

First I change the r8169 driver to r8168 driver, nothing solve,so I returned to r8169.

Reading more and more I found in this link: [http://www.linuxforums.org/forum/networking/136486-gigabit-network-slow-samba-ftp-iperf.html](http://www.linuxforums.org/forum/networking/136486-gigabit-network-slow-samba-ftp-iperf.html) the solution

Change "socket options =" from samba configuration to

**socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE**


The samba will now run close to 950 kbit/s,

---

### Post by TechZilla on 2011-07-29
I agree with those suggestions,
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE

I would also make sure, log level is <= 2.

I have heard talk about not using the other smb.conf socket options, with a 2.6 or later kernel.

forum posts about samba performance, largely recommended SO_SNDBUF=/SO_RCVBUF=.  Which was true in the past (2.4), but now is strongly discouraged.  2.6 has auto optimizing stack or something of that sort...

---

### Post by Sun_Blood on 2011-08-03
> **TechZilla said:**
> I agree with those suggestions,
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE

I would also make sure, log level is <= 2.

I have heard talk about not using the other smb.conf socket options, with a 2.6 or later kernel.

forum posts about samba performance, largely recommended SO_SNDBUF=/SO_RCVBUF=.  Which was true in the past (2.4), but now is strongly discouraged.  2.6 has auto optimizing stack or something of that sort...

That is true. Forcing SO_SNDBUF=/SO_RCVBUF is not going to help in a modern kernel.

At the moment with a fully updated Ubuntu I score about 20MB/sec when transferring. 
This is not good but could go better. Actually when the transfear starts it's up at 90MB/sec but will soon drop to 20. But I think that is cache to cache rates.

---


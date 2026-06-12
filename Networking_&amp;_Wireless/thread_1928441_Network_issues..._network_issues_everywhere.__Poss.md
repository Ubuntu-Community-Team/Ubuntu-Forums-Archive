---
title: "Network issues... network issues everywhere. / Possibly RTL8111 issue."
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by XaTiOn on 2012-02-20
Hello.

I'm having some issues with Ubuntu. I'm posting as a last resort. 

My issue (I believe): I have a RTL8111/8168B Pci Express Gigabit Ethernet Controller.

The first night: Was installing all my updates, attaching accounts to Ubuntu, etc. Internet cuts out at about 12-1am. Spend til 4:30 trying to fix.

Next day: I re-install, after complications with re-installing, after 8 tries it finally worked. 

Today: Worked fine, I noticed that there were issues with Realtek cards during my 8-install run, so I thought "Ugh, I should have just googled first". Okay, so now the problem: I can't connect again. This was triggered as I was on the internet at precisely 1am my internet cut off. This cut off of TeamSpeak, Skype, etc. Everything. No web pages avaliable. Same thing that happened in the first place.

Above is what makes me believe it is RTL8111.

Okay, I can do this. I follow many guides, do everything they say, reboot accordingly, and nothing works. I download the latest drivers from Realtek, r8680-8.028.0, replace the variable names (from outdated guides that were using 17 and so on) and everything eventually falls in to place.

I do a diagnostic command (this is what I'm calling it because it's 3:23AM at time of writing, and the name escapes me) and the driver says it's using r8168, not r8189. I have r8189 blacklisted on blacklist.conf, blacklist-oss.conf, and so on. 

```
sudo lshw -C network
```outputs:

```
network UNCLAIMED
desc: ethernet controller
product RTL8111/8168
vendor Realtek
physical id: 0
bus info: pci@0000:06:00.0
version: 02
width 64 bits
clock 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list
config latency=0
resources ioport:e800(size-256) memory fbeff000-fbeffff memory f6ef0000-f6efffff memory:fbec0000-
```NOW: When I go up in the top right, there are "no network devices avaliable"

BEFORE: I was able to get "Connection", but when a browser - or anything - tried to load, "Waiting for server" was my best friend in chromium. 

System Settings > Network > also used to display something about current connection, but now it's limited to only VPN. Not sure if this helps.


```
Specs: 64-bit Ubuntu 11.10 (Latest one, just installed 3 days ago)
3.0.0-16-generic x86_64
12GB DDR3 Ram
3 Harddrives, Ubuntu is installed on its own.
GTX460

``````

Ifconfig: link encap: local loopback
inet addr: 127.0.0.1 mask 255.0.0.0
inet6addr: ::1/128 scope:host
UP LOOPBCAK RUNNING MTU 16436 Metric: 1
RX packets 1136 errors 0 dropped 0 overruns 0 frame 0
tx packets:1136 errors:0 dropped 0 overruns 0 carrier0
collisions: 0 txqueuelen:0
rx bytes:89728 tx bytes 89728
```Also, networking works fine when I go back to my Win7 64-bit.

To add to that: every other computer on my network works. I'm on a linksys router, with a switch leading to my computer.

I'm sorry if I'm lacking certain information, please let me know if you need more. 

Thank you guys for your help. If this doesn't work, and you cannot answer my questions, should I re-install (again),  / buy a new network card?

---

### Post by gordintoronto on 2012-02-20
Sorry you have had such a tale of woe. However, I'm having trouble following your story. Everything before the most recent install is irrelevant and just confuses me. I can't figure out what you have done since that install, or what your current status is.

The command lspci will identify your Ethernet controller. When I run lshw, part of the output is "RTL8111/8168B" but the "B" didn't appear in your results. Did you use copy/paste to post your result? (I've never used the wired ethernet controller on this computer, only wireless.)

Did you blacklist the bad driver?

---

### Post by dandnsmith on 2012-02-20
OP hasn't said which release Ubuntu he's using, but I've had this problem with various releases of Ubuntu, starting with 10.04.

There seems to be a kernel/driver problem with the 'officially correct' setup for RTL8111 (and some others), which results in the network going to sleep and being tricky to wake. The procedure for fixing it has been documented (I've contributed to several threads on this subject), and it involves using an older driver, and configuring this into the initrd file as well.

I recommend a search - the procedure for fixing it has been used on 3 different sets of hardware (by me) and multiple releases of Ubuntu and Mint with success.

---

### Post by ratcheer on 2012-02-20
Have you tried installing the **r8168** driver from Realtek? I had to do that for almost a year, but for some reason, my PC is now working with the standard kernel driver r8169.

Please post the output of "sudo lspci -v" (just the section for the Ethernet card).

Tim

---

### Post by roelforg on 2012-02-20
i was gonna say: "show us /etc/network/interfaces"
Now i'm saying (from my trickbox as i had my cup of network trouble):
When it cuts out, open a terminal, sudo to root (sudo bash) and type this:
```

/etc/init.d/networking restart
ifconfig
ping -c 4 8.8.8.8

```
and post the output of the last 2 commands.
In my exp. restarting my network (1e command) works 60% of the times.

---

### Post by XaTiOn on 2012-02-20
Okay, so now here's where it gets weird... I start up the computer today, after giving it about 10 hours of downtime, networking detects a network, and I'm posting to this thread on it right now.... Maybe the driver blacklisting of r8169 worked? I had restarted it 3 times, and it didn't work then... 

I'm going to give it until tonight, where it usually drops out on me.

To address the responses that you guys have given me: 

> The command lspci will identify your Ethernet controller. When I run lshw, part of the output is "RTL8111/8168B" but the "B" didn't appear in your results. Did you use copy/paste to post your result? (I've never used the wired ethernet controller on this computer, only wireless.) Yes, I'm sorry. I was writing this from my laptop, trying to mirror the text to post on the forum. It does in fact show 8168B. 

OP hasn't said which release Ubuntu he's using, but I've had this problem with various releases of Ubuntu, starting with 10.04.

There seems to be a kernel/driver problem with the 'officially correct' setup for RTL8111 (and some others), which results in the network going to sleep and being tricky to wake. The procedure for fixing it has been documented (I've contributed to several threads on this subject), and it involves using an older driver, and configuring this into the initrd file as well.

> I recommend a search - the procedure for fixing it has been used on 3 different sets of hardware (by me) and multiple releases of Ubuntu and Mint with success. ```
Specs: 64-bit Ubuntu 11.10 (Latest one, just installed 3 days ago)
3.0.0-16-generic x86_64
``` Also, I have tried the guides, which actually might have fixed the issue. 


> Have you tried installing the r8168 driver from Realtek? I had to do that for almost a year, but for some reason, my PC is now working with the standard kernel driver r8169.

Please post the output of "sudo lspci -v" (just the section for the Ethernet card). 

Yes, I used the driver r8168-8.028.00. I followed a guide for an earlier version (r8168-8.017.00 and r8168-8.020.00 I believe) and replaced the names. Here is the output you requested:   ```
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. M3A78-EH Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 69
	I/O ports at e800 [size=256]
	Memory at fbeff000 (64-bit, non-prefetchable) [size=4K]
	Memory at f6ef0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fbec0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=2 Masked-
	Capabilities: [d0] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 03-00-00-00-68-4c-e0-00
	Kernel driver in use: r8168
	Kernel modules: r8168

```

> i was gonna say: "show us /etc/network/interfaces"
Now i'm saying (from my trickbox as i had my cup of network trouble):
When it cuts out, open a terminal, sudo to root (sudo bash) and type this: Thank you, I will keep that in mind if it does cut out again. As of now, it is working, and I hope for it to stay this way. 

Thank you all for your responses, I really appreciate them. I'm so far having better luck with Ubuntu/Linux than I had when I posted a while (about a year ago) with issues. Thanks.

---

### Post by ratcheer on 2012-02-20
Ok, good job getting r8168 installed and in use. That driver has always worked for me. I am puzzled that it is giving you trouble.

The latest version I used was 8.027 dated around 2011-Nov-16. Maybe I could email it to you, if you'd like. The file is only 62 KB.

Tim

---

### Post by XaTiOn on 2012-02-20
If this current one doesn't work, I'll take you up on that. Thank you for the offer.

---

### Post by XaTiOn on 2012-02-21
Soooo... 1am comes a long, and my music  suddenly stops. The card has 'gone to sleep' at precisely this time, three times so far. 

```
john@John-Ubuntu-Desktop:/etc/init.d$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 
john@John-Ubuntu-Desktop:/etc/init.d$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:0d:4c:8e  
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:8cff:fe0d:4c8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:826382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:591524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:505677185 (505.6 MB)  TX bytes:57047142 (57.0 MB)
          Interrupt:69 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3596 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114087 (114.0 KB)  TX bytes:114087 (114.0 KB)

john@John-Ubuntu-Desktop:/etc/init.d$ ping -c 4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3024ms

```

This time I copy and pasted from the other computer via USB stick text file. Now that I know it's not me, or anything I installed, it's kind of a hilarious matter. My network card is my bed time?

Any ideas?

---

### Post by chris.olive on 2012-05-07
Hi all
Same problem.
Couple of months ago I bought a new laptop HP  DV6  i3 6gb after a lot of try's I managed to get Ubuntu 12.04 up and running, however since doing so the ethernet cut in and out randomly, wireless is fine, this does not happen with win 7.
The problem seems to be, it connects then after a few minutes the connection is dropped network then try's to connect, succeeds then it all starts again.
Same card RTL 8111.
Any ideas.

---

### Post by chris.olive on 2012-05-12
> **chris.olive said:**
> Hi all
Same problem.
Couple of months ago I bought a new laptop HP  DV6  i3 6gb after a lot of try's I managed to get Ubuntu 12.04 up and running, however since doing so the ethernet cut in and out randomly, wireless is fine, this does not happen with win 7.
The problem seems to be, it connects then after a few minutes the connection is dropped network then try's to connect, succeeds then it all starts again.
Same card RTL 8111.
Any ideas.

For some reason this has now sorted itself out after the last set of updates.
Q; Why is synaptic packafe manager missing on 12.04?

---

### Post by MIJ-VI on 2012-05-26
> **chris.olive said:**
> For some reason this has now sorted itself out after the last set of updates.
Q; _Why is synaptic packafe manager missing on 12.04_?

I don't know, but it can be installed via Ubuntu Software Center.

---


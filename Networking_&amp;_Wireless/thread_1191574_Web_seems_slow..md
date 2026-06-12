---
title: "Web seems slow."
date: 2009-06-19
forum: Networking &amp; Wireless
---

### Post by Dead_$partan on 2009-06-19
Hi All,

Seem to be having a few niggles with this 9.04 install, it takes 15-20+ sec to display any web pages, thats just to bring the page up, then it can take a bit longer to load the contents.  I am unsure if this is a browser issue or a networking/protocol problem.

When playing WoW the latency is usually under 100ms and downloading Ubuntu updates can be 450+Mbps which is kinda normal, even though I have an 8mbps connection.

Are there any tweaks or suggestions anyone could give me to boost things?  It seems to be the same when using my LAN and WiFi

---

### Post by papangul on 2009-06-19
Have you tried pinging any server? If not, then open the terminal and type "ping www.google.com" (without quotes) and see what happens.

Two possible solutions for your problem are:
1. Disable ipv6:
In terminal type> sudo gedit /etc/modprobe.d/blacklistand add 'blacklist ipv6' to the end of the file.

2. Set opendns as your dns server:
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by Dead_$partan on 2009-06-21
Can I just check something, I done the blacklist command but I was assuming the file would already exist as you said to add the ipv6 to the end of the file but there is no file of that name on my system, would this be ok?

---

### Post by kharntiitar on 2009-06-21
> **Dead_$partan said:**
> Can I just check something, I done the blacklist command but I was assuming the file would already exist as you said to add the ipv6 to the end of the file but there is no file of that name on my system, would this be ok?

```
modprobe -l ipv6
```

will tell u if it is on your system ... (it most likely is)

then just do what was mentioned before ... and to avoid a reboot do:

```
sudo rmmod ipv6
```

---

### Post by Dead_$partan on 2009-06-21
Hmm I put that command in and nothing happend, just brought brought up the username@computername:~$ line again.

---

### Post by Brandon Williams on 2009-06-21
You're probably running Jaunty, which has IPv6 compiled into the kernel and no way to disable it at the kernel level. Before assuming that the problem is IPv6, do a couple of quick checks with tcpdump to verify. 

First, try 'sudo tcpdump -nvvv -i any port 53', surf to a few pages that are loading slowly, and look for the string 'AAAA?' in the output. If you see 'AAAA?' going out without an immediate 'q: AAAA?' coming back, then your system is performing IPv6 lookups before falling back to IPv4, but your DNS server doesn't support IPv6 lookups. There are work-arounds for this, including switching to opendns (as noted above) and disabling IPv6 dns lookups in firefox.

If the first tcpdump hasn't narrowed down the problem already, then try 'sudo tcpdump -i any ip6' and surf to a few different sites that aren't working well for you. Do you see any output from tcpdump? If not, then IPv6 is most likely not your problem. If you do see output, then you might be able to find a work-around, but I'm not immediately aware of one that has been tested and shown to work.

---


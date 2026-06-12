---
title: "After upgrade to 9.04 SSH connections lag randomly"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by Luchador on 2009-05-05
After the upgrade to 9.04 I encounter the following problem:
During remote sessions through SSH the connection lags from time to time e.g. irc-screen or e-mail client stops receiving input for 2-10 seconds. 
I have not encountered any other problems with my wifi and testing irc-client on the local computer I did not notice any lags.

Also web and bittorrent etc. work without any problems.
The computer is old IBM t40p and as I wrote the SSH problems started after the update to 9.04.

---

### Post by ghempton on 2009-05-06
I am encountering the exact same issue. This happens when I ssh into a machine on the same local network. This is driving me crazy. Anyone found a solution to this?

---

### Post by rhcm123 on 2009-05-06
I can also confirm this on 8.10: The connection will magically drop out, just the blinking cursor at the BASH prompt, and when i am just about to close the terminal window, all the junk charecters I typed appear.

I think this is a lag with the keep-alive option in the /etc/ssh/sshd_config file. In case it matters, i am connecting to a headless ubuntu 8.10 1999 desky.

EDIT: This is the line that you should change to no - this is purely a problem with TCP/IP, not SSH:
```
TCPKeepAlive yes
```
It's more of a random thing, but I think this should fix the problem.

---

### Post by ghempton on 2009-05-06
> I think this is a lag with the keep-alive option in the /etc/ssh/sshd_config file. In case it matters, i am connecting to a headless ubuntu 8.10 1999 desky.

I just tried your solution to no avail. I am fairly certain that I did not experience this issue using 8.10 before I upgraded to 9.04.

FYI, I am also connecting to a 9.04 desktop on a local network.

Anyone else getting this? If I connect to the same server using putty on windows, there are no problems.

---

### Post by ghempton on 2009-05-06
Also, one thing I have noticed which is fairly bizarre is that I get a freeze every minute. Right now in my current ssh terminal I get a freeze at :52 and then all of the junk I inputted shows up at around :06 (determined by looking at the gnu screen bar at the bottom).

---

### Post by ghempton on 2009-05-07
After using the system some more, it turns out that it is indeed the whole TCP/IP network stack which feels laggy. When I ping google.com, I get something similar to the following:

```
~$ ping -c 10 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=240 time=87.5 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=240 time=94.3 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=240 time=95.4 ms

[18 second pause]

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=240 time=101 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=240
[...]
--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 23187ms
rtt min/avg/max/mdev = 87.417/91.470/101.691/4.342 ms
```

There is random significant pause in the middle, but there are no last packets. Seems like a driver issue?

I am on a less than a year old thinkpad T61. On my desktop, 9.04's TCP/IP runs smoothly and doesn't experience any issues.

Any ideas?

---

### Post by rhcm123 on 2009-05-07
> **ghempton said:**
> After using the system some more, it turns out that it is indeed the whole TCP/IP network stack which feels laggy. When I ping google.com, I get something similar to the following:

```
~$ ping -c 10 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=1 ttl=240 time=87.5 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=2 ttl=240 time=94.3 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=3 ttl=240 time=95.4 ms

[18 second pause]

64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=240 time=101 ms
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=5 ttl=240
[...]
--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 23187ms
rtt min/avg/max/mdev = 87.417/91.470/101.691/4.342 ms
```

There is random significant pause in the middle, but there are no last packets. Seems like a driver issue?

I am on a less than a year old thinkpad T61. On my desktop, 9.04's TCP/IP runs smoothly and doesn't experience any issues.

Any ideas?

i think it may just be a flaw in TCP, which, when it lags, causes the keep-alive packets to get stuck in the router buffer, which breaks the connection, until they come though again

---

### Post by ghempton on 2009-05-07
Sounds plausible, but I changed the /etc/ssh/sshd_config file to have ```
TCPKeepAlive no
``` appended to the end. Is there anything else I can do?

---

### Post by rhcm123 on 2009-05-07
> **ghempton said:**
> Sounds plausible, but I changed the /etc/ssh/sshd_config file to have ```
TCPKeepAlive no
``` appended to the end. Is there anything else I can do?

Remember to do that both on your server and the client.

Then, run this command:
```
sudo /etc/init.d/ssh restart
```
to see the difference.

No, there is not much, but you could google up some "speeding up TCP packets" - i never let this bother me much, as it usually only happens once every few weeks.

---

### Post by ghempton on 2009-05-07
I will try this, however I think there is something more fundamental going on here than just lag. Since I am accessing a computer on a local network, there shouldn't be any lag in the first place. Also, this issue never occurred for me on 8.10.

---

### Post by neilb4zod on 2009-05-20
I have what I think is the same problem on a fresh 9.04 install.  When I SSH in from another machine on the local network, if I hold down any key, it lags horribly as the letters scroll across the screen.  In my case, the problem was the wireless network driver.  I switched from ath5k to MadWifi, and the problem went away.  In case this might apply to someone else, here are the details...

My system is a desktop that uses a regular PCI card for wireless.  According to lspci, the wireless card's chipset is an Atheros AR2413.  The default driver for that in Ubuntu 9.04 is ath5k.  I went to Hardware Drivers on the System::Administration menu (i.e. the application jockey-gtk), and I activated the alternate Atheros MadWifi driver there.  What that did was add the following line

blacklist ath5k

to the file /etc/modprobe.d/blacklist-ath_pci.conf.  After rebooting, my SSH lag problem went away.

---

### Post by gadget_hacker on 2009-05-20
I am having similar problems, but I am using wired ethernet, not wifi.  I have 9.04 on to laptops.  SSH works fine on one, but not the other.  Synergy also crashes at random intervals.  I'm not sure if there are drivers for my NIC that I can get or if there is another problem.  Does anyone have ideas?

---

### Post by SL666 on 2009-05-26
This SSH freeze also happens to me, sometimes can be incredible frustrating, i also seem to occasionally get a similar (but much reduced) occurrence in firefox.

Upgraded from 8.10 to 9.04.

Connections to non-upgraded systems, (and other OS) 
Non wifi connection.

Seems to be accompanied by a spike in CPU usage thats showing up in the system monitor graph, but not in the process list.

but in a root top command, the high CPU use and pauses seems to coencide with high cpu use by Xorg .

 ```
2775 root      20   0  632m 187m  28m R 82.0 19.2 480:59.29 Xorg 

```

---


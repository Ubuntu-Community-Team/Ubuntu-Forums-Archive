---
title: "RT3090 issue with uploads"
date: 2013-08-28
forum: Networking &amp; Wireless
---

### Post by pkadeel on 2013-08-28
I have been using Ubuntu 12.04 on my laptop with RT3090 wireless chipset for almost 1 year and WiFi was working almost normally (with random occassional disconections).

Recently I installed LinuxMint 15 on this device and found out that I was able to connect using the WiFi and simple website browsing was working normally but when I tried to upload a file, it failed. Upon further checking I found that I can upload only small sized files (around 1KB) and anything bigger than this failed. Further checking revealed that I can not even send bigger emails or attachments, post lengthy forms like posts on a forum etc. I then installed OpenSuse 12.3 on this laptop and found out that the problem remained but the size of files and emails has further shrunk to less than a half KB. After this I downloaded Kubuntu 13.04, Fedora 19 (both KDE & Gnome) and tested those via Live CDs. The problem still remained. Then I tested all the distros via ethernet cable and there was no problem. So I finally concluded that the problem is with WiFi driver in the new kernels.

Now current situation is that I have OpenSuse 12.3 installed on my laptop and I can not use it to upload files, send emails and do other normal work requiring uploads.
I have a live backup Cd of my previous Ubuntu 12.04 which allows me to upload files and send emails etc
I have a live Cd of Kubuntu 13.04 which also does not upload properly.

Although I can reinstall Ubuntu 12.04 on my laptop using the backupI have and work normally but I don't want to do that because eventually I will have to upgrade at some point of time and I do not want to keep learning a new OS which I will have to stop using in future. Instead I will like to resolve this problem now (if I can) and install Kubuntu or some other KDE distro.

The outputs of wireless-script generated in all the above three mentioned environments are attached and I am looking forward to someone who can help me understand how can I solve this problem.

Edit: And before someone asks, currently I am using live backup Cd of Ubuntu 12.04 to send this post. OpenSuse and Kubuntu didn't succeed.

---

### Post by pkadeel on 2013-08-29
I guess chilies don't grow here anymore, but what about the wild :confused:

---

### Post by chili555 on 2013-08-29
I can't speak for the Wild Man, but I usually try to answer if I have a faint idea about what might be going on and, conversely, I generally refrain from answering when I don't! My silence and, I'll bet, Wild Man's silence, is a good example of the latter.

I'll be happy to explore a few things but I am really just feeling around in the dark. I you accept that, let's start feeling around.

I see this:> IPv4 Settings:
    Address:         192.168.2.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.1.1
    DNS:             192.168.2.1Where did the 192.168.1.1 DNS nameserver come from? Do you have a router behind a router? Can you actually ping 192.168.1.1?

NOTE: I will abbreviate as we go along because you seem to be fairly advanced. For example, I assume you know how to ping a gateway.

There is one and only one driver parameter available for rt2800pci; nohwcrypt=Y. Did you try it? Is the behavior the same with and without it?

Are there any clues here when the slowdown occurs?```
tail -f /var/log/syslog
```I'd open that terminal and let it run and provoke a slowdown to see what emerges. You can escape with Ctrl+c.

Are there any unusual settings in the router? QoS? WPS? Etc.? Is it set for N speeds? Is the behavior the same without N speeds?

For the benefit of Wild Man,  praseodym, Varun, Hadaka, et al who may look in, it might be tempting to install backports, but the driver version in backports-3.11-rc3-1 is the same: 2.3.0. In any case, chime in, guys and gals, if you have any suggestions.

---

### Post by pkadeel on 2013-08-29
> **chili555]I'll be happy to explore a few things but I am really just feeling around in the dark. I you accept that, let's start feeling around.[/QUOTE]
I will like to know more about the tools I use.

[QUOTE=chili555]I see this:Where did the 192.168.1.1 DNS nameserver come from? Do you have a router behind a router? Can you actually ping 192.168.1.1?[/QUOTE]
Yes I have two routers. 192.168.1.1 is the ADSL and 192.168.2.1 is the TP-Link WiFi router. Yes I can not only ping 192.168.1.1 but also any location on internet. As I said earlier, there are no issues with uploading of small packets i.e. (below 368 Bytes in Opensuse and 1Kb in kubuntu). Ok well, ping has an option to ping with a certain sized packet let's see, I will test it also and post result in next reply.

From now on we shall drop the opensuse because I have replaced it with kubuntu 12.04 so that I can do my routine work normally. For testing I will use the Live Cd of kubuntu 13.04 which has problem.

[QUOTE=chili555]There is one and only one driver parameter available for rt2800pci said:**
> 
Didn't know about it. I will now try it also but where can I change this parameter?

[QUOTE=chili555]Are there any clues here when the slowdown occurs?```
tail -f /var/log/syslog
```I'd open that terminal and let it run and provoke a slowdown to see what emerges. You can escape with Ctrl+c.
Didn't check that either. Will do it also.

[QUOTE=chili555]Are there any unusual settings in the router? QoS? WPS? Etc.? Is it set for N speeds? Is the behavior the same without N speeds?[/QUOTE]
The wifi router only has "b/g" and I am using "g" setting

[QUOTE=chili555]it might be tempting to install backports, but the driver version in backports-3.11-rc3-1 is the same: 2.3.0[/QUOTE]
I will prefer to do it the harder way if I had to adopt the non-standard methods i.e. making my own driver from the sources instead of using backports. Atleast I will learn something about my tools.

By the way I had already tried the ndiswrapper tool with the windows xp, vista and 7 drivers and have failed to load those. nidswrapper didn't like windows drivers.

---

### Post by pkadeel on 2013-08-29
```
kubuntu@kubuntu:~$ ping -c 3 -s 1024 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 1024(1052) bytes of data.
1032 bytes from 192.168.2.1: icmp_req=1 ttl=64 time=2.44 ms
1032 bytes from 192.168.2.1: icmp_req=2 ttl=64 time=2.08 ms
1032 bytes from 192.168.2.1: icmp_req=3 ttl=64 time=1.70 ms


--- 192.168.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.705/2.079/2.448/0.305 ms


kubuntu@kubuntu:~$ ping -c 3 -s 1024 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 1024(1052) bytes of data.
1032 bytes from 192.168.1.1: icmp_req=1 ttl=63 time=4.68 ms
1032 bytes from 192.168.1.1: icmp_req=2 ttl=63 time=3.47 ms
1032 bytes from 192.168.1.1: icmp_req=3 ttl=63 time=5.72 ms


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 3.471/4.625/5.724/0.923 ms


kubuntu@kubuntu:~$ ping -c 3 -s 2048 192.168.2.1
PING 192.168.2.1 (192.168.2.1) 2048(2076) bytes of data.


--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms 

```
With a packet size of 1024, I was able to ping both routers but with a packet size of 2048 I wasn't even able to reach the wifi router.

```
[FONT=Ubuntu Mono]tail -f /var/log/syslog[/FONT]
```
It was silent. Did'nt show anything when I tried to upload a file and the browser stood at "Uploading 10%"

---

### Post by chili555 on 2013-08-29
> Yes I have two routers. 192.168.1.1 is the ADSL and 192.168.2.1 is the TP-Link WiFi router. I have a similar setup, actually. Also this is slightly off-topic here, my DNS nameservers are set explicitly in the wireless router using namebench. [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)> Didn't know about it. I will now try it also but where can I change this parameter?Temporarily:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y
```If it helps, we can write a conf file and make it permanent.> I will prefer to do it the harder way if I had to adopt the non-standard methods i.e. making my own driver from the sources instead of using backports. Atleast I will learn something about my tools.The most accessible place I know of where the source is available is the aforementioned backports: [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) However, I wouldn't know where to start because, so far, we don't know what's wrong! Let's not change sparkplugs if we have a flat tire.> By the way I had already tried the ndiswrapper tool with the windows xp, vista and 7 drivers and have failed to load those. nidswrapper didn't like windows drivers. ndiswrapper likes Windows XP drivers and occasionally Windows 2000. It seldom likes 64-bit.> With a packet size of 1024, I was able to ping both routers but with a packet size of 2048 I wasn't even able to reach the wifi router.I doubt that wireless will ever pass greater than 1500. DSL will prefer 1492 or less and you can set it in NM; please see attached. Do you have a larger MTU set somewhere?

We need to find out what is happening during the slowdown. You might look here:```
dmesg
```

---

### Post by pkadeel on 2013-08-30
The problem is solved.

I did a tcpdump in both working (12.04) and non-working (13.04) kubuntus and found a message
```
192.168.1.1 > kubuntu.local: ICMP hostXXXX unreachable - need to frag (mtu 1492)
```

Searched the phrase on google and landed on [http://ubuntuforums.org/archive/index.php/t-979821.html](http://ubuntuforums.org/archive/index.php/t-979821.html)
In your last post you also mentioned about setting MTU in NM. As I had done that before without any luck, This time I changed the MTU in the wifi router which solved the problem. 

So if someone comes here looking for an answer to this problem, the answer is;
Set the MTU in router to 1492 and leave MTU in networking manager/connection manager set to "Automatic"

---


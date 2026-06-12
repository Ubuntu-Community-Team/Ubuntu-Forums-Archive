---
title: "Slow, patchy internet connection"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by shodan_uk on 2009-11-24
Hi there,

I've just installed Ubuntu 9.10 on my Toshiba Equium A210 laptop but am having problems with the wireless internet connection. 

The wireless connection itself seems to be OK; I get good signal quality and have no trouble connection.

However, the connection speed I get is substantially slower than the two other Windows computers in my house and indeed, this laptop itself had no problem with connection speed until I installed Ubuntu.

Furthermore, the internet connection occassionally "locks up" altogether and no pages will load at all, although the wireless signal remains strong.

I haven't had the opportunity to try a wired connection yet but will try to do so as soon as possible.

Any help would be much appeciated but please remember I'm a relative novice when it comes to Ubuntu and Linux in general.

Cheers,
Terry

---

### Post by Lord_ on 2009-11-24
Hi Terry,

I'm assuming that the windows machines are also using wireless? If not then this is a BIG factor

I would benchmark them both by pinging your wireless router to see if there is a significant difference. Turn off any applications which could be using the network and run the following on two of the machines at the same time. I dont know what your routers internal IP will be, probably 192.168.1.1 or 192.168.1.254. (you can type route at the Ubuntu command prompt and look for the "default" one.

ping -c 4 {router ip} - Ubuntu box
ping  {router ip}     - Windows box


You can also repeat this with a couple of public hosts. 4.2.2.2 normally works well

ping -c 4 4.2.2.2    - Ubuntu box
ping 4.2.2.2         - Windows box

let me know how you get on with this, hopefully it will start to narrow down the issue.

---

### Post by shodan_uk on 2009-11-24
Hi Lord_

I've now tested the ubuntu machine on a wired connection and got the full speed although I still wasn't convinced by the stability of the connection and it took what seemed like a relatively long time to "kick in" after plugging the ethernet cable in.

Then when I reconnected to the wireless connection, I got full speed... odd.

I've done the ping tests on both machines: a windows laptop wirelessly connected and the ubuntu machine also wirlessly connected 

Here's the output from the ubuntu terminal:

4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.482/1.661/2.087/0.250 ms
terry@terry-laptop:~$ ping -c 4 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=1.98 ms
64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=1.47 ms
64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=1.60 ms
64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=1.60 ms

The output from the ping command on Windows was:

Reply from 192.168.1.254: bytes=32 time=1ms TTL=64
Reply from 192.168.1.254: bytes=32 time=1ms TTL=64
Reply from 192.168.1.254: bytes=32 time=1ms TTL=64
Reply from 192.168.1.254: bytes=32 time=1ms TTL=64

Ping statistics for 192.168.1.254:
Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 1ms, Maximum = 1ms, Average = 1ms

To me it looks like the window machine is quicker but I don't know if 0.98ms is significant or not?

Cheers,
Terry

---

### Post by Lord_ on 2009-11-24
It does look like a good response overall, assumming these tests were done whilst on wireless then ~2ms is very quick. I get about 3ms responses on mine.

I would give it a while and see how things go. One thing which you may want to consider is using wicd as the network manager. I had similar problems to you on an old laptop of mine and it did sort most of it out. It also has the bonus of loading up quicker in the background when you start your machine.

Since you have got the wired connection to fall back on it shouldn't be too risky to install. I've had to compile it before, but i've just checked and it looks like there is a package for it in 9.10.

sudo apt-get install wicd

I would give your current setup a while before trying, but it has been a big help in the past.

---

### Post by shodan_uk on 2009-11-24
About 10 minutes after my last post, the internet "locked up" on my laptop. I'd only been doing normal "web stuff" ie. reading my email (gmail) in Evolution, checking twitter and facebook in gwibber and some normal web browser, nothing out of the ordinary.

After five minutes of not being able to hit any websites or connect to email servers, I disconnected my wireless connection and tried to reconnect which seemed to take ages before ubuntu asked me for my wep key again, which it had previously remembered and has now seemed to have forgotten.

I gave up then and am now on my windows box.

Any more help would be appreciated. This is the 3rd time I've tried out ubuntu and the 3rd time that I've had some sort of networking issue (on the laptop I mention AND on my desktop machine). In the past it's been more of a problem with actual wireless.

Cheers,
Terry

---

### Post by Gunman1982 on 2009-11-24
Are you using n W-Lan? (The fast speed thing >100MB/s)

---

### Post by shodan_uk on 2009-11-24
No, standard wireless.

---

### Post by shodan_uk on 2009-11-25
Have installed wicd and will give that a go for a while and see how I get on.

Cheers,
Terry

---


---
title: "Firefox connects, but others won't"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Jimmy9pints on 2010-12-28
Hi,
[B]
I have a problem. Only Firefox will connect. Thunderbird won't and other programs won't connect.[/B]

------------------------------

Yesterday I was trying to install programs and found Ubuntu Software centre wouldn't do anything. 

I ran 
```
sudo apt-get update
``` and while a few things did update, most didn't. I got a lot of ```
W: Failed to fetch http://cn.archive.ubuntu.com/ubuntu/dists/maverick-updates/m......
```  kind of messages. 

I live in China and connectivity problems are a way of life here. We get around it by using a VPN.  

The VPN I use (Skydur - which I wouldn't recommend to anybody) has a browser plugin. It allows you to browse freely, but other programs are unaffected.

So, I went to System > Preferences > Network Proxy and changed the proxy to that of the VPN. 

Everything went fine and I could update and install all the software I wanted. 

However, today, **I have a problem. Only Firefox will connect. Thunderbird won't connect. **
```
ping google.com
``` returns
```
ping: unknown host google.com

```

I have reverted the settings to what they were. "Direct internet connection" radio button is clicked. 

If I don't login to the VPN, Firefox also won't work. 

If I do login to the VPN, other programs STILL don't work!

I am baffled. 

Any ideas anyone?

Regards,

Jimmy.

---

### Post by Jimmy9pints on 2010-12-28
Additional info: I've now checked other programs too. Empathy won't connect either. 

To make sure it wasn't a DNS problem I did:
```
jimmy@lil-yellow-asus:~$ ping 72.14.207.99
PING 72.14.207.99 (72.14.207.99) 56(84) bytes of data.
^C
--- 72.14.207.99 ping statistics ---
18 packets transmitted, 0 received, 100% packet loss, time 17085ms

jimmy@lil-yellow-asus:~$ ping 216.239.51.104
PING 216.239.51.104 (216.239.51.104) 56(84) bytes of data.
^C
--- 216.239.51.104 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7037ms

```

---

### Post by Jimmy9pints on 2010-12-29
Sorry to keep asking, but is there anybody who can help?

Quite stuck, and can't connect to some of my email accounts or chat programmes or update my system!

Thanks in advance. 

J

---

### Post by PatchesTheCaveman on 2010-12-29
Firefox isn't set to use a proxy server is it?

Check in Edit > Preferences > Advanced > Network > Connection > Settings.

That is the only thing I can think of that would allow Firefox to connect to the Internet but nothing else.

---


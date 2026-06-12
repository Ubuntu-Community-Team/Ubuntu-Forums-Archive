---
title: "Synaptic through tor"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by gargtarang on 2012-10-05
I am in college and the only way for me to update ubuntu is through Tor. I have configured firefox chromium which was not much of a deal. The real issue for me is Synaptic an apt-get.  Tor only supports Socks5 but Synaptic does not. Please tell me to configure synaptic via tor.
I use Vidalia GUI for Tor and my Ubuntu version is 12.04 precise

---

### Post by albandy on 2012-10-05
You can use proxychains:

sudo apt-get install proxychains

when installed, edit the file /etc/proxychains.conf and search for [ProxyList] entry.

So the file should look like:


[ProxyList]
socks4 127.0.0.1 portnumber


Then you can use synaptic this way:

sudo proxychains synaptic


As I think you can't use apt-get with your configuration, I need to know what version of ubuntu are you using to post the links of each deb package required for this.

---

### Post by gargtarang on 2012-10-05
I am using Ubuntu 12.04 Precise Pangolin.
I want to use Synaptic Package manager and apt-get via socks proxy.

---

### Post by albandy on 2012-10-05
Theese are the packages:
for 32 bit:

[http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/p/proxychains/libproxychains3_3.1-3_i386.deb](http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/p/proxychains/libproxychains3_3.1-3_i386.deb)

[http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/p/proxychains/proxychains_3.1-3_all.deb](http://ubuntu.mirror.cambrium.nl/ubuntu//pool/universe/p/proxychains/proxychains_3.1-3_all.deb)

Download it and in a terminal type:
sudo dpkg -i libproxychains3_3.1-3_i386.deb proxychains_3.1-3_all.deb

---

### Post by gargtarang on 2012-10-12
Thanks. My Synaptic and other applications are working now. :) :)
One more thing, I tried searching about Polipo but could not understand its working. Can you just tell me what exactly is Polipo and how to configure it.?

---


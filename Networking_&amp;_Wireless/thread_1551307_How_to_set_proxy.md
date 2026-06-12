---
title: "How to set proxy"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by ibompotsaris on 2010-08-12
Hello all! Hope someone can help me out with this. So lets get down to bussiness...

I just installed the Lucid server, set IP address, Default gateway and Preferred DNSs and need to be able to use apt-get. Right now this is not possible and my guess is that I have not set the proxy used in my LAN (which is 192.168.255.60:8080) cause I have no clue how to do it.

I can ping every other machine locally but not on the Internet...

Please post details since I am a complete noob. Thank you!

---

### Post by surfer on 2010-08-12
```
sudo nano /etc/apt/apt.conf.d/01proxy
```

inside your new file, add a line that says:

```
Acquire::http::Proxy "http://192.168.255.60:8080";
```

---

### Post by linux-hack on 2010-08-12
This is one way to do'it ... 

The other way is to put the flowing in your **.profile** file or .bashrc if there is one.
```

export http_proxy="http://login:password@proxy.com:3128"

```
and this way to :D

```

sudo echo 'Acquire::http::Proxy "http://proxy.com:3128";' > /etc/apt/apt.conf.d/proxy 

```

---

### Post by pat_bateman on 2010-08-12
Hello,
> This is one way to do'it ...

The other way is to put the flowing in your .profile file or .bashrc if there is one.
export http_proxy="http://login:password@proxy.com:3128"


I like that way more, do not forget to add:
```
export ftp_proxy="ftp://login:password@proxy.com:3128"
```

Also, you can set the proxy from the GNOME GUI.

---

### Post by linux-hack on 2010-08-12
You can do that in **synaptic** too :D by changing the properties.

---

### Post by ibompotsaris on 2010-08-12
> **surfer said:**
> ```
sudo nano /etc/apt/apt.conf.d/01proxy
```inside your new file, add a line that says:

```
Acquire::http::Proxy "http://192.168.255.60:8080";
```


Unfortunately this has not helped. As I understand this is the way to ask aptitude to compensate for proxy, right?

---

### Post by ibompotsaris on 2010-08-12
> **pat_bateman said:**
> Hello,

I like that way more, do not forget to add:
```
export ftp_proxy="ftp://login:password@proxy.com:3128"
```Also, you can set the proxy from the GNOME GUI.

I did forget to add the ftp. I am going to give it a try now.

---

### Post by ibompotsaris on 2010-08-12
By the way, I do not have a GUI... And still I cannot get apt-get to work. I am trying to sudo apt-get install ethtool and still doesn't work.

---

### Post by surfer on 2010-08-12
the line for ftp is:

```
Acquire::ftp::Proxy "ftp://user:pwd@proxy:port";
```

and this is for apt-get, not only for synaptic.

---


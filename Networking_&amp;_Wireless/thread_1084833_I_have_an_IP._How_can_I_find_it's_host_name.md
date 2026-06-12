---
title: "I have an IP. How can I find it's host name?"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-03-02
I have an Ubuntu computer at work that I use for testing various things. On my main work computer, an XP Pro laptop, I have a program known as Angry IP Scanner. When we find an IP that is doing something inappropriate, I scan the IP, find the host name, and the host name naming convention is accurate enough to figure out EXACTLY where the computer is in any of the 8 schools I work for.

But I prefer to use Ubuntu and would like to do this same thing. I have wireshark installed but I have no idea how to use it. Does Ubuntu have any utilities that would do this?

---

### Post by brian_p on 2009-03-02
> **Roasted said:**
> 

But I prefer to use Ubuntu and would like to do this same thing. I have wireshark installed but I have no idea how to use it. Does Ubuntu have any utilities that would do this?

```
man host
```

---

### Post by Roasted on 2009-03-03
Didn't work.

AngryIPScanner picked it up.
"host -6 ip.address.in.here" did not.

---

### Post by Kebabman on 2009-03-03
> **Roasted said:**
> Didn't work.

AngryIPScanner picked it up.
"host -6 ip.address.in.here" did not.

Were there any error messages etc? If so post them and it might be easier to try and troubleshoot the problem. Nice to see your networks are all running IPv6 though.

---

### Post by terazen on 2009-03-03
Tried using dig?
```
dig -x 1.2.3.4
```

Also I think if you did a traceroute or tracepath it would attempt to do the lookup automatically.

---

### Post by terazen on 2009-03-03
I've never used it, but the Angry IP Scanner software has linux binaries on their website.

[http://www.angryziber.com/w/About](http://www.angryziber.com/w/About)...
> Angry IP Scanner is free and open-source software, so use it at your own risk. The license is GPLv2. 

---

### Post by brian_p on 2009-03-03
> **Roasted said:**
> Didn't work.

AngryIPScanner picked it up.
"host -6 ip.address.in.here" did not.

In that case I imagine neither

```
host ip.address.in.here
```

nor

```
host -a ip.address.in.here
```

worked too?

---


---
title: "Issues with Ethereal"
date: 2006-05-17
forum: Networking &amp; Wireless
---

### Post by Kasanax on 2006-05-17
I've used ethereal a couple times before, mostly just to play around (since I don't know that much about networking), and it's always worked in the past.

But recently, when I try and run ethereal as root, I get the following error message:

```
mike@ubuntu:~$ sudo ethereal
Could not set capabilities: Operation not permitted
```

I can't even do things like printing out the version - I get the same error message. If I try to run it as a normal user, it opens fine, except I can't actually capture any packets, since I don't have the proper permissions.

Here's the version information:

```
mike@ubuntu:~$ ethereal -v
ethereal 0.10.12

Compiled with GTK+ 2.8.2, with GLib 2.8.1, with libpcap 0.8.3, with libz 1.2.3,
with libpcre 5.0, without UCD-SNMP or Net-SNMP, with ADNS.

Running with libpcap version 0.8.3 on Linux 2.6.12-mike-4-14-06.

```

I've tried uninstalling and reinstalling, which didn't help. I've also tried installing and running tethereal, but I get the same exact errors. ](*,) 

Any thoughts on what might be going wrong?

---

### Post by Kasanax on 2006-05-18
Another thought - I tried googling the error message, and all I found were:

1) a reference to the problem, but no solution, on the forums at Ethereal's website

2) a page on the Ubuntu SecurityLiveCD, which mentions that ethereal needs to be 'configured' before burning the liveCD. This seems to make sense, but it doesn't explain, and I can't figure out how/what to configure first!

3) A couple of other pages (~4 or 5), in languages which I can't understand.... :-?

---

### Post by jneves on 2006-05-23
You need capability support on your kernel:

```
$ sudo modprobe capability
```

if you want to automate the module loading add:

```
capability
```

to /etc/modules .

Best regards,
João Miguel Neves

---

### Post by Kasanax on 2006-05-23
It worked! Thanks jneves!

---


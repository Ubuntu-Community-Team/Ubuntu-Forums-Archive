---
title: "Access server on host system through virtualbox guest OS"
date: 2012-05-14
forum: Networking &amp; Wireless
---

### Post by jabz on 2012-05-14
Hi everyone, 

I have trouble accessing my local apache server (running in Ubuntu (Host System)) from my Windows XP guest system in virtual box.

**running: **
Ubuntu 11.10. (Host) 
Virtualbox 4.1.2
Windows XP SP3 (Guest)

I need to do some Internet Explorer 7 related CSS workarounds and can not browse files on my localhost on the host system. It seems the server is not even recognized.

So far I have tried all the network adapters for the guest system and made the necessary changes in the Windows host file. None of it worked. 

Does anyone of you have experience with this kind of problem?
Any help is appreciated.

---

### Post by sudodus on 2012-05-14
Can you reach the internet from your guest OS (XP)? In that case you can install the full ssh package and run sshd in your host system, and then log in from XP via ssh or sftp.

If not, you need to reconfigure the network settings in VirtualBox.

---

### Post by roelforg on 2012-05-14
The problem is that you're trying to use localhost on your xp vm to acces your ubuntu host.
It's simple:
localhost always resolves to 127.0.0.1
On your ubuntu host, it causes it to connect to itself.
On the xp vm, it causes xp to try to connect to itself.
Just run:
```

ifconfig

```
on the ubuntu and use the ip that comes after INET ADDR: to access your host from the xp vm.

---

### Post by roelforg on 2012-05-14
> **sudodus said:**
> Can you reach the internet from your guest OS (XP)? In that case you can install the full ssh package and run sshd in your host system, and then log in from XP via ssh or sftp.

If not, you need to reconfigure the network settings in VirtualBox.

He said:
"... but i cannot browse/access my localhost system..."
i assume "localhost system" means the ubuntu host.
Like i explained above, localhost resolves not as he expected.

---

### Post by jabz on 2012-05-15
> **roelforg said:**
> The problem is that you're trying to use localhost on your xp vm to acces your ubuntu host.
It's simple:
localhost always resolves to 127.0.0.1
On your ubuntu host, it causes it to connect to itself.
On the xp vm, it causes xp to try to connect to itself.
Just run:
```

ifconfig

```on the ubuntu and use the ip that comes after INET ADDR: to access your host from the xp vm.

This actually helped a lot. When I connect to inet addr, I can connect to my CMS. My setup is maybe a bit unusual:

domain.dev [CMS]
en.en.domain.dev [English version of the website for UK]
en.us.domain.dev [English version of the website for USA]
...etc.

Roelforg's solution works in the way, that I can get to domain.dev. which is great. But what would I have to do to get to the virtual third- and fourth-level domains? Any ideas? 

Thank you so far. That was a major step.

---

### Post by roelforg on 2012-05-15
> **jabz said:**
> This actually helped a lot. When I connect to inet addr, I can connect to my CMS. My setup is maybe a bit unusual:

domain.dev [CMS]
en.en.domain.dev [English version of the website for UK]
en.us.domain.dev [English version of the website for USA]
...etc.

Roelforg's solution works in the way, that I can get to domain.dev. which is great. But what would I have to do to get to the virtual third- and fourth-level domains? Any ideas? 

Thank you so far. That was a major step.

That's not too hard...
Setup your own dns-server:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
It's a bit old, but still valid. Tell the xp guest to use your ubuntu as it's primary dns (and set the secondary to a working dns like 8.8.8.8)

May i ask what exactly has caused this setup? Do you host some sort of site on your ubuntu and do you want to use the vm to test cross-browser compat?

---

### Post by jabz on 2012-05-15
> **roelforg said:**
> That's not too hard...
Setup your own dns-server:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
It's a bit old, but still valid. 
I believe I have to be careful with this. Looks like this overwrites my hosts file. I will get to work on this immediately.

> **roelforg said:**
> Tell the xp guest to use your ubuntu as it's primary dns (and set the secondary to a working dns like 8.8.8.8)
What would be the IP for the primary DNS entry? Inet addr of my Ubuntu?

> **roelforg said:**
> May i ask what exactly has caused this setup? Do you host some sort of site on your ubuntu and do you want to use the vm to test cross-browser compat?
That is exactly what I am trying to do. I always try not to do IE fixes, but this times I'm forced to do it. :(

---

### Post by roelforg on 2012-05-15
> **jabz said:**
> I believe I have to be careful with this. Looks like this overwrites my hosts file. I will get to work on this immediately.


What would be the IP for the primary DNS entry? Inet addr of my Ubuntu?

May i ask what exactly has caused this setup? Do you host some sort of site on your ubuntu and do you want to use the vm to test cross-browser compat?
That is exactly what I am trying to do. I always try not to do IE fixes, but this times I'm forced to do it. :([/QUOTE]

The INET ADDR is the ip of your ubuntu (i'll refer to it as ubuntu-ip from now on, just so you know that you need to substitute it with the ip of your ubuntu).

Set XP so:
Primary DNS: ubuntu-ip
Secondary DNS: 8.8.8.8

And bind will not overwrite your /etc/hosts (it has no business to do so anyway)
I have one running here myself and it hasen't touched and hosts files.

So you know, this is how your computer would resolve my.pc if it was an entry in hosts (warning: overly simplefied but indicates the point just fine):
```

Is it in hosts? Yes! The ip is ....

```
Or this one for google.com
```

Is it in hosts? No
<reads resolv.conf>
<ip of router>, do you know where google.com is? Yes i do! I asked ... and they said the ip is ...

```
Or this for your domain in the proposed setup:
```

Is it in hosts? No
<reads resolv.conf>
<ip of router>, do you know where my.domain.name is? No
<ip of local dns server (ubuntu host)>, do you know where my.domain.name is? Yes i do! The ip is ...

```
Kinda get it? If you're interested, look up how dns works, really interesting stuff.

---

### Post by jabz on 2012-05-23
I just solved the problem. It was easier than setting up a DNS server (which I did). 

I just had to add

XXX.XXX.XXX.XXX en-de.example.com
XXX.XXX.XXX.XXX de-de.example.com

to the hosts file of the guest system.
Thank you very much. for your help.

---


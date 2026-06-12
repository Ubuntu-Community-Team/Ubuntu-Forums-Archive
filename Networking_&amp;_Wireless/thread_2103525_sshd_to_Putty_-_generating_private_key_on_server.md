---
title: "sshd to Putty - generating private key on server"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by jdege on 2013-01-10
I frequently remote-in to my home Linux box, from my Windows box at work, using Putty to connect to sshd.

When I first opened up port 22 on my Linux box, I'd get tens of thousands of failed login attempts, every day, showing up in my syslog. So I moved sshd to a non-standard port, enabled public key authentication, and disabled password login entirely.

I'm fairly confident that the result is secure. (Actually, I don't think that using a non-standard port increases security, but it does keep me from seeing the script-kiddies failed attempts in my logs).

My problem - the tutorials I followed to get this working had me generate a key pair on the windows client, and then add the public key to the sshd config at the linux server.

What I want to know is how to do it the other way - how to generate a key pair on the linux server, with a private key file that I can carry around with me, and install on any computer that has putty installed.

Ideas?

---

### Post by firebadger on 2013-01-10
There is a ssh-keygen tool that you should already have installed. Works just the same as the Windows one however you are supposed to generate the keys on the client and it just doesn't work the other way round.

---

### Post by jdege on 2013-01-10
That presupposes that you will be configuring each client individually, and that simply can't be a universal use case.

---

### Post by firebadger on 2013-01-10
Pretty sure it is. You need unique certificates on each machine so even if you could do it the other way round you'd still have the same amount of work.

---

### Post by jdege on 2013-01-10
Certificates? Who's talking about certificates?

What I'm looking for is a private key I can carry with me, to use in connecting to the server from whatever client machine I happen to be sitting at.

---

### Post by firebadger on 2013-01-11
Actually the terms "keys" and "certificates" are frequently used to mean the same thing. Try googling "ssh certificate" for example.

The simple answer is that you can't do what you want to do. Also, you might try being a little more polite with people who are trying to help you.

---

### Post by steeldriver on 2013-01-11
there's nothing to stop you copying the private key file (.ppk) that you generated with putty and using that wherever you like - or am I missing something here? :confused:

---

### Post by jdege on 2013-01-11
> **firebadger said:**
> Actually the terms "keys" and "certificates" are frequently used to mean the same thing. Try googling "ssh certificate" for example.
When I google "ssh certificate" I get pages about how openssh has recently added support for Certificate Authority keys, and I was afraid you were leading me down the wrong path, entirely.

> **firebadger said:**
> The simple answer is that you can't do what you want to do.
I know that what I want to do can be done, because I've seen it done.  The only question is how it was done.

> **firebadger said:**
> Also, you might try being a little more polite with people who are trying to help you.
I'm sorry if I sounded a tad frustrated.

---

### Post by firebadger on 2013-01-11
Cool. 

Steeldriver is right you should be able to do it by copying the private key amongst all the client machines. I hadn't heard of anyone doing this before though and I was definitely wrong with my absolute statement previously. 

Anyway, the question of whether you should is another matter. I guess the main issue is that if it was compromised and you had to revoke it you would lose access across many clients rather than just one.

---

### Post by efflandt on 2013-01-12
**Nothing says you need a unique private key for each client.** Perhaps you did not know that PuTTYgen can generate a key for itself from an openssh private key using the key's existing passphrase.

At [http://the.earth.li/~sgtatham/putty/0.62/htmldoc/Chapter8.html#pubkey-puttygen](http://the.earth.li/~sgtatham/putty/0.62/htmldoc/Chapter8.html#pubkey-puttygen) scroll down to:
**8.2.12 Dealing with private keys in other formats**

I use the same Linux openssh generated private key to connect between various computers at home, between PuTTY at work and home, or between any of those and my NetBSD shell account on the internet.  Using the same private key for multiple ssh or PuTTY clients has never been an issue.

I always configure sshd to use keys only, so any password crack attempts are futile.

---

### Post by markbl on 2013-01-12
Normally you generate the key pair on the client side (e.g. using PuTTYgen on Windows) and then copy the public key to the server (e.g. via ssh-copy-id, email, scp/ftp, hand pass on usb stick, etc). The reason is philosophical at least - you always keep the private key local to your client box because it should be kept private and secure. The public key is the one you send to the server because in theory it doesn't matter if it gets intercepted.

---


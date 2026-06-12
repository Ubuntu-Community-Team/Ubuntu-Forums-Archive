---
title: "SSH Server to Annonymize Originating IP"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by zshuford on 2009-11-08
Hey everyone,

I have a server set up with Ubuntu, and it's worked flawlessly. Recently, my brother joined the Peace Corps, and is stationed in Romania. He managed to get the internet there, but he can't use it to watch video (such as DirecTV's web streams of football) due to him being outside of the USA.

I told him, no prob, we'll send you through an SSH tunnel. So I walked him through downloading Putty and FoxyProxy, and he was off. We tested it on Hulu, but when he went there he got the same "can't access videos from outside of the US" message he got before. I know he has the proxy stuff configured right, because when he'd log out of Putty, his web would stop working (so he was definitely using the tunnel).

But for some reason, Hulu still knew he was in Romania. I assumed the SSH tunnel striped off the originating IP, but maybe it's forwarding it along. 

Anyone got any ideas?

---

### Post by kurtkraut on 2009-11-08
I don't think SSH told Hulu the original IP address. I think it is a browser issue, like a cookie. Hulu uses aggressive ways to block non US connections, like DNSBL queries, port scans and I wouldn't be surprised if when he detects a browser in a language different than english, he would block too.

---

### Post by fargle on 2009-11-10
I didn't see any mention of installation of proxy software on your computer - did you do that part?  I use tinyproxy on my home machine, SSH to it from work and forward port 8888, which tinyproxy listens on, then set my work Firefox to use localhost:8888 as its proxy - that's what makes the traffic appear to come from my home machine.

There are still a few Flash apps that I've seen that don't support using a proxy, and I'm not sure if Hulu is one (wouldn't surprise me!) so you'll still have to test.

Have him go to "whatismyip.com" regularly to check that he's showing your machine's address and not his.

---

### Post by kurtkraut on 2009-11-10
> **fargle said:**
> I didn't see any mention of installation of proxy software on your computer

OpenSSH has a built-in SOCKS proxy. It is **ssh -D** command. You may find instructions on how to use it [here]("http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/").

---


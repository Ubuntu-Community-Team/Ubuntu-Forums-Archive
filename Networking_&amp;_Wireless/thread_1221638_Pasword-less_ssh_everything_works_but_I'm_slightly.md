---
title: "Pasword-less ssh: everything works but I'm slightly confused"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by prshah on 2009-07-24
Hello,

I have successfully setup ssh access to my desktop machine from both my laptop as well as my PalmOne Treo 650 (using pssh).

I can do passwordless login from my laptop as well as my Palm, using publickey authentication. If I use other clients, I'm prompted for my password.

All correct.

On a point of order though: I have generated a RSA key pair, but I have kept the public key on my desktop's ~/.ssh and distributed the private key to my laptop and Palm. Is this correct, or am I doing something wrong? To my understanding, I should have to give the id_rsa.pub (public key) file to the clients, but here it's the opposite way around. Is this correct?

When I try it the other way (distribute public key, keep private key on desktop) publickey authentication fails and I'm prompted for password. The authorized_keys2 file on the desktop is accordingly correctly set.

Only the desktop is running the SSH server.

Everything works, but I'd appreciate it if someone can tell me if I've opened up a security hole by distributing the private key instead of the public key.

Finally, how secure is this? I've set up a 2048 bit RSA key, but can the key be "snooped" mid-transmit during authentication? Any other caveats / gotchas?

---

### Post by kidders on 2009-07-25
> **prshah said:**
> I have kept the public key on my desktop's ~/.ssh and distributed the private key to my laptop and Palm. Is this correct, or am I doing something wrong?Technically, you haven't really "distributed" your private key. SSH's public/private key encryption exists to allow you to access an account you don't necessarily own from an account that you *do* own. The theory is that you retain control of the secret component of your key, while the public component is copied (ie distributed) to any servers you would like to access. For example, suppose you were using your laptop to access accounts on shared servers in a university. The private key would reside on the side of the connection that you control, while the public key would be readable by anyone with sufficient access to any of the shared servers.

Put another way, the public key allows someone/something to verify you are who you say you are, and can be freely distributed. The private key lets you say who you are, so it must always remain under your control.

Think of your private key as a plain text password sitting in a file on your hard disk. The main security issue with public/private key encryption is the risk of compromising it. The more devices you copy it onto, the harder it is to keep them all away from prying eyes. 

I hope that helps.

---


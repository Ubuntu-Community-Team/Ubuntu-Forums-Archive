---
title: "Share CUPS printer through the internet...securely"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Cubytus on 2009-02-02
Hi to all, 

I put a shared printer for my home network on an Ubuntu 8.04 machine. I can reach it from my other computers while on the network, but would like to access it from the Internet as well (Printing while outside)

First problem is **access rights**: of course I don't want any unauthenticated userto begin printing from outside: conversely, it's really unergonomic to ask for credentials while inside the network.

Ideally, I would like to use authenticate distant's computer authentication. However, this would render the sharing with another computer.

As far as I know, the most flexible method remains using username/password pairs. This is where lies the second problem: if I want to authenticate some user present on LAN through the Internet, the connection must me secured/encrypted.

How can I do this through SSH?

As well, as Windows doesn't include a SSH client by default, what fallback method could be used without comprimising security (having a sort of "certificate" to hand the server)? PuTTY does exist, but it can't be assumed that I will be able to install anything on the Windows computers I may be using.

So far, I have no idea on how to configure the Ubuntu server to make it work in this setup.

---

### Post by nixscripter on 2009-02-03
What you can do is SSH port forwarding.

Support you have a print server A, a computer B who can access the server directly and can see the outside, and C who wants to use the printer.

B must also be running an SSH server.

C runs this command: ```
ssh -L 631:serverA:631 user@serverB
``` Since authentication into B is required, this is the security part.

Then C connects to B as if B were the print server. The connection will be forwarded invisibly to A.

---


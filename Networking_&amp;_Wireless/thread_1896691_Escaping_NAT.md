---
title: "Escaping NAT"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by 9072997 on 2011-12-17
I have a server , but it is behind NAT and I have asked the network admin if he could forward me a port, but he said he could not forward any ports to my server. on top on that the internet connection for the server is load ballenced between many dynamic ip lines, so my ip changes very often (whatismyip.com gives different results every time i hit refresh.) is their any way i could receive tcp requests. i thought of trying a ip6 tunnel (ip6 of ip4 address would be fine) but it requires that i know my ip, which changes every request.

---

### Post by lisati on 2011-12-17
The only option I can think of at the moment is to see if getting a line dedicated to your server is an option.

---

### Post by Slim Odds on 2011-12-17
> **9072997 said:**
> I have a server , but it is behind NAT and I have asked the network admin if he could forward me a port, but he said he could not forward any ports to my server. on top on that the internet connection for the server is load ballenced between many dynamic ip lines, so my ip changes very often (whatismyip.com gives different results every time i hit refresh.) is their any way i could receive tcp requests. i thought of trying a ip6 tunnel (ip6 of ip4 address would be fine) but it requires that i know my ip, which changes every request.

I take it that this on your company network. They are blocking you for a good reason. Your server would be a tremendous security risk to their network.

---

### Post by lisati on 2011-12-17
> **Slim Odds said:**
> I take it that this on your company network. They are blocking you for a good reason. Your server would be a tremendous security risk to their network.

Now why didn't I think of that? I must have made my coffee incorrectly! :D

Edit: Don't forget to keep the lines of communication open with your admin people so that whatever solution you come up with doesn't strain your relationship with them.

---

### Post by 9072997 on 2011-12-17
@ slim odds

I don't see how it would be more of a security risk with the ability to accept tcp requests, and I have already bean given permission to set up a server on the network. my only goal is to be able to SSH into the box from home.

---

### Post by Dangertux on 2011-12-17
> **9072997 said:**
> @ slim odds

I don't see how it would be more of a security risk with the ability to accept tcp requests, and I have already bean given permission to set up a server on the network. my only goal is to be able to SSH into the box from home.


Well it would be more of a security risk because it is sitting on a network with the rest of their systems.

Thus if your SSH is compromised that gives an external attacker complete access to everything inside the network, that was previously unroutable. By the way -- doing any of this is a great way to get fired, just a heads up.

Also...This isn't really supported on this forum.

---

### Post by mlentink on 2011-12-18
> **9072997 said:**
>  and I have already bean given permission to set up a server ***on*** the network

Which is not exactly the same as serving request from ***outside*** the network, is it? That's likely why your admin people don't want to give you a forward. Seems like they take their jobs seriously, so I suggest a powwow with them.

---

### Post by Iowan on 2011-12-18
Does the internal IP address change? You can ask your network admin about a remote system login - once on the network, you might be able to access the server. If external access is disallowed, any further action would probably be unwise.

---

### Post by Slim Odds on 2011-12-19
> **9072997 said:**
> @ slim odds

I don't see how it would be more of a security risk with the ability to accept tcp requests, and I have already bean given permission to set up a server on the network. my only goal is to be able to SSH into the box from home.

You clearly do not understand how systems get compromised through TCP connections. Therefore, your server will most certainly be a risk if exposed to the Internet.

---

### Post by 9072997 on 2011-12-19
I asked my network admin if their was any other way I could access my server from outside and he provided me with the information to connect to the vpn, so i an tunneling ssh through that.

marked as solved

---

### Post by Slim Odds on 2011-12-20
> **9072997 said:**
> I asked my network admin if their was any other way I could access my server from outside and he provided me with the information to connect to the vpn, so i an tunneling ssh through that.

marked as solved

Nice, that's the proper way to go!

---

### Post by 9072997 on 2011-12-21
for future googlers try [http://netcallback.sourceforge.net/](http://netcallback.sourceforge.net/)

---


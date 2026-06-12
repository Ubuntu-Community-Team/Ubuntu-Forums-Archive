---
title: "Unable to connect to a certain W-LAN"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Samemax on 2010-07-14
I have Karmic Koala and together with my neighbours we have a W-LAN which I was always using without problems. Now, a couple of weeks ago, my neighbour has changed the password to this W-LAN and since then ubuntu is unable to connect.
The network is being recognized, but after the request to unlock a key for the network manager (besides, how can I unlock it once for all?) there comes the window with the request for the network-password, after typing it (correctly), nothing happens. The request for the password comes two more times and then ubuntu states that it is unable to connect.
- We have changed the password again - didn't help
- On Windows I and my neighbours get the connection
- My Ubuntu is able to connect to all other W-LANs

Can someone please help me in connecting on Ubuntu again to this certain network?

---

### Post by Samemax on 2010-07-19
Is really noone able to help me? :(

---

### Post by Iowan on 2010-07-19
Wireless really isn't my forte, but I'll give your thread a bump...
Has Karmic always asked for a key to unlock NM, or is that new since the password change? What is in */etc/network/interfaces* (probably only two lines defining "lo")?

---

### Post by Samemax on 2010-08-01
The two lines that you asked about are:
auto lo
iface lo inet loopback

Koala first started to ask for the key every time I turned on the computer after changing the password of the network.

UPDATE:
I reinstalled Ubuntu (since my notebook wasn't able to create a functioning boot-cd with lynx, I installed Jaunty). The problem remains: I can connect to other networks, but not to ours.
What changed: After choosing our network to connect with, there comes the demand for the network's password, after typing it in and clicking "connect" it tries to connect but can't, so in one minute there comes the demand again. But this time there is a password typed in, but a wrong one (with many digits and letters). Doesn't matter if I try with that weird combination or type the correct password again - the system fails to establish the connection.
The two lines under /etc/network/interfaces are still the same.
And under windows I am still able to connect.

So can someone please explain me, why this is not working on ubuntu? I'm really going crazy... :(

---


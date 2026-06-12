---
title: "ssh tunneling"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by therog726 on 2011-07-30
Hi,

I'm trying to set up ssh tunneling to encrypt my web browsing (for wireless hotspots etc) and I'm just testing it at home at the moment and I'm having some problems. I have a little experience now with linux, I'm mainly just new to the server stuff.

I've followed various guides in setting up a ssh server to tunnel through (like [this one, ]("http://www.searchmarked.com/ubuntu/how-to-surf-anonymously-using-an-ssh-tunnel-and-ubuntu.php")[this one, ]("http://omninoggin.com/blogging/how-to-encrypt-your-internet-traffic/") [or this one.]("http://lifehacker.com/237227/geek-to-live--encrypt-your-web-browsing-session-with-an-ssh-socks-proxy")) and that all seems to be ok.

So now for my questions:

[LIST]
If I tunnel from my laptop connected to my home network to the desktop (also on my home network) does that encrypt my traffic or not? Does the server need to be running on a different network (eg. at a friends place)?
[/LIST]

[LIST]
If I'm out, assuming the desktop running the ssh server is all running fine, how do I connect to it? I know I have to run something similar to:```
ssh -ND 9999 username@<ip address>
```
The ip address is: 192.1681.x but isn't that just the "internal" network address? How do I find out the "external" ip address?? Ie. to access from the outside world?
[/LIST]

That's all I can think of at the moment. Hope it all makes sense!

EDIT: Thought of some more questions:

[LIST]I read that Ubuntu basically has ssh access whenever it's turned on - Is having port 22 (or whatever) open all the time dangerous? If so, how can I make it more secure?
[/LIST]

[LIST]What is actually encrypted when I use an ssh tunnel? Is it all the packets I send via the network or my ip address or what?
[/LIST]

[LIST]My university allows ssh access - could I create a tunnel via that for the same effect? Would it cause problems that they have some web filtering?
[/LIST]

Thanks! :KS

---


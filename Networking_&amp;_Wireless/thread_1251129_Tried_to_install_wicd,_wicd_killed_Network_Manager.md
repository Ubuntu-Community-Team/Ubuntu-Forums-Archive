---
title: "Tried to install wicd, wicd killed Network Manager."
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by junglist313 on 2009-08-27
Ok so I have an Acer Aspire one net book that runs Ubuntu Netbook Remix. I had been experimenting with Awesome window manager but was having a hard time connecting to wireless from the command line. In searching for a solution I found a thread about wicd. I figured I would install it to see how it worked. I ran: 
```
sudo apt-get install wicd
```
It installed and I noticed that it stoped network manager in the process. I could not figure out wicd and I was not expecting it to wipe out Network Manager so I ran:
```
sudo apt-get purge wicd
```
Thinking that would get me back to square 1. When I rebooted Network Manager failed to appear in the panel so I tried:
```
nm-applet --sm-disable
```
And was surprised to see that nm-applet could not be found. I downloaded the debs from the Ubuntu package archive on another machine and copied them over to the netbook and installed them manually. It seems to be working ok now but my question is will Network Manager recieve updates as normal now (because it was installed froma .deb I am not sure)? If not, how would I go about installing the version from the repos?

---

### Post by i.r.id10t on 2009-08-27
apt-get -dy network-manager

then remove the network-manager package(s) you installed manually.

Then apt-get install network-manager



But, I gotta say that nm sorta blows, wicd works much better for me...

---

### Post by junglist313 on 2009-08-27
> But, I gotta say that nm sorta blows, wicd works much better for me...

I have never really had a problem with it (knock on wood) but I have heard many people say the same thing. Thanks for the help, I will try that when I get home. :)

---


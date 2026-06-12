---
title: "[help me] Ports on ubuntu 9.10"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Clouded on 2010-03-02
just installed ubuntu 9.10, first time linux user, and I have encountered several issues which are grating at my nerves. chief among which is the fact that my torrents and aMSN report blocked ports, an issue I have never encountered on my other systems (windows) I run a wireless system on the linux computer, but in the settings of the wireless router I have deactivated all firewall applications and restrictions. I tried connecting it directly to the modem via cable and there were no changes. the modem is set up to not stop any traffic either, and I have never had an issue with it until now.

are there any quick fixes I can apply from a terminal or has the port forwarding ghost reared it's hideous face to defeat me once again? (on earlier networks I have spent days toiling over ports, and they have never ever worked, so imagine my chagrin when my up-until-linux perfect network reported the same issues that had defeated me years ago)

and if it is so, that I HAVE to set up port forwarding, where can I find an explosion proof guide to do it, because I imagine I will be close to suicide by nuclear device by the end of the operation.

---

### Post by dragonboss on 2010-03-02
Try using gufw to allow those programs to run
Code sudo apt-get install gufw or from the Ubuntu Software Center
Gufw guide [here]("http://www.ubuntugeek.com/gufw-simple-gui-for-ufw-uncomplicated-firewall.html")

---

### Post by Clouded on 2010-03-02
tried gufw, if I try to allow any program, port, or service I get an "error performing operation"

---

### Post by Enigmapond on 2010-03-02
```
sudo ufw *port#* allow
```

Are you behind a router? Maybe you need to manually forward the ports on it.

---

### Post by MaindotC on 2010-03-02
> **Enigmapond said:**
> ```
sudo ufw *port#* allow
```

Are you behind a router? Maybe you need to manually forward the ports on it.

Of course he does.  These issues have nothing to do with Ubuntu!

---

### Post by Clouded on 2010-03-02
if the problem doesn't lie with ubuntu, how come all my different windows systems all work perfectly fine, reporting ports as open and functioning, I have run xp sp2 and sp3, vista 32bit and 64bit and win 7 without problems. I am willing to attempt port forwarding one more time, but I will need the be all end all how2 guide on how to do it so if anyone knows of such a guide please link it :)

---

### Post by d3v1150m471c on 2010-03-02
I use a multitude of applications that require an internet connection. Torrents, p2p, instant messaging. I also have a few applications that block suspicious traffic and a rather paranoid firewall setup. Not once have any of those applications failed me. I'm thinking this is a router or an ISP issue. Another thing, does your country block any specific traffic? Based on my own experience with tcp/ip, modems, routers, ect. this is sounding more and more like a peripheral issue. Keep troubleshooting, mate.

---

### Post by Clouded on 2010-03-02
well as I said, on my other computer I am currently running Win XP, and everything runs fine on my network. So I just can't understand why linux, which is said to be superior to windows, is having issues with my system. 4 years I have run this network setup, downloading countless of terrabytes of packets at full speed, only to have linux tell me it's not open. oh well, if you all insist that my network must be blocked then I guess I'll just have to read up on port forwarding, it would be a shame to have to end my freshly started linux career because of this.

---

### Post by MaindotC on 2010-03-02
> **Clouded said:**
> if the problem doesn't lie with ubuntu, how come all my different windows systems all work perfectly fine, reporting ports as open and functioning, I have run xp sp2 and sp3, vista 32bit and 64bit and win 7 without problems. I am willing to attempt port forwarding one more time, but I will need the be all end all how2 guide on how to do it so if anyone knows of such a guide please link it :)

There are various possibilities for this - you'd have to be a developer to understand it but as you stated you're new to Linux so I doubt it would be of any benefit to explain.

In any event, I'm assuming you have an unblemished installation of Karmic which means no ports have been closed by ufw so you have no need to make any modifications to it.  I suggest you log into your access point and enable the specified ports, both port forwarding and port triggering.  You can even try different ports as I believe this is configurable in Transmission.  Transmission also reported to me that I had blocked ports buy my torrents still work.

---

### Post by Clouded on 2010-03-02
I guess I will have to figure out how to set up a static ip for this to work?

---


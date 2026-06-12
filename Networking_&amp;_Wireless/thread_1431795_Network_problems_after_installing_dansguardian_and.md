---
title: "Network problems after installing dansguardian and tinyproxy"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by jackdale on 2010-03-17
Hi guys, I'm a non-tech ubuntu user.

I installed dansguardian with tinyproxy and configured dansguardian.conf to look for port 8888 instead of 3128 as per the instructions on the help page.

However, I found that when I set the Network Proxy to manual: http  localhost at port 8080, the weather applet did not work (gnome-panel), so I removed the new packages and reset the network proxy to no proxy.  The weather applet worked again, but I lost the cairo-dock weather applet.

More of concern, however, I also lost all ability to use apt-get, wget, aptitude and the gui update manager.  I was also not able to ping from cli.

I installed dansguardian and tinyproxy again and everything works again (except of course of the weather applet (in panel).

I don't even know how to begin to debug this.

I have now done this a couple of times with the same effect.
I initially installed the programs from cli and then "completely removed" them from synaptic.  I notice that even though I completely remove from synaptic, that when I sudo apt-get install dansguardian or tinyproxy, it does not download anything, it just installs the package...

Please help.:D

Edit:
I was not explicit in mentioning, that when I have the packages installed, but the Network Manager set to No Proxy, there is no problem (apart from aptitude update having some errors...), but as soon as I remove dansguardian and tinyproxy, everything stops :(

---

### Post by jackdale on 2010-03-27
I don't know what I did wrong in the installation, so I decided to install ubuntu-ce (ubuntu Christian Edition), which has dansguardian pre-configured with tiny-proxy and includes the simple (but effective, albeit a little bit buggy) dansguardian-gui.

This has fixed the problem.  Although I am a Christian (LDS) I didn't particularly need the additional packages included in Ubuntu-CE, but it did the trick and the extra packages are relatively unobtrusive.  It installed rather quickly, although with problems (I had to do a partial distro upgrade and then use aptitude to install because apt-get could not resolve the dependencies.

The network now works well and the proxy/dansguardian is active.  There is no compatibility problem with the weather apps now.

---


---
title: "Why my /etc/network/interfaces does not contain eth0?"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by mmasroorali on 2011-01-01
So far as my knowledge goes, /etc/network/interfaces is supposed to contain a list of all the available interfaces. But my /etc/network/interfaces looks like this,

auto lo
iface lo inet loopback


But I have a perfectly working eth0 connection. Why does not it appear here? 

What is it I might be missing?

---

### Post by chili555 on 2011-01-01
> So far as my knowledge goes, /etc/network/interfaces is supposed to contain a list of all the available interfaces....that are *NOT* controlled by Network Manager. Network Manager has its own list and scheme. If your system is working correctly, I'd do nothing. The behavior is normal and expected.

---

### Post by mmasroorali on 2011-01-01
> **chili555 said:**
> ...that are *NOT* controlled by Network Manager. Network Manager has its own list and scheme. If your system is working correctly, I'd do nothing. The behavior is normal and expected.

Thanks for the answer. I am not going to change my settings. But I need to teach some people on how to configure network from command line. When I started practising, I found my interfaces empty.


BTW, which files are used by the Network Manager?

---

### Post by chili555 on 2011-01-02
The NM settings are in various files in /etc/NetworkManager.

You will have great difficulty configuring from the command line if NM is present and running. You may be able to disable it under System > Preferences > Startup Programs and reboot. Certainly, you can remove it entirely. Of course, a server install or running runlevel 3, where NM hasn't started or isn't even installed will be no problem.

---

### Post by mmasroorali on 2011-01-02
> **chili555 said:**
> The NM settings are in various files in /etc/NetworkManager.

You will have great difficulty configuring from the command line if NM is present and running. You may be able to disable it under System > Preferences > Startup Programs and reboot. Certainly, you can remove it entirely. Of course, a server install or running runlevel 3, where NM hasn't started or isn't even installed will be no problem.

As I have found out (the hard way), NM configures interfaces NOT listed in /etc/networking/interfaces. 

Configuring interfaces directly in this file gives me connectivity, but the network applet says that I am disconnected, which is wrong.

---

### Post by chili555 on 2011-01-02
> the network applet says that I am disconnected, which is wrong.The nm-applet is a graphical indicator of what NM is doing. I think it's telling you that out of all the interfaces that NM is managing, none are connected. Since you took over eth0, it has none left to connect and is therefor disconnected.

Cryptic, ain't it?

---

### Post by mmasroorali on 2011-01-02
> **chili555 said:**
> The nm-applet is a graphical indicator of what NM is doing. I think it's telling you that out of all the interfaces that NM is managing, none are connected. Since you took over eth0, it has none left to connect and is therefor disconnected.

Cryptic, ain't it?

Cryptic and not very helpful for people, specially newcomers. This morning I spent more than two hours to debug why I was disconnected, only to find out that I was actually connected.

---

### Post by chili555 on 2011-01-02
> **mmasroorali said:**
> Cryptic and not very helpful for people, specially newcomers. This morning I spent more than two hours to debug why I was disconnected, only to find out that I was actually connected.I think the assumption is that newcomers are going to connect with NM and be happy for the rest of their lives; not that guys like you and me are going to start taking things apart within an hour of a clean install.

I always promise myself I won't but I always do!

---

### Post by mmasroorali on 2011-01-02
> **chili555 said:**
> I think the assumption is that newcomers are going to connect with NM and be happy for the rest of their lives; not that guys like you and me are going to start taking things apart within an hour of a clean install.

I always promise myself I won't but I always do!

For me it was the other way around, 

1991-1996 Sun Sparc
1997-2006 Fedora
2007-today Ubuntu

I tell my friends that using Ubuntu is making me an *** everyday. I am loosing my expertise and getting accustomed to the comfortable life. And men are no longer men (no offense intended to other half of the world :-))

---

### Post by chili555 on 2011-01-02
I agree with your sentiments entirely. My experience began with Mandrake 7.3 in about 2001. I believe that real men remove NM immediately, set up *interfaces* and *resolv* with vim and are happy the rest of their lives!

Don't even get me started about automatic transmissions and wine versus scotch.

On the other hand, many newcomers here complain that it's too hard; that networking should work out of the box with their invented yesterday wireless dongle or their invented in 1998 PCMCIA device. Oh, and even though WEP and WPA came along long after 1998, they want it to magically do WPA2, injection and airmon-ng! They usually preface their rant with some variation of, "If Ubuntu ever hopes to surpass Windows, it had better do..." 

It's hard to try to be all things to all users. Fortunately, for guys like us, we can ditch NM and other beginner tools and do things the reliable way.

Remember when the only way to burn a CD was the command line?

---

### Post by perspectoff on 2011-01-02
Cool! Another NM bashing thread!

NM doesn't work reliably me for static IP addressing, for wired connections (which freeze randomly and require a network restart), and especially not for wireless connections.

I always remove Network Manager completely. For wired computers I use the default kernel negotiations (and edit /etc/networking/interfaces manually).

For wireless connections I use Wicd.

---

### Post by PatchesTheCaveman on 2011-01-02
You can control NetworkManager from the command-line with the *nmcli* command.  So you can still "be a man" in the modern age.  :-D

wicd can also be controlled with *wicd-curses* but that's just a console version of a graphical control interface, so probably not manly enough for you guys.  :evil:

These tools give you a command-line interface, but with the advantages of using the above programs for network management (e.g. not needing root access for network configuration).

---

### Post by mmasroorali on 2011-01-02
> **chili555 said:**
> I agree with your sentiments entirely. My experience began with Mandrake 7.3 in about 2001. I believe that real men remove NM immediately, set up *interfaces* and *resolv* with vim and are happy the rest of their lives!

Don't even get me started about automatic transmissions and wine versus scotch.

On the other hand, many newcomers here complain that it's too hard; that networking should work out of the box with their invented yesterday wireless dongle or their invented in 1998 PCMCIA device. Oh, and even though WEP and WPA came along long after 1998, they want it to magically do WPA2, injection and airmon-ng! They usually preface their rant with some variation of, "If Ubuntu ever hopes to surpass Windows, it had better do..." 

It's hard to try to be all things to all users. Fortunately, for guys like us, we can ditch NM and other beginner tools and do things the reliable way.

Remember when the only way to burn a CD was the command line?

Yes, I distinctly remember. Now applications like k3b or the one which pops up as soon as you insert a blank CD (I do not use it) sometimes appear like too much comfort for me.

But again, we need these features to get mass people on the boat. However, sometimes it appears to me that the FUD technique has created an almost impossible situation. Add to this the very loose copyright policy in many countries, including mine.

---


---
title: "Goodbye Vinagre, hello Remmina!"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by SteveDee on 2011-12-08
As it appears that Vinagre, tsclient and rdesktop will be replaced with Remmina and FreeRDP in 12.04 I thought I'd take a look at Remmina for myself.

I've been using Vinagre ("Remote Desktop Viewer") for about 3 years to VNC into 'buntu servers, and this year I have been using rdesktop to run a number of thin clients connecting to Windows servers. VNC has always been a bit slow (actually, its been painfully slow), while rdp is very fast. But I have been unable to get RDP working Linux-to-Linux.

So having installed Remmina I was pleasantly surprised when I selected "Protocol: VNC" and accessed my BirdBox server. With Quality set to "medium" and colour set to 16bit, desktop response seems as fast over wifi as if I was working directly on the servers local screen.

I didn't notice any improvement in using Remmina on RDP to a Windows server, compared to rdesktop. And using RDP to access a Linux server still does not work for me, so I need to look at the server (xrdp) end.

Installation via Synaptic was trouble free on Lubuntu 11.xx, as was configuring connections to remote Linux & Windows servers. Your configs can be saved (like Vinagre), and its easy to set quality, colour depth and screen size. It even has a debug window!

---

### Post by bluexrider on 2011-12-08
> **SteveDee said:**
> As it appears that Vinagre, tsclient and rdesktop will be replaced with Remmina and FreeRDP in 12.04 I thought I'd take a look at Remmina for myself.

I've been using Vinagre ("Remote Desktop Viewer") for about 3 years to VNC into 'buntu servers, and this year I have been using rdesktop to run a number of thin clients connecting to Windows servers. VNC has always been a bit slow (actually, its been painfully slow), while rdp is very fast. But I have been unable to get RDP working Linux-to-Linux.

So having installed Remmina I was pleasantly surprised when I selected "Protocol: VNC" and accessed my BirdBox server. With Quality set to "medium" and colour set to 16bit, desktop response seems as fast over wifi as if I was working directly on the servers local screen.

I didn't notice any improvement in using Remmina on RDP to a Windows server, compared to rdesktop. And using RDP to access a Linux server still does not work for me, so I need to look at the server (xrdp) end.

Installation via Synaptic was trouble free on Lubuntu 11.xx, as was configuring connections to remote Linux & Windows servers. Your configs can be saved (like Vinagre), and its easy to set quality, colour depth and screen size. It even has a debug window!

it works very well with windows rdp. i use it to access the XP box and media server

---

### Post by sleepyhollows on 2012-02-11
I've seen vnc run good, but I've never been able to get it reliably good.

Any luck with xrdp?

I've just installed it, and connected successfully to sesman-Xvnc, but it's even slower than vino running on the console! :(

I see in the list, 'sesman-xrdp', which I would like to get working :)

Apparently it uses libxup.so, but thats all ive worked out so far

Mic

---

### Post by sleepyhollows on 2012-02-11
I suggest checking this post out:

[http://www.css-networks.com/2010/12/linuxunix-x-as-an-rdp-remote-desktop-protocol-server/](http://www.css-networks.com/2010/12/linuxunix-x-as-an-rdp-remote-desktop-protocol-server/)

So many threads started by people about xrdp! Doesn't anybody use the search??

---

### Post by SteveDee on 2012-02-11
> **sleepyhollows said:**
> ...Any luck with xrdp?...

I haven't spent any more time looking at this because I'm happy with my home setup. But thanks for the link, I'll check that out.

However, I have a problem at work with jerky video on Linux thin clients running from Microsoft RDP. Microsoft have tried to address their RDP/video problems with "RemoteFX" which we have enabled on our servers. But RemoteFX support has only just been added to FreeRDP (like mid-January), and there is a lack of info on how to use...anyway, that's for another post!

---


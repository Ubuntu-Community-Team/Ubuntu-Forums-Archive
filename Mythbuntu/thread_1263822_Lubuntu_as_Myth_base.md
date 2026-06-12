---
title: "Lubuntu as Myth base"
date: 2009-09-11
forum: Mythbuntu
---

### Post by Boppy3125 on 2009-09-11
I just read about the upcoming Lubuntu distro.  From this writeup, it uses much less memory.  So as a base to run Myth from, it seems that it would potentially leave more system resources to Myth.  Thoughts and comments for those more knowledgeable would be appreciated.  As in, would Mythbuntu ever move from xubuntu base to this, or maybe using this as a base and adding MCC to add the compenents myself.

[http://www.linux-mag.com/cache/7520/1.html](http://www.linux-mag.com/cache/7520/1.html)

---

### Post by mungewell on 2009-09-11
Generally a Myth frontend shouldn't be running on an underpowered machine, so the X11 desktop shouldn't make that much difference. But (if like me) your machine is resource stretched, it certainly can't hurt.

A backend does not need to be running X11 at all.

In theory you should be able to 'apt-get install lde-desktop' and configure GDM to use this as the default desktop. 

There are also other areas to look at too...
1) Network manager - disable and go back to the old '/etc/network/interfaces' method.
2) It may be possible to use the X-in-kernel, which is *MUCH* smaller than the full X11 stack. However this has licensing issues, see [http://www.microxwin.com/](http://www.microxwin.com/)
3) Question whether full mySQL is actually required...

---

### Post by Boppy3125 on 2009-09-11
Thanks, I am also doing some further reading and Lubuntu doesn't really sound like it is very far along.  That article made me thing it was some new official flavor.  It's not.  I am not really that concerned myself, I just read that with thoughts on an old laptop and just started thinking of ramifications on Mythbuntu potential.

---

### Post by klc5555 on 2009-09-11
> **Boppy3125 said:**
> Thanks, I am also doing some further reading and Lubuntu doesn't really sound like it is very far along.  That article made me thing it was some new official flavor.  It's not.  I am not really that concerned myself, I just read that with thoughts on an old laptop and just started thinking of ramifications on Mythbuntu potential.

Depends on how old the laptop. I use an old Thinkpad T23 and an equally old HP/Compaq Nc600 (both running at about 1.1 Gig) as remote wireless frontends (Wireless N, but they were also fine on wireless G). One runs full-blown Ubuntu 9.04 (plus Mythtv packages), the other Kubuntu 9.04 (plus Myth). Both do SD and analog playback flawlessly. Lubuntu or the equivalent are not strictly required on this level of hardware.

If you really wanted to go lightweight, I suppose you could install a command-line-only system using the alternate installer Ubuntu 9.04 disk. Then gradually add just X support, the lightweight WM you wanted (is there a Ubuntu WM lighter than "twm"?), and the few really necessary additional packages with apt. There are a few guides outlining how to do this on the web. Then to this really really minimal Ubuntu system you could add mythtv-common and mythtv-frontend (and their dependencies) and end up with something close to the lightest possible 'buntu laptop myth frontend. That might be a fun little weekend project to try sometime ...

---

### Post by tgm4883 on 2009-09-11
In the very early builds of the first Mythbuntu cycle, we used openbox as the WM. We decided to move away from this as more people are familiar with XFCE (or rather that sort of WM).

I'm not saying that we won't move away from XFCE, but it's not likely. It may break upgrades and that is something we likely will not do.

---


---
title: "Optimal driver for Intel Integrated Graphics Controller (GM965/GL960)"
date: 2008-08-21
forum: Multimedia Software
---

### Post by FFighter on 2008-08-21
Hello folks,

I have a dv6448SE HP laptop running Hardy (8.04). I've disabled Compiz a long time ago so I'm not using desktop effects (since there is a known problem with Compiz and Intel graphics card, at least when I last checked).

However, I've noted that the GUI rendering sometimes is slow and or kind of buggy. I have checked the restricted driver manager and there is not any driver listed there, so I suppose I should install the proprietary drivers for my Intel graphics card?

Here's the relevant output from lspci:

> 
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


And the relevant section from /etc/X11/xorg.conf:

> 
Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphi$
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection


Is the "intel" driver the optimal option for the Integrated Graphics Controller?

Thanks in advance,

Marcelo.

---

### Post by Flyingjester on 2008-08-21
it's the one i always use, and it seems to work for me very well.

---

### Post by FFighter on 2008-08-21
> **Flyingjester said:**
> it's the one i always use, and it seems to work for me very well.

Hey, thanks for the reply.

Does this driver appear in the restricted drivers list for you?

---

### Post by k8bopibu on 2008-08-21
Intels driver should not show up in the restricted drivers because it is open source. It sure beats Vesa or any of the i810 drivers or such. This website may interest you, it has some pretty neat documentation: [intellinuxgraphics.org](http://www.intellinuxgraphics.org/documentation.html)

~k8

---

### Post by georgemolson on 2008-09-07
Hey, I have the same graphics card as you for my Sony Vaio, so I am hoping for some magic from these Intel drivers. I just bought a brand new laptop from Sony shipped with Vista and I couldn'tbelieve how poor the performance was (I wanted a refund but thought I will give Linux a try first and the performance difference is night and day). If I can get compiz running this thing its going to be better than Vista appearance wise too. If I had known how much Vista sucks and how much Linux has come along, I would have looked for a computer that ships with Linux with all drivers working out of the box.

[http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html)

---

### Post by chadeusmaximus on 2009-02-24
> **FFighter said:**
> Hello folks,

I have a dv6448SE HP laptop running Hardy (8.04). I've disabled Compiz a long time ago so I'm not using desktop effects (since there is a known problem with Compiz and Intel graphics card, at least when I last checked).

However, I've noted that the GUI rendering sometimes is slow and or kind of buggy. I have checked the restricted driver manager and there is not any driver listed there, so I suppose I should install the proprietary drivers for my Intel graphics card?

Here's the relevant output from lspci:



And the relevant section from /etc/X11/xorg.conf:



Is the "intel" driver the optimal option for the Integrated Graphics Controller?

Thanks in advance,

Marcelo.
There's a known problem with intel Integrated Graphics?  I have the Intel Integrated Graphics Controller (GM965/GL960) as well,  and sometimes my graphics are really choppy (Toshiba Satellite A205 2X 1.66Ghz coe duo, 2GB Ram).  Any body know where I can get a fix for this? 

The Helios screesaver is really Choppy,  and Nexuiz almost always crashes on me.  Doesn't seem to matter if I'm running Compiz or not.  I'm running Ubuntu 8.10 32bit. (maybe I should switch to 64bit?)

---

### Post by PrincessZeratul on 2010-05-14
I'm having the same problem. I find though if I change the monitor resolution it temporarily works until I restart. It's not a problem with a particular resolution though, as I just keep switching between two. Any longer term solutions out there?

---

### Post by SanraS on 2012-03-21
:confused:> **FFighter said:**
> Hello folks,

I have a dv6448SE HP laptop running Hardy (8.04). I've disabled Compiz a long time ago so I'm not using desktop effects (since there is a known problem with Compiz and Intel graphics card, at least when I last checked).

However, I've noted that the GUI rendering sometimes is slow and or kind of buggy. I have checked the restricted driver manager and there is not any driver listed there, so I suppose I should install the proprietary drivers for my Intel graphics card?

Here's the relevant output from lspci:



And the relevant section from /etc/X11/xorg.conf:



Is the "intel" driver the optimal option for the Integrated Graphics Controller?

Thanks in advance,

Marcelo.

:confused:I have the same Graphics Controller, on an inspiron 1525 and dunno how to get those, I am the type of person that need a s-t-e-p by s-t-e-p guide terminal commands preferably if possible please.

---


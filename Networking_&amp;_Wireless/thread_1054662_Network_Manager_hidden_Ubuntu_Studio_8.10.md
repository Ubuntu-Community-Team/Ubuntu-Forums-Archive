---
title: "Network Manager hidden? Ubuntu Studio 8.10"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by myztic_man on 2009-01-29
Hi there.
I am fairly new to Linux, but I have been using it at work, and just installed it on my Dell Vostro.
However, I cannot find the Network Manager program.

It does not appear under: System->Administration (only the applet 'Network Tools' does).

I have tried running the commands from xterm:
nm-applet &

This returns the information:
'The program 'nm-applet' can be found in the following packages:
*network-manager-gnome
*mythbuntu-diskless-client

So, i assume this means that the thing is installed? I just cannot find it anywhere.. Any ideas?

---

### Post by specialcharacter on 2009-01-31
Actually means it isn't installed, but can be installed in either of the packages mentioned.

Try

```
sudo apt-get install network-manager-gnome
```

and then make sure it will start when you log in by going to System > Preferences > Sessions and adding a new entry with the command 'nm-applet --sm-disable'.

IMHO your better off without network manager and learning to use ifconfig and /etc/network/interfaces, but all in good time eh?

---

### Post by ianchristie on 2009-02-09
I'm having a similar problem, however, network manager is not even available on the install DVD and I can't even get a wired network. And without network, it can be dificult to learn to use ifconfig without being able to look at forum posts or other tutorials.

---


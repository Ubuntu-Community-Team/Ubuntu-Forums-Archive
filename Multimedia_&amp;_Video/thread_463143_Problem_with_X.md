---
title: "Problem with X"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by szopa on 2007-06-03
Hello, 

I recently (~6 weeks ago) started having some strange and annoying problems with X. That is, it sometimes dies, without any warning. Sometimes, I can go to a console and restart GDM (then it works normally), but usually I only get something like this:

[IMG]http://szopa.tasak.gda.pl/krzaki.jpg[/IMG]

Sometimes I am still able to blindly log in as root and restart gdm (doing reset in the shell doesn't help), but usually the computer doesn't seem to be listening to the keyboard (hitting Caps Lock doesn't make the diode to light, for example). The only thing I can do is a hardware reset.

So, I'm getting something like a blue screen of death, with the difference it's not Windows and it's not even blue... ;/

Has anybody experienced similar problems? Or maybe someone knows how to solve them? I would post a bug or something, but I hardly know what's going on...

I am using an up to date Ubuntu Feisty with Gnome and Beryl (but when I switched back to metacity it didn't help--I was getting the same behavior). My video card is an integrated Intel. I can post more details if it may help.

Thanks in advance.

---

### Post by luptinpitman on 2007-06-04
I saw similar corruption when attempting to get Beryl to run on one of my machines.  The only fix I ever found was to reconfigure X using:

```
sudo dpkg-reconfigure xserver-xorg
```

This will re-identify your keyboard as well.  Possible fix maybe.  Still learning my self.

NOTE:  Don't forget to backup /etc/X11/xorg.conf before running above command.

---


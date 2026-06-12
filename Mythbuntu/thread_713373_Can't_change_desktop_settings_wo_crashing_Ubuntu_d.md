---
title: "Can't change desktop settings w/o crashing Ubuntu desktop"
date: 2008-03-02
forum: Mythbuntu
---

### Post by r_endymion on 2008-03-02
I am running mythbuntu with the Ubuntu desktop installed on Gutsy.

Every time that I try to change the themes or even  colors in my shell using the Appearance Preferences tool it completely freezes the sysem and crashes the shell. When I finally get it to reboot I usually get just a background color (no image and no panels), and I have to reboot from console mode.

dpkg-reconfigure ubuntu-desktop did restore the default desktop this time, I just wish I had known that command two clean-installs ago:mad:

The apppearence preference panel displays only generic thumbnails of the themes with a question mark superimposed on top of them. Making any change causes an immmediate problem.

So for the time being, when logged into a GNOME session, I am stuck with the default "Human" theme. I can't change colors, icons, cursors, or anything else.

---

### Post by foxbuntu on 2008-03-02
Please try the following:
```
rm ~/.gtk-2.0
```
Then try changing the theme again.

---

### Post by r_endymion on 2008-03-03
> **foxbuntu said:**
> Please try the following:
```
rm ~/.gtk-2.0
```
Then try changing the theme again.

That just returned error messages:

```

mythtv@absolution:~$ rm ~/.gtk-2.0
rm: cannot remove `/home/mythtv/.gtk-2.0': No such file or directory
mythtv@absolution:~$ sudo rm ~/.gtk-2.0
[sudo] password for mythtv:
rm: cannot remove `/home/mythtv/.gtk-2.0': No such file or directory
mythtv@absolution:~$ 

```

---


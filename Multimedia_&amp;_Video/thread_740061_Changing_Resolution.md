---
title: "Changing Resolution"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by illob32 on 2008-03-30
Hi,

Yesterday I changed my monitor resolution from 1280*1024 to 1024*768. Everything worked fine until this morning when I started the computer.

The resolution is now back to 1280*1024 and when I try to bring it back to 1024*768, I get this message;

[B]Failed to set MetaMode (7) 'CRT-0: 1024x768 @1024x768 +0+0' (Mode 1024x768, id: 56) on X screen 0

Would you like to remove this MetaMode?[/B]

I am using the Nvidia X Server Settings window, installed by Envy.
Even when I go under System---Preferences--Screen Resolution...nothing happens.

Can anyone help?

---

### Post by wolfen69 on 2008-03-30
in terminal, try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then ctrl-alt-backspace

---

### Post by illob32 on 2008-03-30
> **wolfen69 said:**
> in terminal, try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then ctrl-alt-backspace
Thanks a lot wolfen69 ...the resolution seems to be back to 1024*768
what exactly did it do?
does it mean I will need to do this every time I boot the computer?
one thing though....
when I restarted I got this message;

[B]The X system keyboard settings differ from your current GNOME keyboard settings.

Expected was model "pc105", layout "ca" and no options, but the the following settings were found: model "pc105", layout "us" and no options.

Which set would you like to use?[/B]

which one should I choose?

Use X settings  or keep GNOME settings?

---


---
title: "dell dimension 2400 boots to black screen"
date: 2009-11-06
forum: Multimedia Software
---

### Post by wiley692 on 2009-11-06
I just installed 9.10 on my dell dimension 2400 and after two successful boots after installation it started booting to a black screen. I had similar problems with 8.10 but not on any versions in between. Anyone have any ideas what is causing this or how to fix it? I am just using the integrated intel video and have 768mb of ram.

---

### Post by tommynz1975 on 2009-11-06
I have the same system.

if you mean screen is blank between grub and login

it requires an edit of your grub.
from what I understand.

can  you post your  

/boot/grub/menu.lst entry

l and in L not number one

and you will be told what line needs changing

IF you mean the screen is blank after you have logged in, then please specify

---

### Post by wiley692 on 2009-11-06
yeah, it was ok through the white ubuntu logo but never showed anything after that. I took it off my system but I will reinstall it tomorrow and get that menu.lst information posted then

---

### Post by wiley692 on 2009-11-06
I don't have a /boot/grub/menu.lst file like I did with 9.04. Where are those settings saved now?

---

### Post by tommynz1975 on 2009-11-07
a google gave me this response

There is no menu.lst in 9.10. Grub2 has replaced earlier version of grub. Everything has changed regarding editing the boot menu. Here's a link about Grub2, [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
    				__________________


I guess if I may slip a question in here. if grub2 upsets things can one elect to have the standard grub or is their no choice?

---

### Post by heyted on 2009-12-01
I have the same system with the same problem.  I solved the problem as described below.

1.  In /etc/default/grub:
Change 
#GRUB_GFXMODE=640x480
to
GRUB_GFXMODE=1024x768

2.  In /etc/grub.d/00_header:
add 
set gfxpayload=keep
right after
set gfxmode=${GRUB_GFXMODE}

3.  Update grub:
sudo update-grub

grub.cfg should have:
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi

I hope this helps

---


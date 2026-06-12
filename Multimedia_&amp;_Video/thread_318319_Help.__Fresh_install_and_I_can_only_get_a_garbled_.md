---
title: "Help.  Fresh install and I can only get a garbled screen!"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by AceRimmer on 2006-12-13
Hello all.  I'm having a problem here.  I'm installing Xubuntu on a PC and I have run into a problem.  I installed normally, and everything seemed to go fine.  However on the first reboot after install it makes it to the login screen but the screen is a garbled mess!  I can hear the sound that plays when you hit the screen, and since the cursor is in the user name field I am able to log in, but the screens are still garbled.  How can I boot to a command prompt to try and fix this?  Or is there something else I need to do?  I figure I have to edit something in my xorg.conf file most likely.  

Thanks. 

P.S. I'm installing it on a system with a 6600GT Nvidia AGP card.  Thanks.

---

### Post by padre999 on 2006-12-13
When you are at the login screen you can hit STRG+ALT+F1 (or F2,3,4,...) to open another session. It will give you the command line. Log in. Then you can follow instructions on [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) to fix the Xorg.conf.

I hope it helps.

---

### Post by Jaymoon on 2006-12-13
I had the same problem as well.  I kept thinking it was maybe set on a resolution that my monitor didn't like.  But it was actually the video card in my case.

I was using an ATI Rage something or other when I got the garbled mess.  I eventually took it out, and replaced it with this old 16MB Nvidia card I had laying around, and now it works perfect.

Maybe if it's possible, just get another "modern" card.

---

### Post by padre999 on 2006-12-14
Looks like Ubuntu doesn't like your 6600GT so much: [http://ubuntuforums.org/showthread.php?t=312764](http://ubuntuforums.org/showthread.php?t=312764)

So it is not just done with a simple reconfigure of Xorg.conf  :-k

---

### Post by AceRimmer on 2006-12-14
Well I had this card running Dapper after some reconfiguring, and it ran well.  However it gave me problems on install then, but I seem to recall it actually booting into safe mode ok.  I tried to do the ctrl+alt+F1 on my Xubuntu install and that screen was garbled too, so I reinstalled Dapper last night.  Same problems, but at least I was able to get to a command prompt screen.  However when I tried to run sudo gedit /etc/X11/xorg.conf I got an error (NULL) display or something like that.  I left for work this morning with it on that screen so I'll jimmy with it again tonight when I get home. 

Oh well, I view it as a challenge. :-k

---

### Post by taurus on 2006-12-14
Please try to use "gksudo" when you want to use gedit editor...

```
gksudo gedit /etc/X11/xorg.conf
```
Otherwise, boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by AceRimmer on 2006-12-14
Thanks!  That was probably the problem.  Can I just do an apt-get from the command line and get the nvidia drivers downloaded?

---

### Post by taurus on 2006-12-14
Yes.

```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```

p.s.  Make sure you have both uiverse and multiverse enable in /etc/apt/sources.list first...

---

### Post by AceRimmer on 2006-12-14
You da' man.  Thanks I'll give this all a try when I get off work tonight.  

Damn work cutting into my Linux time...:mad:

---

### Post by AceRimmer on 2006-12-14
ok when I try this, when I try to gedit any file with "gedit" I get this message

(gksudo:4991): Gtk-WARNING **: cannot open display:

then I get dumped back to a command prompt.

Edit:  I used vi and was able to get the files installed and the nvidia drivers.  Thanks!

---


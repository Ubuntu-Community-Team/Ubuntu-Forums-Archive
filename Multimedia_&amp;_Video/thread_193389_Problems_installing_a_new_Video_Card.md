---
title: "Problems installing a new Video Card"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by AceRimmer on 2006-06-09
Hello.  I'm using 6.06 and I want to switch my video card to a faster one but I'm having major problems.  I installed the system with an ATI Radeon 9000 Pro AGP card.  It installed fine, the video playback was choppy at first until I edited the xorg.conf file from 'vesa' to 'ati' in the driver section.  It was then running ok, I have no idea how to check if it was running with 3d acceleration or what, the spinning gear fps program was showing around 2500 fps, but at least DVD playback worked without being a slideshow. 

Ok so I want to put in a Nvidia 6600GT card in, a much faster board.  So I go back into xorg.conf to change the driver back to 'vesa' thinking I will avoid a conflict with the system loading the ati driver when a Nvidia card in in there.  Well I reboot, it gets to the login screen and I log in.  It goes to the text shell screen, like you get when you do ctl+alt+backspace, and asks me to log in again.  I do, and then after a few seconds it goes back to the graphical log in screen and prompts me to log back in.  I do and it goes back to the text shell, and appears to be the same session I was in before since the half typed sudo gedit command was still on the screen.  Now it just keeps going back and forth, every time I log in I get the non graphical log in, which only pops back to the graphical login, etc.  I can never get past this session.  One time when I was able to type in a command before reverting to the graphical log in screen I tried to sudo gedit /etc/X11/xorg.conf and it told me there was an error and the file didn't exist.

What did I do wrong, and how do I install a new video card in an existing Linux setup?  

Any help would be appreciated.  I'm really enjoying Dapper other than this issue.  I'm going to throw the ATI card back in and hope I can at least get the x server running again.  :-?

EDIT:  I put my ATI card back in and I have the same problem.  I can't actually log into anything.  This is so frustrating.  Now I have a  dead linux box it appears.  I can't do anything to log into the system. 

EDIT 2: I put the 6600GT back in and I ran this option 'sudo dpkg-reconfigure xserver-xorg' and redetected my video card.  Now I just get a garbled screen and if I go to the shell it immediately goes back to the garbled login screen.  Now I can't even get a shell to reset the driver to vesa.  This is killing me.  Breezy had this problem with the 6600GT as well, so did the live CD.  The card is flawless in Windows and ran fine in Fedora 5.  Why does Ubuntu have such issues with video drivers!  ](*,)

---

### Post by scxtt on 2006-06-10
i've had good ATI success doing the following:

[http://www.ubuntuforums.org/showthread.php?p=1115995#post1115995](http://www.ubuntuforums.org/showthread.php?p=1115995#post1115995)

keep in mind this is after a fresh install of dapper ...

---

### Post by AceRimmer on 2006-06-10
[QUOTE=scxtt]i've had good ATI success doing the following:

[http://www.ubuntuforums.org/showthread.php?p=1115995#post1115995](http://www.ubuntuforums.org/showthread.php?p=1115995#post1115995)

keep in mind this is after a fresh install of dapper ...[/QUOTE]

Thanks I'll give that a try.

---

### Post by AceRimmer on 2006-06-10
Still no dice.  I've got the ATI card working again but I get errors when I run fglrxinfo.  It is the same as this thread [http://www.ubuntuforums.org/showthread.php?t=189000]("http://www.ubuntuforums.org/showthread.php?t=189000")

I really want to get that Nvidia card working so I can see how WoW runs under Wine.  The ATI isn't even close to fast enough for that.

---

### Post by AceRimmer on 2006-06-13
So do you think my best option is a clean install with the Nvidia card in there?

---

### Post by wbmj on 2006-06-13
Did you try sudo dpkg-reconfigure xserver-xorg? Oops didn't see the bottom of your post.

---


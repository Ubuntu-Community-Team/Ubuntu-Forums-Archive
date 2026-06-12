---
title: "Widescreen Resolution Fix"
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by SimonLoftus on 2007-01-06
I had a problem with my resolution, wasn't able to find it in the list given by default.

After asking around and only seeing crap tutorials, we finally got it, and well here it is hopefully :D  And will hopefully be noob proof cos im a noob.

First open up the terminal, Applications>Accessories>Terminal

Type in your prefered resolution and refresh rate, in the following format:

"gtf 1440 900 60 -x"  Assuming that 1440 * 900 is your resolution and 60 is the refresh rate.

then you must edit your xorg.conf file:

In the terminal, type "gksudo gedit /etc/X11/xorg.conf"  This will open up the file so you can write to it, after you put in your pass of course.

First make lines 107 to 116 in your file look like mine but using the information gained from the gtf command.

Then edit line 150 so that your 24bit colour option has the resolution you want to be able to select.  In my case 1440 * 900.

Here is how mine looks, and it works.  [http://ubuntu.pastebin.com/862425](http://ubuntu.pastebin.com/862425)

Then, well you are done, save the file.  In the terminal finish by typing "sudo /etc/init.d/gdm restart"  This will restart your visual bit back to the login screen.

If you do this and for some reason it messes it up, for instance, the graphical user interface wont load, then type "sudo dpkg-reconfigure xserver-xorg" , so make sure to write that down, this will allow you to reconfigure your settings back to they were before, takes a few mins to do that, just select the default for anything you don't understand in it, or read what it says on screen.

If you think you followed everything and it didn't work, please feel free to email me, or just ask on irc, they are really helpful.


Big credit to Jowi, for providing most the help, ikonia for trying his best and the other guys in irc.

---

### Post by taurus on 2007-01-06
You should use "gksudo gedit" instead of "sudo gedit"!

```
gksudo gedit /etc/X11/xorg.conf
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by SimonLoftus on 2007-01-07
What is the difference? hehe  I will change if I got it wrong, I probs copied the command i used wrong, but that seemed to work.

Ok read your tutorial, didn't realise it was a link in the page at first.  Makes sense to me.  I will change it right away.

Thank you :D

---


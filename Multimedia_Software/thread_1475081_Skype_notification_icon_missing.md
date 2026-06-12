---
title: "Skype notification icon missing"
date: 2010-05-06
forum: Multimedia Software
---

### Post by Carthexis on 2010-05-06
Hi there,

I'm using ubuntu 10.4 and accidently removed the notification area from the top panel.
Since then, I haven't been able to retrieve the icon. As I've read in many threads, I've added a new panel and added a notification error, but the area stays empty. (see screenshot)
My other icons like the volume control and the amarok icon were gone as well, but setting up a new indicator applet did the trick. Still, the skype icon won't come back, I've even removed Skype and reinstalled it, but nothing changed.
Does anyone have an idea how I could get the icon back again?

---

### Post by Carthexis on 2010-05-07
*bump*
No one having this problem? I've seen that the pidgin icon is also missing and no longer showing up :(

---

### Post by xc3RnbFO8P on 2010-05-07
Found this:
> berk  wrote on 2010-04-01:  	  #13

Hi,
It certainly happens on Lucid sporadically. This morning I lost my network manager applet too. The difference is, none of the proposed methods work. (restarting nm-applet, reinstalling the package, or readding the indicator applet)

That makes me wonder about gconf settings which turns out to be true.

My very quick and dirty solution is:

- backup your .gconf folder to .gconf-bak and logout
- login. now you have clean desktop with a working network applet
- To restore your old settings, move your new .gconf to .gconf-fresh
- rename .gconf-bak to .gconf
- delete .gconf/apps/panels and copy the working panels from .gconf-fresh/apps/panels

This should work if everything else fails. Unfortunately I did not have time to investigate deeper to find the exact cause. I hope this helps

Cheers

---

### Post by Carthexis on 2010-05-07
Hej,
thanks for your reply!
Sorry if this question may seem stupid, but I'm using ubuntu only for about a week, so I'm fairly new to linux:
Which gconf folder do I have to backup?
I found 4 on my hd with the following paths:

Nr.1 - etc/gconf
Nr. 2 - usr/share/gconf
Nr. 3 - usr/share/sgml/gconf
Nr. 4 - var/lib/gconf

---

### Post by xc3RnbFO8P on 2010-05-07
.gconf is hidden folder in your home folder
/home/your folder/.gconf
ctrl - H, or in Nautilus View> Show Hidden Folder
You can rename gconf (right click on folder) to gconf bak

---

### Post by Carthexis on 2010-05-07
Hi there, found it, thanks :)
Unfortunately, Skype will still not show up in my notification area :(

---

### Post by xc3RnbFO8P on 2010-05-07
Try to delete **/.Skype** and start Skype again.

---

### Post by Carthexis on 2010-05-07
Still not working, sorry :(

---

### Post by xc3RnbFO8P on 2010-05-07
Did you try to restart the computer?

---

### Post by Carthexis on 2010-05-07
I did, but the icon still won't appear

---

### Post by anothr_acc on 2010-06-26
Arg, deleted my entry.  You'd already tried the things I suggest.  Sorry.

---

### Post by paua_fritter on 2010-06-27
I had the same problem. I got it back by:
right click >> add to panel... >> then adding "Notification Area". This made skype and my wireless signal icon reappear.

---

### Post by floopy1962 on 2010-07-07
i'm sorry for asking you but can i remove that skype icon...
the people sey they lost incidently but how :o:D i now use pidgin turn off every skype notify, my icons in notification area are 48x48 and that skype icon look ugly ;(

---

### Post by akeelqureshi on 2010-12-01
> **Carthexis said:**
> Hi there, found it, thanks :)
Unfortunately, Skype will still not show up in my notification area :(
Hello All,

I have resolved this problem 

Right Click on panel free space then click on add panel then click on notification area then skype icon will be display on system tray  :)

Thanks
Akeel

---

### Post by subjucha on 2011-03-11
Sometimes this doesn't help, then try following, helps shurely: 
Press Alt+F2, enter
gconftool --recursive-unset /apps/panel 
  Then press Alt+F1

---

### Post by Gururaj on 2011-04-07
Please dont make life trouble for simple problems .

I had the same problem. I got it back by:
right click >> add to panel... >> then adding "Notification  Area". This made skype and my wireless signal icon reappear.

Cheers
Gururaj

---

### Post by niekas on 2011-04-30
> **subjucha said:**
> Sometimes this doesn't help, then try following, helps shurely: 
Press Alt+F2, enter
gconftool --recursive-unset /apps/panel 
  Then press Alt+F1


Thank you. This worked for me while other solution didn't.

Edit. On the other hand skype icon disappeared after next reboot again. :(

---


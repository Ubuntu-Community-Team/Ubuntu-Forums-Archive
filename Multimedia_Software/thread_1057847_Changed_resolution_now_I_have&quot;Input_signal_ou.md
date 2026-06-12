---
title: "Changed resolution now I have&quot;Input signal out of range&quot;"
date: 2009-02-02
forum: Multimedia Software
---

### Post by flyinghigh4 on 2009-02-02
I am new at Ubuntu. I just installed Ubuntu 8 on my computer that also has Windows XP.  While in Ubuntu I changed the resolution from the desktop. My screen went blank and then said "Input signal out of range" Now I cannot get back into it. I can still get to my Winodws XP and I can sign on under my wife's name in Ubuntu but I can't get on my sign on. I've tried going to Ubuntu 8.10 kernel 2.6.27-7 generic(recovery mode). From there I went to "Drop to root shell prompt". I've tried typing in:
sudo gedit xorg.conf
I get this message (gedit:5011):Gtk-WARNING**cannot open display.
Then I tried:
gksudo gedit /etc/x11/xorg.conf
I got the same message.
then I tried sudo dpkg-reconfigure xserver-xorg
I got "command not found"
I've been searching and working on this for two days now and am at a lose.Can anybody tell what to do to fix this problem?:confused:

---

### Post by redroad55 on 2009-02-02
Try booting live cd and change resolution there..Post results and or Questions .. Best to you

---

### Post by xc3RnbFO8P on 2009-02-02
Do **sudo gedit /etc/[COLOR="SeaGreen"]X[/COLOR]11/xorg.conf**

---

### Post by flyinghigh4 on 2009-02-02
I tried to boot using the CD. It was still the same. When it come to the sign on screen I put my name and password then the screen went blank and said "Input signal out of range. 
I also typed in: sudo gedit /etc/x11/xorg.conf and got the same message Gtk-WARNING**cannot open display. 
When I was at the screen that said signal out of range I pressed Ctrl, Alt, F1 and it took me to a screen that kind of looked like the terminal. It gave me the option for name and password which signed me onto my account in the terminal but I didn't know what to do from there. I tried sudo gedit /etc/x11/xorg.conf again and  It asked for a password again then said Gtk-WARNING**cannot open display. Am I not doing something right?

---

### Post by TopEnder on 2009-02-02
As stated above try: sudo gedit /etc/X11/xorg.conf  where the "X" in  X11 is a capital "X"

---

### Post by redroad55 on 2009-02-02
go back to the point you just achieved enter
> sudo xrandr -s (with the resolution you want)  example: sudo xandr -s 800x600
Post back with your results .. Best to you

---

### Post by flyinghigh4 on 2009-02-02
Topender
I tried it with a capital X
Here's what the line looked like before I hit enter:
root@ubuntu:~#sudo gedit /etc/X11/xorg.conf
Still got the same thing. Gtk-WARNING**:cannot open display.

Redroad55
I went back to where it looked like the terminal and I could sign on with my name and password. Here's what the line looked like when I hit enter:
dave@ubuntu:~$sudo xrandr -s 800x600
It asked for a password again then gave me this message:
[sudo]password for dave
cant open display

---

### Post by redroad55 on 2009-02-02
I'll be back in awhile I'll post back then..best to you

---

### Post by redroad55 on 2009-02-02
I think you will find your way in here..
[https://wiki.ubuntu.com/X/NonGraphicalBoot]("https://wiki.ubuntu.com/X/NonGraphicalBoot")
Post back and let me no your progress ..Best to you

---

### Post by redroad55 on 2009-02-02
also look at this ..[https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution")

---

### Post by xc3RnbFO8P on 2009-02-03
As root:
> cd /etc/X11
> rm xorg.conf
> mv xorg.conf.backup xorg.conf
restart.

---

### Post by flyinghigh4 on 2009-02-08
I'm back again. Been busy for a few days and haven't been able to work on this.
Ringi-
I tried "cd /etc/X11" (without the quotes) and hit enter,
 then "rm xorg.config" and hit enter. 
That when I got "rm:cannot remove 'xorg.conf' no such file of directory

Redroad55-
I went to the two websites you gave me but didn't have any luck. I was ready to get on and post today that I give up and was going to reformat but thought I would try again. This time I put "sudo dpkg-reconfigure xserver-xorg" which is something I tried at the beginning and it worked this time!! Don't know why because it went through the same screens I had before.
 I want to thank you guys for you help and patience.

Thank You!!!

---

### Post by redroad55 on 2009-02-08
That's great .. Good on ya...Best to you

---


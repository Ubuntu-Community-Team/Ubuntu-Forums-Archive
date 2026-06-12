---
title: "Black Screen after i change resolution"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by Strike_105x on 2008-01-25
Hi i installed proprietary drivers that comed with kubuntu 7.10 Gutsy and my desktop resolution is to big the problem is the moment i change it back to 1600X1200 after the logo with Kubuntu after it loads (when i should enter my ID and pass) i get a blank screen can anybody help me pls this is just to big of a resolution for me to whatch on my monitor

my system is ATI 9600XT, Asus K8V-X-SE motherboard, Sempron 3000+,Sata hdd 80 & IDE 40 HDD,

pls help me someone

---

### Post by Strike_105x on 2008-01-26
Cant anyone help me ? :( also i have another problem when i install drivers using methods like sudo apt-get install xorg-drivers-fglrx or i do the manual installation when i right after the driver is installed sudo aticonfig --initial and sudo aticonfig --overlay-type=Xv the xorg.conf deletes it self or something but what is for sure is that it desapires. Forgot to mention something about the xorg.conf like i said it gets deleted after i right sudo aticonfig --initial or sometimes after i right aticonfig ---overlay-type=Xv i see alot of numbers in the terminal and at the end it says "aborted core" after that it gets deleted

---

### Post by bufsabre666 on 2008-01-26
blank sceen usually means that the monitor cant support it, try using the setting under system->admin->screens and graphics and select a refresh rate your monitor can support

---

### Post by Strike_105x on 2008-01-26
With the desktop i managed to change the resolution no more problems but how can i change the resolution for the logon screen with out restricted drivers i had no problem with 1600X1200 85Hz but now with these drivers i get black screen (black not blank sry)

---

### Post by Strike_105x on 2008-01-26
Cant anybody help me pls ? :(

---

### Post by Toadmund on 2008-01-27
I have spent all morning trying to fix mine.
Problem began when I ran envy to try and correct a problem, things worked great, but I couldn't hack a refresh rate of 60Hz, so I went and tried to change it to 70, no option to do that. 
So I then tried to try different options in screens and graphics GUI for my monitor.

Then that screwed me up, on reboot I get a little 1/4 size login window, I log in then I get a black screen.
I try to 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
then I farted around with:
```
sudo dpkg-reconfigure xserver-xorg
```

To no avail.

I tried this:
[http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/]("http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/")
No go, perhaps I did it wrong.
It's not easy to reboot all the time.

How do I fix this black screen after login problem?

---

### Post by Toadmund on 2008-01-27
OK, so I solved the black screen problem by changing the video drivers to 'vesa' using 
```
sudo dpkg-reconfigure xserver-xorg
```
via gnome terminal in the login screen.

Problem now is once I am logged in everything is slantily garbled, now how did I fix that before?

---

### Post by Toadmund on 2008-01-27
please see:
[http://ubuntuforums.org/showthread.php?p=4218774#post4218774]("http://ubuntuforums.org/showthread.php?p=4218774#post4218774")
How I solved the garbled screen.

---


---
title: "Starting Ubuntu without a monitor"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by Amorphous_Snake on 2006-11-27
When I start Ubuntu with my monitor switched on, I get 1024x768 resolution. But when I do so, with the screen switched off, I only get 640x480 with no option to change it to higher values. I have then to log out and then log in again to correct this?

What's wrong, I have nvidia drivers installed and everything seems to be fine?

---

### Post by Amorphous_Snake on 2006-11-28
Anyone can help me?

---

### Post by jclmusic on 2006-11-28
ubuntu obviously detects your monitor during bootup. no monitor detected = default resolution?

---

### Post by Swankyman on 2006-11-28
I wonder if you could remove all the lower resolutions listed in /etc/X11/xorg.conf and only leave the resolution you wanna keep.
Unless it is rewriting that file when it finds no monitor!!

Not sure though:confused:

---

### Post by cmichaelboyd on 2006-11-28
Visit [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

fill out all of the information you know, and then copy and paste the generated modeline into your xorg.conf file, in the "screen" section.  If you want to use more than one resolution, you'll have to enter the information in separately.

---


---
title: "Logitech G15 Plugin for Exaile"
date: 2007-11-08
forum: Multimedia &amp; Video
---

### Post by Chebyshev on 2007-11-08
Here is a working Exaile plugin to display the current track information to the screen on the Logitech G15 (at least it works on my machine). Of course you need g15daemon and g15composer installed and working. It is a work in progress, so let me know if you think something should be added/improved.

To install it, just throw it in ~/.exaile/plugins and then enable it from within Exaile. It makes a pipe at ~/.exaile/g15, but it should delete it when it is finished using it.

Again, let me know if you have problems or suggestions.

Here's a writeup on getting the requirements working:
[http://ubuntuforums.org/showpost.php?p=2461304&postcount=285](http://ubuntuforums.org/showpost.php?p=2461304&postcount=285)

---

### Post by XFocus on 2007-12-09
I tossed it into ~/.exaile/plugins but exaile doesn't seem to pick it up in the plugins list.  Is there anything special that I have to do?

---

### Post by SiMMeOne on 2008-01-06
same problem ... I copied the plugin into ./exaile/plugin but nothing happens. is there a workaround?

---

### Post by SiMMeOne on 2008-01-07
The problem is solved! Install the new version of exaile (0.2.11) from [http://www.exaile.org/downloads](http://www.exaile.org/downloads)
Start exaile and the plugin will apear and works very fine!
The original version (0.2.10)  from ubuntu does not work with the plugin.

Regards
SiMMe

---

### Post by syxbit on 2008-01-28
not working for me.
it shows the long bar indicating position of the song, but no text (running gutsy x64)

---

### Post by Nojatron on 2008-01-30
> **syxbit said:**
> not working for me.
it shows the long bar indicating position of the song, but no text (running gutsy x64)

I'm getting the same problem, also running gutsy x64. The bar seems a little flakey as well, it's flashing every now and then. It's not the border around it, but the inside of it is doing it (the moving part).

---

### Post by Nojatron on 2008-01-31
Ok, figured out that the problem was I didn't ./configure libg15render and g15composer with ttf support (./configure --enable-ttf).

Edit: Now the bar is running fine but the numeric current position is flashing. Other then that I'm pretty happy.

---


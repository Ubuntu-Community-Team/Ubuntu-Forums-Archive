---
title: "Youtube wont work"
date: 2009-02-07
forum: Multimedia Software
---

### Post by BrentonEccles on 2009-02-07
Why cant I view a LOT of youtube and other .flv type videos online?
I´ve got the right programs/drivers to do so isntalled, and even the youtube video will load up and so forth but just refuses to play.

How do I fix this?

---

### Post by linuxuser21 on 2009-02-07
Go System>Add/Remove Applications. Type in "flash" in search bar and download Macromedia Flash plugin.

---

### Post by BrentonEccles on 2009-02-07
> **linuxuser21 said:**
> Go System>Add/Remove Applications. Type in "flash" in search bar and download Macromedia Flash plugin.

I´ve already done that. The problem is it´s function. Videos refuse to play.

---

### Post by gandaran on 2009-02-07
can you provide system details? 32-bits or 64-bits ubuntu? 8.04 or 8.10?

---

### Post by BrentonEccles on 2009-02-07
8.10
memory: 487.6 MiB
Intel Celeron CPU 

I´m pretty sure I´m on 64 bits ubuntu ...

---

### Post by gandaran on 2009-02-07
> **BrentonEccles said:**
> 8.10
memory: 487.6 MiB
Intel Celeron CPU 

I´m pretty sure I´m on 64 bits ubuntu ...
okay for 64-bits remove the flashplugin-nonfree (flashplugin-nonfree is 32-bits flash) or any other flash like gnash or swfdec installed, use synaptic for complete removal, now get the 64-bits adobe flash [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz") 
to install extract the package and move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or if you have more than one user account or use another browser like opera install it in /usr/lib/mozilla/plugins

---

### Post by BrentonEccles on 2009-02-07
Now I get a permission error when I try to move  libflashplayer.so to /usr/lib/mozilla/plugins ... that´s really wierd because I´m the only user besides root.

What´s the problem?

---

### Post by chriswyatt on 2009-02-07
You need to be root to modify all or most things outside of your home folder:

Press Alt-F2 and a little dialog box will pop up.  Now enter "gksudo nautilus" (minus speech marks) and press enter.  This will open up Nautilus as root and you'll be able to copy the files from there.

---

### Post by BrentonEccles on 2009-02-07
Thank-you kindly for your help, problems solved. :)

Linux is quite a learning experience, albeit enjoyable too.

---


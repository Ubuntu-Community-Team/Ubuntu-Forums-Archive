---
title: "Newbie Xine-installation question"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by Toastfuzz on 2007-05-01
I'm trying to get AmaroK to work on my computer with Feisty, but I need to install the Xine-lib. I dont understand the instructions on the website; actually, I can't even get the tar to extract. When I try to extract it with this:

tar xfvz xine-lib-1.1.6.tar.bz2

I get this back:

tar xfvz xine-lib-1.1.6.tar.bz2

The file is located right on my desktop, but even when I narrow it down to the exact directory, it doesnt see the file. What am I doing wrong here?

Also, once I get it extracted, what do I need to do to configure and install it?

Thanks in advance

-Nick

---

### Post by soulfly7x on 2007-05-01
I don't understand. What method did you use to install Amarok that it didn't also install dependencies. In Ubuntu I just did "sudo apt-get install amarok" and it installed everything it needed.

Why are you downloading tarballs?

I usually use Kubuntu which has Amarok, Kaffeine and Xine by default

---

### Post by Toastfuzz on 2007-05-01
That is how I installed AmaroK, but I ran the diagnostic thing (dont remember exactly what it was called) but it runs a series of tests on Xine and the ones that came up negative told me to get the latest xine-lib files. So thats what I'm trying to do.

---

### Post by soulfly7x on 2007-05-01
Is the lib you need available in Synaptic (System > Administration > Synaptic Package Manager) ? You could search Synaptic Package Manager for Xine, and find the lib you need and try installing it that way.

Unfortunately, I don't know if you already tried this or not.

---

### Post by Toastfuzz on 2007-05-01
I've installed pretty much anything Xine related I could find in in Synaptic, along with a series of stuff I found online. I'm pretty positive its just this one file I need to use.

Any idea how to extract/install it?

---

### Post by soulfly7x on 2007-05-01
Well, I'm about all out of ideas. You can see if this link helps if you haven't been there already.
[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

Sorry, unless someone with more expertise comes along. Good luck!

---

### Post by Nythain on 2007-05-02
cant you just open it in your file manager/browser of your Desktop Environment (konqueror in kde, not sure what gnome uses default) or with a gui archiving program (ark in kde, not sure about gnome) and extract it that way???

---

### Post by Toastfuzz on 2007-05-02
I managed to get it extracted and installed, but my sound still doesnt work. Yesterday I had AmaroK working perfectly, and when I turned my computer on today, I was right back to square one, no audio at all through Xine.

---


---
title: "Choppy Flash Video"
date: 2011-07-11
forum: Multimedia Software
---

### Post by Rikeshar on 2011-07-11
Hello all. I'm running Ubuntu 11.04, have 4GB of Memory, and an AMD Phenom II X4 840 Quad Core processor.

When I play Hulu Desktop the video is choppy.

Now, the odd thing is that I had this problem before. It's the whole reason I upgraded my processor. When I upgraded I noticed an improvement, but it was still a little choppy. I then went to the Adobe site and got the latest version of Flash, and lo and behold, I could watch Hulu Desktop on HD quality with no problem!

Since then though I've had to reinstall Ubuntu. I've got the latest version of Flash, but HD quality is still choppy! 

Would anyone out there happen to know what I might be missing in order to resolve this issue? I feel like I'm probably just missing some lib file or something like that, but I can't figure out which.

---

### Post by An Sanct on 2011-07-11
Hello!

Well, what does the terminal output say, if you run it from there? That should give you info on libraries expected, but not found and other debug info...

---

### Post by Rikeshar on 2011-07-11
If I run it from the terminal I get:

(huludesktop:12959): Gtk-CRITICAL **: IA__gtk_style_detach: assertion `style->attach_count > 0' failed


Not sure what that might mean though!

---

### Post by Bucky Ball on 2011-07-11
Open Synaptics (System>Administration), search for and install 'flashplugin-nonfree'. That drags in the installer and installs the latest flashplugin 'automagically'. You don't need to do this manually anymore. ;)

---

### Post by Bucky Ball on 2011-07-11
> **Bucky Ball said:**
> Open Synaptics (System>Administration), search for and install 'flashplugin-nonfree'. That drags in the installer and installs the latest flashplugin 'automagically'. You don't need to do this manually anymore. ;)

Do it this way ...

---

### Post by Rikeshar on 2011-07-11
Hm... okay, so that's done. However, hulu needs to know where to find libflashplayer.so, and I'm not entirely sure where it is now! It was in the /var/lib  directory. I have a /var/lib/flashplayer-installer   but there's nothing in that directory.

(I had to install the "flashplugin-installer" package in order for the flashplugin-nonfree to install)

---

### Post by Rikeshar on 2011-07-11
I apologize, it was in that directory. However, it's still a little choppy :( Maybe it's not a problem with Flash then :(

---

### Post by lovinglinux on 2011-07-11
Install [Flash-Aid](http://ubuntuforums.org/showthread.php?t=1491268) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues. 

I don't have Hulu, since I do not live in the US, so I cannot test it. However, since I am the Flash-Aid developer, I can help you if you experience any issues.

About the path required for Hulu, you can see it in the removal step of Flash-Aid or you can type **about:config** on the address bar, then type **plugin.expose_full_path** in the filter and double click the result to make it true. Then type **about[noparse]:[/noparse]plugins** in the address bar. It will show the plugin path information.

---

### Post by Rikeshar on 2011-07-11
Ah! This looks very familiar, I remember something about installing the beta flash, and I wonder if this was how. I've done so, and am just looking for the libflashplayer.so to tell Hulu Desktop where it is.

EDIT: WOOHOO! That did it. Thanks so much for the help!

---


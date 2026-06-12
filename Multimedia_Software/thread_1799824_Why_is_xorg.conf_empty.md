---
title: "Why is xorg.conf empty?"
date: 2011-07-08
forum: Multimedia Software
---

### Post by Luke M on 2011-07-08
This is my complete /etc/X11/xorg.conf file after a fresh install of ubuntu 11.04 (graphics card: nvidia 6200):

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

As you can see it is almost empty. It doesn't look anything like other xorg.conf files I've seen. There is no "driver" line, for example.

I can generate an xorg.conf file by running "nvidia-settings". Then I get an xorg.conf file that looks normal. But how does the system work with an empty xorg.conf? Where is it getting the information?

---

### Post by dasan on 2011-07-08
I think its normal.
In my machine with built-in nvida chip set it used to come like that. 
but after installing nvida driver and saving configuration it fill be look like other xorg files.

---

### Post by Luke M on 2011-07-08
The nvidia driver is already installed and working (ubuntu installed it automatically).

---

### Post by Yellow Pasque on 2011-07-08
> **Luke M said:**
> But how does the system work with an empty xorg.conf? Where is it getting the information?

Automatic detection..

---

### Post by Grenage on 2011-07-08
> **Luke M said:**
> This is my complete /etc/X11/xorg.conf file after a fresh install of ubuntu 11.04 (graphics card: nvidia 6200):

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

As you can see it is almost empty. It doesn't look anything like other xorg.conf files I've seen. There is no "driver" line, for example.

I can generate an xorg.conf file by running "nvidia-settings". Then I get an xorg.conf file that looks normal. But how does the system work with an empty xorg.conf? Where is it getting the information?

These days you'll normally only find information in xorg.conf if it has been entered by a user, or by a driver utility (such an nvidia-settings).  If you put anything in that file, it *will* be used; it's handy when things aren't detected properly.

---

### Post by Luke M on 2011-07-08
> **Grenage said:**
> These days you'll normally only find information in xorg.conf if it has been entered by a user, or by a driver utility (such an nvidia-settings).  If you put anything in that file, it *will* be used; it's handy when things aren't detected properly.

Hmm. Well, I followed the instructions here:

[http://ubuntunation.blogspot.com/2009/11/howto-rotate-screen-in-linux-using.html](http://ubuntunation.blogspot.com/2009/11/howto-rotate-screen-in-linux-using.html)

And it did not work. I had to generate an xorg.conf file using nvidia-settings before I could add the option.

---

### Post by dasan on 2011-07-08
Thanks for your info Grenage

---

### Post by Grenage on 2011-07-08
No problem.  There are so many old guides out there, and people reading them don't realise that the modern desktops take care of it all automatically now; most of the time, at least.  There's also xrandr for a more on-the-fly configuration.

---


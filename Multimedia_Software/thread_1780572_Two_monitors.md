---
title: "Two monitors"
date: 2011-06-12
forum: Multimedia Software
---

### Post by [compactwelve] on 2011-06-12
Hello there

I'm using an ATI Radeon HD series card and I'm using the open-source drivers for it (I found FGLRX to be a real pain). I also have two monitors and a program which configures those. However, I have to set up these two monitors every time I log in or restart X, which works but is obviously a tad inconvenient. I've looked up various methods on how to get this automatically configured and it all seems to involve Xorg.conf. That's okay, but there's a small problem: I don't have an Xorg.conf! 

I've tried to reconfigure. Nothing. I tried to create my own Xorg with all of the variables I need. Xubuntu then proceeds to bite my face off (or just give me an error message saying that Ubuntu needs to run in low graphics mode). 

I'm not sure how to proceed. Any ideas?

Edit: I'm not using Breezy 5.10, actually. I'm using 10.04 LTS and I haven't bothered updating my profile to reflect this ;)

---

### Post by Toz on 2011-06-12
The xorg.conf file is being deprecated (though it still works if its present). Xorg is very capable of auto-detecting hardware. In cases where you may want to fine-tune the configuration, the new default location for these configuration files is /usr/share/X11/xorg.conf.d.

What is this program that you use to configure the dual monitor? Would it work if you placed it in xfce's autostart?

---

### Post by [compactwelve] on 2011-06-12
> **Toz said:**
> The xorg.conf file is being deprecated (though it still works if its present). Xorg is very capable of auto-detecting hardware. In cases where you may want to fine-tune the configuration, the new default location for these configuration files is /usr/share/X11/xorg.conf.d.

What is this program that you use to configure the dual monitor? Would it work if you placed it in xfce's autostart?

Okay.

The program is grandr, and I'm not sure. Let me try that and see if it works.

---


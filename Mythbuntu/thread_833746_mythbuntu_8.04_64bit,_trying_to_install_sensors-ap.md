---
title: "mythbuntu 8.04 64bit, trying to install sensors-applet"
date: 2008-06-18
forum: Mythbuntu
---

### Post by gsrcrxsi on 2008-06-18
so i installed lm-sensors and configured it. then i installed sensors-applet. but when i try to add it to the panel "Hardware Monitor Sensors" is not in the list. i've tried rebooting and loging out and loging back in, but still its not there. any help would be appreciated!

note: lm-sensors works, running sensors in the terminal outputs everything in the window fine, its the applet im having trouble with. is there a reason why its not in the list? i didnt have this problem with 7.10

---

### Post by gsrcrxsi on 2008-06-18
thanks. but im moving on to 8.04. i want it to work in 8.04. anyone else?

---

### Post by superm1 on 2008-06-19
sensors-applet is intended for a gnome panel.  If you are using xfce (the default in mythbuntu 8.04), you likely won't be able to use it in the xfce panel.

---

### Post by gsrcrxsi on 2008-06-19
thats unfortunate :( i really like how fast XFCE is and how slimmed down it is. i dont need all that other stuff that comes with a full gnome desktop, nor do i want it. any suggestions? are there any applets for XFCE. i was very happy with sensors applet on my previous install and i want/need something with real time readout (watercooled/overclocked, i NEED to keep tabs on temps), i just want a less bloated desktop this time.

---

### Post by jb5 on 2008-06-19
Not quite the same as lm-sensors applet, but I have used both conky and gkrellm.

You can configure it to include the OPs you want.

There are LOADS of config files out there for both programs to get you started.

HTH

---

### Post by tgm4883 on 2008-06-19
+1 for conky

---

### Post by gsrcrxsi on 2008-06-20
i got sensors applet to work. apparently all i needed was a plugin that allowed the use of gnome applets on the xfce panel.

---

### Post by BigWoop on 2008-11-28
> **gsrcrxsi said:**
> i got sensors applet to work. apparently all i needed was a plugin that allowed the use of gnome applets on the xfce panel.

So what's the plugin you used? I'm in the same boat.

---


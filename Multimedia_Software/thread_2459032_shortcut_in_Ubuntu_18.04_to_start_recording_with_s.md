---
title: "shortcut in Ubuntu 18.04 to start recording with simplescreenrecorder"
date: 2021-03-09
forum: Multimedia Software
---

### Post by thosecars822 on 2021-03-09
Hello

I would like to make a keyboard shortcut in Ubuntu 18.04 that does the following in the same order:

1st.  pactl load-module module-loopback 

2nd. launching simplescreenrecorder

3rd. starting to record within simplescreenrecorder with simplescreenrecorder's default settings. With default settings I mean those that can be found when I launch the app and start recording manually.

Does anyone know how to do this?

Thanks

---

### Post by yancek on 2021-03-09
I don't use keyboard shortcuts so my first question is, are you familiar with the process?  The page at the link below explains that.

[https://www.geeksforgeeks.org/step-by-step-guide-to-add-custom-keyboard-shortcut-in-ubuntu/](https://www.geeksforgeeks.org/step-by-step-guide-to-add-custom-keyboard-shortcut-in-ubuntu/)

I would think your first step would be to create a script which performs the steps you want and test that before trying to make a shortcut pointing to the script.

---

### Post by thosecars822 on 2021-03-09
> **yancek said:**
> I don't use keyboard shortcuts so my first question is, are you familiar with the process?  The page at the link below explains that.

[https://www.geeksforgeeks.org/step-by-step-guide-to-add-custom-keyboard-shortcut-in-ubuntu/](https://www.geeksforgeeks.org/step-by-step-guide-to-add-custom-keyboard-shortcut-in-ubuntu/)

I would think your first step would be to create a script which performs the steps you want and test that before trying to make a shortcut pointing to the script.
Thanks for your answer but I already knew how to create a shortcut in Ubuntu. 

What I do not know is how should I proceed to create the script.

---

### Post by yancek on 2021-03-09
I don't use the software you are discussing so can't give specifics so just run each command to perform the step from a terminal, make note of each command which succeeds and you can then put the commands in a simple bash script separated by ( ; ) semi-colons.  If you know how to perform each action separately, it should be fairly simple.  Can't help anymore as I don't use or have the softwware installed.

---

### Post by thosecars822 on 2021-03-10
> **yancek said:**
> I don't use the software you are discussing so can't give specifics so just run each command to perform the step from a terminal, make note of each command which succeeds and you can then put the commands in a simple bash script separated by ( ; ) semi-colons.  If you know how to perform each action separately, it should be fairly simple.  Can't help anymore as I don't use or have the softwware installed.
Thanks for your effor but even though launching simplescreenrecorder is easy from terminal just by typying simplescreenrecorder, I do not know how to start the recording process from a terminal. May be someone else knows how to do this.

---

### Post by ajgreeny on 2021-03-10
I don't have that recorder either but does ***man simplescreenrecorder*** give you any clues about starting and stopping recording commands?

---

### Post by T6&amp;sfpER35% on 2021-03-10
> [COLOR=#000000]I do not know how to start the recording process from a terminal[/COLOR]
```
simplescreenrecorder --start-hidden --start-recording
```

don't know if this what you looking for?

OP's title says he wants a keyboard shortcut, then he says he knows how to use shortcuts,he wants a script to start it from terminal. so i'm confused.
or are you going this route?> [COLOR=#000000]I would think your first step would be to create a script which performs the steps you want and test that before trying to make a shortcut pointing to the script.[/COLOR]

---

### Post by deadflowr on 2021-03-10
*Thread moved to **Multimedia Software***

---


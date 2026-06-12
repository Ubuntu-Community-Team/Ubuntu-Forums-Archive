---
title: "Ubuntu 10.10 keeps crashing"
date: 2010-09-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by pkchips on 2010-09-13
I don't know how to find out what it is that's causing my crashes, and wanted some help.

My Ubuntu seems to randomly crash, sometimes very frequently, and I can't figure out what's causing the crashes. The screen will just go black, with a small cursor at the top left (which isn't blinking). The mouse cursor will also be present, but I can't move it.

Ctrl+Alt+Del does not work and the computer is completely unresponsive.

I tried using memtest to see if the RAM is a problem, but the memory was fine.

---

### Post by pkchips on 2010-09-13
Is there any debugging or logging software that might help?

---

### Post by Joe of loath on 2010-09-13
Considering it's a beta release, it's probably a software bug. Do they keyboard lights flash? Can you ctrl-alt-F1 to a different virtual terminal?

---

### Post by pkchips on 2010-09-13
> **Joe of loath said:**
> Considering it's a beta release, it's probably a software bug. Do they keyboard lights flash? Can you ctrl-alt-F1 to a different virtual terminal?

I can't remember if the keyboard lights are flashing, but the caps lock and scroll lock lights do come on.

Going to another virtual terminal doesn't work - I tried that too.

I understand that it's a beta release - I just want to identify the source of the crashes so I can report it before the final release.

---

### Post by rcayea on 2010-09-13
These sites might help:

[http://www.ibm.com/developerworks/linux/library/l-debug/](http://www.ibm.com/developerworks/linux/library/l-debug/)
[http://www.scribd.com/doc/3009706/Debugging-Linux-Applications](http://www.scribd.com/doc/3009706/Debugging-Linux-Applications)

---

### Post by pkchips on 2010-09-13
> **rcayea said:**
> These sites might help:

[http://www.ibm.com/developerworks/linux/library/l-debug/](http://www.ibm.com/developerworks/linux/library/l-debug/)
[http://www.scribd.com/doc/3009706/Debugging-Linux-Applications](http://www.scribd.com/doc/3009706/Debugging-Linux-Applications)

Wow :O that looks really complicated. Thanks though, but as I don't have a programming background, I don't think I can do that.

I found this:

[http://ubuntuforums.org/showthread.php?t=644232&highlight=random+freezes](http://ubuntuforums.org/showthread.php?t=644232&highlight=random+freezes)

How might I go about booting with a "noapic" parameter?

Also, the problem does not happen in windows XP.

---

### Post by Mark Phelps on 2010-09-13
It's a beta release.  If you're not an experienced Ubuntu user, you have no business messing around with a beta release.

Also, for tech support on beta versions, you should be posting in the proper Beta forum, not this one.  

In this case, go look at the Maverick Development forum.  You may find some threads there dealing with this problem.

---

### Post by Elfy on 2010-09-13
moved

---

### Post by pkchips on 2010-09-13
> **Mark Phelps said:**
> It's a beta release.  If you're not an experienced Ubuntu user, you have no business messing around with a beta release.

LOL, oh ok, well sorry... I didn't realise that beta releases were exclusively for Ubuntu veterans. 

Thank you for your immense wisdom on this topic, I guess I shall stop using all beta versions of products that I have not had at least 10 years of experience with in future. Oh silly me, I never realised how misguided I was when I thought of going to play that Starcraft beta or CnC 3 beta. And oh, thanks to your wisdom, I now realise how massively wrong of me it was to use the Office 2010 beta on my phone and PC.

I've been using Ubuntu since 9.04. I'm not a programmer, but I have navigated my way around various difficulties in the past.

> **Mark Phelps said:**
> Also, for tech support on beta versions, you should be posting in the proper Beta forum, not this one.  

In this case, go look at the Maverick Development forum.  You may find some threads there dealing with this problem.

Mod: Thank you for moving the thread - I didn't know this forum existed.


As for the problem, it's suddenly stopped happening all by itself... if it starts recurring, I will try and find out whats going on.

---

### Post by exploder on 2010-09-13
> As for the problem, it's suddenly stopped happening all by itself... if it starts recurring, I will try and find out whats going on.

I am glad the crashes stopped for you. :D The system logs might hold clues to what was happening before. Some problems are difficult to pin point, usually someone will throw some ideas out there to check out. You don't have to be a seasoned veteran to test, just some patience. Hope for the best but expect the worst and you will find your way through any development cycle. :)

---

### Post by ktp on 2010-09-13
> **pkchips said:**
> LOL, oh ok, well sorry... I didn't realise that beta releases were exclusively for Ubuntu veterans. 

they are not...great learning experience.  I started out with alpha years ago and stay with it since you learn so much about the os.

---


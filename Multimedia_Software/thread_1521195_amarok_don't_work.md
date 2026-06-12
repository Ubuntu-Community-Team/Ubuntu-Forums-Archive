---
title: "amarok don't work"
date: 2010-06-30
forum: Multimedia Software
---

### Post by alenn on 2010-06-30
when I try to play music on amarok it just won't play, it just loads lyrics and then, nothing. on rytmbox everthing works fine but amarok don't work. help

---

### Post by khelben1979 on 2010-06-30
Have Amarok worked okay before on that Ubuntu system? Also, what version of Amarok are you using?

[Amarok F.A.Q]("http://amarok.kde.org/wiki/FAQ")

---

### Post by alenn on 2010-06-30
Version 2.3.0
Using KDE 4.4.2 (KDE 4.4.2)

and this is the first time I'm using amarok

---

### Post by alenn on 2010-06-30
heeeeeeeeeeeeeeeeeeeeeeeeelp

---

### Post by khelben1979 on 2010-06-30
Did you read the F.A.Q?

Also, you can try and reinstall Amarok from Synaptic Package Manager to see if it helps.

---

### Post by alenn on 2010-06-30
You need to test the sound frameworks at the command line:
%xine-check
(The Package xine-ui contains xine-check)
The output from these commands should help you identify the problems you are having and how to fix them.



can you explain me what to do, I typed that text in terminal and it says thaz command does not exist, so how to test sound frameworks using that command.

---

### Post by alenn on 2010-06-30
I reinstaled amarok and it's the same

---

### Post by khelben1979 on 2010-07-02
```
sudo apt-get install xine-ui
``` installs the needed package so you can use xine-check, according to the output from your post.

You can also try with ```
man amarok
``` to see if they got something on that. If the GUI messes up the application but the sound engine works without it, then that would be the way to go (I mean using amarok without GUI if it's possible). Not sure if that would help though but it would not damage anything if you try it. ;)

---

### Post by alenn on 2010-07-03
> **khelben1979 said:**
> ```
sudo apt-get install xine-ui
``` installs the needed package so you can use xine-check, according to the output from your post.

You can also try with ```
man amarok
``` to see if they got something on that. If the GUI messes up the application but the sound engine works without it, then that would be the way to go (I mean using amarok without GUI if it's possible). Not sure if that would help though but it would not damage anything if you try it. ;)

it works fine now, thank you :)

---

### Post by khelben1979 on 2010-07-03
Okay! Good that you got it working! :)

Also, you should mark the thread as solved using the thread tools button.

---


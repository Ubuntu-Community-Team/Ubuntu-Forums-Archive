---
title: "[SOLVED] Where is the Master Volume Control ?!?"
date: 2008-06-18
forum: Multimedia Software
---

### Post by AJSB on 2008-06-18
Hello,
I installed Xubuntu in another comp but in Xubuntu i can't seem to find the Master Volume Control like i can in Ubuntu or Kubuntu !!!

I want to customize volume for headphones, PCM, Mic, etc, and can't !!!

TIA,
AJSB

---

### Post by kpkeerthi on 2008-06-18
You can always use alsamixer from command line (not sure if there is a graphical app in xubuntu)

Open a terminal and type **alsamixer**

- Use left/right arrow keys to navigate
- Use up/down arrow keys to raise volume
- Press 'm' key to toggle mute
- Press 'Esc' to quit.
* Easy *

---

### Post by AJSB on 2008-06-18
Thanks for you help but i found myself a way to have the graphical tool:

1- right click in a empty place of the bar in the button of the screen (Task List ?)
2- select "Add New Item"
3- From the scroolable list choose "Volume Control" and click on "+Add"
4-  Select: Device: Default...
    and make sure that WannabeMaster is Master.0 and that field "When clicked" reads "xcfe4-mixer" or similar thing....click on "Close" and it's done :D

Regards,
AJSB

---

### Post by Ompsksch on 2008-12-25
Everything's set like you describe it, but the volume is always full blast (even though the volume icon shows control from 0-100%). Hmmm...

---


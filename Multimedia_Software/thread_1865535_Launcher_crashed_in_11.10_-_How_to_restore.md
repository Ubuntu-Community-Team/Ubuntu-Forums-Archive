---
title: "Launcher crashed in 11.10 - How to restore??"
date: 2011-10-20
forum: Multimedia Software
---

### Post by wildwildebeest on 2011-10-20
Dear all,

I have just upgraded from 11.04 to 11.10. 

Everything seemed fine at first, but after changing a few settings in CompizConfig (nothing major, just changing the number of desktops or something like that), CompizConfig crashed.
Then the launcher disappeared, along with most of the buttons on the top panel! Only the File>>Help tabs remain, no shutdown buttons or anything. Also, the bars at the tops of windows now have the title and File, Edit (etc) tabs on 2 separate lines, instead of the new format where hovering over the bar switches which is visible.

I have since been using Ctrl+Alt+T to open a terminal and open applications, shut down, etc, from there.

I have typed in the command 
unity --reset 
which has some effect, but the terminal never reaches the end of the task.
I've also done apt-get update, which completed fine.

Can anyone help me restore the launcher and panel functions?? I am getting most frustrated by the fact that once I have used the terminal to open Firefox, I can't do anything else with it!


Many thanks!
Will.

---

### Post by libertao on 2011-10-20
Try ctrl+alt+t to bring up terminal, type ccsm, then enter, then go to Desktop option on the left, then enable Unity plugin (hopefully that was not enabled).  I selected "resolve conflicts" and selected every following one in favor of Unity.  Immediately brought back the launcher.

---


---
title: "Lirc remote settings wrong for my remote"
date: 2008-11-06
forum: Multimedia Software
---

### Post by AndrewWalker on 2008-11-06
I've upgraded my Kubuntu MythTV box to Intrepid and the remote control for my Hauppauge Nova-T doesn't work again. The remote control is the same as for an HVR-1300 card and it works for all buttons except the back/exit button. 
The problem existed on previous versions but could be fixed by editing the file /usr/share/lirc/remotes/hauppauge/lircd.conf.nova-t and editing the control code for that button but that fix no longer works with Intrepid.
It looks like the code is now actually correct in Intrepid but the same error seems to exist. Every other button works correctly but MythTV is unusable without that button working on the remote.
I also get strange results from irw, I'm sure I used to get codes for buttons displayed but now I just get characters from the remote displayed such as the digits from the number buttons.
Any suggestions because I'm pulling my hair out here!

---


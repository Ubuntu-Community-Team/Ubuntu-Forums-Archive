---
title: "remote actions doubled"
date: 2011-08-06
forum: Mythbuntu
---

### Post by danomano on 2011-08-06
I'm not sure whats going on..I have confirmed with ircat
that it is reporting 1 button press, yet when ever I do anything in the mythtv it acts as if I pressed the button twice.

any pointers?

Its configured for the Windows Media IR Receiver, and both the my Universal remote and the original Windows Media Center do the same thing.

---

### Post by danomano on 2011-08-06
For Grins and Giggles I tried re-configuring it has Hauppage Remote.

Well the directional Navigation buttons all work correctly..but..thats it :(

---

### Post by benlyboy on 2011-08-07
Hi

I think you will find this thread helpful...

[http://ubuntuforums.org/showthread.php?t=1595018]("http://ubuntuforums.org/showthread.php?t=1595018")

In short reading through this the problem is that your remote (most likely a streamzap) is an input for xinput and lirc. This means it is seen as a keyboard and a remote at the same time.

The easiest way to fix this maybe to commenting out some of the buttons that are giving you the issue in ~/.lirc/mythtv or whatever file is appropriate for you in the ~/.lirc/ folder.

---


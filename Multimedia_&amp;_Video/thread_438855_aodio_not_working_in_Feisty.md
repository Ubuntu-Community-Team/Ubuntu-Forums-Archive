---
title: "aodio not working in Feisty"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by leo246 on 2007-05-10
Hi all

I have recently installed Feisty, and all appears to be working fine, except for the sound.  When logging on, the sound works, but when clicking on the volume control button, it gives the following msg:

[COLOR="Blue"]No volume control GStreamer plugins and/or devices found.[/COLOR]

I have checked the sound option under:  System ->  Preferences -> Sound, and find my card under all the lists as:

[COLOR="Blue"]Intel 82801AA-ICH[/COLOR]

but when clicking on test, I get the following msg:

[COLOR="Blue"]audiotestsrc wave=sine freq512 !
audioconvert ! adiosample ! gconfaudiosink:
Could not open resource for writing.[/COLOR]

As I am new to linux/Ubuntu, I was wondering if anyone can help me in order to resolve this issue.  I have updated the gstreamer plugins and installed the latest verion.


Kind Regards
Leo

---

### Post by Kobalt on 2007-05-10
Hello,

Have you tried this : [https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

---

### Post by leo246 on 2007-05-12
Hi

I think I have fixed the issue.  It seems like the username I use to log in with does not have rights to the sound.  I used Webmin and assigned certain groups to the account, and VIOLA!  


Thanks for advise, but did not resolve issue, only helped me dig a bit deeper, and get familiar with Ubuntu....



Great stuff
Leo

---

### Post by chewjoel on 2007-05-17
stupid question but how do you assign the (sound) rights for users?

---


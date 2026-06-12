---
title: "Sound isn't working as fresh install"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Yusayoh on 2007-03-27
Hello,
this has been my third Ubuntu install over the course of the last few months as I have switched back from Windows and Ubuntu a lot. Two of the three (including this time), the sound has not worked immediately. I've followed the sound tutorials and such through google and the forums, but to no luck.

Can anyone help me get my sound to work?
Thank you! =D

---

### Post by deadgobby on 2007-03-27
Sure,  what version of Ubie are you using and what is your system specs?

---

### Post by Yusayoh on 2007-03-27
Ubuntu Edgy 6.10
nVidia Geforce 5200 (I believe)
2.66GHz
512MB Ram

And I forgot my soundcard but Ubuntu tells me its Intel IE5 I believe.

---

### Post by deadgobby on 2007-03-27
If you are still running Ubie, can you open up the terminal and copy and paste this command in 

sudo asoundconf list

And post the reply.

Gobby

---

### Post by Yusayoh on 2007-03-27
Names of available sound cards:
ICH5

---

### Post by Zoandar on 2007-03-27
I am having the exact same problem with an ICH6 soundcard. Mind if I tag along?
I have tried a lot of things off different forums today, but had no luck at all. 

What kind of computer are you using? I am using an HP DV1000 series notebook.

The Ubuntu version I am using is 6.10, installed from a LiveCD ISO. Are you using the same version?

---

### Post by Yusayoh on 2007-03-27
I'm using a Dell Pentium 4 Dimension desktop.

Yup same version, freshly burned last night.

---

### Post by pureblood on 2007-04-10
I have this possible workaround. Since I don't know why it works it might not work for you, so don't expect this as a solution. If I run the command "lspci|grep audio" I get:
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
When I upgraded the machine to Debian 4.0 (etch, with kernel 2.6.18 and alsa 1.0.12rc1) the sound wasn't working anymore but the computer wasn't really noticing it. By changing the switch "Line Jack Sense" from On to Off the sound came back working (the microphone is not working though).
You can change the switch by either going on the Switches section in the KMix application or with the program alsamixer (when you get to the "Item: Line Jack Sense" press the "m" key to turn this switch Off).
I hope this helps.

---


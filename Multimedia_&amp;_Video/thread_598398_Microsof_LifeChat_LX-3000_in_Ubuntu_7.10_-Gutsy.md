---
title: "Microsof LifeChat LX-3000 in Ubuntu 7.10 -Gutsy"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by Biggy on 2007-10-31
I have Lifechat LX-3000 Headset USB but in Ubyntu Gutsy doesnt work, i install all alsadriver and only pc speaker work .......

someone help me for configure alsa driver ...!!!??

thnx

sorry for my bad english ... :)


help!!!!

---

### Post by Biggy on 2007-11-27
I have problem with the connection Microsoft lifechat LX-3000, they don't work. What I have to do? help please !!

---

### Post by FLCLFan on 2007-12-25
I just got these, so ummmm im going to BUMP THIS.

Anyone know how to get this to work?

---

### Post by Kheter on 2007-12-25
Just install from apt-get asoundconf-gtk and use that to choose your sound device (USB sound device are splitted from your default sound card).
It worked for me flawlessly with those headset and Gutsy. Using Micro$oft's headphone on Linux is pretty weird, but they're a gift :D

---

### Post by FLCLFan on 2007-12-25
Yep mine was a gift :D

But i figured this out, i just changed my sound prefs and put "USB Audio" for what I want.

---

### Post by oneloveamaru on 2008-03-23
If a program is not using the lifechat headset, it's because your built in sound card is the default. A program usually uses that unless it has an option to use a different one, like xmms. If you want to make it default, follow the directions here. [http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem]("http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem")

You need to scroll all the way down to **Configuring default soundcards / stopping multiple soundcards from switching** section.

---


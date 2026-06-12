---
title: "I have gotten no answers Active directory Share"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by ronw69 on 2012-02-13
I posted this 3 days ago in both [Networking & Wireless]("http://ubuntuforums.org/forumdisplay.php?f=336") and in [[IMG]http://ubuntuforums.org/images/buttons/collapse_thead.gif[/IMG]]("http://ubuntuforums.org/#top")[**Absolute Beginner Talk**]("http://ubuntuforums.org/forumdisplay.php?f=326") forums and I have gotten no one to post any info.  Is this question that difficult or am I wording the question incorrectly?  I really need to get some idea of how to resolve the problem.

I have many Xbuntu clients they log on to a Active directory network with Likewise. All of these clients could have any of 100 different users log on to them at any time. I need to map the users AD share automatically on the desktop or in GVFS places. I have tried using the gvfs-mount command but it calls for entering the users name and password. I have thought of creating a bash file and using the mount command with the USER global variable but I am not aware of a global variable for the password.

---

### Post by silverglade00 on 2012-02-13
That sounds like a good question for the Server section. As for the password, I am just guessing here, but it seems you could do something with the keyring so when they log in, it will unlock their keyring and use the credentials in there. This way, they will only need to provide that password once on their very first login.

---

### Post by ronw69 on 2012-02-13
Thank you Silverglade00 I will re-post this under server and will read up on keyring.  Thank you again for the response, I was at a dead end and this will give me a place to start again.


Ron W.

---


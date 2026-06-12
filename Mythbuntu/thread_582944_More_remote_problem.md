---
title: "More remote problem"
date: 2007-10-20
forum: Mythbuntu
---

### Post by axelsvag on 2007-10-20
I have a very succesfull install of the RC. Everything worked perfectly apart from the xmltv problem. I tried everything I could think of so at last I went to synaptic to install the lost xmltv. Everything worked find until the end when the installer asked me if I wanted to install a remote to my system. As I already had done that and it worked as i should I choosed not to. When I then went back to the frontend the remote was dead. The diod indicated that the ir receiver was sending signals but nothing entered the system. I tried irw but nothing happened sp it seems that something is broken. Does anyone have any idea how to fix this. As I rmebered the same thing have happened when I tried Gutsy RC a few days ago also.

---

### Post by axelsvag on 2007-10-20
Ok now I made a new fresh install. I did not load the xmltv through synaptic but just used the update manager. This time the question about the remote came again. And this time I used the yes option and used the mceusb2 driver. And to to my surprise the remote was gone again. So the problem don´t seem to have anthing to do with the xmltv download but with the update. Now I have to make a new fresh install because the "lirc gutsy" manual dont work. When I choose the command  "sudo apt-get install lirc" or " DEBIAN_FRONTEND=gnome sudo apt-get install lirc"  the manager refuses to start. So this time I will try not to configure the remote during install and wait until the uppdate is finished. Or does anyone have any suggstions??

---

### Post by axelsvag on 2007-10-21
I can´t say I have solved the problem.... but this morning when I restarted the system everything worked as it should. I don´t have any clue what has changed but I am glad anyhow.

---


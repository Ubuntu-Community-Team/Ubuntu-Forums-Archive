---
title: "How do I Install ATI Drivers"
date: 2006-02-01
forum: Multimedia &amp; Video
---

### Post by jumiclads on 2006-02-01
I downloaded the drivers from ATI onto my desktop, started up the Terminal and enter the code as follows,  /home/michel/Desktop/ati-driver-installer-8.21.7-i386.run
 then press Enter it the replies with Permission Denied. Any Ideas?

---

### Post by tkjacobsen on 2006-02-01
See this post. Worked for me

[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+howto](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=ati+howto)

---

### Post by swong1 on 2006-02-01
[QUOTE=jumiclads]I downloaded the drivers from ATI onto my desktop, started up the Terminal and enter the code as follows,  /home/michel/Desktop/ati-driver-installer-8.21.7-i386.run
 then press Enter it the replies with Permission Denied. Any Ideas?[/QUOTE]

Try adding "sudo " in front of the command. Enter the root (administrator) password when prompted.

---

### Post by Thomas,Bakker on 2006-02-06
ok type the following in the terminal;

[COLOR="Red"]cd /home/michel/Desktop[/COLOR]
[COLOR="Red"]sudo sh ./ati-driver-installer-8.21.7-x86_64.run[/COLOR]

you can now use the graphical interface of the installer but that's only how far i got
not sure if its working now....... worth a trie though

---


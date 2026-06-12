---
title: "Uninstalling songbird,"
date: 2009-02-07
forum: Multimedia Software
---

### Post by Shpongle on 2009-02-07
i installed songbird using the script linked  and code below.
i find its too demanding on my system, so iv since went back to rhythmbox which is fast and lightweight, iv tried to remove it using synaptic pacakge manager and the add/remove progs option in the menu but it doesnt pick it up, iv searched for it and found it but i dont have permission to remove it, im not too familiar with the shell commands and i didnt wanna try any "rm" command in case i delete important sys files. i was wondering if someone could take a look at the script and advise me on the best way to remove it,

thanks in advance.....


>  Great sound prog
Songbird. Great mp3 and media player.

Download this script to desktop.

[http://www.psychocats.net/ubuntu/installsongbird.sh](http://www.psychocats.net/ubuntu/installsongbird.sh)


Then at terminal, run.
cd ~/Desktop
chmod +x installsongbird.sh
./installsongbird.sh


Carl.

---

### Post by mc4man on 2009-02-07
This is what you want to remove - 1 folder, 1 link and 2 files, delete what's shown in red if doing graphically ( using gksudo nautilus from a terminal and browsing there. If using gksudo nautilus you'll want to highlight the folder or file and use shift+delete or it will end up in the root trash


/usr/local/bin/[COLOR="Red"]songbird[/COLOR]
/usr/bin/[COLOR="Red"]Songbird[/COLOR]
/usr/share/pixmaps/[COLOR="Red"]songbird.png[/COLOR]
/usr/share/applications/[COLOR="Red"]songbird[/COLOR].desktop

(if you want to use a rm command than the last one will need full name - songbird.desktop

---

### Post by Shpongle on 2009-02-07
Thanks for that mc4man , it worked fine!!=D>

---


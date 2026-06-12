---
title: "plex help"
date: 2012-04-10
forum: Multimedia Software
---

### Post by hedoe on 2012-04-10
im running 11.10 64-bit and im trying to install plex
but when i use the
sudo gedit /ect/apt/sources.list
command i get a black window with no text or list in it
any ideas on how to fix this?
thanks

---

### Post by FatFrog on 2012-04-10
What happens when you try vim?

#sudo vi /etc/apt/sources.list.

---

### Post by FatFrog on 2012-04-10
Also, PLEX is awesome! I havent found anything I like better for my media...

---

### Post by hedoe on 2012-04-10
this
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1015_42_28.png[/IMG]

---

### Post by hedoe on 2012-04-10
someone suggested trying something else
so i did and this is what i got
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1017_12_18.png[/IMG]

---

### Post by hedoe on 2012-04-10
so ive done some exploratory surgery
[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1017_22_49.png[/IMG]

[IMG]http://i107.photobucket.com/albums/m294/hedoe/Screenshotat2012-04-1017_23_59.png[/IMG]

so should i just manually update the file?
which one?
there are 3
and what happens if i still cant save it?
thanks guys

---

### Post by FatFrog on 2012-04-10
if you run a 
#locate sources.list
do you see an entry for '/etc/apt/sources.list'

If you don't see it, i'll have to research and see if that .distUpgrade version is going to be what you are lookling for. If it is, add the repository to that file.
Then I would find out how to fix that file name and make the correct symbolic link for /etc/apt/sources.list ...

---

### Post by oldos2er on 2012-04-10
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=1956150](http://ubuntuforums.org/showthread.php?t=1956150)

Please don't start more than one thread per topic.

---


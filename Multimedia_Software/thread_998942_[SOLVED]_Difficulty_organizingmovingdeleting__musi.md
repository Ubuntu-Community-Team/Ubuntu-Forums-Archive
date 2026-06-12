---
title: "[SOLVED] Difficulty organizing/moving/deleting  music files"
date: 2008-12-01
forum: Multimedia Software
---

### Post by poetstorm on 2008-12-01
Hi! :) Still getting the hang of Ubuntu here, have only had it installed for maybe a week and a half now. I love it but need help with a few little things that I'm sure will be a piece of cake for you guys. I did search for my problem but so far nothing has matched up completely. 

I moved all my music over to my Ubuntu computer. It is on my main Ubuntu drive now under my Music directory.

I have noticed two things. Forst there are image files of album covers suddenly mixed up with my music. Second when I go to delete the album covers, it won't move to trash or permanently delete. Also I can't move any of these music files around to other folders/directories. I can't seem to organize my music but I can delete other files so I don't think it is a whole hard drive permissions problem. 

I can also delete files downloaded with Limewire so I don't think it is affecting all music, just the folders copied over from my old Windows machines that have album pics. (Also I never noticed these image files in Windows. I wonder why.) They were coped over our home network wirelessly if that helps. 

Any idea what I can do to get permission over moving these files, and also how to get rid of the album cover images? It makes it very hard to browse my music. Thanks!

---

### Post by benson444 on 2008-12-01
You could restore all the permissions within the Music directory to the default permissions for created directories and files. I'm supposing that the Music folder is /home/username/Music.

Open a terminal (Applications > Accessories > Terminal) and enter these commands.

Change to your home directory:
```
cd ~
```

Make sure you are in the right place by checking that the Music directory appears in a listing of the current directory:
```
ls
```

Change the owner and group permissions of all the subdirectories and files in Music to your username:
```
sudo chown -hR username:username Music
```

Search through Music and change permissions of all subdirectories to 755:
```
find Music -type d -exec chmod 755 {} \;
```

Do the same for normal files but change to 644:
```
find Music -type f -exec chmod 644 {} \;
```

---

### Post by poetstorm on 2008-12-02
Ah, thank you very much. 

I thought it wasn’t a permissions problem because it only affected certain files in the same directories but I see you are right now. 

I found a way to change permissions with the graphic GUI file browser but I’m gonna do it your way just for practice and to get used to the Linux terminal commands. Thanks a lot!

---


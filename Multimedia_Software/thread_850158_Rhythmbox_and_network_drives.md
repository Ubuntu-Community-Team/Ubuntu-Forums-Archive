---
title: "Rhythmbox and network drives"
date: 2008-07-05
forum: Multimedia Software
---

### Post by chrisod on 2008-07-05
I have all my music files on a NAS drive and uses Rhythmbox. It works just fine, except when the network connection drops. If I open Rhythmbox and the network connection has failed for some reason, Rhythmbox dumps the entire music library. It's a not a huge deal as it will re-import once the network is back up, but it is annoying. 

Is there a way to make Rhythmbox fail more gracefully?

---

### Post by hughc1 on 2008-08-20
I have a Nas with music on it too, when the nas isn't available the music library used by rhymthm box goes away too. 
In an effort to stop this from happening I chose edit/preferences/Music and unchecked "watch library for new files".  I don't know if this helps or not.

---

### Post by dizzyhaha on 2010-01-23
having issues getting rhythmbox to connect to my network drives.  

running unbuntu 9.10, trying to connect to a netgear readynas duo on the network.  i can see the network music folder thru file browser, but in rhythmbox 
when i try to import folder, i don't even have the option to add the network folder, in fact "network" is not an option in "Places"  any ideas?

---

### Post by elliotbeken on 2010-06-03
i have the exact same problem as the last post i can see the folders just not through rhythmbox ?????

---

### Post by Boondoklife on 2010-06-03
Doesn't import copy it to a local folder? I know for me I just change the library location to the mapped network folder.

I wrote a script to help me manage my network drives [HERE]("http://ubuntuforums.org/showthread.php?t=1186877&page=8"), just edit the file to include your shares and put it into your startup applications. It will not fix the problem of the NAS being unavailable, but if your connection drops then it will automatically remap it for you.

The code is listed in one of my posts on the linked page.

---

### Post by canplaythegame on 2010-06-05
i too have a readynas duo
and i cant import files or folders from it
ubuntu 10.04 i think it is
i am very new at this non windows stuff
i can see the files and folders but nothing happens when i import them
i can play them through totem and vlc but cant play them in rhythmbox
just checked can also play in guayadeque
but cant figure out how to add the nas folder to the playlist
i am also new to networking so i dont quite understand all the numbers getting assigned just yet
i really like the rhythmbox program and would like to stay with it
i have searched forums and tried a lot of things that have worked for other peole but didnt help me
any help would be appreciated

thanks

daniel d

---

### Post by IBUA on 2010-06-05
I have the same problem too :(

---

### Post by canplaythegame on 2010-06-05
i found updates this morning when i woke up
and it is fixed now
they were proposed updates i think
so i did change something before about looking for proposed updates
cant remember where atm
but it is fixed for me now
importing folders as we speak

daniel d

---


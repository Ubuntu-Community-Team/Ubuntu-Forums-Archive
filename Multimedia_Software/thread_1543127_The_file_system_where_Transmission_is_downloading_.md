---
title: "The file system where Transmission is downloading files running out of space."
date: 2010-07-31
forum: Multimedia Software
---

### Post by correnticalde on 2010-07-31
I would not like to post a question or a problem, but a solution.
Just to help out on a problem I faced and others might face.

The problem:
The file system where Transmission is downloading files, and it is running out of space.

The solution:
Add another disk with enough space, create a new file system on the new disk, pause all downloads, move there all partially downloaded files to the new file system. In Transmission change the save to location preference to the new  file system, set location, verify local data, restart all downloads.

Step-by-step guide:
1. In the Transmission GUI pause all downloads:
        edit -> select all -> click on pause
2. Close the Transmission GUI
3. Open a Terminal, create the new folder and move there all the partially downloaded data:
        mkdir /media/disklabel/Downloads-external
    mv /home/yourhome/Downloads/* /media/disklabel/Downloads-external
       be patient might take a while.
4. Open the Transmission GUI, change the save to location preference:
        edit -> preferences -> torrents -> save to location -> select the folder at step 3.
5. In the Transmission GUI, select a file (one by one):
        torrent -> set location -> select "local data is already there" -> apply
       repeat this step for all the files you have.
6. In the Transmission GUI,select a file (one by one):
        torrent -> verify local data
       repeat this step for all the files you have.
7. All partially downloaded files are in the same status as before, but on a 
    edit -> select all -> click on start
8. Enjoy! ;o)

Cheers,

Fabrizio

---


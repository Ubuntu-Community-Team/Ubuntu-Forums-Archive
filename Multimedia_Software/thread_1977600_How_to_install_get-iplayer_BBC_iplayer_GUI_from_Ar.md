---
title: "How to install get-iplayer BBC iplayer GUI from Arch AUR in Ubuntu"
date: 2012-05-10
forum: Multimedia Software
---

### Post by SirPecanGum on 2012-05-10
I found this very nice GUI for get-iplayer in the Arch AUR: [https://aur.archlinux.org/packages.php?ID=59166](https://aur.archlinux.org/packages.php?ID=59166)

And a youtube demo of it here:                              [http://www.youtube.com/watch?v=2zruDXXr3Eo&feature=youtu.be](http://www.youtube.com/watch?v=2zruDXXr3Eo&feature=youtu.be)

Question:                                                   How can I install this in Ubuntu?

---

### Post by F1nchy on 2012-09-06
Did you find out how to install this?

---

### Post by SirPecanGum on 2012-09-06
No, I'm still using the command line for get-iplayer.

---

### Post by shantiq on 2012-09-06
deb [**here **]("http://sourceforge.net/projects/giplayer/files/giPlayer.deb/download?use_mirror=ignum&r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fgiplayer%2Ffiles%2FgiPlayer.deb%2Fdownload&use_mirror=ignum") designed by [mr Bob]("http://ubuntuforums.org/showpost.php?p=9845464&postcount=1")


download deb file and double click it will install through Ubuntu Software Centre


or place in your home folder and in terminal

```
sudo dpkg -i giPlayer.deb
```





then find under applications/sound and video

---

### Post by O2Blevel on 2012-09-06
Your link is not working.

---

### Post by F1nchy on 2012-09-06
No, doesn't seem to be working for me either. 

Does the rtmpdump thing that grabs the HD versions work as well?

[http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/)

---

### Post by shantiq on 2012-09-07
ok guys and sorry   corrected [**it now**]("http://sourceforge.net/projects/giplayer/files/giPlayer.deb/download?use_mirror=ignum&r=http%3A%2F%2Fsourceforge.net%2Fprojects%2Fgiplayer%2Ffiles%2FgiPlayer.deb%2Fdownload&use_mirror=ignum") and in earlier post

[ altho you could have got there following the second link :]]


also on newer ubuntu versions  it will install fine but tell you you have broken packages


no sweat there


go to synaptic after it is installed [will work fine anyway] and click on edit/fix broken packages/apply

then all good;   it is basic as a gui but clear and efficient

---

### Post by shantiq on 2012-09-07
> **F1nchy said:**
> No, doesn't seem to be working for me either. 

Does the rtmpdump thing that grabs the HD versions work as well?

[http://rtmpdump.mplayerhq.hu/](http://rtmpdump.mplayerhq.hu/)


ok for HD  need to update to 2.82 

so with [**PPA**]("http://ubuntuforums.org/showpost.php?p=12184083&postcount=4")


with [**deb**]("http://ubuntuforums.org/showpost.php?p=12215358&postcount=6")

---


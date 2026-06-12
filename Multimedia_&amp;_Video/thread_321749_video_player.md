---
title: "video player"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by huviduc on 2006-12-19
i am having trouble finding a video player that i am happy with. For some reason the only one that will play .avi files when i double click them is totem, but i am not happy with video play back and controls actually working well. Kaffiene and VLC player seem to be a little better but they wont open upon Double clicking, the give me this error 
"The filename "Beerfest[2006]DvDrip[Eng]-aXXo.avi" indicates that this file is of type "avi document". The contents of the file indicate that the file is of type "AVI video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "AVI video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. "

what video player do you guys use? which is the best for playing all different types of files and has good playback and controls that work well?

---

### Post by huviduc on 2006-12-19
i am sure someone has some input as to which video player they use and love

---

### Post by antofthy on 2008-07-01
I have been battling this problem for years, on and off. but no one seemed to have an answer.   However I have now finally found the solution in a 'fedora' forum.

The problem is that you personal 'mime' settings do not match the system mime settings.  I have no idea what cases this but it screws up my thumbnails and double-left clicking of AVI documents.  The solution is simple.
```
rm ~/.local/share/mime/globs
```
Now logoff and log back in.  Suddenly AVI's and even AVI thumbnailing is working properly!!!  :D

If this does not work you can also try running
```
update-mime-database /usr/share/mime
```
as the root user.   I myself did not need this.

PS: AVI thumbnailing in Fedora requires the "totem-xine" package from the livna repository.  No idea about this in Ubuntu.

---


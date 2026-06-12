---
title: "saving a change in nautilus actions?"
date: 2008-06-28
forum: Multimedia Software
---

### Post by prophetski on 2008-06-28
new to ubuntu, ive dual booted with windows a week ago ive been trying to get audacious to work as good as i am used to winamp working in windows and through this link [http://www.techthrob.com/tech/actionconfig.php](http://www.techthrob.com/tech/actionconfig.php) , installed nautilus actions and followed the instructions on the link. however at the end it didnt work and no change has been made to my right click window, i then noticed that it says *"Once I saved my new menu item"*. there doesnt seem to be a save or apply option in nautilus so im wondering what im doing wrong. any help would be greatly appreciated

---

### Post by mc4man on 2008-06-28
Are you r. clicking on a file or a folder. The way that how to sets up you won't get the option on folders. (by setting filename and mimetype in conditions. 
I use 3 r. click actions with Amarok, very easy to set up and because I want to use on both files and folders, I leave the filename and mimetypes at default
[http://ubuntuforums.org/showthread.php?t=830427](http://ubuntuforums.org/showthread.php?t=830427)  if your interested in amarok
screenshot - how your conditions should look

edit: screenie 2 -  how the main add should look (the icon they suggested may or maynot work, to set action after configuring just click ok

---

### Post by prophetski on 2008-06-28
i want the option to work on both folders and files, i tried what you advised using your  screenshots as a guide, it still doesn't work, when i right click this is what i get. thanks for the prompt reply to the last post

---

### Post by mc4man on 2008-06-28
I don't have audacious so I'm not sure if it'll work , that being said it should show up. From the top, go system -> preferences -> Nautilus Actions Configuration -> add. Make the menu item and action look like screenshot 2 and the conditions like screenshot 1. Click okay and try (maybe restart  Ctrl+Alt+backspace)

Edit: don't use your guides parameters (maybe)
if you want to just queue to a current list or queue to the player (no start) use the guides parameters
 if you want to add what you r.click on and to start (queue and start playback)  use this as parameter
```
-e -p %M
```

If you want to create a new temp playlist and start playing use this
```
-E -p %M
``` or you could create 2 or 3, experiment

redit - I'd probably make 2 at min.

-e -p %M - will start a new list or add to current and play,  (load and play)
-e %M  - will queue to current list added after last listed song (appends)

---

### Post by prophetski on 2008-06-29
thanks again for that. finally got an add to playlist working though the icon doesnt appear, i think it was the restart that did it. maybe it was because i'd installed nautilus actions and hadnt restarted afterwards.??
thanks again for your help
:)

---

### Post by prophetski on 2008-06-29
oops
just been at the computer again and realised that the add to playlist option isnt workin properly, it adds the file name to the playlist but its just the name. it isnt playable and no time/duration info appears

---

### Post by mc4man on 2008-06-29
While i'm not going to use audacious the 2 parameters I mentioned do work here, as long as audacious _can play the file in the first place_ I had some .wma's I'd quickly copied off a disk yesterday (just did a fresh install, was setting up when i saw your post) and audacious can only play some of them. Obviously the ones it won't play won't work from the r. click. I just added some mp3's and the r. click actions work as expected.

I'm using (-e -p %M)as parameters in 1 action (load in aud)
and (-e %M )(queue in aud) as the other
if you wanted to remove current list, load and start playing use (-E -p %M)
What parameters are you using?

---

### Post by mc4man on 2008-06-29
Here's 3 screenshots of 3 possible actions, tool tip describes as best i could. The conditions would be set the same in all as shown previously. Note I'm not using %d anywhere in parameters.

---

### Post by mc4man on 2008-06-29
and what the heck , here are the 3 actions for amarok. They pretty much cover anything you'd want to do without ever seeing the playlist gui. The conditions again are the same for all as above. (allows action to work with files, folders, sub folders, ect., contents of folders, sub folders are loaded in the order listed)
You may uncheck ' remember current playlist on exit' in settings -> configure Amarok  (from the gui), not necessary if you use the load action to open amarok

---

### Post by prophetski on 2008-06-30
sorry mc4man, thought i saved an edit on the last post i made last night but obviously not. i actually solved my problem with help from this link which everyone might like to see. why solve a problem when someones done it already? you might like to add your configurations to this page [http://www.grumz.net/?q=node/301](http://www.grumz.net/?q=node/301) . cant thank you enough for all your help. i use the computer just for internet and media stuff, so getting the audio player to work the way i was used to with windows was super important.:D

---


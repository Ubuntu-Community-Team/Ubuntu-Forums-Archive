---
title: "Synchronize iPod Touch in Ubutu 9.04"
date: 2009-07-22
forum: Multimedia Software
---

### Post by Alvaro_SG on 2009-07-22
Hi, I have a jailbroken iPod Touch with the version 3.0 of firmware. I tried Rhythmbox, Banshee, gtkpod... but nothing works. Is possible syncronize without Wine+iTunes?

---

### Post by Alvaro_SG on 2009-07-22
Bump!

---

### Post by Stickee on 2009-07-26
Also looking for a solution.  Same deal as OP, 3.0, jailbroken.  Want to use it with Linux.

---

### Post by Nburnes on 2009-07-26
I'm pretty sure it's not possible as the only tutorials I have found only worked with 1.x.x firmwares :(

---

### Post by Labello on 2009-07-26
I resolved this issue by using the non-free version of virtualbox with usb-support and installed XP + itunes and everything went just fine. You can even establish shared folders to sync your ipod with virtualbox from your hostsystem:

1. install virtual box from the sun website (there is a special repository)
2. install any windows you want/need
3. install itunes
4. go into the settings of your created virtual machine and setup the USB prts to be routed to windows
5. plug iPod in and go into itunes -> ipod should be detected and you should be able to restore firmware.

---

### Post by mess110 on 2009-07-26
I had the same "problem".

Sync'ing is a bitch. If your iPod is jailbroken than I am pretty sure you do music transfer over SSH (wireless)

the best thing to do in my opinion is just take a folder for your music, rename it ipod or sth and keep all the music you have on your ipod in that folder. And every time you add music to your ipod you just add the whole folder.

I didn't manage to connect in any way to banshee or gtkpod due to some crap I am not aware of. Pretty sure its the same thing for you too. Just use a SSH connection. It is fast enough and it is wireless :D

---

### Post by Stickee on 2009-07-28
> **mess110 said:**
> I had the same "problem".

Sync'ing is a bitch. If your iPod is jailbroken than I am pretty sure you do music transfer over SSH (wireless)

the best thing to do in my opinion is just take a folder for your music, rename it ipod or sth and keep all the music you have on your ipod in that folder. And every time you add music to your ipod you just add the whole folder.

I didn't manage to connect in any way to banshee or gtkpod due to some crap I am not aware of. Pretty sure its the same thing for you too. Just use a SSH connection. It is fast enough and it is wireless :D
I suppose I can try this, but before I do:
1. Where do the does the music on the iPod go, /Library/Audio?
2. Is there any specific naming convention you need to use, or does the player use the ID3 tags?

Thanks

edit: actually just tried iTunes in my VirtualBox XP machine, and it worked fine.  I just shared my music folder with XP, added the music and all was well. :D

---

### Post by mess110 on 2009-08-19
happy to know it now works for you.

A quick note: if you use a jailbroken ipod you also should use a jailbroken player. and in that player you can specify where the music goes.

as for id3 tags.. well the old ipod architecture is pretty much gone. so your mp3 files won't be renamed. just edit the id3 tag on the mp3 file and the ipod will know.

---


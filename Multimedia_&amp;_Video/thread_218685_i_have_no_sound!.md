---
title: "i have no sound!"
date: 2006-07-18
forum: Multimedia &amp; Video
---

### Post by bails on 2006-07-18
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

that is the error message that i get when i try to click on the colume controll and mplayer sends me an error message as well about sound not being connected to any devices as well

---

### Post by ivotedforkodos on 2006-07-19
I think we are having the same problem:

[http://www.ubuntuforums.org/showpost.php?p=1273051&postcount=85](http://www.ubuntuforums.org/showpost.php?p=1273051&postcount=85)

Was your sound working before?

---

### Post by bails on 2006-07-19
my sound was working before, tho we have different sound cards i have intel blah blah blah but it soundsw like the same problem

---

### Post by bails on 2006-07-19
ok in addition i have an alternate user on my comp and THAT account DOES have sound, why does mine not?

---

### Post by ivotedforkodos on 2006-07-19
Hey, me too! That must mean that the problem is localized within your home directory. I'm guessing that it's a misconfiguration of a .gnome file or something along those lines. Let me know if you get it to work.

Update: I tried reinstalling GDM as suggested in the Comprehensive Sound Guide, but that didn't work. Have you tried anything new or found a solution?

---

### Post by bails on 2006-07-21
i have been not finding any help and i'm a new user like as of last week so i don't know really what i'm doing, which is why i posted here :(

---

### Post by jrjr on 2006-07-21
Check your permissions... I had the same trouble.

System/Administration/Users and Groups
Enter your user password
under user tab click your username and then properties
Under user privileges check all the boxes and say ok
You might have to reboot, I cant remember

Good luck!!

Edit,
If you cannot do it from the user that has no sound, log into the user that does have sound and configure the user that does not have sound.

---

### Post by ivotedforkodos on 2006-07-22
bails, I was able to solve my problem! I did this at LordRaiden's suggestion:

ivotedforkodos - look in this file

```

sudo nano /etc/group

```

each line in the file has the name of the group. Go to the audio line (they aren't alphabetical but the list is not too long). Add your username (the one without sound) to the audio line.

so if you line read

```

audio:x:29:user1,user2

```

it will now read (assuming you want to add the user 'newuser')

```

audio:x:29:user1,user2,newuser

```

Be very careful when editing that file.

---

### Post by bails on 2006-07-22
IT WORKED!!! thanks SOOO much i really appreciate it!!! i have sound now!!!

---

### Post by odyniec on 2006-07-22
Just a note: vigr should be used to edit the group file in a safe manner.

---

### Post by S!ian on 2006-09-12
Hi, I kind of having a similar problem. Until a week ago my sound was working just fine, but suddenly it stopped.

Here is my problem:
Until I log on (I enter my user name and password) to my machine the sound works.(Means I can hear the log on music) I created an extra account and it has sound. I use VLC player and it has sound. BUT my main account has no sound (except VLC player).

I tried the sudo gvim /etc/group" thing, but it was allready how it is supposed to be and didn't change anything. Since my other account has sound it has to be something simple, but I'm really new to linux and have no clue what it could be. Any suggestions?

Thanks for taking time.

Edit: I forgot to mention, nothing is muted. ;)

---

### Post by S!ian on 2006-09-13
Never mind, I just found [this]("http://www.ubuntuforums.org/showthread.php?t=32063") usefull how to which fixed it. Big thanks to Gandalf. 

Another usefull thing was [this.]("http://www.ubuntuforums.org/showthread.php?t=238446&highlight=sound+account")

To whoever has to deal with that issue, hope this helps to solve your problem.

---

### Post by Christopher Cook on 2006-09-13
If nothing works, it may be an unsupported sound card. Mine was.

---


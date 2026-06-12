---
title: "Audio issue on Feisty Fawn 64 bit version"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by DraeLee on 2007-05-22
Ok I am not sure what happened exactly but here goes.  As far as I know when I went to work last night my audio and everything was working at it should in Ubuntu.  I log on today and I have no sound whatsoever.  No music, no drums at the login screen nothing.  I am Using KDE on the 64bit Ubuntu 64 bit kernal.  Ive googled quite a bit and tried a few things but still no audio.  I went into Windoze since I can dual boot and my audio is fine.  So I know nothing is unhooked or something like that.  My sound is generic onboad sound.  Any help would be appreciated I am kind of at a lost with this.  This is the first problem in a while I havnt been able to google and solve myself.  Which says a lot about Ubuntu and the great job they are doing.  I dont know it this is a constant issue or just me but thank you in advance for any advice.

---

### Post by dbott67 on 2007-05-22
Check this thread (post #2):
[http://ubuntuforums.org/showthread.php?t=448231&highlight=asoundrc](http://ubuntuforums.org/showthread.php?t=448231&highlight=asoundrc)

There's also a link to a "[Comprehensive Sound Problems Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")" that you can try if the above doesn't work.

-Dave

---

### Post by dbott67 on 2007-05-22
Further to my above post, before doing anything drastic, you may just want to create a new user account and try logging in using the new account.  If you get sound, then you know that it's something in your user account profile (such as the .asoundrc file).

-Dave

---

### Post by DraeLee on 2007-05-22
> **dbott67 said:**
> Further to my above post, before doing anything drastic, you may just want to create a new user account and try logging in using the new account.  If you get sound, then you know that it's something in your user account profile (such as the .asoundrc file).

-Dave

good point.  Ill try that and let ya know

thank you again

---

### Post by DraeLee on 2007-05-22
You are the man.  I went into an old login that I had instead of making one.  And all my sounds came through music and all.  So now I need to find the file you were talking about. I view to show all hidden files but didnt see it.  So I am doind a search and I will let you know

---

### Post by DraeLee on 2007-05-22
hmm I did a search for the file and could not find it at all.  I made sure view hidden files was turned on also

---

### Post by dbott67 on 2007-05-22
For me, the file was in my home directory and called:
```
.asoundrc
```

The file is related to ALSA.  If you use OSS, there may be a different config file.

Additionally, there may be some sound settings buried in the **.gnome2** directory.  Unfortunately, I know very little about the black art of sound in Linux.

Another option would be to copy over all of your current user data to the newly created user account's home folder and then change ownership of the files to the new user.

If you really want to use the old account, you could delete it (as well as the user's home folder) and then re-create the account.  Then copy all of the data back and change ownership back.

Hope this helps.

-Dave

---


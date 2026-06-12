---
title: "vlc"
date: 2009-04-06
forum: Multimedia Software
---

### Post by jayanramesh on 2009-04-06
Dear pals,
After reinstallation of my vlc player in intrepid 64 bit it resist to start by giving the error"VLC could not open the file "/usr/share/vlc/skins2/text.bmp".Could any friend help me to solve this problem?.
Thank you.

---

### Post by ad_267 on 2009-04-06
I would try deleting the .vlc directory in your home directory. Either use the file browser and press Ctrl+H to show hidden files, then delete it, or:
rm -rf ~/.vlc

That will remove any previous settings you have made. I'm guessing it's looking to apply a skin which no longer exists.

---

### Post by jayanramesh on 2009-04-06
Dear ad_267,
I have deleted .vlc directory and reinstalled vlc player but I 've got the same error again.This happened after I have changed my vlc skin.Is there any way to resolve my prob.Could you tell me how to add skin to the appropriate folder?


Thanks

---

### Post by logic++ on 2009-04-06
You could try putting a picture named "text.bmp" in folder /usr/share/vlc/skins2/ as a workaround.

---

### Post by ad_267 on 2009-04-06
How are you installing VLC?

Are you installing the version from the Ubuntu repositories?

---

### Post by jayanramesh on 2009-04-06
Dear ad_267.
I got it from 
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by mc4man on 2009-04-07
If you are using 8.10 (intrepid) with a 0.9.x version of vlc then the configuration file(s) are in home folder -> .config/vlc

Or try from terminal
```
vlc --reset-config
```

---

### Post by bobbypavan on 2009-04-07
I think the problem is with the skin you are using rather than with the player's ability to play multimedia files. As per wiki "Many graphical user interfaces use bitmaps in their built-in graphics subsystems". May be the bmp file that ur present skin needs may be missing. 

As such I don't see any point in reinstalling the program. See if you can find the bmp file in the source package u downloaded. Put it in the folder it is showing. That might possibly work. Or just change the skin :)

Only for reference: 
If u r not bothered by skins and just want a working VLC player, turn on all third party repositories in synaptic and use 
apt-get install vlc to install the program.

---

### Post by jayanramesh on 2009-04-07
Dear Mc4man,
Thanks a lot,problem is solved - I've got it back everything by the code you have provided

---

### Post by jayanramesh on 2009-04-07
Dear Bobby pavan,
Thanks for ur response but the prob.'s solved by the help of Mc4man

---

### Post by euriconeto on 2009-04-09
Hello Folks,

I'm very new at ubuntu and recently installed Jaunty and downloaded Totem and VLC in an attempt watch DVDs but so far both (Totem and VLC) don't go through. I have downloaded medibuntu, restricted-codec, and all other files on threads saying that would solve problems with playing DVDs, but so far the problem remains.

Following this thread's advices I found this report message "main decode error: decoder is leaking pictures, resetting the heap"

Can any one help me with this?
Cheers,
Eurico

---

### Post by jayanramesh on 2009-04-14
Dear euriconeto,
Please uninstall vlc from synaptic and reinstall it from this [> http://http://www.videolan.org/vlc/download-ubuntu.html]("http://www.videolan.org/vlc/download-ubuntu.html")This may solve your problem.Even after this if the problem is not solved check out you have installed ffmpeg from synaptic package manager.

---


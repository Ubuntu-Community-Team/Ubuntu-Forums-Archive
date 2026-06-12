---
title: "amarok 2 sound does not work... eventually"
date: 2009-08-28
forum: Multimedia Software
---

### Post by scandido on 2009-08-28
Amarok 2 seems to work fine on my Ubuntu 9.04 for a while. Then, at some point I'll try and start Amarok again and it will give me the message:

Phonon: KDE's Multimedia Library
The audio playback device HDA Intent (ALC888 Analog) does not work.
Falling back to HDA Intel (ALC888 Digital).

At this point, Amarok acts as though it is playing but no sound reaches the speakers. A restart fixes this problem, but its getting pretty annoying. Can anyone offer any advice or explain what this message is saying?

Thanks in advance for your time.

---

### Post by celsofaf on 2009-10-12
I am also having the same problem. Amarok 2 worked fine for months but yesterday this same thing happened. Rebooting didn't work either. Yes, also using 9.04 here.

Thanks in advance for any advice!

---

### Post by rotwang888 on 2009-11-04
Oh my.  No replies since August?  Oh well, I'll bump this to say I have the same problem running 9.10.

---

### Post by scandido on 2009-11-04
I am still with 9.04, but it seems like updates since last time I posted have actually caused this problem to get worse. Although its not 100% certain, it seems that often when I skip to the next track while the current song is playing, I get the error. Sometimes it just happens when a song starts playing as well. Very annoying, but no one seems to have an answer.

---

### Post by Fernando Negro on 2009-11-06
Try changing the phonon backend.

Uninstall the "phonon-backend-gstreamer" package and install the "phonon-backend-xine" one instead.

([http://ubuntuforums.org/showpost.php?p=7197502&postcount=3](http://ubuntuforums.org/showpost.php?p=7197502&postcount=3))

---

### Post by scandido on 2009-11-06
Thanks for the suggestion. Apparently I'm already using the Xine backend, so unfortunately it is not a fix, at least in one case.

---

### Post by Fernando Negro on 2009-11-07
You're welcome.

Yes, in my case, I can now play my Bach flacs, with them being cut a few seconds from the end, but I still can't play my mp3s.

I think it' a bug in "phonon", since K3b also complains about the same error.

I would make a bug report myself, but I can't remember when it started, and have recently changed my motherboard, so I wouldn't know how to explain what happened exactly.

You can always use Audacious Audio Player in the meantime.

---

### Post by Claus7 on 2009-12-03
Hello,

> **Fernando Negro said:**
> Try changing the phonon backend.

Uninstall the "phonon-backend-gstreamer" package and install the "phonon-backend-xine" one instead.

([http://ubuntuforums.org/showpost.php?p=7197502&postcount=3](http://ubuntuforums.org/showpost.php?p=7197502&postcount=3))

I had the same problem with kaffeine. I installed phonon-backend-xine without uninstalling anything, as that required to uninstall almost all my system, yet even though I got rid with the phonon error message, I do not have sound... Only with kaffeine...

Regards!

---

### Post by redmorning on 2011-01-20
> **Fernando Negro said:**
> Try changing the phonon backend.

Uninstall the "phonon-backend-gstreamer" package and install the "phonon-backend-xine" one instead.

([http://ubuntuforums.org/showpost.php?p=7197502&postcount=3](http://ubuntuforums.org/showpost.php?p=7197502&postcount=3))

Hi,

I'm having this problem and as it seems there is not still a solution nor a workaround for that. I just have "phonon-backend-xine", so nothing to remove and Amarok stops to use audio devices randomly (like the others, it keeps playing). Everything is fine with Amarok but it is getting really annoying. 

Thanks in advance.

---

### Post by redmorning on 2011-01-20
After a little more googling:

Thanks to **Dimitar Krasimirov Boichev**

Solution from original post (you can find in the link too):
> OSS HOWTO:
1) Download this file: [http://www.fileupyours.com/view/77985/libphonon.conf]("http://www.fileupyours.com/view/77985/libphonon.conf")
2) Put it in:~/.config/kde.org/ (where ~/ means your home directory) You may need to create the kde.org directory
3) If you don't have phonon-backend-xine install it.
sudo apt-get install phonon-backend-xine
4) Restart Amarok 2 and have fun.

[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/349847]("https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/349847")

when i did this and restarted Amarok, first i get the same error message but i was able to get the sound. So maybe in the next times i won't get that error message at all. 

Cheers.

---

### Post by redmorning on 2011-01-21
i still get that error message and sound cuts randomly, so it wasn't an exact solution for me.

by the way, here is my environment:
Ubuntu 10.04 Lucid
KDE 4.4.5
AMarok 2.3.0 (Using KDE 4.4.2)

---

### Post by mnajar on 2011-06-14
I was experiencing the same problem, seems to be fixed changing the deinterlace method

Settings-> Configure Amarok
Playback
Sound System Configuration {Configure}
Backend TAB
Deinterlacing method -> Linear (was appearing use_vo_driver)

Hope that is clear enough and helps, is working and the Phonon KDE message is not appearing anymore

---


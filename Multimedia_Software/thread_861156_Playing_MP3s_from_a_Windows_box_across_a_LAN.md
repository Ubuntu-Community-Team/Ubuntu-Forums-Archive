---
title: "Playing MP3s from a Windows box across a LAN"
date: 2008-07-16
forum: Multimedia Software
---

### Post by Mark Phelps on 2008-07-16
I've done a lot of searching but haven't come up with a solution to my problem -- perhaps someone here can help ...

I have LOTS of MP3s stored on a Windows XP box.  I have shared the directories holding those files, and using either Nautilus or Gnome Commander, I can open those directories and see the files.

But when I click on a file and try to play it, I get a message about being unable to play a "remote" file and having to download it first.  I don't want to download the music collection to my Linux box just to play the tunes.

The sound clients I have installed include Audacious, XMMS, Rhythmbox -- and a host of Video players (Mplayer, SMplayer, VLC player).  I should mention that I have all the codecs needed to play the files and all the apps work fine with files stored locally.

I even tried messing around with PulseAudio -- but that hosed up my Linux box so bad that I ended up restoring the image from backup.

I don't want the Windows box broadcasting music because it's a shared resource and each of us using it want to play different tunes.  And, since everyone else uses a Windows version to access the box, I'm not up to convering it to a LAMP server.

So, is there a way to play the MP3 files across the local network using the Linux box?

---

### Post by wkulecz on 2008-07-16
Have you "mounted" your XP share so there is a desktop icon for it?  This works for me for mp3 songs and flv youTube downloads.  My share is an older version of Ubuntu running SAMBA but this shouldn't really matter.

--wally.

---

### Post by unoodles on 2008-07-16
I am assuming you are using the standard windows (samba) shares.
the way i do it is mount the share, and then access the through /home/<username>/.gvfs/<sharename>
This way the file manager thinks its a local folder, and it works great.

---

### Post by blazercist on 2008-07-16
my audacious plays remote mp3s, i just open audacious first and click add dir and browse to the share.

---

### Post by aeiah on 2008-07-16
if all you want is media sharing, you could set up a UPnP or daap media server on your windows box and stream the content to your linux box.

---

### Post by Mark Phelps on 2008-07-16
Replies ...

wkulecz: No, I have not tried that.  I am viewing the Windows shares using Nautilus or Gnome Commander.  I'm not actually mounting the shares.  I'll have to look into that but when I tried smbfs some time back, I could not get it to work.

unoodles:  Same reply -- I'll have to look into mounting the share.

blazercist: My Audacious has no "add dir" option. I'm running version 1.5.0 on Hardy and only have options Play File and Play Location.  The first only allows me to select local files; the second does not find network locations.

aeiah: I don't want to stream music from the server, I want to access music located on the server. Does either of those do that?

---

### Post by AndrewEsther on 2008-07-16
Mounting the windows share should do the trick. I play files off of my other windows machine all the time using amarok.


Cheers

---

### Post by Mark Phelps on 2008-07-16
Folks ... 

Many thanks for the "mount" suggestion.  I just got done playing around with mounting smbfs shares and it works great!  Since I don't like external mounts interfering with the boot operation, I've created new menu items to mount and unmount the music share.

BTW, once the share is mounted, Audacious sees it, but not before.

---


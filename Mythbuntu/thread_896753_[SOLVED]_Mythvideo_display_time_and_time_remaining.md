---
title: "[SOLVED] Mythvideo display time and time remaining"
date: 2008-08-21
forum: Mythbuntu
---

### Post by frego on 2008-08-21
Back when I used Knoppmyth, I could hit the "i" key and mythvideo would toggle from time into the avi, overall time remaining, etc.  I'm now using Mythbuntu and I can no longer find that info in mythvideo.  Does anyone know how I can regain this functionality?

---

### Post by newlinux on 2008-08-21
Are you using the internal player for viewing .avi files? I believe the default is to use mplayer in mythbuntu. In mplayer I think you would use the "o" key to get that info,

---

### Post by frego on 2008-08-31
Thanks for the informative reply.  You are correct, the 'o' key does bring up the info.  Can anyone tell me how to map 'o' to my info button in MythVideo?

---

### Post by newlinux on 2008-08-31
Off the top of my head I don't know how to remap the keyboard with mplayer (probably a change in mplayer.conf or another config file). If you are using a remote you can do with LIRC pretty easily, but I think you are using a keyboard. 

man mplayer

should give you more information.

Alternatively, you could just use the internal player instead of mplayer for mythvideo (you can change this in the mythvideo settings).

---

### Post by frego on 2008-08-31
sorry, I am using lirc.  I have an MCE2 USB remote.  I thought maybe the mcc dynamic key mapping would help me.  I can't figure out how to insert a new mapping on there.  Back when I was on Knoppmyth, I would just edit the lircd.conf file.  I haven't been able to find which file it is under Mythbuntu.  I do notice there are separate files for different appz.  Like:  /home/user/.lirc/mplayer Maybe I can change that and have it work?

---

### Post by frego on 2008-08-31
Ahh... that did it! In the file:
/home/user/.lirc/mplayer

I added the keymapping:

```
begin
    remote = mceusb
    prog = mplayer
    button = more
    config = o
    repeat = 0
    delay = 0
end
```

I can now use my MCE 2 remote to get the info in MythVideo while using mplayer as my player.:)

---


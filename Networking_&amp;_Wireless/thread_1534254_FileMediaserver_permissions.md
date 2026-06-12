---
title: "File/Mediaserver permissions"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by Xaero252 on 2010-07-19
Okay, I'm pretty familiar with chmod and the like, and I have the fileserver etc all configured and ready to go (it also doubles as the wireless router in this specific environment).
Heres the concept for what I want to do:
I will have 3 public shares (and maybe some private ones) active on the server One of these shares should be READ ONLY, which is simple to accomplish, and I have already done so, people can easily view and copy content as they wish but they may not add to it at all, only root will be able to add files to the directory - sweet. 
The second share is also not complicated, I want people to be able to add to the server freely, but I need to be able to control what they add - porn, etc should not be allowed, where home made movies, pictures, music etc will be allowed. To accomplish this I make a write-only directory where the incoming data will sit until I or one of the other administrators sifts through it deleting the garbage and moving it to the active directories..
The finally share is where things get tricky. These files cannot be copied from the server. They will all be video files. I want people to be able to watch them, but I don't want them to copy the movies to their physical drives. To my knowledge this is impossible via normal permissions... I have a couple of strange workaround ideas in mind, but I figured I would see what the experts around the forums have to say...

My current (most rational) idea is: Have a script parse the video directory periodically and create *.pls files, and streaming the files over some other protocol besides samba...
Another potential solution is to create a media center extender out of this particular share directory, but this requires transcoding in some cases, and will not only spike resource usage, but will potentially sever users from accessing the content.

Is there another way to do the final directory? I understand that no matter what they will just be able to screencap it, but this is more prohibitive (most people will not have ill intent, and those that would probably wouldn't have the know-how anyway).

Thanks in advance
~Xaero

---


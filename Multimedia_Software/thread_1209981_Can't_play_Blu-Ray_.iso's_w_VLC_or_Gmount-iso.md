---
title: "Can't play Blu-Ray .iso's w/ VLC or Gmount-iso"
date: 2009-07-10
forum: Multimedia Software
---

### Post by mj07h on 2009-07-10
I have multiple Blu-ray .ISO's that I'd like to play.  I'm new to Ubuntu, but I'm quickly catching on.  I've already installed VLC and gmount-iso, but for some reason I can't get these blu-ray .iso's to play!?  Can anyone help? Thanks

---

### Post by starcraft.man on 2009-07-10
If your positive the encryption was removed on archiving then I'm puzzled. As far as I know, without the security features the blu ray disc is nothing more than an h.264 or VC1 encoding. [VLC plays both]("http://www.videolan.org/vlc/features.html#video_notes") that I know of.

If you just made straight ISOs of the bits on the disc, then the security is intact and you'll need a software that does the decryption. That would be something like cyberlink or slysoft and unfortunately they are windows only to my knowledge.

---

### Post by cozmicharlie on 2009-07-10
> **mj07h said:**
> I have multiple Blu-ray .ISO's that I'd like to play.  I'm new to Ubuntu, but I'm quickly catching on.  I've already installed VLC and gmount-iso, but for some reason I can't get these blu-ray .iso's to play!?  Can anyone help? Thanks

Blu Ray support for Linux is not there yet.  Too bad, Blu Ray and netflix are the only reasons I need to keep my windows dual boot.  You can try this [https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD).  If you get it working post back because I have not been able to.  If not the the only options are to dual boot or use Virtual box.  

Good luck!

---

### Post by pizza-is-good on 2009-07-10
> **mj07h said:**
> I have multiple Blu-ray .ISO's that I'd like to play. I'm new to Ubuntu, but I'm quickly catching on. I've already installed VLC and gmount-iso, but for some reason I can't get these blu-ray .iso's to play!? Can anyone help? Thanks
 
I envy the fact that you have blu-ray capabilities...
 
Good luck!

---

### Post by mj07h on 2009-07-11
> **starcraft.man said:**
> If your positive the encryption was removed on archiving then I'm puzzled. As far as I know, without the security features the blu ray disc is nothing more than an h.264 or VC1 encoding. [VLC plays both]("http://www.videolan.org/vlc/features.html#video_notes") that I know of.

If you just made straight ISOs of the bits on the disc, then the security is intact and you'll need a software that does the decryption. That would be something like cyberlink or slysoft and unfortunately they are windows only to my knowledge.

Ahh...but that's the thing!  I used AnyDvD to rip the blu-ray movies into .iso's myself and they play great with VLC in my Vista environment.  All I have to do is mount them with a virtual drive and they play encryption free...so I can't understand what the problem is...I just can't seem to mount them and then get VLC to "see" them...

---

### Post by cozmicharlie on 2009-07-11
> **mj07h said:**
> Ahh...but that's the thing!  I used AnyDvD to rip the blu-ray movies into .iso's myself and they play great with VLC in my Vista environment.  All I have to do is mount them with a virtual drive and they play encryption free...so I can't understand what the problem is...I just can't seem to mount them and then get VLC to "see" them...

Check the doom9 forums - I don't believe Blu Ray ripped via anydvd will play on Linux.  I beleive you need dumpHD - see this forum for a detailed discussion [http://forum.doom9.org/showthread.php?t=123111&highlight=linux](http://forum.doom9.org/showthread.php?t=123111&highlight=linux)

---

### Post by woutervanwijk on 2010-03-17
try this: mount -o loop -t udf pathtobluray.iso /media/cdrom

---

### Post by mister_playboy on 2010-04-08
> **woutervanwijk said:**
> try this: mount -o loop -t udf pathtobluray.iso /media/cdrom

Thanks! :guitar: Once the iso is mounted, I could play the .m2ts file in VLC player.

---

### Post by Yfrwlf on 2011-04-30
Now if only VLC, MPlayer, Totem, or others supported straight playback of BR ISO files like they do with DVD ISO files, that would be great.  As of now though it seems none of them support the BR menus, so you have to play the m2ts files directly instead without menus.

---

### Post by mastapat11 on 2011-05-10
> **mister_playboy said:**
> Thanks! :guitar: Once the iso is mounted, I could play the .m2ts file in VLC player.

i tried and once the iso is mounted, I could NOT play the .m2ts file in VLC player. BUT, it did play mPlayer.  Anybody know what's up w/ vlc 1.1.9?

@woutervanwijk: thanks for this tip

---

### Post by Yfrwlf on 2011-05-10
> **mastapat11 said:**
> i tried and once the iso is mounted, I could NOT play the .m2ts file in VLC player. BUT, it did play mPlayer.  Anybody know what's up w/ vlc 1.1.9?

@woutervanwijk: thanks for this tip

I've never ever had a problem playing m2ts files in VLC, in fact that's primarily what I use for them as Totem will play them but has really bad problems with seeking should you skip to other places in the video.

---

### Post by youqu8 on 2012-01-03
> **woutervanwijk said:**
> try this: mount -o loop -t udf pathtobluray.iso /media/cdrom

thx indeed!!

---


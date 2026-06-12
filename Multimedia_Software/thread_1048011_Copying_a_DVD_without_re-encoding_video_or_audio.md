---
title: "Copying a DVD without re-encoding video or audio"
date: 2009-01-23
forum: Multimedia Software
---

### Post by needhelpplease on 2009-01-23
Simple question: I have some DVDs which I would like to copy, for making legal backups.

I have dual-layer DVDs I can burn onto, and a dual-layer burner.  It all works well.

I'm trying to use k9copy but it seems to always want to re-encode.  What I would really like it to do is to decrypt the content but otherwise don't alter it.  Of course I also want it to create menus and remove the region code, but it always does this.  I want this so I could play it on a player I have from Asia, for example.

Any suggestions?

Thanks.

---

### Post by mc4man on 2009-01-23
Haven't used k9 in a long time but somewhere in the settings/preferences you can set the target size which defaults to 4.3Gb. Set it to 7.5 - 8 and it won't transcode (shrink

Otherwise try vobcopy (for non structure protected titles
basic command (if drive mounts to /media/cdrom0
vobcopy -v -m -F 16 

vobcopy -v -m -F 16 /media/[COLOR="Red"]cdrom1[/COLOR] (adjust to mount point in media if different

---


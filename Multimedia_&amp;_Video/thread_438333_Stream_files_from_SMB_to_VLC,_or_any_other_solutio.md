---
title: "Stream files from SMB to VLC, or any other solutions?"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by CaineDNA on 2007-05-09
I've got a media center machine that I'm trying to use Ubuntu with, and having some issues. I should say that by media center, I don't care much about tuning TV. I mainly watch a lot of fansubbed anime and podcasts, truth be told.

So the issue that I have is viewing those files. I've tried a couple different video players, but found that Totem, Kaffeine and Mplayer didn't do the trick for a number of those files. VLC seems to work like a charm, not just being able to play them back, but not choking on them either.

VLC however, doesn't seem to like playing back files across an SMB share, however. The other players would be willing to, is the part I don't quite get. I searched around Google and these forums, and found that people were suggesting mounting the share permanently, and that it might fix the issue. I've been fighting with getting this to work, because honestly, I'm a GUI type of person. After 2 hours of trying to just get this one thing done, I'm wondering if maybe there's a better way to do this? Here's my situation:

I have a Windows XP file server with the video files on it. RIght now it's using samba, but I'm not locked into this if there's a better option.

I typically download and send over the files from my main machine.

I really like the playback in VLC on Linux over the others I've tried, but I'm open to different options there too

I considered streaming the files from VLC on the Windows machine, but my library changes pretty quickly. I'm hoping for something that would auto update me.

This will be the nail in the coffin if it just works well! The less I need to do command-line, the better.

---

### Post by jamescox84 on 2007-05-09
You could use smbfs to mount the samba share on you file system.

Install smaba and smbfs
```

sudo apt-get install samba smbfs

```

Make sure the the workgroup is set to the same name as your windows workgroup
goto System -> Administration -> Shared Folders -> General Properties -> Domain/Workgroup


Create a mount point for the shared folder
```

example:
sudo mkdir /media/smb

```

Mount the share
```

sudo mount -t smbfs //servername/sharename /mountpoint

example:
sudo mount -t smbfs //james-desktop/Music /media/smb

```

You might also want to specify a user name and password if it's required use -o at the end of mount like this.
```

sudo mount -t smbfs //servername/sharename /mountpoint -o username=yourusername,password=yourpassword

```

Hope that's helpful. If it works you might want to add it to /etc/fstab

---


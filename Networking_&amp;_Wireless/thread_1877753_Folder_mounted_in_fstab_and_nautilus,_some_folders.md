---
title: "Folder mounted in fstab and nautilus, some folders missing on mounted share?"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by jarthurs on 2011-11-08
I have a Acer Altos EasyStore NAS on which I have stored all my audio files. Now I've never had a problem seeing the contents with Nautilus but for some reason I've had a lot of permissions issues when trying to mount shared folders. Previous problems with this box all appeared to resolve themselves when I mounted it with the 'nounix' option in /etc/fstab 

However I recently noticed that when I add files to the NAS, I can see them in Nautilus but machines mounting the folder through fstab cannot see the new files or folders.

The drive is mounted in fstab as:

//nas/media/Audio /mnt/audio cifs credentials=/filename,iocharset=utf8,nounix,file_mode=0777,dir_mode=0777,0 0

I can view the contents in Nautilus at smb://nas/media/Audio and see the full contents. 

-- Nautilus --
drwx------ 1 jason jason    0 2006-04-02 01:32 Ballard, Russ
drwx------ 1 jason jason    0 2011-03-29 16:45 Basement Jaxx
drwx------ 1 jason jason    0 2011-03-29 16:49 Beloved, The
drwx------ 1 jason jason    0 2011-10-24 21:02 Benjamin Francis Leftwich
drwx------ 1 jason jason    0 2011-10-24 21:43 Billy Connolly
drwx------ 1 jason jason    0 2011-03-29 16:48 Bjork
drwx------ 1 jason jason    0 2006-04-02 01:43 Black
drwx------ 1 jason jason    0 2006-04-02 01:58 Blur
drwx------ 1 jason jason    0 2011-03-29 00:17 Bonobo
drwx------ 1 jason jason    0 2006-04-02 02:11 Bush, Kate
drwx------ 1 jason jason    0 2011-01-22 16:17 Byrne, David

But the contents of the mounted folder are showing only 8 of the 11 folders present on the NAS.

-- /mnt/audio (mounted in fstab) --
drwxrwxrwx  2 root root    0 2006-04-02 01:32 Ballard, Russ
drwxrwxrwx  5 root root    0 2011-03-29 16:45 Basement Jaxx
drwxrwxrwx  4 root root    0 2011-03-29 16:49 Beloved, The
drwxrwxrwx  2 root root    0 2011-03-29 16:48 Bjork
drwxrwxrwx  2 root root    0 2006-04-02 01:43 Black
drwxrwxrwx  5 root root    0 2006-04-02 01:58 Blur
drwxrwxrwx  5 root root    0 2006-04-02 02:11 Bush, Kate
drwxrwxrwx  3 root root    0 2011-01-22 16:17 Byrne, David

Can anyone shed some light on this?

Many Thanks,
Jason.

---


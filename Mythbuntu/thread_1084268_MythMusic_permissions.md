---
title: "MythMusic permissions?"
date: 2009-03-01
forum: Mythbuntu
---

### Post by uncle hammy on 2009-03-01
OK, I am in the middle of turning my Myth setup into a full fledged media distribution center.  

On my backend, I created a directory /media_storage to hold all my videos, pictures and music and shared it.

I then created 3 sub directories....

/media_storage/Pictures
/media_storage/Videos
/media_storage/Music

Finally, I set the owner of the media_storage folder to mythtv:mythtv and set the permissions to rwx for everyone and set the sticky bit for group so that everything new is given mythtv group ownership.  I should point out that originally I set the ownership to the user I log into Mythbuntu with, however with this setup my frontends couldn't generate thumbnail files for MythGallery, so I went the mythtv:mythtv setup copying the model from the default Music / Video / Pictures directories in /var/lib/mythtv.  The ls -all shows the current settings for my /media_storage directory....

drwxrwsrwx   7 mythtv mythtv    84 2009-03-01 07:36 media_storage

Next, on all my frontends, I created the same directory /media_storage and then mounted the share to it.  This way from any machine, the path to Pictures (for instance) is /media_storage/Pictures

It works great, and I have full access to all my media from any machine in the house.  However, I have one small issue and my linux permissions / ownership understanding seems to be letting me down...

I can't rip a CD from my main front end.  It keeps failing saying it can't access the directory.  When it starts, it creates the directory for the Artist, however with the permissions it sets, it can't write to it.  So, I go give it the proper permissions, and start again.  This time is creates the directory for the album, but can't write to that.  After I fix those permissions and start over, it finally rips the songs.

So, my question is, what is the proper permissions / ownership to give to my /media_storage folder?

Thanks,
Scott

---

### Post by uncle hammy on 2009-03-02
Just a bit more information.  I am using smb for my share on the backend machine.  Here's the share in the smb.conf file....

[media_storage]
path = /media_storage
available = yes
browsable = yes
public = yes
writable = yes


and the fstab entry in the frontends....

//192.168.1.200/media_storage     /media_storage     cifs     username=<username>,password=<password>     0     0

---

### Post by uncle hammy on 2009-03-03
bump

---


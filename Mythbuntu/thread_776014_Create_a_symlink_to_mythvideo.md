---
title: "Create a symlink to mythvideo"
date: 2008-04-30
forum: Mythbuntu
---

### Post by Chewiesw on 2008-04-30
Hi

Please could someone tell me how to create a symlink between mythweb and mythvideo. Below is the error I get when I try to access my video thru mythweb.

Error
Could not create a symlink to /var/lib/mythtv/videos, the local MythVideo directory for this hostname (pvrbox). Please create a symlink to your MythVideo directory at data/video in order to use the video portions of MythWeb.

Thanks

---

### Post by fain on 2008-04-30
You can create a symbolic link by using

ln -s source target

Type "ln --help" or "man ln" for more options

---

### Post by sgunther on 2008-05-01
To fix for MythWeb do the following;


```
cd /var/www/mythweb/data/
sudo rm ./video
sudo ln -s **<Path to Videos>** ./video
sudo rm ./video_covers
sudo ln -s **<Path to Video Covers>** ./video_covers
```

Note: You must put in your local paths where the <> symbols are.
      You should only have to do this for non default video storage locations.

---

### Post by NarsilAnduril on 2008-05-10
Good , but what if I have many video folders in my mythvideo setings ?

My mythvideo si sset to /mnt/NAS1/video/Enfants:/mnt/NAS1/video/Films ...

And the result is :

```
The requested URL /mythweb/data/video//mnt/NAS1/video/Films/Beemovie.avi was not found on this server.
```

Could you help me ?

Diego

---

### Post by fain on 2008-05-10
> **NarsilAnduril said:**
> Good , but what if I have many video folders in my mythvideo setings ?

My mythvideo si sset to /mnt/NAS1/video/Enfants:/mnt/NAS1/video/Films ...

And the result is :

```
The requested URL /mythweb/data/video//mnt/NAS1/video/Films/Beemovie.avi was not found on this server.
```

Could you help me ?

Diego

Maybe you could put a symbolic link to the second folder inside the main folder.

---

### Post by NarsilAnduril on 2008-05-10
That's a good idea, I'll do it.

But anyway, it doesn't work, when i click on the movie link in mythweb, i get 

The requested URL /mythweb/data/video//mnt/NAS1/video/Films/Abyss (version longue).avi was not found on this server.

---

### Post by datadude on 2010-01-24
an old thread but I am seeing this same error today. Any ideas

running mythbuntu 9.10

---

### Post by anthortic on 2010-05-02
> **sgunther said:**
> To fix for MythWeb do the following;


```
cd /var/www/mythweb/data/
sudo rm ./video
sudo ln -s **<Path to Videos>** ./video

```

Note: You must put in your local paths where the <> symbols are.
      You should only have to do this for non default video storage locations.

Thank you so much for this great advice, that was the answer for me :)

> **NarsilAnduril said:**
> Good , but what if I have many video folders in my mythvideo setings ?

My mythvideo si sset to /mnt/NAS1/video/Enfants:/mnt/NAS1/video/Films ...

And the result is :

```
The requested URL /mythweb/data/video//mnt/NAS1/video/Films/Beemovie.avi was not found on this server.
```

Could you help me ?

Diego

Yes I also have more than one video source in the backend-setup config. 

They were:

/video/tv
and
/video/film

they were on the same drive so what i have to do was

1. move all the sub-directory's from video/tv to /video 
2. move all film recordings from /video/film to /video
3. delete the now empty /video/tv and /video/film folders
4. go into the frontend - media library - watch videos - menu ('m' key) - scan for changes

This will repopulate the database correctly for mythtv and mythweb and now the links work! Streams very nicely through vlc on my housemates windows laptops making me hugely popular ;)

> **NarsilAnduril said:**
> Good , but what if I have many video folders in my mythvideo setings ?

My mythvideo si sset to /mnt/NAS1/video/Enfants:/mnt/NAS1/video/Films ...



Oh also I think you should be using the link /media/ instead of /mnt/ but I dont know for certain..........

---


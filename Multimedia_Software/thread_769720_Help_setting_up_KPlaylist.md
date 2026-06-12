---
title: "Help setting up KPlaylist"
date: 2008-04-26
forum: Multimedia Software
---

### Post by tamoneya on 2008-04-26
Long post:

I have installed kplaylist on a server running ubuntu 8.04 with apache, php and mysql. I am having problems getting files into the database. I have tried both uploading and updating the database. When I attempt to upload it says: "File could not be uploaded". When I attempt to upload it just hangs at: "Hold on - fetching file list..".
I have tried following this post: [http://www.kplaylist.net/forum/viewtopic.php?t=1010&highlight=upload](http://www.kplaylist.net/forum/viewtopic.php?t=1010&highlight=upload) but it did not work. I did everything that it suggested and then restarted my apache server. I have also checked to make sure the directory where the music files will be stored, /media/disk/kplaylist/, is accessible to the web server. Currently the permissions are 777.

Later I went into setting->file handling. I used the "find" button next to base directory. It found several directories which are part of my operating system which contain music files. I then ran the update function and it found 35 files. It added these files fine. Now the question I have is why can't it do this with my normal files. I thought it might have to do with the fact that /media/disk/kplaylist is on a different physical disk. So I made /kplaylist in my main partition and changed the permissions to 777. 

This had no effect on whether kplaylist was able to find them when i used the"find" button. If I add /kplaylist/ to the base directory field and run an update it still just finds the 35 files from before.

I noticed that the files imported are mainly .ogg. The files which I attempted to upload were all mp3 so i attempted uploading an ogg file of my own. The upload "suceeded" but when I go look for the file in my kplaylist I see no mention of it.

I also checked some things that were suggested by kplaylist: 1) $streamtypes_default = array 2) $cfg['detecttypes'] = array('.mp3' => 1, '.mp2' => 1, '.ogg' => 1, '.wma' => 1);
Both of these seem configured correctly to me from what I learned from their forums.

Im guessing that these problems are related but I am not positive. Any Ideas?

Note: I posted this initially in the kplaylist forums and found the community there to be nice but not as helpful as the ubuntu community.  I was hoping that there might be some people who could enlighten me here.  I attached my index.php file.  I had to compress it in order for the forum to allow me to attach.

---


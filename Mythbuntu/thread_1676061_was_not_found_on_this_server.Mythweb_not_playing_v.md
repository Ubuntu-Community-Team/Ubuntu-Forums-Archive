---
title: "was not found on this server.Mythweb not playing videos 404 error"
date: 2011-01-26
forum: Mythbuntu
---

### Post by geekyhawkes on 2011-01-26
hey;

so i have been sorting out the last few errors on my myth setup for a while and i had previously not had videos working in mythweb as i hadnt set up any storage groups.  

I have now set them up and all of my videos show in mythweb, but when i click to play i get the following error;

404 Not Found

The requested URL /mythweb/data/video/video file name here  was not found on this server.

Anyone know what might be going on, and how i could fix it?  The error doesnt really give me much to go on.

Thanks

---

### Post by nickrout on 2011-01-26
> **geekyhawkes said:**
> hey;

so i have been sorting out the last few errors on my myth setup for a while and i had previously not had videos working in mythweb as i hadnt set up any storage groups.  

I have now set them up and all of my videos show in mythweb, but when i click to play i get the following error;

404 Not Found

The requested URL /mythweb/data/video/video file name here  was not found on this server.

Anyone know what might be going on, and how i could fix it?  The error doesnt really give me much to go on.

Thanks

I have the same error, which i only noticed because of what you posted.

I'm not sure I would ever want to play a video on my web browser, that's what frontends are for, so it doesn't worry me.

---

### Post by geekyhawkes on 2011-01-31
Hmm, guessing its not just me then if you have the same error.  I really would like to be able to get at videos away from my frontend, just gives a bit of flexibilty to my home system really. 

Anyone have any thoughts as to how i can fix this?

---

### Post by tgm4883 on 2011-02-01
> **geekyhawkes said:**
> Hmm, guessing its not just me then if you have the same error.  I really would like to be able to get at videos away from my frontend, just gives a bit of flexibilty to my home system really. 

Anyone have any thoughts as to how i can fix this?

It's likely because the mythweb path is using a symlink to the default location for videos (/var/www/mythweb/data/video points to /var/lib/mythtv/videos).

You could recreate the symlink to point to the correct location that your videos reside in

---

### Post by geekyhawkes on 2011-02-10
Thanks but im not sure this is the issue.  Having followed the symblink thats in place from a terminal i can see all my video files.  I also tried remaking the symblink into my media folder but no luck really, same issue.  

Anyone have any luck with mythweb playing videos?

---

### Post by geekyhawkes on 2011-02-18
Not really trying to bump, just really out of ideas how to get this fixed.  Anyone?

---

### Post by tgm4883 on 2011-02-18
Not sure, I just tested here and it works on my system after moving my symlink.

Where on your filesystem are your videos stored?

What happens if you put a new video file into /var/lib/mythtv/videos/, do a scan in the frontend, then try the file in mythweb?


What is the output of 

```
ls -l /var/www/mythweb/data/
```

---

### Post by nhtrader on 2011-03-07
> **tgm4883 said:**
> Not sure, I just tested here and it works on my system after moving my symlink.

Where on your filesystem are your videos stored?

What happens if you put a new video file into /var/lib/mythtv/videos/, do a scan in the frontend, then try the file in mythweb?


What is the output of 

```
ls -l /var/www/mythweb/data/
```


using MythTV v0.24-206

I can add that I moved MythTV default directories from /var/lib/mythtv to /home/mythtv


So I experienced the same error and here's my output:

ls -l /var/www/mythweb/data
total 112
-rw-r--r-- 1 www-data www-data 55077 2011-02-20 23:48 MyTown.xml
lrwxrwxrwx 1 root     root        30 2011-02-03 18:05 cache -> /var/cache/mythweb/image_cache
-rwxr-xr-x 1 mythtv   mythtv   55077 2011-02-20 23:48 FLVPlayer.swf
lrwxrwxrwx 1 root     root        21 2011-02-03 18:05 music -> /var/lib/mythtv/music
lrwxrwxrwx 1 root     root        26 2011-02-03 18:05 recordings -> /var/lib/mythtv/recordings
lrwxrwxrwx 1 root     root        30 2011-02-03 18:05 tv_icons -> /var/cache/mythweb/image_cache
lrwxrwxrwx 1 root     root        22 2011-02-03 18:05 video -> /var/lib/mythtv/videos
lrwxrwxrwx 1 root     root        22 2011-02-03 18:05 video_covers -> /var/lib/mythtv/videos
d


Clearly I need to reset mythweb's links, but I don't know how to do this.


here's some other info:

1. localhost/mythweb/video  - shows all of my movies but when I click on the title I get this error:
Not Found
The requested URL /mythweb/data/video/MyMovie.m4v was not found on this server.

2. localhost/mythweb/settings/mythweb  -  I tried the various tabs but there are no relavent settings to change

3. localhost/mythweb/settings/video  - I scanned the list of parameters and VideoStartupDir = /home/mythtv/videos (which is correct)

---

### Post by tgm4883 on 2011-03-07
> **nhtrader said:**
> using MythTV v0.24-206

I can add that I moved MythTV default directories from /var/lib/mythtv to /home/mythtv


So I experienced the same error and here's my output:

ls -l /var/www/mythweb/data
total 112
-rw-r--r-- 1 www-data www-data 55077 2011-02-20 23:48 MyTown.xml
lrwxrwxrwx 1 root     root        30 2011-02-03 18:05 cache -> /var/cache/mythweb/image_cache
-rwxr-xr-x 1 mythtv   mythtv   55077 2011-02-20 23:48 FLVPlayer.swf
lrwxrwxrwx 1 root     root        21 2011-02-03 18:05 music -> /var/lib/mythtv/music
lrwxrwxrwx 1 root     root        26 2011-02-03 18:05 recordings -> /var/lib/mythtv/recordings
lrwxrwxrwx 1 root     root        30 2011-02-03 18:05 tv_icons -> /var/cache/mythweb/image_cache
lrwxrwxrwx 1 root     root        22 2011-02-03 18:05 video -> /var/lib/mythtv/videos
lrwxrwxrwx 1 root     root        22 2011-02-03 18:05 video_covers -> /var/lib/mythtv/videos
d


Clearly I need to reset mythweb's links, but I don't know how to do this.


here's some other info:

1. localhost/mythweb/video  - shows all of my movies but when I click on the title I get this error:
Not Found
The requested URL /mythweb/data/video/MyMovie.m4v was not found on this server.

2. localhost/mythweb/settings/mythweb  -  I tried the various tabs but there are no relavent settings to change

3. localhost/mythweb/settings/video  - I scanned the list of parameters and VideoStartupDir = /home/mythtv/videos (which is correct)

Fixing the links will need to be done via a terminal. Delete the current link (eg. /var/www/mythweb/data/videos), then see this link for how to create symbolic links.
[http://help.hardhathosting.com/question.php/95](http://help.hardhathosting.com/question.php/95)

On the same note, don't place the storage directories inside the home directory. I've seen that cause way too many issues.

---

### Post by nhtrader on 2011-03-07
> **tgm4883 said:**
> On the same note, don't place the storage directories inside the home directory. I've seen that cause way too many issues.

I moved the directories b/c I wanted to be able to backup the system without all of the user data files (recordings, etc.). Plus it would be easier to replace a HDD when all of the user data is separate from the system.

As for the changing the links, I'll read the reference cited.

---

### Post by nhtrader on 2011-03-07
> **tgm4883 said:**
> Fixing the links will need to be done via a terminal. Delete the current link (eg. /var/www/mythweb/data/videos), then see this link for how to create symbolic links.
[http://help.hardhathosting.com/question.php/95](http://help.hardhathosting.com/question.php/95)


Well, I changed the symbolic link and got this error message:


Downloading File
Name: MyMovie.m4v (1.1 Gb)
From: localhost
Open with: Other Application...
Remember choice and do not show dialog again
Help | Cancel | Save | Open

I selected Open and it opened the file manager.


Here's what I did...

sudo su
cd /var/www/mythweb/data
rm video
ln -s /home/mythweb/videos  ./video

Apparently, I didn't create the correct link. 


Before I made this change, there were two symbolic links:

/var/www/mythweb/data/video -> /var/lib/mythtv/videos
/var/www/mythweb/data/video/videos -> /home/mythtv/videos

Note that the video link contained a videos link.


What do I do next?

---

### Post by nhtrader on 2011-03-07
For those that tread after me, I just lost all of my videos!

Here's what I did...

I was following symbolic links and discovered that I had two copies of my videos.
One copy was in where I expected it to be - /home/mythtv/videos
and the other copy was in /var/lib/mythtv/videos/videos. So I deleted the file in the second location. 

Then I removed/deleted the following directory:
/var/lib/mythtv/videos/videos

and now have
/var/lib/mythtv/videos

Then I noticed all of my movies in /home/mythtv/videos are gone!

Caution! renaming links can be hazardous to your movies. What I don't understand is why the original files were deleted?

---

### Post by tgm4883 on 2011-03-07
> **nhtrader said:**
> For those that tread after me, I just lost all of my videos!

Here's what I did...

I was following symbolic links and discovered that I had two copies of my videos.
One copy was in where I expected it to be - /home/mythtv/videos
and the other copy was in /var/lib/mythtv/videos/videos. So I deleted the file in the second location. 

Then I removed/deleted the following directory:
/var/lib/mythtv/videos/videos

and now have
/var/lib/mythtv/videos

Then I noticed all of my movies in /home/mythtv/videos are gone!

Caution! renaming links can be hazardous to your movies. What I don't understand is why the original files were deleted?

That isn't entirely accurate. First, you didn't rename any links, at least not in any of the posts you made here. Second, in the posts that you did make, none of that should have deleted your videos, so I must guess that the syntax was slightly different. It also may have depended on exactly where the mount point was for the link, and exactly what you deleted.

In any case, what's done is done. You may be able to recover some of it, but I'm unfamiliar with file recovery. Does the /var/www/mythweb/data/ directory contain the correct symbolic link now?

---

### Post by nhtrader on 2011-03-08
> **tgm4883 said:**
> 
In any case, what's done is done. You may be able to recover some of it, but I'm unfamiliar with file recovery. Does the /var/www/mythweb/data/ directory contain the correct symbolic link now?

1. I don't know. What should it be?

2. All I'm trying to do is get MythWeb to play a movie that uses *.m4v. MythTV plays this movie, but I can't get MythWeb to play a movie.

What should I do?

---

### Post by nickrout on 2011-03-08
> **nhtrader said:**
> 1. I don't know. What should it be?

it should point to the directory where your movies reside.
> 
2. All I'm trying to do is get MythWeb to play a movie that uses *.m4v. MythTV plays this movie, but I can't get MythWeb to play a movie.

What should I do?

get the link right.

---

### Post by nhtrader on 2011-03-08
> **nickrout said:**
> it should point to the directory where your movies reside.


get the link right.


I've tried what you've suggested many times...


here are the links I created...

enter terminal mode
sudo su
cd /var/www/mythweb/data
rm video
rm video_covers

ln -s /home/mythtv/videos  ./video
ln -s /home/mythtv/videos  ./video_covers

cd /home/mythtv/vidoes
chown mythtv:mythtv  mymovies.m4v


Now open MythWeb
select Movies Icon
Movies Appear
Click Movie title

Then I get the following prompt:

   Downloading File...

Name: MyMovie.m4v
Type: unknown
From: localhost
Open With: Other Application

Buttons: Help | Cancel | Save | Open


I don't know what this means? So I attempted to select a program (media player) to play the movie. I chose /usr/bin/vlc and another dialog box appears with "File Manager" showing me my directories.

What is the right link?
What is the path to MythTV's internal media player?
What do I do to get Mythweb to play a movie?

---

### Post by tgm4883 on 2011-03-08
> **nhtrader said:**
> I've tried what you've suggested many times...


here are the links I created...

enter terminal mode
sudo su
cd /var/www/mythweb/data
rm video
rm video_covers

ln -s /home/mythtv/videos  ./video
ln -s /home/mythtv/videos  ./video_covers

cd /home/mythtv/vidoes
chown mythtv:mythtv  mymovies.m4v


Now open MythWeb
select Movies Icon
Movies Appear
Click Movie title

Then I get the following prompt:

   Downloading File...

Name: MyMovie.m4v
Type: unknown
From: localhost
Open With: Other Application

Buttons: Help | Cancel | Save | Open


I don't know what this means? So I attempted to select a program (media player) to play the movie. I chose /usr/bin/vlc and another dialog box appears with "File Manager" showing me my directories.

What is the right link?
What is the path to MythTV's internal media player?
What do I do to get Mythweb to play a movie?

So that "error message" you think you are getting, means you have it set up correctly on the mythweb system. 

Mythweb isn't going to play the movie directly, you will need an external program to do that. VLC might work, but I haven't tried it.

---

### Post by nhtrader on 2011-03-08
> **tgm4883 said:**
> So that "error message" you think you are getting, means you have it set up correctly on the mythweb system. 

Mythweb isn't going to play the movie directly, you will need an external program to do that. VLC might work, but I haven't tried it.


Well, that's a surprise. So this is normal behavior for MythWeb; not to play a movie. I didn't expect that.


Am I correct if I said that Mythweb only delivers content but does not play it. That Mythweb only fetches the content and the PC receiving the content must provide the media player.

Therefore if I want to stream a movie from my MythBox; there are three pre-requisites. 1. The content being delivered by MythWeb must be in a format that facilitates streaming (such as flash or m4v). 2. The client PC receiving the content must have a media player that can play streaming content (such as flash player, flowplayer, etc). 3. The client PC receiving the content must have the necessary codecs to play the content.

Or, MythWeb can't be used to stream movie content and only functions as a file transfer client, much like FTP. It has no playback functionality for movies.



What media player do you use?

Where is the config file for MythWeb so that I can set the default media player and its path?

How can I set MythWeb to use MythWeb's flowplayer to play movies in *.m4v or other streaming format?

Is it possible to set MythWeb to use MythTV's internal media player as the default? (this question addresses my confusion with respect to how all of this works)

---

### Post by nickrout on 2011-03-08
> **nhtrader said:**
> Well, that's a surprise. So this is normal behavior for MythWeb; not to play a movie. I didn't expect that.



it's your browser, not your mythweb that is doing that

---

### Post by nhtrader on 2011-03-08
> **nickrout said:**
> it's your browser, not your mythweb that is doing that

What does that mean? 

Perhaps you might answer this. When accessing mythweb through my browser, can mythweb play a movie?

Secondly, how about taking a stab at answering any of the previous questions that I asked?

It would help me to understand mythweb better; being that I don't know of anyone who uses MythTV besides those of you here in this forum. I would gladly ask someone in my Town about using MythTV, but everyone I ask has never heard of it.

---

### Post by nickrout on 2011-03-08
> **nhtrader said:**
> What does that mean? 

Perhaps you might answer this. When accessing mythweb through my browser, can mythweb play a movie?

Secondly, how about taking a stab at answering any of the previous questions that I asked?

It would help me to understand mythweb better; being that I don't know of anyone who uses MythTV besides those of you here in this forum. I would gladly ask someone in my Town about using MythTV, but everyone I ask has never heard of it.

The problem is that your web browser doesn't know what to do with an m4v file. That's why it asks you. Generally you should choose you favourite movie playing software. Alternatively you could download the file to your hard drive and then play it like any other movie file.

---

### Post by nhtrader on 2011-03-08
Thank you.

Now, with that said, is there a way to get the movie to viewed/played in the same manner as a TV recording can be played using flowplayer?

In essence you taught me how to configure mythweb so that the *.mpg TV recordings could be converted in realtime to flash video and then streamed to the browser on the remote PC which utilized mythweb's "flowplayer". Can I do the same thing with movies in *.m4k or *.mkv ?

---

### Post by nickrout on 2011-03-09
> **nhtrader said:**
> Thank you.

Now, with that said, is there a way to get the movie to viewed/played in the same manner as a TV recording can be played using flowplayer?

In essence you taught me how to configure mythweb so that the *.mpg TV recordings could be converted in realtime to flash video and then streamed to the browser on the remote PC which utilized mythweb's "flowplayer". Can I do the same thing with movies in *.m4k or *.mkv ?

I can't see a link for that, but possibly the code for the flowplayer for recordings could be used.

---

### Post by geekyhawkes on 2011-03-10
Im glad im not alown with this.  If you get it to work could you let me know please?  Thanks.

---

### Post by nhtrader on 2011-03-11
> **geekyhawkes said:**
> Im glad im not alown with this. If you get it to work could you let me know please? Thanks.
 
Well, here's one configuration that works:
 
PC1=Desktop with Mythbuntu 10.10 (32 bit) FE+BE using MythTV v0.24-206
     MythWeb enabled and password protected
 
PC2=Win7 Laptop using IE8 as my browser. When I select the Movie from the MythWeb page, IE8 automatically uses MSFT Media Player and starts playing the movie immediately (in streaming mode). 
 
Please note that this laptop has been used extensively for testing various interfaces with MythTV. Therefore, after installing XBMC and various windows versions of MythTV's Frontend for Windows, I don't know if the codecs for *.m4v are native to Win7 or not. I've installed/uninstalled many media players on this PC and do not know how this has affected the number of codecs that remain.  However, I am reporting that this configuration works.
 
 
 
Here's a configuration that does not work:
 
PC1=Desktop with Mythbuntu 10.10 (32 bit) FE+BE using MythTV v0.24-206
     MythWeb enabled and password protected
 
PC2=Desktop with Mythbuntu 10.10 (32 bit) FE only using MythTV v0.24-206. This PC uses Opera 11.01 as the browser and selecting a movie from MythWeb does not play. In addition, I've tried to change Opera's Preferences by adding a MIME type for *.m4v. But I'm fishing. I really don't know the correct MIME type and have been trying various combinations with no luck. Such as...
video/mpeg-4
video/x-flv
application/x-shockwave-flash
 
and I've tried selecting the default application to /usr/bin/vlc or the libflashplayerplugin.so
 
Again, so far no luck.

---

### Post by nhtrader on 2011-03-12
Here's another configuration, but this one partially works. By that I  mean this configuration is semi-automatic. It will play the movie but  only after the movie has completely downloaded and then it will use VLC  as the media player.

PC1=Desktop with Mythbuntu 10.10 (32 bit) FE+BE using MythTV v0.24-206
      MythWeb enabled and password protected
  
PC2=Desktop with Mythbuntu 10.10 (32 bit) FE only using MythTV  v0.24-206. This PC uses Firefox 3.6.15 as the browser and selecting a  movie from  MythWeb does not play until after the entire movie downloads. In  addition, once it is downloaded, a prompt appears which allows you to  choose your media player. The good news is that the default player is  VLC and it can play *.m4v files. 

Again, this configuration will play a movie, but not as I had expected  it would. I'm expecting the movie to be played in streaming mode and it  appears that Mythbuntu 10.10 does not have its default webbrowser  firefox configured to stream *.m4v files. I  wouldn't expect other distros to be able to play these kinds of videos,  but Mythbuntu is a media-centric distro and this oversight should be  corrected in future updates.

BTW, the only reason why I am attempting to play *.m4v files is b/c  MythTV v0.24 no longer rips movies and I was forced to install another  package called handbrake, and its default uses Mpeg4 format. Then I  selected the option "web optimized" so that progressive downloads are  possible (streaming mode). This creates *.m4v or *.mkv files. 

MythTV v0.23.1 was the last version to rip DVDs directly into mpeg2  format which produced *.VOB files. And I have not updoaded a movie in  *.VOB format yet so that I might test how this format performs with the  various webbrowsers. But I will admit that this be unproductive, since  my goal is to watch movies remotely outside of my local network. 

I'm interested in streaming mode and streaming such large files (4.7Gb)  will not work with my limited outbound bandwidth. So it was  serendipitous for me to explore handbrake and discover that it natively  creates web formatted video files that can be streamed (prior to this I  didn't know that this was possible - single pass conversion. I was under  the impression that I would have to create them using multiple steps  such as converting multiple VOBs into single mpeg into flash video). I  was thrilled to learn that I can rip a movie directly into *.m4v So I am  devoting my efforts into exploring how to get these smaller files ( a 1  hour and 40 minute movie is now only 800Mb in size) to play in the  various browsers: IE8, opera, firefox, chrome on the various operating  systems.

---

### Post by geekyhawkes on 2011-03-13
Thanks for the info above nhtrader but i think your problems are different to mine (from the orignal post).  Mythweb cant find my video files so the issue i am having is on the server side.  your above details (nicely described for all popular browsers) seem client side to me.

---

### Post by nickrout on 2011-03-13
> **geekyhawkes said:**
> Thanks for the info above nhtrader but i think your problems are different to mine (from the orignal post).  Mythweb cant find my video files so the issue i am having is on the server side.  your above details (nicely described for all popular browsers) seem client side to me.

Did you change the symlink? refer earlier in this thread. If your videos are not in /var/lib/mythtv/videos then the symlink will be wrong.

---

### Post by nhtrader on 2011-03-14
In continuing my quest to get MythWeb's Video links to play *.m4v files directly, I've stumbled upon a clumsy solution for Opera and Firefox users.

The solution is as follows:
1. copy the web address from MythWeb's Video links (right-click: select copy link address)

2. open vlc (select: Applications|MultiMedia|VLC media player)
3. select Media Menu|Open Location from Clipboard  (your URL should be automatically be visible)
4. select play button.
5. enter Mythweb's username and password
6. movie plays.

Still not the holy grail, but it helps to know that this works.

---

### Post by nhtrader on 2011-03-14
I finally figured out how to play m4v video files on Mythbuntu 10.10 using xfce 4.8.1 with Firefox and Opera browers.

The trick was to use synaptic to install a package: gecko-mediaplayer and all of its dependencies (which includes gnome-mediaplayer).

Once this package was installed the gecko-mediaplayer.so plugin was installed automatically into Firefox and Opera.

Now when I click on movie link (*.m4v) in MythWeb-Video, the movie plays in the browser in progressive/streaming mode, which is what I wanted.

I can now use my remote linux PCs with either Firefox or Opera to watch a movie using MythWeb. Awesome!



And if you want to eliminate the annoying download prompt and play the movie directly, all you need to do is change the apache configuration file for MythWeb.

Here's how you insert a MIME type:
(locate the other MIME types in the file and insert the following entry at the bottom of the list.)
sudo pico /etc/apache2/sites-available/mythweb.conf

AddType    video/x-m4v    .m4v

save and exit
must restart computer for change to take affect

---


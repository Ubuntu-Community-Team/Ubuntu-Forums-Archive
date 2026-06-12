---
title: "Video Manager, IMDB search crashes"
date: 2009-09-06
forum: Mythbuntu
---

### Post by MonsterMaxx on 2009-09-06
First oddity is that when I go into the video manager, there's a box already up that says 'Enter IMDB #' But it's not active or anything, I can scroll thru normally.

When I try to execute the search it says "user/share/mythtv/mythvideo/s (the rest is truncated so I don't know exactly what is the file)
failed: not executable
Check VideoManager settings.
Press 'ok' and that's the last thing the frontend will do, it's locked up.

It was working fine when I tried it a few months ago, last night I tried to add a few vids and it locks up.
I don't recall making any changes to videomanager settings, doesn't mean I didn't, just don't remember doing so.

Could this possibly be related to what I did to fix this problem?
[http://ubuntuforums.org/showthread.php?t=1209139](http://ubuntuforums.org/showthread.php?t=1209139)

---

### Post by SiHa on 2009-09-07
Have you looked in Video Manager settings? (Settings > Media Settings > Video Manager, I think). Is there a box there to specify a script to run. I'm guessing it's pointing to a script in**/usr/share/mythtv/mythvideo/scripts/**. Does this script exist? Is it executeable?

Hold on - whilst typing this out, I unconciously typed /usr/share... not /us**[COLOR="Red"]e[/COLOR]**r/share. In your post it's 'user' - it should be 'usr'

So hopefully, it's one of two things:

1) You've accidentally changed the path in Video Manager settings, change 'user' back to 'usr'.

2a) It's 'usr', and you just typed 'user' in the post, in which case...

2b) Perhaps the script has accidentally had it's ownership or permissions changed. If, for example it's called **/usr/share/mythtv/mythvideo/scripts/script.sh** then ```
sudo chmod a+x /usr/share/mythtv/mythvideo/scripts/script.sh
``` will make the script executeable by all.

...assuming the script exists

---

### Post by MonsterMaxx on 2009-09-07
fyi: it's a typo when I posted the problem here.. the actual error message has ** /usr/**


Nothing like what you suggest that I can find

It goes
Setup->Media Settings->Videos Settings->
Then there's
General Settings
Player Settings
File Types
Rip Settings

no place to define that script in any of these


did the chmod as you suggested, now there's a whole diarrhea of error messages beginning with:
 
Can't locate Mythtv/MythVedoeCommon.pm in @INC (@INC
contains: /sur/share/mythtv/myt
/usr/local/share/perl/5.10.0 /uusr/
.
.
.

but, it's not crashed.

---

### Post by dsbw on 2009-09-07
Yeah, I have the same problem with the IMDB# pop-up.

Mine didn't work either; I tried replacing it with the updated TMDB script, and no dice.

---

### Post by williammanda on 2009-09-07
> **MonsterMaxx said:**
> First oddity is that when I go into the video manager, there's a box already up that says 'Enter IMDB #' But it's not active or anything, I can scroll thru normally.

When I try to execute the search it says "user/share/mythtv/mythvideo/s (the rest is truncated so I don't know exactly what is the file)
failed: not executable
Check VideoManager settings.
Press 'ok' and that's the last thing the frontend will do, it's locked up.

It was working fine when I tried it a few months ago, last night I tried to add a few vids and it locks up.
I don't recall making any changes to videomanager settings, doesn't mean I didn't, just don't remember doing so.

Could this possibly be related to what I did to fix this problem?
[http://ubuntuforums.org/showthread.php?t=1209139](http://ubuntuforums.org/showthread.php?t=1209139)

I went through this last night. Apparently IMDB is no longer being using and tmdb ([http://www.themoviedb.org/]("http://www.themoviedb.org/")) is...but the mythtv world isn't totally on aboard yet. To get the cover art and metadata now you need to add the tmdb script located here:

[URL="http://www.mythtv.org/wiki/Tmdb.pl"]http://www.mythtv.org
/wiki/Tmdb.pl[/URL]

and then use this to rid the constant "enter IMDB #"

```
find /usr/share/mythtv/themes/ -name "video-ui.xml" -print | xargs sudo sed -i 's/enterimdb/entertmdb/g'
```

While this works on my master backend the slave backend doesn't see the cover art. Also when I add or delete a video and use the slave backend and adjust the videos using the video manager...the metadata & cover art is lost. So this is a work around but not a total fix. If anyone has a better fix, please post.
Thanks

---

### Post by dsbw on 2009-09-08
Well, the IMDB # fix worked, but I still don't see any movie posters. (The other data downloads and it says it's downloading the posters with no errors--but no pix in video manager.)

---

### Post by williammanda on 2009-09-08
> **dsbw said:**
> Well, the IMDB # fix worked, but I still don't see any movie posters. (The other data downloads and it says it's downloading the posters with no errors--but no pix in video manager.)

Check /var/lib/mythtv/posters...make sure the permissions are setup correctly.
Thanks

---

### Post by williammanda on 2009-09-08
9> **williammanda said:**
> 
While this works on my master backend the slave backend doesn't see the cover art. Also when I add or delete a video and use the slave backend and adjust the videos using the video manager...the metadata & cover art is lost. So this is a work around but not a total fix. If anyone has a better fix, please post.
Thanks

Update 9/8/09
I had videos on two different drives /var/lib/mythtv/videos and another drive. I was using a symlink to get them all together. Apparently Mythtv needs to see them all from /var/lib/mythtv/videos. I moved all the videos to the other hard drive and made the videos directory a symlink to the other hard drive. Also I had to use nfs to get the cover art to the slave backend. Everything seems to be functioning as expected.

---


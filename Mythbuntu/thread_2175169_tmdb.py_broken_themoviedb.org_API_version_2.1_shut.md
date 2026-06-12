---
title: "tmdb.py broken? themoviedb.org API version 2.1 shutdown 15th September"
date: 2013-09-17
forum: Mythbuntu
---

### Post by RavenB72 on 2013-09-17
I am  new to Mythbuntu.
 My movies suddenly stopped updating in my video library. I traced the issue to tmdb.py and found it is using version 2.1 of the TMDb API. A google search revealed that it has been shut down and replaced with version 3.
Is there an update for this or work around for this? I am using the latest available build of Mythbuntu.

Cached page with the notice: [http://webcache.googleusercontent.com/search?q=cache:sNIfEnSSWBMJ:api.themoviedb.org/2.1/+&cd=1&hl=en&ct=clnk&gl=us](http://webcache.googleusercontent.com/search?q=cache:sNIfEnSSWBMJ:api.themoviedb.org/2.1/+&cd=1&hl=en&ct=clnk&gl=us)

Thanks

---

### Post by RavenB72 on 2013-09-17
It looks like Version 3 of the API had been included in later releases of MythTV. It's in the current repository at the very least. It looks like TMDB updates won't work for the current release of Mythbuntu (12.04.3).

---

### Post by tgm4883 on 2013-09-18
> **RavenB72 said:**
> It looks like Version 3 of the API had been included in later releases of MythTV. It's in the current repository at the very least. It looks like TMDB updates won't work for the current release of Mythbuntu (12.04.3).

That isn't entirely true, the Mythbuntu team provides updated packages for 12.04.3. You need to use tmdb3.py.

---

### Post by newlinux on 2013-09-18
> **tgm4883 said:**
> That isn't entirely true, the Mythbuntu team provides updated packages for 12.04.3. You need to use tmdb3.py.

I discovered this yesterday too. I'm on 12.04.2 for most of my machines and tmdb3.py is there and works.

It's in

/usr/share/mythtv/metadata/Movie/

just like tmdb.py

---

### Post by RavenB72 on 2013-09-18
Thank you for the clarification. I did see tmdb3.py. I tried calling it from the command line but it generated errors. I can't find any reference material for the parameter format. Does it require different parameters? 
Can you tell how to configure MythTV to use this script instead of tmdb. py or point me to a reference?

---

### Post by newlinux on 2013-09-18
```
tmdb3.py -h
```

Will give you usage information if running it commandline. you could try

```
tmdb3.py -M "World War Z"
```

As for configuring with myth I didn't even bother looking for a place. I just removed the existing tmdb.py and renamed tmdb3.py tmdb.py and it worked fine for the two files I tried in mythvideo. So I'm guessing it takes the same parameters. this might not be the right way to do it, but since the old tmdb.py is never gonna work again anyway I didn't see any issue with it.

---

### Post by RavenB72 on 2013-09-19
I gave this a try last night and this approach does seem to work fine. Thanks.

This is a related question, not sure its worth another thread?

I am still not able to get my TV Shows to update. I created two folders "/var/lib/mythtv/videos/Movies" and "/var/lib/mythtv/videos/TV Shows". If I put TV show files in the The TV Shows folder should the ttvdb.py script run on this folder or is it only run on recorded content?

The script does return good data if I run it from the command line. The Example file I used was "Once Upon A Time S01E01.mp4".

Maybe I am not using the video folder as I should?

---

### Post by RavenB72 on 2013-09-20
Looking at the logs it does appear that the script is being called, it just doesn't do a very good job at resolving the program titles. XBMC seems to do a much better job.

---

### Post by qsilver7 on 2013-09-29
System status shows my TV metadata lookup failing since I change the tmdb3.py to tmdb.py. Would this affect tv lookup?

---

### Post by newlinux on 2013-09-29
I think the issue is that the tv metadata call is looking to use a -t option for tmdb.py that doesn't exist anymore. So it fails.  Perhaps newer versions of myth don't use this option? Or there's a place in mythtv configuration to tell it not to use this option?

Rather than search for that I think I'll just modify tmdb.py to take a -t argument and do nothing. in the 2.1 tmdb.py this was simply used to test for availabilty of runtime dependencies. So I'll just modify the new script to return true when given -t.

---


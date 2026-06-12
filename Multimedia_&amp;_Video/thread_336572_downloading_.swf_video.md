---
title: "downloading .swf video"
date: 2007-01-11
forum: Multimedia &amp; Video
---

### Post by igeterrors on 2007-01-11
OK, so let's say that there was a video of me [**here.**]("http://www.brilliantbutcancelled.com/shows/top_chef_rejects.php")  Never mind which one I am, it's too embarrassing.  But all I want to do is download and save it -- I already *have* the video, of course, but not with that little "Bravo" logo on it, which I think is kind of cool.

I think it's posted as a Shockwave movie.  I have the Firefox VideoDownloader extension but it won't recognize the URL.  Still, I can play it on my computer just fine.  

What's making me crazy is my instincts tell me that if the video can be played on my computer, it must exist on my computer *somewhere,* even if only for the duration of playback.  While it's playing, it's occupying RAM and maybe even being written to my swap partition.  So there's got to be a way of saving it, right?  It's just something I haven't thought of, or more likely something I don't know about.

Any thoughts?  Thanks.

---

### Post by maximilian35 on 2007-01-19
May be you can try to download it by typing:
```
mplayer <url> -dumpstream -dumpfile file_name.swf

```
I can't guarantee it but just an idea.:rolleyes:

---

### Post by Mis_Uszatek on 2007-01-19
Yep, it is true.
The video is in your web browser cache.
Everything what are you watching, you may 'download'.
swf, flv, avi and so on...

Simple method, locate cache dir of your browser (for Opera it would be ~/home_directory/.opera/cache/cache4
In that directory there should be a lot of files.
Clear cache(remove all files from it), open browser, watch movie, look into cache. Big files with latest date. 

That's all

---


---
title: "Odd video file icon"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by murphykieran on 2008-03-12
I'm not sure this is the right forum, so feel free to move it to the correct place.

I've got an odd problem.  I have a video file on my Ubuntu system that has a history.  My brother originally had it on his Windows laptop and he gave it to me via USB key and I put it on my own Windows desktop.  It was then put onto my Creative Zen MP3 player.

Since then, I have migrated over to Ubuntu on my desktop.  Today, I eventually successfully  got my Creative Zen working and as part of testing the device, copied over the aforemention video file into my Videos folder.

The file is okay and working no prob, but has an odd problem.

Other files in the same folder, the icon looks like a random frame taken from the video.  The video file in question however, has an icon that looks like a frame from a pornographic movie.  It shows a shot of a woman with her hands around a naked guy.

I'm not prudish so this doesn't bother me at all, but it just strikes me as bizarre, because the video file in question isn't pornographic at all the the screengrab in question is obviously not from the video it represents.  I can host the file somewhere online if someone needs to see the files in question, but can anyone explain such a bizarre occurance - a pornographic scene being put up as the image icon for a video that isn't porno in anyway?

---

### Post by mgmiller on 2008-03-12
That really is strange.   If the file is an .avi, try opening it in avidemux and then slowly scroll through it frame by frame to see if that frame just might be in there.  If it is, you can edit it out with avidemux and then resave it.  
If you don't have avidemux:
```
Sudo apt-get install avidemux
```

If it's not an .avi, you can play it in vlc and click the "play slower" button a few times to get it to show frame by frame.

---

### Post by murphykieran on 2008-03-12
I know without reading the FAQs that posting about pirated stuff is probably frowned upon (like all forums), but here goes anywhere.  The video in question is a copy of the documentary "King of Kong" and has been already converted in Windows to a low quality version suitable for the Zen.  It looks **** in Ubuntu because it's low-res, but I'm just stumped about the random porno scene.

I'll try what you already suggested and see what happens.  Thanks for the reply.

---

### Post by murphykieran on 2008-03-12
Here's a link to the icon that appears in Ubuntu.  I've blown it up 200% for clarity.

Possibly NSFW:
[[IMG]http://img80.imageshack.us/img80/848/kong2lt7.th.jpg[/IMG]](http://img80.imageshack.us/my.php?image=kong2lt7.jpg)

---

### Post by mgmiller on 2008-03-12
The only thing I can think of is, since I am assuming it's pirated, based on your statement:
>  I know without reading the FAQs that posting about pirated stuff is probably frowned upon 
I suspect there is some interesting random stuff embedded in it.  Possibly even malware that could cause a windows system to try to go to a porno site when viewing the video, or just a link to one with a racy picture as a teaser.  It's no danger to Ubuntu, but you may want to check your windows boxes for spyware, just to be safe.

My helping you with this in no way implies that I condone downloading pirated software.  Discussion of pirated software is frowned upon in these forums.  

I was just intrigued by the weird problem.

Let me know what you find in a "frame by frame" analysis.

---


---
title: "[Amarok 1.4.5 + libgpod1] Artwork still doesn't work on ipod"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by derbouka on 2007-02-28
Hi!

I'm trying to get the Artwork to work on my ipod, but those small covers just don't show.. :(

I'v a iPod blue nano 4 GB, and I'v installed Amarok 1.4.5 and libgpod1 in my Festy Ubuntu version.
I think that it must be something wrong when it sends the covers to the ipod, since in my ipod, when I play a song that should have a cover, it shows the song info(text) aligned left and before this new version of amarok and libgpod it showed the text aligned at center.
I think that maybe it's already saying that it has a cover, but the file is missing or something :confused: 

Does anyone know how to solve this issue?

Best regards.

---

### Post by estebancs on 2007-02-28
Don't know how to fix it, (I haven't even tried amarok) but I suggest using gtkpod instead [http://www.gtkpod.org](http://www.gtkpod.org)

---

### Post by derbouka on 2007-02-28
> **estebancs said:**
> Don't know how to fix it, (I haven't even tried amarok) but I suggest using gtkpod instead [http://www.gtkpod.org](http://www.gtkpod.org)Can't get it to work with gtkpod either..:(
When I start the ipod with gtkpod it said this:
```
iTunesDB '/media/DANIEL BOTE/iPod_Control/iTunes/iTunesDB' does not match checksum in extended information file '/media/DANIEL BOTE/iPod_Control/iTunes/iTunesDB.ext'
gtkpod will try to match the information using MD5 checksums. This may take a long time.

```

---

### Post by estebancs on 2007-03-01
I think I get the same message everytime I sync my ipod with any oter program that isn't gtkpod, (I still use itunes to sync movies)... but after I get that messages it still works great... In your case it gives you that message because you haven't synced with gtkpod but with itunes (I guess) but once you sync with gtkpod it won't give that message anymore (unless you sync again with itunes)... To get artwork working I make gtkpod read the database (as I said sometimes I get the same message), I update the artwork and then I hit the sync button, and I see at the bottom of the screen writing to ipod's DB or something like that.... and that's it!... well that's for me I've heard that gtkpod may work very different for some people... sometimes it always work (in my case), sometimes it never works, or it works ramdomly....

Oh... if you don't get gtkpod working you should try banshee

[http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

---


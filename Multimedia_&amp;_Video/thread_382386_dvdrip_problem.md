---
title: "dvd::rip problem"
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by pdrift on 2007-03-12
i'm having trouble with dvd::rip lately which kinda sucks because i was in the process of ripping my movie collection to xvid avi. 

i have used this program only a couple of days ago and it was working wonderfully. i did about 7 movies already with it.

now for some reason it hangs after it rips the title. it seems that whatever is wrong it has to do with the preview grabbing. i know it ripped the title because i can see the vob files it created and if i click on the vob's they play just fine. 

i tried different movies, even movies that i have already successfully transcoded toxvid avi and it just does the same thing no matter what

it rips the title then hangs. it won't grab any previes and it won't let me transcode.
the transcode option is grayed out .

i tried uninstalling and then reinstalling but i still get he same results. i tried using acidrip instead but my dvd player doesn't like to play nice with movies i encode with it. 

i hope i can sort this out with some help because i love this program. my movies fit on a cd and had great quality.

---

### Post by 454redhawk on 2007-03-12
I gave up on dvd:rip

I now use acidrip. Works like a charm and very easy to use.

---

### Post by pdrift on 2007-03-12
yeah i like acidrip too but for some reason my movies don't playback nice on my dvd player after i burn them to cd.
i use gnomebaker to burn to cd just like i do for movies done with dvd::rip
the movies jump and stutter a lot. 

what settings do you use for your movies?

---

### Post by 454redhawk on 2007-03-12
xvid options
chroma_opt:vhq=4:bvhq=1:quant_type=mpeg

mp3lame options
abr:br=96

They seems to work pretty good on my standalone dvd player.

---

### Post by jocheem67 on 2007-03-13
It's probably a transcode problem. 

You can watch the log created within dvd::rip and hopefully there's an errormessage.

An option: try to uninstall dvd::rip completely, you could use the beautiful program gtkorphan  ( sudo gtkorphan from the command-line ) . 
Also get rid of the .dvdrip in your home directory...

another option: try to convert with ffmpeg within dvd::rip. Maybe it's xvid-related ?

did you install new packages lately ?

Last way, compile dvd::rip yourself ?

---


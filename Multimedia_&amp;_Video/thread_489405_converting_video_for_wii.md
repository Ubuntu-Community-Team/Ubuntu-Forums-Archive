---
title: "converting video for wii"
date: 2007-07-01
forum: Multimedia &amp; Video
---

### Post by williamwade on 2007-07-01
**This post could be related to an Ubuntu bug filed at**: wii video [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				is there an ubuntu program that will convert videos for my wii?

if not 

should i set up avidemux/vlc to encode it?

---

### Post by motang on 2007-08-20
I am wondering the same thing, I tried out avidemux but I had no luck.  I was able to make the files into motion JPEG but they didn't play on the Wii.  So I am hoping someone out there will make something like [Wii Video 9]("http://www.redkawa.com/videoconverters/wiivideo9/").

---

### Post by motang on 2007-08-20
Well I found this on Google, and tested it out and it works very well.  So here is what you got to do.

1. Install **mencoder** if you don't have it already on your system.
> sudo apt-get install mencoder
2. After mencoder is installed on your system go to the directory where the video file is located (in terminal) and type this:
> mencoder videofilename.avi -fps 29.97 -ovc lavc -lavcopts \
3. followed by:
> vcodec=mjpeg -oac pcm -vf scale -zoom -xy 512 -o videofilename.avi
4. Wait for the encoding to finish and once it's done make sure the file plays on your system by typing in:
> mplayer videofilename.avi
or
totem videofilename.avi
Once you are done with that you can copy it over to your SD card and play the file on your Wii with the_ Photo Channel_.

source: [http://icculus.org/~dolson/wii-video-conversion.html]("http://icculus.org/~dolson/wii-video-conversion.html")

Hope this helps, as it worked on mine.

---

### Post by williamwade on 2007-08-25
yay for you!

Thanks for this, sorry it took so long for me to respond but i've been having computer problems.

---


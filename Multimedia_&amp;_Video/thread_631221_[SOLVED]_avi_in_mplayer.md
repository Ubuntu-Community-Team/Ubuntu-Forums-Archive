---
title: "[SOLVED] avi in mplayer"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Bheegerji on 2007-12-04
"Error! 
Failed to open file :///home/username/videos/filename.avi"

Earlier when I tried to play any video file in MPlayer, I used to get this message

"Error opening/initializing the selected video_out (-vo) device"
That error was solved when the edited the GUI.conf file replacing the line
 vo_driver = "xv"   with   vo_driver = "gl".

And then most formats would play. But not .avi files.

So, I searched these forums and found some solved cases similar to mine.
Accordingly, I changed vo_driver to x11.
And
v_vfm = "ffmpeg"
a_afm = "ffmpeg"

But of no use. What should I do?

---

### Post by banewman on 2007-12-04
It's not a true solution to your issue but I found vlc as a media player handles everything I throw at it. :)

---

### Post by Bheegerji on 2007-12-04
thanks but I think mPlayer can handle avi. Whats so different in my case?

---

### Post by njparton on 2007-12-04
.avi is just a wrapper and the video inside can be encoded with a multitute of codec including divx, xvid etc etc.

Are you having problems with all avi's or just some encoded with a specific codec?

---

### Post by kelvin spratt on 2007-12-04
Now this may sound silly but I had this same problem tried everything but I did not change any config files,In the end I just uninstalled the skins and then installed the blue skin, after reading there was a problem with Mplayer and the blue skin mysteriously cured it!.Set video pref to the 2nd option now it all works plays ISO files, youtube full screen, the BBC news full  screen, and movie trailers, As well as Avi and DVD. I know this does not make sense but it worked for me.

---

### Post by Bheegerji on 2007-12-04
I've problems with all AVIs

---

### Post by Bheegerji on 2007-12-04
Hey Kelvin, here's another crazy thing. After one long hour of battle with MPlayer I decided to quit. Before I quit, I was so much attracted into SMPlayer that I decided to install it thinking it was another player. And to my relief it played every crap. After a sense of achievement , I decided to log out. Jus then, another post caught my attention. I found that SMPlayer was just another GUI for the legendary MPlayer.


Who cares whatever the crap SMPlayer is? the thing is MPlayer rocks...

---

### Post by Bheegerji on 2007-12-04
One minor problem though. Whenever I launch SMPlayer and tyy to open a file from the menu, I get three error messages in order. Here they go:

"Could not find mime type
application/octet-stream"

I give "OK", then.

"No MIME types installed"

again "OK", then,

"Malformed URL
file:///home/username"

"OK"

Then the GUI appears but I'm not able to browse through my home folders.
But i'm content that MPlayer is able to play.

If anybody has a solution, please do guide me.

---


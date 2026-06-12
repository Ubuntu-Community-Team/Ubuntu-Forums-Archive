---
title: "mythmovie not working"
date: 2010-01-09
forum: Mythbuntu
---

### Post by benlyboy on 2010-01-09
Hi all

I had to update my mythbuntu 9.10 to the latest build (22). This was to fix a the fact that I was not getting audio out of my hdmi, and it worked, all works great on that front now.

However now mythmove doesn't work. When I open it, I get the message "failed to process the grabber data"

Here is part of my frontend log

> 
2010-01-09 17:23:11.183 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/movies-ui.xml
2010-01-09 17:23:11.192 Movie Data Has Expired. Refreshing.
2010-01-09 17:23:11.196 MythMovies Data Grabber: Executing '/usr/bin/ignyte --zip 47591 --radius 10'
2010-01-09 17:23:12.419 Grabber Finished. Processing Data.
2010-01-09 17:23:12.419 Error parsing data from grabber: Error: tag mismatch Location Line: 1 Column 58
2010-01-09 17:23:12.420 Failed to process the grabber data!



Any ideas...?

---

### Post by azmyth on 2010-01-09
It doesn't work for anyone. Something was changed where the info was grabbed from. This happens every so often with myth (movie times, weather).

---

### Post by benlyboy on 2010-01-09
Oh ok so I guess we just wait till someone fixes it.

Thats cool just nice to know it's not my system.

Thanks for the info :)

---

### Post by XxDAVILxX on 2010-01-10
benlyboy, if you dont mind me asking. How did you get your HDMI audio output to work 'cause I'm getting the same problem. I just installed Ubuntu and MythTV yesterday, so please like I'm a 3 year old because I'm a complete noob at this.
 
Thanks in advance.

---

### Post by benlyboy on 2010-01-10
This is kinda the blind leading the blind here, new to this as well

But take a look at [this post]("http://ubuntuforums.org/showthread.php?t=1370228") it was how I got mine going.

But in short first update to the latest build .22.

Then I went to mythbuntu control center and found that there was a new recommended nvadia driver so I installed this.

last up, use the asound.conf file as talked about on the above post 

You never said what video chip you are using or what version of mythbuntu so I'm not sure if your system is the same as mine, but this is what worked for me. 

Hope this helps good luck

---

### Post by woodsby on 2010-01-11
I am now having this same problem.  It worked the last time I checked it - about a month ago.  Also, my mythflix is not working either.  The funny thing is my database now has no records under netflix or the movie tables.  Something weird happened, because I know that at least the netflix table had data in it because I entered it myself.  Is anyone else experiencing the same issue with mythflix?

---

### Post by mythbuntu101 on 2010-01-28
movie info not coming in due to 'grabber' . how can i fix this?

---

### Post by bbruenfl on 2010-01-29
Looks like the movie grabber is part of the compiled portion of mythtv so first, you should download and install svn so you can get a current working copy of the source code then go to mythplugins/mythnetvision/mythnetvision/ figure out how it is supposed to work then figure out what is broken and fix it.  Does that answer your question?

---

### Post by mythbuntu101 on 2010-01-29
i'm new to this. what is svn?

---


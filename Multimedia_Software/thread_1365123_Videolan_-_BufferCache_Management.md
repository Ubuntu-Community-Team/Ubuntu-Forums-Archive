---
title: "Videolan - Buffer/Cache Management"
date: 2009-12-26
forum: Multimedia Software
---

### Post by itaBannet on 2009-12-26
Hello!

I have some doubt about the cache management of vlan ...
I'm trying to watch a long video (movie) on Internet. 
My connection speed is lower than the bit-rate of the video that I'm going to watch.
In the settings of vlc you can set the cache in ms ... for example I've set 30 000ms (30 sec).
But every time I try to watch the movie it start to get the cache, after 30 secs starts to play but it stop after about 2 minutes. This means that if the average bit-rate of the video is 800kbps, the received data is about 600kbps. If the movies length is 90min, It need at least 20/25 mins of buffering to play the entire movie!
My questions is: there is an option that allow me to set an unlimited cache and let me choose when play the film?
The best way should be something that can read the length of the movie, the bit-rate of the output streaming and the speed of the incoming data and calculate how much it need to get enough buffer to play the whole video without interruptions...

---

### Post by Haitoyou on 2009-12-26
I'm not sure of how to go about doing what you ask, but I can offer you a solution to your movie problem that involves downloading the streamed movie first then watching it (you need to use firefox):

1. Open Tools/addons
2. change tab to Get Add-ons
3. Search for downloadhelper (single word, no space)

this is the image:
[IMG]http://i665.photobucket.com/albums/vv18/Haitoyou/downloadhelperinstallerpic.jpg[/IMG]

4. install it, and there will be a three colored icon most likely by your home button, if not, add it by opening View/Toolbars/Customize...


After you've done that, whenever you visit a webpage with a streaming video like youtube or whatever site you are using to stream your movie, the icon next to the home button will light up and if you left click, it will give you a download option. After that, just let it sit there until the movie finishes downloading. I should warn you, you need to close the tab with the streaming movie in order to see the true progress of the video download, cause it kinda doesn't display it while the page with the streaming video on it is still open. BE CAREFUL, YOU NEED TO KEEP FIREFOX OPEN TO CONTINUE DOWNLOADING! If the only tab you have open is the streaming video site, do not close firefox! Here is an image of how it lights up and the options:

[IMG]http://i665.photobucket.com/albums/vv18/Haitoyou/DLhelperinaction-1.jpg[/IMG]

Just click the stream video you want, and the download option, then poof, you know the rest.

And that is how the cookie crumbled...

---

### Post by itaBannet on 2009-12-27
Thank you for your tip...it could be useful...
but, in my case, it don't really solve my problem ...
I already use to download movies that i can't stream ... but is very annoying because it became a download, not a stream! In this way I always have to wait 1.30 hour to complete the download and watch the video!
I would like just to wait the minimum time I can to let load the buffer ...

---


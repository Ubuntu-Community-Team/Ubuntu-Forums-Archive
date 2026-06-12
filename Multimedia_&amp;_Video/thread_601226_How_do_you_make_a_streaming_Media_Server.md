---
title: "How do you make a streaming Media Server?"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by henrypootel on 2007-11-03
Hi All.
I have a problem. at home i have a ubuntu server box which stores all of my music/videos/photos. i also now have a laptop which usually sits in the lounge but gets moved around. it doesn't have a very big hard-drive(40gb i think), so i can't store much video on it, but i want to be able to play my videos on it(the ones that are on the server). it's networked(via wifi) to the other machine, and is currently running Windows XP Pro.
I had setup an SMB share of all the video files on the ubuntu box and was trying to play them from the laptop, but it takes ages to open the file. i assume it has to download a certain portion of the file first or something. anyway, it takes too long, so i have ditched that idea. what i really need is something capable of streaming the video on the ubuntu box, over the network to the laptop. i have tried using mediatomb, but it seems to just wait and download the whole file before playing it as well. i have also tried VLC, but that only lets me use 1 video at a time, and i have to set up the share first on the ubuntu box, which kinda defeats the purpose of the thing.
anyway, i am completely at a loss as to what to do now. basically, i think i need some sort of streaming media software that lets me choose from my library of media instead of just playing a file i have set to stream on my server.

please help!

---

### Post by Jose Catre-Vandis on 2007-11-03
Try using mplayer (yes there is a windows version)

Also try setting up NFS server (although this gets more complicated with XP, and wifi does funny things with it in terms of speed)

You may be expecting too much from your wifi in terms of speed?

Try [www.geexbox.org](www.geexbox.org). This means you would have to reboot using it's Live CD, but it does the job.

---

### Post by henrypootel on 2007-11-03
thanks, i gave it a go with MPlayer and it works fine. However, it still isn't quite what i want.
Ideally, i want to use it as a proper 'Media Centre' type app, like Elisa or Fluendo.
At the moment, i open up firefox, go tom my mediatomb bookmark, find the video i want, right-click on it and hit 'copy shortcut', open up mplayer, go to 'open URL', paste in the URL, and hit Enter. then, it works fine(no issues with wifi speed).
this is hardly smooth or easy, especially considering how good it all looks in Elise on the server itself. what i want now, is a Media-Centre application which can take my mediatomb UPnP stream and use that instead of local media.
Does anyone know what i can use?

---

### Post by Jose Catre-Vandis on 2007-11-03
Another alternative is to install gnump3d
```
sudo apt-get install gnump3d
```
It is primarily built to serve mp3, but it will do movies as well.
All done via a web interface and a single click should start the movie playing.
You may need to edit mime types in firefox to get real mplayer to play the file instead of mplayer plugin in firefox, unless you are happy watching within firefox

---

### Post by henrypootel on 2007-11-04
wow, i didn't know that gnump3d could do movies.
i will have to give that a try.

thanks

---

### Post by Jose Catre-Vandis on 2007-11-05
> **henrypootel said:**
> wow, i didn't know that gnump3d could do movies.
i will have to give that a try.

thanks

You can find movies by setting the preferences in your client and ticking the radio button for movies. it's also worth a try of the different themes to find one you like

---


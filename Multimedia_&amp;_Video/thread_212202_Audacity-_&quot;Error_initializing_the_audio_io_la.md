---
title: "Audacity- &quot;Error initializing the audio i/o layer&quot;"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by atenlaugh on 2006-07-09
When I open up Audacity it says: "Error initializing the audio i/o layer.You will not be able to play or record audio//Error: Host error." 

I am able to record with Sound Recorder, and as far as I know, all other sound output/input is working fine. I had just used Audacity yesterday to record a small guitar piece, but not I can't access it. 

I've seen the problem in a few places, but never in the kind of circumstances of my issue, and I haven't found any sort of answers given that would apply to my case...

Edit: Under preferences --> Audio I/O it has two boxes for Playback/Device and Recording/Device, but it isn't giving me any options in either.

---

### Post by keith whitehouse on 2006-07-09
hi atenlugh,

if you had gone to Google and searched, Re: Audacity- "Error initializing the audio i/o layer",you would have found numerous posts on your problem.

Quote "There was an error initializing the audio i/o layer. You will not be able to play or record audio. Error: Host error." then audacity cannot access your sound card. Audacity cannot use the audio i/o layer when it is in use by another application. If you are using Gnome, KDE or another window manager, be sure to disable the system sounds before starting Audacity.

best regards keith

---

### Post by atenlaugh on 2006-07-09
Keith, I had forgot about just simply googling it! I'll be sure to do that next time, as, sure enough, it's better documented elsewhere (naturally). 

There's a wiki for it here, in case anyone stumbled on the thread: [http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues)

But turning off system sounds works for me (though doesn't explained why it had worked straightaway before, but I'm not going to complain).

---


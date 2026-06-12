---
title: "Audio Server to an Android Client"
date: 2013-01-13
forum: Multimedia Software
---

### Post by churl on 2013-01-13
What I want to do is this:
I want to play an mp3 with an audio player (gmusicbrowser preferred) and have the mp3 play normal on the host computer.  I want to be able to connect to the currently playing mp3 from my Android phone in another room of the house (via local wireless is what I'd be using), so I can keep listening to, say, an audio book without having to load the song on my phone at the correct time in the story.

I know gmusicbrowser has the -server argument.  I didn't have any luck with my limited knowledge of this kind of subject.  This might work just fine for what I'm trying to do.  If you know this works, suggested settings will be helpful.   

Is there a better way to go about this set up/end result?  Suggestions are welcome.  Thanks

---

### Post by tgalati4 on 2013-01-13
To use gmusicbrowser with the -server switch, you would need to have an icecast2 server installed and running.  So you would have to install and configure icecast2 and have it running.

If you use a DAAP plug-in with rhythmbox, then use can use mediabrowser on Android to see the DAAP shares and play them.  If you restrict the library on rhythmbox to only those files that you want to listen to remotely, it will take less time for DAAP to load.  It takes a while to load large libraries with DAAP, and it can be quite annoying.

I haven't used gmusicbrowser with the -server switch, but it sounds like it will simply relay whatever is playing to the running icecast2 server then you should be able listen with any device that can see the server.

---


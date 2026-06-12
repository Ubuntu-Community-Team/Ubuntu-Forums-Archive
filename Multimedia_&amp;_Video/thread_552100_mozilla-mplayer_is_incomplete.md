---
title: "mozilla-mplayer is incomplete"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by Praill on 2007-09-16
One final annoyance with Ubuntu being a "regular usage" machine is the incompleteness of firefox's mplayer plugin.

I have it installed, and it works in the sense that i can view and hear the media but thats pretty much all I can do.
Sometimes I can see a progress bar, sometimes I can't, but at best its just an indication of my position in the video. I can't use the bar to chose a spot in the video, nor can I use the rewind or fast forward button to change the position. It's very annoying because if I miss something I have two options, deal with it, or watch the whole thing over.

Whatsmore, is theres no easy way to start the whole thing over, I have to physically refresh the page. Im limited to play, and pause.... and sometimes I can see how much time is remaining... sometimes.

Ive been through the configuration and I've looked all over the forum for a similar question, but to no avail. 

I have tried to use the media player connectivity plugin (almost unwillingly since IDEALLY i would like to stream inside the page) but native mplayer and totem both give me a host resolve error and vlc caches a maximum of 10 seconds (or so) which isnt enough on my connection for stage6 files.

Essentially my question is... does anyone know a way to add more options and functionality to the mplayer plugin interface? Either through some hidden configuration file or a more "beefed up" version of it?

---

### Post by aidanr on 2007-09-16
I find the arrow keys give me more control than clicking on the bar. You might want to give gnome-mplayer [[link]("http://www.getdeb.net/app.php?name=Gecko+Media+Player")] [[link]("http://www.getdeb.net/app.php?name=GNOME+MPlayer")] a try.

Note: for some reason firefox didn't pick up the plugins it installed at /usr/lib/mozilla/plugins, so I copied them to ~/.mozilla/plugins

---

### Post by Praill on 2007-09-16
Thanks for your reply. 

Since I posted I've been messing with various players. I've now managed to get network streaming capability out of gxine and kmplayer as well as vlc. They all have a common problem tho, no rewinding. I can fast forward, play, pause, start over, but can't rewind.

With gxine the button is just missing, vlc its greyed out, and kmplayer it just doesnt work. I have to assume this isnt coincidental and lies much further within a common library they all use for processing streamed divx encoded video. 
Essentially, by the sounds of it, there is no fix due to how the linux libraries read the protocol.... <sigh> oh well.... maybe some day.

---

### Post by Praill on 2007-09-16
BTW, in case anyone else comes across this. My "good enough" solution was to use the MediaPlayerConnectivity plugin to open up gxine. gxine seems to handle it the best imo.

---


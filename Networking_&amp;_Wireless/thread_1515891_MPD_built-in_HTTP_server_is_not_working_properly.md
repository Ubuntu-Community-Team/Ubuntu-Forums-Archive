---
title: "MPD built-in HTTP server is not working properly"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by firestorm69 on 2010-06-23
Ok so I've been all over Google trying to find an answer as to why my MPD server won't properly output over httpd. When I try to connect to it from any source, it gives me a "404: Entity Not Found" error. There hasn't been any useful info out there to solve this problem. Help please! Attached is my mpd.conf file. All my permissions and firewalls are set up properly AFAIK.

---

### Post by Brandon Williams on 2010-06-24
Just to double check, have you started the stream? With an icecast stream, the stream won't be available until you start streaming. It can be paused, just not stopped. This might be true of the built-in streams, too.

---

### Post by firestorm69 on 2010-06-25
I suppose I don't fully understand how MPD's built-in HTTP server works. Do I need to start it with a separate command? The way I understood it from the wiki and other scattered docs is that in order to run and operate the server, all you had to do was enable it in mpd.conf and make sure it's running as an output. Am I wrong in my assumption? I'd greatly appreciate help in setting this up properly.

---

### Post by Brandon Williams on 2010-06-28
Sorry for the delay ...

What I meant was that you might need to add some tracks to the playlist and then play the playlist. With mpc, that would be:
```
mpc add <file>
mpc play
```

If you run 'mpc status' on the command line, it should indicate some track and whether that track is currently playing or paused.

---

### Post by firestorm69 on 2010-07-04
I've run MPD all sorts of ways, with and without playlists playing, all combinations of my different outputs enabled and disabled (i have alsa, pulse, ogg, and the server set up as different outputs) and still a no go.

---

### Post by dinopio on 2010-07-06
> **firestorm69 said:**
> I've run MPD all sorts of ways, with and without playlists playing, all combinations of my different outputs enabled and disabled (i have alsa, pulse, ogg, and the server set up as different outputs) and still a no go.

I have exactly the same issue
I enable http built in server and use the default settings 

When I tune into the URL i see a buffering stream but no audio output.

tried [http://URL:8000/](http://URL:8000/) and [http://URL:8000/mpd.ogg](http://URL:8000/mpd.ogg)

I tried changing the encoder and the same issue persists...

---


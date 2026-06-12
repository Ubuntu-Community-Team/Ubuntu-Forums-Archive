---
title: "Front-end / Back-end solution"
date: 2009-04-24
forum: Multimedia Software
---

### Post by elfranger on 2009-04-24
I need some assistance in figuring out the best way to accomplish my idea. Maybe it already exists too :-).

I want to put an Ubuntu machine next to my receiver, will probably be an old laptop I have lying around. Its sole purpose in life will be to feed music to my receiver during parties.

I have had it somewhat like that before, but with people sitting close to it to manage playlists and finding songs... What I would like is to just leave it there, and use yet another laptop on WLAN as a frontend. The front-end laptop should be able to control every aspect of the back-end when it comes to searching for songs, enqueing them and making playlists...

Is this even possible with somethnig that exists today? I have started looking into rhythmbox, but have not found what I am looking for yet...

Any ideas?

---

### Post by mobilediesel on 2009-04-24
> **elfranger said:**
> I need some assistance in figuring out the best way to accomplish my idea. Maybe it already exists too :-).

I want to put an Ubuntu machine next to my receiver, will probably be an old laptop I have lying around. Its sole purpose in life will be to feed music to my receiver during parties.

I have had it somewhat like that before, but with people sitting close to it to manage playlists and finding songs... What I would like is to just leave it there, and use yet another laptop on WLAN as a frontend. The front-end laptop should be able to control every aspect of the back-end when it comes to searching for songs, enqueing them and making playlists...

Is this even possible with somethnig that exists today? I have started looking into rhythmbox, but have not found what I am looking for yet...

Any ideas?

Use [Music Player Daemon]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki") on the computer that will be hooked to the receiver. Then use any of the [clients]("http://mpd.wikia.com/wiki/Clients") that work with it. MPD sits there and takes commands from a client to play music. The client just gives you an interface to MPD.

I personally use [Sonata]("http://mpd.wikia.com/wiki/Client:Sonata") to control the music.

You would store the music on the computer with MPD on it. Once you set up the playlist from the client you can even shut down the client and MPD will keep playing to the end of the playlist.

---

### Post by elfranger on 2009-04-24
excellent, I will have a go at it this evening :-). I will post my experiences here.

---


---
title: "Music Player with Web-Based Interface (I've Tried Jinzora)"
date: 2008-08-12
forum: Multimedia Software
---

### Post by i.wanna.corndog on 2008-08-12
Well, I've been searching around for quite awhile to try to find something that fits my needs with no luck.

I'm looking for a media player that can:
-play common file types (i.e. mp3, ogg, flac)
-be controlled via web interface
-not require a GUI (I simply need to be able to scan a specific folder for music that is added to a database)
-output to the local sound card
-run as a DAAP server (optional, but preferred)

Basically, I have a headless home media server that is located near my stereo. I would like to connect my media server to my stereo (just a simple 3.5 mm jack connection) and to play music from my media server through my stereo. I would like to be able to select a playlist via a web interface from any of the computers on my network. Also, if possible, I would like to be able to browse and play back the music from an individual computer using iTunes if necessary.

Does anyone have any suggestions? I tried Jinzora, but I can only seem to get it to allow me to play back music through one of my networked computers (not through the server's audio out port). If Jinzora can do this, I'd love to know how (and if you could point me in the direction of a nice tutorial, that would be superb!).

Also, I did a little bit of looking into MPD, but I'm not sure where I'd start with that. If that would work and someone could provide a link to a good tutorial, that might work as well.

Thanks for any suggestions!

---

### Post by i.wanna.corndog on 2008-08-12
I just wanted to reply to my own post to say that I found a solution, which I will outline here.

1.) Install MPD with any necessary dependencies (see [http://packages.ubuntu.com/hardy/mpd](http://packages.ubuntu.com/hardy/mpd) for a list).
2.) Edit /etc/mpd.conf to point mpd to the directory of your music.
3.) Restart mpd (sudo killall mpd && mpd)
4.) Download a web client (I chose RelaXXPlayer for its nice interface: [http://relaxx.dirk-hoeschen.de/](http://relaxx.dirk-hoeschen.de/) ) and extract the tar file to /var/www/ 
5.) Navigate to [http://serverhostname/relaxx/](http://serverhostname/relaxx/) and click "Config". Log in using "admin" as the user and no password.
6.) Change the password if you want and select "Update DB".
7.) Refresh the page after a few seconds (or longer, depending on your music library size) and you should see your music!
8.) Connect the server to your speaker system and enjoy!

The only thing this didn't fulfill for me was having an iTunes DAAP server, but I'm sure I can find another software package to do that (Done with m-daapd!).

---


---
title: "Installing mt-daapd"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by russell.h on 2007-08-24
I installed mt-daapd from the repositories, started it with ```
sudo /etc/init.d/mt-daapd start
``` and can browse to it by going either to [http://localhost:3689](http://localhost:3689) or to [http://192.168.1.11:3689](http://192.168.1.11:3689) (which didn't work until I allowed connections to port 3689 in Firestarter).

The web based configuration utility seems to work fine, and shows that it has 74 songs (which sounds about right, I havn't counted, but I gave it maybe 6 albums to test).

But I just cannot get iTunes or anything else (including rhythmbox with the DAAP plugin running locally) to connect to it. Is there some other port I need to unblock or something? This is driving me nuts.

Note: I'm running 64 bit Feisty

---

### Post by trak87 on 2007-10-07
I'm having the same difficulty. I've got mt-daapd installed and running and can surf to [http://localhost:3689](http://localhost:3689) or [http://192.168.x.x:3689](http://192.168.x.x:3689), and it looks good, it has indexed the songs, but no client program connects to it. At least I'm assuming a client will show an entry coming from that resource. I've tried Rhythmbox, Banshee and Exaile. Anybody have any clues. Thanks.

---

### Post by russell.h on 2007-10-07
I haven't personally tried it, but a forum member I communicated with provided me with these instructions:

[quote=aaltieri]Greetings. I have gotten mt-daap to work under Edgy.

First, visit this site for the mt-daap package:
[http://au.ubuntu.cafuego.net/dists/edgy-cafuego/media/](http://au.ubuntu.cafuego.net/dists/edgy-cafuego/media/)

That will install nicely. Then, there is a file you need to edit to make the avahi side turn on. It's described here:
[https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

Once I did these, it worked great. I use iTunes 7.4.1 and it is GREAT. It transcodes the flac for me so I can dig on my cab calloway.

One thing I will warn you about though. Make CERTAIN your library is in good order! I didn't think about it and tossed up a bunch of mp3s with out checking them. They had no ID tags. So now I get to bring them back to my computer and try to sort them out![/quote]
Good luck, and do let me know if it works. If I have time tonight I might try it myself, although I'm 1600 miles from my computer right now so I'll have to go via ssh.

---


---
title: "Looking for the best streaming audio player"
date: 2011-01-26
forum: Multimedia Software
---

### Post by Erich-A on 2011-01-26
I need my Ubuntu box to play an http audio stream on boot. It must heedlessly attempt to reconnect to the audio stream no matter how many network errors I may or may not have.

Currently using VLC on boot with the commands: -loop -http-reconnect

VLC works fine for the first little while, but after a day or two, it doesn't try to reconnect enough to meet my needs. (Like 2 hour downtime if the stream stops without user assistance)

Any help would be muchly appreciated :)

Cheers!

---

### Post by Erich-A on 2011-01-26
Any suggestions???

I don't mind stress testing any and all software. I just have no idea where to start looking, so I came here after google searches failed me. I'm a fan of lightweight and advanced buffer options, but any software that'll stay solid after moments when I have an ip hiccup is the perfect software for me :)

---

### Post by mutex77 on 2011-01-26
I was about to say VLC, then I actually read it and saw that you were already using it :)

Can this be mangled to suit your needs?
[http://stackoverflow.com/questions/1284032/best-way-to-monitor-for-a-server-on-a-tcp-port](http://stackoverflow.com/questions/1284032/best-way-to-monitor-for-a-server-on-a-tcp-port)

I had a user that needed something similar years ago, they ended up monitoring the TCP port to see if the stream was still there or not. Pretty straighforward, if there's less than 10 packets from thestream.com port 8080 in a min then renegotiate the connection by restarting the client. We put something in so after a few restarts in a certain amount of time it stopped trying so we werent reconnecting over and over on some remote server that was having probs. I think we used tcpdump, but im sure there's a better network monitor out there by now. 

You could also do the same thing with the audio device itself like using sox to record for a few secs on the card then check if theres anything there. I think the network monitor would be easier though.

I did a quick google searchout of personal curiousity. I was surprised there wasnt something built into VLC that did this. Others werent having luck with http-reconnect either. Some did have luck with -repeat and otjhers with -sout. 

Good luck!

---

### Post by weedeater64 on 2011-01-26
Certainly no master of streaming here, but I recently found myself in search of a new player.

I tried vlc and had troubles with it running out of control, and eating cpu's like crazy.

Scanning the boards I get the impression that mplayer is the boss' in the linux world for all things video/music.

I'm giving it a whirl, and so far liking it..

There is a huge amount of documentation on it the man page alone is several hundred pages long.

I'm no configuration guru either, but if you are any good at that sort of thing I suspect you'll be happy with mplayer.

I don't know how to make it auto start, but I do know that if it drops a connection for some reason, I can tab/enter and it's back up in a couple of seconds.

---

### Post by Erich-A on 2011-01-27
I just started using mplayer, so far so good. Mind you VLC only gave me issues after running for longer than a day, so it'll be some time before I know how good it really is. But I like the fact i'm running it from commandline

---


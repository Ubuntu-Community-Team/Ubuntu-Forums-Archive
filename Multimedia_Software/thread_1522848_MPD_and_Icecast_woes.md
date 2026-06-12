---
title: "MPD and Icecast woes"
date: 2010-07-02
forum: Multimedia Software
---

### Post by bhalash on 2010-07-02
I want to stream my music collection over to my iPod, so I settled upon MPD and Icecast to handle it. I've been following the [Arch Linux HOWTO](http://wiki.archlinux.org/index.php/Streaming_With_Icecast_and_MPD) on setting this up, but I've run into a a seeming dead end on getting everything working together. The facts:

MPD functions - I'm listening to it right now.

Icecast functions - I can browse to it's bound IP/port (192.168.1.100:8000) and see that MPD is connected as a source. I can access this via my iPod too (in a browseR) so I know it's functioning over the network. But when I attempt a client connection (via [MPoD](http://www.katoemba.net/makesnosenseatall/mpod/) or anything else) it is refused. 

[icecast.xml](http://dl.dropbox.com/u/4144919/website/content/757801037/icecast.xml)

[mpdconf](http://dl.dropbox.com/u/4144919/website/content/757801037/mpdconf)

Pertinent section of mpdconf:

```

audio_output {
	type		"shout"
	encoding	"ogg"			# optional
	name		"RAWR"
	host		"192.168.1.100"
	port		"8000"
	mount		"/mpd.ogg"
	password	"hackme"
#	quality		"5.0"
	bitrate		"128"
	format		"44100:16:1"
	protocol	"icecast2"		# optional
	user		"mark"			# optional
#	description	"Music...from me to you"# optional
	genre		"jazz"			# optional
	public		"no"			# optional
	timeout		"2"			# optional
}

```

I am directing my clients to connect to:

Server: 192.168.1.100
Port: 8000
Password: Relay (correct?) password

What am I doing wrong?

---


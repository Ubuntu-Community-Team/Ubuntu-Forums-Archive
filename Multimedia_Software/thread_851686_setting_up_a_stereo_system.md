---
title: "setting up a stereo system"
date: 2008-07-06
forum: Multimedia Software
---

### Post by tears.of.angels on 2008-07-06
hey everyone. i was just thinking about working something out for a stereo system, and i was hoping someone could help me out. basically i want to create a headless system that will play audio cds and some mp3s. i'm looking at getting the firefly mini remote. and i want to be able to operate my cd's from there - monitorless. the challenge here is twofold:

1) does anyone know if the firefly mini remote is customizable enough for me to setup custom commands? (ex: >>| = "cdcd -next")

2) does someone know an easier way to stream mp3s to the system from my laptop than with ssh? (i want the whole system to be console based, as i don't want to deal with X)

any help or input is greatly appreciated

---

### Post by s3a on 2008-07-07
For custom commands, maybe clicking System-->Preferences-->Keyboard Shortcuts? Sorry if this is not what you're looking for.

---

### Post by tears.of.angels on 2008-07-07
thanks, but not quite.

that's a gnome command, and i don't want to use X (i'm going to be monitorless, actually.)

i have discovered i can use Xmodmap & lirc.conf to set custom bindings for the remote.

now does anyone know of a command-line cd/mp3 player that does gapless playback? i like orpheus, but it's not gapless

---

### Post by camccall on 2008-07-07
I have no experience with the firefly remote so I can't help you there.  

As far as number 2, why don't you use samba to stream your music, ssh would work of course, but samba will work for this problem to, It's what I use on my media server.  NFS would also work of course. 

As far as mp3 players I would look into [mpd]("http://www.musicpd.org/").

---

### Post by tears.of.angels on 2008-07-07
oh mpd is great. it's what i use on my laptop right now (connecting to localhost)

but is mpd able to play music cd's? i really like listening to the physical cds, and that's one of my reasons for orpheus.

---

### Post by camccall on 2008-07-07
Ah sorry, didn't really think about that, I'm not 100% sure but I don't believe that is supported at this time.  I did a quick search but I'll try to dig a bit deeper this afternoon. 

Another option that I have no experience with but might be a possibility of is running vlc without the gui, of course then you lose the gapless playback :(.  You could possibly use a combination of those though, maybe launch vlc when an audio cd is detected and then fall back to mpd when no cd is in the drive.  I'll do some looking for you, I like playing with different audio players when I have down time.

---

### Post by tears.of.angels on 2008-07-07
thanks, i'll look into vlc. i didn't know it had a command-line interface. and keep me posted on what you find.

right now i'm thinking of using cdcd - it's a command-line cd player in conjunction with mpd. i'm going to tinker with it tonight and see what i come up with too.

---

### Post by camccall on 2008-07-08
Hey, sorry I didn't get a chance to do any looking last night, ended up having to pickup a friend from the airport and didn't get home until after 10:00.  CDCD could work, seems like a good choice, lightweight and simple.  

One other thing to consider, with mpd and possibly vlc you could have a web frontend that would be accessible.  As you already use mpd, I'm assuming you know about some of those.  VLC also has a web interface available to you as well.  Check out [http://wiki.videolan.org/Web_Interface](http://wiki.videolan.org/Web_Interface)

---

### Post by tears.of.angels on 2008-07-09
yeah, im aware of the web interface for mpd (i sometimes use pitchfork with my apache server on my laptop)

but i didn't know VLC had a web interface. thanks for the link, i'll check it out.

---


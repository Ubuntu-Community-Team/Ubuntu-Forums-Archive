---
title: "Best way to play music over Wi-Fi from laptop to stereo-connected desktop?"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by Endolith on 2007-09-11
I bought a cheap desktop to act as my network file server/backup drive/sound system/etc.

For the sound system part, I've got files on both my laptop and desktop, and share them so the desktop can access them over SSH.

Then I have a menu option configured for ssh -fX rhythmbox (Quod Libet apparently doesn't support network files (GNOME VFS?), so I'm using Rhythmbox for now.)  Then the desktop plays through its sound card to the room.  So I am controlling the apartment's sound with my laptop over Wi-Fi from anywhere.  It works pretty well, but:
[LIST]
[*]It asks for my desktop password to SSH to the other machine (of course)
[*]It doesn't use the keyring, so it is constantly asking for my laptop password to access the files on my laptop (I guess samba shares would fix this, but I want the files deletable and tags editable as possible.)
[*]Can't play sound from Flash, games, YouTube, etc. only sound files.
[*]Have to control the volume and change tracks from the program itself instead of my laptop's volume/multimedia keys.   Requires too much clicking and too much delay if I want to change something quick.  ;-)
[/LIST]

Instead of this sort of roundabout system, is there a way to run the music player on the laptop and stream the sound itself across Wi-Fi instead of the files?  Something like NAS?  Gstreamer wifi plugin?  The Preferences --> Sound menu has things like "Music and Movies" that can be redirected to different sound output devices.  Is there a way to install a network sound output device, and stream the audio directly to a server on the desktop?

I don't know the technical details, and I can't find any good info, though I could understand it if someone explained it to me.

---

### Post by nomasteryoda on 2007-09-12
Just a quick reply... Recommend you look at mpd and mpd clients. I use mpd with all my music residing on a small form-factor headless desktop running Ampache. The frontend is any computer with a webbrowser from anyplace that has web access.... You can also setup a remote on the "server" system to sit on your couch and surf the "channels".

And for authentication:

Use ssh key pairs and publish the public key of the client to the "server" system you are accessing... That way you only type ssh servername.local and your password once... From then on no more passwords have to pass between those 2 systems.... There are some excellent tutorials out there... This one is well written.. [http://www.oreillynet.com/pub/h/66]("http://www.oreillynet.com/pub/h/66") 

good luck! :)

---

### Post by martin_prince on 2007-09-12
ditto, mpd is an excellent music server.  It is available in the repos (apt-get install mpd) and there's just a couple of options you'll need to set in /etc/mpd.conf.  Then, install an MPD client like Sonata on your laptop (or use the web interface) and away you go.  Then you shouldn't really need to worry about SSH from then on, but if you still do, SSH keypairs is the way to go...

---

### Post by Endolith on 2007-09-12
> **nomasteryoda said:**
> Just a quick reply... Recommend you look at mpd and mpd clients.

I'm installing it now.

> I use mpd with all my music residing on a small form-factor headless desktop running Ampache.

Yeah, same idea as my desktop.

> The frontend is any computer with a webbrowser from anyplace that has web access....

That's good.  So visitors could use it as well?  Play stuff from their own laptops over the sound system?

> Use ssh key pairs and publish the public key of the client to the "server" system you are accessing... That way you only type ssh servername.local and your password once... From then on no more passwords have to pass between those 2 systems.... There are some excellent tutorials out there... This one is well written.. [http://www.oreillynet.com/pub/h/66]("http://www.oreillynet.com/pub/h/66")

Ah.  Does "between those 2 systems" mean the hardware itself or the accounts in use?   I don't necessarily want anyone on my laptop to be able to access anything on the desktop.

---

### Post by Endolith on 2007-09-12
Hmmm...

Doesn't look like this can play arbitrary sound from my laptop; just music files, so it's really the same thing I'm doing right now, but more dedicated.

Why is it limited to only MP3, Ogg Vorbis, FLAC, AAC, Mod, and wave files?


Agh text file configuration, manual audio configuration, all directories as hand-configured symlinks.   This is ridiculous.  Any other alternatives?

---

### Post by Endolith on 2007-09-21
No other ideas?

---

### Post by MeanderingCode on 2007-10-11
This thread is similar => [http://ubuntuforums.org/showpost.php?p=3447577&postcount=8](http://ubuntuforums.org/showpost.php?p=3447577&postcount=8)
Haven't tried it, but i'm looking, too.

Good luck
    OR
Did you get it to work already?

---

### Post by Endolith on 2007-10-11
I'm still doing what I was doing before (ssh -fX remotecomputer rhythmbox).

Also see:

[http://ubuntuforums.org/showthread.php?p=3517495](http://ubuntuforums.org/showthread.php?p=3517495)

---


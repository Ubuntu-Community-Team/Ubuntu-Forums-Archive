---
title: "Command Line Music Player"
date: 2009-03-04
forum: Multimedia Software
---

### Post by CarltonF on 2009-03-04
I have only been using ubuntu for 2 days so please forgive me if this is obvious.

We live in a student house, each of us has a desktop and a laptop plus now I have just set up a ubuntu computer in the main room. The idea for this was that we can use it to play music that is on any computer in the house, in the main room. So here comes the problem. The ubuntu computer has no monitor/mouse/keyboard. Just a set of speakers. So I want to SSH into the computer in order to play the audio.

I tried VLC but could only seem to play or add to the playlist, individual files. For a whole album that is going to take a while, plus I dont know by heart what the full path to every audio file on every computer is.

I tried some others, mpg123, mpg321, mplayer and amarok. I still have this same problem. I would just like to pass the media player the path of a directory full of music and have it play all the music in that folder, ie:
<some media player name> "smb://somecomputer/music/Portishead/Dummy/" could play that album, or even if I just go to the Portishead folder, which contains 3 folders titled the names of 3 of their albums, it could queue those up. Just having it read a directory and not having to type in every file name would be a great deal closer to what I have now though, so any help is much apreciated.

---

### Post by InspiredIndividual on 2009-03-04
Maybe you can use mplayer. I think it probably suits your needs. How did it fail? You should be able to use wildcards, I think. See also this link: [http://www.go2linux.org/mplayer-command-line-music-video-player](http://www.go2linux.org/mplayer-command-line-music-video-player) .

---

### Post by duanedesign on 2010-07-02
MOC is an easy to use command line player. [Here is their about page]("http://moc.daper.net/about").


Music Player Daemon perhaps. I was [reading this]("http://www.linux-mag.com/id/3855") and it sounded like it might be what you are looking for. There is more information on the [Music Player Daemon Wiki]("http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki")

---


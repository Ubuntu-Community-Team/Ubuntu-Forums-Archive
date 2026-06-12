---
title: "vlc over ssh"
date: 2009-05-04
forum: Multimedia Software
---

### Post by docjones2 on 2009-05-04
I have a computer on my network that stores all of my music, I configured it as an ssh server and can ssh locally no problem.

What I want to do is ssh into the computer and run a "vlc song.flac" type of a command and have the song play through the client's speakers (you can tell me how to get it to play through the server's speakers too, that would make a great practical joke)

I do not want to mount any locations or get involved in anything samba related, I just want to do it through a terminal sshed into a computer on the network.  I'm sure vlc has some interesting/obscure command arguments for this type of thing but I don't know vlc or linux well enough to deduce anything.

Thank you.

---

### Post by detroit/zero on 2009-05-29
I wouldn't mind hearing what some other people are doing with this, too. I have a modest-sized collection of media files spread out over two ubuntu computers on a home network. I have ssh access on all the machines, and would like a straightforward way to call on VLC to play files at remote (i.e., not on localhost) locations.

---

### Post by steve_c on 2011-03-12
This is a really old thread but I'm bumping it anyway because it's relevant.

I'm sitting in my bed on my laptop. I have a desktop with a 24" monitor on my desk over there. I'm lazy. I want to play videos on that 24" monitor. I'm SSHed into the desktop machine, but when I try to run VLC it tries to do it in the terminal window for some reason (which results in noise). I want to make it run on that big screen over there.

How do I do this? I'm sure it's just some simple command line parameter, but five minutes of googling hasn't found it for me yet so I thought I'd ask here while I look. I'll post a solution if I find one before someone else gives me one. No one should have to leave their bed to play videos on their desktop ten feet away when their laptop is conveniently on their lap.

---

### Post by steve_c on 2011-03-12
BAM! Nevermind. Should've searched these forums first.

From here: [Turing On VLC remotely using ssh]("http://ubuntuforums.org/showthread.php?t=437753")

> after you login through ssh, do this

export DISPLAY=:0

then when you open vlc, it will show up on the computer you are logged into through ssh. to play the video you want, just put its name after vlc if it is in the same directory.

vlc video_name.avi

Thank you to the original answerer on the other thread! Heh.

---

### Post by zokama on 2011-04-02
Also, if you happen to have an Android device, note that the application SSHmote ([www.zokama.com/sshmote](www.zokama.com/sshmote)) does all that for you: it gives you to access all your media files and allows you to control you favorite media player through SSH!

---

### Post by steve_c on 2011-04-04
Awesome zokama! Thanks for that!

---

### Post by zokama on 2011-04-07
I'm glad you find it useful. Please don't hesitate to give me a feedback (good or bad). The app is in early stages of development, I know it is not perfect as is, and I have a lot of ideas for the next versions. So critics on its current state or requirements for future versions are always appreciated.

---

### Post by FakeOutdoorsman on 2011-04-07
I often use SSHFS:
```
sshfs lordneckbeard@192.168.1.129:/your/remote/directory /your/local/mount/directory
```

Then:
```
cvlc /your/local/mount/directory/audio.flac
```

---


---
title: "MPLAYER on ubuntu server startup gets crazy"
date: 2014-09-02
forum: Multimedia Software
---

### Post by John Br on 2014-09-02
Hi there masters, I need some help regarding my PBX mp3s files. I want my ubuntu file server to play three mp3 files in a loop at boot. I wrote the script, tested in in the command line and it worked perfectly, but when I set it to run after booting, Mplayer got crazy like "flashing text" and of course it did not play anything. And for me to be ble to login in the server, I need to type alt+F2, then login and kill the Mplayer process. I used the update-rc.d command to set it up authomatically. 

What did I do wrong? If it plays with a ./script, why won't it at boot?

Is there any other way you could suggest for me to do it? That would help too.

Please, I need this working.

---

### Post by TheFu on 2014-09-02
Until a user logs in, I don't think sound will be possible. That's the nature of multi-user operating systems.

If you have a user auto-login, then it might be possible ... but I wouldn't want that security nightmare on my PBX.

OTOH, playback of audio for the PBX is completely different than playing audio through a speaker.  Do you really want the audio thorugh a speaker?

---

### Post by John Br on 2014-09-02
Thanks for the reply, and I will try to do a user auto login. I will have to check how to do this though.

The PBX board has the capability to let somebody who called and is waiting to hear a little song, I actually tried to get the audio playing with an old cell phone, but it was LG and too old. Even an ancient cdplayer would do it. I do not see a security problem, but please tell me what it could be.

And the speaker is the PBX board itself, I will plug the green-audio-plug into the server green-jack and that is it. When I ran the pbx script myself it played perfectly, I made a call here(Brazil), let me waiting(on purpose) and could hear the song with no problems.
But when I set it on boot, it really did not work.

Thanks again

---

### Post by TheFu on 2014-09-02
You can test the PBX interface using any SIP device or software through a network connection. There are lots of SIP clients for every platform. 

What PBX software are you using?  Most of them (all that I know) have "on hold music" built-in - no hardware board necessary. Just add the hold music directory/files to the config.

Security?  Having a PBX available to anyone walking passed is a bad idea.  Even inside a locked room, having a login required to access the interface, even the CLI as it is, is smart. People tend to touch things, breaking them. A PBX isn't any different.

If this is for a home, perhaps security doesn't matter as much. Inside a business - I'd have the box in a hardended cage, inside a locked server room, with cameras on all entrances and exits. After all, if someone can access the PBX from outside the approved interfaces, they can charge phone service to the owner for $20K/month easily.   Asterisk gets hacked daily around the world.  

There are log files that will show any warnings or errors when somehting goes wrong. Do those have anything useful?  If not, can the logging level be turned up?

---

### Post by John Br on 2014-09-02
Man, thanks but I believe we are talking about very different PBX setups. The one we have here, is an old one. I work at an english school and we got a very simple PBX. I took  a look at SIP. It is nice but not needed for now.

The sofware the board has surely is builtin, but I do not touch it. There is no interface, just a bunch of cables connected to it, two of them are for the PBX sound which can play some music for someone hanging on the phone.

Do you get a picture? What I need to do is get some music playing with the plug coming from the PBX board. It can be any device but the server is sitting right in front of it and it has an audio jack, so it can play. It is really simple. 

I wrote the script, played, tested the phone fine, but to make it work at boot is my problem.

I just took a look if I have a directory to copy music to and play. Well, I don't. I need to get it playing somewhere else and it will be heard when there is a call.

thanks again

---

### Post by TheFu on 2014-09-02
So this isn't a linux-based PBX?

Rockwell, Nortel or something like that from the 1990s?

What does the computer have to do with the PBX?

---

### Post by John Br on 2014-09-02
No this is not. It is an IntelBras Conecta, not from the 1990s but it is at least 7 or 8 years old. It is basically a board with its phone connections in it.

Well, the computer is the file server, the PBX(only the board) has the audio plug so it can play songs(not actually play, it lets the sound go through it) something else needs to play it and then the PBX passes the audio along to people hanging on the phone.

What I want to do is use the computer audio capabilities to play the songs for me at boot. that is it. We turn it on in the morning, it serves files, the java system and I want it to play the songs for me too.

I got it to auto login, later I will run the script to see if it will work.

Thanks for the help. If you have more ideas, please tell me.

---

### Post by TheFu on 2014-09-02
Ah - I understand. Haven't seen a PBX like that in years and years.  

The thing to understood is that local logins are given access to devices (like sound) that remote users are not allowed.  That's why the auto-login on the physical console is necessary.  The auto-login needs to be for a user account, not root.

The big guys here are all VoIP running Avaya or Cicso stuff (I've designed a deployment for 11 locations and 4K users - left the team halfway through the project).  The small guys (100 seats or less) are mostly Asterisk or have completely outsourced their PBX stuff to internet providers.  I've gone that way myself - outsourced to a reputable PBX provider for $5/month/line.

---

### Post by John Br on 2014-09-03
Now ok! We got it. Yes man, I live in Brazil, so I will have to wait to have these good PBX options. By the way, I took a lok on line and it appears that some companies are selling this ISP PBX service.

I will auto-login and try it later.

thanks a lot so far.

---

### Post by TheFu on 2014-09-03
Everywhere in the world has old stuff.  Heck, my first job was modifying 20 yr old mainframe software. Often the older stuff is the best answer.  Sometimes there isn't a good way (or any need!) to get something newer.

---

### Post by John Br on 2014-09-04
You bet. And this morinig I tested it with auto-login and it did not work. So, as this is getting a little dangerous because the server is really important, I will stop here, study more and just later will try it again. If I break this server I am dead. I will let something else play those songs for the PBX.

Thanks for all the help.

See u TheFu

---


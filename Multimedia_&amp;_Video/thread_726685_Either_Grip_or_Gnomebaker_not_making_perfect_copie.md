---
title: "Either Grip or Gnomebaker not making perfect copies"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by Sweet Spot on 2008-03-16
I've been archiving some CD's lately, and in the process noticed that after having backed up a MOFI Soundlabs CD of Dark Side Of The Moon, which was ripped and encoded to FLAC, that after having made an audio CD from it, there were 2 second gaps between each song. 

I decided just now then, to rip another disc (Radiohead's Kid A) and burn it using both Grip to rip and Gnomebaker to burn.  In Grip, I chose to rip+encode (but encode after all tracks were done ripping) to FLAC, with IDtags and then stuck them in Gnomebaker in order to burn as an Audio CD. 

I didn't see any settings in Grip which would indicate whether or not there'd be any gaps present, as I've seen in other programs, so I trusted that it would be an exact, bit for bit (including gaps between songs) rip. I then put the disc in and set the track to the end of Idioteque which seamlessly transitions into Morning bell, with the music from Idioteque seeping into the beginning of the track... but it was cut off. There was again, a two second gap ? 

I put the original disc in my CD player, thinking that my NAD might be at fault somehow, but nay, it is the rip or burn. The CD plays gaplessly as it should. So, what am I missing here ? Is there a setting in Grip that I didn't see ? I'd really appreciate some help. And if Gnomebaker can't do the job, what should I use ? I'm starting to think I should use the WINE version of EAC..... But would really rather not. 

Doug

---

### Post by eye208 on 2008-03-17
The gaps are made by the CD writing software. Try setting it to DAO (disc-at-once) mode. DAO is the only way to burn gapless CDs. If gnomebaker can't do it, try gcdmaster.

---

### Post by |{urse on 2008-03-17
i know it's for kde but k3b works great in gnome too. and its in the repos.

---

### Post by Sweet Spot on 2008-03-17
Are you guys absolutely positive that the problem lies within the burning software and not Grip (or ripping)  ?   Though, you're probably right, from what I recall. Going to try gcdmaster now.

---

### Post by Sweet Spot on 2008-03-17
Well, gcdmaster is a bust. First off, it doesn't even recognize either of my DVD-RW drives and seems a pain in the *** to configure.  Secondly, I noticed that it doesn't handle FLAC files... So that's a no go. I don't mind working with WAV files, but if I already have FLAC's, I'd rather not have to go through one extra step and decode them to WAV files.  So now I have to try K3b, which is fine but... not being able to **easily** get this task done with a native Gnome app, is annoying. 

Guess I'll chalk this one up for the "Is Ubuntu ready for the Desktop" thread, as a negative. It shouldn't be this hard/annoying to get an exact copy of your own music CD.

---

### Post by Sweet Spot on 2008-03-17
Ok. K3b it is then ! I have to say, it's a very sweet app for burning music, and i like the interface a lot more than Gnomebaker's. The options are far more abundant, as well. Too bad there isn't a Gnome native app like it (that I know of). What's up with that ? 

Anyway, it got the job done in spades, and hardly uses any memory in the process, so I'm very happy with it indeed. Not to mention no more wasted blank discs. 

Thanks so much fellas, I really appreciate the help. 

Doug

---

### Post by |{urse on 2008-03-20
np t8r ^^

---


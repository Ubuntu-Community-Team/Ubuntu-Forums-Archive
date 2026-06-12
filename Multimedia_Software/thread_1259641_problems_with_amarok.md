---
title: "problems with amarok"
date: 2009-09-06
forum: Multimedia Software
---

### Post by VobSub on 2009-09-06
I just installed ubuntu because i accidentally killed xp with viruses.  I was trying to figure out how to get my ipod and music to work together on Ubuntu.  I tried to copy all of my music from an external hard drive to ubuntu but the transfer would freeze at 2.1 gigs out of 8.3 gigs.  Then i tried to just use amarok to pull the files from the external hard drive but it would freeze at 3%.  When i force quit amarok everything else goes hay-wire and freezes also except firefox and Konquest.

---

### Post by RedRat on 2009-09-06
> **VobSub said:**
> I just installed ubuntu because i accidentally killed xp with viruses.  I was trying to figure out how to get my ipod and music to work together on Ubuntu.  I tried to copy all of my music from an external hard drive to ubuntu but the transfer would freeze at 2.1 gigs out of 8.3 gigs.  Then i tried to just use amarok to pull the files from the external hard drive but it would freeze at 3%.  When i force quit amarok everything else goes hay-wire and freezes also except firefox and Konquest.

It would be helpful if you could tell us what your machine is and which distro of Ubuntu you have installed (it sounds as if it kbuntu since you are using Konquest and Firefox). Is that correct or are you using Gnome based Ubuntu? How much RAM and what size hard drive? Have you checked the external hard drive on which you have your music stored for errors? 

You might try moving or copying your music folder by folder, there might be an error in one of the files, I found this when I tried to move a large number of files from my NTFS external drive to my Ubuntu drive, just one small file (these were photos) and for some reason Ubuntu using Nautilus balked. Just had to skip that one photo. The same can go for music files.

---

### Post by VobSub on 2009-09-06
I have a Compaq  evo D310 micro tower with ubuntu 9.04.  Its a 2.4 ghz P4 with 1 gig ddr and a 40 gig hard drive.  Yes i noticed that when i tried to go folder by folder i ran into song problems, but when i pulled them off of my ipod the songs worked fine.  Is it a hard drive issue?

2nd Question.
I can't seem to get Amarok to get album covers. It keeps saying to change my search or something to that extent

---

### Post by RedRat on 2009-09-06
> **VobSub said:**
> I have a Compaq  evo D310 micro tower with ubuntu 9.04.  Its a 2.4 ghz P4 with 1 gig ddr and a 40 gig hard drive.  Yes i noticed that when i tried to go folder by folder i ran into song problems, but when i pulled them off of my ipod the songs worked fine.  Is it a hard drive issue?

2nd Question.
I can't seem to get Amarok to get album covers. It keeps saying to change my search or something to that extent

I don't quite understand what you mean by "song problems". However, everything works off the iPod. It may well indicate a hard drive problem. If it is an NTFS hard drive, you might want to run chkdsk /r (fix and repair that drive). 

Keep in mind that Amarok depends on ID3 tags on your mp3 files. If these tags are screwed up, Amarok will not report them with titles etc. If the moved files have their titles and artist in the filename proper, you might want to try using EasyTag to create proper ID3 tags. BTW which version of Amarok are you  using, 1.4.9 or the newer 2x version? I have heard tales fo woe for the newer version.

---

### Post by VobSub on 2009-09-06
Yup, its version 2.  Also Amarok won't play any of my songs.  It keeps saying there are too many errors in the playlist.  Because of this i switched over to Rhythmbox and i am wondering is it possible to have Rhytmbox get the album artwork.  Another question, Do i have to do anything special to get Rhythmbox or Amarok to sync w/ my ipod.  And do i have to get different programs to sync videos and pictures onto my ipod or will Amarok or Rhythmbox do all that also.

---

### Post by RedRat on 2009-09-06
> **VobSub said:**
> Yup, its version 2.  Also Amarok won't play any of my songs.  It keeps saying there are too many errors in the playlist.  Because of this i switched over to Rhythmbox and i am wondering is it possible to have Rhytmbox get the album artwork.  Another question, Do i have to do anything special to get Rhythmbox or Amarok to sync w/ my ipod.  And do i have to get different programs to sync videos and pictures onto my ipod or will Amarok or Rhythmbox do all that also.

OK, for its worth, I have heard that some people are having issues with Amarok 2. I have seen its spiffy new interface but have stuck with 1.4.9. Many have had success and like Rhythmbox so give it a try. Since I don't use the usual channels for music, I don't really care all that much about the album art, nice if you can get it, but the music sounds just as good without it. 

I am Creative Zen guy, so I can't give advice about iPods. There are others here who know that quite well.

---

### Post by djcslip on 2009-09-16
@ RedRat

I'm also a creative zen chap - but i have problems when placing tracks into playlists. All my ID3 tags are in place - but gnomad puts the songs in alphabetical order rather than track order. Any advise?

---

### Post by RedRat on 2009-09-16
> **djcslip said:**
> @ RedRat

I'm also a creative zen chap - but i have problems when placing tracks into playlists. All my ID3 tags are in place - but gnomad puts the songs in alphabetical order rather than track order. Any advise?

  My Creative Zen is now about 4-5 years old, lost track when I bought it, but I think that since then they did a firmware upgrade to the Zen. I believe it had something to do with file structure, this happened about a year after I bought mine. So it might not be quite like yours. I don't do playlists on mine, I tend to just listen to albums while I walk the dog. However, I believe that my version will read those m3u playlist files, though I am not sure since I have long since lost my instruction booklet.        My playlists, when I do use it are created &quot;on the fly&quot; in my menu system (remember mine is old). I am an album oriented type guy. To be honest, I do not know if they are in alphabetical order to not, but I think they are played in the order in which you place them in the playlist.       I have had good success in going to the Creative website and technical support. Try asking them, they seemed pretty good at getting back to me when I first started using Linux and trying to load music on the Zen.    Sorry I couldn't be more help.

---

### Post by djcslip on 2009-09-17
Thanks for replying - i'd got so carried away with playlists - i forgot i could just listen to the album normally!

---


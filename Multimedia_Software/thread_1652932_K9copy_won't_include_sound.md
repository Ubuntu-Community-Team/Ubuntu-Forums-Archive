---
title: "K9copy won't include sound"
date: 2010-12-25
forum: Multimedia Software
---

### Post by Jonny87 on 2010-12-25
I'm trying to use K9copy in Ubuntu 10:10 to shrink some videos from a straight iso copy down to a 800MB avi file. The video seems to copy fine and the picture looks fine but when I try play it in VLC theres no sound.

Is there something I'm missing?

And yes I played the ISO in VLC and had it play with sound fine.

---

### Post by 0N3 on 2010-12-25
Handbrake is the best ripper for Ubuntu in my opinion

k9 copy is a kde application

sudo add-apt-repository ppa:stebbins/handbrake-snapshots

sudo apt-get update && sudo apt-get install handbrake-gtk

---

### Post by Jonny87 on 2010-12-26
> **0N3 said:**
> Handbrake is the best ripper for Ubuntu in my opinion

k9 copy is a kde application

sudo add-apt-repository ppa:stebbins/handbrake-snapshots

sudo apt-get update && sudo apt-get install handbrake-gtk

I've used handbreak in the past and wasn't a big fan of it. I like k9copy and now that I have K9copy installed on my system I'd much rather try and get that working rather than keep swapping and changing application.  I've just noticed that encoding straight from a physical DVD rather than an ISO I get sound on the avi, but the picture seems to a bit poor. So why can't I get sound when encoding from the iso when the only difference is the source??

---

### Post by carlturney on 2011-03-04
p { margin-bottom: 0.21cm; }  Hello,
 

 I'm having very similar problems with K9Copy too -- and no solution in sight.



I think this is a GUI for a powerful and flexible program, but it is harmed by poor/missing user-friendly documentation.
 

 I've just =wasted= well over 12 hours, trying every permutation of K9Copy Assistant I can think of.  (See list of some attempts, below.)  Result: failure.  I only wish to rip a multi-Chapter Title, reduce it in size, with the output as a single file that can reliably play in the current Ubuntu versions of SMPlayer, GXine, and/or VLC.   
 

 Nothing has worked yet.  The problem is usually the sound is completely un-synchronised from the visual, as soon as I jump forward/backward during the playback (via hotkey or time-line slider).  e.g. The sound starts again from the very beginning, or the sound continues on the original timeline, while the video jumps forward/backward as I commanded.  Or else the video freezes, while the sound track jumps forward/backward as I commanded.
 

 Another common problem is the sound track sounds like it is coming through a slow-spinning large-bladed fan.  i.e. 1/8 second of sound in each full second.  I can not understand anything said, but can tell male from female voice, or sound effect from music, though.
 

 I can not tell you which version of K9Copy Assistant I am using.  It has a bad layout design, that does not even offer a Help >> About option.  But I =am= running K9Copy 2.3.5 on top of KDE 4.4.5 which is on my Ubuntu 10.4.2 LINUX.  I have installed every codec (and similar dependency file) that Medibuntu and Synaptic Package Manager have suggested.  I run Update Manager every day and accept all recommendations.  This is true of K9Copy and my 3 multimedia playback applications.  When I run the conversion processes (below), there is never an error window or warning message.
 

 What am I doing wrong?  (Please, do not say "go to HandBrake" or "go to DVD::Rip".  I have already seen that on similar forums about K9Copy.  And I see =just= as many "problem" posts on forums for those other programs too.  Besides, I =will= try them, if I can't find out what I am doing wrong with K9.)
 

 Thanking you very much, in advance.   
 

 Carl Turney, Christchurch, NZ  
 (Yes, where the earthquakes are.   
 Just now felt another aftershock.)
 

 SOME OF THE ATTEMPTS:
 

 K9Copy Assistant, Source = DVD, Rip & Encode, Chose the Title, Encoder = ffmpeg, Video = MPEG4, = 720 width, = 690mb file size, Audio = AAC, =128 bitrate.  Took 50 minutes to do a 1hr 34 minute Title.  Results: 684mb .avi file When playing that file using SMPlayer, and skipping forward or backward on the time scale, the video freezes and the sound track starts again from the very beginning.
 

 K9Copy Assistant, Source = DVD, Rip & Encode, Chose the Title, Encoder = mencoder, Video = MS MPEG4 (DivX3), width = 720, Size = 69mb, audio = copy.  Took 1minute 20 secs to do a 2 minute 5 second Title.  Results:  62mb file (original was 69mb). Playing the file in SMPlayer gave a black screen for the visual.  Playing in Gxine gave a black screen and the controls locked up.
 

 K9Copy Assistant, Source = DVD, Rip & Encode, Chose the Title, No subtitles, 1 6-channel audio track, Encoder = ffmpeg, Video = MPEG 4, 512 width, file size 640mb, Audio = copy.  Took 1 hr 15mins to convert.  Results 850mb file(!)  Playback was messed up.  (Did not note particular problem.)
 

 K9Copy Assistant, Source = DVD, Rip & Encode, Chose the Title, No subtitles, 1 6-channel audio track, Encoder = ffmpeg,  Video = copy, Audio = copy.  Said size would be 700mb.  Took 6 minutes to process.  Output file was 3.4GB (!).  Playback on SMPlayer and GXine and VLC ... sound track was totally messed up for each (Did not record details this time.  See above).
 

 K9Copy Assistant, Source = DVD, Rip & Encode, Chose the Title, No subtitles, 1 6-channel audio track, Encoder = ffmpeg,  Video = MPEG4, width 512, file size 640mb, Audio = Copy.  Took 40 minutes to process a 1hr 28 minute Title.  Output 834mb (!) avi file.  Playback on SMPlayer... soundtrack is OK, but whenever jumping forward or backward on time line, the video freezes.
 

 K9Copy Assistant, Source = DVD, Rip WITHOUT Encoding, Chose the Title, No subtitles, 1 6-channel audio track, Shrink factor set to 2.5 (1.48GB of a 3.7GB original).  Processing took 6 minutes to do a 1hr 28 minute Title.  Output... Total size was 1.4GB, but in 23 SEPARATE files (1 for each chapter in the title).

---

### Post by egmont on 2011-12-16
Bon, j' ai eu le même problème, et je viens juste de le résoudre!!
Pour pouvoir lors de la sauvegarde enregistrer également l' audio, il semble indispensable de sélectionner avant tout autre chose, les langues ou les pistes souhaitées.
Dans mon cas je souhaitais copier un DVD film et que ce soit vers une image ISO ou copie-DISK le son n' était pas enregistré!
Donc:
1/ ouvrir K9copy
2/ cliquer sur "open"
3/ dans nouvelle fenêtre cliquer sur le film (ou la partie de film choisie),; puis à droite cliquer sur CHAQUE langue et sous-titre choisi!
Sauvegarder, et c' est terminé!
Bonne chance à tous!
Al

---


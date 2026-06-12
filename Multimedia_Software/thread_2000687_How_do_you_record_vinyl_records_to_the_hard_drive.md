---
title: "How do you record vinyl records to the hard drive?"
date: 2012-06-09
forum: Multimedia Software
---

### Post by MissTina on 2012-06-09
Have an ion profile LP turntable.  Seems the thing works ok, but I've worked on it, and on the Net, for many hours, with several Linux OS's & many software installs, trying to get this thing going, but have got failures only. This tt came with a Windows and Mac install CD, and instruction manual, but without any mention of Linux.  Seems this tt might be for Windows and Mac only. There's no mention of Linux in the user's manual.  Anyone out there or in there, know how to make an ion tt work with Ubuntu?

---

### Post by eddier on 2012-06-11
AFAIK its not worth the hassle,read here-[http://http://www.which.co.uk/technology/computing/reviews-ns/ion-profile-lp-usb-turntable/]("http://http://www.which.co.uk/technology/computing/reviews-ns/ion-profile-lp-usb-turntable/").

On the bright side,if you have or can obtain a standard turntable and an amp then you can record in much better quality.

Connect Amplifier 'TAPE' outputs to your onboard sound inputs and use Audacity. There is a Tutorial somewhere on the Webby thingy,if I find it I will post URL.

eddie

oops! found allready [http://audacity.sourceforge.net/manual-1.2/tutorials.html]("http://audacity.sourceforge.net/manual-1.2/tutorials.html")

---

### Post by MissTina on 2012-06-15
Dear Eddier

WoW! that's a tremendous manual for sound & Audacity..  As far as manuals go it doesn't get any better..  Thanks..

I recall a little smell of something "electronicish", when I first fired-up the Ion turntable & Audacity..  It didn't seem to affect anything..  My first tries recording a vinyl, I got a lot of horrid clipping..  I pushed down the meters, and reduced the clipping down to about 2%, but I can't get saved recorded file to convert to MP3..  I'm supposing it didn't record properly.. probably I didn't set things just right..?  But the new recordings don't play with any audio player softwares..?  Now I'm wondering if the electronicish smell was the sound card frying.. because even old tunes on the hd don't play now..  Is there any possibility that "Audacity and Lame and Ion, in Fedora-14" can nuke a sound card in an older machine..?

I can only make guesses..  Maybe the sound card is thht..?

Seems I'm back to square one...
The plan is to set up another tower that plays tunes properly..
Install Audacity & Lame...

What's the best converter for wave to mp3..?

While I'm switching over to another tower, which has a clean formatted hd, any ideas which is the very best Linux distro for recording tunes with Ion tt's & the Audacity/Lame combo..?
How can you quick/simple test definitely that a sound card isn't shot, and is shot, besides it not playing a tune..?  I'm wondering if there's a little software conflict in what I'm running..?

More and more it's seeming "recording, editing and shaping with Audacity" is an Art...

I tried recording with Fedora-14 & Centos-6..  When I load Audacity in F-14, the toolbar at the bottom on the screen jitters a lot while loading..  I suppose that indicates software conflicts..? so F-14 is Out...  Centos-6 is problematic for installing many various softwares I need for art, music and desktop customizing...  Seems I'm off to "DistroWatch" in search of a suitable OS for music...

The first part of the plan is to study your Audacity link till I know it...

---

### Post by FakeOutdoorsman on 2012-06-15
> **MissTina said:**
> What's the best converter for wave to mp3..?

LAME, or anything that uses it:
```
lame -V 4 input.wav output.mp3
```
or via ffmpeg:
```
ffmpeg -i input.wav -acodec libmp3lame -aq 4 -metadata title="Your Title" -metadata author="MissTina" output.mp3
```

A useful resource: [Recommended LAME encoder settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_encoder_settings).

---

### Post by Randy M on 2012-06-15
I have this set up on my wife's computer. Load Audacity and go to "Edit" and "Preferences". In "Devices" select "ALSA". Audacity should then find your turntable and allow you to record your vinyl. Be sure to have the turntable turned on and plugged in when you open Audacity.

---

### Post by SeijiSensei on 2012-06-15
Any suggestions for a simpler recording application than Audacity?  It seems like overkill for just recording from my turntable though the audio jack.  I like being able to remove background noise from the resulting file, but I presume I could do that anyway if I could first record to WAV with a simpler app, then feed the result to Audacity.  I've browsed around a bit at Google and Wiki, but perhaps others here have some suggestions based on actual experiences.

---

### Post by MissTina on 2012-06-16
> **eddier said:**
>   ...On the bright side, if you have or can obtain a standard turntable and an amp then you can record in much better quality.



Over the years, I've been grabbing-up turntables at garage-sales, and twisting-off play arms, w cartridges and stylus intact, from record players, in junk where ever I'd happen to find one..  I've got a box full, but quality stylus's are really hard to get these days, especially from trash..   The last 4 available stylus's for my cartridges, they wants $400+.. and "tomorrow" they'll probably want $500..  I'm considering going straight to laser.. but till then, I just gotta get the songs I need from that ton of plastic..  
They are abusing their market.. Trying to get tunes from the Net is a nightmare, and expensive..  It gives the feel like "if a crowd of visitors all banged sticks on the chimp-cages just before feeding time".. is how the "money-world" feels like to me, and to a few...  
So I'm gonna get those tunes to mp3, even if I hafta turn this tower insideout, and make it into an old radio...

But then there's the "cleanups".. eliminating scratches and such without loosing the pleasing levels of the tunes.. "Oyie! it gonna-be a sretch...
Plus, there's bits of tunes I really don't want in them.. Those parts kill the tune's mood, they "bring me down"...  So, "audio-editing" here I come.. 
Plus, I've got installed "Hydrogen" & "FreeBirth"..  I've got a dozen new drum rifts to get into digi-audio, but no time to mess with the computer...  Would be nice if there was a sound softy that you click the mouse on "record at custom set levels, to mp3"..  Click, clickidy, click.. and the thing is recording plastic to a desktop file..  and done..  and you're listening to it on your ipod an hour later... 
But seems I gotta learn all about the driver's seat in an OS, and about all the controls in "a Boing 747's dashboard", ufor I kin gits this-here music to me ears...  But I learned enough for ten lifetimes..  Now I just wants to switch a thing On, and enjoy it doing it's thang..  I really don't wants to hafta get my hands in its insides, squishing juicy things here there and everywhere, just to use a thing...

So..  Is there a straight forward step by step, "1, 2, 3, 4, 5, 6.."  and suddenly tunes are recording, plastic to computer..?
I suppose if there isn't, it soon will be.. as soon as someone who writes Linux figures it out in computer language...  
Which pulls forth a few new questions:  Can people speak computer languages, like how a person can ramble-off a statement in English..? 
If one could, then you would simply tell the computer a fiction-story, and it would create a new software of it..?  "liquid transistors in a beehive matrix"...
I said that, so I could say this..  Can abstract & nature sounds be resynthed into English..?  I wonders if some messages would be scary, and some so funny it brings some to their knees.. or cry..  grrrr..  spin.. sink..?

Do Suns make sounds..?  
If they do.. how would one lower terra background distortions, so to get good recordings..?  
umm?.. "Audasunty" ?..



:guitar::popcorn:

---


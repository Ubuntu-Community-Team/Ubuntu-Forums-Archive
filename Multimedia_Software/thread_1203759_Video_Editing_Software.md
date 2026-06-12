---
title: "Video Editing Software"
date: 2009-07-03
forum: Multimedia Software
---

### Post by John Private on 2009-07-03
I need an Editing software for Videos the main thing I need is Zoom n' Pan so make sure it has that and I don't want to use Wine for it.

--John

---

### Post by John Private on 2009-07-04
I need an Editing software for Videos the main thing I need is Zoom n' Pan so make sure it has that and I don't want to use Wine for it.

--John

---

### Post by overdrank on 2009-07-04
Please do not create multiple threads on the same issue. Threads merged :)

---

### Post by John Private on 2009-07-04
> **overdrank said:**
> Please do not create multiple threads on the same issue. Threads merged :)Sorry No Body Replies and I thought it was liked moved to the second page once again Sorry.

---

### Post by zero777zero on 2009-07-04
professional video editing software is lacking on linux more than any other type of program

---

### Post by rsambuca on 2009-07-04
Try Cinelerra.  It should do the trick.

---

### Post by John Private on 2009-07-05
> **rsambuca said:**
> Try Cinelerra.  It should do the trick.Where can I download its not in Add/Remove.

---

### Post by philcamlin on 2009-07-05
> **John Private said:**
> Where can I download its not in Add/Remove.

[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu) :popcorn:

---

### Post by John Private on 2009-07-05
> **philcamlin said:**
> [http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu) :popcorn:New to Linux kinda seems hard to install...:(

---

### Post by heracles on 2009-07-05
Go to the Ubuntu site and download Ubuntu Studio version its no different to downloading Ubuntu standard which you have already done. Included in the download are lots of applications (although mostly sound ones) that are needed for video production including Kino a video editing application. Sadly as many of your other replies have intimated video editing is not vastly catered for under Linux. We can always hope however. All the other apps work under Ubuntu Studio as per the other versions of Ubuntu so you have nothing to lose in trying it.

---

### Post by rsambuca on 2009-07-05
> **John Private said:**
> New to Linux kinda seems hard to install...:(

Did you read the instructions?  All you have to do is copy and paste this command into a terminal and press 'enter'.  To open a terminal, go to your top menu bar and select Applications -> Accessories -> Terminal.  Paste this command into the terminal window and press 'Enter':

```
wget -q http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
```

---

### Post by jukingeo on 2009-08-27
> **rsambuca said:**
> Did you read the instructions?  All you have to do is copy and paste this command into a terminal and press 'enter'.  To open a terminal, go to your top menu bar and select Applications -> Accessories -> Terminal.  Paste this command into the terminal window and press 'Enter':

```
wget -q http://akirad.cinelerra.org/pool/addakirad.deb && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update
```

Hmmm, I am installing Cinelerra too right now and ran that line in my Terminal.  It looked like it was doing some kind of install, but yet, I don't have a Cinelerra icon in my programs menu.  Am I missing something?

Thanx,

Geo

---

### Post by beastrace91 on 2009-08-27
After running the above posted line did you also actually install the program using ```
sudo apt-get install cinelerracv
``` in terminal? The line in the above post simply adds the cinelerra repos to your sources.list

Once it is actually installed it should appear under Applications->Sound & Video->Cinelerra

~Jeff

---

### Post by jukingeo on 2009-08-27
> **beastrace91 said:**
> After running the above posted line did you also actually install the program using ```
sudo apt-get install cinelerracv
``` in terminal? The line in the above post simply adds the cinelerra repos to your sources.list

Once it is actually installed it should appear under Applications->Sound & Video->Cinelerra

~Jeff

Oooops, yes running the install WOULD help.  I have it up and running now.  Thanx.

I think it would be a good idea to sticky those two terminal lines someplace as it would make a quick and easy way to install the program.

---

### Post by AlexanderDGreat on 2009-09-12
Do I need to reformat my Ubuntu JJ 9.04?

---

### Post by jukingeo on 2009-09-12
> **AlexanderDGreat said:**
> Do I need to reformat my Ubuntu JJ 9.04?

Oh!  I guess you found your way here.

Reformat?  No, you shouldn't have to touch the OS.   Just copy those lines to get Cinelerra and then install it.  The program should run even without rebooting (but I would recommend a reboot after install).

Geo

---

### Post by AlexanderDGreat on 2009-09-13
Sorry but my question was intended for another reply.

He said that I install Ubuntu Studio. What if I'm using Jaunty right now? Do I need to clean format it or install Studio just on top of it?

He said that Studio has already Cinelerra and its dependencies installed on it.

Sorry for the confusion.

Thanks. =)

---

### Post by jukingeo on 2009-09-13
> **AlexanderDGreat said:**
> Sorry but my question was intended for another reply.

He said that I install Ubuntu Studio. What if I'm using Jaunty right now? Do I need to clean format it or install Studio just on top of it?

He said that Studio has already Cinelerra and its dependencies installed on it.

Sorry for the confusion.

Thanks. =)

Oh, ok, in that case YES you have to do a complete reinstall because if you just add the Ubuntu Studio components to Ubuntu, you will still not have the rt kernel.  (I found that out the hard way) It is very much advisable to do a fresh install when dealing with Ubuntu Studio.  In Hardy you still you have to make some mods to Jack & FFADO if you want to use firewire.  Jaunty should have the updates and you need not worry about it there.

As for Cinelerra being installed with Ubuntu Studio, it wasn't on my version (Hardy).   I seriously doubt they added it to the Jaunty package, BUT I could be wrong.

Geo

---

### Post by AlexanderDGreat on 2009-09-14
Great got all theories I need, I need to take action. Thanks community. =)

---

### Post by AlexanderDGreat on 2009-09-15
Hey, I've finally installed cinelerra and quite the contrary, it's so EASY to use!

Plus, it only crashed 1x on my Ubuntu 9.04 while rendering 2x 1-minute span videos with transitions and effects.

Compared to others kdenlive and OpenShot which crashed 149x just doing cutting and transitions.

To only take away watch these tutorial videos:

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc&](http://www.youtube.com/watch?v=-Q-NTYLiyKc&)

Trust me it would only take 30-45 minutes of your time. If a newbie like me can do it, you can do it too...

Thanks. =)

---

### Post by jukingeo on 2009-09-15
> **AlexanderDGreat said:**
> Hey, I've finally installed cinelerra and quite the contrary, it's so EASY to use!

Plus, it only crashed 1x on my Ubuntu 9.04 while rendering 2x 1-minute span videos with transitions and effects.

Compared to others kdenlive and OpenShot which crashed 149x just doing cutting and transitions.

To only take away watch these tutorial videos:

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc&](http://www.youtube.com/watch?v=-Q-NTYLiyKc&)

Trust me it would only take 30-45 minutes of your time. If a newbie like me can do it, you can do it too...

Thanks. =)

Well, with the proper tutorial and instructions I would believe it.  Also if you have past professional video editing experience, that helps too.  I will check that guide out.

For me, while I have had my 'learning curve' pains with Cinelerra, I KNOW it is a good program and it is still on my system.  I would never get rid of it because I know it does work.  But I will take a peek at that guide, if you found it useful and it got you up and running quick perhaps I can learn a thing or two from it.

Geo

---

### Post by qamelian on 2009-09-15
> **jukingeo said:**
> Oh, ok, in that case YES you have to do a complete reinstall because if you just add the Ubuntu Studio components to Ubuntu, you will still not have the rt kernel.  (I found that out the hard way) It is very much advisable to do a fresh install when dealing with Ubuntu Studio. 
No, you don't need to do a fresh install. You can install the RT kernel from the repos the same way you can install the rest of Ubuntu Studio. I'm running it right now on my production box, installed on top of a regular Jaunty install.

---

### Post by AlexanderDGreat on 2009-09-15
Hi jukingeo, out of frustration, that's why I needed to watch the videos.

You will find it very stable and easy trust me! =)

I'm now editing 3.0gb videos, cutting, pasting, inserting subtitles, transitions, mp3s, deinterlacing, making volume to a minimum, and I don't have editing experience, maybe Windows Movie Maker. =)

From my brother's iMovie - I extracted movie files to m4v, but there were no sounds, I converted them using winff to DV files 4:3, and cinelerra accepts them without difficulty.

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
Basic Editing in Cinelerra Pt. 2 - [http://www.youtube.com/watch?v=r4ollw6Cqjc&](http://www.youtube.com/watch?v=r4ollw6Cqjc&)
Basic Editing in Cinelerra Pt. 3 - [http://www.youtube.com/watch?v=cIjSBiWc9Qs&](http://www.youtube.com/watch?v=cIjSBiWc9Qs&)
Basic Editing in Cinelerra Pt. 4 - [http://www.youtube.com/watch?v=gxWbfhD6Tnw&](http://www.youtube.com/watch?v=gxWbfhD6Tnw&)
Basic Editing in Cinelerra Pt. 5 - [http://www.youtube.com/watch?v=PyxCf5qwYlE&](http://www.youtube.com/watch?v=PyxCf5qwYlE&)

And a lot more, just subscribe to the guy's channel.

Hope you can make great movies without much friction. =)

---

### Post by jukingeo on 2009-09-15
> **AlexanderDGreat said:**
> Hi jukingeo, out of frustration, that's why I needed to watch the videos.

You will find it very stable and easy trust me! =)

I'm now editing 3.0gb videos, cutting, pasting, inserting subtitles, transitions, mp3s, deinterlacing, making volume to a minimum, and I don't have editing experience, maybe Windows Movie Maker. =)

From my brother's iMovie - I extracted movie files to m4v, but there were no sounds, I converted them using winff to DV files 4:3, and cinelerra accepts them without difficulty.

Basic Editing in Cinelerra Pt. 1 - [http://www.youtube.com/watch?v=-Q-NTYLiyKc](http://www.youtube.com/watch?v=-Q-NTYLiyKc)
Basic Editing in Cinelerra Pt. 2 - [http://www.youtube.com/watch?v=r4ollw6Cqjc&](http://www.youtube.com/watch?v=r4ollw6Cqjc&)
Basic Editing in Cinelerra Pt. 3 - [http://www.youtube.com/watch?v=cIjSBiWc9Qs&](http://www.youtube.com/watch?v=cIjSBiWc9Qs&)
Basic Editing in Cinelerra Pt. 4 - [http://www.youtube.com/watch?v=gxWbfhD6Tnw&](http://www.youtube.com/watch?v=gxWbfhD6Tnw&)
Basic Editing in Cinelerra Pt. 5 - [http://www.youtube.com/watch?v=PyxCf5qwYlE&](http://www.youtube.com/watch?v=PyxCf5qwYlE&)

And a lot more, just subscribe to the guy's channel.

Hope you can make great movies without much friction. =)

Did you find that you had to load all the codecs for Cinelerra.  I had to do that with some of the file formats.  I still have to add more though.

Geo

---

### Post by AlexanderDGreat on 2009-09-16
Hi, I really don't know the technical side to Cinelerra.

Here is my case: I had a bunch of .m4v videos from iMovie, converted them to avi's with 16:9 aspect ratio (for DVDs) using Avidemux.

It's friendly GUI video converter in my opinion.

Then I Load files to Cinelerra, edit, cut, paste, insert subtitles, burn to dvd, distribute to family and friends, and I'm so happy. =)

---

### Post by jukingeo on 2009-09-16
> **AlexanderDGreat said:**
> Hi, I really don't know the technical side to Cinelerra.

Here is my case: I had a bunch of .m4v videos from iMovie, converted them to avi's with 16:9 aspect ratio (for DVDs) using Avidemux.

It's friendly GUI video converter in my opinion.

Then I Load files to Cinelerra, edit, cut, paste, insert subtitles, burn to dvd, distribute to family and friends, and I'm so happy. =)

Well, that is another way to work around the codec problem...just convert.  I usually prefer to use the proper codec because some conversion processes are "lossy" and you loose some of the quality.   But then again there is a final conversion process anyway before you go to burn a disc.  Just some conversion processes are better than others.  Bottom line, if you like the quality of the conversion, then you are good to go!

In my case, I have a lot of .flv files from doing captures off the internet.  So I need to find that codec for Cinelerra.  With OpenShot, no problem, the program has all the codecs.

Geo

---

### Post by wildhostile on 2009-09-17
Hi jukingeo,

Cinelerra 2.1 doesn't support .flv files. Cinelerra 4 does. But the binary file (to run the software) is still buggy and very few people succeeded to compile the sources.
You can still test it. see ==> [http://www.heroinewarrior.com/cinelerra.php#download](http://www.heroinewarrior.com/cinelerra.php#download).

Roland.

---

### Post by jukingeo on 2009-09-19
> **wildhostile said:**
> Hi jukingeo,

Cinelerra 2.1 doesn't support .flv files. Cinelerra 4 does. But the binary file (to run the software) is still buggy and very few people succeeded to compile the sources.
You can still test it. see ==> [http://www.heroinewarrior.com/cinelerra.php#download](http://www.heroinewarrior.com/cinelerra.php#download).

Roland.

Ahhh, I thought when I reinstalled Cinelerra I was getting the latest version.  I guess not....it is still 2.1.

Ok, so that is a bummer. 

I think I am just going to have to spend a few evenings and convert my .flv files.  Just have to face the music and do it.

That in mind, what is a GOOD .flv video conversion program?

Thanx,

Geo

---

### Post by AlexanderDGreat on 2009-09-19
@jukingeo hi, maybe you can ask that guy in the Cinelerra tutorials I think he's good because I saw he's a network engineer, and responds quickly, maybe he knows a few tricks or easy routines to convert videos, and where to get those codecs.

Yeah, I did notice a significant decrease when jumping from format to format. But in our camera, I extracted the videos, uncompressed it's 1.3 gb AVI.

But in m4v it's only 384 mb, how do you solve problems like these?

---

### Post by jukingeo on 2009-10-01
> **AlexanderDGreat said:**
> @jukingeo hi, maybe you can ask that guy in the Cinelerra tutorials I think he's good because I saw he's a network engineer, and responds quickly, maybe he knows a few tricks or easy routines to convert videos, and where to get those codecs.

Yeah, I did notice a significant decrease when jumping from format to format. But in our camera, I extracted the videos, uncompressed it's 1.3 gb AVI.

But in m4v it's only 384 mb, how do you solve problems like these?

Hello Alex,

Sorry I been away from my machine for a while.  Two weeks ago I went on vacation and this past week I spent quite a bit of time catching up at work.   It is only today where I got back to handle some of my Linux issues.

With OpenShot, they do acknowledge that there is a bug in the VIDEO to audio sync (not vice versa).  It could be a buffer issue.  So they are working on it.

I have not had a chance to play around with those suggested tutorials in Cinelerra.  In fact my video projector came this week and I have yet to unpack it to try it out.

Busy busy busy.

I will be back here soon though.

Geo

---

### Post by AlexanderDGreat on 2009-10-05
Hi, I've made up my mind, since I was given 60+ more videos to EDIT with formats like WMV, MP4, AVI, MPG, and FLV, I organized a plan to use them.

First, I will use Avidemux, to convert them using:

Video: mpeg4 AVC (x264)

* Is this the same with H264? I want to use this because it correctly detects my aspect ratio

Audio: AAC

* I will use this because I find MP3 (Lame) has a lot of restrictions and might add to complexity and technicality, plus AAC is free.

Finally, I will use mp4 as my Container since it's small in size? And YouTube loves it, so does Cinelerra.

That's all.

Pls. comment on my method.

Thanks.

---

### Post by jukingeo on 2009-10-05
> **AlexanderDGreat said:**
> Hi, I've made up my mind, since I was given 60+ more videos to EDIT with formats like WMV, MP4, AVI, MPG, and FLV, I organized a plan to use them.

First, I will use Avidemux, to convert them using:

Video: mpeg4 AVC (x264)

* Is this the same with H264? I want to use this because it correctly detects my aspect ratio

Audio: AAC

* I will use this because I find MP3 (Lame) has a lot of restrictions and might add to complexity and technicality, plus AAC is free.

Finally, I will use mp4 as my Container since it's small in size? And YouTube loves it, so does Cinelerra.

That's all.

Pls. comment on my method.

Thanks.

So Advidemux is also a converter?  I thought it was just a 'limited' editor.

I thought that I had the new version of Cinelerra, but I don't so I DON'T have support for .flv files as I thought.  While the new version of Cinelerra has support for .flv files, I heard it was buggy.  Anyway, I might end up on the conversion bus as well.  I am still hoping for OpenShot though.  They have acknowledged a sync bug and hopefully they can fix it soon.

Geo

---

### Post by AlexanderDGreat on 2009-10-05
Yeah, it wouldn't load FLVs and MKVs. Haven't tried the new version though.

Here's what I do though:
Launch Avidemux
Click Open (I think it's only 1 video at a time)
On the left, Choose Video: MPEG-4 AVC (x264)
Audio: AAC (FAAC)
Format: MP4
Then on the top choose "Save" - Then save it!

I know there lots more conversion programs out there, but due to the fast nature of my work, I chose the simplest and easiest. More importantly, it works for me.

Just share your ideas if you want.

---

### Post by jukingeo on 2009-10-14
> **AlexanderDGreat said:**
> Yeah, it wouldn't load FLVs and MKVs. Haven't tried the new version though.

Here's what I do though:
Launch Avidemux
Click Open (I think it's only 1 video at a time)
On the left, Choose Video: MPEG-4 AVC (x264)
Audio: AAC (FAAC)
Format: MP4
Then on the top choose "Save" - Then save it!

I know there lots more conversion programs out there, but due to the fast nature of my work, I chose the simplest and easiest. More importantly, it works for me.

Just share your ideas if you want.

Supposedly when you download Cinelerra, it will default to the older version.  The newer version (4 I think) has a harder install procedure.   This version WILL support the FLV files, but it is still isn't very stable. 

So it looks like for Cinelerra I would be forced to convert for now.

My mistake though is that I 'waited' for a bug to be resolved with OpenShot and I should have been looking into the Cinelerra tutorials.   Now I have an event coming up for Halloween.  My video presentation is almost fully together, but I made it in OpenShot.   I guess for now I am going to complete it in OpenShot and just have to live with the  audio/video sync problem.  My movies I am going to run via VLC though so that will be no problem.  But my custom splash screens will run through OpenShot.    Only the first intro screen is sync dependent though, so it should work out fine.   I am hoping though that they will eventually fix the problem because for quick and easy editing OpenShot is the only hope for a multi file format editing program for Gnome.  But if the issue isn't resolved by Christmas then I am just going to have to bite in the sour apple and do the long conversions and fully learn Cinelerra.  Then I wouldn't need anything else.

Geo

---

### Post by AlexanderDGreat on 2009-10-14
@jukingeo, yeah, I can relate. In my case, I invested A LOT OF TIME learning Sony Vegas. Then, I switched to Linux. I listed every task I do in Windows and its equivalent in Ubuntu. So far, Cinelerra has been the easiest for me and thus like Sony Vegas for my projects, but everything I learned is now, a waste! Good luck in your journey.

---

### Post by jukingeo on 2009-10-14
> **AlexanderDGreat said:**
> @jukingeo, yeah, I can relate. In my case, I invested A LOT OF TIME learning Sony Vegas. Then, I switched to Linux. I listed every task I do in Windows and its equivalent in Ubuntu. So far, Cinelerra has been the easiest for me and thus like Sony Vegas for my projects, but everything I learned is now, a waste! Good luck in your journey.

You are probably right.  I SHOULD invest more time into Cinelerra.  

Basically what I want to do is create a Drive-In theater style program for Halloween  that goes like this:

Trivia slides to background music as guests arrive-->Custom intro identifying 'theater'-->Older Nostalgic Theatre Rules --> Two older sci-fi/horror trailers-->Movie Short (Little Rascals episode)-->Snack bar consession ad --> First Feature "Monsters V.S. Aliens" (will run this from DVD)-->10 minute intermission clip-->2nd Feature "E.T. The Extra Terrestrial".   

After this lineup the kiddies go to bed and I am going to cap the night off with "Alien".

So overall it is mostly going to be sci-fi themed.  I have not decided to do anything fancy, but the trivia slides and custom intro will need a backing audio track.  It is this custom into that I am having the trouble with in OpenShot. 

Everything up to the Snack Bar Consession ad I would like to compile into one file using the editing program (Cinelerra).  Then I will have VLC run that file and then after the snack bar concession ad The DVD player will take over and it will be VLC from there on in.

I COULD have VLC do most of the work, but the trouble is that sometimes when VLC changes resolution, it quickly shows the desktop for a couple of seconds and I don't want that.  So I am trying to keep VLC down to a minimum.

I have much planned for the event so this weekend I pretty much would like to get this all edited together.

Pretty easy to do in Cinelerra?

Thanx,

Geo

---


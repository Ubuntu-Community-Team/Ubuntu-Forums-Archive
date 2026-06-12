---
title: "How to Normalize mp3s"
date: 2009-11-26
forum: Multimedia Software
---

### Post by Ghost|BTFH on 2009-11-26
The purpose of this post is to give users the opportunity to properly adjust the audio volume of an mp3 collection so that the maximum volume for each song remains the same, while keeping the songs low points and high points as they were intended to be heard.

It is also my purpose to show users how to fix a bug that has not been fixed in over two years.  If anyone can find a more elegant way to do this, please let me know.

*****************************

[COLOR="Red"]PLEASE NOTE![/COLOR]  The processes I describe in the following post involve changing the code in a program as well as permanently altering music files!  If you are uncomfortable with this process, DO NOT ATTEMPT IT!

[COLOR="Red"]I am not responsible for the death or destruction of your music library - always remember to make backups of any file prior to altering it in any way![/COLOR]

*****************************

I've recently wanted to "normalize" my music library, only to find out that I didn't understand what it was that I actually wanted.

First, let me say that normalizing, in its purest form, is not something most people will ever want done to their music library.  I have learned this the hard way.

What normalizing does by default, is scan a file for an "average" volume and pull up the soft spots to match the loud spots.  The issue with this is that some music is designed to start off quiet and build to a powerful climax (most classical music and heavy metal are prime examples) and this effect is almost completely ruined as a result of the normalizing.  The soft spots have now hit the same volume as the crescendo and there's really no emotionally powerful explosion left in the music.

What I have found to be the best experience is to adjust the volume of each file to a specific peak - this means the loudest part of each song will hit exactly the same decibel rating.  The rest of the song will be adjusted accordingly, thus giving you the full range of sound at the volume it was meant to be.

So how is this done?  There are several options out there for us, including mp3gain, as an example (not a good example in my book) that adjusts volumes within the tags of the mp3 so the files themselves are untouched.

Sounds great, but if you want to use that file in a variety of ways, including burning a mix CD, you will find that not all applications will read that tag properly - if at all.  The end result will be varying volumes over a range of songs both burned onto CD and listened to in various mp3 players.

Instead, I prefer to alter the file itself.  Granted - if you have all the CDs, burning them as .wav and altering the file from there is probably the very BEST solution, but that's not always possible for a variety of reasons.

So what I have discovered as the best solution for my own needs is to use normalize-mp3, which will take an existing mp3 file, break it down to .wav, adjust the audio properly and then convert it back into .mp3 format.

Now I know there will be those who say "But Ghost, decoding and then re-encoding mp3s will degrade your audio!!!" and to those people I say it's true!  However, I challenge you to degrade an mp3 by simply decoding and re-encoding it one time.  I personally have done so to an .mp3 over a dozen times as a personal experiment.  I noticed audio quality loss after about the 4th time it was done.  Prior to that, there was no noticeable loss in quality.

If you can show me proof that there is serious audio loss, I'll be happy to listen.  Until then, please keep an open mind about this process and try it for yourself before you automatically assume it will degrade the sound quality.

I digress.  

****************** This section for Jaunty Jackalope and back, Karmic has the file "fixed" properly!*******************
In order to use normalize-mp3, we actually have to fix it first!  Sadly this has not been fixed even though there are ample bug reports on it, but thanks to Matt Hickford's post in one of those reports, there is a semi-easy fix for the program.

Step 1:  Install what we need.

*sudo apt-get install normalize-audio lame mpg123*

Step 2: Fix what we need.

*sudo gedit /usr/bin/normalize-mp3*

The first thing you will notice (after all the comments) is a section that has:

[COLOR="green"]$MP3DECODE = " -q -o %w %m";
$MP3ENCODE = " -quiet %w %m";[/COLOR]

This is where the program will error out every time until it's fixed.  We want to change these two lines to read:

[COLOR="green"]$MP3DECODE  = "mpg123 -q -w %w %m";
$MP3ENCODE  = "lame --quiet %w %m";[/COLOR]

This will specify the decoder (mpg123) and the encoder (lame) and actually make the program work the way it is intended.  Why this issue has not been fixed in over two years is anybody's guess.

Now the only issue I've noticed is that for some reason, adjusting the bitrate just doesn't seem to work.  It always defaults back to whatever lame's default setting is.  To work around that, what I do is alter lame's default setting inside the normalize-mp3 file by adding the following:

$MP3ENCODE  = "lame --quiet [COLOR="red"]-b 256[/COLOR] %w %m";

Note, you can change the number after -b to whatever you prefer.  You could even pass on -V (variable bitrate) or any of the other "lame" commands.  Just remember, whatever you change in here, you change for normalize-mp3 and any file you use it on will be adjusted in that fashion.

Now that we have a properly working normalize-mp3, we can use it on our library!

****************** End section for Jaunty Jackalope and back********************

First, [COLOR="Red"]TEST TEST TEST!  DO NOT JUST CONVERT YOUR ENTIRE LIBRARY WITHOUT TESTING FIRST![/COLOR]  Grab a few random mp3s and COPY them into a separate folder away from everything else.  Run your tests on them first, if all works as planned, great.  If not, adjust your settings and try again.

I generally create a folder called ~/Downloads/ and then do my testing in /mp3s/ which I create inside the /Downloads/ folder, thus making sure I don't accidentally edit something I wanted left alone.

So now we have a few test mp3s sitting in a lone folder, let's go into the terminal and cd into that folder.  So for mine I would type:

*cd ~/Downloads/mp3s*

Next, while in the terminal, type the following command:

*normalize-mp3 -a -8dBFS -v *.mp3*

This will decode the .mp3 into .wav format and then pass on the command to adjust the amplitude of the file to -8dBFS, and then re-encode it back into .mp3 format.

I arrived at -8dB after much experimentation with varying levels and studying the results in audacity.  I noted that going beyond -8dB (Note, the lower the number, the higher the volume) resulted in clipping (not something I want in my music library!) but -8dB gave me the closest result to max dB without clipping.

The default format is -12dB, which is rather soft for my tastes but definitely will keep you free of clipping, so if in doubt, just use [COLOR="Red"]-a[/COLOR] instead of [COLOR="Red"]-a -8dBFS[/COLOR].

Now take a listen to the mp3s.  We're listening for 3 things here:

Soft spots where there should be soft spots.
Max loudness being the same between all the mp3s.
No clipping or distortion.

If you've got all that and are happy with the results, then it's time to fix our music library!

If not, replace the mp3s with copies from the music library. (We don't want to continuously re-edit the same file over and over again - it will eventually harm the sound quality!)

Once you've found your proper settings, cd back into your music library's root folder (mine is ~/Music/) and from the terminal type in this command:

*find . -name '*.mp3' -exec normalize-mp3 -a -8dBFS -v {} ';'*

This tells it to find any file in the current folder or subfolders with the extension .mp3.  When it finds them, it is to execute normalize-mp3 and adjust the amplitude to -8dBFS in verbose mode.

This will take quite a lot of time depending on the size of your library.  Plan to do this before bed and it will most likely be done when you get up.

Afterward, you will be able to listen to your music through any of the mp3 programs in Ubuntu without altering your speaker volume for each song, be able to transfer them to your favorite mp3 player and enjoy them all at the same volume and even burn a CD of various mp3s without having to run normalize before the burn process.

This process will also work with .ogg files however, it will recreate the .ogg file if you ran the process like this:

*find . -name '*.ogg' -exec normalize-mp3 -a -8dBFS -v {} ';'*

If you wanted to convert the .ogg to .mp3 format, you would simply use:

[I]find . -name '*.ogg' -exec normalize-mp3 -a -8dBFS -v [COLOR="Red"]--mp3[/COLOR] {} ';'
[/I]
This will convert the .ogg into .wav, adjust the amplitude and then re-encode the file in .mp3 format.

Enjoy!

PS: If anyone knows of an easier way to adjust the bitrate using normalize-mp3 directly, please feel free to post it!  In my experience, --bitrate ### does not work.  Perhaps it's another piece of the code that needs to be fixed.

---

### Post by Ghost|BTFH on 2009-11-30
38 views and no replies???

Well, I guess they can't all be winners.

Cheers,
Ghost|BTFH

---

### Post by andrea000 on 2009-11-30
Hi,

Thanks i believe this is what i have needed i have
some mp3's that (on my player)say out of range so
i am hoping this will fix them.

---

### Post by automaton26 on 2009-12-17
Thanks for the guide - it pointed me in the right direction. By the way, the script was already correct (fixed) under my Karmic 9.10 installation.

I also looked at using the **Audacity** application to normalize my tracks. The default "MP3 Conversion" script (under the "File...Edit Chains..." menu) does Normalization and you can "Apply Chains..." to do it to a set of files.

However, that doesn't do exactly what I want either - has anyone found a normalizing solution that both works across a folder hierarchy *and* maintains existing bitrate ?

---

### Post by Ghost|BTFH on 2009-12-17
> **automaton26 said:**
> Thanks for the guide - it pointed me in the right direction. By the way, the script was already correct (fixed) under my Karmic 9.10 installation.

I also looked at using the **Audacity** application to normalize my tracks. The default "MP3 Conversion" script (under the "File...Edit Chains..." menu) does Normalization and you can "Apply Chains..." to do it to a set of files.

However, that doesn't do exactly what I want either - has anyone found a normalizing solution that both works across a folder hierarchy *and* maintains existing bitrate ?

The only way I could think of doing something like that would be using a script where you would first query the file's bitrate, get the answer and then plug the result back into the script.

Although Audacity may have a way of keeping track of bitrates - I have never used it to do a batch of files before.

As for the file being correct (FINALLY!) in Karmic, that's great news! Only took them over two years. :D

Cheers,
Ghost

---

### Post by vanadium on 2009-12-17
I do not quite agree with the initial post of this thread, which is interesting but leads to a suboptimal advise.

Instead of "normalize", the term used by the "normalize-audio" software, I would prefer to use the term "replay gain adjustment".

Wikipedia: "Audio normalization is the process of increasing (or decreasing) the amplitude of an entire audio signal so that the resulting peak amplitude matches a desired target."

What normalize-audio does, however, is more useful than just "normalizing": it adjusts the level of the audio such that the *perceived loudness* of the audio is similar between tracks. This is replay gain adjustment (see [http://en.wikipedia.org/wiki/Replay_Gain](http://en.wikipedia.org/wiki/Replay_Gain)).

You can REPLAYGAIN your mp3's MUCH FASTER and WITHOUT REENCODING in ONE SINGLE STEP.

For this, use the mp3gain program with the option "-a" (for album mode: all tracks receive the same adjustment; useful if your directory contains tracks from the same album) or "-r" (radio mode: each track is individually adjusted). These options cause mp3gain not just to store the tags, but to readjust the volume of the audio. The volume adjustment will work on any player, even those unaware of replay gain tags.

This approach will cause the mp3 file to be adjusted MUCH FASTER, and WITHOUT ANY REENCODING nor loss in quality.

Easymp3gain is a graphical interface to mp3gain: [http://sourceforge.net/projects/easymp3gain/](http://sourceforge.net/projects/easymp3gain/)

---

### Post by Ghost|BTFH on 2009-12-17
> **vanadium said:**
> I do not quite agree with the initial post of this thread, which is interesting but leads to a suboptimal advise.


Kind of like your advice?

Everyone has their own opinion, perhaps you should do your own post on the subject.  While mp3gain is an option for some, it's one I discourage most people from doing because quite simply, it makes the music sound like rubbish.  It trashes the kick in your bass while making your treble sound weak, not to mention what it does to vocals.

On top of all this, the method works for "normalizing" your music files right up until you try to burn it to CD - then the adjustments done (which are done via the mp3 tag and not the actual adjustment of the music) are dropped, leaving you with non-normalized audio.

This would make it completely useless to myself and to a great deal of people who enjoy ripping portions of their collection into mix CDs.

I do not need a computer algorithm killing the full range spectrum of my music to make it "appear" (perceived volume) normalized.  I would prefer that it simply adjust the song so that the loudest part of the track is the same as the loudest part of my other tracks - collection wide.  I would also prefer that this is done to the music itself, so I don't have to do it yet again every time I go to burn a CD.

If you can tolerate your music mushed up by a sub-standard algorithm that ruins the audio quality, enjoy.  But please don't jump my thread and imply that my method is substandard while offering a "solution" that doesn't even change the file but rather the tag for the computer to read and make adjustments on the fly.

Cheers,
Ghost

---

### Post by vanadium on 2009-12-17
> While mp3gain is an option for some, it's one I discourage most people from doing because quite simply, it makes the music sound like rubbish. It trashes the kick in your bass while making your treble sound weak, not to mention what it does to vocals.
Cannot be because the audio is unaltered. Replaygain or adjusting using your method gives the same result, except that in your case the data is reencoded and thus at least theoretically of lower quality (I agree with you that most people won't hear when transcoding at high quality).

> On top of all this, the method works for "normalizing" your music files right up until you try to burn it to CD - then the adjustments done (which are done via the mp3 tag and not the actual adjustment of the music) are dropped, leaving you with non-normalized audio.

You missed my point. You can use mp3gain also in a way that the audio itself is adjusted (-r or -a options). Then the corrected volume will make it to the CD, whether your CD-burning software supports replay gain tags or not.

For other file formats like ogg, your method is the way to go for creating CD's. These formats do not support lossless adjustment of the volume of the audio.Also in that case, one should not recompress, but just burn the adjusted WAV files.

I would never transcode my ogg collection for volume correction. Rather, I'd transcode my lossless flacs to wav, or re-rip my CDs, and perform volume adjustment with normalize-audio before encoding in ogg or another format.

> I do not need a computer algorithm killing the full range spectrum of my music to make it "appear" (perceived volume) normalized.
I need to emphasize again that this is a subjective, unsubstantiated statement.

> I would prefer that it simply adjust the song so that the loudest part of the track is the same as the loudest part of my other tracks - collection wide.
Agree fully.

>  I would also prefer that this is done to the music itself, so I don't have to do it yet again every time I go to burn a CD.
This is exactly what m3gain does with the -r or -a option. 

Other compressed formats, such as ogg or flac, cannot be "hard" adjusted (i.e. changing the audio itself) without reencoding, though. There, your method would be the only way. Quality wise, it is preferred to adjust using the replay gain tag for use on the computer. If the CD burning software does not support replaygain tags, your method is very useful to adjust the volume of the uncompressed WAV's before burning to CD.

> If you can tolerate your music mushed up by a sub-standard algorithm that ruins the audio quality, enjoy. 

...again. Please reread my previous reply.

> 
But please don't jump my thread and imply that my method is substandard while offering a "solution" that doesn't even change the file but rather the tag for the computer to read and make adjustments on the fly.

1) What was your PS. about? Yes, I have read your post till the end. Please do the same with my previous reply.
2) If there is any possibility that you method is not optimal, then it should be signaled and discussed. People can then decide for themselves once they are fully informed about the pro's and the cons.

---

### Post by Ghost|BTFH on 2009-12-17
> **vanadium said:**
> Cannot be because the audio is unaltered. Replaygain or adjusting using your method gives the same result, except that in your case the data is reencoded and thus at least theoretically of lower quality (I agree with you that most people won't hear when transcoding at high quality)

I understand what you're saying, but I also know what I'm hearing.  I run a high end sound system off my computer and I've done a lot of audio editing both for myself and for some local bands, so I have a little background with music and sound in general.

I've heard a quality loss using mp3gain that I have not heard using my posted method - it's actually why I bothered to post it in the first place.

[QUOTE=vanadium]You missed my point. You can use mp3gain also in a way that the audio itself is adjusted (-r or -a options). Then the corrected volume will make it to the CD, whether your CD-burning software supports replay gain tags or not.[/QUOTE]

I caught your point, I just disagree with it.  In my opinion, the options aren't the only thing that makes it to the CD, so does some poor audio quality.  I don't care that it *can* do it, I don't like *what* it does.

[QUOTE=vanadium]I would never transcode my ogg collection for volume correction. Rather, I'd transcode my lossless flacs to wav, or re-rip my CDs, and perform volume adjustment with normalize-audio before encoding in ogg or another format.[/QUOTE]

I agree.  Ripping to wav or converting flac to wav and doing the adjustments would be the very best way to go, but sometimes that's just not reasonable, especially if you have a 300+ CD collection. :)

[QUOTE=vanadium]I need to emphasize again that this is a subjective, unsubstantiated statement.[/QUOTE]

But it's a *fact* that mp3gain sounds just fine?  Actually, it's a subjective, unsubstantiated statement.  These are also known as opinions.  You have one, obviously, that mp3gain is the way to go.  I disagree and feel it is NOT the way to go.  

It's why I urge people to test it out themselves - if they can't hear a difference, hey...go for it.  *I* can hear a clear difference.  My wife can hear a clear difference.  My brother can hear a clear difference.  My mother who's half deaf can hear a clear difference. Anyone who's ever ridden in my car can hear a clear difference.  I even had a CD with both methods processed from the original CD using mp3gain vs. normalize, to give them a demonstration.  I know, I'm a sound nerd. :)

[QUOTE=vanadium]This is exactly what m3gain does with the -r or -a option.../......again. Please reread my previous reply.[/QUOTE]

I know what you're saying.  I know mp3gain has the option to hardcode the adjustments.  I also know that the sound quality is crap in comparison to the procedure I use and therefore wouldn't want to hardcode crap into my music files.  (This is, in case you were wondering, my opinion, just like everything else I've stated thus far)

[QUOTE=vanadium]1) What was your PS. about? Yes, I have read your post till the end. Please do the same with my previous reply.
2) If there is any possibility that you method is not optimal, then it should be signaled and discussed. People can then decide for themselves once they are fully informed about the pro's and the cons.[/QUOTE]

I did read your post all the way through, I don't agree with most of it.  Yes mp3gain can do what you're saying - it does it poorly in my opinion, end of discussion.

If there is a possibility that my method is not optimal, people can do a quick google search on "mp3gain" which I mention in my article as another option, just not one I agree with, and get half a dozen articles explaining how to use it.

At which time I would presume if they really wanted to know the difference for themselves, they'd try both processes and see if they can tell a difference and choose for themselves their own preferred method - whether it is my method or using mp3gain, or leaving everything alone and dealing with variable volumes.

I agree it's all about choice and from my research, there are tons of tutorials on how to use mp3gain - it's rather popular.  There's very little on how to really tweak normalize so it does a very nice, clean job without making everything really quiet (try the default settings once - you have to crank up your system to just hear it!) which I don't care for.

Since I spent quite awhile tweaking and testing this process to find the "sweet spot" in the software, I thought I'd fire off a tutorial that will save people about 2-3 hours of testing to hit optimal levels in their audio without clipping.

That would be what the P.S. is about.  I'm not running around yelling at people who write about mp3gain "HEY! YOUR METHOD IS SUBOPTIMAL!!!"  Instead, I did my research, tested the process multiple times, came to a conclusion and reported my conclusion in a (hopefully) clear and concise report for fellow users.

See my point now?

Cheers,
Ghost

---

### Post by vanadium on 2009-12-17
I remain troubled by your report to have experienced this loss in quality using mp3gain. For me, it remains extremely hard to believe that mp3gain was the cause. What you describe is impossible according to the theory on how it works. In addition, I would expect to see reports elsewhere of people having a similar issue.

Anyway, if you feel mp3gain is a problem, you should not use it indeed. I am glad I learned about the normalize-audio software through your post.

On the other hand, it remains my opinion, based on my experience, that your post was to be complemented by some critical comments. The final decision (and eventually further testing) is up to the user.

---

### Post by Ghost|BTFH on 2009-12-17
> **vanadium said:**
> I remain troubled by your report to have experienced this loss in quality using mp3gain. For me, it remains extremely hard to believe that mp3gain was the cause. What you describe is impossible according to the theory on how it works. In addition, I would expect to see reports elsewhere of people having a similar issue.

Well, you have to understand that I'm pretty picky when it comes to my audio, and the sound difference is very subtle.  In fact, most people would just shrug and say, "It's sounds similar" without really being able to put their finger on any oddities they might experience.

For myself, there is a deadening in the vocals, a slight muting in the trebles (cymbals, high hats, etc) and there is a slight depreciation in the sharpness of the bass.

For my wife, if I play one that's been adjusted using mp3gain, she cringes, expresses that the song sounds "dead" with no energy at all and over awhile will even complain about headaches.  The same music not modified by mp3gain causes no negative effect.

As this was a blind test where she was unaware of my music experimentation at the time, and based on the fact that she has been into music since she was a child and has acoustically astounding ears (She can tell when my guitar is off on low E by as little as an eighth of a turn on the tuning knob, which according to my tuner is just shy of perfect pitch.) I consider it a pretty accurate reflection of what's going on.

What I *can* tell you is that adjustment of an equalizer can reduce the negative effects of mp3gain.  That coupled with the speed that it can work, this may explain why DJs prefer to use it.  It's fast, simple and they usually do fine tuning via their EQ anyhow.

> **vanadium said:**
> Anyway, if you feel mp3gain is a problem, you should not use it indeed. I am glad I learned about the normalize-audio software through your post.

I'm glad I shared it then and yes, I agree, mp3gain is definitely not for me and never will be.

> **vanadium said:**
> On the other hand, it remains my opinion, based on my experience, that your post was to be complemented by some critical comments. The final decision (and eventually further testing) is up to the user.

I'd agree and I also urge other users (As well as yourself) to test these things out and see for themselves.

If you *can't* hear a difference, use whatever works for you.  mp3gain is very fast and pretty simplistic.  If you *can* hear a difference, use what sounds best to your ears - whether that's mp3gain or normalize.

Cheers,
Ghost

---

### Post by vanadium on 2009-12-18
> If you can't hear a difference, use whatever works for you. mp3gain is very fast and pretty simplistic. If you can hear a difference, use what sounds best to your ears - whether that's mp3gain or normalize.

So be it!

Cheers

---

### Post by Chronon on 2009-12-18
ReplayGain simply adds a relative gain adjustment in the form of a value written to metadata tags.  It doesn't change the data in the files or how they are decoded.  There should be no difference between applying replay gain to a track and adjusting the volume in the media player.  If there is, then something is wrong.

I also want to point out that .ogg supports replay gain just fine.  The vorbisgain program will calculate and add tags to .ogg files. I actually use Foobar2000 in Ubuntu to add Replay Gain tags to my music as it allows batch tagging of all files regardless of codec and supports automatically tagging albums with album gain.

OP's argument about burning to CD is sound, though.  I don't ever do this, so Replay Gain works fine for me.  All of my portable music players do support Replay Gain, so it's a perfect solution for me.

---

### Post by seeker5528 on 2009-12-18
Personally I prefer something that doesn't change the original audio.

Using the ReplayGain tool in SoundKonverter seems to work pretty well for me, the volume gets adjusted up or it gets adjusted down either on a track by track or album basis. I have not had any problems with it, not perfect for sure, since there is only so much you can do by adjusting the volume up or adjusting it down, but I have not noticed it changing the way the music sounds or that it changes how loud the loud and quiet spots within a song sound relative to each other. That's not to say that doesn't happen because I could see where there may be cases if it didn't do that where the quiet stuff may be too quiet and the loud stuff might get clipped, but I can't tell that when I listen to the music. 

If you have a portable music player that doesn't understand replay gain tags, which seems fairly likely, then I can certainly understand the desire to normalize the actual tracks.

If I burn a music CD, I expect the burning software to provide the option to normalize and I expect it to have similar results as replay gain does, if you are just burning the tracks as data to use with something that can play them back, then that may be another situation where you need to normalize the file instead of doing the replay gain thing. 

I could have sworn that at least on of the ripping programs had an option to normalize, but I am not having productive results on Google at the moment, having the option in the ripping software to normalize as part of the ripping process would be optimal.

In the end it all comes down to personal preference, and the limits of the hardware/software you are using.

Later, Seeker

---

### Post by luptinpitman on 2012-10-16
So I've run normalize-mp3 as described on a single album and everything appeared to go off without a hitch.

After completing I sucked all of the original files and the newly modified files into MP3Tagger to see what changed. Apparently 3 files were not modified and kept the original bitrate but added an APEv2 tag. All other songs were modified and re-encoded at 128 bitrate but do not have the APEv2 tag added.  Is this expected behavior?  The files sizes are radically lower on the modified files which makes sense because they are now CBR 128 instead of VBR ~256.

Appreciate the tutorial as I have been struggling with this for years now and still can't find a viable solution.

---


---
title: "Trouble encoding waves (Rhythmbox or Audio Juicer)"
date: 2009-01-05
forum: Multimedia Software
---

### Post by jamesisin on 2009-01-05
I am not able to properly encode CD's as .wav files.  The file is generated without any noticible error or glitch, yet when I try to play the files back audio devices on my Ubuntu 8.10 system offer only a generic GStreamer error.  If I try to play them back with VLC on my Mac or my Windows machine I get only static, Quicktime can't open them, and iTunes also plays static.

Anybody an encoding expert?

---

### Post by jamesisin on 2009-01-06
How about an aspiring encoding expert?

---

### Post by GepettoBR on 2009-01-06
I'm a moderate understander of encoding.

It seems that if no one can play the file, it simply isn't encoding right. To be absolutely sure, open it in Audacity and see if the waveform is truly static.

Most of the times such a problem occurs a specific encoder library is missing or corrupted, which shouldn't affect other forms of encoding. Did you also try encoding in any other formats, such as flac or ogg, and get similar results? If so, the problem might be with reading the CD itself. That being the case, your computer wouldn't be able to play the CD's tracks at all. Try playing directly from the CD.

In either case, if it still doesn't work, installing the w32codecs package (or w64codecs if you're running 64-bit Ubuntu) might solve your problem, as might reinstalling SoundJuicer.

---

### Post by jamesisin on 2009-01-06
For waves I tried encoding using both Sound Juicer and Rhythmbox with the same (static) results.

I was able to encode flacs using Rhythmbox without issue.

I don't see w32 anything listed in Synaptic.  Is it in there under a different name?

---

### Post by GepettoBR on 2009-01-06
> **jamesisin said:**
> For waves I tried encoding using both Sound Juicer and Rhythmbox with the same (static) results.

I was able to encode flacs using Rhythmbox without issue.

I don't see w32 anything listed in Synaptic.  Is it in there under a different name?

Unless I'm mistaken, Rhythmbox relays files to SoundJuicer for encoding, so it's natural that a problem with SJ would also affect RB. I'd try reinstalling SoundJuicer to see if it fixes the wave encoding.

Also, it appears "w32codecs" has been renamed to "non-free-codecs". Sorry for the wrong information.

Might I ask, though, why it's necessary that the files be in waveform encoding? FLAC is also lossless and renders much smaller files. There are other lossless options as well, such as Monkey's Audio and lossless ogg.

---

### Post by pedja_portugalac on 2009-01-06
> **jamesisin said:**
> I am not able to properly encode CD's as .wav files.  The file is generated without any noticible error or glitch, yet when I try to play the files back audio devices on my Ubuntu 8.10 system offer only a generic GStreamer error.  If I try to play them back with VLC on my Mac or my Windows machine I get only static, Quicktime can't open them, and iTunes also plays static.

Anybody an encoding expert?

Extract CD with cdparanoia. Open terminal and type:
```
cdparanoia -B
```
It will perfectly rip the CD to .wav files even if it's copy protected. After that you'll need lame if you want to encode to .mp3. 

PS. Ultimately I had problem ripping and even reading one new CD on ubuntu 8.10. cdparanoia resolved that problem perfectly ripping into .wav whole disk witch I encoded after into HQ Stereo VBR .mp3s with lame. Lames command is:
```
lame -m s -V 0 -q 0 input.wav output.mp3
```

Or you can make script like this one for whole folder:
```
#!/bin/sh
mkdir mp3_encoded
for i in *.wav ; do
lame -m s -V 0 -q 0 $i mp3_encoded/"${i%.wav}.mp3"
done
```

---

### Post by jamesisin on 2009-01-06
pedja_portugalac - Thanks for the script.  Can Lame do other formats (like wave-->ogg or wave-->aac)?

I'll check out cdparanoia also.


GepettoBR - Yeah, I thought about flac and ogg (and others).  The thing is that with storage as cheap as it is now I see no reason to risk *any* sort of data loss through compression.  Essentially, the reason I am making this server is to remove my CD shelves from my living room (more than 600 CD's).  I have good audio gear and I don't want to short change myself.

Lossless is key, of course, but I think I'll move as close to the original as possible.  I even considered just ripping the CD's as ISO's (which solves some problems and creates others).

---

### Post by GepettoBR on 2009-01-06
> **jamesisin said:**
> pedja_portugalac - Thanks for the script.  Can Lame do other formats (like wave-->ogg or wave-->aac)?

I'll check out cdparanoia also.


GepettoBR - Yeah, I thought about flac and ogg (and others).  The thing is that with storage as cheap as it is now I see no reason to risk *any* sort of data loss through compression.  Essentially, the reason I am making this server is to remove my CD shelves from my living room (more than 600 CD's).  I have good audio gear and I don't want to short change myself.

Lossless is key, of course, but I think I'll move as close to the original as possible.  I even considered just ripping the CD's as ISO's (which solves some problems and creates others).

Lame is exclusively an MP3 encoder. For AAC, you can look [here](https://help.ubuntu.com/community/RestrictedFormats/AAC) or use Nero's AAC Encoder, which is an excellent piece of software. Ogg encoders are a dime a dozen in the repos, but I don't use them often enough to make an informed recommendation.

As for risking "any sort of data loss through compression", worry not. Losslessly compressed files are much like a zipped archive that can be executed without requiring extraction. That's what the "lossless" stands for (no loss of information, only compresion), and it's only goal. If you rip a CD track to a wave file or rip to a flac file and then convert that to wave, the two wave files would be identical, and flac is around half the size. I use it all the time, as well as lossless video codecs like Lagarith, and I can vouch for the 100% fidelity of flac encoding.

But if storage really isn't a problem, then ripping to isos realy is the way to go. Some CDs have "hidden tracks" that the computer ignores when ripping. An example is Rammstein's "Reise, Reise" which features a black box recording before the first track. On a CD player, you can force-rewind to before 0:00 and hear it, but software players and rippers ignore everything before the 0:00 mark. Of course, playing the music on the computer would be a PIA, but that's as close to the original as you can get.

---

### Post by pedja_portugalac on 2009-01-06
> **jamesisin said:**
> pedja_portugalac - Thanks for the script.  Can Lame do other formats (like wave-->ogg or wave-->aac)?

I'll check out cdparanoia also.


GepettoBR - Yeah, I thought about flac and ogg (and others).  The thing is that with storage as cheap as it is now I see no reason to risk *any* sort of data loss through compression.  Essentially, the reason I am making this server is to remove my CD shelves from my living room (more than 600 CD's).  I have good audio gear and I don't want to short change myself.

Lossless is key, of course, but I think I'll move as close to the original as possible.  I even considered just ripping the CD's as ISO's (which solves some problems and creates others).
Lame can convert from .wav to .mp3 and .mp3 to .wav. The method I am using, preserving stereo and not using join-stereo, is very close to perfect and is specially recommended for use with devices like iPods and other players using headphones. Listening long hours constant beat rate .mp3s can be dangerous for ears, that's one more reason why variable beat rate is preferable! You can still choose to backup as lossless .wavs or flac but you'll need 1TB for about 700 CDs. Remember that full hard drives are very slow and risky. I think hard drives should never be used more then 50% of its total capacity.

---

### Post by GepettoBR on 2009-01-06
> **pedja_portugalac said:**
> Lame can convert from .wav to .mp3 and .mp3 to .wav. The method I am using, preserving stereo and not using join-stereo, is very close to perfect and is specially recommended for use with devices like iPods and other players using headphones. Listening long hours constant **beat** rate .mp3s can be dangerous for ears, that's one more reason why variable **beat** rate is preferable! You can still choose to backup as lossless .wavs or flac but you'll need 1TB for about 700 CDs. Remember that full hard drives are very slow and risky. I think hard drives should never be used more then 50% of its total capacity.

You mean "bit rate", of course, since encoding, unless done incorrectly, would not alter the speed of the music. But this is new information to me. Why is VBR "safer" than CBR?

---

### Post by pedja_portugalac on 2009-01-06
> **GepettoBR said:**
> You mean "bit rate", of course, since encoding, unless done incorrectly, would not alter the speed of the music. But this is new information to me. Why is VBR "safer" than CBR?

Bit rate, sorry. I saw it first on TV few months ago. If I remember well, it's about low noises. CBR mp3s have same volume even on low noises and that's what can harm ears and make head pain when you listen songs more then ? hours a day and it's even more dangerous when you listening it on high volume.

PS. It's strange I can't find anything about that on google.

---

### Post by jamesisin on 2009-01-06
I completely agree that 50% is a general, approximate maximum for hard drive performance.  But, again, storage today is cheap.  I can get 2TB of sata drives for maybe $300-$400 (mirrored, so four 1tb drives for instance).  I have paid that much for shelving.

I too am curious about this bit/beat rate being bad for one's ears.  I could accept easily that a fixed beat could be ill for one's mind/psyche, but I would think that *volume* would be much more a factor to the ears than anything relating to either bits or beats.  Link?

I definitely won't be using mp3's.  They are rather terrible when you get right down to it.  I have two iPods: one for music, the other for language lessons.  The music is all waves (sound quality is everything).  The lessons are heavily compressed (64bit stereo) aac files (sound quality is unimportant).


I have considered using flacs on the server, but then I run into a problem with my iPod.  I would have to maintain another library with files for my iPod.


It really is tempting to run iso's on the server.  Windows won't mount iso's natively, but I suppose I could perhaps find a way to transcode and output a usable signal to a Windows box (on/from the server).  Another issue is that if I mount an iso on the server, this could compound the buffer problem to the client machine.  And finally, this makes it very cumbersome to do something like create a playlist that jumps around my collection.  Thoughts?

---

### Post by GepettoBR on 2009-01-06
> **pedja_portugalac said:**
> Bit rate, sorry. I saw it first on TV few months ago. If I remember well, it's about low noises. CBR mp3s have same volume even on low noises and that's what can harm ears and make head pain when you listen songs more then ? hours a day and it's even more dangerous when you listening it on high volume.

PS. It's strange I can't find anything about that on google.

That doesn't make sense. Yes, CBR allocates the same amount of bits of data even in low or no-sound portions, but they simply carry information for "silence", not "static" or anything else The amount of bits per second is unrelated to volume, proof of that is that software to normalize the volume in mp3 files was popular long before mainstream devices were able to read VBR, or even ABR encodes. Distortions occur in high complexity parts of CBR encodes because there aren't enough bits per second, not in silent parts because there are too many.

This is probably some low-key urban myth.

---

### Post by GepettoBR on 2009-01-06
> **jamesisin said:**
> It really is tempting to run iso's on the server.  Windows won't mount iso's natively, but I suppose I could perhaps find a way to transcode and output a usable signal to a Windows box (on/from the server).  Another issue is that if I mount an iso on the server, this could compound the buffer problem to the client machine.  And finally, this makes it very cumbersome to do something like create a playlist that jumps around my collection.  Thoughts?

I'm not sure what exactly you mean by a buffer problem, but if you mount the  iso files on the server, you can probably create a playlist file that points to the mount points of the several ISOs instead of the ISOs themselves and use that on the client machine(s).

---

### Post by jamesisin on 2009-01-06
Hmmm... file paths into mount points.  Hadn't considered that.  Very interesting.  I would end up with hundreds of mount points (one for each actual disc).  Sounds hectic but I suppose there is no specific limitation that would prevent that.

What's the buffer issue?  As I see it:

There shouldn't be much in the way of a bandwidth issue across a 10/100 network like mine, assuming I'm not using the network for other activities at the time of listening (BT, terminal server, &c).  However, there is still the matter of getting the play data to the client machine in time for it to play each bit in sequence in real time.  Players, like iTunes, help this by activating a buffer to pre-load some segment of the incoming file.  The large the data segment, the more critical the buffer becomes.  One second of sound requires more data to be prepared when it's from a wave than when it's from an mp3--and so it would seem that buffering an iso might be more troublesome in this respect (unless, as we are discussing, we mount the iso and send the cda file--which ought to circumvent this issue).  Or something like that.


Looks like I already have cdparanoia installed.  Is there a gui or is it strictly command line?

---

### Post by GepettoBR on 2009-01-06
I know of no limitations to the number of images you can mount at once, but I've never had more than 10 mounted at one time. Since you're loking at way more than that, maybe you should look around.

And as for the sound buffer, wouldn't the problem be solved by just making it really big? Another possible (but more complicated) solution would be to not manage the player on the clients, but on the server and stream the output to the clients, which would reduce the amount of data requiring transfer. You would, however, need to ssh or use a virtual desktop to control the sever from the client, so that might not be a good idea.

---

### Post by logos34 on 2009-01-06
> **jamesisin said:**
> Looks like I already have cdparanoia installed.  Is there a gui or is it strictly command line?

most gui rippers use cdparanoia as their backend (soundjucier too).

Since you say you're getting a generic gstreamer error, I'd try getting these:
> sudo apt-get install [COLOR="Red"]ubuntu-restricted-extras[/COLOR] gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdread3 liblame0 

**Completely** uninstall sound-juicer/audio cd extractor and then reinstall it.

---

### Post by jamesisin on 2009-01-06
logos34 - A good suggestion.  I already have the restricted extras installed.  I reinstalled it just now, just in case.

Can you confirm that any of those codecs relate to wave output?

I am getting the gstreamer error when I try to play those ripped waves back, not when I am creating them.  The creation *seems* to be just fine.  But playback works on Windows and Mac--except what is played back is mere static.


GepettoBR - Yeah, I'm guessing it would be somewhere in the 700-900 range (due to multiple cd sets).

True on the buffer as well: really big.  Just not sure how big or how to go about it.  But you are correct (I think) about using streaming from the server (ought to negate the buffer issue based upon the largeness of an iso).

Maybe I could even craft a script that would auto-mount any iso within a particular directory/tree.

Of course, this probably also leaves wide open the issue of synquing my iPod(s).

---

### Post by logos34 on 2009-01-06
> **jamesisin said:**
> logos34 - A good suggestion.  I already have the restricted extras installed.  I reinstalled it just now, just in case.

Can you confirm that any of those codecs relate to wave output?

no, but ubuntu-restricted-extras recommends those gstreamer pkgs...besides you'll eventually need them at some point

> I am getting the gstreamer error when I try to play those ripped waves back, not when I am creating them.  The creation *seems* to be just fine.  But playback works on Windows and Mac--except what is played back is mere static.


i see 

the only thing I can think to suggest is examining the .wav files to make sure they'r normal 16-bit 44.1k pcm files

sudo apt-get install shntool

shntool info file.wav

good luck

---

### Post by jamesisin on 2009-01-06
I have all of those except liblame0.  Synaptic shows liblam4.  Is that the one you mean?

Sound Juicer, in its preferences (Editing profile "Voice, Lossless") it shows "audio/x-raw-int,rate=22050,channels=1 ! wavenc name=enc" under "GStreamer pipeline:".  This is normal for voice work.  I can change the rate for music (44100 x 2) but the fact is, if it's encoding waves at all any rate/channel (under wave) should work.  I'll try one and report back.

---

### Post by jamesisin on 2009-01-07
Well, I stand corrected.  I really do.  I have a standing workstation.  I am actually standing here typing all of this.  No ****.  Anyway...

I created another profile in Sound Juicer:

[LIST]
[*]Open Sound Juicer: Applications --> Sound & Video --> Audio CD Extractor
[*]Open the preferences: Edit --> Preferences
[*]Click the "Edit Profiles..." button
[*]Click the "New" button [name it whatever you'd like--I used "MusicWaves"]
[*]Then the "Create" button to close that dialog
[*]Select your newly created profile in the "Profiles:" list and click the "Edit" button.
[*]For "GStreamer pipeline:" you will enter "audio/x-raw-int,rate=44100,channels=2 ! wavenc name=enc"
[*]Under "File extension:" use "wav".
[*]Check the "Active?" box or you won't be able to select it from the drop-down in Sound Juicer.
[*]Close that and get to work.
[/LIST]

Using this newly created profile (by selecting it in the "Output Format:" drop-down) I was able to create satisfactory waves from from a CD.

If this doesn't work for you, ask yourself "why did I copy and paste the quotation marks?"

I'll be writing a blog post on this one.

---

### Post by jamesisin on 2009-01-07
Thanks: logos34, GepettoBR, and pedja_portugalac.

Come have a look at my music server project if you haven't already:

[http://ubuntuforums.org/showthread.php?t=1031063](http://ubuntuforums.org/showthread.php?t=1031063)


logos34 - shntool looks interesting.  What can you tell me about it?  Do you use it?

---

### Post by logos34 on 2009-01-07
> **jamesisin said:**
> 
logos34 - shntool looks interesting.  What can you tell me about it?  Do you use it?

yes, I used it for a while to convert .ape tracks (music torrents) on the command line.  Supports quite a range of formats.  

glad you figured out the basic sound juicer config--I was about to suggest [this page]("https://help.ubuntu.com/community/CDRipping#Installing%20Additional%20Audio%20Formats") but thought you already did all that

good luck

---

### Post by jamesisin on 2009-01-07
Don't know anything about .ape files.

That page looks great.  I love finding pages like that.  I'll probably include it in my blog post now.

I'll metion that tool also, if for no other reason than because it's potentially useful somewhen.

---

### Post by logos34 on 2009-01-07
.ape = monkey's audio

a lot of torrents these days are whole albums rolled as big ape images.  It has a slightly better compression ratio (average about 8% smaller than flac -best setting).  I'd rather flac personally because there's a lot of cpu overhead involved in playback and converting monkey's audio.

here's where I came across it:

[http://aidanjm.wordpress.com/2007/02/04/converting-monkey%e2%80%99s-audio-ape-files-to-flac-in-ubuntu/](http://aidanjm.wordpress.com/2007/02/04/converting-monkey%e2%80%99s-audio-ape-files-to-flac-in-ubuntu/)
[http://www.gomellow.com/?p=30](http://www.gomellow.com/?p=30)

anyway, enjoy

---

### Post by jamesisin on 2009-01-09
Only a few of my waves have metadata in them.  In specific, everything I encoding using Sound Juicer does not.  Do I need another app to add that metadata (artist namd and album name)?

---

### Post by logos34 on 2009-01-09
> **jamesisin said:**
> Only a few of my waves have metadata in them.  In specific, everything I encoding using Sound Juicer does not.  Do I need another app to add that metadata (artist namd and album name)?

wavs don't contain metadata, unless they're special broadcast format wavs (.bwf)

the application is supposed to fetch the info (from remote or local cddb) and apply it to compressed output file(s).  

you shouldn't be having this much trouble

---

### Post by jamesisin on 2009-01-09
Isn't trouble what computers are all about?

When Sound Juicer loads the CD it also pulls down the metadata.  Clearly it's using this to create the folder heirarchy and file names.  However, if waves don't support metadata then there would be no way for Sound Juicer to attach this information to each file, and so when I open my library in Rhythmbox it will have no ideas about where the music came from--only what it's current file name is.

I speculate it would be possible to write a plugin which would make assumptions about album/artist information based upon the folder heirarchy, but I know of no such extension.

At least, that's my current guess.  If this information is incorrect, please adjust...

---

### Post by logos34 on 2009-01-09
right--it applies the info it fetches from the server to the rip output folder (artist and album), but the only thing that gets attached to each file is the track title--look at the tag info using any media player and it will be empty.  I'm sure there's a plugin like you say, I don't know off top of my head because I never keep wavs

---

### Post by jamesisin on 2009-01-09
The rip output folder?  I don't see any info file in the folder (aside from the obvious music files).  I have hidden files/folders shown.  Did I miss your meaning?

---

### Post by logos34 on 2009-01-09
no, what I meant was it names the folders with artist and album...no info file or anything like that (although that what be neat since it might be what you're looking for!)

I don't know much abotu Rhythmbox.  I use amarok, which has gobs of scripts/plugins--there might be one to do what you want...Also, have you checked out **Wavpack**?  I have it but never use (flac works fine for me)...It may support tag info...The next closest thing to wav but at half (?) the size.

Edit: It does support tag info. So that's what I'd recommend.  Compression ratio better than I thought--just did a whole album = 41% size of original (235 MB vs. 567 MB).  

Forgot you were using iPod, but I think Rockbox firmware supports wavpack (lossy and lossless)

just throwing out ideas

good luck

---

### Post by jamesisin on 2009-01-10
Yeah, I was talking with my friend last night about Rockbox.  It supports flac and ogg for sure.  Since the only impedement to my choosing flac over wave at this point (since I can at any time convert any flac into wave or cda without losing any information) was my iPod/iTunes...

Well, I think it's time those rat-battereds (WMP too) started supporting flac.  As such, I should support flac and be one more (consumer) reason for them to support it.

In the interim, I can always create waves from the flacs for my Mac and thus my music iPod--or run Rockbox.

Been nice to have decided this before I encoded 200+ discs.  C'est la vie.

As to tagging waves, waves do not support tags per se.  Though you can add RIFF header information to a wave file, they apparently won't hold much information.  Typically album and artists would be all, but that would be enough.  I'm sure there is some Linux software out there which edits the RIFF headers, but since I've decided to support flac I won't likely be seeking it out.

---

### Post by jamesisin on 2009-01-10
For anyone interested, here is my blog post on this subject:

[http://www.soundunreason.com/InkWell/?p=588](http://www.soundunreason.com/InkWell/?p=588)

---

### Post by lostfawords on 2009-08-27
just my 2 cents - to rip CD's i find grip by far the best and most configurable gui. i use this to rip wavs which i keep as backups for the ease of replacing lost/damaged discs. (kept on several friends drives to be sure)

if you use the same scheme as i; /Artist/Album/<Track number> - Title
which can be set in the grip prefs so that it is saved in this way from the cddb info, then i use a small shell script to take the Artist Album Track Number and Title info from the filename and folder structure and convert any new files and folders in my Wave directory to tagged mp3s in my Mp3 directory.

oh, and vice versa for any songs for which i can only get as mp3s it will convert them to waves in the appropriate folder structure in my wave directory.

---

### Post by jamesisin on 2009-08-28
I'll take a closer look at Grip (I loaded it already).  I don't know that I need any of its specific features though.  I really do merely use Audio CD Extractor to rip flacs.  I get a new CD; put it in; rip it as a flac; and archive it into the box in the basement.

I would question your choice of waves, though.  You may want to check out my blog post (linked above) as I make a critical analysis of the benefits of waves v flacs.

Also, what is the file you attached?

---


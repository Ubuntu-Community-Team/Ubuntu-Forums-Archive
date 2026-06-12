---
title: "Audio conversion to AAC for the Nintendo DSi .M4A"
date: 2009-04-22
forum: Multimedia Software
---

### Post by the.scarecrow on 2009-04-22
Having acquired a new DSi, I wanted to try out the audio on the SDHC card slot. Problem was nothing I wanted to listen to was in .M4A format and searching Ubuntu forums didn't help me find a file conversion program that I liked. So I looked for all available applications and found FormatFactory 1.08 which I think is very easy to use and has a huge range of audio and video file conversions included.

Having downloaded and installed it in Windows XP I converted some files, copied them to the SDHC card and they worked perfectly.

But I don't use Windows, I wanted it in Ubuntu 8.10 and a Linux version does not seem to be available even though FormatFactory 1.08 is available as a free OpenSource application.

So I installed WINE 1.0.1 via Synaptic, then double clicked on the application “FFSetup1_80.exe” and bingo! FormatFactory seems to work perfectly in Ubuntu 8.10 using WINE. Now I can put audio files from any format I have ever seen onto my DSi as .M4A files, using Linux :).

I have only tested the .M4A output format but FormatFactory 1.08 oozes quality and so I think all the file conversions should work just as well. Its available from here.

[HTML]http://www.formatoz.com/[/HTML]

Hope this helps some other Linux/DSi users.

---

### Post by andrew.46 on 2009-04-23
Hi the.scarecrow,

I can appreciate the motivation for you to spread the word on a program that you have appreciated. You might however be interested to know that this particular program is in fact a front-end for several well known programs, the first 4 of the list below having considerable roots in Linux:

[LIST=1]
[*]FFmpeg
[*]MPlayer
[*]MEncoder
[*]mkvmerge
[*]MP4Creator
[/LIST]

You will see all of these in the directory FFModules. Importantly in my brief look at this program I could not see that the author of Format Factory actually acknowledges his considerable debt to these fine programs. My apologies if this is in fact incorrect.

All the best,

Andrew

---

### Post by the.scarecrow on 2009-04-23
Hi andrew.46

That's very interesting and if anything it is testament to the strengths of Open Source. I have only been using Linux since autumn last year and I have had great success with it, virtually dropping Windows completely.

As for Format Factory, I did read their web site and noticed that they encourage users to adapt and re-distribute it so for me they certainly have their heart in the right place.

As a non-technical user I like the fact they have put it all together in such an easy to use package, just a shame not to provide a native Linux version. However, Format Factory is not often referred on this forum and I wanted to pass on my results to help save others a bit of time. The fact it works in WINE gets a tiny mention on the WINE home site.

Thanks for you interest.

---

### Post by JoshuaRL on 2009-04-24
This looks pretty bad to me.  As andrew stated, it seems to heavily step on the toes of some important FOSS projects, without awknowledging their work.  I'd go so far as to say it goes against the GPL, and is in bad legal territory.  Sure, there's no money changing hands that I can see, but still this is problematic.

---

### Post by the.scarecrow on 2009-04-24
Ooops, I was just pleased with its functionality and usability, not what was going on under the bonnet.

Is it not that if the Open Source community gets worried about this level of correctness then should we be using any of these file formats anyway as they are not Open Source?

Snag is you can't listen to much using .ogg also it was difficult and more expensive to buy my MP3 player because I wanted it to play .ogg

---

### Post by JoshuaRL on 2009-04-24
Well, most of that is a gray area honestly.  But the community has made tools to use those proprietary file types, and given them away free with source code.  They only ask that you do the same if you use them in something, and acknowledge that you're using their work.  That's it.  And that's the thing that this programmer doesn't do.  Honestly, it's only a nice UI over top of those applications you probably already have installed from what I can tell.  And you have to run it in Wine!

I have a fair amount of .ogg files too, but I use Rockbox on my iPod and can play almost any audio file type.  Bought it on eBay for $100 used, full of music.  :)

---

### Post by FakeOutdoorsman on 2009-04-24
> **JoshuaRL said:**
> This looks pretty bad to me.  As andrew stated, it seems to heavily step on the toes of some important FOSS projects, without awknowledging their work.  I'd go so far as to say it goes against the GPL, and is in bad legal territory.  Sure, there's no money changing hands that I can see, but still this is problematic.

There are hundreds of these programs, and most are made by the same couple of groups in China, as one of the FFmpeg devs told me.  Sometimes they get added to the FFmpeg Hall of Shame, but they just change the program name.  They will sometimes make posts in these forums advertising their software.

---

### Post by the.scarecrow on 2009-04-24
Well as a 99.8% GUI user I always break out in a cold sweat when I start typing sudo something into a terminal session.

Are you saying all I need to do is enter a terminal command to convert some .mp3 podcasts into .M4A format, if so then I agree that is much more efficient. Snag is I don't know how to do that.

I think you are right that they should give credit to the source of the code they used as indeed they ask people who modify Format Factory to give credit to them.

I want to thank everybody for making the whole Linux thing available so in effect giving me back my PC to use it just as I want.

---

### Post by andrew.46 on 2009-04-24
Hi the.scarecrow,

> **the.scarecrow said:**
> Well as a 99.8% GUI user I always break out in a cold sweat when I start typing sudo something into a terminal session.

Are you saying all I need to do is enter a terminal command to convert some .mp3 podcasts into .M4A format, if so then I agree that is much more efficient. Snag is I don't know how to do that.

Using a gui is fine, there is no need for a cold sweat :-). There is a nice gui for FFmpeg called winFF that is actively discussed and supported on these forums that might help you out. As well there is a hugely popular multimedia thread:

Comprehensive Multimedia & Video Howto
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

that might be your best bet and this also discusses the installation of winFF. There are many ways to do things.

About the ogg player: I found an iRiver X20 a while back and this features native ogg playback, you might also have a look at the new Cowon players these seem to play everything :-).

If you are interested at some stage in working on the commandline FFmpeg the best way to start is here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

or here:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Lots of choices and I wish you all the best with whichever choice you make :-).

Andrew

---

### Post by SuperSonic4 on 2009-04-24
I'd recommend soundconverter over winFF as a frontend for pure audio conversion.

---

### Post by FakeOutdoorsman on 2009-04-24
I have an older Cowon iAudio G3 that I use to play ogg vorbis audio files.  It works fine, but I don't like the slow startup, the split-second fade in it applies to each song, and the supplied headphones are not very useful.  I do like that it acts as a mass storage device and you can just copy whatever you want to the player with no proprietary software, no synchronization, DRM limitations, or other annoyances dealing with transferring files.  I also like that it uses a single AA battery which is nice for me because I use rechargeables.

---

### Post by the.scarecrow on 2009-04-24
> **FakeOutdoorsman said:**
> I have an older Cowon iAudio G3 that I use to play ogg vorbis audio files.  It works fine, but I don't like the slow startup, the split-second fade in it applies to each song, and the supplied headphones are not very useful.  I do like that it acts as a mass storage device and you can just copy whatever you want to the player with no proprietary software, no synchronization, DRM limitations, or other annoyances dealing with transferring files.  I also like that it uses a single AA battery which is nice for me because I use rechargeables.

I did buy a Samsung TP-S2 MP3 player, it works with .ogg and MP3s no DRM and good headphones. For a very basic 2GB player it works extremely well and its fully compatible with Jaunty 8.10. However, given its simple nature it was expensive compared to higher featured MP3 only players. It charges on the USB with a non-replaceable battery so it probably has a life of about 5years.

I use it for Podcasts of all sorts of things. Has anyone listened to Dan Carlin? REALLY interesting and entertaining
[HTML]http://www.dancarlin.com/[/HTML] but I'm not sure I'm allowed to say things like this.

Thanks andrew.46 and SuperSonic4 I am going to checkout your suggestions and give em all a go. You never stop learning something new with Ubuntu.

---

### Post by JoshuaRL on 2009-04-24
> **the.scarecrow said:**
> but I'm not sure I'm allowed to say things like this.

Don't worry too much about this thread.  It's obvious that you didn't know and just wanted to let other users see what you thought was a good application.  That's why we informed you of what this application is, so you could see and make the right decision.  Continuing to learn is what Linux is all about.

---

### Post by bapoumba on 2009-04-25
Thanks to all the very good and informative answers :)
(We, as Staff, always end up saying "no" or "bad" left and right, and rarely take the opportunity to say "this turned out nicely").

---

### Post by the.scarecrow on 2009-04-25
This thread has not gone where I expected it would. Its my opinion that the real problem we all are facing is that a Toy/Game manufacturer chooses to use a restricted proprietary file format against Open Source or at least the ubiquitous MP3 that the world finds so convenient. Worse still is that Nintendo insist you accept a set of extreme terms and conditions if you want to enjoy the most important new features included on the DSi	(DsiWare).

Another example of the same problem is the British Broadcasting Corporation (BBC) adopting iPlayer to access their programs on the net, I don't want to be forced to use applications like this. I have complained to the BBC but their bland reassuring replies totally avoid the point.

Microsoft are often painted black in the Linux community whilst IBM come over as a pretty decent company. But I remember dealing with IBM before Microsoft existed and IBM almost ran the computing world keeping their customers in a state of constant fear should you somehow upset them whilst purchasing their products and services. It was IBM customers that invented the term FUD (Fear Uncertainty Doubt).

No, what goes wrong is when an organization gets too powerful, they can then become the “tail that wags the dog”, dictating what their customers must and must not do. Microsoft needs the competition its gets from Open Source and others to keep it (Microsoft) healthy and innovative. If Microsoft moved towards its own GNU, the shared innovations in software development would push forward computer development very quickly. I mean why on earth argue about the use of FAT32, NTFS and WS3? its like arguing over who owns the shape of the slot in your DVD player.

So back to Format Factory, why care about small details? They are probably Chinese so they are brilliant in their comprehension of English. Just, I like what they have done so now can they produce a Linux version please. If only they were all that Open Source had to worry about.

OK off the soap box. Just to point out I am retired and have no interests in any of the companies named in this thread.

---

### Post by drunkmatador on 2009-06-10
I just got a DSi and am having the same problem. Going to download Format Factory and give that a shot.. I finally got mplayer and faac to work but the .aac files didn't show up on my DSi. Then I renamed them to .m4a files and they show up now, but wont play.

---

### Post by mcframe on 2010-03-10
I had this prob bringing music to the DSi of my son. I solved it by creating this command, which converts all mp3 files within the given path to m4a files which the DSi is playing smoothly.

```
find /your/path/ -name '*.mp3' -exec sh -c 'ffmpeg -y -i "{}" -ab 128k "`basename "$0" .mp3`".m4a' {} \;
```

Hope it helps someone

Regards

---

### Post by frncz on 2010-11-11
soundconverter, as suggested above, works great for converting .mp3 to .m4a, the format needed for my kids' Nintendo DSI. It can do batch files and whole directories. I had used ffmpeg before, but only managed one song at a time

Mike

---


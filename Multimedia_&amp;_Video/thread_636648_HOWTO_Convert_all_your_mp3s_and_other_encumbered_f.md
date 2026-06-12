---
title: "HOWTO: Convert all your mp3s and other encumbered formats into superior OGGs easily!"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by Yfrwlf on 2007-12-10
This will allow you to convert your music archive (and videos too, but I haven't tried that yet) into the royalty-free, open source and superior OGG format.  No more installing the annoying restricted mp3 support codecs!  OGG is included by default and just works out of the box because [COLOR="Green"]it is not restricted or burdened by any patents or copyrights[/COLOR].  Your MP3s should be able to be converted into a smaller OGG file, too, so depending on your settings and if you convert correctly you can shrink the size of your entire music collection.  Keep in mind that when you purchase your next portable music player to get one which supports OGG, which there are several kinds that do.  Also, buy one that supports Linux or simply supports directly accessing the player like a memory stick, and doesn't require installation of some proprietary Windows application to access it.

If you first would like a true demonstration that OGG is better than MP3, if you have a wave file around, amaze yourself and your friends by comparing MP3 to OGG and showing them that the smaller OGG sounds just as good!  If you don't have a wave file, converting an MP3 into a bit smaller of an OGG is still a good example as you will not be able to hear a difference between them.  Keep in mind if you go too small by converting it into too low of a bitrate, any codec will sound bad at that point.

[COLOR="Red"]Converting from one lossy codec to another always results in some additional data loss, but this is minimal for me and I cannot hear a difference in part because OGG is very good, and because I use fairly high default quality settings in this example.  Ideally if you can convert from the original source instead of from MP3 or other lossy codec formats to prevent more loss, you may wish to do so.  Also, I use a fixed bit rate in this example, so always test that you are happy with your results and that everything went smoothly before deleting your original files![/COLOR]

[COLOR="Red"]The following problem will be fixed in soundKonverter version 0.3.7.  soundKonverter will skip any files that have ANY UPPERCASE LETTERS IN THE EXTENSION.  Sorry for yelling. ;)  You can use find via the command line or something like Find Files in the Dolphin tools to locate any MP3 or Mp3 or mP3 files so that you can rename them to mp3, or even faster, simply drag and drop all these files into soundKonverter to take care of them, because this bug only occurs when adding folders in soundKonverter and does not apply to direct files.  I have already filed a bug report about this problem.[/COLOR]

[COLOR="Blue"]Step 1:[/COLOR]  Open Add/Remove.

[COLOR="Blue"]Step 2:[/COLOR] Choose show all available applications in the top right corner.

[COLOR="Blue"]Step 3:[/COLOR] Look up all the formats you wish to convert from, like mp3, and mark them.  Some of the following applications may not be necessary to install, but I'm too lazy to find out which ones are truly needed, so just do them all!  For mp3, check mark the "GStreamer extra plugins" package that says it contains codecs to play mp3, sid, mpeg1, etc.  Check mark the "Ubuntu restricted extras" package.  Check mark "Mplayer".  Look up "convert" or whatever and check mark "soundKonverter".  If you'd like what is in my opinion the best audio player, you can also check mark "Amarok". ;)  Click install.  If you can't find certain codecs or packages for certain file types in Add/Remove Applications, open up Synaptic Package Manager and look there.  There is also a program called "Sound Converter" that is GTK so will be a little faster to load if you're using Gnome, but I have not tried out this program yet.

[COLOR="Blue"]Step 4:[/COLOR] Start soundKonverter from Applications > Sound & Video.

[COLOR="Blue"]Step 5:[/COLOR] Go to Settings > Configure soundKonverter and click on Backends.  Make sure there are decoders for the files you want to convert from, and that the OGG encoder is there too.  If it's not, search for things to install for decoding and encoding the things you want and rerun the program to see if it found them.  I use mplayer for the decoder backend, which is why I had you install it in the previous step.

[COLOR="Blue"]Step 6:[/COLOR] Back in soundKonverter, select Source Directory for your output if you would like to keep your folder structure, otherwise change it to something different if you would like to create a whole new folder system for your music.

[COLOR="Blue"]Step 7:[/COLOR] Adjust the output format to ogg, and select a quality.  I use "high".

[COLOR="Blue"]Step 8:[/COLOR] Drag and drop a file into the window and select start.  The old file will **not** be deleted, you will only delete files after you are comfortable with their new counterparts.  Play this file after you are finished and compare it to the original.  If you chose something other than Source Directory, it will tell you where it is saving it in the Output column as it is encoding the file.

[COLOR="Blue"]Step 9:[/COLOR] As soon as you are comfortable with your quality settings and don't mind having the same quality setting for all your music files, select Add Folder in the bottom left of soundKonverter and add your entire music folder, and then select start.  If you would like to have the quality setting lower for low-quality mp3s so that they shrink in size instead of increasing, add those separately.  The same goes for any collections of ultra-high-quality mp3s, you may wish to encode those at a higher bitrate, but you probably don't need to select the *same* bitrate.  [COLOR="Red"]Again, always test first and make sure you like it before you delete the originals![/COLOR]  Keep in mind that there is no option (that I've found) to delete while encoding, so you need to have enough space, or do smaller sections at a time.  You can use a program like KFind (accessible through the Dolphin file manager) to find all your mp3s or other file types and delete them after you are finished.


[COLOR="DarkOrchid"]NOTES:[/COLOR]  soundKonverter can convert videos too, just look at all the file formats it supports converting to and from!  Play around with this great utility to convert all your annoying proprietary audio and movie codecs into free ones!

Yes, there are ways to do all this through the command line and would be much quicker since the GUI is always slower, and if someone would like to make a simple command line tutorial to do all this, I will provide a link to it, but this tutorial is intended for the command line impaired.

Yes, I know that you can't "upconvert" in quality, and yes I know that converting from one lossy format to another can be bad sometimes, but in this case I'm completely satisfied with the results.  The decoded and then re-encoded music I get from this are indistinguishable for me from the original.  If you are an audiophile and notice a difference, set the quality settings higher.

If you are converting all files to a set bitrate like you are in this tutorial, keep in mind that very high quality bitrate files like 190 and 256 may be downgraded in quality somewhat if you convert them to 144 kbit OGGs by using the "high" setting.  I find "high" to be a happy medium, but in reality I believe that you only need to use the same or slightly lower bitrate for each song you convert into OGG from mp3.  This would be about 33% lower if it were from a wave file, since that is the approximate bitrate compression difference I think between mp3 and ogg, but you need to use higher I think since it's mp3 to ogg and you want to prevent lossless-to-lossless format data loss as much as possible.  Anyone care to clarify this for me?  In this case, make sure that if you have any "ultra-high fidelity" music collections that you increase the quality for them if you wish to retain the quality.  For lower quality sound files, keep in mind that using a high quality setting may be unnecessary.  Again though, I find "high" or "medium" to be a perfectly acceptable setting.

---

### Post by eye208 on 2007-12-10
> **Yfrwlf said:**
> I believe that you only need to use the same or slightly lower bitrate for each song you convert into OGG from mp3.
Converting from MP3 to Vorbis makes no sense unless you're going for very low bitrates and do not care about quality. Because no matter what you do, the Vorbis file will always sound worse than the MP3 and be unusable with most portable players. So what's the point?

---

### Post by NovaAesa on 2007-12-10
Even if you transcode an mp3 from a high bitrate to a ogg vorbis file of a lower bitrate, it CANNOT sound as good as the original. It's much better to get out your CD collection and re-reip everything into ogg vorbis.

EDIT: Or alternatively if have FLAC files from your CDs somewhere you can transcode from these if you don't want to have to re-rip everything. FLAC is a lossless format, so when you go from FLAC to ogg vorbis, its just like ripping a CD to ogg vorbis but much faster.

---

### Post by Yfrwlf on 2007-12-11
> **eye208 said:**
> Converting from MP3 to Vorbis makes no sense unless you're going for very low bitrates and do not care about quality. Because no matter what you do, the Vorbis file will always sound worse than the MP3 and be unusable with most portable players. So what's the point?

This is for anyone wanting to do this, but your opinions are welcome of course. ;)  Using this method you will get files that I cannot hear a difference in quality with, and if you can then you can increase the quality, but if it gets to the point where you can't hear any differences and it will not make the file smaller, then it definitely all depends on your preference for "lock-in" and proprietary formats.  The MP3 format is a restricted format and OGG is superior, so OGG should be promoted and MP3 should be discontinued, and as for your comments about lossy-to-lossy conversion read the following reply...

> **NovaAesa said:**
> Even if you transcode an mp3 from a high bitrate to a ogg vorbis file of a lower bitrate, it CANNOT sound as good as the original. It's much better to get out your CD collection and re-reip everything into ogg vorbis.

EDIT: Or alternatively if have FLAC files from your CDs somewhere you can transcode from these if you don't want to have to re-rip everything. FLAC is a lossless format, so when you go from FLAC to ogg vorbis, its just like ripping a CD to ogg vorbis but much faster.

Re-ripping should definitely be done when you can, *unless* you can't tell a difference.  Try it, and find out if you can actually tell, because I can't.  Like I said in the notes for this process, I already know that converting from one lossy to another is "bad", but how bad it is depends on your ears and your preference for unrestricted formats, and like you said if you don't want any loss whatsoever, then use FLAC and store your music that way, I just hope you're OK with the file space it takes up. ;)

---

### Post by NovaAesa on 2007-12-14
> **Yfrwlf said:**
> 
Re-ripping should definitely be done when you can, *unless* you can't tell a difference.  Try it, and find out if you can actually tell, because I can't.  Like I said in the notes for this process, I already know that converting from one lossy to another is "bad", but how bad it is depends on your ears and your preference for unrestricted formats, and like you said if you don't want any loss whatsoever, then use FLAC and store your music that way, I just hope you're OK with the file space it takes up. ;)

Yes, I totally agree with you, it all depends if you can actually hear a difference or not. When I rip from a CD, I encode in ogg vorbis with the -q5 option because I can't tell the difference between -q5 and -q6 with my computer speakers. However, when I put ogg vorbis files onto my mp3 player I use -q1 because I can't tell the difference between -q1 and -q0.

I guess when I comes down to it, if you really can't tell the difference then there's no problem with reencoding lossless to lossless. This will depend on your hearing ability, your speakers, sound card etc. But bear in mind that if you ever upgrade your hardware you may notice the difference then :)

---

### Post by TGArcher on 2007-12-15
> **eye208 said:**
> Converting from MP3 to Vorbis makes no sense unless you're going for very low bitrates and do not care about quality. Because no matter what you do, the Vorbis file will always sound worse than the MP3 and be unusable with most portable players. So what's the point?

HA AH HA HA HA HA HA HA HA!!!!!!!!!! If I told that to some people I know, they would go INSANE. 1) ogg vorbis generally have higher compression and BETTER sound quality than mp3. Vorbis IS a supereor format. 2) I have a player that plays ogg. Get a Sansa e200 series and throw Rockbox on it and it turns from a player to somthing of GOD! lol but really, take the same song on a CD and rip it into 192 ogg and 192 mp3 you will find that mp3 is bigger and sounds worse.

---

### Post by Goemon4 on 2007-12-15
thanks, tho common knowledge, i could never get soundKonverter to work, but this helped. Now I'm mp3-free!! The sound is pretty much the same quality, but idc, ima start re-ripping my cd's as FLAC/OGG anyways so ill just up the quality then, still ty tho

but imo, if you allow it to convert it to the highest possible bit-rate, it usually remains the same quality, if you limit the ogg to a certain quality, and if the mp3 is higher, OBVIOUSLY quality will go down. But if  you go for the highest possible, it usually converts them all to the mp3 equivalent. Idk tho, I'm not a genius when it comes to audio files, but from experience, when my Between The Buried and Me "Colors" album, which was at 320kbps (mp3), was converted to the highest possible ogg, sounded just like the mp3. It all depends on what you allow it to convert to, if you limit it, you will lower quality, but OGG is defiantly capable of going to higher quality than mp3 from experience. FLAC is a #1 tho :D

---

### Post by Yfrwlf on 2007-12-17
> **TGArcher said:**
> HA AH HA HA HA HA HA HA HA!!!!!!!!!! If I told that to some people I know, they would go INSANE. 1) ogg vorbis generally have higher compression and BETTER sound quality than mp3. Vorbis IS a supereor format. 2) I have a player that plays ogg. Get a Sansa e200 series and throw Rockbox on it and it turns from a player to somthing of GOD! lol but really, take the same song on a CD and rip it into 192 ogg and 192 mp3 you will find that mp3 is bigger and sounds worse.

You're right about the players even if they aren't as common as MP3 players, but again, he's right about the conversion from one lossless codec to another.  There is no arguing that OGG is superior really, you're right, but going from lossless to lossless accumulates the total net loss of each codec into one sound file.  In reality however, I cannot hear a difference, so the loss that is occurring here seems to be very minimal.  It completely depends on what is being cut out when the codec compresses the music file.  If the removed information coincides with each other between both codecs, then the second codec would not lower the quality any further than that of the first.

> **Goemon4 said:**
> thanks, tho common knowledge, i could never get soundKonverter to work, but this helped. Now I'm mp3-free!! The sound is pretty much the same quality, but idc, ima start re-ripping my cd's as FLAC/OGG anyways so ill just up the quality then, still ty tho

but imo, if you allow it to convert it to the highest possible bit-rate, it usually remains the same quality, if you limit the ogg to a certain quality, and if the mp3 is higher, OBVIOUSLY quality will go down. But if  you go for the highest possible, it usually converts them all to the mp3 equivalent. Idk tho, I'm not a genius when it comes to audio files, but from experience, when my Between The Buried and Me "Colors" album, which was at 320kbps (mp3), was converted to the highest possible ogg, sounded just like the mp3. It all depends on what you allow it to convert to, if you limit it, you will lower quality, but OGG is defiantly capable of going to higher quality than mp3 from experience. FLAC is a #1 tho :D

It's really a no-brainer of a HowTo since the answer is "soundKonverter" and it's just a simple GUI, but of course command line methods are cool too and could be more powerful of course like always.  Regardless, I'm glad you possibly found it at least a little helpful. ^^  Yes, OGG is superior vs. MP3.  I'm not sure about AAC, but AAC is also restricted by legal crap, so OGG all the way until a new, unrestricted and better format emerges. ;)

---

### Post by Tarmael on 2007-12-17
> **TGArcher said:**
> HA AH HA HA HA HA HA HA HA!!!!!!!!!! If I told that to some people I know, they would go INSANE. 1) ogg vorbis generally have higher compression and BETTER sound quality than mp3. Vorbis IS a supereor format. 2) I have a player that plays ogg. Get a Sansa e200 series and throw Rockbox on it and it turns from a player to somthing of GOD! lol but really, take the same song on a CD and rip it into 192 ogg and 192 mp3 you will find that mp3 is bigger and sounds worse.

Vorbis may be superior but I think what eye208 was trying to point out is there is a loss of quality when going from one lossy format to another, you DO lose quality no matter how small it is.

The overall meaning of this thread is, if it doesn't bother you to rip one lossy format into another superior one then go for it, else rip new CDs to either FLAC or OGG straight from the start.

It is rather sad that MP3 is the standard media format for most portable media players these days, because OGG is superior.

I don't feel eye208 was saying that MP3 is superior, just that it's standardized and there is no point encoding lossy to lossy.

Cheers,
Basil.

---

### Post by ubunter1 on 2007-12-17
how about converting flac or ogg to mp3?, reason being ive a mp3 player that cant take those files without a update from the players site,which i cant do in linux. will this program do it?.thanks.

---

### Post by Yfrwlf on 2007-12-18
> **ubunter1 said:**
> how about converting flac or ogg to mp3?, reason being ive a mp3 player that cant take those files without a update from the players site,which i cant do in linux. will this program do it?.thanks.

I would highly recommend that you try to use Wine to run your music player's update software, or find a computer with Windows that you can use to update your mp3 player so that you won't have to convert from a superior format to a worse one.  I think that would save you the most trouble in the long run by far.  But if you want to convert to MP3 then yes you should be able to use soundKonverter to do so, you just need to install an MP3 encoder in order to do it.  To do so, from the repositories install lame or ffmpeg.  Preferrably lame as soundKonverter says it has "full" support with it.  If it's not in Add/Remove then check in Synaptic Package Manager.  After restarting soundKonverter (or allowing it to rescan for encoders, however it does it), you should see lame show up for mp3 encoding.  Otherwise, if you can't get that installed, install ffmpeg.

---

### Post by eye208 on 2007-12-18
> **Yfrwlf said:**
> The MP3 format is a restricted format
It depends on your location. For example, software patents are not enforceable in Europe. If you own a hardware MP3 player, you already paid to use the format anyway. On the other hand, the legal status of Vorbis is unknown. Remember the time when JPEG was considered a free format.

Software patents are a mine field. There is no way to prove that a piece of code is not covered by patents, unless the code is very old.

By the way, if you need to convert from MP3 to Vorbis because you don't own the original uncompressed recordings, you probably infringe someone's copyright already. Why care about patents then? ;)

---

### Post by mozetti on 2007-12-18
One of the reasons you stated for doing this is so you don't have to install the packages for "encumbered" formats like mp3. But, the first step in doing this requires you to install the mp3 packages anyway. So, if you've already installed the packages for mp3s so you can decode them, whammo! - you can play them now. Why go through the extra trouble of actually re-encoding?

As far as converting flac to mp3 -- check out my thread here: [http://ubuntuforums.org/showthread.php?t=642861](http://ubuntuforums.org/showthread.php?t=642861)

---

### Post by Goemon4 on 2007-12-18
> **Yfrwlf said:**
> 
It's really a no-brainer of a HowTo since the answer is "soundKonverter" and it's just a simple GUI, but of course command line methods are cool too and could be more powerful of course like always.  Regardless, I'm glad you possibly found it at least a little helpful. ^^  Yes, OGG is superior vs. MP3.  I'm not sure about AAC, but AAC is also restricted by legal crap, so OGG all the way until a new, unrestricted and better format emerges. ;)

Yeah, i got my 12 gig mp3 collection down to 7.8 gigs of ogg. But i still find FLAC the best, to bad its so damned big.  I never liked AAC, i found it incompatible with alot of media players (on the computer and portable), i guess cause it is a restricted format, but man does it sound nice :D 

@ eye208 - Ha, yeah you got a point there, but if you only have a downloaded version it isnt like convertign it will improve quality much, but i guess a main reason to convert to ogg is to save space. Though if  you rip a cd to ogg, this is worth it, cause IIRC soundKonverter (or soundconverter) can rip cd's to ogg to, so either way, i guess its just about which format you prefer. 


@ mozetti - well yeah, but afterwards you can just un-install it if you hate the idea of having anything not-free. I guess this is just to set it up so you dont need it.

---

### Post by Yfrwlf on 2007-12-19
> **eye208 said:**
> It depends on your location. For example, software patents are not enforceable in Europe. If you own a hardware MP3 player, you already paid to use the format anyway. On the other hand, the legal status of Vorbis is unknown. Remember the time when JPEG was considered a free format.

Software patents are a mine field. There is no way to prove that a piece of code is not covered by patents, unless the code is very old.

By the way, if you need to convert from MP3 to Vorbis because you don't own the original uncompressed recordings, you probably infringe someone's copyright already. Why care about patents then? ;)

Legalities with copyrights and patents are a pain, and you're right that it depends where you live as most countries aside from the US don't have crazy stupid restrictions, things are really screwed up here and it's all due to monopolies ruling the lawbooks and selfishness in general, but that's just my opinion.  Feel lucky if you live in a country that doesn't have dreaded software patents at the very least.  The law is a joke here, it's just leverage for monopolies to smite competition is all it's used for.  At least we're not to the point where the DRM police break into your home and arrest you for listening to or watching something in a way not explicitly authorized by the creator, 1984 isn't quite here yet.  /rant

But, you can still support the formats that are currently free and ignore the FUD until something has been firmly decided.  In law, nothing ever can be though, but you know what I mean.  Right now there can be as much FUD as competition would like there to be, so you shouldn't listen to it, it's not like anyone has the legal authority to go after OGG users/developers/players/encoders here in the US, not yet any way.

As for your last comment, there are several ways in which you'll run into MP3s, regardless of if you "bought" them or not, and you should have the right to convert them to what format you want to listen to them in.  A game may have come with MP3 music, or you may have "bought" an mp3 online.  Regardless, here in the U.S., moving to codecs that aren't "encumbered" can save developers and users headaches caused by the laws here (though mostly developers), and you should support your developers. ;)

> **mozetti said:**
> One of the reasons you stated for doing this is so you don't have to install the packages for "encumbered" formats like mp3. But, the first step in doing this requires you to install the mp3 packages anyway. So, if you've already installed the packages for mp3s so you can decode them, whammo! - you can play them now. Why go through the extra trouble of actually re-encoding?

As far as converting flac to mp3 -- check out my thread here: [http://ubuntuforums.org/showthread.php?t=642861](http://ubuntuforums.org/showthread.php?t=642861)

Because you can remove them afterward, and you no longer will have to do this in the future, nor on any other computers or devices you wish to use to listen to them, nor will your friends have to if you let them listen to them.  If you don't wish to convert to an unencumbered format though, then don't, it's obviously up to you.  I've listed a few reasons to convert to OGG, but if none of them sound appealing to you, don't do it.

> **Goemon4 said:**
> Yeah, i got my 12 gig mp3 collection down to 7.8 gigs of ogg. But i still find FLAC the best, to bad its so damned big.  I never liked AAC, i found it incompatible with alot of media players (on the computer and portable), i guess cause it is a restricted format, but man does it sound nice :D

Nice, I'm still waiting for the end results after compressing my archive which is around 40 GB.  I'm expecting to save perhaps around 10 GB, but we'll see. :)

---


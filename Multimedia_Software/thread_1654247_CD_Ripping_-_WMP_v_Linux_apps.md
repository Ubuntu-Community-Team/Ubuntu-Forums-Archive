---
title: "CD Ripping - WMP v Linux apps"
date: 2010-12-28
forum: Multimedia Software
---

### Post by Mylorharbour on 2010-12-28
I had a new portable MP3 player for Christmas. Downloaded some music files to it but only some of them show up on the player, the ones ripped by WMP. Anything ripped using Sound Juicer failed.

It transpires Sound Juicer cannot write the required ID3v2.23 tags. OK so I can use EasyTag to write those but that's a 2 stage process. Now I can see them but there's no album art so I search the net for the required art, import it into Gimp, resize it, save it then bring it into EasyTag for each individual file.

So, what is a one click function in WMP takes an eternity in Ubuntu. There must be a better way. Can anyone point me in the right direction?

*N.B. I sometimes need to use Sound Juicer as WMP often fails to tag UK compilations correctly. Now if WMP used MusicBrainz life would be so much easier. Linux life is so frustrating at times.*

---

### Post by Joe of loath on 2010-12-28
Have you tried ripping using rhythmbox/banshee?

---

### Post by cascade9 on 2010-12-28
Sound Juicer isnt the only ripper that works with linux. I havent tried getting ID3 v2.23 tags in my rips, as I dont rip straight to mp3 (I use flac), but I'm sure that one of them will write those tags. 

You can (or at least used to) be able to easily get album art with album art cover downloader- 

[http://www.unrealvoodoo.org/hiteck/projects/albumart/](http://www.unrealvoodoo.org/hiteck/projects/albumart/)

---

### Post by samfuzz on 2010-12-28
in "gnome-audio-profiles-properties"

set id3mux instead of id3v2mux in your gstreamer mp3 profile,
this will write id2v2.3 tag instead of id2v2.4 tag

and for cover art rhythmbox, banshee ... retrieve album art

and lot of more :
[http://gnome-look.org/content/show.php/CoverChooser?content=117330](http://gnome-look.org/content/show.php/CoverChooser?content=117330)

picard with plug ins 

........

---

### Post by pricetech on 2010-12-28
I haven't had the issues you describe, but I will say the only thing I find frustrating is the lack of support for Linux from other parties.

It all works for me.

---

### Post by VanillaMozilla on 2010-12-28
Sound Juicer (Audio CD Extractor) has a bug that may not yet be fixed in the current distribution.  I have had absolutely no problems with K3b, and I recommend it.

Now for your penance, please edit the offensive title of your thread.  ;)


EDIT:  Fixed in version 2.31.6, which is distributed with Maverick.  Not fixed in Lucid as of yesterday.

---

### Post by trinitydan on 2010-12-28
I have never had any problems with the super intuitive software for ripping CDs with Ubuntu.  I put in the disc, select the option to add the tracks to my libray, it finds the album art online, and voila!  MP3's.  Granted I had to switch from the open source .OGG format to the more supported but proprietary .mp3 codecs, but can Linux be blamed for this?  By default WMP makes .wma files right?  That's annoying. :P

+1 for changing the inaccurate thread title.

---

### Post by tuppe666 on 2010-12-28
LOL WMP is garbage. That said NO Media Player will ever replace a standalone music tagger.

No for the advice and this is quite serious "ID3v2.23 tags" thats a joke. At least I hope you have a guarantee ready. Its a OBSOLETE standard, and has been for years. I suspect your player will support at least 2.3 if not 2.4 tags otherwise its "not fit for purpose"

EasyTag I haven't used for years. Its not in development. I would probably use MP3 Diags(2.3) it will teach you more than you want to know about your MP3s and FIX them. Although Puddletag(2.4) is quite a fun application.

Seriously not sure why you are editing pictures in Gimp!

---

### Post by Mylorharbour on 2010-12-28
> **Joe of loath said:**
> Have you tried ripping using rhythmbox/banshee?I've tried Rhythmbox v0.12.8 on Lucid so far Joe but I don't get ID3v2.3 tags, just ID3v2.4 and no album art. I'll try Banshee later but some of the other guys above have given me something to work on.

> **samfuzz said:**
> in "gnome-audio-profiles-properties"

set id3mux instead of id3v2mux in your gstreamer mp3 profile,
this will write id2v2.3 tag instead of id2v2.4 tag

and for cover art rhythmbox, banshee ... retrieve album artsamfuzz, How do I open "gnome-audio-profiles-properties"? I'm not quite a beginner but that's got me stumped. I've tried retrieving art for a British album in Rhythmbox but I just get a searching whirlygig.

> **pricetech said:**
> 
It all works for me.Could you expand on that pricetech?

> **VanillaMozilla said:**
> ...I have had absolutely no problems with K3b, and I recommend it.....Now for your penance, please edit the offensive title of your thread.  ;) I'll give K3b a try along with Banshee. I don't think the title is actually offensive but I'll be happy to change it when it proves incorrect. So far it appears it may not be possible to do a one-click rip in Ubuntu and produce the desired outcome.

> **trinitydan said:**
> ...I put in the disc, select the option to add the tracks to my libray, it finds the album art online, and voila!  MP3's.  ...By default WMP makes .wma files right?Are you using Sound Juicer trinitydan? Do you get ID3v2.3 tags and album art? You are right about the default .wma files but that's easy to change.

> **tuppe666 said:**
> LOL WMP is garbage.
No for the advice and this is quite serious "ID3v2.23 tags" thats a joke. At least I hope you have a guarantee ready. Its a OBSOLETE standard, and has been for years. I suspect your player will support at least 2.3 if not 2.4 tags otherwise its "not fit for purpose"
I would probably use MP3 Diags(2.3) it will teach you more than you want to know about your MP3s and FIX them.

Seriously not sure why you are editing pictures in Gimp!There's a lot wrong with WMP tuppe but it does rip to mp3, with ID3v2.3 tags and album art which is all I'm after.

As for ID3v2.3 being obsolete see here [http://www.id3.org/]("http://www.id3.org/"). Para 3 states:
[I]While there are legacy and future standards for ID3 tags, the most popular version implemented today is ID3 version 2.3. A follow on version, 2.4, is documented on this website but has not achieved popular status due to some disagreements on some of the revisions and the tremendous inertia present in the software and hardware marketplace. 
[/I]
My player is the latest Sansa Fuze+.

---

### Post by trinitydan on 2010-12-29
Maybe if you edit the title people will come back and help you?  :p  It gets tiresome trying to talk people into using something they don't like.  Yes I use Sound Juicer.  I am not sure what type of tags it uses.  It never has been an issue for me.  The tags are recognized by my iPods and iTunes if that helps determine at all if they will work for you.  As I was mentioning, you will have to do some configuring of SoundJuicer to get the correct .MP3 output.

I do think there is going to be a solution to your problem.  It sounds like you made the assumption it wasn't going to work and started doing things the hard way and frustrated yourself.  I am not trying to give you a hard time.  I hope you can get Ubuntu to do everything you need it to do.  However the title of this thread is, if not offensive, at the very least inflammatory.  Most people here would not agree with your sentiment whatsoever.  You state that the open source alternative is inferior and challenge us to prove you wrong.  You would do better I think just to explain your problems and ask for help to get your desired results.

---

### Post by Mylorharbour on 2010-12-29
Ok, I've asked the mods to change the title.

To précis what I'm trying to do....

My Sansa Fuze+ mp3 player recognises mp3's that are ripped by WMP and also displays the associated album art. Anything ripped so far by Lucid apps fails to show or shows as 'unknown artist'. From searching the Sansa forums it appears the ripped mp3's need ID3v2.3 tags.

Rhythmbox and Sound Juicer, out of the box, apply ID3v2.4 tags and don't appear able to download album art for the British CD I'm testing with, (Cliff Richard - The Whole Story).

K3b requires a codec apparently to rip to mp3. I'm struggling to get this working.

Banshee rips by default to Ogg Vorbis. I haven't yet found a way to rip to mp3.

I prefer to do everything I can in Ubuntu. 

Thanks for the help so far guys. Apologies if I've upset some of you. It wasn't intentional.

---

### Post by trinitydan on 2010-12-29
I didn't mean to get on your case.  I meant all I said in good spirits, I really do hope we can solve this for you!  The only ripping software I am familiar with is Sound Juicer. It is difficult for me to weed through the results of searches for your desired tag format, but I suspect Sound Juicer would do what you need.  I will continue to look into it.

---

### Post by trinitydan on 2010-12-29
Given your special tag format need, I am going to have to recommend you go with RubyRipper.  It does support the tag format you need.  You can find how to install it here:

[https://help.ubuntu.com/community/CDRipping#RubyRipper](https://help.ubuntu.com/community/CDRipping#RubyRipper)

Just post up when you get stuck and someone will help you out!  

You might want to have a look at [this]("http://linux.oneandoneis2.org/LNW.htm") at some point too when you get a chance.

---

### Post by tuppe666 on 2010-12-30
> **DanielTodaro said:**
> Although most variants of Linux have greatly improved the ease of use, Windows is still much easier to use by new computer users.Linux has a wide range of available programs, utilities and games. However, Windows has much larger selection of software available.

Not true. If your argument had been better quality commercial programs...Maybe, or Proprietary Games...Maybe. I notice you are fairly new so perhaps you should be a little more constructive with your posts.

---

### Post by inobe on 2010-12-30
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

there are pictures too.

---

### Post by tuppe666 on 2010-12-30
> **Mylorharbour said:**
> Ok, I've asked the mods to change the title.

To précis what I'm trying to do....

My Sansa Fuze+ mp3 player recognises mp3's that are ripped by WMP and also displays the associated album art. Anything ripped so far by Lucid apps fails to show or shows as 'unknown artist'. From searching the Sansa forums it appears the ripped mp3's need ID3v2.3 tags.

Rhythmbox and Sound Juicer, out of the box, apply ID3v2.4 tags and don't appear able to download album art for the British CD I'm testing with, (Cliff Richard - The Whole Story).

K3b requires a codec apparently to rip to mp3. I'm struggling to get this working.

Banshee rips by default to Ogg Vorbis. I haven't yet found a way to rip to mp3.

I prefer to do everything I can in Ubuntu. 

Thanks for the help so far guys. Apologies if I've upset some of you. It wasn't intentional.

Turn off "write metadata" to files. I've read the same forums. You need "MP3 Gain" it will clean and convert all your tags in one press of the button for all you tunes to 2.3.

---

### Post by Mylorharbour on 2010-12-30
Trinitydan,
Thanks for that. Yes RubyRipper does write the correct tags but it takes an awfully long time. Something like 1.5hrs per cd so I reckon I must have some settings wrong as it seemed to do an awful lot of checking. I also can't ask it to write to my music folder nor will it download album art.

Still, it's progress. Between that and MP3 Diags at least I'm able to do what I'm after now.

---

### Post by trinitydan on 2010-12-30
You're welcome! It's progress, but we're not there yet.  That is an unacceptable amount of time.  This isn't solved until we get you ripping cd's with ease and speed equal to or better than WMP! :D  I am currently installing RubyRipper as I have never used it and I am going to try to look into other ripping programs that might also be able to support your format.  Hopefully someone else will offer some more insight as well.  It seems like tuppe666 knows what they are talking about, so in the meantime if you want you could try to follow their suggestion as well.

---

### Post by Mylorharbour on 2010-12-30
> **tuppe666 said:**
> Turn off "write metadata" to files. I've read the same forums. You need "MP3 Gain" it will clean and convert all your tags in one press of the button for all you tunes to 2.3.Do you mean MP3 Diags? I've been playing with that and am quite impressed. I can also find a use for MP3 Gain though, thanks.

---

### Post by trinitydan on 2010-12-31
So I was looking into increasing speed using RubyRipper, and apparently you can't!?  I guess it's because of the developers commitment to quality.  Fast ripping is not an option.  That's not the level of freedom I like to enjoy with my software.  :(  

I am still looking for solutions in my spare time.  For now you might want to try out [Kid3]("http://kid3.sourceforge.net/").  I installed it on my computer and it has a very nice fairly easy to use interface for converting tag formats.  Here's the [10.04 .deb package]("http://sourceforge.net/projects/kid3/files/kid3/1.5/kid3_1.5-0lucid_i386.deb/download").

---

### Post by cascade9 on 2010-12-31
> **trinitydan said:**
> So I was looking into increasing speed using RubyRipper, and apparently you can't!?  I guess it's because of the developers commitment to quality.  Fast ripping is not an option.  That's not the level of freedom I like to enjoy with my software.  :(  

I normally HATE this response, but.....you arent forced to use rubyripper. 

Rubyripper is very similar to EAC,and meant to replicate the secure ripping that EAC does. Its just a frontend for cdparanoia, if rubyripper doesnt suit I'm sure that there is a different CDparanoia frontend that will do what you want.

---

### Post by mc4man on 2010-12-31
> So I was looking into increasing speed using RubyRipper, and apparently you can't!? I guess it's because of the developers commitment to quality. Fast ripping ingis not an option. 

The current 'speed' issues with rubyripper are due to the default versions of ruby, ruby-gtk2 used by ubuntu (and many other distros), which causes a large delay between tracks.

This can be resolved by using ruby 1.9.1 or 1.9.2 and a newer ruby-gtk2, though a little work. (made easier by a recent ruby1.9.2 ppa

An simplier solution for some is to setup thru the gui and then run the rip from  a terminal using one of these, depends on version of rr in use 
rrip_cli -a
or
rrip_cli -d

abcde (cli only) also works quite well, can use either cdparanoia or cdda2wav, there are some threads around on how to use and or setup

---

### Post by cascade9 on 2010-12-31
I was thinking that trinitydan was talking about 'match all chunks', minimum settings of 2. No single pass rips.

---

### Post by mc4man on 2010-12-31
> I was thinking that trinitydan was talking about..
Possibly but all lucid, mav. or natty users of the gui will find it takes more time to go from 1 track to the next then it takes to rip/encode that track. There is no 'fix' other than to use what I've mentioned. (the cli is unaffected, the gui works fine other than the actual ripping.

[http://code.google.com/p/rubyripper/issues/detail?id=348&colspec=ID%20Type%20Status%20Summary%20Stars%20Opened%20Modified](http://code.google.com/p/rubyripper/issues/detail?id=348&colspec=ID%20Type%20Status%20Summary%20Stars%20Opened%20Modified)

(it only takes about 5 min to set up ruby1.9.X and build a new ruby-gtk2, install RR, ect. but the 'setup in gui, rip in cli' is quicker to describe

---

### Post by trinitydan on 2010-12-31
> **trinitydan said:**
>   That's not the level of freedom I like to enjoy with my software.  :(  
> **cascade9 said:**
> I normally HATE this response, but.....you arent forced to use rubyripper. 
> **trinitydan said:**
> 
I am still looking for solutions in my spare time.
I understand that I am not forced to use RubyRipper, and I am probably  not going to, but that is kind of beside the point as I am just trying  to help out the original poster.  By "still looking for solutions", I  meant I am still looking for an alternative software program to meet the  OPs needs.  I have no need whatsoever for a ripper that outputs ID3v2.3 tags.

Edit:  I do see what you mean though, in this instance in particular we are not forced to use RubyRipper as it looks like there are a variety of options to get our desired outcome.  I should have reflected on your post further before replying.

> **cascade9 said:**
> I was thinking that trinitydan was talking about 'match all chunks', minimum settings of 2. No single pass rips.
That was what I was referring to, but it is possible that I was mistaken about what was making the rips unacceptably slow.  How long does it take to rip a cd from the command line with the options described?

---

### Post by mc4man on 2010-12-31
> How long does it take to rip a cd
Well that would depend on disc condition, the drive, desktop or laptop.

Using a disc in decent condition, a good desktop drive, a 50 min cd (11 tracks) took 10.5 min.'s w/ 2 pass, full paranoia 
(that was with the gui/ruby1.9.2, the cli would be the same

---

### Post by trinitydan on 2010-12-31
> **samfuzz said:**
> in "gnome-audio-profiles-properties"

set id3mux instead of id3v2mux in your gstreamer mp3 profile,
this will write id2v2.3 tag instead of id2v2.4 tag


Maybe the simplest solution is the best?

I tried changing the settings in Sound Juicer by editing the CD Quality MP3 profile as specified by samfuzz.  The rip speed is still what I would consider "normal" and the ID tags are recongnized by my iPod.  Hopefully this solution will work for the OP.

---

### Post by trinitydan on 2010-12-31
> **mc4man said:**
> Well that would depend on disc condition, the drive, desktop or laptop.

Using a disc in decent condition, a good desktop drive, a 50 min cd (11 tracks) took 10.5 min.'s w/ 2 pass, full paranoia 
(that was with the gui/ruby1.9.2, the cli would be the same

OK, now that's reasonable.  I could see a person wanting to use RubyRipper in that case to get the highest quality rips.  That hangup between tracks must be the main problem.

---

### Post by mc4man on 2010-12-31
> That hangup between tracks must be the main problem
Most definitely, the time from the end of the 2nd pass to starting next track, (when creating the midsum) should only be about 1 -1.5 seconds.

I generally use abcde which is highly configurable thru a .abcde.conf, usually placed in home folder

---

### Post by Mylorharbour on 2010-12-31
> **mc4man said:**
> The current 'speed' issues with rubyripper are due to the default versions of ruby, ruby-gtk2 used by ubuntu (and many other distros), which causes a large delay between tracks.

This can be resolved by using ruby 1.9.1 or 1.9.2 and a newer ruby-gtk2, though a little work. (made easier by a recent ruby1.9.2 ppa

An simplier solution for some is to setup thru the gui and then run the rip from  a terminal using one of these, depends on version of rr in use 
rrip_cli -a
or
rrip_cli -d

abcde (cli only) also works quite well, can use either cdparanoia or cdda2wav, there are some threads around on how to use and or setup

:) Sorry mc4man, I had to smile when I read your solution(s). This is an excerpt from my OP.

> **Mylorharbour said:**
> So, what is a one click function in WMP takes an eternity in Ubuntu. There must be a better way. Can anyone point me in the right direction?

---

### Post by trinitydan on 2010-12-31
What about the solution suggested by samfuzz quoted in post 27?  I think that might work to get your desired result.

---

### Post by mc4man on 2010-12-31
> I had to smile when I read your solution(s). This is an excerpt from my OP.
That's ok, I've never been much for 1 click since using linux...

As an aside (mind you, not a solution), you can actually make it less than 1 click, RR and to some extent abcde can be set to autorun on cd insertion. Just pop the cd in, several minutes later it will eject, all done, no clicks

---

### Post by cascade9 on 2011-01-01
> **mc4man said:**
> Possibly but all lucid, mav. or natty users of the gui will find it takes more time to go from 1 track to the next then it takes to rip/encode that track. There is no 'fix' other than to use what I've mentioned. (the cli is unaffected, the gui works fine other than the actual ripping.

[http://code.google.com/p/rubyripper/issues/detail?id=348&colspec=ID%20Type%20Status%20Summary%20Stars%20Opened%20Modified]("http://code.google.com/p/rubyripper/issues/detail?id=348&colspec=ID%20Type%20Status%20Summary%20Stars%20Opened%20Modified")

(it only takes about 5 min to set up ruby1.9.X and build a new ruby-gtk2, install RR, ect. but the 'setup in gui, rip in cli' is quicker to describe

Agreed, it does have that huge pause between tracks. I havent bothered trying to setup ruby 1.9, I havent been ripping that much lately, and I can deal with the pause anyway. Nice to know that ruby 1.9 does fix that pausing, hopefully I get it in a dist-upgrade soon (sid/aptosid). 

> **trinitydan said:**
> I understand that I am not forced to use RubyRipper, and I am probably  not going to, but that is kind of beside the point as I am just trying  to help out the original poster.  By "still looking for solutions", I  meant I am still looking for an alternative software program to meet the  OPs needs.  I have no need whatsoever for a ripper that outputs ID3v2.3 tags.

Edit:  I do see what you mean though, in this instance in particular we are not forced to use RubyRipper as it looks like there are a variety of options to get our desired outcome.  I should have reflected on your post further before replying.

That was what I was referring to, but it is possible that I was mistaken about what was making the rips unacceptably slow.  How long does it take to rip a cd from the command line with the options described?

Honestly, I dont think that there will be single GUI 'solution' to the OPs problem, and from what I've seen of WMP users, any more suffing around will be a cause for grumbling. Maybe I've only dealt with the lamest WMP users though, they cant ALL be like that. :lolflag: 

No problem. Most of the time I'd agree with you, but rubyripper is kind of a 'why use that' program....just like EAC (less options than EAC, but EAC is the king of rippers) 

I dont think you can exactly replicate rubyripper from command line (it uses its own algorithm). I could be wrong about that, maybe mc4man knows ;)

---

### Post by VanillaMozilla on 2011-01-03
Wow!  You really got the title changed.  Some of us are a little partisan, you know.  :D

Update:  That crash I mentioned in Sound Juicer *is* fixed in Maverick, but not in Lucid.

---

### Post by Mylorharbour on 2011-01-03
> **trinitydan said:**
> Maybe the simplest solution is the best?

I tried changing the settings in Sound Juicer by editing the CD Quality MP3 profile as specified by samfuzz.  The rip speed is still what I would consider "normal" and the ID tags are recongnized by my iPod.  Hopefully this solution will work for the OP.
It took me some time to work out what samfuzz meant.

> Originally Posted by samfuzz View Post
in "gnome-audio-profiles-properties"

set id3mux instead of id3v2mux in your gstreamer mp3 profile,
this will write id2v2.3 tag instead of id2v2.4 tag
I couldn't find "gnome-audio-profiles-properties" but I found something similar after I turned on the Configuration Editor in System, Preferences, Main Menu.

Yes, very close now......but still no album art?

---

### Post by trinitydan on 2011-01-03
Unfortunately it seems there is no way to embed album art with Sound Juicer so that is a nogo in our quest for the 1 click rip with ID3v2.3 tags and album art.  I am wondering if now that you have set up the correct audio profile it will work with easyTAG?  If not it is possible there is a configuration option that will work in easyTAG.  I am downloading it right now to try it out.

Edit:  I had a blonde moment apparently...  That's not ripping software.  Perhaps k3b will work with the new audio profile settings?  I am going to have to look into it further.

---

### Post by trinitydan on 2011-01-03
Well, the best temporary fix I can give you is not that pretty.  For now you should use Rythymbox to find album art.  For an individual album, just start playing the album and it should add album art.  If you have ripped a bunch of albums and want to find album art for a bunch of albums at once, then go to the edit menu in Rythymbox and select "Plugins" and uncheck and recheck the box to get album art.  There are other programs to tag MP3s in Ubuntu, but they are more sophisticated and are not rippers.  Even still I don't think the original title of this thread would hold up as accurate to many members here as most of us prefer the vast choice of programs, from simple to advanced, over a slight setback in terms of ease of use.  I have personally been very impressed with several of the programs I learned about in the course of this thread.  In particular, K3B does seem like a very full featured and high quality ripping program, much like Nero.  RubyRipper is also a great program to look into for the MP3 aficianado. 

I hope that this temporary fix works alright for you and doesn't leave you feeling as frustrated with your Ubuntu CD ripping experience.  I will continue to look for rippers and simpler ways to tag whole collections with album artwork or maybe someone else will have figured something out and post up here.

---

### Post by Mylorharbour on 2011-01-04
Thanks for all your help trinitydan. 

Between Sound Juicer, Rhythmbox and MP3 Diags I can get most ripping and album art done reasonably quickly. I'll look back at this thread as I think someone mentioned other sources of album art. I don't know what sources Rhythmbox uses but most sources, including WMP struggle with British compilations and genres like brass bands and folk.

It's usually easy to get a jpg of album art from Amazon UK etc but do you know of a way to get that into the tags?

---

### Post by trinitydan on 2011-01-04
> **Mylorharbour said:**
> 
It's usually easy to get a jpg of album art from Amazon UK etc but do you know of a way to get that into the tags?
I think now that you have the correct ID3 tag setup, you should just be able to drag the album art from the web browser window and drop it in the artwork sidepane of Rhythymbox while a song is playing and it should adjust the artwork accordingly for the album.  You'll have to test it out and see if it does embed the correct art to the tags and not just in Rhythymbox for your player.

> **Mylorharbour said:**
> Thanks for all your help trinitydan. 
You're very welcome!  Also thanks samfuzz for the vital bit about  changing out the backend and everyone else who contributed to this  informative thread!  Hopefully more developments will arise here.  I'd love to see a [SOLVED] on this thread when you have found ways to surpass the ripping capability you enjoy in WMP.
:guitar:

---

### Post by Mylorharbour on 2011-01-04
EasyTAG will apply a jpg but only one track at a time it seems. Some of my compilations have 150 tracks.

Thanks all.

---

### Post by trinitydan on 2011-01-04
Did you try dragging and dropping it in RhythymBox?  It does full albums for my machine (only 10-15 tracks for me usually), but as I said I have no way of testing if the tags would stick for your player not just in RhythymBox.  That draging and dropping album art while the track playing is pretty nifty.  I have to give credit to iTunes for being the first place I saw that years ago, but I am very glad it was adopted into RhythymBox.  It is the easiest and most intuitive way to change album art in most cases IMO.

---

### Post by tuppe666 on 2011-01-05
> **Mylorharbour said:**
> EasyTAG will apply a jpg but only one track at a time it seems. Some of my compilations have 150 tracks.

Thanks all.

I have little knowledge of your choice of music, but I would suggest that there are only a few of those 150!? tracks in any compilation that you really want. I also suspect that those you do have been released as singles. Music Players both Physical and 3 panel are geared towards Albums. Its more work but you can find stuff and you listen to what you really want, be aware that iTunes and WMP implement Various Artists with different tags.

---


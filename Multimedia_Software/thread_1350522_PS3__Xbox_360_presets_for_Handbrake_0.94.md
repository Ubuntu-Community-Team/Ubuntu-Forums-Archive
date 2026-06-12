---
title: "PS3 / Xbox 360 presets for Handbrake 0.94"
date: 2009-12-09
forum: Multimedia Software
---

### Post by gdbutcher on 2009-12-09
Handbrake 0.94 no longer has presets for PS3 and Xbox 360. The devs don't use the devices so they wont create profiles for them.

I have copied the presets from 0.93 and have attached them to this post. I can confirm the PS3 one works, but not the xbox 360 (becuase I don't have one).

To get them running in Handbrake 0.94, simply save the attachment(s).

Rename them from:

PS3.txt to PS3.plist
Xbox 360.txt to Xbox 360.plist

Open Handbrake, go to bottom left corner, click on 'Options'
then 'Import' and choose PS3.plist or Xbox360.plist.

it should appear in grey in your preset menu, to make it the default setting, click on it, go to 'Options' then click on 'Make Default'

And your done

I can confirm the PS3 one works, if someone could try the Xbox 360 one and leave feedback that'd be great.

---

### Post by JohnAStebbins on 2009-12-09
> **gdbutcher said:**
> Handbrake 0.94 no longer has presets for PS3 and Xbox 360. The devs don't use the devices so they wont create profiles for them.

"wont create profiles" is inaccurate. The PS3 preset became redundant.  Both the "Normal" and "High Profile" presets should work with the PS3.  It was no longer necessary to have another preset with the special name "PS3".

So there are multiple PS3 presets.  They just are not named "PS3".

---

### Post by gdbutcher on 2009-12-09
> Both the "Normal" and "High Profile" presets should work with the PS3.

I read that on handbrake website too, but I'm afraid neither of these profiles work on the PS3, thats why I uploaded these old presets. 

Hopefully someone else will find them useful.

---

### Post by JohnAStebbins on 2009-12-10
> I read that on handbrake website too, but I'm afraid neither of these profiles work on the PS3, thats why I uploaded these old presets.
This is the same problem we had with the old PS3 preset.  Some people claimed it worked, some claimed it didn't.  Yet another reason it was dropped. I've not noticed any forum posts that categorically demonstrate that the high profile preset doesn't work. Here's one that says the High Profile preset works fine.

[http://forum.handbrake.fr/viewtopic.php?f=5&t=13478&p=65727&hilit=ps3+preset#p65727](http://forum.handbrake.fr/viewtopic.php?f=5&t=13478&p=65727&hilit=ps3+preset#p65727)

I believe that user did rename the output file extenstion from .m4v to .mp4.  Handbrake will use the .mp4 extension if the output file does not have ac3 audio, subtitles or chapter markers.  If it has any of those things, .m4v is used for quicktime compatibility reasons.

---

### Post by MrSqueezles on 2009-12-10
I had lots of compatibility issues.  The best solution I found was to use a good media server.  MediaTomb (Linux) and TVersity (Windows) will let you play any media file.

---

### Post by Avoozl on 2009-12-13
Thank you so much!  I haven't tried this yet but the PS3 presets in 0.9.3 worked like a charm for me until 0.9.3 wouldn't run anymore... then I found out they removed them in 0.9.4 and I was ready to kick my monitor in.

---

### Post by jecarroll on 2009-12-21
Just wanted to say a big thank-you for this! Have been trying to convert a 720p mkv movie for my Xbox 360 and after several attempts and criptic error messages on my Xbox, I was about to give up. The Xbox preset worked a treat - many thanks!

---

### Post by mongolooks on 2010-01-02
Seems to be working like a charm for XBOX360 with Connect360 on a MacBook Pro. Thanks and much appreciated.

---

### Post by ChiaJesus on 2010-01-03
Thanks for posting this! Last night I tried watching a couple of movies on my PS3 where I had used the "High Profile" setting for the conversion and both of them had audio/video sync issues. I hope this clears that up.

---

### Post by ameetcam on 2010-01-19
thanks man, hope it works! :D

---

### Post by twisted_steel on 2010-01-27
Thanks for the Xbox 360 preset.  I'm going to give it a try.

EDIT:
Works perfectly with Fuppes for streaming. Thanks!

---

### Post by MartinChir on 2010-03-22
I have an LG BD370 (MTK chipset I think) & the only relevant option was "Ref. Frames" set to "1" I could use everything else on the high profile.

Thanks for the PS3 profile, put me on the right direction.

Also I suggest people go down to 96Kbps/44.1KHz, AAC is very efficient & 44.1 is transparent to 48Khz.

Also if working directly from the DVD drive beware the program does not stop on errors! Or even declare them to the user! Rip the ISO first with DVD Decrypt!

---

### Post by the_bengine on 2010-07-25
Thanks for these.
Another happy customer.

---

### Post by jquarry1 on 2010-08-15
Like many, I was disappointed to lose the PS3 presets in the new build.  Thanks for making it easy to restore the preset -- much appreciated.

---

### Post by Mr.MS on 2010-12-30
thanx much im converting a video now and i really hope it'll work for me

---

### Post by bruno-jordan on 2011-01-10
I couldn't load it at macbook pro with hanbrake 0.9.5

---

### Post by bigKJ on 2011-01-11
Thanks I will give this a shot!

---

### Post by bigKJ on 2011-01-11
Imported it into 0.9.5 so far so good. Thanks!

---

### Post by 7up1n3 on 2011-01-20
> **bigKJ said:**
> Imported it into 0.9.5 so far so good. Thanks!
So far so good here too.  High Profile preset left me sans sound, so thanks indeed!

---

### Post by se7enhuss on 2011-01-22
just downloaded and installed xbox 360 profile, encoded quickly and worked perfectly, thank you very much.

---

### Post by eklipse84 on 2011-01-23
> **bruno-jordan said:**
> I couldn't load it at macbook pro with hanbrake 0.9.5
Well I'm on a macbook pro running the latest 10.6.6 mac os. Using handbrake 0.9.5 and I uploaded the ps3 file just fine. Up on the top bar, once you have the handbrake program open, click on presets drop down and select import. The ps3 file you should of rename to PS3.plist and it should work. Shows up on your preset windows as (import) PS3

---

### Post by alby72 on 2011-02-02
thanks a lot from  my side!
it works fine on PS3:popcorn:

---

### Post by bodam on 2011-02-23
> **se7enhuss said:**
> just downloaded and installed xbox 360 profile, encoded quickly and worked perfectly, thank you very much.

The XBOX settings worked for me but the sound is only 2 channel stereo rather than 5.0/5.1.  Any ideas?

---

### Post by orngchkn on 2011-03-27
Xbox preset didn't work for me (and it took about 8 hours to finish transcoding).

---

### Post by vivi the mage on 2011-03-30
Thanks, very helpful :).

---

### Post by jonthysell on 2011-04-29
I just use the Regular/Normal or Regular/High profiles and they work great on the Xbox 360, as long as you rename the file to .m4v instead of .mp4.

---

### Post by tdawg309 on 2011-05-24
Sorry to open a old thread. But, I felt it was necessary to say I love you. This just saved me from a lot of time consuming work! So, thank you.:KS



Edit: Maybe it wasn't old. I was looking at the first post. Haha

---

### Post by Leviathan88 on 2011-10-01
> **gdbutcher said:**
> Handbrake 0.94 no longer has presets for PS3 and Xbox 360. The devs don't use the devices so they wont create profiles for them.

I have copied the presets from 0.93 and have attached them to this post. I can confirm the PS3 one works, but not the xbox 360 (becuase I don't have one).

To get them running in Handbrake 0.94, simply save the attachment(s).

Rename them from:

PS3.txt to PS3.plist
Xbox 360.txt to Xbox 360.plist

Open Handbrake, go to bottom left corner, click on 'Options'
then 'Import' and choose PS3.plist or Xbox360.plist.

it should appear in grey in your preset menu, to make it the default setting, click on it, go to 'Options' then click on 'Make Default'

And your done

I can confirm the PS3 one works, if someone could try the Xbox 360 one and leave feedback that'd be great.

Where is the *THANK YOU* button to say thanks to the OP!? ;)

---

### Post by scotlandtb on 2011-12-15
> **bodam said:**
> The XBOX settings worked for me but the sound is only 2 channel stereo rather than 5.0/5.1. Any ideas?
 
Found the XBOX preset and trying now Thanks for getting it as I was having to handbrake then convert to WMV which SUCKED.
 
Bodam - have a look at the XBOX video specs. Only WMV can do 5.1 al other formats are encoded at stereo.
 
Steve

---

### Post by adwhite on 2011-12-18
Thanks!

---

### Post by jasondo2112 on 2012-01-26
This preset worked like a charm for the Xbox setting. This just eliminated three steps in my encoding and streaming process.

---

### Post by Vegburner on 2012-02-03
> **ChiaJesus said:**
> Thanks for posting this! Last night I tried watching a couple of movies on my PS3 where I had used the "High Profile" setting for the conversion and both of them had audio/video sync issues. I hope this clears that up.
 
I had the same problem with sync of Audio/Video. Thanks to these presets not any more well done.  My file was an mkv that would not convert to MP4 without the sync issue. Using a dual pass and keeping to a 4gb setting I could save it to an external Fat32 drive compatable with PS3 and also burn onto DVD.  The preset did the trick.

---

### Post by sjordan99 on 2012-03-10
> **jonthysell said:**
> I just use the Regular/Normal or Regular/High profiles and they work great on the Xbox 360, as long as you rename the file to .m4v instead of .mp4.

Thanks a million! This worked perfectly for me.

---

### Post by Waffle S.S. on 2012-06-01
Sorry to bump an old thread but wanted to say thanks so much for this. I had tried a bunch of different combinations of HandBrake settings but nothing worked for getting my Xbox 360 to recognize my videos, but this preset works consistently.

I took the liberty of [making a gist]("https://gist.github.com/2814482") (paste) with these presets, in case someone stumbles across this thread and doesn't want to create an account in order to view them.

---

### Post by army0193 on 2012-06-27
Wow thanks a ton for posting this! Im sure this will be of help to others as it was to me. :popcorn:

> **Waffle S.S. said:**
> Sorry to bump an old thread but wanted to say thanks so much for this. I had tried a bunch of different combinations of HandBrake settings but nothing worked for getting my Xbox 360 to recognize my videos, but this preset works consistently.

I took the liberty of [making a gist]("https://gist.github.com/2814482") (paste) with these presets, in case someone stumbles across this thread and doesn't want to create an account in order to view them.

Too bad I didn't see your post first!

---


---
title: "Is gstreamer limiting your LAME bitrate???"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by GrouchoMarx on 2007-11-09
I was trying to rip a CD to mp3s using Sound Juicer. The following gstreamer profile worked perfectly under feisty:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=1002 ! xingmux ! id3v2mux
```

It uses [LAME's "extreme" preset]("http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/presets.html") to create 200-240kbps VBR mp3s. However, under Gutsy, something is capping the bitrate to a CONSTANT 160kbps. You can achieve any constant bitrate under 160kbps by changing the profile quality, but WHO NEEDS THAT? The bitrates were confirmed using vlc's stream statistics.

Is anyone else having this problem? I didn't even notice it until I heard the lower quality in one of my rips, so it might be happening to more people than they realize.

Maybe somebody could post a command to bypass gstreamer, and encode directly from the CD? Possibly using LAME itself?

Thanks...:-k

---

### Post by GrouchoMarx on 2007-11-16
Can anyone else confirm (positively or negatively) this behavior? It is essentially a fresh Gutsy install (as far as the media codecs are concerned).

---

### Post by dbw6993 on 2007-11-20
I'm experiencing the same problem. I seem to recall this occurring in Feisty as well, but I can't remember what I had to do to fix it...

---

### Post by GrouchoMarx on 2007-11-20
> **dbw6993 said:**
> I'm experiencing the same problem. I seem to recall this occurring in Feisty as well, but I can't remember what I had to do to fix it...

But you *did* fix it eventually?

---

### Post by GrouchoMarx on 2007-11-26
Okay, so more information...

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr-quality=[0-9] ! xingmux ! id3v2mux
```

where vbr-quality can be any number from 0-9. This ALWAYS gives a constant bitrate of 128kbps, regardless of vbr-quality. (Unless you explicitly specify LAME's "new" vbr algorithm, in which case the bitrate limit becomes 160 kbps).

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=[lame preset] ! xingmux ! id3v2mux
```

where vbr-quality can be any of the lame presets (medium, standard, extreme, insane). This ALWAYS gives a constant bitrate of 160 kbps, regardless of the lame preset.

This is confirmed on two FRESH Gutsy installs, on two seperate computers, and BOTH pipelines work properly in Feisty.

Can anyone see anything wrong with the pipelines?

---

### Post by captaintrav on 2007-11-30
I'm seeing the exact same behavior on my Debian Box, google found this thread for me.

I'm using a Debian-Testing install with some packages from Unstable.

gstreamer0.10-lame 0.10.6-0.1

The defaults are producing 128kbs mp3s instead of VBR ones, and the best I can get by changing the profile is 160kbs.

---

### Post by GrouchoMarx on 2007-11-30
> **captaintrav said:**
> I'm seeing the exact same behavior on my Debian Box, google found this thread for me.

I'm using a Debian-Testing install with some packages from Unstable.

gstreamer0.10-lame 0.10.6-0.1

The defaults are producing 128kbs mp3s instead of VBR ones, and the best I can get by changing the profile is 160kbs.

I'm still trying to find a solution. What front-end are you using for gstreamer?

---

### Post by captaintrav on 2007-12-01
I'm using sound juicer.  It does appear that most of the parameters are not getting passed to Lame, I guess I will have to use a ripper that doesn't use gstreamer backend.  After noticing this, I double checked some other music I had ripped with sound juicer in the past, and the resulting mp3s were fine, so it is definately a "new" problem.  I'm also guessing if the problem exists in Gutsy as well as in Debian, it is some sort of upstream bug in gstreamer.

---

### Post by gweaver on 2007-12-03
> **GrouchoMarx said:**
> This ALWAYS gives a constant bitrate of 160 kbps, regardless of the lame preset.

This is confirmed on two FRESH Gutsy installs, on two seperate computers, and BOTH pipelines work properly in Feisty.

I have noticed this too, most annoying.

---

### Post by Lumo on 2007-12-03
I'm having this problem with Asunder ripping to mp3 (with lame) - setting it to the highest quality it makes a something around a 128-160kbs file.

This is annoying, I can boot into Vista and rip it properly there, but that is by no means an ideal solution!

---

### Post by mobiusstrip on 2007-12-06
> **captaintrav said:**
> I'm seeing the exact same behavior on my Debian Box, google found this thread for me.

I'm using a Debian-Testing install with some packages from Unstable.

gstreamer0.10-lame 0.10.6-0.1

The defaults are producing 128kbs mp3s instead of VBR ones, and the best I can get by changing the profile is 160kbs.

Same problem here. You can get any CBR rate by setting vbr-min-bitrate=320 (for example); that will give you 320. Files end up a bit big tho....

---

### Post by GrouchoMarx on 2007-12-06
> You can get any CBR rate by setting vbr-min-bitrate=320 (for example); that will give you 320.

Yes, I noticed that you can push the CBR past 160 by setting vbr-min-bitrate. But as you mentioned, the result is still a constant bitrate, equivalent to setting "bitrate=320". Unfortunately if you want to have your music on a portable player, you need VBR mp3s! (ogg won't do :()

---

### Post by mobiusstrip on 2007-12-07
true - not least as my player doesn't play ogg! or flac...

---

### Post by GrouchoMarx on 2007-12-10
Some more information...

It seems that we can rule out lame as being the source of the problem. Using lame from the command line you can create variable bitrate mp3s of any quality:

```
lame --vbr-new -V 1 song.wav song.mp3
```

-V # sets the quality of the encoding, equivalent to setting vbr-quality in gstreamer. Your input wav file must have a bitwidth of 8, 16, 24, or 32. Also, because it's not being piped through any tagging software (xingmux, id3v2mux) most media players will not report the bitrate correctly. You can use VLC's real-time stream statistics to confirm that the result is a high quality variable bitrate (-V 1 should be ~224 kbps).

This suggests that gstreamer is in fact the source of the problem. Any more ideas are welcome!

---

### Post by schtum on 2007-12-14
This is just a "me too" post. Same exact problem, also using Gutsy. I'll keep an eye on this thread for a solution.

---

### Post by schtum on 2007-12-14
Okay, I can confirm that the solution is to use Grip instead of Sound Juicer ;)

Check out this thread for instructions when you're ready to give up on gstreamer:
[http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151](http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151)

I'm using as my encoder command-line: -V 2 --vbr-new %w %m
Change the 2 to whatever you'd normally use after "vbr-quality=" with gstreamer. 

Quick tips to make Grip output files exactly like Sound Juicer:

Under config/encode/encoder:
Encode file format: ~/music/%A/%d/%t - %n.%x
 (replace ~/music/ with the location of your own music folder)

Under config/misc:
check: Do not lowercase filenames
check: Do not change spaces to underscores

And you're done.

Average bit rates and song lengths are even accurately reported in Amarok.

---

### Post by GrouchoMarx on 2007-12-14
Grip looks like an interesting piece of software and it may be a good interim solution. However, many other useful programs (soundconverter is also effected by this problem) use the gstreamer framework and it would be nice to get Ubuntu's default cd ripper working.

Does anyone know what would be the next step? Do we report this as a bug in launchpad or something? I've never done that before.

---

### Post by 12barz on 2007-12-16
If it doesn't get reported as a bug it won't get fixed.  Grouchomarx probably knows the most about this,  judging from his posts in this thread and the one on vbr mp3's.  Groucho, it would probably be good for us all if you would report this to the bug guys.  You have more specifics that you can use to explain it clearly so they'll realize it really is a bug and not the result of mistakes by the unsophisticated.

---

### Post by GrouchoMarx on 2007-12-16
I appreciate the vote of confidence ;) but I am not familiar with the reporting process. Also I think a that it has already been reported on Bugzilla: [Bug 498004]("http://bugzilla.gnome.org/show_bug.cgi?id=498004"). I left a comment indicating that the problem is not limited to the lame presets and that it also affects the other vbr parameters, like vbr-quality.

Anyone who might know of a more effective way to contribute, please speak up!

---

### Post by 12barz on 2007-12-20
I think the place to report it might be:
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
since it involves sound-juicer.

---

### Post by GrouchoMarx on 2007-12-20
> **12barz said:**
> I think the place to report it might be:
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)
since it involves sound-juicer.

I'm fairly certain that the problem is not due to Sound Juicer. The following command:

```
gst-launch-0.10 filesrc location=foo.wav ! audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr-quality=0 ! xingmux ! id3v2mux ! filesink location=foo.mp3
```

uses the gstreamer framework to encode a lame mp3 independently of soundjuicer, and produces the anomalous behavior discussed in this thread.

---

### Post by Scruffynerf on 2008-01-04
Just a "me too" on Feisty. Lame version 3.96.1-2ubuntu1, Gstreamer Bad / Ugly versions 0.10.5

---

### Post by GrouchoMarx on 2008-01-04
> Just a "me too" on Feisty. Lame version 3.96.1-2ubuntu1, Gstreamer Bad / Ugly versions 0.10.5

That's very interesting because my experience on Feisty has been that gstreamer successfully encodes lame mp3s of all bitrates. Unfortunately, my feisty box just went caput, and so I have no way of corroborating the lib versions.

---

### Post by Scruffynerf on 2008-01-05
> **GrouchoMarx said:**
> That's very interesting because my experience on Feisty has been that gstreamer successfully encodes lame mp3s of all bitrates. Unfortunately, my feisty box just went caput, and so I have no way of corroborating the lib versions.

Just recently decided to rip my cd collection to mp3 to allow me to create mixes for driving to work, and running soundjuicer.

Was following the guide at [https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping) and set up a soundjuicer profile to mp3. Using both of the commands/voodoo/pipline as given, and modifying them to set to a supposed bitrate of 320 (specifying the bitrate at 320 in first option, setting preset to insane, or 1004 in the second option, all of them only came out at a bitrate of 120 as validated by 3 other programs.

Audio quality was also noticably crappy.

I'll probably play around with Grip later on to see if that will work.

I've seen [http://bugzilla.gnome.org/show_bug.cgi?id=498004](http://bugzilla.gnome.org/show_bug.cgi?id=498004) , however I don't really understand it - all I know is that it's not working as it should.

---

### Post by GrouchoMarx on 2008-01-06
Ok, so I found a solution to getting gstreamer to work under Gutsy. I hate these kinds of solutions, but if you want Sound Juicer to work properly, it's pretty simple:

The culprit is version 0.10.6 of the gstreamer library file libgstlame.so. To downgrade to a working version (0.10.5) simply downgrade the **gstreamer0.10-plugins-ugly-multiverse** package from version **0.10.6-0ubuntu1** to version **0.10.5-2**.

You can download the 0.10.5-2 libraries here: [http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/]("http://archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/")

Uninstall the default Gutsy package:
```
sudo apt-get remove gstreamer0.10-plugins-ugly-multiverse
```
and install the 0.10.5 package:
```
sudo dpkg -i gstreamer0.10-plugins-ugly-multiverse_0.10.5-2_i386.deb
```

The downgrade eliminates the anomalous behavior discussed in this thread. Since libgstlame.so is the only library file in the ugly-multiverse package, it is also the only library affected by the downgrade. As I said, I hate these types of solutions, but obviously the 0.10.6 library is unusable (or at least I can't figure out how to get it working), and shouldn't have been pushed out before it was ready.

I am still somewhat suspicious that more people haven't confirmed this problem. The only explanation I have is that they haven't noticed!

---

### Post by GrouchoMarx on 2008-01-06
Once you've downgraded the gstreamer0.10-plugin-ugly-multiverse package you might also want to put it on hold to avoid a perpetual update notification:

Through synaptic: find your downgraded gstreamer0.10-plugin-ugly-multiverse package, then from the menu select Package and check "Lock Version".

Through the CLI:
```
sudo aptitude hold gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by nihildeclaro on 2008-01-27
Another "me too" on Gutsy.

LAME 3.97 (working fine - tested with WAV files created with cdparanoia)
gstreamer bad/ugly 0.10.6

---

### Post by Lobinho on 2008-01-28
Me too.  Removed the default gstreamer 0.10 but can't seem to find the 10.5 - got this error:

user@host:~$ sudo dpkg -i gstreamer0.10-plugins-ugly-multiverse_0.10.5-2_i386.deb
dpkg: error processing gstreamer0.10-plugins-ugly-multiverse_0.10.5-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gstreamer0.10-plugins-ugly-multiverse_0.10.5-2_i386.deb

Am I doing something wrong?

Thanks!

Lame 3.97
Gutsy

---

### Post by GrouchoMarx on 2008-01-28
It seems like the .deb file is not in the directory in which you ran the command.

Make sure that you either run the command in the same directory as the .deb file, or that you supply the full path to the file: ~/directory/to/package.deb

Hope that helps! Let me know your results!

---

### Post by GrouchoMarx on 2008-01-28
Also make sure that you downloaded the correct file, "gstreamer0.10-plugins-ugly-multiverse_0.10.5-2_i386.deb", from the list of gstreamer packages:

> You can download the 0.10.5-2 libraries here: [http://archive.ubuntu.com/ubuntu/poo...ultiverse0.10/](http://archive.ubuntu.com/ubuntu/poo...ultiverse0.10/)

;)

---

### Post by Lobinho on 2008-01-29
Thanks for the info.  I got the 10.5, but the problems persist.

I'm using Sound Juicer and the output format I created is not showing up as an option.  However, when I hit 'edit profiles', I see it and it's active.  Also, the MP3 lossy preset which I altered to vbr-quality=2 still puts out 128kbps mp3s.

I found this post: [http://ubuntuforums.org/showthread.php?t=652698](http://ubuntuforums.org/showthread.php?t=652698) and will follow up as I try to fix the Sound Juicer problems first.  Post #14 is pretty much exactly what I'm getting...

Thanks.

---

### Post by GrouchoMarx on 2008-01-29
Just to make sure that the 10.5 version is properly installed, try the following command in your terminal:

```
gst-inspect-0.10 lame | grep Version
```

This should output the version number of your gstreamer lame plugin. Then give the following profile a try:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 preset=extreme ! xingmux ! id3v2mux
```

The profile should create a high-quality variable bitrate around 200-240 kbps, using the built-in lame presets.

---

### Post by Lobinho on 2008-02-01
Hi there.  With 10.5 properly installed and using the above pipeline, I got a mp3 that doesn't say the sampling rate and the song duration is completely wrong.

Maybe the id3v2mux or xingmux are not working properly? It seems the tags are not correct...

Also, my added output profile still doesn't show up in the drop-down menu in sound juicer.  Does sound juicer not show more than one output format of the same type? (mp3, in this case)

This is so strange.  Thanks much for your help.

---

### Post by GrouchoMarx on 2008-02-01
> I got a mp3 that doesn't say the sampling rate and the song duration is completely wrong.

This suggests to me that the new pipeline is not being used, because the "! xingmux" component of the pipeline should specifically resolve the misreported song duration.

Additionally the profile you created is not showing up in the sound juicer drop-down menu, so let's see if we can update the original mp3 profile. You can try the following:

In your terminal, run the command:
```
gconf-editor
```
This program allows you to view and change all your gnome settings, including your gstreamer profiles. The profiles can be found under:

system > gstreamer > 0.10 > audio > profiles > mp3

Select the mp3 profile and then right click on the "pipeline" paramater to "Edit Key...". Then replace the old pipeline with the pipeline I suggested (you may want to temporarily save the old pipeline in a text file somewhere):

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 preset=extreme ! xingmux ! id3v2mux
```

Then you can go back, restart sound juicer, and the mp3 profile should be updated to use the new pipeline. Within sound juicer, you can double check that the mp3 profile has been updated. Also double check that the profile is marked "active" and that you have it selected in the sound juicer drop-down menu. Then give it a rip.

Let me know if this works.

---

### Post by Lobinho on 2008-02-02
Ok, using this pipline, I'm getting a file size that must reflect the preset because it's double or triple the file size from the 128kbps.  However, the duration in Rhythmbox is off, while it displays correctly in audacious.  Neither player nor a right-click and properties shows the bitrate, but I'm pretty sure the quality is where I want it.  Is there something wrong with Rhythmbox?

Also, I've figured out how to get my own profiles to show - the name of the profile has to follow the default profile naming scheme.  Ok.  So now I have two mp3 profiles available - one uses the pipeline suggested and the other is the same with "-preset=standard" instead of extreme.

So, generally happy except for that weird song duration bug with rhythmbox...

Again, thanks - I really appreciate you helping me out with this.

---

### Post by GrouchoMarx on 2008-02-02
> However, the duration in Rhythmbox is off, while it displays correctly in audacious. Neither player nor a right-click and properties shows the bitrate, but I'm pretty sure the quality is where I want it. Is there something wrong with Rhythmbox?

If you want to know the bitrate of your mp3, then you can do the following. When you rip a track in sound juicer it will show you the length of the song off of the CD. Then, using this song duration and the resulting file size, you can calculate the average bitrate of your variable bitrate mp3:

[ ( Filesize in MB * 1024 MB/KB * 1024 KB/B * 8 B/b ) / 1000 b/kb ] /  (song duration in seconds) = Bitrate in kbps

OR, if you have the VLC media player then you can see the bitrate in real-time through "view > stream and media info > statistics". You will see the bitrate fluctuate around your average bitrate.

The fact that the bitrate and the song duration are not being properly reported in Rhythmbox is not really a bug per se. It is a consequence of the fact that Rhythmbox looks at the beginning of the file to determine the bitrate. For variable bitrate mp3s the bitrate will appear very low because the beginning of most songs have very little sound, and are encoded at a much lower bitrate than the rest of the song. Rhythmbox then takes this very low initial bitrate, and given the normal file-size, calculates that the song must be very long. The only solution is to use tagging software to insert file "headers" that contain all the necessary information such as song duration. However, the pipeline I gave you should have done that: "! xingmux" adds header information to the mp3 files during the encoding process. When I added it to my pipeline, it immediately solved the song duration problem (though it still may not solve the reported bitrate problem).

---

### Post by Lobinho on 2008-02-03
Hmm, yeah it seems like the xingmux should insert the correct headers, but for some reason, it's not working...

Is there a way to do that on the command line so I can see whatever error(s) might be present?

---

### Post by GrouchoMarx on 2008-02-04
The following will allow you to rip the first track off a CD:

```
gst-launch-0.10 -v cdda://1 ! audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=extreme ! xingmux ! id3v2mux ! filesink location=foo.mp3
```

You can change the output (foo.mp3) to whatever/wherever you want. You should see these lines somewhere in the output:

> /pipeline0/xingmux0.src: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3, channels=(int)2, rate=(int)44100
/pipeline0/xingmux0.sink: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3, channels=(int)2, rate=(int)44100

---

### Post by Lobinho on 2008-02-04
So, I see those two lines for the xingmux, but upon importing the file to Rhythmbox, the duration is wrong and no artist/album/etc. information is present.  Is there anything present in this quote that tells what's happening (or not happening)?  What are those NULLs toward the bottom?

> user@host:~$ gst-launch-0.10 -v cdda://1 ! audio/x-raw-int,rate=44100,channels=2 ! lame name=enc preset=extreme ! xingmux ! id3v2mux ! filesink location=moving.mp3
Setting pipeline to PAUSED ...
/pipeline0/cdparanoiasrc0.src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)44100, channels=(int)2
Pipeline is PREROLLING ...
/pipeline0/cdparanoiasrc0: track = 1
/pipeline0/capsfilter0.src: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)44100, channels=(int)2
/pipeline0/capsfilter0.sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)44100, channels=(int)2
/pipeline0/enc.src: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3, channels=(int)2, rate=(int)44100
/pipeline0/enc.sink: caps = audio/x-raw-int, endianness=(int)1234, signed=(boolean)true, width=(int)16, depth=(int)16, rate=(int)44100, channels=(int)2
[B]/pipeline0/xingmux0.src: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3, channels=(int)2, rate=(int)44100
/pipeline0/xingmux0.sink: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3, channels=(int)2, rate=(int)44100[/B]
/pipeline0/id3v2mux0.sink: caps = audio/mpeg, mpegversion=(int)1, layer=(int)3, channels=(int)2, rate=(int)44100
/pipeline0/filesink0.sink: caps = application/x-id3
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
Got EOS from element "pipeline0".
Execution ended after 28840763000 ns.
Setting pipeline to PAUSED ...
Setting pipeline to READY ...
/pipeline0/filesink0.sink: caps = NULL
/pipeline0/id3v2mux0.src: caps = NULL
/pipeline0/id3v2mux0.sink: caps = NULL
/pipeline0/xingmux0.src: caps = NULL
/pipeline0/xingmux0.sink: caps = NULL
/pipeline0/enc.src: caps = NULL
/pipeline0/enc.sink: caps = NULL
/pipeline0/capsfilter0.src: caps = NULL
/pipeline0/capsfilter0.sink: caps = NULL
/pipeline0/cdparanoiasrc0.src: caps = NULL
Setting pipeline to NULL ...
FREEING pipeline ...


Thanks for taking a look.

---

### Post by GrouchoMarx on 2008-02-04
Your output is identical to mine (aside from the encode duration, since we're encoding different songs). Unfortunately, I can't tell what, if anything is wrong.

Does the song duration show when you right click on the file and view it's properties?

---

### Post by Lobinho on 2008-02-06
Right click and properties shows the incorrect song duration and N/A for sampling rate.

---

### Post by GrouchoMarx on 2008-02-20
The only other thing I can recommend is to double check that you have the "gstreamer0.10-plugins-bad" package installed. It contains the xingmux libraries.

---

### Post by Scrik on 2008-02-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've opened a bug page on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483](https://bugs.launchpad.net/ubuntu/+source/sound-juicer/+bug/195483)

:popcorn:

---

### Post by Horns on 2008-02-27
> **GrouchoMarx said:**
> Once you've downgraded the gstreamer0.10-plugin-ugly-multiverse package you might also want to put it on hold to avoid a perpetual update notification:

Through synaptic: find your downgraded gstreamer0.10-plugin-ugly-multiverse package, then from the menu select Package and check "Lock Version".

Through the CLI:
```
sudo aptitude hold gstreamer0.10-plugins-ugly-multiverse
```

HELP!

I had the same bitrate issue, so I tried the 0.10.05 fix and all was good! Great stuff!

However, when I used the command given above to lock the version through the CLI, not only did it not get rid of the updates, it uninstalled 6 other packages (mplayer and a few others) and now I no longer have an mp3 option in sound juicer, despite having the mp3 plugin installed. 

What have I done?

---

### Post by ryth on 2008-03-04
Have there been any further updates on this? It seems a rather grevious bug to have floating around in a core app like gstreamer.

---

### Post by Major_Kong on 2008-03-04
> **GrouchoMarx said:**
> (...)
Maybe somebody could post a command to bypass gstreamer, and encode directly from the CD? Possibly using LAME itself?

Thanks...:-k

Try using rubyripper (think EAC for linux) instead of soundjuicer.


> **ryth said:**
> Have there been any further updates on this? It seems a rather grevious bug to have floating around in a core app like gstreamer.

It is, but that doesn't mean it will be quickly fixed. :wink:

---

### Post by GrouchoMarx on 2008-03-06
> However, when I used the command given above to lock the version through the CLI, not only did it not get rid of the updates, it uninstalled 6 other packages (mplayer and a few others) and now I no longer have an mp3 option in sound juicer, despite having the mp3 plugin installed.

What have I done?

Yikes! I really don't know how the command could have uninstalled 6 other packages. :confused:  (I just tried it again and it behaved as expected).

Do you have a list of which packages were uninstalled? If you do, then reinstall them, and lock the 0.10.05 gstreamer package via the GUI in synaptic.

---

### Post by GrouchoMarx on 2008-03-06
> [QUOTE]Have there been any further updates on this? It seems a rather grevious bug to have floating around in a core app like gstreamer.
It is, but that doesn't mean it will be quickly fixed. [/QUOTE]

That, and I'm willing to bet the majority of people don't even notice the difference in quality.

---

### Post by strumer on 2008-03-14
I just spent a week or so ripping with soundjuicer.  I guess i should have played a few of the mp3s in the beginning.  I played a few last night and they all sound crappy.

Any word on this ?

---

### Post by fiddler59 on 2008-03-16
This bug needs to be fixed BIG TIME.....having to rip at cbr doesn't get it for me !!!! Same bug exists in Hardy too...

David B

---

### Post by Major_Kong on 2008-03-16
> **GrouchoMarx said:**
> That, and I'm willing to bet the majority of people don't even notice the difference in quality.

The people who do, just use the CLI or scripts or another sound ripper. The Gstreamer support for mp3 encoding is very bad, so people just don't rely much on it.... 
And for those who like secure ripping, soundjuicer just isn't an option in the first place.

PS: There have been other major problems not related to encoding quality that have been "overlooked" for a long time.

---

### Post by gweaver on 2008-03-17
The problems with gstreamer have led to me giving up on MP3s. I realised that storage is so cheap now that OGG/MP3 etc are only necessary for mobile devices.
So I rip my music to FLAC using Sound-Juicer and tag it with MusicBrainz. Now I don't have to worry about whether I have used the best encoder settings for ripping my music, and I won't have to rip a CD twice because I got the encoder settings wrong.

If I need my files in a lossless compression format for a mobile device I can use SoundConverter to convert the files to the appropriate format. I guess there will always be better lossy compression formats, but FLAC won't go away for a long time.

---

### Post by Blingin2Mingin on 2008-04-11
I've followed the instructions in this thread and VBR is now working for me. But I have fallen out with using GStreamer for mp3 encoding so I started looking for simple to use alternatives. 

If else anyone is looking for an alternative to Sound Juicer and finds Grip a little too complex, they could try Asunder.   

 [COLOR="Red"][http://littlesvr.ca/asunder/index.php]("http://littlesvr.ca/asunder/index.php")[/COLOR] .

Dependencies are. GTK, Libcddb, Cdparanoia, LAME, Vorbis-Tools and FLAC.  
Thats It. NO GStreamer.
Theres a prebuilt Ubuntu Debian package on the site.

Seems very easy to use (Mp3  bit rate is set with a slider, VBR with a check box ).

It rips to wav first so it may be a little slow for some but this doesn't bother me.

The 2 flaws I've found in the day I've been using it are .
1. It uses only ID3v1 tags.
2. I Cannot make it default to ripping to Artist > Album >  Nested Folders. The Artist Folder Requires Setting up every time.

These are minor quibles for me though so I'm going to carry on using it.

---


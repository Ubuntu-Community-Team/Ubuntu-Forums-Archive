---
title: "RealPlayer stopped working with BBC"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by tree trunk on 2007-03-07
Until recently, I had complete success in watching streaming video from the BBC with realplayer 10.0.8.805 in firefox 2.0.0.2,  (a lot of it can be found here  ([http://news.bbc.co.uk/))](http://news.bbc.co.uk/))), then something changed.

The look of the player in the BBC website has been updated.  Since the update, I've not been able to get realplayer to work with the BBC.

The last time I tried, a crash report was automatically generated, but it opened a "sorry but we don't have a page for your problem" page in launchpad.

What might be going on here?

Realplayer seems to be working properly otherwise.

Thanks

tree

---

### Post by mrhelpman on 2007-03-07
It looks like we are running two threads on the same topic here.  In a way I am glad it is not just me that is having problems - see other thread titled "BBC news video clip problems".  It had not occurred to me that the Beeb had changed their end, I had assumed it was due to the update to firefox. However thinking about it, I am seeing the same problem on both my desktop (Dapper) and my laptop (Edgy) and as each version of ubuntu uses a different version of firefox and the version of realplayer has not changed, this suggests that it could be something that the BBC have done.

My symptoms are: the video seems to try to start and I see a very brief flash of the normal realplayer plugin window before the area of the screen that should be playing the streamed video goes blank (white). However I can click on the "watch in stand alone player" and this works. I have not seen it crash yet.

I would say it was all working fine say 2 weeks ago.

---

### Post by gripped on 2007-03-08
> My symptoms are: the video seems to try to start and I see a very brief flash of the normal realplayer plugin window before the area of the screen that should be playing the streamed video goes blank (white). However I can click on the "watch in stand alone player" and this works. I have not seen it crash yet.

Same here. I'm going to report this to the bbc with a link to this thread.

---

### Post by klytu on 2007-03-10
> **mrhelpman said:**
> It looks like we are running two threads on the same topic here.  In a way I am glad it is not just me that is having problems - see other thread titled "BBC news video clip problems".  It had not occurred to me that the Beeb had changed their end, I had assumed it was due to the update to firefox. However thinking about it, I am seeing the same problem on both my desktop (Dapper) and my laptop (Edgy) and as each version of ubuntu uses a different version of firefox and the version of realplayer has not changed, this suggests that it could be something that the BBC have done.

My symptoms are: the video seems to try to start and I see a very brief flash of the normal realplayer plugin window before the area of the screen that should be playing the streamed video goes blank (white). However I can click on the "watch in stand alone player" and this works. I have not seen it crash yet.

I would say it was all working fine say 2 weeks ago.

I have the same issue and I can also manage to play the videos by clicking "watch in stand alone player" as you do.

---

### Post by mrhelpman on 2007-03-11
> **gripped said:**
> Same here. I'm going to report this to the bbc with a link to this thread.

I have just done the same.  I have given the beeb links to both threads.

JT

---

### Post by thomaswp on 2007-03-18
Just for the record I have the exact same problem - anyone solved this yet?

I am on a very fresh/clean edgy install though I have had a lot of problems installing realplayer - eventually used the bin file

---

### Post by Dekunuts on 2007-03-18
What you can do is click on 'launch in stand alone player' and then save the .ram file on your desktop and then click that file and open it with realplayer. The movie will play that way, it's not a clean way, but it works

---

### Post by vjones777 on 2007-03-18
Thanks Dekunuts,
I was about to try reinstalling realplayer and then firefox until I came across this thread.
That workaround worked for me. :)

---

### Post by Dekunuts on 2007-03-18
Glad I could help :)

---

### Post by tom56 on 2007-03-18
The latest Realplayer available in the commercial repo fixes this.

1. Go to "Applications"->"Add/Remove"
2. At the top right select "Third Party Applications" from the drop-down box.
3. Untick Realplayer, click yes to any questions then click apply.
4. Now retick Realplayer, again clicking yes to any questions then click "Apply"

Essentially what you are doing is making sure "commercial" is in your sources.lst, but if you don't know what sources.lst is then the above is an easy way to do it.

---

### Post by thomaswp on 2007-03-18
Goodness, I wish I had twigged that way of installing it the first time.

I removed my .bin installation (deleted the directory and plugins from /usr/lib/firefox/plugins) but I still get no joy at all - the player comes up and then goes "white" after a few seconds (I assume the moment it starts to try playing the content).

Wondering if any of the fiddling I have done has upset this - I removed manually the other plugins (mplayer and totem?) trying to play ram files - thought they'd be in the recycle bin but they aren't so I cannot try putting them back.

The work around of clicking the link is fine - but I had a nightmare trying to change the "helper app" for "ram" files because there seems no easy way to do it in FireFox now.  I had to edit the mimeTypes.rdf file in my /home/thomas/.firefox folder AND reboot to get it to work.  No idea why firefox would not pick up the changes without a reboot.

---

### Post by klytu on 2007-03-19
> **tom56 said:**
> The latest Realplayer available in the commercial repo fixes this.

1. Go to "Applications"->"Add/Remove"
2. At the top right select "Third Party Applications" from the drop-down box.
3. Untick Realplayer, click yes to any questions then click apply.
4. Now retick Realplayer, again clicking yes to any questions then click "Apply"

Essentially what you are doing is making sure "commercial" is in your sources.lst, but if you don't know what sources.lst is then the above is an easy way to do it.

Tried this with Dapper and Firefox 1.5.0.10 but the behaviour is the same. I still need to do the workaround by launching the BBC video in a standalone player. With Opera browser however, I don't have the issue at all.

---

### Post by tom56 on 2007-03-19
> **klytu said:**
> Tried this with Dapper and Firefox 1.5.0.10 but the behaviour is the same. I still need to do the workaround by launching the BBC video in a standalone player. With Opera browser however, I don't have the issue at all.

I should have specified that I'm using Edgy so I meant that the latest realplayer in the edgy-commercial repo works.

---

### Post by thomaswp on 2007-03-19
I have edgy - but the problem is there still.  I may try opera but after testingn opera and firefox under windows I found I preferred firefox despite the obvious speed improvements in Opera.

---

### Post by lotus49 on 2007-03-20
I have precisely the same problem (on Edgy BTW) but uninstalling/reinstalling didn't do anything.

I can also launch the standalone player, but it's a bit of a pain and anyhow, this should work and I hate things that should work but don't.

Did any of you figure out what the problem was and fix it?

---

### Post by psm22 on 2007-04-15
Hi,
I'm having the same problem on my otherwise working-very-well, fresh edgy install. Realplayer 10 works ok as standalone but not straight off the BBC website. I tried tom56's suggestion but still the same behaviour. Watching this space...

---

### Post by phollands on 2007-04-17
Toms' solution did not work for me. 

Realplayer crashes still when watching BBC News Videos.

Something is going way wrong with realplayer which is outside of the control directly of the Ubuntu Team. (Proprietary Code). You can see all the gory details if you open a terminal console; and then start firefrox from a  bash shell. 

Then select a BBC News video to watch from within the browser.
When the reaplayer stuff starts to go wrong, lot's of technical information appears on the screen - and then realplayer does a core dump.

There are complaints about :
 Attempting to add a widget with type HXPlayer to a container of type HXBin, but the widget is already inside a container of type HXBin, the GTK+ FAQ at [http://www.gtk.org/faq/](http://www.gtk.org/faq/) explains how to reparent a widget.

There are many many warnings about the window set sizes being invalid. The BBC site is defintely helping to trigger a bug. Some old Videos of square proportions still work. e.g. 
[http://www.bbc.co.uk/mediaselector/check/media/video/otdvideo/61/04/20/8665_20-04-61?size=4x3&bgc=6699CC&nbram=1&nbram=1&bbram=1&news=1](http://www.bbc.co.uk/mediaselector/check/media/video/otdvideo/61/04/20/8665_20-04-61?size=4x3&bgc=6699CC&nbram=1&nbram=1&bbram=1&news=1)
Which plays just fine without crashing.

I'm going to see whats happening about this bug in the firefox plugin forums.

---

### Post by eggdeng on 2007-04-17
BBC headlines play for me on Edgy using the media player plug-in rather than realplayer. gxine will play just about everything else, including .ra and ,ram stuff from the BBC, Just tick gxine and gxine-plugins in synaptic.

---

### Post by klytu on 2007-04-22
> **eggdeng said:**
> BBC headlines play for me on Edgy using the media player plug-in rather than realplayer. gxine will play just about everything else, including .ra and ,ram stuff from the BBC, Just tick gxine and gxine-plugins in synaptic.

I installed Fiesty on a spare hard drive this weekend. BBC videos also play flawlessly for me so far using the media player plug-in instead of realplayer. I used the default totem firefox plugin after installing the gstreamer multimedia codecs: ```
sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
``` In fact, after installing Flash, and the plugins/codecs above just about all imbedded Firefox video now plays for me in Fiesty without doing anything else. I might not even have to bother installing realplayer.

---

### Post by thomaswp on 2007-04-23
Almost fantastic!  I took out Realplayer and installed the packages using your code above.  I then installed the mplayer plugin.

Now real video from the BBC looks like it is goigng to work but I just get audio - no video.

This is better than the realplayer plugin but when I click on "View in realplayer" I get the same problem - no video at all.  This happens in Beryl and Metacity.

Any clues?  I'd love to get this working.

Later:  Tried the totem-mozilla plugin (unistalled the mplayer one) and now it tells me I have "no plugin" for realplayer.

---

### Post by klytu on 2007-04-23
> **thomaswp said:**
> Almost fantastic!  I took out Realplayer and installed the packages using your code above.  I then installed the mplayer plugin.

Now real video from the BBC looks like it is goigng to work but I just get audio - no video.

This is better than the realplayer plugin but when I click on "View in realplayer" I get the same problem - no video at all.  This happens in Beryl and Metacity.

Any clues?  I'd love to get this working.

Later:  Tried the totem-mozilla plugin (unistalled the mplayer one) and now it tells me I have "no plugin" for realplayer.

I didn't try RealPlayer in Fiesty with BBC yet, but others have reported the same issue. To clarify, when using the default totem-mozilla plugin In Fiesty, I chose viewing with Windows Media Player on BBC, not RealPlayer. Then the news video loads without a problem with the totem-mozilla plugin.

---

### Post by thomaswp on 2007-04-24
Aaaah.  I see.  THANK YOU for that. 

And I can now see Windows media reports from the BBC which is excellent (some of the time).

At times I get audio and a black screen.  If I move the window the video appears if I am lucky!

---

### Post by klytu on 2007-04-25
> **thomaswp said:**
> Aaaah.  I see.  THANK YOU for that. 

And I can now see Windows media reports from the BBC which is excellent (some of the time).

At times I get audio and a black screen.  If I move the window the video appears if I am lucky!

Yeah, Windows media can create another set of issues. In Dapper, I get best results with the mplayer-firefox plugin for Windows media, but the playback is still buggy. Many times a WIndows media stream will begin to load and then stop or it will appear to load and reload repeatedly.  A workaround that corrects these behaviours for me  almost every time is to go to fullscreen mode while the Windows media stream is loading. If I wait a couple of seconds, normal playback begins and then I can either keep watching in fullscreen mode or go out of fullscreen mode and playing will continue. 

With BBC in Dapper, I still get best results using Real Player and launching stand alone. In Fiesty, I have had good results so far with no need of any workarounds using just the totem-mozilla plugin and viewing BBC streams using Windows Media.

---

### Post by dolphinholmer on 2007-04-27
I received this email reply from the BBC:

Thank you for your email.

Our technical team is currently investigating problems that Linux users have been having with the News Player.

We are working hard to resolve outstanding issues following the relaunch of the News Player and unfortunately I cannot say at when this might be resolved.

Regards,

News Player Team

---

### Post by Bengaul on 2007-05-07
> **tom56 said:**
> The latest Realplayer available in the commercial repo fixes this.

1. Go to "Applications"->"Add/Remove"
2. At the top right select "Third Party Applications" from the drop-down box.
3. Untick Realplayer, click yes to any questions then click apply.
4. Now retick Realplayer, again clicking yes to any questions then click "Apply"

Essentially what you are doing is making sure "commercial" is in your sources.lst, but if you don't know what sources.lst is then the above is an easy way to do it.

Thats all very well, but even with Commercial in the sources.lst, it still does not pick up Realplayer!!

---

### Post by tom56 on 2007-05-07
Yeah, the commercial repo no longer has Realplayer in with Feisty. I think it's still there in Edgy though.

---

### Post by itsjustarumour on 2008-01-14
> **phollands said:**
> Toms' solution did not work for me. 

Realplayer crashes still when watching BBC News Videos.

Something is going way wrong with realplayer which is outside of the control directly of the Ubuntu Team. (Proprietary Code). You can see all the gory details if you open a terminal console; and then start firefrox from a  bash shell. 

Then select a BBC News video to watch from within the browser.
When the reaplayer stuff starts to go wrong, lot's of technical information appears on the screen - and then realplayer does a core dump.

There are complaints about :
 Attempting to add a widget with type HXPlayer to a container of type HXBin, but the widget is already inside a container of type HXBin, the GTK+ FAQ at [http://www.gtk.org/faq/](http://www.gtk.org/faq/) explains how to reparent a widget.

There are many many warnings about the window set sizes being invalid. The BBC site is defintely helping to trigger a bug. Some old Videos of square proportions still work. e.g. 
[http://www.bbc.co.uk/mediaselector/check/media/video/otdvideo/61/04/20/8665_20-04-61?size=4x3&bgc=6699CC&nbram=1&nbram=1&bbram=1&news=1](http://www.bbc.co.uk/mediaselector/check/media/video/otdvideo/61/04/20/8665_20-04-61?size=4x3&bgc=6699CC&nbram=1&nbram=1&bbram=1&news=1)
Which plays just fine without crashing.

I'm going to see whats happening about this bug in the firefox plugin forums.

Hi,

Did you ever get to the bottom of this problem?  

itsjustarumour

---

### Post by eggdeng on 2008-01-14
I think you're on a hiding to nothing with realplayer on the BBC. Most people get better results using the Mplayer plugin & choosing the W*nd*ws Media Player option. 
The trick is to make sure to remove the totem plugin (and the vlc plugin if present). (I also think logical positivism did a pretty good job on metaphysics.)

---


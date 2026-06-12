---
title: "HOWTO: Watch Stage6 DIVX movies"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by sagui on 2007-05-04
This is my first time HOWTO, so understand if my instructions are not the best/most efficient.

Anyways, Stage6.com is a new video hosting website, much like youtube and all the others.  What sets it apart is that it uses the DIVX codec and offers a special player to play the vidoes.  Of course once again the Linux community is left out, because the player is Windows only.  But here is how I got it to work:

First, I use Ubuntu and Firefox.  I don't know what the Kubuntu equivalent is, nor do I know whether this works under any other browser.  Further mPlayer is my player of choice, but I haven't gotten it to work yet using that particular player.  I used the Media Player Connectivity workaround so that I could keep mPlayer as my default player for all other video formats.  But I digress:

I first got the Media Player Connectivity plugin for firefox (simply google and install).  This causes firefox to launch an external media player for whatever video you're playing.  If you want to stream on the web page just hit the "x" button on the top right of the black video placeholder.  

Next, use Synaptics (System -> Administration -> Synaptics Packet Manager) and install:

gstreamer0.8-plugins
gstreamer0.8-xvid
totem-gstreamer
(totem-mozilla)  (only install this package if you want to skip the media player connectivity part)

Now after the installation is complete, go to Firefox and edit the preferences for Media Player Connectivity (Tools->Add-ons->Media Player Connectivity->Preferences).  Now check the box next to DIVX and in the text box next to it type: "/usr/bin/totem" (without the "").  Click okay.

Now, go to the stage6 video of your choice, click on the play button of the mock up video still.  What you should see now is a black rectangle with a "play" button in the biddle.  Clicking the button should open totem, which in turn should be showing the video you selected.


Now you should be all set.  I'm sure this is not the most efficient way to do it, but it works for me.

---

### Post by Deep Dish on 2007-05-06
I am able to view video's from Stage6 DIVX, however there is no sound from the streamed video's.

Is there something I overlooked?

---

### Post by Deep Dish on 2007-05-06
> **Deep Dish said:**
> I am able to view video's from Stage6 DIVX, however there is no sound from the streamed video's.

Is there something I overlooked?

Nevermind, I managed to get sound by using VLC instead of Totem as the default Stage6 DIVX player.
Simply change the path in the Media Player Connectivity plugin for DiVX to: **/usr/bin/wxvlc**

---

### Post by saxophobe on 2007-05-07
I used this method to be able to view DIVX clips online and it's working great!

Thanks very much for the great set of instructions!  :) 

sax

---

### Post by epique on 2007-05-08
hi thanks for the tutorial it was helpful. it work on the stage 6 site but the problem ive found is when you try to load a video from another site [www.tv-links.co.uk](www.tv-links.co.uk) for example it spits up this error.

Totem could not play 'http://www2.tv-links.co.uk/link.do/4/2181/3120/21610/33733/once/599868ae121e1ff411b42203235d26f5b95d8f2/go.divx'.
The connection to this server was refused.

im fairly new to Linux and don't even know where to look to try and fix this problem. if any one could help it would be appreciated

---

### Post by mrgnash on 2007-05-11
> **epique said:**
> hi thanks for the tutorial it was helpful. it work on the stage 6 site but the problem ive found is when you try to load a video from another site [www.tv-links.co.uk](www.tv-links.co.uk) for example it spits up this error.

Totem could not play 'http://www2.tv-links.co.uk/link.do/4/2181/3120/21610/33733/once/599868ae121e1ff411b42203235d26f5b95d8f2/go.divx'.
The connection to this server was refused.

im fairly new to Linux and don't even know where to look to try and fix this problem. if any one could help it would be appreciated

Seconded.

---

### Post by sagui on 2007-05-12
> **epique said:**
> hi thanks for the tutorial it was helpful. it work on the stage 6 site but the problem ive found is when you try to load a video from another site [www.tv-links.co.uk](www.tv-links.co.uk) for example it spits up this error.

Totem could not play 'http://www2.tv-links.co.uk/link.do/4/2181/3120/21610/33733/once/599868ae121e1ff411b42203235d26f5b95d8f2/go.divx'.
The connection to this server was refused.

im fairly new to Linux and don't even know where to look to try and fix this problem. if any one could help it would be appreciated

I'm not sure why it didn't work and unfortunately I can't check it, because that particular video is down.  i tried another and it worked fine.  Can you give another example, maybe not a direct link, but rather tell me the show name, season and episode?  Maybe I can help you out

---

### Post by dizee on 2007-05-12
Thank you for this tutorial, works perfectly now for me.

---

### Post by Skylara on 2007-05-14
> **sagui said:**
> I'm not sure why it didn't work and unfortunately I can't check it, because that particular video is down.  i tried another and it worked fine.  Can you give another example, maybe not a direct link, but rather tell me the show name, season and episode?  Maybe I can help you out

I am having the same issue with Totem, and when I try using VLC with the addon pref changed to wxvlc, it fails to load at all.  It's a repeatable problem with the movie [Flowers in the Attic]("http://tv-links.co.uk/show.do/4/2366") .

Flowers in the Attic is a new addition to the site, but I loaded it up on my Windows XP laptop (just now) and it works just fine, so I know that the file or DivX Stage 6 is not the problem.  Just can't get it working on Ubuntu on my desktop :cry:

---

### Post by flope on 2007-05-14
Great! it works for me using VLC ("/usr/bin/X11/vlc"). Thanks for the tutorial!
Ubuntu 7.04 64-bit.

> Flowers in the Attic is a new addition to the site, but I loaded it up on my Windows XP laptop (just now) and it works just fine, so I know that the file or DivX Stage 6 is not the problem. Just can't get it working on Ubuntu on my desktop 

hmmm.... When you click in some of the show in TV links, there is indicated where the movie is hosted or (where they got it). In Flowers in the Attic case, it is hosted by: DivX Stage6. So, visit the site to see it.

But I don't know, why it is not working directly from TV Links?
I tried other shows and they do not work.

Can we reproduce other type of formats like flash in VLC? is there any pluggin for that? If it so, it help me a lot, because I cannot reproduce youtube videos in the 64bit ubuntu. (of course there is other elaborated methods to do it).

---

### Post by Skylara on 2007-05-14
There is another thread basically related to DivX in Ubuntu [HERE]("http://ubuntuforums.org/showthread.php?p=2655306#post2655306").

Stage 6 videos play fine now for me thanks to that thread and this one.  Downloaded DivX videos play fine as well.  The only issue I am still having is that Stage 6 DivX videos refuse to play for me when I try and play them from [TV Links]("http://tv-links.co.uk").

As I said in the other thread, it could just be an issue with the way the videos are being linked from TV Links.  I'm going to try to uninstall/reinstall and/or compile my mplayer as suggested on the other thread and see if that helps.

Still could use someone that can see Stage 6 hosted DivX shows and videos from TV Links in Ubuntu (in any player) to try and help me out with this though.

---

### Post by Skylara on 2007-05-14
> **flope said:**
> hmmm.... When you click in some of the show in TV links, there is indicated where the movie is hosted or (where they got it). In Flowers in the Attic case, it is hosted by: DivX Stage6. So, visit the site to see it.

I've tried that and, for some reason, I can't hardly ever find the movies from the sites that say are hosting them.  I did find Flowers... but that's the first one I've EVER found when I've gone directly to a host site for the video.

> **flope said:**
> Can we reproduce other type of formats like flash in VLC? is there any pluggin for that? If it so, it help me a lot, because I cannot reproduce youtube videos in the 64bit ubuntu. (of course there is other elaborated methods to do it).

I did a *uname -a* for the other thread I was posting on related to this issue to find out if my Dapper was 32 or 64 bit.  Here's what it returned: *Linux green-desktop 2.6.17-11-386 #2 Tue Mar 13 23:30:30 UTC 2007 i686 GNU/Linux*

Since I don't see a 32 or 64 in that string, I have no idea which mine is lol.  Yes, I'm a Ubuntu noob.  Anyhow, I can play Flash from most anywhere just fine... from YouTube, Flash ads on sites, and even from TV Links.  I just had to download the [Media Player Connectivity plug-in]("https://addons.mozilla.org/en-US/firefox/addon/446?id=446") from Firefox like this How-To suggested for the DivX playback and the mplayer from Synaptic (see [this thread]("http://ubuntuforums.org/showthread.php?t=396569") for more information on how to get that all set up).

---

### Post by iamlost on 2007-05-17
It works fine with me that only problem i have is i can't seem to have the ability to jump about on the movie with the slider at the bottom only play and pause. I doubt there is a solution to this because it's be being streamed but if there was it would be great i'm using totem to watch it btw.

---

### Post by sagui on 2007-05-18
> **iamlost said:**
> It works fine with me that only problem i have is i can't seem to have the ability to jump about on the movie with the slider at the bottom only play and pause. I doubt there is a solution to this because it's be being streamed but if there was it would be great i'm using totem to watch it btw.

Yeah, I've been trying to figure this one out myself.  I tried the VLC method and it seems at least there you are able to fast forward (of course only as far as the stream is already downloaded), but no rewind.

I don't know enough about this to say whether this is the nature of the stream or whether both totem and vlc are incapable of handling that.  Does anyone know whether the downloadable windows DIVX player can do that?

---

### Post by Tyltyl on 2007-05-19
I could see the movies on Stage6 just fine without Media Player Connectivity, by using the mplayer dvx plugin.
Today though this doesn't work anymore, the plugin is still in the right directory but it doesn't show up in the about:plugin page.
The Totem DIVX plugin works fine.
What happened?

EDIT: Solved, apparently I had to change the last 4 options in mplayer plugin preferences.

---

### Post by RabidDawgr on 2007-05-19
> **sagui said:**
> Yeah, I've been trying to figure this one out myself.  I tried the VLC method and it seems at least there you are able to fast forward (of course only as far as the stream is already downloaded), but no rewind.

I don't know enough about this to say whether this is the nature of the stream or whether both totem and vlc are incapable of handling that.  Does anyone know whether the downloadable windows DIVX player can do that?

The downloadable DIVX player for windows downloads the video and plays as its downloading...you can even choose to save the file to a folder. 

I noticed that using the totem plugin it streams it live... heh its fine most of the time but if there is a lot of motion it gets really choppy due to the higher bitrates in fast movements, unfortunately im not aware of any linux application or codec that downloads the file while playing.

---

### Post by Lihaässä on 2007-05-29
Thanks for the help

---

### Post by ske1fr on 2007-05-30
Nice work sagui, I can confirm this works in Kubuntu Dapper Drake by installing the gstreamer bits and the Media Player Connectivity extention for Firefox. I configured the extention to use vlc and it works perfectly for the vid I watched from Stage6, AND the one from TV Links!  

Respect!

---

### Post by Janzuka on 2007-05-30
This howto works perfectly, and was simple enough - even for me ;)
Therefore, thank you sagui!

---

### Post by -X- on 2007-05-31
I went the mozilla-mplayer route. For some strange reason this is now broken after a feisty reinstall. Mplayer buffers about 3% (as normal), plays a split second of audio and video and then keeps on buffering until it reaches 99% and then it just stops. It might have something to do with totem crashing when trying to play an mp3 file... Anyone?

---

### Post by sagui on 2007-05-31
I had the same thing happen to me, which is why I came up with this workaround.

I tried to fix mplayer by compiling it from source, but for some reason I can't compile it, although I have all the required repos.

---

### Post by benjy on 2007-06-14
Just to throw in my two pence, it seems as though I needed to do far less than anyone here.

I've been using ubuntu for some time now and had recently broken my system (well... it wasn't broken but... fancied a nice clean install, okay I admit it - I started playing around with gutsy - which by the way has some nice new features but I don't want to use it permanently just yet) so wanted to do a nice new Feisty install.

My previous system had slowly been upgraded from Hoary through to edgy so I thought a fresh install would be a good idea...

Aaaanyway, where was I... oh yes. I wanted to test out this newfangled detection process for proprietary codecs so I promptly asked totem to play an mp3 file. Up comes a new dialog offering me three (or perhaps four...) options for codecs, all were gstreamer bar one for ffmpeg. I selected two (ffmpeg and gstreamer ugly) allowed them to install and happily then played my mp3.

Later, whilst browsing tv-links, I happened upon a stage6 provided link. Expecting it to just stop and do nothing I was astounded to see it began to play - and in glorious high quality divx technicolour! No choppyness, bad sound or pixelation - just high quality video.

I think it important to note also that my computer is no powerhouse, an old agp GeForce fx5200 is all that pings my screen, though I do run swiftfox as for the me the speed increase is noticeable.

Things needn't always be complicated...

---

### Post by rainwalker on 2007-06-18
I followed your instructions and it looks like it should work, but when I try to play the movie at [http://www.filmzzz.com/film.php?filmid=11](http://www.filmzzz.com/film.php?filmid=11) Totem says
> 
Totem could not play 'http://divx-690.vo.llnwd.net/stage6vid/1254065.divx'.
Cannot play this file over the network. Try downloading it to disk first.

This doesn't seem to make sense, though, because normally the video would be playing in the DivX web player on the page anyway.
Any ideas?

---

### Post by diablofatt on 2007-06-19
I followed the step's exactly. Although I think it should be known I am pretty newb to Linux in general and used and older Ubuntu flavor some time ago. 

I go to TV link's and I try to run the DivX movie's.. For example: [http://www.tv-links.co.uk/link.do/3/3588/5445/34266/52203](http://www.tv-links.co.uk/link.do/3/3588/5445/34266/52203) - Previously I had gotten a "Cannot locate file" in my Mplayer winodw. Now I get a picutre of a red X and nothing happens. The X was after I retraced my installation step's. So I search for more...

I come across [http://www.tv-links.co.uk/link.do/4/2431/3519/23504/39746](http://www.tv-links.co.uk/link.do/4/2431/3519/23504/39746)

I noticed its a Stage 6 so I click the first link. The first window that pop's up plays the movie. I right click and select Open with MOvie Player (hoping for better quality and then i get "An error has occurred. Cannot locate file" I go back to my original link and now where the video had played before (in the first window) wont do anything and I get the red X. 

Anything better then the suicide solution would be nice. Thanks for reading.:KS

---

### Post by Gremlinzzz on 2007-06-19
Thxs skylare
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
worked for me i can now watch divx on line.nice

---

### Post by benjy on 2007-06-24
diablofatt: The red x means it has been removed from stage6, by the sounds of it you have it working in firefox.

---

### Post by cookiemonster0774 on 2007-06-24
Thanks for the tips. I being a complete Linux virgin need all the help I can get.
 However, after following all the instructions I started getting sound (which I did not before) but still   no video. I could really use a little more help. Thanks

---

### Post by DannyG on 2007-07-02
Keep in mind, the errors you are reporting could be the result of deleted videos.

Stage6, afterall, is hosting copyrighted material...

---

### Post by cyrano_says on 2007-07-02
i was messing with all possible options.. finally one worked

configure media player connectivity to use gmplayer /usr/bin/gmplayer for divx 
and disable it

---

### Post by deaz on 2007-07-05
Edit: Nevermind

---

### Post by Soglad on 2007-07-05
I hope someone is able to tell me what my problem is here because it's really confusing.

I am using Kubuntu (the latest version) and have all the codecs, the Media Player Connectivity thing for Firefox and Mplayer, but when I go into the Media Player Connectivity add-on and try to choose a program for Divx, I can't see a Divx option listed! All I have is Real Media, Windows Media, Quicktime, Playlist (pls/m3u), mp3/acc, OGG theora, Flash, Wave/Midi/Au/Aif, Nullsoft Video, Shockwave and Authorware.....no Divx option. Can someone sort this out for me? I hate having to reboot the computer and use Windows for Divx!

Thanks in advance,

Dav.

---

### Post by Soglad on 2007-07-06
Anyone? Please?

---

### Post by Soglad on 2007-07-07
Never mind, fixed it! :P

---

### Post by dmorand on 2007-07-18
I was messing around with MediaPlayerConnectivity and then all of a sudden I could watch divx movies on stage6, but on tv-links they just sit there trying to load.  Any suggestions?

---

### Post by dmorand on 2007-07-20
Any ideas?

---

### Post by adam0s on 2007-08-06
benjy  ffmpeg fixed the problem. thanks

---

### Post by Kynan on 2007-08-20
Is there a definitive answer now? is it assumed that the workaround indeed works and it is just bad links from tvlinks or stage6 that is causing this trouble? 
I have also been experiencing the same frustration, hope this fix will be in gusty.

---

### Post by Kaldir on 2007-08-22
Worked great for me!  Thank you!:popcorn:

---

### Post by neo.patrix on 2007-09-23
Hi

Totem gives me location not found error when i click on STage6 link, any ideas?

---

### Post by buu700 on 2007-09-23
I don't know about the Totem problem, but stage6 worked perfectly for me after:

sudo aptitude install vlc vlc-plugin-esd mozilla-plugin-vlc

and then installing all the gstreamer codecs from Add/Remove programs

---

### Post by aeto on 2007-09-24
I don't know if this has been posted before but with nothing else other than the simple mplayerplug-in package (no vlc, xine, totem and all that), all Mplayer codecs, & Firefox/Opera (sorry Konq I'm unsure), getting divx AND stage6 to work flawlessly is pretty simple.

```
sudo nano ~/.mozilla/firefox/pluginreg.dat
```

Look for the first section that looks something like:

```
a href="http://mplayerplug-in.sourceforge.net/">mplayerplug-in</a> 3.45<br>$
mplayerplug-in 3.45:$
24
0:video/mpeg:MPEG:mpg,mpeg:$
1:audio/mpeg:MPEG:mpg,mpeg:$
2:video/x-mpeg:MPEG:mpg,mpeg:$
```

It'll not be the same, just look for the first section that has an mplayerplug-in line. Notice the **24**, and also the numbering sequence. These won't be the same for you. After the last number in that section, let's assume it's *23* (total would be reported as **24** like above), add a new line below:

```
*24*:video/divx:DIVX Video:divx:$
```

Then go back up to add 1 to the **24** so it becomes **25**. Save it, CTRL+O (or depending on which editor you used) and exit. For Opera you just need to install opera-mplayer-plugin & not the gecko one. Fire up the Firefox, go to stage6.divx.com and carry on your illegal habits ;) 

Magic from: [http://forums.divx.com/forum/viewTopic.php?id=4128](http://forums.divx.com/forum/viewTopic.php?id=4128)

---

### Post by Gremlinzzz on 2007-09-24
I just put these commands in terminal
cd /usr/lib/firefox/plugins/
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.xpt
sudo ln -s /usr/lib/mozilla/plugins/mplayerplug-in-dvx.so
:guitar:

---

### Post by Griff on 2007-09-30
Everything worked without a hitch for me.  Tv-links included.  Thanks.
I'm using feisty gnome.
-Griff

---

### Post by Rob-e on 2007-10-03
hey guys, before i found this thread i was using the downloadhelper extension to get the movies, and there are usually 2 options of what to download, there is go.divx and (numbers).divx (ex:235896.divx)

sooo, when i go to use this media player extension sometimes it opens go.divx, which is when i get the error in totem, and other times i get the numbers and it works

so maybe that will help... this is on tv-links btw

---

### Post by sgtsnoopy on 2007-10-13
After a bit of trial and error I have finally found a way of watching all (well all the ones i've tested) stage6 videos on tv-links.

All stage6 videos have the url: "http://video.stage6.com/[number]/.divx" where [number] is the video id.  On tv-links, the stage6 videos have an url similar to "http://divx-745.vo.llnwd.net/stage6vid/[number].divx" which can easily be seen when you attempt to play the video in totem.  Even the video's that come up with the "go.divx" contain that number somewhere in the url.

To play the video in totem or vlc, you need to put the stage6 url into the "open url" or "open network stream" line of your player.  For example, "http://video.stage6.com/1726444/.divx" will play a Torchwood episode hosted on tv-links which can't be found by searching stage6 for it (even though it's hosted there).  On tv-links, this url attempts to play from "http://divx-745.vo.llnwd.net/stage6vid/1726444.divx" but won't play in vlc or totem like that.  When I added the number at the end to the stage6 url as shown above, it played immediately with no issues and no lag in vlc (though it was a little choppy and buffered frequently when using totem).

As I said above, I've tried this with about 10 or so random stage6 videos on tv links and it has worked with all of them.  It is a bit of a pain to do, but I'm sure someone wiser than me can write a script or something to automate this task a little.  And as I stated above, the video's hosted on stage6 seem to play much better on vlc than totem (well for me anyway), so I am writing this from a vlc perspective, but  I did test a couple of the videos in totem using this method and it worked on there too.

I hope the above makes sense, as I am a little tired.  I hope this helps anyone having issues.

EDIT - The url in the address bar on stage6 ISN'T the same as the url the video plays from.  The stage6 url I have put above is where the video actually streams from, not necessarily the url that appears in the address bar for the page that contains the video you want to watch.

EDIT 2 - Also, I got the whole thing working originally by following the excellent instructions at the start of this thread.  Kudos to the author, you've helped me immeasurably.

---

### Post by Rob-e on 2007-10-25
well what sucks if the main guy on tv-links was arrested so forget everything mainly

---

### Post by SM0k3 on 2007-10-31
Worked great only thing I had to do differently was use the VLC player, I wasn't getting any sound in Totem. :)

---

### Post by MACRI on 2007-11-11
having no problems viewing/listening to the movies but i find them to be very choppy even if i download them and when i do it on my windows partition they run smooth and well dvd quality... any ideas as to why???

---

### Post by andykimbrey on 2007-12-28
Just to say I'm using 7.10 Gutsy, clean installation. Followed this HowTo and it worked perfectly first time. Great guide, many thanks!

Andy Kimbrey

---

### Post by cherry316316 on 2008-01-02
i installed divx for linux from the divx website, but I am not able to play
the divx for linux as I am not able to locate where the hell it has installed the run file 
I only see *.h files :(( 
any of you has tried divx for linux ?

---

### Post by bill_greene on 2008-01-02
> **cyrano_says said:**
> i was messing with all possible options.. finally one worked

configure media player connectivity to use gmplayer /usr/bin/gmplayer for divx 
and disable it
 
Same thing happened to me. Only I have it enabled . Works great finally ](*,)

---

### Post by PhatKat on 2008-06-23
> **SM0k3 said:**
> Worked great only thing I had to do differently was use the VLC player, I wasn't getting any sound in Totem. :)

Hi am having the same problem - can someone guide a buntu newbie on how to set VLC to play Divx??

---


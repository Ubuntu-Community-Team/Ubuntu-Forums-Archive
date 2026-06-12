---
title: "Why can't we configure mplayer/totem/vlc plug-ins to play flash vid?"
date: 2009-05-17
forum: Multimedia Software
---

### Post by ticket on 2009-05-17
Full screen flash video playback by the adobe flash plug-in is awful, often a slide show on less powerful machines.  Yet mplayer, etc can play full screen streaming flash video really well.  Why can't we configure the mplayer/totem/vlc browser plug-ins to take over the job of playing streaming flash video from the adobe plugin?

---

### Post by ticket on 2009-05-22
Slight bump for any views ...

---

### Post by monraaf on 2009-05-22
Most of the "flash video's" you see on websites such as YouTube
consist of two parts. The player itself which is made with
Adobe Flash, and the flv file which is the video itself.
The players on websites as YouTube are designed in such a way
that they know from what location to download the actual video
file from. 

If you want to replace the Adobe Flash player (which is indeed
crappy for video playback) with mplayer there are several
problems, let me just name two.

First is that flash is used for more than just playback of flv
files. Some websites have whole interactive user interfaces in
flash, obviously none of the media players can handle that. So
how do you determine that a flash object is merely used as a
player for flv files or that it's used for something entirely
else? Unfortunately you can't do that in a general way.

The second problem is that in order for mplayer or any other 
media player to playback an flv file it must first know the url
of the file, unfortunately each website has a different method
for generating the url of the actual video file, which their own 
video player knows about, but mplayer obviously does not. So
there's no general way to get the url of the flv file.

Now there are several Greasemonkey scripts around that rewrite 
web pages so that the video playback can be done with a normal
video player.  One of those scripts is You Totem which allows
you to play the video's on YouTube with totem.

[http://userscripts.org/scripts/show/25481](http://userscripts.org/scripts/show/25481)

This script only works on YouTube, now there maybe other 
Greasemonkey scripts for other websites around, but again
there's no generic way to have it all work for all sites.

I know it sucks, but that's the way it is.

---

### Post by ticket on 2009-05-26
Hi monraaf,

Thanks for your thoughts.  Frankly, I am only interested in streaming video playback, so a plug-in that fails to handle flash games and adverts is fine by me.

As you rightly point out, there are some greasemonkey scripts that find the video url in the YouTube web page script and feed that to mlayer or totem (HQTube is another).  These work quite well, except that they can fail whenever YouTube decides to rename its streams, and are specific to the YouTube site.

What is needed is a way to generically detect the url of an incoming video stream. The firefox plug-in called NetVideoHunter does this quite well, but it cripples itself by using its own flash player instead of invoking mplayer or totem. So it's only good for downloading, not viewing.  I am trying to see if I can fix this myself, but java and the firefox api are new stuff to me. Could be while ...

Another way that works quite well is by using the flashgot firefox extension. It can detect a stream and you can then get it to call mplayer (or anything else).  It's ability to detect streams isn't quite as good as NetVideoHunter though.  It's my best solution yet, but a fixed up NetVideoHunter would be the best solution.

There's some more musing over this on:
 
[http://ubuntuforums.org/showthread.php?t=1137424](http://ubuntuforums.org/showthread.php?t=1137424)

---

### Post by monraaf on 2009-06-05
Interesting, it looks like netvideohunter waits for the original site specific flashplayer to play the flv file and then uses some kind of firefox snooping function to capture the url of the flv file.

I'll try to look into it, when I have time.

---

### Post by monraaf on 2009-06-05
Ok, after a little modification I got the netvideohunter extension working with the mplayer plug in.

You still need the crappy flash plug in though, because netvideohunter can only get the uri of the video file after playback is started with the original player. Besides some small issues it works pretty good. It even works on Vimeo.

I have attached a small patch, you have to apply it to the unzipped xpi.

Here's a howto:
```

mkdir Netvideohunter && cd Netvideohunter
wget https://addons.mozilla.org/en-US/firefox/downloads/latest/7447/addon-7447-latest.xpi
unzip netvideohunter-0.4.2-fx.xpi
patch -p0 < patch.txt
zip -r netvideohunter-0.4.2-fx.xpi chrome
firefox netvideohunter-0.4.2-fx.xpi

```

Here's a screenshot of a YouTube HD video.

[[IMG]http://img268.imageshack.us/img268/1787/screenshotmovieplayer.th.jpg[/IMG]](http://img268.imageshack.us/i/screenshotmovieplayer.jpg/)

---

### Post by jgor on 2009-06-05
In FireFox there is an extremely useful add on ["Video DownloadHelper"]("https://addons.mozilla.org/en-US/firefox/addon/3006"). As of yet I have been able to download over 10GB of South Park from streaming video and many Mp3s from streaming audio on MySpace and Face Book pages. The downloaded .flv files play smoothly in totem mplayer and vlc. Sometimes, however the video will play slightly faster or slower than intended on some files, making the audio seem late or early.

---

### Post by ticket on 2009-06-05
> **monraaf said:**
> Ok, after a little modification I got the netvideohunter extension working with the mplayer plug in.


Great work, monraaf!  I must try this out.

Edit:  Yes, it works!

---

### Post by ticket on 2009-06-06
Monraaf, 

Could you say something about how you managed to do this? I am not at all familiar with the firefox api stuff or javascript.

Another question:  although you say you still need to call the flash player to detect the streams, when 'play' is pressed, is the flash player and the mplayer plug-in running at the same time? If so, this might swallow a lot of bandwidth and cpu. However, I suspect that isn't the case, as on pressing 'play' I just get the mplayer window immediately. Did you somehow stop the flash playback once it started?

Anyway, great job!

---

### Post by monraaf on 2009-06-06
> **ticket said:**
> Monraaf, 

Could you say something about how you managed to do this? I am not at all familiar with the firefox api stuff or javascript.


Well I'm no expert on the firefox api myself either. Basically what i did is modify the embed tag from the netvideohunter extension which originally embedded their flash player. Also, it appears to me that the original netvideohunter extension was sending out statistics of video's you download to some website, I commented out that stuff also ;)

> 
Another question:  although you say you still need to call the flash player to detect the streams, when 'play' is pressed, is the flash player and the mplayer plug-in running at the same time? If so, this might swallow a lot of bandwidth and cpu. However, I suspect that isn't the case, as on pressing 'play' I just get the mplayer window immediately. Did you somehow stop the flash playback once it started?

Anyway, great job!

I don't know if we're talking about the same flash player here. So let me clarify.  The flash player provide by the netvideohunter extension isn't running at all with this modification. But the flash player provided by the video site (i.e youtube, vimeo) and which is needed to capture the url is.

---

### Post by ticket on 2009-06-06
I understand. The original web page is where the stream url is grabbed from.

Instead of playing the stream using an embedded player (e.g. like mozilla-mplayer, gecko-mediaplayer, etc), how easy would it be to modify the program to fire up a non-embedded player instead (e.g. gmplayer, gnome-mplayer, mplayer, totem, etc) ?

Then we could get rid of the player window area.  The 'history' window for the visited media streams is all we then need, to either play the streams or save the video stream to disc.

---

### Post by lovinglinux on 2009-07-09
Never mind, I figure it out.

---

### Post by lovinglinux on 2009-07-09
> **ticket said:**
> I understand. The original web page is where the stream url is grabbed from.

Instead of playing the stream using an embedded player (e.g. like mozilla-mplayer, gecko-mediaplayer, etc), how easy would it be to modify the program to fire up a non-embedded player instead (e.g. gmplayer, gnome-mplayer, mplayer, totem, etc) ?

Then we could get rid of the player window area.  The 'history' window for the visited media streams is all we then need, to either play the streams or save the video stream to disc.

I'm trying to find ways to replace flash players with mplayer plugin. The best solution I could find is a Greasemonkey script. Check it out at the **[COLOR="DarkRed"]Flash Optimizatio[/COLOR]**n section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). Scroll down to the [COLOR="DarkRed"]Flash Replacements[/COLOR] topic. Unfortunately, it is site specific.

The Netvideohunter with the monraaf patch is an interesting solution, but not exactly what want. I would like to be able to see the video embedded, using gecko-mediaplayer. Anyways, I will look into the code of Netvideohunter and will try to create a new extension or a Greasemonkey script.

---

### Post by ticket on 2009-07-23
Yes, I agree that a fully embedded solution would be better.  

Adobe should deliver it, but obviously doesn't (why don't they stick mplayer inside their flash plug-in? After all, the source code is available!)

Netvideohunter with the monraaf patch works well, but you have to let the adobe flash player embedded on the web site to play in order for Netvideohunter to detect the stream.  I often just close the original web page once the stream has started. I can go back to the Netvideohunter 'play list' to watch the video at any time during a firefox session.  But as you say, too many key presses!

A solution that combines the website independence of Netvideohunter with the embedded solutions from greasemonkey scripts would be ideal, until this problem gets fixed.

Keep us posted on progress!  In the meantime, I have added my vote to the Adobe site to get this fixed, at:
[http://bugs.adobe.com/jira/browse/FP-1692](http://bugs.adobe.com/jira/browse/FP-1692)

---

### Post by Psumi on 2010-01-23
> **monraaf said:**
> Ok, after a little modification I got the netvideohunter extension working with the mplayer plug in.

You still need the crappy flash plug in though, because netvideohunter can only get the uri of the video file after playback is started with the original player. Besides some small issues it works pretty good. It even works on Vimeo.

I have attached a small patch, you have to apply it to the unzipped xpi.

Here's a howto:
```

mkdir Netvideohunter && cd Netvideohunter
wget https://addons.mozilla.org/en-US/firefox/downloads/latest/7447/addon-7447-latest.xpi
unzip netvideohunter-0.4.2-fx.xpi
patch -p0 < patch.txt
zip -r netvideohunter-0.4.2-fx.xpi chrome
firefox netvideohunter-0.4.2-fx.xpi

```

Here's a screenshot of a YouTube HD video.

[[IMG]http://img268.imageshack.us/img268/1787/screenshotmovieplayer.th.jpg[/IMG]](http://img268.imageshack.us/i/screenshotmovieplayer.jpg/)

And what if we get this?

```
patching file chrome/netvideohunter/content/netvideohunter/mediaList.js
patching file chrome/netvideohunter/content/netvideohunter/mediaList.xul
Hunk #2 FAILED at 31.
1 out of 2 hunks FAILED -- saving rejects to file chrome/netvideohunter/content/netvideohunter/mediaList.xul.rej
patching file chrome/netvideohunter/content/netvideohunter/overlay.js
```

There's a new version of that ext as well that you told me to download, so it's no longer... 0.4.2

---

### Post by texaswriter on 2010-01-23
To those having problems with the adobeflash-plugin, assuming it is the one in the repository of your respective version, have you tried compiling one from source or using a .deb or .apt from Adobe's website. <<--- That's a bit heretical I know, but that's usually what I do. 

Well, on my laptop, I did just reinstall Karmic, and I used the flash plugin from the repositories [instead of compiling my own]. So far have played some hd videos on [www.youtube.com](www.youtube.com) and have not had problems. Also, Hulu is playing fine as well. 

I might suggest that, if you are having problems with flash videos, it is perhaps a result of a video driver and/or configuration.

---

### Post by morgonzola on 2010-02-15
> **Psumi said:**
> And what if we get this?

```
patching file chrome/netvideohunter/content/netvideohunter/mediaList.js
patching file chrome/netvideohunter/content/netvideohunter/mediaList.xul
Hunk #2 FAILED at 31.
1 out of 2 hunks FAILED -- saving rejects to file chrome/netvideohunter/content/netvideohunter/mediaList.xul.rej
patching file chrome/netvideohunter/content/netvideohunter/overlay.js
```

There's a new version of that ext as well that you told me to download, so it's no longer... 0.4.2

YES i need some help with this also becuase this is the best workaround i have found as of yet. i really appreciate that monraaf made a script for us to use but it doesnt carry through with the newest version of netvideohunter. if someone could kindly modify the script or tell others how to it would be HUGELY appreciated. i would do it myself but when it comes to things like this i am reduced to the title of script kiddie. SO PLEASE!!! HELP A BROTHA OUT

---

### Post by monraaf on 2010-02-15
Download attachment, rename to netvideohunter-0.4.3-fx.xpi and open with Firefox. By default it should use Totem for playback.

---

### Post by morgonzola on 2010-02-15
> **monraaf said:**
> Download attachment, rename to netvideohunter-0.4.3-fx.xpi and open with Firefox. By default it should use Totem for playback.

oh my god you are a lifesaver. i hereby grant you 500 internets

---

### Post by morgonzola on 2010-02-15
> **morgonzola said:**
> oh my god you are a lifesaver. i hereby grant you 500 internets

you still get your 500 internets but i have one question... the plugin works fine and it uses totem for playback, but i lose all my controls and it only streams like one second of it and stops. is this a prob with my totem? or am i just doing something dumb

---

### Post by ticket on 2010-02-25
> **morgonzola said:**
> you still get your 500 internets but i have one question... the plugin works fine and it uses totem for playback, but i lose all my controls and it only streams like one second of it and stops. is this a prob with my totem? or am i just doing something dumb

I have managed to get the updated netvideodownloader to work with gecko mplayer.  With that package installed, you can configure Firefox to use it instead of totem.  netvideodownloader itself doesn't specify the player to use.

Totem may have troubles playing some youtube formats - at least it did 1 year ago.

An alternative to  netvideodownloader is to use flashgot.  It is able to detect streams the same way - the trick (I have yet to do) is to get it to fire up mplayer or totem instead of (or as well as) saving the stream as a download.

---

### Post by aston4 on 2010-02-28
Easy way to play Youtube videos is just open the youtube video in firefox, hit pause, and then in a termianl type "vlc /tmp/Flash*"

I guess this would work for Hulu, but I don't know where the Hulu player puts the stream as it downloads?

---

### Post by ticket on 2010-02-28
> **aston4 said:**
> Easy way to play Youtube videos is just open the youtube video in firefox, hit pause, and then in a termianl type "vlc /tmp/Flash*"

I guess this would work for Hulu, but I don't know where the Hulu player puts the stream as it downloads?

Yes, that method is always worth a shot. But there are some video feeds that either do not get stored in /tmp or, if they are, they are only stored in short segments that another player cannot use. Oh well, roll on html5 ?

---

### Post by yashaneiman on 2010-07-12
Thanks monraaf for your contribution.
Based on your work, I made another modified version of NetVideoHunter.
The install instructions are the same: rename the file extension to .xpi, and run with Firefox.

The differences are:

1. I applied the patch to the newer version 1.3 of NetVideoHunter, which has some additional features such as removing selected entries from the media list.
2. The Play button now opens the movie in a separate browser window. This has a couple of benefits if we are to use it as a regular online viewing alternative to Flash, rather than just a preview: 
  a. When the add-on recognizes a new stream, it will no longer stop the  playback of a previous one.
  b. Several movies can be loaded and watched simultaneously.
3. I changed the credentials of the add-on. This way, Firefox won't prompt for updates of the original NetVideoHunter, which would override our changes.

Disclaimer:
I'm not much of a web programmer, and this is a sloppy job. Some of the advanced features of the add-on are probably lost, e.g. configuring options for the player. 

Hope this helps. This is my first active experience with the open-source process!

---

### Post by lovinglinux on 2010-07-12
> **yashaneiman said:**
> 
2. The Play button now opens the movie in a separate browser window. This has a couple of benefits if we are to use it as a regular online viewing alternative to Flash, rather than just a preview:

You might want to take a look into an extension I'm developing that replaces the video on site: [https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

---

### Post by yashaneiman on 2010-07-26
> **lovinglinux said:**
> You might want to take a look into an extension I'm developing that replaces the video on site: [https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)
I'm sure your extension is helpful, but I needed a solution which is not site-specific. I don't suppose you'll be supporting Israeli TV sites any time soon ;).

By the way, seeing that YouTube is one of your supported sites, I noticed that it works quite well in Google Chrome, without any player replacements. Not very surprising given the affiliation, but nice to know. And I'd certainly like to know how they're doing it.

---

### Post by lovinglinux on 2010-07-26
> **yashaneiman said:**
> I'm sure your extension is helpful, but I needed a solution which is not site-specific. I don't suppose you'll be supporting Israeli TV sites any time soon ;).

By the way, seeing that YouTube is one of your supported sites, I noticed that it works quite well in Google Chrome, without any player replacements. Not very surprising given the affiliation, but nice to know. And I'd certainly like to know how they're doing it.

Experiences may vary. I have seen reports that Chrome works better and others that Firefox works better.

---

### Post by Alec006 on 2010-09-01
> **monraaf said:**
> Ok, after a little modification I got the netvideohunter extension working with the mplayer plug in.

You still need the crappy flash plug in though, because netvideohunter can only get the uri of the video file after playback is started with the original player. Besides some small issues it works pretty good. It even works on Vimeo.

I have attached a small patch, you have to apply it to the unzipped xpi.

Here's a howto:
```

mkdir Netvideohunter && cd Netvideohunter
wget https://addons.mozilla.org/en-US/firefox/downloads/latest/7447/addon-7447-latest.xpi
unzip netvideohunter-0.4.2-fx.xpi
patch -p0 < patch.txt
zip -r netvideohunter-0.4.2-fx.xpi chrome
firefox netvideohunter-0.4.2-fx.xpi

```Here's a screenshot of a YouTube HD video.

[[IMG]http://img268.imageshack.us/img268/1787/screenshotmovieplayer.th.jpg[/IMG]]("http://img268.imageshack.us/i/screenshotmovieplayer.jpg/")


Hi this sounds totally great but I'm a clomplete newie can yo explain me how to intall it thanks for you time!!!

---

### Post by Alec006 on 2010-09-02
> **yashaneiman said:**
> Thanks monraaf for your contribution.
Based on your work, I made another modified version of NetVideoHunter.
The install instructions are the same: rename the file extension to .xpi, and run with Firefox.

The differences are:

1. I applied the patch to the newer version 1.3 of NetVideoHunter, which has some additional features such as removing selected entries from the media list.
2. The Play button now opens the movie in a separate browser window. This has a couple of benefits if we are to use it as a regular online viewing alternative to Flash, rather than just a preview: 
  a. When the add-on recognizes a new stream, it will no longer stop the  playback of a previous one.
  b. Several movies can be loaded and watched simultaneously.
3. I changed the credentials of the add-on. This way, Firefox won't prompt for updates of the original NetVideoHunter, which would override our changes.

Disclaimer:
I'm not much of a web programmer, and this is a sloppy job. Some of the advanced features of the add-on are probably lost, e.g. configuring options for the player. 

Hope this helps. This is my first active experience with the open-source process!


can you do the same bur using VLC?
it would be great!!!:)

---

### Post by yashaneiman on 2010-09-05
> **Alec006 said:**
> can you do the same bur using VLC?
it would be great!!!:)

I tried at some point, but couldn't make it work and gave up. I agree that VLC is the best player for local files, but mplayer seems to do the job for online streams. Do you have a particular issue that requires VLC?

---

### Post by lovinglinux on 2010-09-07
> **yashaneiman said:**
> I tried at some point, but couldn't make it work and gave up. I agree that VLC is the best player for local files, but mplayer seems to do the job for online streams. Do you have a particular issue that requires VLC?

I agree. VLC plugins is not good. I recommend gecko-mediaplayer, which is mplayer based.

---

### Post by yashaneiman on 2010-09-19
A partially relevant update:
After a while, the wife got sick of Ubuntu altogether, because of the lags with flash content other than movies.
I ended up switching the old comp to Lubuntu, and I like it a lot. Non-movie flash content loads reasonably fast, many movies play well straight from the browser, and our modified NetVideoHunter takes care of the rest.

---


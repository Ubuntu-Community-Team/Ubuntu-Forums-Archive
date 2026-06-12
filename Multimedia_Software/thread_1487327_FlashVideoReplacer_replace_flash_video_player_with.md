---
title: "FlashVideoReplacer: replace flash video player with mplayer plugin (low CPU usage)"
date: 2010-05-18
forum: Multimedia Software
---

### Post by lovinglinux on 2010-05-18
I have released a Firefox extension, called [FlashVideoReplacer]("http://www.webgapps.org/addons/flashvideoreplacer"), that automatically replaces embedded flash video object with video/mp4 or x-flv, allowing to watch flash streaming content with a less CPU intensive plugin. 

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)
[https://addons.mozilla.org/en-US/firefox/addon/161869/](https://addons.mozilla.org/en-US/firefox/addon/161869/)

Stay tuned!

[IMG]http://tinyurl.com/2ezzlef[/IMG]

---

### Post by ZequeZ on 2010-05-19
This will totally be a Flash Killer for me. Videos are the only thing I still use Flash for. I will be subscribed, thanks ^^.

---

### Post by lovinglinux on 2010-05-20
Version 1.0.0 is available for download at the [extension site](http://flvideoreplacer-extension.blogspot.com).

I have decided to release it sooner, without adding additional sites to the compatibility list, but you can request new sites to be included by voting on the [extension site poll]("http://flvideoreplacer-extension.blogspot.com"). If the site is not included in the poll, then please send me an [e-mail]("http://lovinglinuxblog.blogspot.com/p/contact.html") or fill a feature request in the extension [Bug Tracker]("http://code.google.com/p/flvideoreplacer/issues/list") or post here on this thread.

Any suggestions or comments will be much appreciated.

---

### Post by xzero1 on 2010-05-21
Congratulations, nice work! Your plugin works for the most part but there are a few issues. It seems to use gstreamer not mplayer??? Some youtube videos (crackle) will still use flash to play. I will post the link. It may be a better idea to default to low or medium instead of high. Once again, good job.

youtube crackle video examples:
[http://www.youtube.com/show?p=UMu1inydRWc](http://www.youtube.com/show?p=UMu1inydRWc)[URL="http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9334667"]
[/URL]

---

### Post by lovinglinux on 2010-05-21
> **xzero1 said:**
> Congratulations, nice work! Your plugin works for the most part but there are a few issues. It seems to use gstreamer not mplayer???

Thank you. What I meant by mplayer is the x-mplayer2 mime type file. If you are using a gstreamer based plugin (totem), then it will use gstreamer framework, but if you are using an mplayer based plugin (gecko-mediaplayer), then it will use mplayer framework. Windows users will use either windows media player or quicktime.

I would try to change the title of the thread.

> **xzero1 said:**
> Some youtube videos (crackle) will still use flash to play. I will post the link. 

If the extension cannot find a compatible x-mplayer2 file, it will fall back to flash. Nevertheless, some types of pages (for instance user channels) won't work. I will wait for the link (the one provided is broken) to check if it is a bug, a compatibility issue or simply the lack of suitable alternative videos.

> **xzero1 said:**
> It may be a better idea to default to low or medium instead of high. Once again, good job.

You can change that in the extension preferences, in the cased of YouTube.

---

### Post by xzero1 on 2010-05-21
Sorry for the wrong link, it has been fixed. Crackle has its video site if that helps any [http://www.crackle.com/](http://www.crackle.com/)

---

### Post by lovinglinux on 2010-05-21
> **xzero1 said:**
> Sorry for the wrong link, it has been fixed. Crackle has its video site if that helps any [http://www.crackle.com/](http://www.crackle.com/)

Thanks. For now, the extension should work only with regular videos, not with featured channels like that. The main issue is that I need to see the video page code, in order to configure the extension to replace the video object based on the  id and fetch the mp4 video link accordingly. If the site has different video content pages, with different object ID values or link authentication, then I need to write a new code to identify them separately. 

I hope you understand the limitations I'm facing. I wish I could write an extension that would work on every site and every page, without needing to hack each code separately, but I don't have that skill yet.

Unfortunately, this is what I get when viewing that channel.

> This video contains content from Sony Pictures Movies & Shows, who has blocked it in your country on copyright grounds.

I have tried to access the content with a web proxy, but I haven't been successful so far. I don't want to use such resources, because I'm not sure that would be legal, even considering I'm not intending to watch or download the video.

I'm going to investigate if YouTube uses different code for each channel or not. If I can access a channel that is not blocked, then maybe I can write the necessary code for all of them.

---

### Post by lovinglinux on 2010-06-02
The first version of FlashVideoReplacer has been approved by Mozilla and is available through the Stable Channel now. New versions updates will be available through Firefox add-ons manager.

---

### Post by Cenoforums on 2010-06-20
Youtube has various quality options, 480p, 720p. When high quality is selected in the addon menu, which quality am I getting? the highest availabe *p?

---

### Post by zerojay on 2010-06-20
The plugin works fine on blip, but I can't get it to do anything whatsoever with Youtube at all. Youtube flash player still starts up and plays.

---

### Post by lovinglinux on 2010-06-20
> **Cenoforums said:**
> Youtube has various quality options, 480p, 720p. When high quality is selected in the addon menu, which quality am I getting? the highest availabe *p?

Click the FlashVideoReplacer icon in the status bar and select the quality of the video. To make it simple, I have provided only three options: HIGH, MEDIUM and LOW. When you select the HIGH, the extension will choose the best quality available. The LOW quality will do the inverse.

> **zerojay said:**
> The plugin works fine on blip, but I can't get it to do anything whatsoever with Youtube at all. Youtube flash player still starts up and plays.

It doesn't work on channels. You need to select a single video to play. I'm working working on this for a future version. 

If it doesn't work, deselect YouTube in the preferences, wait for the site to reload (it should reload automatically) and select it again. It should reload the video and replace it automatically.

---

### Post by zerojay on 2010-06-20
It's just a standard single video page, not a channel page or any other. Did what you said and it still just reloads the flash player repeatedly, Youtube button turned on or not.

Any other ideas?

EDIT: Turns out that my issue was caused by a corrupt Firefox profile. I started a new one and the plugin worked fine right away. Sorry for the complaints. :)

---

### Post by lovinglinux on 2010-06-20
> **zerojay said:**
> EDIT: Turns out that my issue was caused by a corrupt Firefox profile. I started a new one and the plugin worked fine right away. Sorry for the complaints. :)

No problem. I'm glad is working now.

---

### Post by Artemis3 on 2010-06-23
I just tried this and it doesn't seem to do anything in youtube. You sure it works with NoScript? I also have flashblock, and 64 bit Adobe Player.

---

### Post by lovinglinux on 2010-06-23
> **Artemis3 said:**
> I just tried this and it doesn't seem to do anything in youtube. You sure it works with NoScript? I also have flashblock, and 64 bit Adobe Player.

It works with NoScript, but I haven't tried with Flashblock. Just in case, disable both and try again.

Also, test these videos:

[LIST]
[*][a video on Vimeo](http://vimeo.com/5606758)
[*][a video on YouTube](http://www.youtube.com/watch?v=u7deClndzQw&feature=related)
[/LIST]

---

### Post by Artemis3 on 2010-06-24
> **lovinglinux said:**
> It works with NoScript, but I haven't tried with Flashblock. Just in case, disable both and try again.

Also, test these videos:

[LIST]
[*][a video on Vimeo](http://vimeo.com/5606758)
[*][a video on YouTube](http://www.youtube.com/watch?v=u7deClndzQw&feature=related)
[/LIST]

Disabling flashblock made it work with youtube. I'm using mozilla-plugin-vlc which works fine except there are no controls of any sort, so i can't go fullscreen (f) which kinda defeats its purpose...

---

### Post by lovinglinux on 2010-06-24
> **Artemis3 said:**
> Disabling flashblock made it work with youtube. I'm using mozilla-plugin-vlc which works fine except there are no controls of any sort, so i can't go fullscreen (f) which kinda defeats its purpose...

Use gecko-mediaplayer or totem. They both have controls and work fine with FlashVideoReplacer.

---

### Post by swong on 2010-06-25
You can also enable Flashblock, but add YouTube to its whitelist, and FlashVideoReplacer will work as intended.

@lovinglinux - I would just like to say that this is one of the best Firefox addons I've used, my cpu usage on average has halved when playing YouTube videos using the gecko-mediaplayer plugin as opposed the to Flash plugin.  Keep up the good work!

---

### Post by lovinglinux on 2010-06-25
> **swong said:**
> You can also enable Flashblock, but add YouTube to its whitelist, and FlashVideoReplacer will work as intended.

@lovinglinux - I would just like to say that this is one of the best Firefox addons I've used, my cpu usage on average has halfed when playing YouTube videos using the gecko-mediaplayer plugin as opposed the to Flash plugin.  Keep up the good work!

Thank you very much.

---

### Post by crienoloog on 2010-06-25
IS there a Chrome variant as well?

---

### Post by lovinglinux on 2010-06-25
> **crienoloog said:**
> IS there a Chrome variant as well?

No. Not sure if would be possible to do that in Chrome, since extensions are limited in functionality. Anyway, I have decided to support only Firefox for now.

---

### Post by crienoloog on 2010-06-25
Obrigado...
to bad, I'll have to stick to Flash then. :popcorn:

---

### Post by proteusmoteus on 2010-06-29
Both gnash and swfdec can be configured to not autoplay flash so [Flashblock]("https://addons.mozilla.org/en-US/firefox/addon/433/") is not necessary when using them. I recommend swfdec (swfdec-mozilla in synaptic) as my testing today indicated it still works better than gnash despite being unmaintained. 

While installing swfdec-mozilla also install gecko-mediaplayer (plugin for mplayer) and remove the package totem-mozilla. gecko-mediaplayer offers better functionality in the form of: buffer progress info, seeking (jumping to different times in the video), replay, and can be configured to buffer less before starting playback.

swfdec-mozilla configuration: right click on flash object (not on the 3 supported video sites as the flash object is replaced by gecko-mediaplayer) go to "Autoplay" option and select "Never".

gecko-mediaplayer configuration: in Gnome MPlayer (now under Sound & Video in Gnome menu) select Edit > Preferences; or edit preferences via right clicking the embedded object. Lower the time spent buffering before starting playback via first the "Plugin" tab and changing the "Cache Size" to 544. You have to use the arrows (doesnt allow input from typing) to go down to 32 and then up to 544. Note due to a bug the 32 value doesnt work as well as 544, and the numbers before going all the way down to 32 are invalid. Of course raise this value if you want video to buffer longer (slow connection), but don't modify cache values on other tabs as those relate to max memory allowed for mplayer (disabled by default) rather than amount of video data to download before playing.

Pretty quick and easy, but dont expect any other video sites to work with swfdec, though the one game I tried did work ([desktop tower defense]("http://www.handdrawngames.com/")).

---

### Post by lovinglinux on 2010-07-04
[SIZE="4"]**[COLOR="Sienna"]FlashVideoReplacer 1.0.1 released![/COLOR]**
[/SIZE]
This is a maintenance version that addresses a problem with plugin selection. The previous version was using x-mplyer2 mime type, that defaults to Windows Media Player plugin, thus not allowing some Quicktime users to view the videos properly (only affects Windows users).

The new preferences dialog allows to select which mime type to be used and consequently the plugin. Additionally the extension now defaults to Quicktime, instead of WMP. Although Windows Media Player is still supported, it only works with additional codecs to allow mp4 decoding.

**[COLOR="Red"]Linux users[/COLOR]** can now use  gecko mediaplayer, gxine, kaffeine, mozplugger, totem and xine plugins.

This version does not support additional web sites because that issue with plugins was a priority and I wanted to make it available as soon as possible. Nevertheless, I have received many requests for new web sites support and will be implementing a few soon. 

It will take a couple of days before Mozilla can review this version and approved it, but you can download it right now from the Stable Channel on the [extension web site](http://flvideoreplacer-extension.blogspot.com/p/changelog.html).

See [Changelog](http://flvideoreplacer-extension.blogspot.com/p/changelog.html) for details.

---

### Post by lovinglinux on 2010-07-21
FlashVideoReplacer version 1.0.2 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version adds compatibility with Firefox 4.0b3pre.

---

### Post by swong on 2010-07-24
Is anyone having problems using this with YouTube?  The gecko-mediaplayer does show up on screen but it does not load the video, this seems to have happened within the last few days (even before v1.02).

I've tested it with Vimeo, and the addon works on that site.

---

### Post by lovinglinux on 2010-07-24
> **swong said:**
> Is anyone having problems using this with YouTube?  The gecko-mediaplayer does show up on screen but it does not load the video, this seems to have happened within the last few days (even before v1.02).

I've tested it with Vimeo, and the addon works on that site.

You are correct. It seems YouTube changed the code of their pages, so I will need to update the extension. Please stay tuned.

---

### Post by lovinglinux on 2010-07-24
FlashVideoReplacer version 1.0.3 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version fixes changes introduced on YouTube on July 22nd, which prevented videos from loading. 

[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[https://addons.mozilla.org/en-US/firefox/addon/161869/versions/](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/)

---

### Post by SEBASTIANFFX on 2010-07-29
Bravo for such great plugin, can't wait for the facebook support ;)!
I'll try to help  with bug tracking.

---

### Post by lovinglinux on 2010-07-29
> **SEBASTIANFFX said:**
> Bravo for such great plugin, can't wait for the facebook support ;)!
I'll try to help  with bug tracking.

Thanks.

---

### Post by Methodize on 2010-08-11
Beautiful job with Flash Video Replacer. The first time I tried it on YouTube it loaded the entire video before it started to play. Then I added on Flash-Aid and the video played fine as it was loading.

can't wait for Megaupload to be available!

---

### Post by lovinglinux on 2010-08-11
> **Methodize said:**
> Beautiful job with Flash Video Replacer. The first time I tried it on YouTube it loaded the entire video before it started to play. Then I added on Flash-Aid and the video played fine as it was loading.

can't wait for Megaupload to be available!

Thank you. I'm currently working on the stability of the extension, specially since Firefox 4 will be released soon. Nevertheless, as soon as I have the opportunity I will add more supported sites.

---

### Post by lovinglinux on 2010-08-16
FlashVideoReplacer version 1.0.4 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version fixes an issue that prevented the extension from working properly when the video page is loaded in the background.

---

### Post by riverkarl on 2010-08-27
> **Methodize said:**
> Beautiful job with Flash Video Replacer. The first time I tried it on YouTube it loaded the entire video before it started to play. Then I added on Flash-Aid and the video played fine as it was loading.

can't wait for Megaupload to be available!

I have this same problem where the video will load all the way and then start playing rather than playing while loading. I added Flash-Aid and still no dice. What setting can I change to get the video to play while it is still loading.

---

### Post by lovinglinux on 2010-08-27
> **riverkarl said:**
> I have this same problem where the video will load all the way and then start playing rather than playing while loading. I added Flash-Aid and still no dice. What setting can I change to get the video to play while it is still loading.

What plugin you are using to replace flash?

---

### Post by riverkarl on 2010-08-27
> **lovinglinux said:**
> What plugin you are using to replace flash?

FlashVideoReplacer, and I used the FlashAid addon to fix any conflicts with my version of flash. 

Also I noticed that the problem of the video not playing while loading happens on many youtube videos but not all. There are a few youtube videos that it will play while they load and it will do so every time for those same videos. On others I can hear sound and the video will play in snapshots while it loads. 

I would just call it quits but flashvideoreplacer does such a great job at flash (on the clips it works for) compared to flash player, that it's definitely worth pursuing.

---

### Post by lovinglinux on 2010-08-27
> **riverkarl said:**
> FlashVideoReplacer, and I used the FlashAid addon to fix any conflicts with my version of flash. 


What I mean is the video plugin. FlashVideoReplacer is not a plugin, but an extension that allows you to replace embedded flash videos with other type of video. To play this other video type, you need a plugin like totem, gecko-mediaplayer, gxine
kaffeine, mozplugger or xine, which is loaded in the place of the flash video. Which one do you have?

---

### Post by riverkarl on 2010-08-27
Oh right, sorry. Ah, I believe it is using Totem Movie Player as the plugin/player. Would changing the video player perhaps fix this and if so how could I change it.

---

### Post by lovinglinux on 2010-08-27
> **riverkarl said:**
> Oh right, sorry. Ah, I believe it is using Totem Movie Player as the plugin/player. Would changing the video player perhaps fix this and if so how could I change it.

I recommend gecko-mediaplayer. You can remove totem and install gecko with these commands:

```
sudo apt-get remove totem-mozilla
sudo apt-get gecko-mediaplayer
```

You can customize the buffer cache size by editing ~/.mplayer/config file:

```
gedit ~/.mplayer/config
```

Then add the following to the [gnome-mplayer] section:

```
cache=8192
cache-min=10.0
cache-seek-min=30
```

You might need to tweak the values to your liking. Some videos take longer to buffer, depending on the resolution. On YouTube, higher resolution videos tend to buffer faster. If it takes too long to buffer and the video doesn't show, click play while buffering.

Also make sure you have all the proper codecs. See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").

If some videos still doesn't work, please provide a link so I can verify it. Also, please explains what happens when you try to watch ito. I need to know if the extension is not replacing the flash video or if the video simply doesn't load with the gecko plugin.

---

### Post by riverkarl on 2010-08-27
Okay cool, got it working. Only problem was that "sudo apt-get gecko-mediaplayer" should be "sudo apt-get install gecko-mediaplayer", but other than that thanks a lot!

---

### Post by lovinglinux on 2010-08-27
> **riverkarl said:**
> Okay cool, got it working. Only problem was that "sudo apt-get gecko-mediaplayer" should be "sudo apt-get install gecko-mediaplayer", but other than that thanks a lot!

Oops, sorry. :oops:

Sometimes I think I should stop multitasking :)

---

### Post by lovinglinux on 2010-09-18
FlashVideoReplacer version 1.0.5 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

This version fixes 4:3 video aspect in Windows Quicktime and also removes the extension menu icon from the statusbar, due to upcoming changes in Firefox 4, in which the statusbar will be replaced by a new addons bar. So from now on, the extension will only be accessible from the navigation toolbar.

[IMG]http://tinyurl.com/26cpax7[/IMG]

Users that prefer to access FlashVideoReplacer from the bottom of the browser will be allowed to move it to the new addons bar in Firefox 4.

[http://flvideoreplacer-extension.blogspot.com](http://flvideoreplacer-extension.blogspot.com)
[http://github.com/lovinglinux/flvideoreplacer/downloads](http://github.com/lovinglinux/flvideoreplacer/downloads)
[https://addons.mozilla.org/en-US/firefox/addon/161869/versions/](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/)

---

### Post by Rusna on 2010-09-20
> **lovinglinux said:**
> FlashVideoReplacer version 1.0.5 has been released today and is available for download through the Stable Channel. It will be available at Mozilla site as soon it gets reviewed by Mozilla editors.

I suppose it's still Firefox only, no Chrome support?

---

### Post by lovinglinux on 2010-09-20
> **Rusna said:**
> I suppose it's still Firefox only, no Chrome support?

Yes, this is a Firefox only extension. I have no intentions to try to port my extensions to Chrome in the near future.

---

### Post by lovinglinux on 2010-10-03
Today I'm celebrating a milestone. FlashVideoReplacer has reached the mark of 100.000 downloads. It is by far my most popular extension, followed by FLASH-AID with 30.000 downloads. Both extensions were initially released 4 months ago.

This milestone is definitely a big incentive and the result of almost 2 years learning XUL and Javascript programming. When I started developing Firefox extensions, by the end of 2008, I was totally clueless about software development and coding, but I'm feeling more comfortable every day and I'm very excited about my future releases. 

I have a lot of ideas for new add-ons and I'm currently developing 3 extensions that will certainly compete with FlashVideoReplacer for a spot on my most downloaded extensions list. They are a replacement for the experimental FoxMediaCenter, which I decided to terminate, and will provide many interesting features for movie and TV series fans.

I would like to thank all my extensions users, the Ubuntu community and Mozilla for the great support I have received so far.

Programming Firefox extensions is awesome!

---

### Post by lovinglinux on 2010-11-06
> **Rusna said:**
> I suppose it's still Firefox only, no Chrome support?

I have started to port some of my extension to Opera and Chrome, so I will probably release a version of FlashVideoReplacer for Chrome soon.

---

### Post by lovinglinux on 2010-11-06
FlashVideoReplacer version 1.0.6 has been released today and is available for download through GitHub. It will be available through Firefox's extensions update and through the Stable Channel as soon it gets reviewed by Mozilla editors.

The most important change is the increase of video resolution on all YouTube quality settings. I have received some complains about video quality, so I raised the maximum limit. Now the LOW quality setting will play the best resolution available, up to 480p, the MEDIUM quality setting will play the best resolution available, up to 720p and the HIGH quality setting will play the best resolution available, including original HD higher than 1080p.

You can test the extension with [Sintel HD]("http://www.youtube.com/watch?v=HomAZcKm3Jo") video, which renders incredible video quality when setting the extension to HIGH quality YouTube videos.

High Resolution Screenshot: [http://goo.gl/VNrsr](http://goo.gl/VNrsr)

The extension also has some feedback alerts now, which will notify the user if some incompatible extensions are installed and will notify the selected video resolution on YouTube.

---

### Post by G4dget on 2010-11-06
Thanks for the add-on. This was a quick fix to get flash working after the upgrade to 10.10

---

### Post by lovinglinux on 2010-11-06
> **G4dget said:**
> Thanks for the add-on. This was a quick fix to get flash working after the upgrade to 10.10

You are welcome.

---

### Post by beew on 2010-11-08
Hi, 

Thanks for the addon. I am using gecko-player to replace flash, but for high definition videos (720p) the cpu usage is just as high,--100%  even with Compiz disabled. The only difference is that it is not 100& all the time so I get very choppy videos instead of a total slide show. :) I notice that in my system (Lucid, 1G of ram 2Ghz cpu) mplayer is not very good at playing 720p videos even offline (aside: actually none of the players can play 720p well offline in Lucid for this machine, but vlc plays 720p quite nicely in Maverick on the same machine!)

On the other hand minitube plays 720p Youtube videos smoothly  and on full screen even with Compiz (same machine of course and in Lucid). I wonder if you know whether it uses another player as its backend and if this can be somehow used with your plugin. Thanks.

---

### Post by beew on 2010-11-08
Oh, I missed your last post. I think that may answer my question. In order to view a video whose highest setting in 720p, should I then set the addon's setting to medium instead of high? 

EDIT: I just realize I have version 1.0.5. So the setting should be high? (and that uses 100% cpu. :()
I was using this as a test [http://www.youtube.com/watch?v=G9X-Lw6xtbc](http://www.youtube.com/watch?v=G9X-Lw6xtbc)

---

### Post by lovinglinux on 2010-11-08
> **beew said:**
> Hi, 

Thanks for the addon. I am using gecko-player to replace flash, but for high definition videos (720p) the cpu usage is just as high,--100%  even with Compiz disabled. The only difference is that it is not 100& all the time so I get very choppy videos instead of a total slide show. :) I notice that in my system (Lucid, 1G of ram 2Ghz cpu) mplayer is not very good at playing 720p videos even offline (aside: actually none of the players can play 720p well offline in Lucid for this machine, but vlc plays 720p quite nicely in Maverick on the same machine!)

On the other hand minitube plays 720p Youtube videos smoothly  and on full screen even with Compiz (same machine of course and in Lucid). I wonder if you know whether it uses another player as its backend and if this can be somehow used with your plugin. Thanks.

I'm going to check this. Is possibly some configuration settings used by minitube.

> **beew said:**
> Oh, I missed your last post. I think that may answer my question. In order to view a video whose highest setting in 720p, should I then set the addon's setting to medium instead of high?

If you need to limit the resolution to below 720p, then use the LOW option. If you need to limit the resolution to 720p, then set it as MEDIUM. If you use the HIGH option and the video has videos up to 720p, then it will play 720p, but if it has resolutions higher than 720p then it will play the best of them. 

> **beew said:**
> EDIT: I just realize I have version 1.0.5. So the setting should be high? (and that uses 100% cpu. :()
I was using this as a test [http://www.youtube.com/watch?v=G9X-Lw6xtbc](http://www.youtube.com/watch?v=G9X-Lw6xtbc)

Yes, on that version the settings should be high to get 720p.

---

### Post by beew on 2010-11-10
Hi, lovinglinux,

I was playing around with mplayer's settings and it turns out that  your flashvideoreplacer works magic if I set mplayer's video output to "xv"!  (as a result mplayer also plays downloaded videos perfectly now) I did another thing that may help a little, I disabled the flashvideoreplacer, brought up a youtube video and right clicked it, a setting box appeared and I changed the amount of information that the video could store in the computer to minimum (10k)  and then renabled the flashvideoreplacer. This seems to speed up load time tremendously.

I don't know what the explanation is  but now I can  watch 720p on youtube smoothly and in full screen even when full Compiz is on! The quality is almost as smooth as minitube now except in the beginning of a clip mplayer seems to lag a bit but stopping and starting again solves the problem.

Again thanks for the great addon! By the way, I remember reading that one can use mozplugger with the flashvideoreplacer, how is this done? I am happy with mplayer, but I just wonder how one can use different video players because I don't find any option in the flashvideoplayer (other than windows media player and quick time, neither is relevant to Linux)  and how does mozplugger fit in. Thanks.

---

### Post by lovinglinux on 2010-11-10
> **beew said:**
> I was playing around with mplayer's settings and it turns out that  your flashvideoreplacer works magic if I set mplayer's video output to "xv"!  (as a result mplayer also plays downloaded videos perfectly now)

Yes. The reason for using mplayer instead of flash is that flash can't use xv, which has much better performance.


> **beew said:**
> I did another thing that may help a little, I disabled the flashvideoreplacer, brought up a youtube video and right clicked it, a setting box appeared and I changed the amount of information that the video could store in the computer to minimum (10k)  and then renabled the flashvideoreplacer. This seems to speed up load time tremendously.

Interesting. I don't see how it would affect mplayer, but worth investigating.

> **beew said:**
> Again thanks for the great addon! By the way, I remember reading that one can use mozplugger with the flashvideoreplacer, how is this done? I am happy with mplayer, but I just wonder how one can use different video players because I don't find any option in the flashvideoplayer (other than windows media player and quick time, neither is relevant to Linux)  and how does mozplugger fit in. Thanks.

In Linux, **video/quicktime** and **application/x-mplayer2** mime types are both handled by the same plugins. So it doesn't really matter which one you choose. The only way to change the plugin used in Linux is to disable the plugin currently in use by Firefox and enabling a different one. If you want to try mozplugger, you will need to install that plugin and disable the plugin you are using now through Firefox preferences.

---

### Post by beew on 2010-11-10
> In Linux, **video/quicktime** and **application/x-mplayer2** mime  types are both handled by the same plugins. So it doesn't really matter  which one you choose. The only way to change the plugin used in Linux is  to disable the plugin currently in use by Firefox and enabling a  different one. If you want to try mozplugger, you will need to install  that plugin and disable the plugin you are using now through Firefox  preferences.I have an old machine that I am fixing up for my friend. It has a nvidia Gforce4 4200 go graphic card and a screen resolution of 1680X1050 , but it has only 512m of ram so playing videos of 720p is difficult. 

I downloaded the file (720p) I used to test flashvideoreplacer on youtube (see post above) to this machine. It absolutely kills mplayer, but vlc can play it fairly smoothly. In my own less old machine mplayer is almost as good as vlc (and way better than totem and banshee) but on this old machine the difference is huge (I don't know why but vlc seems to be always way ahead of other Linux media players)

I tried to use vlc ff plugin with flashvideo replacer so I disabled the mplayer plugins but when  I loaded a youtube page all I got was plugin not enabled or something like that, tried mozplugger and gxine plugins and got the same result. It seems that it only wants mplayer.

P.S. gxine is smooth but it loses the audio half way. It is the same with other very high resolution clips . That makes me think maybe minitube is using gxine because it has the same problem playing resolution which is a bit too high (720p on the very old machine and 1080p on my less old one) video goes fluidly but no sound.

---

### Post by lovinglinux on 2010-11-10
> **beew said:**
> I have an old machine that I am fixing up for my friend. It has a nvidia Gforce4 4200 go graphic card and a screen resolution of 1680X1050 , but it has only 512m of ram so playing videos of 720p is difficult. 

I downloaded the file (720p) I used to test flashvideoreplacer on youtube (see post above) to this machine. It absolutely kills mplayer, but vlc can play it fairly smoothly. In my own less old machine mplayer is almost as good as vlc (and way better than totem and banshee) but on this old machine the difference is huge (I don't know why but vlc seems to be always way ahead of other Linux media players)

I tried to use vlc ff plugin with flashvideo replacer so I disabled the mplayer plugins but when  I loaded a youtube page all I got was plugin not enabled or something like that, tried mozplugger and gxine plugins and got the same result. It seems that it only wants mplayer.

P.S. gxine is smooth but it loses the audio half way. It is the same with other very high resolution clips . That makes me think maybe minitube is using gxine because it has the same problem playing resolution which is a bit too high (720p on the very old machine and 1080p on my less old one) video goes fluidly but no sound.

VLC is awesome, but the VLC plugin is not.

Try to add this to mplayer config:

```
skiploopfilter=all
```

---

### Post by beew on 2010-11-11
> **lovinglinux said:**
> VLC is awesome, but the VLC plugin is not.

Try to add this to mplayer config:

```
skiploopfilter=all
```

Hi, did that. It didn't work. VLC is smooth and fluid but mplayer stops like every few seconds. Wonder what technology is vlc using and why it is not adopted by other media players. :)

---

### Post by lovinglinux on 2010-11-11
> **beew said:**
> Hi, did that. It didn't work. VLC is smooth and fluid but mplayer stops like every few seconds. Wonder what technology is vlc using and why it is not adopted by other media players. :)

I think is some configuration option. BTW, I don't use VLC, I use smplayer (mplayer frontend) and it works great.

---

### Post by beew on 2010-11-11
You probably have more ram than 512 M. mplayer is almost as good as vlc in my other laptop with 1 G of ram. :)

---

### Post by lovinglinux on 2010-11-11
> **beew said:**
> You probably have more ram than 512 M. mplayer is almost as good as vlc in my other laptop with 1 G of ram. :)

Yes, I have 2Gb.

---

### Post by beew on 2010-11-21
Hi,  LovingLinux,

I have some more questions in case you are still reading this (or if anyone knows the answer).

I have tried gxine and it seems that it is somewhat lighter than mplayer for playing higher definition mp4 files locally. I tried to use the gxine plugin with the flashvideoreplacer by disabling the mplayer stuffs but I was greeted with "plugin missing" on Youtube. In your instruction for using the flashvideoreplacer you did mention using gxine as a possibility, I wonder if you have any advice.

I would also like to know if the flashvideoreplacer works on  sites other than Youtube and whether it would work for distros other than Ubuntu. I am going to install a Fedora system and wonder if this great addon will work there as well, how about flashaid?

Thanks again for the great apps.

---

### Post by lovinglinux on 2010-11-21
> **beew said:**
> Hi,  LovingLinux,

I have some more questions in case you are still reading this (or if anyone knows the answer).

I have tried gxine and it seems that it is somewhat lighter than mplayer for playing higher definition mp4 files locally. I tried to use the gxine plugin with the flashvideoreplacer by disabling the mplayer stuffs but I was greeted with "plugin missing" on Youtube. In your instruction for using the flashvideoreplacer you did mention using gxine as a possibility, I wonder if you have any advice.

I just tested gxine again and it isn't working now. I recommend using gecko-mediaplayer.

> **beew said:**
> I would also like to know if the flashvideoreplacer works on  sites other than Youtube and whether it would work for distros other than Ubuntu. I am going to install a Fedora system and wonder if this great addon will work there as well, how about flashaid?

FlashVideoReplacer works on YouTube,Vimeo and Blip.tv. It is OS independent, so it will work on Fedora too.

I'm not familiar with Fedora and haven't tested Flash-aid on it. However, if it doesn't work, then instead of running the extension through the end, stop when it shows which commands will be executed, copy the commands and run them in a terminal making the necessary adjustments if any command fails.

---

### Post by beew on 2010-11-21
Hi,

Thanks for the speedy reply.

---

### Post by lovinglinux on 2010-11-21
> **beew said:**
> Hi,

Thanks for the speedy reply.

You are welcome.

---

### Post by lovinglinux on 2010-12-09
YouTube has made some changes today that affects all versions of FlashVideoReplacer, preventing it from working. I'm working on a solution and will release a new version as soon as possible.

---

### Post by lovinglinux on 2010-12-09
Version 1.0.7 has been released and is waiting approval.

This version fixes the changes introduced on YouTube today, that broke the extension functionality.

You can get it from the extension version page while it is under review by Mozilla:

[https://addons.mozilla.org/en-US/firefox/addon/161869/versions/](https://addons.mozilla.org/en-US/firefox/addon/161869/versions/)

---

### Post by beew on 2010-12-10
Thanks dude! I just started a thread wondering why flashvideoreplacer has stopped working, while forgetting about this thread. 

I thought it might have been youtube because the flashvideoreplacer still works on vimeo and blip.tv and minitube stops working as well (until just now when I got an update)

Cheers, thanks again for enhancing the Linux experience.

---

### Post by lovinglinux on 2010-12-10
> **beew said:**
> Thanks dude! I just started a thread wondering why flashvideoreplacer has stopped working, while forgetting about this thread. 

I thought it might have been youtube because the flashvideoreplacer still works on vimeo and blip.tv and minitube stops working as well (until just now when I got an update)

Cheers, thanks again for enhancing the Linux experience.

You are welcome.

---

### Post by darkwolfalone on 2010-12-11
I installed the update and Youtube still doesn't work for me. BlipTV still works as well as it ever did.

---

### Post by lovinglinux on 2010-12-11
> **darkwolfalone said:**
> I installed the update and Youtube still doesn't work for me. BlipTV still works as well as it ever did.

If you are using totem plugin, then set the extension to use Windows Mewdia Player. Then visit a video, let it buffer for a few seconds and click play. However, I would recommend using gecko-mediaplayer, since totem doesn't have buffering feedback and there is no indication that the video is actually being downloaded.

---

### Post by Dilutu on 2010-12-12
I installed your extention on my main computer running 10.04 with gecko-mediaplayer and it works realy good. I also installed it the same way on my laptop running Hardy,and it works good on vimeo but not on youtube.I can see the cache filling, but when I click "play" it says "playing" and then "stopped"??????

---

### Post by lovinglinux on 2010-12-13
> **Dilutu said:**
> I installed your extention on my main computer running 10.04 with gecko-mediaplayer and it works realy good. I also installed it the same way on my laptop running Hardy,and it works good on vimeo but not on youtube.I can see the cache filling, but when I click "play" it says "playing" and then "stopped"??????

Try to change the quality settings.

---

### Post by beew on 2010-12-16
Hi, Lovinglinux,

While version 1.07 works it seems to load youtube videos less smoothly than it was before. When a video loads the cpu usage sometimes goes up to 100% and firefox becomes dim momentarily and then it is normal again (as a result cpu gets hot even before the video is played). This didn't happen before, I tested with the same videos. I wonder if I need to set some parameters in mplayer?

Thanks.

---

### Post by beew on 2010-12-16
Hi,

I think I have figured it out, at least part of it. It turns out that the hot cpu has to do with flash player settings (to access it, disable flashvideoreplacer, restart ff, go to youtube  and right click on any video). Disabling hardware acceleration would prevent the cpu from heating up. I have disabled it before, but what happened was I use bleachbit to clean my system and I have set it to delete all cookies for flash player and this reverts the setting to default, which is to use hardware acceleration.

But I still have a question. I don't know if this makes any sense, but I think cpu usage can be reduced if I allow the video to cache a bit more before it starts playing back, because it seems that downloading  and playing back at the same time would require more resources (to test that hypothesis I downloaded the same clips from youtube and play them off line with mplayer, it did use less cpu than when I use ff with flashvideoreplacer) I have set flashvideoreplacer to play video automatically. I still want that but I am wondering if I can adjust when it would start in terms of how much has been cached already?

There is another question which probably has been asked many times. My understanding is that you are basically a ff developer, but is there any possibility to port this great addon to other browsers such as Opera? 

Thanks.

---

### Post by lovinglinux on 2010-12-16
> **beew said:**
> Hi,

I think I have figured it out, at least part of it. It turns out that the hot cpu has to do with flash player settings (to access it, disable flashvideoreplacer, restart ff, go to youtube  and right click on any video). Disabling hardware acceleration would prevent the cpu from heating up. I have disabled it before, but what happened was I use bleachbit to clean my system and I have set it to delete all cookies for flash player and this reverts the setting to default, which is to use hardware acceleration.


Hi,

I think it is strange that you solved the problem by tweaking flash, because it should not be involved, once the video is loaded with mplayer. Are you sure is not falling back to flash?

> **beew said:**
> But I still have a question. I don't know if this makes any sense, but I think cpu usage can be reduced if I allow the video to cache a bit more before it starts playing back, because it seems that downloading  and playing back at the same time would require more resources (to test that hypothesis I downloaded the same clips from youtube and play them off line with mplayer, it did use less cpu than when I use ff with flashvideoreplacer) I have set flashvideoreplacer to play video automatically. I still want that but I am wondering if I can adjust when it would start in terms of how much has been cached already?

You can set that in mplayer's config file (eg. ~/.mplayer/config) like this:

```
cache-min=20.0
cache-seek-min=50
```


> **beew said:**
> There is another question which probably has been asked many times. My understanding is that you are basically a ff developer, but is there any possibility to port this great addon to other browsers such as Opera? 

Thanks.

I was basically a Firefox developer, but I recently adopted Opera as my primary browser since they started supporting extensions, so I'm developing for it too now. I'm also developing for Chrome, which has a similar extension framework.

Bottom line, I have already started to port FlashVideoReplacer to Opera. However, it wasn't working as expected during the alpha phase, so I stopped. Now that Opera 11 has been officially released, I will resume the work on it.

Unfortunately, this week has been kind of crazy. I had to update 3 extensions because of bugs and because YouTube, Adobe and Vimeo keep changing things when I am overloaded :) On top of that, I am finalizing the new web site for the extensions. So I will be pretty busy until next year.

Anyways, I'm working on the clock to release what will be FlashVideoReplacer 2.0, which will have tons of new features and will fix Vimeo, that stopped working since yesterday. For instance, it will allow to open videos in a new tab (covering entire page area), in a new window or with external players. It will also allow to automatically choose WebM player on YouTube if available, without the need to join the HTML5 Beta program (requires Firefox 4). It will also be more clever in regard to video source selection, so you can prioritize mp4 over flv. The extension will detect compatible plugins and players and suggest the appropriate ones. It will also allow to download the videos.

I am currently experiencing difficulties to parse the correct links from YouTube and Vimeo. The links I was able to fetch work fine with plugins, but not the external players. Hopefully I will be able to fix this and release the new version in a week or so. Stay tuned.

---

### Post by beew on 2010-12-17
Hi,

> **lovinglinux said:**
> Hi,

I think it is strange that you solved the problem by tweaking flash, because it should not be involved, once the video is loaded with mplayer. Are you sure is not falling back to flash?


You are right, on further testing the advantage disappeared. It might be that I forgot to empty the cache before the second run so the video was already cached and as a result it loaded more smoothly.

So this brings me back to my original problem. It seems that initial launching of flashvideoreplacer is not as smooth as before and sometimes it seems almost struggling and as a result heating up my cpu even before playback. This didn't happen before youtube broke the previous version of flashvideoreplacer. I didn't post the question for a number of days because I thought that it might be the internet connection but I am actually getting much better connection now than before after changing my router two days ago.

(On a side note,  when I first upgraded flashvideoreplacer about a week ago videos would just start playing for a few seconds and then stop and start reloading. This no longer happens for flashvideoreplacer but it is still like that for minitube, basically rendering it unusable, it is probably something at youtube's end)

> 
You can set that in mplayer's config file (eg. ~/.mplayer/config) like this:

```
cache-min=20.0
cache-seek-min=50
```Just did that but apparent nothing changes. Videos still load almost immediately if flashvideoreplacer is set to play video automatically.  I changed the 20.0 and 50 to other values and there seemed to be no difference.  I would appreciate it if you can tell me what these lines do?

It may be relevant information that I have set mplayer's cache size to 1056kb (from gnome mplayer)



> ..Anyways, I'm working on the clock to release what will be FlashVideoReplacer 2.0, which will have tons of new features and will fix Vimeo, that stopped working since yesterday. For instance, it will allow to open videos in a new tab (covering entire page area), in a new window or with external players. It will also allow to automatically choose WebM player on YouTube if available, without the need to join the HTML5 Beta program (requires Firefox 4). It will also be more clever in regard to video source selection, so you can prioritize mp4 over flv. The extension will detect compatible plugins and players and suggest the appropriate ones. It will also allow to download the videos.

I am currently experiencing difficulties to parse the correct links from YouTube and Vimeo. The links I was able to fetch work fine with plugins, but not the external players. Hopefully I will be able to fix this and release the new version in a week or so. Stay tuned...
It sounds exciting with all the developments going on. :) We can't thank you enough for your hard work!

---

### Post by lovinglinux on 2010-12-17
> **beew said:**
> Hi,

You are right, on further testing the advantage disappeared. It might be that I forgot to empty the cache before the second run so the video was already cached and as a result it loaded more smoothly.

So this brings me back to my original problem. It seems that initial launching of flashvideoreplacer is not as smooth as before and sometimes it seems almost struggling and as a result heating up my cpu even before playback. This didn't happen before youtube broke the previous version of flashvideoreplacer. I didn't post the question for a number of days because I thought that it might be the internet connection but I am actually getting much better connection now than before after changing my router two days ago.

FlashVideoReplacer 1.0.7 was released to address the YouTube issue as quick as possible. However, it still have issues that should be addressed in the next version. I have introduced some optimizations in version 2.0.0 that should fix those problems.

Because of those issues that I decided to rewrite the entire extension and add the features mentioned before. I wish I could release it today, but there are still things to be addressed.

> **beew said:**
> 
(On a side note,  when I first upgraded flashvideoreplacer about a week ago videos would just start playing for a few seconds and then stop and start reloading. This no longer happens for flashvideoreplacer but it is still like that for minitube, basically rendering it unusable, it is probably something at youtube's end)

YouTube changes messed really bad. Try to delete the YouTube cookies.

> **beew said:**
> Just did that but apparent nothing changes. Videos still load almost immediately if flashvideoreplacer is set to play video automatically.  I changed the 20.0 and 50 to other values and there seemed to be no difference.  I would appreciate it if you can tell me what these lines do?

cache-min is the percentage of the cache that needs to be buffered before it can start playing.

cache-seek-min is the percentage of the cache that needs to be buffered before you can seek the video.

> **beew said:**
> It may be relevant information that I have set mplayer's cache size to 1056kb (from gnome mplayer)

Yes, it's relevant. Increase your cache size to delay the start.

> **beew said:**
> It sounds exciting with all the developments going on. :) We can't thank you enough for your hard work!

This version will be a major step forward. I will finally be able to add more sites to the supported list, now that the extension code is more robust.

---

### Post by beew on 2010-12-18
Hi,

> **lovinglinux said:**
> 

cache-min is the percentage of the cache that needs to be buffered before it can start playing.

cache-seek-min is the percentage of the cache that needs to be buffered before you can seek the video.



Yes, it's relevant. Increase your cache size to delay the start.


I have tried different values for cache-min and cache-start (always with cache-min  < cache-seek after your 20 - 50 pattern but should it be the other way around because you have to find the video first before you can play it?)but if flashvideoreplacer is set to play video automatically playback always begins when the cache is about 3% filled according to the progress bar under the video.

I look forward to version 2.0, thanks!

---

### Post by I'mGeorge on 2010-12-18
it's a nice add-on but it still has a long way until it could properly replace flash player

---

### Post by lovinglinux on 2010-12-19
> **beew said:**
> Hi,



I have tried different values for cache-min and cache-start (always with cache-min  < cache-seek after your 20 - 50 pattern but should it be the other way around because you have to find the video first before you can play it?)but if flashvideoreplacer is set to play video automatically playback always begins when the cache is about 3% filled according to the progress bar under the video.

I look forward to version 2.0, thanks!


Here is a better explanation from the man pages:

```
       -cache <kBytes>
              This option specifies how much memory  (in  kBytes)
              to  use  when precaching a file or URL.  Especially
              useful on slow media.

       -nocache
              Turns off caching.

       -cache-min <percentage>
              Playback will start when the cache has been  filled
              up to <percentage> of the total.

       -cache-seek-min <percentage>
              If  a seek is to be made to a position within <per-
              centage> of the cache size from the  current  posi-
              tion,  MPlayer will wait for the cache to be filled
              to this position rather than  performing  a  stream
              seek (default: 50).
```

> **I'mGeorge said:**
> it's a nice add-on but it still has a long way until it could properly replace flash player

Thanks. Honestly, I have no illusion that FlashVideoReplacer could totally replace flash some day, but as long as people can watch HD on YouTube I'm happy with it,

However, I think you will be surprised with the next version. Although it is limited to YouTube and Vimeo video pages, it will offer great flexibility. I hope I can add more sites soon.

---

### Post by vtk_90 on 2010-12-22
How do I get it to work? I've tried installing gxineplugin, then saw the previous post recommending gecko-mediaplayer, installed it, but still nothing happens when I open a youtube video.

Help please? Noob here...

---

### Post by lovinglinux on 2010-12-23
> **vtk_90 said:**
> How do I get it to work? I've tried installing gxineplugin, then saw the previous post recommending gecko-mediaplayer, installed it, but still nothing happens when I open a youtube video.

Help please? Noob here...

Please wait for the next version, which will fix all issues created by YouTube recent changes.

I'm in the final stages of testing version 2.0, in order to release it, which should happen today or tomorrow (most likely today).

It also has several new features.

---

### Post by lovinglinux on 2010-12-24
Version 2.0 is out, with tons of new features and bug fixes.

You can get it from the new extension web site, while it is being reviewed by Mozilla.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

Happy Holidays!

---

### Post by lovinglinux on 2010-12-26
Version 2.0.1 is out, with a bug fix and an option to turn off alerts (user request).

You can get it from the new extension web site, while it is being reviewed by Mozilla.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

---

### Post by tjeremiah on 2011-01-03
Thanks for creating this add-on :). Is there a way this extension can take over all flash video content?

---

### Post by lovinglinux on 2011-01-03
> **tjeremiah said:**
> Thanks for creating this add-on :).

You are welcome.

> **tjeremiah said:**
> Is there a way this extension can take over all flash video content?

Unfortunately, not that I am aware of.

---

### Post by tjeremiah on 2011-01-09
I LOVE this add-on and thank you :). Though I think theres one problem and its very minor. After a video plays and stops, it appears the player re-downloads the same video that was watched.

---

### Post by lovinglinux on 2011-01-09
> **tjeremiah said:**
> I LOVE this add-on and thank you :). Though I think theres one problem and its very minor. After a video plays and stops, it appears the player re-downloads the same video that was watched.

You are welcome.

Which player and site?

---

### Post by verymadpip on 2011-01-11
I've just installed Ubuntu Studio 64 bit on my test box & added Flashaid to FF.  It's working a treat at the moment :D.

Thank you very much for this headache fixer.

---

### Post by lovinglinux on 2011-01-11
> **verymadpip said:**
> I've just installed Ubuntu Studio 64 bit on my test box & added Flashaid to FF.  It's working a treat at the moment :D.

Thank you very much for this headache fixer.

You are welcome.

---

### Post by beew on 2011-01-25
Hi, Lovinglinux

Thanks again for the great work. There are a few things I would like to bring to your attentions.

I am noticing that flashvideoreplacer uses a lot more cpu in firefox4 beta (minefield) than it is in firefox3.x. I have a Nvidia graphic card with vdpau enabled.  It is as if mplayer is not using vdpau on ff4.

On the other hand, in firefox3.x there is still a sharp initial spike of cpu usage on youtube  when flashvideoreplacer is launched.I tried this on several machines with different video cards and this is not related to vdpau. 

It is almost as if it is struggling and sometimes flash would start playing before flashvideoreplacer catches on. This problem doesn't appear in minefield, launch is a lot smoother.

Thanks once again and happy new year. :)

---

### Post by lovinglinux on 2011-01-25
> **beew said:**
> Hi, Lovinglinux

Thanks again for the great work.

You are welcome.

> **beew said:**
> I am noticing that flashvideoreplacer uses a lot more cpu in firefox4 beta (minefield) than it is in firefox3.x. I have a Nvidia graphic card with vdpau enabled.  It is as if mplayer is not using vdpau on ff4.

It could be indeed vdpau, because I don't have it and I don't see any difference in CPU usage when comparing FF 3.6.x with 4.0.

Keep in mind that once the video is loaded with mplayer, the extension interaction stops. So it's a Firefox/NVidia/Mplayer issue. If you can, please [report this to Mozilla]("https://bugzilla.mozilla.org/enter_bug.cgi"). I could do it, but ideally the report should be made from the system with the bug.

> **beew said:**
> On the other hand, in firefox3.x there is still a sharp initial spike of cpu usage on youtube  when flashvideoreplacer is launched.I tried this on several machines with different video cards and this is not related to vdpau. 

It is almost as if it is struggling and sometimes flash would start playing before flashvideoreplacer catches on. This problem doesn't appear in minefield, launch is a lot smoother.

Thanks once again and happy new year. :)

There are much more things going on behind the scenes in version 2.0.x before the video is replaced. So that CPU spike is to be expected. Firefox 4 has a much better javascript engine, so the extension runs smoothly. Please let me know if the browser freezes.

The next version will include an option to delay the video replacement. This was added primarily to deal with YouTube related video thumbnails not loading, but can also help with performance. Personally, I set the delay to 0, since I don't care much about the related videos.

Happy new year for you too.

---

### Post by beew on 2011-01-26
> **lovinglinux said:**
> You are welcome.



It could be indeed vdpau, because I don't have it and I don't see any difference in CPU usage when comparing FF 3.6.x with 4.0.

Keep in mind that once the video is loaded with mplayer, the extension interaction stops. So it's a Firefox/NVidia/Mplayer issue. If you can, please [report this to Mozilla]("https://bugzilla.mozilla.org/enter_bug.cgi"). I could do it, but ideally the report should be made from the system with the bug.


It seems like mplayer is not using vdpau when using flashvideoplayer based on the "top" output, it uses a lot more cpu than it would  in ff3. But then after testing in other machines I think high cpu usage may not be just failing to use vdpau. 

It seems that flashvideoreplacer uses a lot more cpu in ff4 than ff3.x even without the Nvidia card. While the initial launch is smoother in ff4, cpu usage during playback is significantly higher.

I used several 1080p or 720p clips on youtube for testing on an older machine where flashvidoreplacer would be most usefull (Dell Latitude D410, 2Ghz cpu, 1G of Ram)  The playback resolution  for flashvideo replacer was set to "medium". For this clip and a few like it flashvideoreplacer ran smoothly in ff3 but chokes in the middle and freezes in ff4. [http://www.youtube.com/watch?v=YW8p8JO2hQw](http://www.youtube.com/watch?v=YW8p8JO2hQw)  Enabling and disabling hardware accelaration in ff4 doesn't seem to make a difference.

I will make a bug report once I have sorted out my observations. Thanks for the reminder.


> There are much more things going on behind the scenes in version 2.0.x before the video is replaced. So that CPU spike is to be expected. Firefox 4 has a much better javascript engine, so the extension runs smoothly. Please let me know if the browser freezes.For ff4 the launch is smooth, but play back uses more cpu. For FF3X it is the other way around. The browser does freeze momentarily on my older machine when launching flashvideoreplacer in ff3.x  (the screen turned grey) but only briefly, it does lag quite a bit in  that it doesn't kick in until after flash has started playing the video. Depending on the clip the lag can be a few seconds or more, at first I thought it might be the internet connection but it can be ruled out because it happens always in ff3 but never in ff4 and independent of whether I use wireless or cable. Maybe thats explain the cpu spike? (flash is starting, video is loading and mplayer is starting..)

> The next version will include an option to delay the video replacement. This was added primarily to deal with YouTube related video thumbnails not loading, but can also help with performance. Personally, I set the delay to 0, since I don't care much about the related videos.
Good to hear that. Keep up the good work!

---

### Post by lovinglinux on 2011-01-26
> **beew said:**
> It seems like mplayer is not using vdpau when using flashvideoplayer based on the "top" output, it uses a lot more cpu than it would  in ff3. But then after testing in other machines I think high cpu usage may not be just failing to use vdpau. 

It seems that flashvideoreplacer uses a lot more cpu in ff4 than ff3.x even without the Nvidia card. While the initial launch is smoother in ff4, cpu usage during playback is significantly higher.

I used several 1080p or 720p clips on youtube for testing on an older machine where flashvidoreplacer would be most usefull (Dell Latitude D410, 2Ghz cpu, 1G of Ram)  The playback resolution  for flashvideo replacer was set to "medium". For this clip and a few like it flashvideoreplacer ran smoothly in ff3 but chokes in the middle and freezes in ff4. [http://www.youtube.com/watch?v=YW8p8JO2hQw](http://www.youtube.com/watch?v=YW8p8JO2hQw)  Enabling and disabling hardware accelaration in ff4 doesn't seem to make a difference.

I will make a bug report once I have sorted out my observations. Thanks for the reminder.


For ff4 the launch is smooth, but play back uses more cpu. For FF3X it is the other way around. The browser does freeze momentarily on my older machine when launching flashvideoreplacer in ff3.x  (the screen turned grey) but only briefly, it does lag quite a bit in  that it doesn't kick in until after flash has started playing the video. Depending on the clip the lag can be a few seconds or more, at first I thought it might be the internet connection but it can be ruled out because it happens always in ff3 but never in ff4 and independent of whether I use wireless or cable. Maybe thats explain the cpu spike? (flash is starting, video is loading and mplayer is starting..)

Good to hear that. Keep up the good work!

Please test it using the "New Tab" replacing method and once the video is loaded in a new tab, close the original YouTube page. Tell me if there is any difference in CPU usage.

---

### Post by beew on 2011-01-27
> **lovinglinux said:**
> Please test it using the "New Tab" replacing method and once the video is loaded in a new tab, close the original YouTube page. Tell me if there is any difference in CPU usage.

I think you are talking about the spiking of cpu when flashvideoreplacer launches in ff3.x. There is no difference, switching replacing method just results in the new tab struggling to open for a little while while flash starts playing in the original tab. I should clarify that this is only a problem on my low performance system (1 G of ram, 2GHz cpu single core) whereas on my newer system this is not perceptible (dual core 2.2Ghz each, 3 g of rams and a Nvidia card) But then I think flashvideoreplacer is most useful for lower end systems.

Since ff3 is going to be replaced soon that may not be a big issue afterall, what troubles me more is the high cpu usage of ff4 (but even with this high usage it still launches slower than opera at startup!). It just uses more cpu in general and especially at startup. Even with flashvideoreplacer cpu usage is considerably high on my old system when viewing videos (still much better than flash of course). Same youtube clips that play smoothly in ff3 with flashvideoplayer (despite the initial spike in cpu for ff3) are struggling in ff4. To lower cpu usage I usually don't start the video until it is almost fully load if it is 720p.

In my newer system it is not a problem but it still bothers me a lot that mplayer doesn't appear to be using vdpau (while in ff3 with flashvideoreplacer it certainly is)

---

### Post by beew on 2011-01-29
Hi,

Seems like the high cpu usage of ff4 has to do with the BarTab addon not really working even though it is supposed to be compatible with ff4. I closed most of the tabs and cpu usage has gone down dramatically, on startup, browsing and using flashvideoreplacer,--cpu usage comparable to ff3 when watching youtube. In ff3 I can have as many tabs opened but cpu usage remains low because bartab is working pproperly.

However, on my machine with the Nvidia card vdpau is definitly not working for the gecko-player pluggin for ff4. For the same youtube clips using flashvideoreplacer cpu usage in ff4 is way higher than in ff3, it is as if vdpau is not used (I waited til the videos were  100% loaded before playback to make sure it has nothing to do with slow internet or the streaming)

P.S. Just updated to ff4 b11 and apparently all open tabs are wiped out everytime ff4 restarts. Maybe that is how they solve the problem. :)

---

### Post by lovinglinux on 2011-01-29
> **beew said:**
> Hi,

Seems like the high cpu usage of ff4 has to do with the BarTab addon not really working even though it is supposed to be compatible with ff4. I closed most of the tabs and cpu usage has gone down dramatically, on startup, browsing and using flashvideoreplacer,--cpu usage comparable to ff3 when watching youtube. In ff3 I can have as many tabs opened but cpu usage remains low because bartab is working pproperly.

However, on my machine with the Nvidia card vdpau is definitly not working for the gecko-player pluggin for ff4. For the same youtube clips using flashvideoreplacer cpu usage in ff4 is way higher than in ff3, it is as if vdpau is not used (I waited til the videos were  100% loaded before playback to make sure it has nothing to do with slow internet or the streaming)

P.S. Just updated to ff4 b11 and apparently all open tabs are wiped out everytime ff4 restarts. Maybe that is how they solve the problem. :)

Thanks for the heads up. Good to know you was able to find the culprit.

---

### Post by lovinglinux on 2011-02-23
FlashVideoReplacer 2.0.3 has been released and is available for download.

Changelog

* added support for Ustream and Blip.tv
* added support for VLC player
* added option to delay video replacement, to deal with related videos thumbnails not being loaded on YouTube.
* fixed preferences dialog scroll bar
* force plugin compatibility when pluginreg.dat do not exists
* removed plugin check tool

---

### Post by user68 on 2011-03-07
I tried flashvideoreplacer hoping it would fix a problem I have but am not sure if I'm doing it right. This is what I have:

Ubuntu 10.04 32 bit
Celeron 540 2.0Ghz CPU
Intel X3100 video card
Adobe Flash 10.2 + Mozilla plug-in

I'm trying to watch a Wowza multi bitrate RMTP stream in Firefox. The stream opens at high resolution then quickly changes permanently to low resolution video. It's not a bandwidth issue and I don't think the ISP is throttling port 1935 (but awaiting confirmation). I've tried changing the Adobe Flash settings to disable hardware acceleration but the settings box is greyed-out when I right click.

So, I decided to use flashvideoreplacer but it's not curing the problem. In fact, if I right click in the streaming window I see at the bottom that the flash window is still Adobe 10.2.

So my questions are, could flashvideoreplacer potentially allow me to watch a better quality video stream and, if so, what must I do to get it to actually replace Adobe?

---

### Post by lovinglinux on 2011-03-08
> **user68 said:**
> I tried flashvideoreplacer hoping it would fix a problem I have but am not sure if I'm doing it right. This is what I have:

Ubuntu 10.04 32 bit
Celeron 540 2.0Ghz CPU
Intel X3100 video card
Adobe Flash 10.2 + Mozilla plug-in

I'm trying to watch a Wowza multi bitrate RMTP stream in Firefox. The stream opens at high resolution then quickly changes permanently to low resolution video. It's not a bandwidth issue and I don't think the ISP is throttling port 1935 (but awaiting confirmation). I've tried changing the Adobe Flash settings to disable hardware acceleration but the settings box is greyed-out when I right click.

So, I decided to use flashvideoreplacer but it's not curing the problem. In fact, if I right click in the streaming window I see at the bottom that the flash window is still Adobe 10.2.

So my questions are, could flashvideoreplacer potentially allow me to watch a better quality video stream and, if so, what must I do to get it to actually replace Adobe?

FlashVideoReplacer only works on certain sites. Please visit the extension web site for documentation and supported sites list.

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

---

### Post by Gonzalo_VC on 2011-03-09
Yes, replace FlashPlugins whenever possible. 
Flash keeps crashing under Linux (I'm using Ubuntu), 32 or 64 bits, and is not open source.
We really need an open source replacement for all this Adobe stuff, urgently!
Godspeed GNU!!!

---

### Post by lovinglinux on 2011-03-11
FlashVideoReplacer 2.1.0 has been released and is available for download. This version brings a new set of improvements in the interface and video detection.

**What has changed? **

The context menu has been moved to the toolbar icon, thus reducing the context menu clutter.

The extension no longer opens the video automatically, but replaces the video with a placeholder. So in order to play it, the user just need to click the placeholder. This behavior can't be changed when using the "Standalone", "New Tab" or "New Window" methods. However, if the user wants to play the video automatically when using the "Embedded" replacing method, there is an option in the preferences to skip the placeholder.

Below the placeholder, there is a menu that offers the ability to choose the replacing method on-the-fly. So there is no more "Prompt" method in the options and there is no more prompt dialog.

**See attached screenshot**

In this version is also possible to disable/enable the extension by middle-click over the toolbar icon. So if the user wants to disable the extension temporarily, there is no more need to untick all sites in the preferences. However, these options are still available, if the user wants to turn the extension off permanently for a specific site.

The YouTube quality settings has changed a little bit. Now, there is "LOW", "MEDIUM", "HIGH" and "SUPER" quality settings.

[LIST]
[*]"LOW" best video quality up to 360p if available
[*]"MEDIUM" best video quality up to 480p if available
[*]"HIGH" best video quality up to 720p if available
[*]"SUPER" best video quality over 1080p if available
[/LIST] 

Due to performance issues, on Firefox 3.x the extension will detect less video formats in the download menu. Firefox 4 has the same behavior of previous versions and lists all available formats in the selected quality range.

**Changelog**
[LIST]
[*]added placeholder with a replacing method menu
[*]removed prompt dialog
[*]moved context menu to toolbar menu
[*]added option to disable/enable the extension with a middle click on toolbar icon
[*]expanded YouTube quality options
[*]switched to asynchronous XMLHttpRequest
[*]path detection using environment variables 
[/LIST]

---

### Post by lovinglinux on 2011-03-19
Version 2.1.1 has been released to address some potential security issues, that prevented version 2.1.0 from being approved by Mozilla.

---

### Post by racoq on 2011-03-19
Hello Lovinglinux

First of all congratulations for your effort on replacing embedded flash videos with mplayer (using gnome-mplayer + gecko-mediaplayer 0.9.9.2 from lucid)

I'm using your latest version on firefox 4.0 RC, with a few caveats.

- In youtube some pages aren't "caught by your plugin" see for instance this on this page [http://www.youtube.com/user/wtofficial](http://www.youtube.com/user/wtofficial), and try to play the video that is presented on that page. However if you play the same video as a separate link isolated from that page, it is caught by your plugin.

- I see some fragments on video (squares or "blocking"). Specially if you use full screen and abandon full screen, some times.
- About the plugin preference (prefer mp4 over flv), i find that the quality when i "prefer mp4 over flv videos,  is worst (more noise/squares on image) when this option is enabled. Is that normal?

---

### Post by lovinglinux on 2011-03-20
> **racoq said:**
> Hello Lovinglinux

First of all congratulations for your effort on replacing embedded flash videos with mplayer (using gnome-mplayer + gecko-mediaplayer 0.9.9.2 from lucid)

Thank you. I wish I could get rid of flash completely :-)

> **racoq said:**
> 
- In youtube some pages aren't "caught by your plugin" see for instance this on this page [http://www.youtube.com/user/wtofficial](http://www.youtube.com/user/wtofficial), and try to play the video that is presented on that page. However if you play the same video as a separate link isolated from that page, it is caught by your plugin.

The extension does not work on YouTube channels, only on video pages. That's why it works when you isolate the video from the channel. 

> **racoq said:**
> - I see some fragments on video (squares or "blocking"). Specially if you use full screen and abandon full screen, some times.

Unfortunately, that depends on the original video quality. The extension will try to get the best video available according to the quality settings in you preferences, but not all quality versions are available for all videos.

> **racoq said:**
> - About the plugin preference (prefer mp4 over flv), i find that the quality when i "prefer mp4 over flv videos,  is worst (more noise/squares on image) when this option is enabled. Is that normal?

Yes, is normal because the most common mp4 file for low resolution videos has only 480x360. The reason for providing that option is because some players, specially on Windows, cannot play flv files. So when you select the option to prefer mp4, the extension will give priority to the 360p mp4 version, even if a flv version with better resolution is available. However, if  you choose the HIGH or SUPER quality and the video is availabe as 720p or higher, then the low resolution mp4 will be ignored.

On Linux you can safely disable the option to prefer mp4, in order to get better resolution on videos without 720p versions.

---

### Post by RobbieThe1st on 2011-03-20
This -looks- like a very interesting plugin, but it doesn't seem to work for me; at least, not with what I'm trying to do.
When I go to redvsblue, which uses blip.tv for it's videos, the flash player isn't getting replaced. Here's an example page: [http://redvsblue.com/archive/?id=2991](http://redvsblue.com/archive/?id=2991)

Also, is there any way to have your extension play webm html5 videos with mplayer? I've been having some issues with lagging and dropped frames in the built-in player; playing them through mplayer gives me at least partial hardware-acceleration too, so if there's any way of using it I'd really appreciate it.

Thanks,

-Rob

---

### Post by lovinglinux on 2011-03-20
> **RobbieThe1st said:**
> This -looks- like a very interesting plugin, but it doesn't seem to work for me; at least, not with what I'm trying to do.
When I go to redvsblue, which uses blip.tv for it's videos, the flash player isn't getting replaced. Here's an example page: [http://redvsblue.com/archive/?id=2991](http://redvsblue.com/archive/?id=2991)

The extension only works on supported web sites, not on third-party sites with embedded videos.

See the extension documentation for a list of supported sites:

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)

> **RobbieThe1st said:**
> Also, is there any way to have your extension play webm html5 videos with mplayer? I've been having some issues with lagging and dropped frames in the built-in player; playing them through mplayer gives me at least partial hardware-acceleration too, so if there's any way of using it I'd really appreciate it.

Thanks,

-Rob

Unfortunately, no. There is no plugin capable of playing webm, after all webm is new and was designed to work without a plugin.

---

### Post by RobbieThe1st on 2011-03-20
> **lovinglinux said:**
> 
Unfortunately, no. There is no plugin capable of playing webm, after all webm is new and was designed to work without a plugin.
Now, wait a second - Why not? 
webm video is VP8 video + OGG audio inside a Matroska container. I just found a webm sample video, setup a proper object tag giving the mime-type as matroska instead of webm, and it now plays it with gnome-mplayer:
```

<html>
<head><title>Test HTML5 video through container</title></head>
<body>
<object type="video/x-matroska" data="http://www.ioncannon.net/examples/vp8-webm/big_buck_bunny_480p.webm" width="640" height="480">
  <param name="src" value="http://www.ioncannon.net/examples/vp8-webm/big_buck_bunny_480p.webm" />
  <param name="controller" value="true" />
  <param name="autostart" value="true" />
</object>
</body>
</html> 

```
Example(with a different video): [http://robbiethe1st.afraid.org/test/videotest.html](http://robbiethe1st.afraid.org/test/videotest.html)
Looks like all you'd need to do is change the mime-type on webm files to make them play with your external player - Provided, of course that you've got the VP8 codec installed.

---

### Post by lovinglinux on 2011-03-20
> **RobbieThe1st said:**
> Now, wait a second - Why not? 
webm video is VP8 video + OGG audio inside a Matroska container. I just found a webm sample video, setup a proper object tag giving the mime-type as matroska instead of webm, and it now plays it with gnome-mplayer:
```

<html>
<head><title>Test HTML5 video through container</title></head>
<body>
<object type="video/x-matroska" data="http://www.ioncannon.net/examples/vp8-webm/big_buck_bunny_480p.webm" width="640" height="480">
  <param name="src" value="http://www.ioncannon.net/examples/vp8-webm/big_buck_bunny_480p.webm" />
  <param name="controller" value="true" />
  <param name="autostart" value="true" />
</object>
</body>
</html> 

```
Example(with a different video): [http://robbiethe1st.afraid.org/test/videotest.html](http://robbiethe1st.afraid.org/test/videotest.html)
Looks like all you'd need to do is change the mime-type on webm files to make them play with your external player - Provided, of course that you've got the VP8 codec installed.

I was actually referring to playing the webm container directly. Changing the mime-type as you did will work, provided that you have the proper codec. However I don't see how this would help. If you want to play webm videos from YouTube, simply disable the webm option in the extension preferences and the extension will redirect to the regular YouTube page instead of the html5 page, which will be replaced and will use a mp4 or flv source file with gecko-mediaplayer. Is that what you want?

---

### Post by RobbieThe1st on 2011-03-20
> **lovinglinux said:**
> I was actually referring to playing the webm container directly. Changing the mime-type as you did will work, provided that you have the proper codec. However I don't see how this would help. If you want to play webm videos from YouTube, simply disable the webm option in the extension preferences and the extension will redirect to the regular YouTube page instead of the html5 page, which will be replaced and will use a mp4 or flv source file with gecko-mediaplayer. Is that what you want?
What I was hoping for is to use your extension to re-write the webm container into something that will play the webm file through gecko-mediaplayer.
This will do three things: 1, it will provide hardware-acceleration through mplayer,  2, a nice right-click save-as option, and 3, proper html5 fullscreen playback.
Yes, I suppose I could just use mp4 or flv... but dangit, webm's the future, why shouldn't we be able to use it just as well? The codec's are all there; all that's needed is a dozen or so lines of JS to re-write the container.

---

### Post by lovinglinux on 2011-03-20
> **RobbieThe1st said:**
> What I was hoping for is to use your extension to re-write the webm container into something that will play the webm file through gecko-mediaplayer.
This will do three things: 1, it will provide hardware-acceleration through mplayer,  2, a nice right-click save-as option, and 3, proper html5 fullscreen playback.
Yes, I suppose I could just use mp4 or flv... but dangit, webm's the future, why shouldn't we be able to use it just as well? The codec's are all there; all that's needed is a dozen or so lines of JS to re-write the container.

Well, the whole purpose of webm is to play video without plugins. So I guess nobody will try to do what you want. In regard to the extension, just disable the webm option and you will be fine.

---

### Post by RobbieThe1st on 2011-03-21
Isn't the whole purpose of your application, though, to lower CPU usage -through- the use of native plugins?

Oh well. Never mind then. I suppose I can just use Greasemonkey.

---

### Post by lovinglinux on 2011-03-21
> **RobbieThe1st said:**
> Isn't the whole purpose of your application, though, to lower CPU usage -through- the use of native plugins?

Oh well. Never mind then. I suppose I can just use Greasemonkey.

You are not getting my point. The point is that you don't need webm whatsoever when using my extension. So why would I provide support for a webm hack, when I can bypass the webm page and use gecko-mediaplayer with my extension?

Such a hack would only be useful if YouTube didn't provide a regular flash player page for all videos.

---

### Post by lovinglinux on 2011-03-24
Version 2.1.2 released. This version fixes YouTube, which was broken due to changes in their source code.

---

### Post by diazamet on 2011-03-26
Any news on FlashVideoReplacer for Chrome?

---

### Post by lovinglinux on 2011-03-26
> **diazamet said:**
> Any news on FlashVideoReplacer for Chrome?

I have been extremely busy updating my Firefox extensions lately.

I will post here whenever a version for Opera or Chrome is ready.

---

### Post by lovinglinux on 2011-03-26
Released version 2.1.3, which addresses an issue with 720p video detection on youtube, added a "Silent Download" option and German translation.

---

### Post by lovinglinux on 2011-03-26
Version 2.1.4 available for download.

* added support for html5 beta program pages on YouTube

---

### Post by lovinglinux on 2011-03-29
FlashVideoReplacer 2.1.5 has been released and is available for download.

This version brings some important updates. For instance, FlashVideoReplacer no longer requires flash plugin to be installed to work. Additionally, it is now compatible with the popular Flashbock extension. This means you can block flash content on supported sites using Flashblock to improve performance. FlashVideoReplacer will replace the Flashblock placeholder with it's own placeholder. There is also individual options to play the video automatically with each replacing method. So if you are using Flashblock and the "Embedded" replacing method, you can watch the videos immediately, without additional clicks and without loading any flash on the page.

Another new feature available is the "Fallback Player". This option allows you to play the videos with flash, if the extension cannot detect a compatible plugin, but using a different flash player like Flowplayer or Neolao's player.

The extension preferences dialog has been redesigned and is less cluttered now.  

**Changelog**

[LIST]
[*]works without flash plugin installed
[*]added compatibility with Flashblock extension
[*]added option to play videos using Flowplayer or Neolao's player when the replacement plugin cannot handle the video format
[*]added individual options to automatically load the video with each replacing method
[*]new improved options dialog
[*]improved placeholder formatting
[*]added support for html5 beta program pages on Youtube (v 2.1.4)
[*]fixed 720p detection on YouTube (v 2.1.3)
[*]added silent download option (v 2.1.3)
[*]added German translation (v 2.1.3)
[/LIST]

---

### Post by lovinglinux on 2011-03-31
FlashVideoReplacer 2.1.6 has been released and is available for download.

The extension has support for downloading videos with DownThemAll! and brings some overlay enhancements, like hover effects and video preview images.

**Changelog**

[LIST]
[*]added support for downloads with DownThemAll!
[*]added video preview image as background on YouTube, Vimeo and Ustream
[*]added hover effect to overlay elements
[*]toolbar icon changes dynamically to indicate supported sites
[*]split alerts into three categories (errors, video info and tips)
[/LIST]

---

### Post by messier on 2011-04-01
Hi, is there no option for 1080p Youtube videos for now?
Something seems to be mixed up, because on 1080p videos the max available resolution trough this plugin is 720p and on 720p videos its only 480p.

Other than that, this plugin is really great. Keep up the good work :)

Edit: Sorry, my mistake, I used version 2.1.2. This plugin is just great... Thanks a lot!

---

### Post by dBuster on 2011-04-05
Not exactly sure what is going on but I am frustrated.

Firefox 4.0 - tried with no adblock or flashget and same result - nothing!
64 bit flash - You have version 10,3,162,29 installed
FlashVideoReplacer 2.1.2

Now when I need it for Youtube I have no problems it works as it is supposed to.  

However with the eagle hatchings going on I can not get it to work with ustream!  Here is the website of what I am trying to watch : [Decorah Eagles]("http://www.ustream.tv/decoraheagles")

No matter what I do I can not get ustream to play on my system.  Either in chrome, which I know you do not have an extension for, or in Firefox which I have the extension. 

Any ideas?  Would like to catch some of this years eagle hatches...

---

### Post by lovinglinux on 2011-04-05
> **messier said:**
> Edit: Sorry, my mistake, I used version 2.1.2. This plugin is just great... Thanks a lot!

You are welcome.

> **dBuster said:**
> Not exactly sure what is going on but I am frustrated.

Firefox 4.0 - tried with no adblock or flashget and same result - nothing!
64 bit flash - You have version 10,3,162,29 installed
FlashVideoReplacer 2.1.2

Now when I need it for Youtube I have no problems it works as it is supposed to.  

However with the eagle hatchings going on I can not get it to work with ustream!  Here is the website of what I am trying to watch : [Decorah Eagles]("http://www.ustream.tv/decoraheagles")

No matter what I do I can not get ustream to play on my system.  Either in chrome, which I know you do not have an extension for, or in Firefox which I have the extension. 

Any ideas?  Would like to catch some of this years eagle hatches...

Hi,

First of all, I would like to recommend that you get version 2.1.6 from my website or from the "All versions" page at Mozilla:

[http://www.webgapps.org/addons/flashvideoreplacer](http://www.webgapps.org/addons/flashvideoreplacer)
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/versions/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/versions/)

This version has tons of improvements.

About the problem with Ustream, is my fault. Sorry. I wasn't clear that it doesn't work with live streams, only recorded videos. Unfortunately, supporting live streams is a lot more complicated than recorded videos and I am not even sure if it is possible to do it. At some point I will try to implement such feature, but that is something will probably demand a lot of time. I have been working on FVR a lot and there is still tons of things to improve and feature requests to fulfill.

---

### Post by lovinglinux on 2011-04-07
EDIT: See next post.

---

### Post by lovinglinux on 2011-04-09
**IMPORTANT:** FlashVideoReplacer 2.1.8 has been released and has a workaround to deal with recent YouTube problems. However, the standalone replacing method won't work anymore, unless you block YouTube cookies in Firefox preferences.

---

### Post by lovinglinux on 2011-04-10
**Announcement: FlashVideoReplacer Development Channel **

Is not uncommon for a supported web site like YouTube to change their source code, which can break FlashVideoReplacer extension functionality. I usually fix such issues in the same day I receive a bug report. However, due to the time required for Mozilla to review and approve new versions, the version available for download at Mozilla site might still be broken.

To avoid this issue, I have made available a Development Channel, with the latest versions of FlashVideoReplacer. These versions are usually the same as the latest stable version under review, but they are updated automatically by Firefox Add-ons Manager independently of the review process.

Keep in mind that once you start using a development version, you will always get such versions in the future, unless you manually install a stable version.
If you don't want to use the Development Channel, you can always get the latest stable version waiting for review in the All versions page at Mozilla or from this web site.

**Latest Update:** FlashVideoReplacer 2.1.8 and 2.1.9pre have a workaround to deal with recent YouTube problems. However, the standalone replacing method won't work anymore, unless you block YouTube cookies in Firefox preferences.

---

### Post by beew on 2011-04-11
Hi, 

Don't know if this problem has been reported but I just noticed that flashvideoreplacer has stopped working at all on youtube. It is as if it has not been installed at all. (FF4 and flashvideoreplacer 2.1.2, same problem in Maverick and Natty)

Is that fixed in version 2.1.8? (will try that when I have access to Ubuntu)

Thanks.

---

### Post by lovinglinux on 2011-04-11
> **beew said:**
> Hi, 

Don't know if this problem has been reported but I just noticed that flashvideoreplacer has stopped working at all on youtube. It is as if it has not been installed at all. (FF4 and flashvideoreplacer 2.1.2, same problem in Maverick and Natty)

Is that fixed in version 2.1.8? (will try that when I have access to Ubuntu)

Thanks.

Yes. It stopped because YouTube shut down youtube-nocookie.com. Version 2.1.8 and 2.1.9pre works. However, if you use a standalone external player, then you need to block YouTube cookies, otherwise the player won't play the content.

---

### Post by drieg500 on 2011-04-14
Having a problem here, using 2.1.9b.

I'm supposed to disable cookies right? But when I do that, I apparently signed out and when I do try to sign in, it just redirects me to the home page (supposedly it remembers the login) but with my account still not signed in. But when I turn on cookies, I have my account logged in. Its pretty annoying since I have subscriptions.

Any workaround on this?

EDIT: This is probably not a problem with the plugin, it works great, but the thing with the cookie is rather annoying.

---

### Post by lovinglinux on 2011-04-14
> **drieg500 said:**
> Having a problem here, using 2.1.9b.

I'm supposed to disable cookies right? But when I do that, I apparently signed out and when I do try to sign in, it just redirects me to the home page (supposedly it remembers the login) but with my account still not signed in. But when I turn on cookies, I have my account logged in. Its pretty annoying since I have subscriptions.

Any workaround on this?

EDIT: This is probably not a problem with the plugin, it works great, but the thing with the cookie is rather annoying.

The cookie thing is really a big problem, but I don't have a solution yet. Keep in mind that if you are not using a standalone external player, then you don't need to block YouTube cookies. You can replace the video using gecko-mediaplayer.

---

### Post by drieg500 on 2011-04-14
> **lovinglinux said:**
> The cookie thing is really a big problem, but I don't have a solution yet. Keep in mind that if you are not using a standalone external player, then you don't need to block YouTube cookies. You can replace the video using gecko-mediaplayer.

How do I use an external player/replace totem player? I'm pretty new to ubuntu, just switched for 3 weeks.

---

### Post by lovinglinux on 2011-04-14
> **drieg500 said:**
> How do I use an external player/replace totem player? I'm pretty new to ubuntu, just switched for 3 weeks.

When you see the FlashVideoReplacer icon over a video, click the menu below it and select "Standalone". If you have a compatible standalone player (most likely you do), it will launch the video using it. If the extension cannot detect a compatible video player you can specify the path manually in the extension preferences. Keep in mind it works fine with other supported sites, but on YouTube it doesn't work unless you block cookies. This is happening since Youtube killed the nocookie site. So the recommended method of replacement for YouTube is "Embedded", "New Tab" or "New Window", which will use a Firefox plugin to play the video. I suppose you are using totem plugin, which is not the recommended one and only works if you change the mime type in the extension preferences. So remove it and install gecko-mediaplayer.

You can do that via terminal, by running these commands:

```
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```

After running those commands, restart Firefox, visit a Youtube video page, select "Embedded" in the FlashVideoreplacer menu and click the logo. The video will play in the original location, using gecko-mediaplayer instead of flash.

---

### Post by lovinglinux on 2011-04-14
> **siverekoto said:**
> thank you [te&#351;ekkürler dostum]("http://www.hasarli.com")

You are welcome.

---

### Post by drieg500 on 2011-04-14
> **lovinglinux said:**
> You can do that via terminal, by running these commands:

```
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```After running those commands, restart Firefox, visit a Youtube video page, select "Embedded" in the FlashVideoreplacer menu and click the logo. The video will play in the original location, using gecko-mediaplayer instead of flash.

Thanks man. Finally works better. Hoping for a workaround for the cookies soon.

EDIT: No problem with the cookies. Just enabled them again. No problems with the player whatsoever. Thanks for the quick response.

---

### Post by lovinglinux on 2011-04-14
> **drieg500 said:**
> Thanks man. Finally works better. Hoping for a workaround for the cookies soon.

EDIT: No problem with the cookies. Just enabled them again. No problems with the player whatsoever. Thanks for the quick response.

You are welcome.

---

### Post by beew on 2011-04-30
Hi, 

I am having a bit of problem again with flashvideoreplacer. It works perfectly on one install (Maverick) but stops working (it used to work) in Natty and another Maverick.

The version of FlashVideoReplacer is 2.1.8 for all three.   For the two installs where it doesn't work, I have to clear the youtube cookies everytime I watch something, I would have to clear the cookies again if I want to watch another clip. Moreover, while I can see the videos after clearing the cookies, the status bar doesn't show.

I use "embed" mode in all three installations.

gnome-mplayer works on all three installs (in the Maverick install that FlashVideoReplacer fails to work gnome-mplayer stops if video output is not left blank, it may have something to do with the Nividia driver)

Thanks.

P.S. upgraded FlashVideoReplacer to 2.19pr in the Maverick install where FVP doesn't work, it didn't help.

---

### Post by lovinglinux on 2011-04-30
> **beew said:**
> Hi, 

I am having a bit of problem again with flashvideoreplacer. It works perfectly on one install (Maverick) but stops working (it used to work) in Natty and another Maverick.

The version of FlashVideoReplacer is 2.1.8 for all three.   For the two installs where it doesn't work, I have to clear the youtube cookies everytime I watch something, I would have to clear the cookies again if I want to watch another clip. Moreover, while I can see the videos after clearing the cookies, the status bar doesn't show.

I use "embed" mode in all three installations.

gnome-mplayer works on all three installs (in the Maverick install that FlashVideoReplacer fails to work gnome-mplayer stops if video output is not left blank, it may have something to do with the Nividia driver)

Thanks.

P.S. upgraded FlashVideoReplacer to 2.19pr in the Maverick install where FVP doesn't work, it didn't help.

What do you mean by status bar?

---

### Post by beew on 2011-04-30
The white bar in the bottom showing progress, % dwonloaded and the full screen button.

Just remove .mozilla foldder and restart, no luck still.

---

### Post by lovinglinux on 2011-04-30
> **beew said:**
> The white bar in the bottom showing progress, % dwonloaded and the full screen button.

Just remove .mozilla foldder and restart, no luck still.

Check if you do not have another plugin like vlc or mozplugger installed. If the video controls are not showing, then most likely you have a different plugin taking over the content.

---

### Post by beew on 2011-04-30
I have mozplugger installed for reading embedded pdf but I have it on all 3 Ubuntu installs.

---

### Post by beew on 2011-04-30
Uninstalled Mozplugger in Natty and FPR now works. But what I don't understand is I also have Mozplugger installed  in the Mavarick where FPR works and I have always installed Mozplugger in all my Ubuntu installations as i need it for viewing inline pdf and doc files, etc.

Is there a way I can edit Mozplugerrc so that it doesn't interfere with FVP?

Thanks.

---

### Post by lovinglinux on 2011-04-30
> **beew said:**
> Uninstalled Mozplugger in Natty and FPR now works. But what I don't understand is I also have Mozplugger installed  in the Mavarick where FPR works and I have always installed Mozplugger in all my Ubuntu installations as i need it for viewing inline pdf and doc files, etc.

Is there a way I can edit Mozplugerrc so that it doesn't interfere with FVP?

Thanks.

You are welcome.

I am not sure, but I suppose the order of installation might interfere in which plugin is loaded first. You could try to remove both plugins, then install mozplugger, then install gecko. If that doesn't work, try the invert order.

Unfortunately, I can't help you with the mozplugger plugin configuration.

I remember that some years ago there was an extension that allowed to choose between multiple plugins. I will look into that.

On a side note, I use [gPDF]("https://addons.mozilla.org/en-US/firefox/addon/14814/") extension, which allows to view PDF with Google Docs.

---

### Post by beew on 2011-04-30
I have tried editing mozpluggerrc by removing all texts under video and audio but FVR doesn't work. The only way is to remove mozplugger for it to work. It doesn't sound good. :(

Just saw your last post, will try reinstalling the plugins and see how it goes, thanks.

---

### Post by lovinglinux on 2011-05-05
FlashVideoReplacer 2.1.9 has been released and is available for download.

This version fixes recent YouTube changes.

A new version is also available in the Beta Channel.

---

### Post by lovinglinux on 2011-05-12
I have released version 2.1.10pre2 in the Development Channel, which brings a video quality selector in the placeholder (YouTube only). This feature is only available to Firefox 4 users, due to performance issues.

Please test it and give some feedback about performance and the functionality itself.

---

### Post by rent0n on 2011-05-23
Just wanted to say thanks for this great add-on.

I'm using it on Debian Squeeze installed on an Apple PowerMac G5.
On the PPC architecture (where Adobe Flash is not available) it performs better than Gnash! That's quite an important achievement to be proud of!

It doesn't work with the browser-plugin-parole though, so I had to install the gecko-mediaplayer plugin, are you aware of the issue? Parole is the official Xfce player.

Thanks!

---

### Post by lovinglinux on 2011-05-23
> **rent0n said:**
> Just wanted to say thanks for this great add-on.

I'm using it on Debian Squeeze installed on an Apple PowerMac G5.
On the PPC architecture (where Adobe Flash is not available) it performs better than Gnash! That's quite an important achievement to be proud of!

It doesn't work with the browser-plugin-parole though, so I had to install the gecko-mediaplayer plugin, are you aware of the issue? Parole is the official Xfce player.

Thanks!

Hi,

Thanks for your comments.

I have tested the parole plugin. Indeed it doesn't work at all. I need more time to test tho. Anyway, gecko is the best.

---

### Post by beew on 2011-05-23
> **rent0n said:**
> Just wanted to say thanks for this great add-on.

I'm using it on Debian Squeeze installed on an Apple PowerMac G5.
On the PPC architecture (where Adobe Flash is not available) it performs better than Gnash! That's quite an important achievement to be proud of!


That is interesting. i thought that even if you use FVR flash has to be installed. I have installed FVR in Fedora 15without Flash and it doesn't work. Maybe FVR doesn't work for Fedora? (I should install Flash and try again and see if FVR works but Fedora 15 has crashes and burned and needs a reinstall, haven't gotten around to do that)

---

### Post by lovinglinux on 2011-05-23
> **beew said:**
> That is interesting. i thought that even if you use FVR flash has to be installed. I have installed FVR in Fedora 15without Flash and it doesn't work. Maybe FVR doesn't work for Fedora? (I should install Flash and try again and see if FVR works but Fedora 15 has crashes and burned and needs a reinstall, haven't gotten around to do that)

Recent versions of FVR doesn't need flash. If it doesn't work, let me know so I can troubleshoot.

FVR should work with any OS, however experience may vary depending on available plugins and players.

---

### Post by beew on 2011-05-23
> **lovinglinux said:**
> Recent versions of FVR doesn't need flash. If it doesn't work, let me know so I can troubleshoot.
.

It doesn't work without Flash in Fedora 15, need to check if it works with Flash (in case something else is broken) after reinstalling Fedora.

---

### Post by lovinglinux on 2011-05-23
> **beew said:**
> It doesn't work without Flash in Fedora 15, need to check if it works with Flash (in case something else is broken) after reinstalling Fedora.

Test not only with YouTube, because it is the most problematic.

What happens is that when flash is not detected, YouTube overlays a new element with the warning over the video object. I have included a code to remove that element, but sometimes things get loaded in a different order and FVR fails to replace the video.

---

### Post by lovinglinux on 2011-06-20
Version 2.1.12 has been released.

This version fixes YouTube cookie issues, that previously required to block cookies to play the videos with external players. No more need to block cookies. This version also fixes some code leak that was interfering with another extension.

Blip.tv support has been removed temporarily, due to changes in their site.

---

### Post by Tesno on 2011-06-23
This would be pure awesomeness, but... I can't get it to work. How come the vlc url is so complicated, vlc can basically open normal youtube url? Also tried this with Windows Xp with several players without any success. (Embed quicktime worked ok, but sucks from different reasons)

---

### Post by lovinglinux on 2011-06-23
> **Tesno said:**
> This would be pure awesomeness, but... I can't get it to work. How come the vlc url is so complicated, vlc can basically open normal youtube url? Also tried this with Windows Xp with several players without any success. (Embed quicktime worked ok, but sucks from different reasons)

First make sure you have FlashVideoReplacer 2.1.12. Previous versions suffer from a problem that prevented FVR from opening videos on external players unless you block YouTube cookies. This has been fixed on version 2.1.12. It seems this fix also makes VLC work now, however it is still considered not fully supported until I can make sure it doesn't suffer any issues.

FVR doesn't open regular YouTube urls, because not all players can handle that. What is does is to fetch the real video url in the original format and parse it to the player. This means your player needs to be capable of playing mp4 and flv.

Unfortunately for Windows users, there aren't many options. FVR was essentially created to solve a problem with Flash in Linux, which has a wide variety of players and plugins that can handle mp4.

If you are trying to play the videos with totem plugin on Linux, then change the Mime Type in the FVR preferences to x-totem-plugin. However I would recommend using gecko-mediaplayer instead. BTW, although VLC player is an excellent player, the plugin is terrible. Don't use VLC plugin for embedded video. There are much better plugins for Linux.

Please let me know if this helps or not.

---

### Post by Tesno on 2011-06-23
Okay, it seems to work decently now. One video didn't work with vlc though. I'll try to test if there's more. Is there a way to use 240p videos by default? I presume lowest quality should offer 240p first?

---

### Post by lovinglinux on 2011-06-23
> **Tesno said:**
> Okay, it seems to work decently now. One video didn't work with vlc though. I'll try to test if there's more. Is there a way to use 240p videos by default? I presume lowest quality should offer 240p first?

Actually, it will select the best resolution between 240p and 360p. But you can override it, by selecting the resolution before clicking the placeholder.

I could invert the selection sequence to default to 240p, but YouTube also defaults to 360p and I received some complains about low quality, so I programmed the extension to default to the best resolution among each range.

BTW, if it fails with VLC, reload the page. Sometimes it fails here too, but works after a reload. Anyways, I recommend using smplayer instead.

---

### Post by lovinglinux on 2011-07-15
Version 2.1.13 has been released.

This version brings minor bug fixes and compatibility with Firefox 8.0a1.

---

### Post by geoaraujo on 2011-07-16
> **lovinglinux said:**
> Version 2.1.13 has been released.

This version brings minor bug fixes and compatibility with Firefox 8.0a1.
I like this app, but I belive that having video controls (like when watching youtube videos on flash) is something really essential and that prevents me from using it. Is it posible to add those to Flash Video Replacer?
I know that we can change settings to watch videos on an external player (like mplayer), but I'd prefer to watch them on the same web page...

---

### Post by lovinglinux on 2011-07-16
> **geoaraujo said:**
> I like this app, but I belive that having video controls (like when watching youtube videos on flash) is something really essential and that prevents me from using it. Is it posible to add those to Flash Video Replacer?
I know that we can change settings to watch videos on an external player (like mplayer), but I'd prefer to watch them on the same web page...

The video controls are not something I can change, because it depends on the plugin you are using for viewing the videos. FlashVideoReplacer just replaces the video object, so the browser can play it with a different plugin. Once the video is replaced and starts palying, FlashVideoReplacer is simply inactive.

If you don't have controls, then most likely you have a VLC plugin or something else. While VLC is a great player, the plugin isn't. I recommend removing your current media plugins and installing gecko-mediaplayer. If you need to keep the plugins for some reason, then install gecko-mediaplayer and change the Mime Type option in FlashVideoReplacer preferences to matroska. This will most likely to make FVR videos open with gecko-mediaplayer instead of other plugins.

---

### Post by geoaraujo on 2011-07-16
> **lovinglinux said:**
> The video controls are not something I can change, because it depends on the plugin you are using for viewing the videos. FlashVideoReplacer just replaces the video object, so the browser can play it with a different plugin. Once the video is replaced and starts palying, FlashVideoReplacer is simply inactive.

If you don't have controls, then most likely you have a VLC plugin or something else. While VLC is a great player, the plugin isn't. I recommend removing your current media plugins and installing gecko-mediaplayer. If you need to keep the plugins for some reason, then install gecko-mediaplayer and change the Mime Type option in FlashVideoReplacer preferences to matroska. This will most likely to make FVR videos open with gecko-mediaplayer instead of other plugins.
It worked... but it seems I can't click on, say, minute five of a 9 min lenght video to watch it from that point.
Is this correct?

---

### Post by lovinglinux on 2011-07-16
> **geoaraujo said:**
> It worked... but it seems I can't click on, say, minute five of a 9 min lenght video to watch it from that point.
Is this correct?

Unfortunately, is correct. You can only click on a point that has been buffered already. Depending on the plugin, it will start buffering from that point, but not gecko-mediaplayer. This problem doesn't occur with standalone players, like SMplayer, VLC or Gnome Mediaplayer.

---

### Post by geoaraujo on 2011-07-17
> **lovinglinux said:**
> Unfortunately, is correct. You can only click on a point that has been buffered already. Depending on the plugin, it will start buffering from that point, but not gecko-mediaplayer. This problem doesn't occur with standalone players, like SMplayer, VLC or Gnome Mediaplayer.
I see.. what a shame... Other plugins don't handle it quite well neither...Why does that happen with some plugins and with others it doesn't?

---

### Post by beew on 2011-07-17
> **geoaraujo said:**
> I see.. what a shame... Other plugins don't handle it quite well neither...Why does that happen with some plugins and with others it doesn't?

Maybe I misunderstood, with the gecko plugin I can play at any point that has been buffered without starting from the beginning, so I am not sure what the problem is (with DIVX videos I can't, once started I can't move back and forth) Even with flash you can't start with a point that has not been buffered!

---

### Post by geoaraujo on 2011-07-22
> **beew said:**
> Maybe I misunderstood, with the gecko plugin I can play at any point that has been buffered without starting from the beginning, so I am not sure what the problem is (with DIVX videos I can't, once started I can't move back and forth) Even with flash you can't start with a point that has not been buffered!
The thing is, based on what I've understood, unlike flash video replacer (at least with gecko), with flash plugin it's possible to *start buffering from a certain point*.

---

### Post by beew on 2011-07-29
Hi, 

It seems that the FVR has stopped working on Youtube. If I access Youtube with the FVR whole screen disappears! Disabling the FVR and use flash then it still works fine.

---

### Post by lovinglinux on 2011-07-29
> **beew said:**
> Hi, 

It seems that the FVR has stopped working on Youtube. If I access Youtube with the FVR whole screen disappears! Disabling the FVR and use flash then it still works fine.

Thanks for reporting.

I have already received some similar reports and verified that YouTube indeed changed again. I will try to fix this as soon as possible.

---

### Post by lovinglinux on 2011-07-31
Version 2.1.14pre and 2.1.14 have been released with a YouTube fix.

---

### Post by beew on 2011-07-31
> **lovinglinux said:**
> Version 2.1.14pre and 2.1.14 have been released with a YouTube fix.

Thank you! It works again, you are fast!

---

### Post by lovinglinux on 2011-07-31
> **beew said:**
> Thank you! It works again, you are fast!

You are welcome and thanks.

Actually, it took more than usual this time, because they made some significant changes in the url map. When I finished fixing it, I realized it wasn't working with external players due to mirror redirection. So I had to start again. Now I am bypassing the mirror selection and getting the url for the fallback server. I think this is the reason why the download speed has improved. There is also a significant improvement in the extension performance (time necessary to replace the video with the placeholder), specially for Firefox 3.6 users, due the way the extension is detecting the urls.

---

### Post by dandonnelly on 2011-09-09
Unfortunately I have found that this add-on does not seem to work anymore. I am not sure if it is the Youtube website or whether it is the configuration that I am trying to run it on but I can not get it to work properly.

[I]When navigating to this page (for example):

[http://www.youtube.com/watch?v=tQmEd_UeeIk](http://www.youtube.com/watch?v=tQmEd_UeeIk)[/I]

It always give the error that it was unable to replace due to a lack of compatible plugin for autodetect?

[B]I am running KDE 4.6 using Firefox 5.0.1 with your 2.1.14 FVR
[/B]
[SIZE=3][COLOR=SeaGreen]Thanks[/COLOR][/SIZE]

---

### Post by lovinglinux on 2011-09-10
> **dandonnelly said:**
> Unfortunately I have found that this add-on does not seem to work anymore. I am not sure if it is the Youtube website or whether it is the configuration that I am trying to run it on but I can not get it to work properly.

[I]When navigating to this page (for example):

[http://www.youtube.com/watch?v=tQmEd_UeeIk](http://www.youtube.com/watch?v=tQmEd_UeeIk)[/I]

It always give the error that it was unable to replace due to a lack of compatible plugin for autodetect?

[B]I am running KDE 4.6 using Firefox 5.0.1 with your 2.1.14 FVR
[/B]
[SIZE=3][COLOR=SeaGreen]Thanks[/COLOR][/SIZE]

I just tested that video and it is working. Your alert means the extension couldn't detect a compatible plugin for mp4 and flv. Type [noparse]about:plugins[/noparse] in the address bar and make sure you have a multimedia plugin capable of playing mp4 and flv. If not, install gecko-mediaplayer.

---

### Post by geoaraujo on 2011-09-29
Hello lovinglinux.

Today I've updated to Firefox 7 and the controls for pause, stop etc are missing.
Any fix yet?
Cheers.

---

### Post by lovinglinux on 2011-09-30
> **geoaraujo said:**
> Hello lovinglinux.

Today I've updated to Firefox 7 and the controls for pause, stop etc are missing.
Any fix yet?
Cheers.

That depends on the plugin you are using. Most likely a bug with libtotem. 

If you are not using gecko-mediaplayer, try it. Don't forget to disable similar plugins, like totem and VLC.

---

### Post by geoaraujo on 2011-09-30
Oh, I didn't change anything. It was perfect before this Firefox update.

---

### Post by lovinglinux on 2011-10-01
> **geoaraujo said:**
> Oh, I didn't change anything. It was perfect before this Firefox update.

It is a bug in the Totem plugin, that only affects Firefox 7.

Disable totem and use gecko-mediaplayer.

---

### Post by geoaraujo on 2011-10-03
> **lovinglinux said:**
> It is a bug in the Totem plugin, that only affects Firefox 7.

Disable totem and use gecko-mediaplayer.

How? :confused:

---

### Post by lovinglinux on 2011-10-04
> **geoaraujo said:**
> How? :confused:

You can install gecko-mediaplayer and remove totem-mozilla from the Software Center or using these commands:

```
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```

---

### Post by geoaraujo on 2011-10-05
> **lovinglinux said:**
> You can install gecko-mediaplayer and remove totem-mozilla from the Software Center or using these commands:

```
sudo apt-get remove totem-mozilla
sudo apt-get install gecko-mediaplayer
```
Actually Totem was not installed. Gecko-mediaplayer, which installs also Gnome-mediaplayer was already installed. I don't get it... :confused:

---

### Post by lovinglinux on 2011-10-05
> **geoaraujo said:**
> Actually Totem was not installed. Gecko-mediaplayer, which installs also Gnome-mediaplayer was already installed. I don't get it... :confused:

Type [noparse]about:plugins[/noparse] in the address bar, copy the content of the page and paste here inside code tags.

---

### Post by geoaraujo on 2011-10-05
> **lovinglinux said:**
> Type [noparse]about:plugins[/noparse] in the address bar, copy the content of the page and paste here inside code tags.

Ok, here it goes...

```

    **Plugins ativos**

 Mais informações sobre plugins em  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Encontre atualizações para os plugins instalados em  [mozilla.com/plugincheck]("http://www.mozilla.com/plugincheck/"). 
 Ajuda sobre a instalação de plugins em  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
 **Shockwave Flash**

 Arquivo:  npwrapper.libflashplayer.soVersão:   Shockwave Flash 10.3 r183   Tipo MIME Descrição Sufixos    application/x-shockwave-flash Shockwave Flash swf   application/futuresplash FutureSplash Player spl  **Google Talk Plugin Video Accelerator**

 Arquivo:  libnpgtpo3dautoplugin.soVersão:   Google Talk Plugin Video Accelerator version:0.1.44.11   Tipo MIME Descrição Sufixos    application/vnd.gtpo3d.auto O3D MIME 
 **Google Talk Plugin**

 Arquivo:  libnpgoogletalk64.soVersão:   Version: 2.3.2.0   Tipo MIME Descrição Sufixos    application/googletalk Google Talk Plugin googletalk  **VLC Multimedia Plug-in**

 Arquivo:  libvlcplugin.soVersão:   Version 1.1.11 The Luggage, copyright 1996-2007 The VideoLAN Team
[http://www.videolan.org/](http://www.videolan.org/)   Tipo MIME Descrição Sufixos    audio/mpeg MPEG audio mp2,mp3,mpga,mpega   audio/x-mpeg MPEG audio mp2,mp3,mpga,mpega   video/mpeg MPEG video mpg,mpeg,mpe   video/x-mpeg MPEG video mpg,mpeg,mpe   video/mpeg-system MPEG video mpg,mpeg,mpe,vob   video/x-mpeg-system MPEG video mpg,mpeg,mpe,vob   audio/x-mpegurl MPEG audio m3u   video/mp4 MPEG-4 video mp4,mpg4   audio/mp4 MPEG-4 audio mp4,mpg4   audio/x-m4a MPEG-4 audio m4a   application/mpeg4-iod MPEG-4 video mp4,mpg4   application/mpeg4-muxcodetable MPEG-4 video mp4,mpg4   video/x-m4v MPEG-4 video m4v   video/x-msvideo AVI video avi   video/quicktime QuickTime video mov,qt   application/x-ogg Ogg stream ogg   application/ogg Ogg stream ogg   video/ogg Ogg video ogv   application/x-vlc-plugin VLC plug-in vlc   video/x-ms-asf-plugin Windows Media Video asf,asx   video/x-ms-asf Windows Media Video asf,asx   application/x-mplayer2 Windows Media 
  video/x-ms-wmv Windows Media wmv   video/x-ms-wvx Windows Media Video wvx   audio/x-ms-wma Windows Media Audio wma   application/x-google-vlc-plugin Google VLC plug-in 
  audio/wav WAV audio wav   audio/x-wav WAV audio wav   audio/3gpp 3GPP audio 3gp,3gpp   video/3gpp 3GPP video 3gp,3gpp   audio/3gpp2 3GPP2 audio 3g2,3gpp2   video/3gpp2 3GPP2 video 3g2,3gpp2   video/divx DivX video divx   video/flv FLV video flv   video/x-flv FLV video flv   video/x-matroska Matroska video mkv   audio/x-matroska Matroska audio mka   application/xspf+xml Playlist xspf xspf   video/webm WebM video webm   audio/webm WebM audio webm   audio/amr AMR audio amr  **Shockwave Flash**

 Arquivo:  libflashplayer.soVersão:   Shockwave Flash 11.0 d1   Tipo MIME Descrição Sufixos    application/x-shockwave-flash Shockwave Flash swf   application/futuresplash FutureSplash Player spl  **Java(TM) Plug-in 1.6.0_26**

 Arquivo:  libnpjp2.soVersão:   The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   Tipo MIME Descrição Sufixos    application/x-java-vm Java&#8482; Plug-in 
  application/x-java-applet Java&#8482; Plug-in Applet 
  application/x-java-applet;version=1.1 Java&#8482; Plug-in 
  application/x-java-applet;version=1.1.1 Java&#8482; Plug-in 
  application/x-java-applet;version=1.1.2 Java&#8482; Plug-in 
  application/x-java-applet;version=1.1.3 Java&#8482; Plug-in 
  application/x-java-applet;version=1.2 Java&#8482; Plug-in 
  application/x-java-applet;version=1.2.1 Java&#8482; Plug-in 
  application/x-java-applet;version=1.2.2 Java&#8482; Plug-in 
  application/x-java-applet;version=1.3 Java&#8482; Plug-in 
  application/x-java-applet;version=1.3.1 Java&#8482; Plug-in 
  application/x-java-applet;version=1.4 Java&#8482; Plug-in 
  application/x-java-applet;version=1.4.1 Java&#8482; Plug-in 
  application/x-java-applet;version=1.4.2 Java&#8482; Plug-in 
  application/x-java-applet;version=1.5 Java&#8482; Plug-in 
  application/x-java-applet;version=1.6 Java&#8482; Plug-in 
  application/x-java-applet;jpi-version=1.6.0_26 Java&#8482; Plug-in 
  application/x-java-bean Java&#8482; Plug-in JavaBeans 
  application/x-java-bean;version=1.1 Java&#8482; Plug-in 
  application/x-java-bean;version=1.1.1 Java&#8482; Plug-in 
  application/x-java-bean;version=1.1.2 Java&#8482; Plug-in 
  application/x-java-bean;version=1.1.3 Java&#8482; Plug-in 
  application/x-java-bean;version=1.2 Java&#8482; Plug-in 
  application/x-java-bean;version=1.2.1 Java&#8482; Plug-in 
  application/x-java-bean;version=1.2.2 Java&#8482; Plug-in 
  application/x-java-bean;version=1.3 Java&#8482; Plug-in 
  application/x-java-bean;version=1.3.1 Java&#8482; Plug-in 
  application/x-java-bean;version=1.4 Java&#8482; Plug-in 
  application/x-java-bean;version=1.4.1 Java&#8482; Plug-in 
  application/x-java-bean;version=1.4.2 Java&#8482; Plug-in 
  application/x-java-bean;version=1.5 Java&#8482; Plug-in 
  application/x-java-bean;version=1.6 Java&#8482; Plug-in 
  application/x-java-bean;jpi-version=1.6.0_26 Java&#8482; Plug-in 
 **DivX Browser Plug-In**

 Arquivo:  gecko-mediaplayer-dvx.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    video/divx DivX Media Format divx   video/vnd.divx DivX Media Format divx  **RealPlayer 9**

 Arquivo:  gecko-mediaplayer-rm.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    audio/x-pn-realaudio RealAudio ram,rm   application/vnd.rn-realmedia RealMedia rm   application/vnd.rn-realaudio RealAudio ra,ram   video/vnd.rn-realvideo RealVideo rv   audio/x-realaudio RealAudio ra   audio/x-pn-realaudio-plugin RealAudio rpm   application/smil SMIL smil  **QuickTime Plug-in 7.6.4**

 Arquivo:  gecko-mediaplayer-qt.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    video/quicktime Quicktime mov   video/x-quicktime Quicktime mov   image/x-quicktime Quicktime mov   video/quicktime Quicktime mp4   video/quicktime Quicktime - Session Description Protocol sdp   application/x-quicktimeplayer Quicktime mov  **Windows Media Player Plug-in**

 Arquivo:  gecko-mediaplayer-wmp.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    application/asx Media Files *   video/x-ms-asf-plugin Media Files *   video/x-msvideo AVI avi,*   video/msvideo AVI avi,*   application/x-mplayer2 Media Files *   application/x-ms-wmv Microsoft WMV video wmv,*   video/x-ms-asf Media Files asf,asx,*   video/x-ms-asx Media Files asx,*   video/x-ms-wm Media Files wm,*   video/x-ms-wmv Microsoft WMV video wmv,*   audio/x-ms-wmv Windows Media wmv,*   video/x-ms-wmp Windows Media wmp,*   application/x-ms-wmp Windows Media wmp,*   video/x-ms-wvx Windows Media wvx,*   audio/x-ms-wax Windows Media wax,*   audio/x-ms-wma Windows Media wma,*   application/x-drm-v2 Windows Media asx,*   audio/wav Microsoft wave file wav,*   audio/x-wav Microsoft wave file wav,*  **mplayerplug-in is now gecko-mediaplayer 1.0.0**

 Arquivo:  gecko-mediaplayer.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    audio/x-mpegurl MPEG Playlist m3u   video/mpeg MPEG mpg,mpeg   audio/mpeg MPEG mpg,mpeg   video/x-mpeg MPEG mpg,mpeg   video/x-mpeg2 MPEG2 mpv2,mp2ve   audio/mpeg MPEG mpg,mpeg   audio/x-mpeg MPEG mpg,mpeg   audio/mpeg2 MPEG audio mp2   audio/x-mpeg2 MPEG audio mp2   audio/mp4 MPEG 4 audio mp4   audio/x-mp4 MPEG 4 audio mp4   video/mp4 MPEG 4 Video mp4   video/x-m4v MPEG 4 Video m4v   video/3gpp MPEG 4 Video mp4,3gp   audio/mpeg3 MPEG audio mp3   audio/x-mpeg3 MPEG audio mp3   audio/x-mpegurl MPEG url m3u   audio/mp3 MPEG audio mp3   application/x-ogg Ogg Vorbis Media ogg,oga,ogm   application/ogg Ogg Vorbis Media ogg,oga,ogm   audio/x-ogg Ogg Vorbis Audio ogg,oga   audio/ogg Ogg Vorbis Audio ogg,oga   video/x-ogg Ogg Vorbis Video ogg,ogm   video/ogg Ogg Vorbis Video ogg,ogm   application/x-vlc-plugin VLC plug-in vlc   application/x-google-vlc-plugin Google VLC plug-in 
  audio/flac FLAC Audio flac   audio/x-flac FLAC Audio flac   video/fli FLI animation fli,flc   video/x-fli FLI animation fli,flc   video/x-flv Flash Video flv   video/flv Flash Video flv   video/vnd.vivo VivoActive viv,vivo   audio/x-matroska Matroska Audio mka   video/x-matroska Matroska Video mkv   application/x-nsv-vp3-mp3 Nullsoft Streaming Video nsv   audio/x-mod Soundtracker mod   audio/x-aiff AIFF Audio aif   audio/basic Basic Audio File au,snd   audio/x-basic Basic Audio File au,snd   audio/midi MIDI Audio mid,midi,kar   audio/x-scpls Shoutcast Playlist pls   video/x-mng Multiple-Image Network Graphics mng   audio/webm WEBM audio File webm   audio/x-webm WEBM audio File webm   video/webm WEBM video File webm   video/x-webm WEBM video File webm   
    
    


```


Some parts seems to be missing...

---

### Post by lovinglinux on 2011-10-05
> **geoaraujo said:**
> Ok, here it goes...

```

  **Plugins ativos**

 Mais informações sobre plugins em  [mozilla.org]("https://pfs.mozilla.org/plugins/"). 
 Encontre atualizações para os plugins instalados em  [mozilla.com/plugincheck]("http://www.mozilla.com/plugincheck/"). 
 Ajuda sobre a instalação de plugins em  [plugindoc.mozdev.org]("http://plugindoc.mozdev.org/"). 
  
**Shockwave Flash**

 Arquivo:  npwrapper.libflashplayer.soVersão:   Shockwave Flash 10.3 r183   Tipo MIME Descrição Sufixos    application/x-shockwave-flash Shockwave Flash swf   application/futuresplash FutureSplash Player spl  **Google Talk Plugin Video Accelerator**

 Arquivo:  libnpgtpo3dautoplugin.soVersão:   Google Talk Plugin Video Accelerator version:0.1.44.11   Tipo MIME Descrição Sufixos    application/vnd.gtpo3d.auto O3D MIME 
  **Google Talk Plugin**

 Arquivo:  libnpgoogletalk64.soVersão:   Version: 2.3.2.0   Tipo MIME Descrição Sufixos    application/googletalk Google Talk Plugin googletalk  **VLC Multimedia Plug-in**

 Arquivo:  libvlcplugin.soVersão:   Version 1.1.11 The Luggage, copyright 1996-2007 The VideoLAN Team
[http://www.videolan.org/](http://www.videolan.org/)   Tipo MIME Descrição Sufixos    audio/mpeg MPEG audio mp2,mp3,mpga,mpega   audio/x-mpeg MPEG audio mp2,mp3,mpga,mpega   video/mpeg MPEG video mpg,mpeg,mpe   video/x-mpeg MPEG video mpg,mpeg,mpe   video/mpeg-system MPEG video mpg,mpeg,mpe,vob   video/x-mpeg-system MPEG video mpg,mpeg,mpe,vob   audio/x-mpegurl MPEG audio m3u   video/mp4 MPEG-4 video mp4,mpg4   audio/mp4 MPEG-4 audio mp4,mpg4   audio/x-m4a MPEG-4 audio m4a   application/mpeg4-iod MPEG-4 video mp4,mpg4   application/mpeg4-muxcodetable MPEG-4 video mp4,mpg4   video/x-m4v MPEG-4 video m4v   video/x-msvideo AVI video avi   video/quicktime QuickTime video mov,qt   application/x-ogg Ogg stream ogg   application/ogg Ogg stream ogg   video/ogg Ogg video ogv   application/x-vlc-plugin VLC plug-in vlc   video/x-ms-asf-plugin Windows Media Video asf,asx   video/x-ms-asf Windows Media Video asf,asx   application/x-mplayer2 Windows Media 
   video/x-ms-wmv Windows Media wmv   video/x-ms-wvx Windows Media Video wvx   audio/x-ms-wma Windows Media Audio wma   application/x-google-vlc-plugin Google VLC plug-in 
   audio/wav WAV audio wav   audio/x-wav WAV audio wav   audio/3gpp 3GPP audio 3gp,3gpp   video/3gpp 3GPP video 3gp,3gpp   audio/3gpp2 3GPP2 audio 3g2,3gpp2   video/3gpp2 3GPP2 video 3g2,3gpp2   video/divx DivX video divx   video/flv FLV video flv   video/x-flv FLV video flv   video/x-matroska Matroska video mkv   audio/x-matroska Matroska audio mka   application/xspf+xml Playlist xspf xspf   video/webm WebM video webm   audio/webm WebM audio webm   audio/amr AMR audio amr  **Shockwave Flash**

 Arquivo:  libflashplayer.soVersão:   Shockwave Flash 11.0 d1   Tipo MIME Descrição Sufixos    application/x-shockwave-flash Shockwave Flash swf   application/futuresplash FutureSplash Player spl  **Java(TM) Plug-in 1.6.0_26**

 Arquivo:  libnpjp2.soVersão:   The next generation [Java]("http://java.sun.com/") plug-in for Mozilla browsers.   Tipo MIME Descrição Sufixos    application/x-java-vm Java™ Plug-in 
   application/x-java-applet Java™ Plug-in Applet 
   application/x-java-applet;version=1.1 Java™ Plug-in 
   application/x-java-applet;version=1.1.1 Java™ Plug-in 
   application/x-java-applet;version=1.1.2 Java™ Plug-in 
   application/x-java-applet;version=1.1.3 Java™ Plug-in 
   application/x-java-applet;version=1.2 Java™ Plug-in 
   application/x-java-applet;version=1.2.1 Java™ Plug-in 
   application/x-java-applet;version=1.2.2 Java™ Plug-in 
   application/x-java-applet;version=1.3 Java™ Plug-in 
   application/x-java-applet;version=1.3.1 Java™ Plug-in 
   application/x-java-applet;version=1.4 Java™ Plug-in 
   application/x-java-applet;version=1.4.1 Java™ Plug-in 
   application/x-java-applet;version=1.4.2 Java™ Plug-in 
   application/x-java-applet;version=1.5 Java™ Plug-in 
   application/x-java-applet;version=1.6 Java™ Plug-in 
   application/x-java-applet;jpi-version=1.6.0_26 Java™ Plug-in 
   application/x-java-bean Java™ Plug-in JavaBeans 
   application/x-java-bean;version=1.1 Java™ Plug-in 
   application/x-java-bean;version=1.1.1 Java™ Plug-in 
   application/x-java-bean;version=1.1.2 Java™ Plug-in 
   application/x-java-bean;version=1.1.3 Java™ Plug-in 
   application/x-java-bean;version=1.2 Java™ Plug-in 
   application/x-java-bean;version=1.2.1 Java™ Plug-in 
   application/x-java-bean;version=1.2.2 Java™ Plug-in 
   application/x-java-bean;version=1.3 Java™ Plug-in 
   application/x-java-bean;version=1.3.1 Java™ Plug-in 
   application/x-java-bean;version=1.4 Java™ Plug-in 
   application/x-java-bean;version=1.4.1 Java™ Plug-in 
   application/x-java-bean;version=1.4.2 Java™ Plug-in 
   application/x-java-bean;version=1.5 Java™ Plug-in 
   application/x-java-bean;version=1.6 Java™ Plug-in 
   application/x-java-bean;jpi-version=1.6.0_26 Java™ Plug-in 
  **DivX Browser Plug-In**

 Arquivo:  gecko-mediaplayer-dvx.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    video/divx DivX Media Format divx   video/vnd.divx DivX Media Format divx  **RealPlayer 9**

 Arquivo:  gecko-mediaplayer-rm.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    audio/x-pn-realaudio RealAudio ram,rm   application/vnd.rn-realmedia RealMedia rm   application/vnd.rn-realaudio RealAudio ra,ram   video/vnd.rn-realvideo RealVideo rv   audio/x-realaudio RealAudio ra   audio/x-pn-realaudio-plugin RealAudio rpm   application/smil SMIL smil  **QuickTime Plug-in 7.6.4**

 Arquivo:  gecko-mediaplayer-qt.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    video/quicktime Quicktime mov   video/x-quicktime Quicktime mov   image/x-quicktime Quicktime mov   video/quicktime Quicktime mp4   video/quicktime Quicktime - Session Description Protocol sdp   application/x-quicktimeplayer Quicktime mov  **Windows Media Player Plug-in**

 Arquivo:  gecko-mediaplayer-wmp.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    application/asx Media Files *   video/x-ms-asf-plugin Media Files *   video/x-msvideo AVI avi,*   video/msvideo AVI avi,*   application/x-mplayer2 Media Files *   application/x-ms-wmv Microsoft WMV video wmv,*   video/x-ms-asf Media Files asf,asx,*   video/x-ms-asx Media Files asx,*   video/x-ms-wm Media Files wm,*   video/x-ms-wmv Microsoft WMV video wmv,*   audio/x-ms-wmv Windows Media wmv,*   video/x-ms-wmp Windows Media wmp,*   application/x-ms-wmp Windows Media wmp,*   video/x-ms-wvx Windows Media wvx,*   audio/x-ms-wax Windows Media wax,*   audio/x-ms-wma Windows Media wma,*   application/x-drm-v2 Windows Media asx,*   audio/wav Microsoft wave file wav,*   audio/x-wav Microsoft wave file wav,*  **mplayerplug-in is now gecko-mediaplayer 1.0.0**

 Arquivo:  gecko-mediaplayer.soVersão:   [Gecko Media Player]("http://kdekorte.googlepages.com/gecko-mediaplayer") 1.0.0

Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using [MPlayer]("http://mplayerhq.hu/")   Tipo MIME Descrição Sufixos    audio/x-mpegurl MPEG Playlist m3u   video/mpeg MPEG mpg,mpeg   audio/mpeg MPEG mpg,mpeg   video/x-mpeg MPEG mpg,mpeg   video/x-mpeg2 MPEG2 mpv2,mp2ve   audio/mpeg MPEG mpg,mpeg   audio/x-mpeg MPEG mpg,mpeg   audio/mpeg2 MPEG audio mp2   audio/x-mpeg2 MPEG audio mp2   audio/mp4 MPEG 4 audio mp4   audio/x-mp4 MPEG 4 audio mp4   video/mp4 MPEG 4 Video mp4   video/x-m4v MPEG 4 Video m4v   video/3gpp MPEG 4 Video mp4,3gp   audio/mpeg3 MPEG audio mp3   audio/x-mpeg3 MPEG audio mp3   audio/x-mpegurl MPEG url m3u   audio/mp3 MPEG audio mp3   application/x-ogg Ogg Vorbis Media ogg,oga,ogm   application/ogg Ogg Vorbis Media ogg,oga,ogm   audio/x-ogg Ogg Vorbis Audio ogg,oga   audio/ogg Ogg Vorbis Audio ogg,oga   video/x-ogg Ogg Vorbis Video ogg,ogm   video/ogg Ogg Vorbis Video ogg,ogm   application/x-vlc-plugin VLC plug-in vlc   application/x-google-vlc-plugin Google VLC plug-in 
   audio/flac FLAC Audio flac   audio/x-flac FLAC Audio flac   video/fli FLI animation fli,flc   video/x-fli FLI animation fli,flc   video/x-flv Flash Video flv   video/flv Flash Video flv   video/vnd.vivo VivoActive viv,vivo   audio/x-matroska Matroska Audio mka   video/x-matroska Matroska Video mkv   application/x-nsv-vp3-mp3 Nullsoft Streaming Video nsv   audio/x-mod Soundtracker mod   audio/x-aiff AIFF Audio aif   audio/basic Basic Audio File au,snd   audio/x-basic Basic Audio File au,snd   audio/midi MIDI Audio mid,midi,kar   audio/x-scpls Shoutcast Playlist pls   video/x-mng Multiple-Image Network Graphics mng   audio/webm WEBM audio File webm   audio/x-webm WEBM audio File webm   video/webm WEBM video File webm   video/x-webm WEBM video File webm   
    


```

The culprit is VLC plugin. It is not a good plugin and it takes precedent over gecko. To remove it, use this command:

```
sudo apt-get remove mozilla-vlc-plugin
```

Restart Firefox and you should be fine.

---

### Post by geoaraujo on 2011-10-05
It worked! Thanks for your help and time!

---

### Post by alexcckll on 2011-10-05
Critical requirement.  Can you use this addon to access BBC iPlayer, 4OD, Seesaw etc?  if not - dealbreaker.

---

### Post by lovinglinux on 2011-10-06
> **geoaraujo said:**
> It worked! Thanks for your help and time!

You are welcome.

---

### Post by lovinglinux on 2011-10-06
> **alexcckll said:**
> Critical requirement.  Can you use this addon to access BBC iPlayer, 4OD, Seesaw etc?  if not - dealbreaker.

BBC iPlayer no, the other probably not. Sorry.

---

### Post by Bromden on 2011-11-23
Thank you for this great add-on, i just don't understand two things...

1)how can i get video controls? I can't view any loading bar and pause/play button for the videos.
2)There is no sound :\

---

### Post by geoaraujo on 2011-11-23
Hello lovinglinux. It says [here]("http://www.webgapps.org/add-ons/flashvideoreplacer/download-firefox") that flash video replacer is compatible with Firefox 8, but since I've updated, it stopped working. :(

---

### Post by lovinglinux on 2011-11-23
> **Bromden said:**
> Thank you for this great add-on, i just don't understand two things...

1)how can i get video controls? I can't view any loading bar and pause/play button for the videos.
2)There is no sound :\

Probably because you have VLC plugin. Uninstall it and install gecko-mediaplayer.

> **geoaraujo said:**
> Hello lovinglinux. It says [here]("http://www.webgapps.org/add-ons/flashvideoreplacer/download-firefox") that flash video replacer is compatible with Firefox 8, but since I've updated, it stopped working. :(

It is enabled but not working or it is disabled by Firefox?

---

### Post by geoaraujo on 2011-11-23
> **lovinglinux said:**
> It is enabled but not working or it is disabled by Firefox?
It was disabled by the app when I updated from 7.0.1 to 8.0.

---

### Post by lovinglinux on 2011-11-24
> **geoaraujo said:**
> It was disabled by the app when I updated from 7.0.1 to 8.0.

Update your add-ons throught the add-ons manager. It will download a version compatibility patch.

---

### Post by CHAUDHRY07 on 2011-11-24
hey i was happy that i could watch videos without slowing up my old pc.i use xubuntu 11.10.i installed flash video replacer and when i started to play video it just crashed and restarted fire foxx.....cant understand whats problem :(
and yeah hats off for a good work though i havent tried but heard its awesome.

---

### Post by lovinglinux on 2011-11-24
> **CHAUDHRY07 said:**
> hey i was happy that i could watch videos without slowing up my old pc.i use xubuntu 11.10.i installed flash video replacer and when i started to play video it just crashed and restarted fire foxx.....cant understand whats problem :(
and yeah hats off for a good work though i havent tried but heard its awesome.

Which video plugins you have installed? You can check that by typing [noparse]about:plugins[/noparse] in the address bar.

---

### Post by Bromden on 2011-11-24
> **lovinglinux said:**
> Probably because you have VLC plugin. Uninstall it and install gecko-mediaplayer.

SOLVED thank you ;)

---

### Post by CHAUDHRY07 on 2011-11-24
i have shock wave flash 11.1 n 11.2,java iced tea and vlc plugins.

---

### Post by lovinglinux on 2011-11-24
> **CHAUDHRY07 said:**
> i have shock wave flash 11.1 n 11.2,java iced tea and vlc plugins.

Uninstall VLC plugin and install gecko-mediaplayer plugin.

BTW, you don't mneed to remove VLC player, just the plugin.

---

### Post by geoaraujo on 2011-11-24
> **lovinglinux said:**
> Update your add-ons throught the add-ons manager. It will download a version compatibility patch.
"No updates available".

---

### Post by lovinglinux on 2011-11-24
> **geoaraujo said:**
> "No updates available".

Uninstall the extension, got to Mozilla site and install it again.

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

---

### Post by geoaraujo on 2011-11-24
> **lovinglinux said:**
> Uninstall the extension, got to Mozilla site and install it again.

[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

Ok, it worked. Thanks.

---

### Post by lovinglinux on 2011-11-24
> **geoaraujo said:**
> Ok, it worked. Thanks.

You are welcome.

---

### Post by mihamtalamac on 2011-11-24
This plugin will extend the life of my laptop :). Keep up with the good work ;)

---

### Post by mobilediesel on 2011-11-24
How do I get FlashVideoReplacer to play the 240p video? My computer does not like the 360p whether it's flash or mp4.

---

### Post by lovinglinux on 2011-11-24
> **mobilediesel said:**
> How do I get FlashVideoReplacer to play the 240p video? My computer does not like the 360p whether it's flash or mp4.

When the FVR placeholder shows up over the video, select the 240p video from the menu, before clicking the placeholder.

---

### Post by CHAUDHRY07 on 2011-11-25
> **lovinglinux said:**
> Uninstall VLC plugin and install gecko-mediaplayer plugin.

BTW, you don't mneed to remove VLC player, just the plugin.

so i will have to install mplayer for that too right ok i ll give feedback after instlling.
thanks

---

### Post by mobilediesel on 2011-11-25
> **lovinglinux said:**
> When the FVR placeholder shows up over the video, select the 240p video from the menu, before clicking the placeholder.

The menu on the placeholder only shows:
[LIST]
[*]Embedded
[*]New Tab
[*]New Window
[*]Standalone
[/LIST]
The version of FVR I have is 2.1.14 on Iceweasel 3.6.24

---

### Post by lovinglinux on 2011-11-26
> **mobilediesel said:**
> The menu on the placeholder only shows:
[LIST]
[*]Embedded
[*]New Tab
[*]New Window
[*]Standalone
[/LIST]
The version of FVR I have is 2.1.14 on Iceweasel 3.6.24

Video quality selection on FVR is only available for Firefox/Iceweasel 4 or superior. Visit [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247) to see how to get the latest Firefox version.

---

### Post by mobilediesel on 2011-11-26
> **lovinglinux said:**
> Video quality selection on FVR is only available for Firefox/Iceweasel 4 or superior. Visit [Firefox 8 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247) to see how to get the latest Firefox version.

I'm running a Pentium 3 at 1Ghz with 512MiB of RAM. Firefox 4 through 8 is far beyond what this old computer can handle. I know the later versions of firefox/iceweasel are supposed to use less memory but that's certainly not the case on this computer as running firefox 8 for 20 minutes with only a couple tabs open quickly fills up memory and moves on to filling up the swap partition before I'm finally able to kill it.

---

### Post by lovinglinux on 2011-11-26
> **mobilediesel said:**
> I'm running a Pentium 3 at 1Ghz with 512MiB of RAM. Firefox 4 through 8 is far beyond what this old computer can handle. I know the later versions of firefox/iceweasel are supposed to use less memory but that's certainly not the case on this computer as running firefox 8 for 20 minutes with only a couple tabs open quickly fills up memory and moves on to filling up the swap partition before I'm finally able to kill it.

The problem is that Firefox 3.6 javascript engine is a lot slower than FF 8, so I had to limit the video quality detection. Perhaps I could add an option to get the lowest video quality in the next version.

---

### Post by mutorio on 2012-01-14
First of all many thanks for your awesome extension. After testing every possible mediaplayer and prefenrence I am using now the extension with smplayer and the cache settings: 32mb. VLc and gnome-mplayer stop very often on hd videos playing. By smplayer I can solve this issue nearly. The reason is that if I take 8mb cache size for example (Player start after 20% of cache filling) after about 4 minutes hd-videos stop playing. With now 32mb ist stops after 20 minutes.. This is ok because the most videos I watch are not longer.
With normal flashplayer it is everytime working but flash we all now is no solution for linux because of its poor performance and the bad video experience. But somehow flash-video-replacer stop loading the youtube-stream after a while.

Is there any way to customize the cache from flash-video-replacer so it works for long videos?

Anyway I am very happy to find your extension and I hope you will continue your great work. Maybe one time it will work with vevo.com ;)

best regards


mutorio

---

### Post by lovinglinux on 2012-01-15
> **mutorio said:**
> First of all many thanks for your awesome extension. After testing every possible mediaplayer and prefenrence I am using now the extension with smplayer and the cache settings: 32mb. VLc and gnome-mplayer stop very often on hd videos playing. By smplayer I can solve this issue nearly. The reason is that if I take 8mb cache size for example (Player start after 20% of cache filling) after about 4 minutes hd-videos stop playing. With now 32mb ist stops after 20 minutes.. This is ok because the most videos I watch are not longer.
With normal flashplayer it is everytime working but flash we all now is no solution for linux because of its poor performance and the bad video experience. But somehow flash-video-replacer stop loading the youtube-stream after a while.

Is there any way to customize the cache from flash-video-replacer so it works for long videos?

Anyway I am very happy to find your extension and I hope you will continue your great work. Maybe one time it will work with vevo.com ;)

best regards


mutorio

The cache depends on the backend you are using to play the videos.

There must be something wrong on your system, because the videos shouldn't stop when the initial cache is reached.

---

### Post by mutorio on 2012-01-15
Thank you for the fast response.
I get it work now.. Since I deinstall yesterday gecko-mediaplayer and the mozilla-plugin-vlc until now it is working even for long videos :D.

But after using many days flash-video-replacer I found many videos that are not playable with flash-video-replacer even on any player embedded or extern. Here are a few examples:
[http://www.youtube.com/watch?v=y-IU-De33gw](http://www.youtube.com/watch?v=y-IU-De33gw)

and

[http://www.youtube.com/watch?v=UIUJh2mA8vg](http://www.youtube.com/watch?v=UIUJh2mA8vg)

and

[http://www.youtube.com/watch?v=PfMFAEoVX1Y](http://www.youtube.com/watch?v=PfMFAEoVX1Y)

edit: it seems this videos only don't work with 1080p, for 720p and more down it work. With flashplayer both Resolutions work and my bandwith is 32mbit and I didn't have Network problems.

There are much more Video like this. Some of them work by clicking play twice or changing resolution down and then up again. Some videos only work if I reload the page first, sometimes I have to reload the page even after 15 minutes not using them.

I don't want to complain because on most videos your addon really working awesome, but there a still place for improovement.

In the settings menu of the addon the option use mp4 priority before flv always take back to enabled if I uncheck it and close, while all other preferences save well.

I hope it was not to much now.

Your addon is the best out there for skip flash from youtube. 
I am really appreciate what you are doing for the linux Community and I hope you have sucess with your awesome work.

best regards mutorio

---

### Post by andromedanevel on 2012-01-19
Love this plugin, but I stopped working yesterday on Youtube. The videos remain black.

Did youtube change something again?

---

### Post by MoreOrLess on 2012-01-19
> **andromedanevel said:**
> Love this plugin, but I stopped working yesterday on Youtube. The videos remain black.

Did youtube change something again?
I also had issues with yt today and I wasn't using this plugin.

---

### Post by Farinet on 2012-01-19
> **andromedanevel said:**
> Love this plugin, but I stopped working yesterday on Youtube. The videos remain black.

Did youtube change something again?

It's the same for me. First i tried and retried with plugin setup (thinking i did something wrong). Then, i saw FlashVideoReplacer works still fine with vimeo, so i think that might be some changement in youtube (??).

---

### Post by MoreOrLess on 2012-01-19
Oh, I forgot about the blackout protest. Maybe it was that. Some vids stil worked though. Hmm.

---

### Post by andromedanevel on 2012-01-19
No it was not the SOPA protest, because today it still isn't working and if I disable the plugin, YouTube works again (but with flash plugin crashes).

---

### Post by over_my_head on 2012-01-19
does anyone know if this plugin works to play the tabs on songsterr.com

[http://www.songsterr.com/](http://www.songsterr.com/)


?

if not, i'll just download it and try it out myself but i thought i'd ask here first. 
:-)

---

### Post by lovinglinux on 2012-01-20
> **andromedanevel said:**
> Love this plugin, but I stopped working yesterday on Youtube. The videos remain black.

Did youtube change something again?

Hi all,

It indeed stopped working on YouTube. I will try to fix it as soon as I can and will post any updates here.

> **over_my_head said:**
> does anyone know if this plugin works to play the tabs on songsterr.com

[http://www.songsterr.com/](http://www.songsterr.com/)


?

if not, i'll just download it and try it out myself but i thought i'd ask here first. 
:-)

Nope, it doesn't work on that site.

---

### Post by Farinet on 2012-01-20
Thanks a lot for your effort!!! :) :)

---

### Post by andromedanevel on 2012-01-20
> **lovinglinux said:**
> Hi all,

It indeed stopped working on YouTube. I will try to fix it as soon as I can and will post any updates here.


Wow, great! Will keep an eye on this site. Is it not an pain in the *** that youtube keeps changing its site? Last time was still in december right?

---

### Post by lovinglinux on 2012-01-20
> **andromedanevel said:**
> Wow, great! Will keep an eye on this site. Is it not an pain in the *** that youtube keeps changing its site? Last time was still in december right?

It has been a while since FVR stopped working on YT for the last time.

---

### Post by over_my_head on 2012-01-20
> **lovinglinux said:**
> Hi all,

Nope, it doesn't work on that site.

thanks for letting me know. 

still it's great that someone's working on an alternative to flash player!

---

### Post by verymadpip on 2012-02-05
I'm using 10.04.3 (minimal install) & don't seem able to install (or find) flashvideoreplacer any more.

I've done the "best add-ons" thing that lets me select desired add-ons, of which fvr is one, & that hasn't worked either.

Hardware specs:

> Compaq TC1000 tablet PC
1 GHz  Transmeta Crusoe 5800
486(?)Mb RAM  [24 MB of system RAM is reserved for processor usage.]
nVidia  GeForce2Go with 16-MB SDRAM

If more info is required I'll try to provide it

Everything was kind of working on 11.10 minimal, although I was having trouble with sync.

Any help is greatly appreciated.

---

### Post by SoFl W on 2012-02-05
> **verymadpip said:**
> 
I've done the "best add-ons" thing that lets me select desired add-ons, of which fvr is one, & that hasn't worked either.   Any help is greatly appreciated.


?  Seems the author (lovinglinux] took it down?
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

---

### Post by MoreOrLess on 2012-02-05
I assume the author is making a new FF 10-compatible plugin.

---

### Post by verymadpip on 2012-02-05
I'm assuming so too :)

The TC1000 has been a bit of a project.  Being able to watch moving pictures instead of some stills with sound would be cool.

I'll be patient & wait & see what happens.

---

### Post by lovinglinux on 2012-02-05
> **SoFl W said:**
> ?  Seems the author (lovinglinux] took it down?
[https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/](https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/)

> **MoreOrLess said:**
> I assume the author is making a new FF 10-compatible plugin.

> **verymadpip said:**
> I'm assuming so too :)

The TC1000 has been a bit of a project.  Being able to watch moving pictures instead of some stills with sound would be cool.

I'll be patient & wait & see what happens.


I have disabled the add-on because the current version is not compatible with YouTube.

There is a fix to the YouTube issue already, but I still need to fix another issue.

I will let you know here when a new version is available.

---

### Post by verymadpip on 2012-02-05
Thanks lovinglinux. 
You, sir, are a star.

---

### Post by lovinglinux on 2012-02-22
I have released version 2.1.15. It doesn't fix all the issues I wanted to fix, but it works on YouTube again.

I apologize for the delay.

---

### Post by karlingen on 2012-03-29
Seems to be down again. I'm getting a black screen. Only Audio works.

---

### Post by lovinglinux on 2012-03-31
> **karlingen said:**
> Seems to be down again. I'm getting a black screen. Only Audio works.

I have tested and it is working fine here.

Which plugin you are using? If you are using Totem, try to disable it and install gecko-mediaplayer.

---

### Post by earthshakergb on 2012-04-01
Works OK but when in embedded mode, how do I stop the video? (no stop button)

---

### Post by lovinglinux on 2012-04-01
> **earthshakergb said:**
> Works OK but when in embedded mode, how do I stop the video? (no stop button)

That's because you are using the VLC plugin. Install gecko-mediaplayer, type [noparse]about:plugins[/noparse] in Firefox address bar, disable the VLC plugin.

---

### Post by Orestez on 2012-05-03
Hi there,

Im hugely enjoying your extension (I actually had the idea a while back and was positively surprised to see someone had already implemented it), but I somehow can't play embedded videos anymore. I have flash and gecko media player installed and no matter what quality/format I select on youtube I just get a message saying 

"FVR was unable to replace the video, due to lack of a compatible plugin for autodetect."

I cannot select anything but Auto under Plugin/MimeType. Im using Iceweasel under debian.

Edit²: Actually, it works for *some* videos if I select "Prefer WebM when available".

---

### Post by saronno on 2012-06-11
I told lovinglinux of something I discover about his plugin.
I used UMPlayer as external app for youtubevideo (it has an incorporated
tool to search for videos without even open the browser and is based on mplayer),
and the app has very poor performance when the video is launched by videoreplacer.
When you launch it by the internal search it goes smoothly.

The reason is that FVR use the fallback URL instead of the preferred one,
and this cause some troubles (especially with older machines) with hd (720p)
videos.

If somehow, lovinglinux will change how videoreplace get the url
we will have much better performance with HD videos.

Usually the url beginning as "o-o.preferred.seabone..." have much
better streaming performance that the fallback one.

However he did a great job.

---

### Post by Imfego on 2012-06-27
Thank you for creating this alternative to Adobe player.
One thing, though, that is a little uncomfortable in usage is that you can't choose which one of the players you want activated at the moment (you have to disable the extension and restart the browser first to have the adobe one back) which can be inconvenient when trying to watch a video with close captions loaded.
Also, can you help me finding out which command options are needed to define in SMplayer Youtube's video quality and the streaming video's precaching values?
I've been trying to pass video page URLs to it via flashgot, but it seems to load a too high resolution for me and thus ends up crashing because of a slow internet connection.

---

### Post by RJARRRPCGP on 2012-09-06
It was fun when it lasted, just like good weather in parts of the Rockies and Alaska. (Where you're lucky to have good weather for 5 days)

---

### Post by saronno on 2012-09-15
Youtube has change something. I've seen that netvideoreplacer has solved the problem. Checking out the URL I find out that they add the signature parameter to the url.  Old not working: [http://o-o---preferred---seabone-mil5---v3---lscache2.c.youtube.com/videoplayback?upn=ZDSXeruMbgo&sparams=cp%2Cgcr%2Cid%2Cip%2Cipbits%2Citag%2Cratebypass%2Csource%2Cupn%2Cexpire&fexp=906357%2C923003%2C920917%2C922401%2C920704%2C912806%2C913419%2C913558%2C913556%2C920201%2C912706&ms=au&expire=1347771700&itag=22&ipbits=8&gcr=it&sver=3&ratebypass=yes&mt=1347749170&ip=80.116.115.193&mv=m&source=youtube&key=yt1&cp=U0hTTFdST19FSkNOM19PTFNIOmNKbFhMdUlPaXFN&id=3368eb88cb7f82f2&newshard=yes](http://o-o---preferred---seabone-mil5---v3---lscache2.c.youtube.com/videoplayback?upn=ZDSXeruMbgo&sparams=cp%2Cgcr%2Cid%2Cip%2Cipbits%2Citag%2Cratebypass%2Csource%2Cupn%2Cexpire&fexp=906357%2C923003%2C920917%2C922401%2C920704%2C912806%2C913419%2C913558%2C913556%2C920201%2C912706&ms=au&expire=1347771700&itag=22&ipbits=8&gcr=it&sver=3&ratebypass=yes&mt=1347749170&ip=80.116.115.193&mv=m&source=youtube&key=yt1&cp=U0hTTFdST19FSkNOM19PTFNIOmNKbFhMdUlPaXFN&id=3368eb88cb7f82f2&newshard=yes)  New working: [http://o-o---preferred---seabone-mil5---v3---lscache2.c.youtube.com/videoplayback?upn=l_bzU9TeknE&sparams=cp%2Cgcr%2Cid%2Cip%2Cipbits%2Citag%2Cratebypass%2Csource%2Cupn%2Cexpire&fexp=906357%2C923003%2C920917%2C922401%2C920704%2C912806%2C913419%2C913558%2C913556%2C920201%2C912706&ms=au&expire=1347771700&itag=22&ipbits=8&gcr=it&sver=3&ratebypass=yes&mt=1347749651&ip=80.116.115.193&mv=m&source=youtube&key=yt1&cp=U0hTTFdST19FSkNOM19PTFNIOmNKbFhMdUlPaXFN&id=3368eb88cb7f82f2&newshard=yes&signature=B7D003D92EE25C4876AA180B8753266200551A0C.17665C9F3CAE3E564F651A552CF21BC2201B2677](http://o-o---preferred---seabone-mil5---v3---lscache2.c.youtube.com/videoplayback?upn=l_bzU9TeknE&sparams=cp%2Cgcr%2Cid%2Cip%2Cipbits%2Citag%2Cratebypass%2Csource%2Cupn%2Cexpire&fexp=906357%2C923003%2C920917%2C922401%2C920704%2C912806%2C913419%2C913558%2C913556%2C920201%2C912706&ms=au&expire=1347771700&itag=22&ipbits=8&gcr=it&sver=3&ratebypass=yes&mt=1347749651&ip=80.116.115.193&mv=m&source=youtube&key=yt1&cp=U0hTTFdST19FSkNOM19PTFNIOmNKbFhMdUlPaXFN&id=3368eb88cb7f82f2&newshard=yes&signature=B7D003D92EE25C4876AA180B8753266200551A0C.17665C9F3CAE3E564F651A552CF21BC2201B2677)  We need the same mod on flashvideoreplacer somehow.

---

### Post by bernie86 on 2012-09-17
Seeing as I ran into some problems with the embedded flashplayer, I found this nice AddOn - when trying to install, it sadly says "Removed by the author"... any other source I can get this from?

---

### Post by lovinglinux on 2012-09-17
> **bernie86 said:**
> Seeing as I ran into some problems with the embedded flashplayer, I found this nice AddOn - when trying to install, it sadly says "Removed by the author"... any other source I can get this from?

[https://github.com/webgapps/flvideoreplacer/downloads](https://github.com/webgapps/flvideoreplacer/downloads)

Keep in mind it is probably broken, since I haven't been able to update it lately.

---

### Post by verymadpip on 2012-09-22
Super.  I think FVR is the only way I can make my ancient TC1000 tablet do You Tube.
How do I install it from tar.gz?

---

### Post by BicyclerBoy on 2012-09-22
This works nicely for the flash content on youtube
quvi & mplayer
[http://ppcluddite.blogspot.co.nz/2012/09/yet-another-flash-alternative.html](http://ppcluddite.blogspot.co.nz/2012/09/yet-another-flash-alternative.html)

The html5 (webm) stuff still plays embedded in firefox with gecko-mplayer.

---

### Post by claracc on 2012-09-23
Unfortunately I had to removed the excellent flashvideoreplacer addon because since one week ago it doesn't work in youtube for my ancient pIII, 1GHz CPU and 512 MB ram.

I think youtube has changed something in its page , so now I cannot play youtube videos with flashvideoreplacer.

Instead I have installed greasymonkey addon in firefox and now using viewtube script (from userscripts.org) in order to watch flash videos in youtube with native mp4 player.

In the future, could we see flashvideoreplacer working again?

---

### Post by verymadpip on 2012-09-26
I coulkdn't get quvi to work, I'm probably missing something simple.
I have found that this works pretty well for me regarding You Tube:

[http://crunchbanglinux.org/forums/topic/19172/watching-youtube-without-flash/](http://crunchbanglinux.org/forums/topic/19172/watching-youtube-without-flash/)

So far I've only had to use the first command to get things to play.  I use smplayer rather than mplayer as I like to see the time elapsed/left thingy.
Some videos have seemed a little slowed down so I'm working on that.

I expect that YMMV.

---

### Post by verymadpip on 2012-09-28
Sad face....

Now all I get is a bunch of nothing, or a 403 forbidden.
Looks like the TC1000 is going in a cupboard somewhere.

---

### Post by BicyclerBoy on 2012-09-28
Elaborate on the problem with quvi..

Note that terminal copy & paste is done with <ctrl>+<shift>+<c> & <ctrl>+<shift>+<v> respectively..

---

### Post by verymadpip on 2012-09-29
Elaborate?  Yeah, sure.

This is the quvirc (I've probably got this wrong actually.......)

```
exec = "mplayer -framedrop -cache 10000 -cache-min 10 %u"
format = fmt18_360p
```

When I issue the command assuggested I get:
```

$ quvi "http://www.youtube.com/watch?v=gDW_Hj2K0wo"
:: Check for URL redirection ...done.
:: Fetch config ...done.
:: Verify media URL ...error: server response code 403 (conncode=0)
```

I'm missing something simple I expect.

---

### Post by danield on 2012-09-29
> **verymadpip said:**
> When I issue the command assuggested I get:
```

$ quvi "http://www.youtube.com/watch?v=gDW_Hj2K0wo"
:: Check for URL redirection ...done.
:: Fetch config ...done.
:: Verify media URL ...error: server response code 403 (conncode=0)
```

I'm missing something simple I expect.

I wrote that blog post on quvi.  You're not missing anything as quvi is now broken for me, too.  Same error.  I guess Youtube made one of those changes that breaks every Youtube downloader under the sun and we'll have to wait for an update.

---

### Post by BicyclerBoy on 2012-09-29
That's to force us to watch adverts..
Google flexing it's power..or making thing work better for mobile flash players.

html5 (webm) still works for now.

---

### Post by verymadpip on 2012-09-29
Unfortunately such workarounds are the only way I have any chance of successfully watching you tube on the TC100 (Compaq tablet from 2000/2001 I think, 1GHz Transmeta Crusoe CPU 486 Mb RAM.

---

### Post by danield on 2012-10-09
Just to let anybody here know, an updated quvi-scripts has migrated to Debian Testing.  This should fix Youtube on quvi.

EDIT: I meant libquvi-scripts.

---


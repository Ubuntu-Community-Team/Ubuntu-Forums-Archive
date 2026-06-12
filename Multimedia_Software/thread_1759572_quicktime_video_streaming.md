---
title: "quicktime video streaming"
date: 2011-05-15
forum: Multimedia Software
---

### Post by beew on 2011-05-15
Hi,

 I have installed the gecko-mediaplayer plugin for Firefox and I am wondering if it is possible to watch quicktime video streams in Firefox.

Tried these two links for experiment but no luck.
[http://www.2xstream.co.uk/mediaexamples/quicktime/qtexamples.html](http://www.2xstream.co.uk/mediaexamples/quicktime/qtexamples.html)
[http://cinematechnic.com/jda/quicktime_demo_index.html](http://cinematechnic.com/jda/quicktime_demo_index.html)

Are these supposed to work or am I just wasting my time? Thanks.

---

### Post by mc4man on 2011-05-15
Well they work here with the totem-mozilla plugin, will try gecko-mediaplayer later (and edit in if possible - should be
(you'll also notice with the totem plugin it's being cached (/tmp

---

### Post by beew on 2011-05-16
These are my screen shots trying to access the first site with gecko-mediaplayer and the firefox addon configuration. For some reasons FF is configured to use Mozpluger by gecko is used but not loading. I can't seem to change the FF action for quick time to gecko.

---

### Post by lovinglinux on 2011-05-16
**First link:**

Streaming doesn't work. Tested gecko and mozplugger

Progressive work with gecko and mozplugger

**Second link:**

Doesn't work.

> **beew said:**
> I am also wondering how does Firefox decide which plugin to use for handling different file types because from tools > addons it says quicktime video would be handled by Mozpluger but gecko is always used, just not showing anything.


Funny thing that on my system, priority is always given to mozplugger. I tried to change the installation order, but didn't help. Even with gecko-mediaplayer being selected in the Applications tab, Firefox always use mozplugger if both are installed.

---

### Post by beew on 2011-05-16
Hi, 

Thanks for the quick response!

So does gecko work with qt streaming at all? What about other kinds of streaming? I would want to do some tests so if you know some good streaming sites I would appreciate some links.

The totem-mozilla plugin apparently works for mc4man though it doesn't work for me either on Natty.

---

### Post by lovinglinux on 2011-05-16
> **beew said:**
> Hi, 

Thanks for the quick response!

So does gecko work with qt streaming at all? What about other kinds of streaming? I would want to do some tests so if you know some good streaming sites I would appreciate some links.

The totem-mozilla plugin apparently works for mc4man though it doesn't work for me either on Natty.

Well, I use only gecko with FVR and it works on all supported sites, but with mp4, flv and m4v. Looks like gecko and mozplugger have issues with non-progressive quicktime only.

I don't know any site you could use to test. Most video sites I use are flash based.

---

### Post by mc4man on 2011-05-16
> **beew said:**
> Hi, 

Thanks for the quick response!

So does gecko work with qt streaming at all? What about other kinds of streaming? I would want to do some tests so if you know some good streaming sites I would appreciate some links.

The totem-mozilla plugin apparently works for mc4man though it doesn't work for me either on Natty.
Just to get back to you on that - the streaming samples don't work here either, the Progressive work with both plugins in browser and also directly in players using the url's. (the streaming are rtsp which can at times be a problem
(those virtual ones also work but can't rotate w/ mouse

The 2nd site doesn't work at all, not even in windows. (tried many ways..
As far as plugins - have always found it's best to have only one installed at a time. (have always wished they could be set as alternatives but I  don't think it's that simple, 
(atm prefer the totem-mozilla one here, but both have their strong and weak points

---

### Post by beew on 2011-05-19
Found another link, please try it and let me know if you have any luck. Thanks.
[URL="http://trailers.apple.com/trailers/focus_features/takingwoodstock/"]
http://trailers.apple.com/trailers/focus_features/takingwoodstock/[/URL]

The "standard" streams work in Windows but the HD ones don't. None work with Gecko-player it seems.

---

### Post by lovinglinux on 2011-05-19
> **beew said:**
> Found another link, please try it and let me know if you have any luck. Thanks.
[URL="http://trailers.apple.com/trailers/focus_features/takingwoodstock/"]
http://trailers.apple.com/trailers/focus_features/takingwoodstock/[/URL]

The "standard" streams work in Windows but the HD ones don't. None work with Gecko-player it seems.

Doesn't work here.

Have you tried the Quicktime hack explained in the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")? I am not sure is updated, but worth a try. It solved my quicktime issues in the past.

---

### Post by mc4man on 2011-05-19
Apple tends to change those links up a bit from time to time
So the one you linked doesn't work in FF browser window (using the totem plugin, I gather the same for the gecko one) but if I was to just l. click on the trailer button (Ex. HD 720p) then it would open directly in totem (screen

Trailers that have a different setup like here should open in your browser, just expand the drop down, choose the download option > r. click > open in a new tab or window
[http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/](http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/)

Or try this to test the gecko plugin - (i still think the totem plugin is better for some things

This is the url from the above - should just start playing - r. click on > open link in ..
[http://trailers.apple.com/movies/disney/piratesofthecaribbeanonstrangertides/pirates4-wetagain_720p.mov](http://trailers.apple.com/movies/disney/piratesofthecaribbeanonstrangertides/pirates4-wetagain_720p.mov)

---

### Post by beew on 2011-05-19
Hi,

Thanks guys for the responses.

I tried the totem quicktime plugin for my own link above and mc4man's and they both work (including the HD parts for my link which don't work on Windows) 

So I am using the totem plugin for qt and the gecko one for other things such as dvix. I tested other streaming sites (non qt) and gecko still works.

The only problem is  LovingLinix's FlashVideoReplacer  stops working even though I have only enabled the  totem plugin for quicktime. I think FVR works better with gecko player so I would want to use it instead of totem for FVR.

---

### Post by mc4man on 2011-05-19
Good to see you're making some progress here - 
One thing to sorta warn about the mozilla plugin (can be useful a times

When playing streams that cache most will be cached in /tmp
At least here many times they are not removed when switching sites or even closing the browser, so this may accumulate MB's
(will be removed on log out if not before

The advantage at times is when for whatever reason streaming may not be smooth.
Then you can just go into /tmp and play directly with a video player
(most of those apple trailers cache here fully  in about a min. or less

---

### Post by lovinglinux on 2011-05-19
> **beew said:**
> Hi,

Thanks guys for the responses.

I tried the totem quicktime plugin for my own link above and mc4man's and they both work (including the HD parts for my link which don't work on Windows) 

So I am using the totem plugin for qt and the gecko one for other things such as dvix. I tested other streaming sites (non qt) and gecko still works.

The only problem is  LovingLinix's FlashVideoReplacer  stops working even though I have only enabled the  totem plugin for quicktime. I think FVR works better with gecko player so I would want to use it instead of totem for FVR.

The crazy thing is that you can turn on all Totem plugins except the QT one. All other plugins don't interfere with FVR and allow gecko to take over.

The good thing is that if you disable the QT plugin in the add-ons manager, the video will be loaded by gecko, even if you have already started streaming with totem.

So, I will try to implement an option in FVR to disable the plugins you don't want to use when a supported site is opened and enable again when leaving the page.

---

### Post by beew on 2011-05-19
mc4man, 

Thanks for the tips.

---

### Post by beew on 2011-05-19
> **lovinglinux said:**
> The crazy thing is that you can turn on all Totem plugins except the QT one. All other plugins don't interfere with FVR and allow gecko to take over.

The good thing is that if you disable the QT plugin in the add-ons manager, the video will be loaded by gecko, even if you have already started streaming with totem.

So, I will try to implement an option in FVR to disable the plugins you don't want to use when a supported site is opened and enable again when leaving the page.

This is indeed crazy. :)

Thanks, I look forward to the next release of FVR, you are the man!

---

### Post by lovinglinux on 2011-05-19
> **beew said:**
> This is indeed crazy. :)

Thanks, I look forward to the next release of FVR, you are the man!

In fact, I might have a simpler solution. I am implementing an option to force the Mime Type to mkv. Neither totem or mozplugger can handle mkv, only gecko. See where I am going with this line of thought? :-)

---

### Post by lovinglinux on 2011-05-19
I just found a bug. The Mime Type override is not working.

I will try to fix this as soon as possible and implement the matroska option.

---

### Post by lovinglinux on 2011-05-19
Here is the real deal. I have already implemented the option to use x-matroska. It works. Gecko is used, even with totem and mozplugger enabled. The bug affects only YouTube and I bet it was introduced with the new resolution menu.

Working on it....

---

### Post by lovinglinux on 2011-05-19
Please test version [2.1.11pre]("https://addons.mozilla.org/en-US/firefox/addon/flashvideoreplacer/versions/").

Set the MimeType in the preferences to **Matroska (video/x-matroska)**

If everything goes as planned, gecko will be used, even if totem and mozplugger are installed and enabled.

---

### Post by beew on 2011-05-20
Hi, LovingLinux, 

You are awesome. It works and it works with Mozplugger as well, but Mozplugger doesn't work with the Totem pluggin, though that is another story ( I actually have installed gpdf instead so I no longer need mozplugger, but it would be interesting to try to fix this by editing the conf file when I have time)

Thanks for the speedy fix, I really appreciate it!

---

### Post by lovinglinux on 2011-05-20
> **beew said:**
> Hi, LovingLinux, 

You are awesome. It works and it works with Mozplugger as well, but Mozplugger doesn't work with the Totem pluggin, though that is another story ( I actually have installed gpdf instead so I no longer need mozplugger, but it would be interesting to try to fix this by editing the conf file when I have time)

Thanks for the speedy fix, I really appreciate it!

You are welcome. 

I will try to do the same for mozplugger/totem using "video/x-theora" and "application/x-totem-plugin", which can only be played by mozplugger and totem respectively.

This way you can choose any of those three plugins by forcing the mime type.

---

### Post by lovinglinux on 2011-05-20
It worked like a charm. So now is possible to choose between mozplugger, gecko or totem.

Funny thing is that Totem is working a lot better with x-totem-plugin than with x-mplayer2.

Now I am going to wrap those things into a plugin menu for Linux users.

---

### Post by beew on 2011-05-20
> **lovinglinux said:**
> You are welcome. 

I will try to do the same for mozplugger/totem using "video/x-theora" and "application/x-totem-plugin", which can only be played by mozplugger and totem respectively.

This way you can choose any of those three plugins by forcing the mime type.

Hi,

How do you set these options? Can't find them in FF's application tab.

Thanks.

---

### Post by mc4man on 2011-05-20
just as a side note on the orig. apple trailer that wouldn't play in FF but would in totem directly (the woodstock link and similar type pages on apple trailers - the ones without the download option'
If you remove the h from the link then it does play directly in FF (again I'm using totem plugin
Ex
[http://trailers.apple.com/movies/focus_features/takingwoodstock/takingwoodstock-fte_720p.mov](http://trailers.apple.com/movies/focus_features/takingwoodstock/takingwoodstock-fte_720p.mov)

---

### Post by beew on 2011-05-20
> **mc4man said:**
> Apple tends to change those links up a bit from time to time


Trailers that have a different setup like here should open in your browser, just expand the drop down, choose the download option > r. click > open in a new tab or window
[http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/](http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/)

Or try this to test the gecko plugin - (i still think the totem plugin is better for some things

This is the url from the above - should just start playing - r. click on > open link in ..
[http://trailers.apple.com/movies/disney/piratesofthecaribbeanonstrangertides/pirates4-wetagain_720p.mov](http://trailers.apple.com/movies/disney/piratesofthecaribbeanonstrangertides/pirates4-wetagain_720p.mov)

Hi, 

Actually I have tried the second link and it worked, the first link is supposed to have a drop down menu that opens up the second link as you said, but I realize that I can't see the drop down options in Linux though they show up in Windows, tried the agent switcher in FF but no luck.

Sorry for being so insistence, I don't really care for these trailers but I am now trying to get someone to wipe Vista to install Ubuntu. It is an easy sell because Vista is crap and she only uses the PC for basic stuffs, but I want to make sure I get some basic features covered. :)

---

### Post by lovinglinux on 2011-05-20
> **beew said:**
> Hi,

How do you set these options? Can't find them in FF's application tab.

Thanks.

You don't. That is done via FVR MimeType menu. Basically what the extension does is to specify the mime type in the embed code that is injected in the page. The video source will still be flv, mp4 or whatever provided by the site, but Firefox will think they are x-matroska, x-totem-plugin or x-theora and thus open the video with the supported plugin. Since each one of those mime types are supported only by one of the three plugins, you force FF to open the video with the plugin you want.

---

### Post by mc4man on 2011-05-20
> 
the first link is supposed to have a drop down menu that opens up the second link as you said, but I realize that I can't see the drop down options in Linux though they show up in Windows, tried the agent switcher in FF but no luck.

I'm not sure what should show in the 'older' style trailer page, only that at times those are harder to play in the browser, you  tend to get redirected back to main page.

The best way I've found here is to do what's shown in screen, -  copying the link, then pasting in the  browser's address bar -  but before going to the page removing the h from '_[COLOR="Blue"]h[/COLOR]720p.mov' in the pasted address
Whether your friend takes to that ..?

---

### Post by beew on 2011-05-20
> **mc4man said:**
> I'm not sure what should show in the 'older' style trailer page, only that at times those are harder to play in the browser, you  tend to get redirected back to main page.

The best way I've found here is to do what's shown in screen, -  copying the link, then pasting in the  browser's address bar -  but before going to the page removing the h from '_[COLOR=Blue]h[/COLOR]720p.mov' in the pasted address
Whether your friend takes to that ..?

The problem is basically that the page doesn't have a link to the actual video  or a play button (See your first link [http://trailers.apple.com/trailers/d...strangertides/]("http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/")
)

I saw  a "play now" button in Windows before but it doesn't show in Linux.  But I just tried the site on my friend's vista machine and the play option is gone too. So at this point it is not my problem any more. :)

I poked around a bit and guess what the stupid site doesn't even work for Mac! Hahahhahahahaha!!! 

[https://discussions.apple.com/message/15229492](https://discussions.apple.com/message/15229492)


Thanks for the help!

---

### Post by beew on 2011-05-20
> **lovinglinux said:**
> You don't. That is done via FVR MimeType menu. Basically what the extension does is to specify the mime type in the embed code that is injected in the page. The video source will still be flv, mp4 or whatever provided by the site, but Firefox will think they are x-matroska, x-totem-plugin or x-theora and thus open the video with the supported plugin. Since each one of those mime types are supported only by one of the three plugins, you force FF to open the video with the plugin you want.

Thanks for the explanations.

---

### Post by LoREZ on 2011-05-20
I know people weren't talking about this, since you wanted to play the trailers within the browsers, but I thought I'd spread this knowledge a bit.  I found it useful.  Put this line in your .bash_aliases file:

```
alias qtrailer='mplayer -cache 8192 -rtsp-stream-over-tcp -user-agent QuickTime/7.6.4'
```

Then just go to an apple trailer, right click and copy the given link (usually parsed by resolution like "HD" or "720p" etc), then type in a terminal:

```
qtrailer [link]
```

Where [link] is the copied link pasted into the terminal windows using cntrl+shift+v.  Of course, you'll need mplayer installed for this to work, but it works beautifully.

On another note, it seems weird that most of the trailers at trailers.apple.com are everything *but* quicktime.  Didn't used to be the case.  IMO this is a good thing -- even seeing webm and ogg in a few.

---

### Post by beew on 2011-05-21
I am afraid you misunderstand, I can play the video with totem (that is qucktime 7.6.6 by the way) once there if there is a play option or a link to the actual media file (see mc4man's posts)

The problem is that I don't find a link to the video file or a "play" option on their main page and I don't think your solution addresses that (I have actually tried something similar by creating an xml file and added it to Firefox's user agent switcher addon and changed the user agent to quicktime 7.6.6 but it didn't work, if it works for you I must have been doing something wrong.)

Check this link to see if there is any play option.
[URL="http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/"]
http://trailers.apple.com/trailers/disney/piratesofthecaribbeanonstrangertides/[/URL]

But then it doesn't show any link to the video file or play option in Windows either and Mac users are complaining that they can't access the trailers as well so I don't think it is a problem on my end.

Thank you for the response though.

---

### Post by LoREZ on 2011-05-21
Oops!  I see your point.  You are right, of course: it isn't you.  The link isn't on the page, as it used to be.  I didn't see this as a glitch, but a change in Apple's site format, when I was looking into it at first.  The trailer is only found by clicking on the movie's website link, which it seems is almost never a quicktime stream (lol).  Yes, I know it used to be right there, and usually in several resolutions.  I *suppose* the safe money is on it being a glitch, but I don't know...

---

### Post by beew on 2011-05-27
Hey, just checked the apple trailers site today and it has been fixed. The totem plugin works a lot better than quicktime in Windows on the same machine! (Friend's PC has vista and I booted into Natty on an external drive) The playback in Natty is smooth, can be stopped and resumed easily and can go full screen. Quicktime cannot do any of these in my friend's native vista.

:)

---


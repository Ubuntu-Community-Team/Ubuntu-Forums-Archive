---
title: "Problem with Quicktime codec in Jaunty"
date: 2009-08-20
forum: Multimedia Software
---

### Post by Psychobudgie on 2009-08-20
Totem has suddenly stopped playing Quicktime movies from the Apple trailers site. [http://www.apple.com/trailers/](http://www.apple.com/trailers/) . Everything was working up until a couple of hours ago. Nothing has been added to the system and nothing has been removed. I've reinstalled all codecs and also reinstalled Totem aswell as tried VLC and MPlayer. When it fails to play it attempts to search for a text/html decoder which also fails. Has apple changed the Quicktime codec or is this something far more obvious that I'm missing?

---

### Post by zshuford on 2009-08-20
No clue, but it just started happening to me too.  I know I applied the auto-update today, but I didn't pay attention to what was in it, and I'm wondering if something there is the cluprit. 

I should also mention I have a Greasemonkey script that lets me download the movies directly - it has stopped working too, making me suspect Apple has done something.

---

### Post by ajgreeny on 2009-08-20
Not working here either.  I use the gecko-mediaplayer plugin and it has always in the past worked with no problem, so I also think Apple must have made changes, unless it's something to do with all the new kernel upgrades recently appearing.  I shall try a previous kernel and see if it makes any difference.

EDIT:
Well, I've just tried with the only other kernel still on my machine (2.6.28-14) and it has made no difference, the .mov trailers are not showing at all, and in the FF- Tools- Page Info page there is nothing showing about a .mov media file, as I think there should be.  I may have to try it in Windows in a minute or two, just to find out if that can play the trailers at the moment.

---

### Post by samcompton on 2009-08-20
Having the same issue on both my Ubuntu computers.  I booted up a live CD of Linux Mint 7 which has all the codecs on the live CD.  Videos not working with that either.  They do still play from my virtualbox windows.  How long will it take someone to get around this?

---

### Post by zshuford on 2009-08-20
I loaded the sit up in VirtualBox, and it was working fine.

---

### Post by ajgreeny on 2009-08-20
> **zshuford said:**
> I loaded the sit up in VirtualBox, and it was working fine.
But which OS in VB?

---

### Post by mobius777 on 2009-08-20
Same here. I recently watched some Quicktime videos on Apple.com/trailers a few days ago, and today it is not working. I am using FF 3.0.11 on Ubuntu 8.04 (I know, I know, leave me alone). The point is, this is not strictly a Jaunty issue. I have GStreamer, of course, and I can view .mov files that I have on my local network without issue. 

I also tried to open the URL directly to the movie directly in MPlayer and VLC, and both failed.  I can only guess that Apple just updated their Quicktime codes, or has done something with they way they are streaming the videos that breaks whatever GStreamer is expecting (that's my guess, anyway). Oddly, the videos I was able to watch a few days ago are now broken as well (when I open in FF, I get the video window with a big red X in it). 

It's extremely irritating, especially since I was trying to show a trailer to someone on my Ubuntu machine, and of course when it didn't work the first thing the guy suggested was "Just use Windows, man". Grrrrr!

---

### Post by efes50cl on 2009-08-20
same here I couldnt watch the avatar movie clip at apple. This sucks......!!!!!:(((((((

---

### Post by TeflonMaster on 2009-08-21
haha I'm guessing everyone in this thread tried to watch the Avatar trailer. Same reason I'm here.

---

### Post by wirelessmonkey on 2009-08-21
To get the .mov file, try this:
```

wget -U QuickTime/7.6.2 http://movies.apple.com/movies/fox/avatar/avatar2009aug0820a-tsr_h1080p.mov

```

from [http://mirzmaster.wordpress.com/]("http://mirzmaster.wordpress.com/2009/08/20/apple-movie-trailer-downloads-are-broken/")

Then play the file with Mplayer or VLC
It worked for me.

---

### Post by Psychobudgie on 2009-08-21
Well atleast that confirms that Apple appear to have made a change. The fact that the movies still play when grabbed using wget seems to suggest it's an issue with the website rather than the codec. Anyone got any idea what is going on here?

---

### Post by zshuford on 2009-08-21
I used the site with Win XP in VirtualBox, and it worked.

Using the WGet direct download posted earlier also worked.

---

### Post by mobius777 on 2009-08-21
Confirmed here too. I was able to download a movie and play it in MPlayer. So yes, it would seem the movies are OK. Apple has just done something to their site and failed to test it on Linux systems.

---

### Post by Psychobudgie on 2009-08-21
It appears that they are now checking the user agent before streaming the videos or have tightened up the checking, either way if you change the user agent (example below) it works. Just need some method of repeating this in Totem or VLC.

mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' 'http://movies.apple.com/movies/sony_pictures/district9/district9-tlr1_720p.mov'

---

### Post by mc4man on 2009-08-21
vlc
```
vlc --http-user-agent QuickTime/7.6.2    http://movies.apple.com/movies/paramount/transformers2/transformersrevengeofthefallen-tlr2r_720p.mov

```
or with some add. caching when needed (1000 = 1 sec

```
vlc --http-user-agent QuickTime/7.6.2  --http-caching 3000  http://movies.apple.com/movies/paramount/transformers2/transformersrevengeofthefallen-tlr2r_720p.mov
```

---

### Post by Psychobudgie on 2009-08-21
> **mc4man said:**
> vlc
```
vlc --http-user-agent QuickTime/7.6.2    http://movies.apple.com/movies/paramount/transformers2/transformersrevengeofthefallen-tlr2r_720p.mov

```
or with some add. caching when needed (1000 = 1 sec

```
vlc --http-user-agent QuickTime/7.6.2  --http-caching 3000  http://movies.apple.com/movies/paramount/transformers2/transformersrevengeofthefallen-tlr2r_720p.mov
```

Nice one. Now if that could be incorporated into the plugin....

---

### Post by vässlan on 2009-08-21
I thought I broke something with the last update I did a couple of days ago, didn't look what got updated. 

So whats apple's problem , you have to have a mac or a pc to watch trailers, that's just idiotic.

---

### Post by bobince on 2009-08-21
Well, it's just typical Apple proprietariness: their position is that you MUST have the QuickTime plugin installed to play their trailers and if the JavaScript on that page can't find the specific QT plugin, they'll push you off to go download it.

It is of no interest to them if you have a different plugin that's perfectly capable of playing .MOV files; they are Apple and have no desire to Play Well With Others.

Hopefully between Flash streaming and HTML5's video tag, this tedious plugin crap (QT, WMP, Real) will eventually be squeezed out of the market.

---

### Post by PatricioLearner on 2009-08-21
that worked nicely for me thanks!
i wish it gets incorporated into the plugins

---

### Post by LADmaticCA on 2009-08-21
Woops. I just made a thread about this same issue. I'm using the gecko media player plugin :(.

---

### Post by Morm on 2009-08-21
Use the User Agent Switcher for Firefox and add the agent mentioned above - 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' and set it as default. I'm using the Mplayer plugin, but I can now watch the trailers just as before. I'm guessing that will work for the Gecko plugin, too.

---

### Post by Garrovick on 2009-08-22
I read something a few weeks ago about Apple trying to eliminate all traces of any of their software being able to work under Linux.  That mainly is for the newest iPods now, but I bet it will be expanded Apple wide.

---

### Post by LADmaticCA on 2009-08-22
> **Morm said:**
> Use the User Agent Switcher for Firefox and add the agent mentioned above - 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' and set it as default. I'm using the Mplayer plugin, but I can now watch the trailers just as before. I'm guessing that will work for the Gecko plugin, too.

I've tried some variations but I haven't got it to work with gecko yet...maybe I'm doing it wrong. I'm new to this user agent thing.

---

### Post by PatricioLearner on 2009-08-22
Yes, can you provide more details about setting up the agent?
Thanks!

---

### Post by Troll_the_Great on 2009-08-23
> **PatricioLearner said:**
> Yes, can you provide more details about setting up the agent?
Thanks!

I would also like to know more about setting up this user agent. Thanks in advance!

---

### Post by exploder on 2009-08-23
Here is how to set the user agent.

[http://img25.imageshack.us/img25/8499/screenshotedituseragent.png](http://img25.imageshack.us/img25/8499/screenshotedituseragent.png)

I also was not clear on how to set this up, so I thought I would post this to clear things up for everyone.

---

### Post by LADmaticCA on 2009-08-23
> **exploder said:**
> Here is how to set the user agent.

[http://img25.imageshack.us/img25/8499/screenshotedituseragent.png](http://img25.imageshack.us/img25/8499/screenshotedituseragent.png)

I also was not clear on how to set this up, so I thought I would post this to clear things up for everyone.

Thank you so much! That got mine working.:)

---

### Post by Troll_the_Great on 2009-08-23
> **exploder said:**
> Here is how to set the user agent.

[http://img25.imageshack.us/img25/8499/screenshotedituseragent.png](http://img25.imageshack.us/img25/8499/screenshotedituseragent.png)

I also was not clear on how to set this up, so I thought I would post this to clear things up for everyone.

Thanks a million, it works for me too!

---

### Post by stevo1977 on 2009-08-23
Maybe I'm having a completely unrelated problem.  I set up the user-agent as described above, with no noticeable difference.

When I right-click on the non-functioning movie and select 'Open with "Movie Player"', Totem returns the error "The playback of this movie requires a text/html decoder plugin which is not installed."  Firefox and apt show no updates available.  Thanks for any ideas.

---

### Post by fromgi on 2009-08-23
I can't find the User Agent within Firefox 3.0.13 or Synaptic.  How do we install it/access it?

---

### Post by stevo1977 on 2009-08-23
You can edit it manually in "about:config" or you can install the User-Agent add-on.  I just searched google for "+firefox "user-agent"" and it was near the top.  Once installed, it becomes an option under "Tools."

---

### Post by theprodejeff on 2009-08-24
I want to thank the person who came up with the whole user agent thing. It work out for me but is there a way to integrate it into the about:config, so that I don´t need to activate the user agent anymore. Again thanks.

If someone could write a small ´´how to´´ for the about:config, that would be nice.

Gtz Jeff

---

### Post by samcompton on 2009-08-24
I just ran across this:  Someone filed a bug with gnome.org.  The poster attached a patch to get gstreamer to workaround this apple issue.  Can some more experienced Ubuntu users explain how to apply the patch?  You can find it attached to the bug report here:  [http://bugzilla.gnome.org/show_bug.cgi?id=592665](http://bugzilla.gnome.org/show_bug.cgi?id=592665)

Thanks.

---

### Post by mc4man on 2009-08-25
To apply that patch you'd need to get the jaunty gst-plugins-good source, apply the diff (patch) (or manually add the lines) to the file "gstsouphttpsrc.c" ( in /ext/soup/), then build and re- install the plugin

My preferred method would to also apply  the jaunty gst-plugins-good,,, .diff.gz and then build as a normal debian package. (that way if the patch isn't useful, or has an unsuitable side effect, you simply mark the plugin for re-install in synaptic to revert to the repo version

( I use hardy and don't see that particular file, but it's right where shown in jaunty

---

### Post by eddietours on 2009-08-25
they user agent no good for me @#$%

---

### Post by Morm on 2009-08-28
This should help anyone having trouble with the user agent.

You can get the User Agent Switcher for Firefox [here]("https://addons.mozilla.org/en-US/firefox/addon/59").

In Firefox, click Tools - Default User Agent - Edit User Agents. Click New - New User Agent. 

Description: Quicktime 7.6.2
User Agent: QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)

Click Ok - Ok. 

Click Tools - Default User Agent - Quicktime 7.6.2.

Enjoy your trailers!

Note: I'm using the mozilla-mplayer plugin since the last time I used the Gecko player I wasn't able to save movies.

---

### Post by Shinger on 2009-08-29
> **Morm said:**
> This should help anyone having trouble with the user agent.

You can get the User Agent Switcher for Firefox [here]("https://addons.mozilla.org/en-US/firefox/addon/59").

In Firefox, click Tools - Default User Agent - Edit User Agents. Click New - New User Agent. 

Description: Quicktime 7.6.2
User Agent: QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)

Click Ok - Ok. 

Click Tools - Default User Agent - Quicktime 7.6.2.

Enjoy your trailers!

Note: I'm using the mozilla-mplayer plugin since the last time I used the Gecko player I wasn't able to save movies.


Did what you said except the mozilla-mplayer plugin it dint work then i installed the plugin but couldnt find the way to attach it to quicktime movies it only shows use quicktime.... or totem.

---

### Post by treesurf on 2009-08-29
Firefox just crashes completely whenever I try to play one of the Apple movie trailers with mozilla-mplayer.  I tried the user agent switcher with no success.

---

### Post by richarglamb on 2009-08-30
I too have this problem, user agent no good. 

Probably didn't help that I tried a variety of file associations and codecs before bothering to read the forums. 

,Thanks for everyone's inputs so far.

---

### Post by Gen2ly on 2009-08-30
I like wirelessmonkeys solution using wget, then you can download it and play it with your favorite movie player.  Only thing is the link on the website:

```
wget -U QuickTime/7.6.2 http://movies.apple.com/movies/fox/avatar/avatar2009aug0820a-tsr_1080p.mov
```

Is different than the download link:

```
wget -U QuickTime/7.6.2 http://movies.apple.com/movies/fox/avatar/avatar2009aug0820a-tsr_h1080p.mov
```

Notice the 'h' before the resolution?  I'm not good enough with bash scripts to be able to do this, but maybe someone with a little more knowledge can help.  Here is the script so far:

```
#!/bin/bash
# quickget - download trailers from Apple website

if [ -z $@ ]; then
  echo "quickget <apple-trailer-url>"; exit
fi

wget -U QuickTime/7.6.2 "$@"
```

Anyone know enough about parameter substitution to do this?

---

### Post by Gen2ly on 2009-08-30
Gotta love [stack overflow]("http://stackoverflow.com/questions/1354109/prepend-to-regex-match").  Thanks to Ian there who helped me out.

```
#!/bin/bash
# atget - download trailers from Apple website

# Usage if no parameters give
if [ -z $@ ]; then
  echo " atget <apple-trailer-url>"; exit
fi

# Prepend 'h' before resolution to create a valid url
newurl=$(echo $@ | sed 's/_\([0-9]*[0-9][0-9][0-9]\)p.mov/_h\1p.mov/g')

# Download trailer and save to the desktop
#wget -U QuickTime/7.6.2 "$newurl" -O $HOME/Desktop/${@##*/}

# Play trailer with mplayer (using 200MB cache to be sure trailer is dl'd first)
mplayer -cache 200000 -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' $newurl
```

Psychobudgie, I couldn't get the mplayer line to work although that would be preferable.  On my computer if mplayer plays the video file faster than download it gets all kinds of nasty gliches.  Any way to pause mplayer until the download is complete?

---

### Post by mc4man on 2009-08-30
> Any way to pause mplayer until the download is complete?

add a -cache xxxx to command (maybe 2048 or 4096

Here the amount of cache needed (either with mplayer or vlc) will depend on the time of day, resolution,  and amount of traffic , Newer trailers are more likely to need a cache, late at night or older ones a smaller or none at all.

(looking thru my terminal history I see both mplayer and vlc will play with or without the h, ....?

---

### Post by Gen2ly on 2009-08-30
Good tip mc4man.  I've added to the script a cache of 200MB.  This should accommodate just about any video on the website.

---

### Post by andrew.46 on 2009-08-30
Hi Gen2ly,

> **Gen2ly said:**
> Good tip mc4man.  I've added to the script a cache of 200MB.  This should accommodate just about any video on the website.

For playback you might want to have a look at the *-cache-min* option which simply sets the percentage of the cache that must be filled for the initial playback. Not the most necessary option but if you have spent a lot of time on your script perhaps this will be a final touch :-). Perhaps a smaller cache and a larger cache fill might get you watching your movie faster?

Andrew

---

### Post by Gen2ly on 2009-08-30
> **andrew.46 said:**
> Hi Gen2ly,

For playback you might want to have a look at the *-cache-min* option which simply sets the percentage of the cache that must be filled for the initial playback. Not the most necessary option but if you have spent a lot of time on your script perhaps this will be a final touch :-). Perhaps a smaller cache and a larger cache fill might get you watching your movie faster?

Andrew

Hey andrew, how ya doin'?  Hmm, hadn't thought of that.  Good thinking, Dang.  Only thing that's holding me back on that is that download speeds depend on the connection people have.  What does the trick for me may not do it for other people.

---

### Post by LarryMi on 2009-08-31
I only needed to add one Preference Name to Firefox.

I typed:

1) about:config

you'll get a list of preference names
within this listing of preference names,

2( click the opposite mouse button

choose: New, String

3) Type "general.useragent.override" press enter
4) Type "QuickTime/7.6.2(qtver=7.6.2;os=Windows NT 5.1Service Pack 3" press enter

That's it.

This is the only line I had to enter.  After that, the trailers played.

---

### Post by lindylex on 2009-09-02
LarryMi, I tried your tip but every time I close the browser and reopen it the configuration is gone.

I am using totem-mozilla what plugin are you using?

I am experiencing the same problem as stevo1977 on post #29.

---

### Post by LarryMi on 2009-09-03
lindylex,

I'm using the Gecko Media Player 0.9.4 plugin.

You might want to add this line to your pref.js file the firefox folder instead:

user_pref("general.useragent.override", "QuickTime/7.6.2(qtver=7.6.2;os=Windows NT 5.1Service Pack 3");

Hope this helps!

---

### Post by biltong on 2009-09-04
Got any ideas on who to get the useragent to work with Opera plugins? 

The only thing I can think of is to add a new Opera menu (standard_menu.ini) to specifically open mplayer(with parameters) to play the link.

Something like this:

mplayer -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' 'http://movies.apple.com/movies/sony_pictures/district9/district9-tlr1_720p.mov'

However, I have not got it right ....yet.  ;-)


UPDATE:

To watch quicktime (HD) videos in Opera:

Create a custom menu entry: (Tools, Preferences, Advanced (tab), toolbars)
add this this to the [Image Link Popup Menu]:

*Item, "Watch with VLC"= Execute program, "/usr/bin/vlc --http-user-agent QuickTime/7.6.2  --http-caching 3000 ", "%l"*

Now you just have to right click on any quicktime link and select "Watch with VLC".
You could add another entry to "Download Quicktime Video".

---

### Post by treesurf on 2009-09-06
> **LarryMi said:**
> I only needed to add one Preference Name to Firefox.

I typed:

1) about:config

you'll get a list of preference names
within this listing of preference names,

2( click the opposite mouse button

choose: New, String

3) Type "general.useragent.override" press enter
4) Type "QuickTime/7.6.2(qtver=7.6.2;os=Windows NT 5.1Service Pack 3" press enter

That's it.

This is the only line I had to enter.  After that, the trailers played.


I added the useragent override to my Firefox config file.  However, whenever I try to play one of the quicktime trailers the browser simply shuts down/closes.  Any suggestions?

I'm using the mozilla-mplayer plugin and Firefox 3.0.13.

---

### Post by lindylex on 2009-09-06
treesurf, this is the same thing that happens to me.  I read that this package version has the solution.  "This bug was fixed in the package mplayerplug-in - 3.55-2ubuntu1" [https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/376932](https://bugs.launchpad.net/ubuntu/+source/mplayerplug-in/+bug/376932)  

The problem is that I need a deb file of this version of mozilla mplayer plugin to install to get things to work.

Any ideas how I might be able to do this?  I could try to building from source but I have never been successfully with building this packaged, it has been a nightmare.

---

### Post by treesurf on 2009-09-07
I think that version of mplayer is only compatible with Karmic.

---

### Post by cb474 on 2009-09-10
Any suggestions how to play this video?

[http://events.apple.com.edgesuite.net/0909oijasdv/event/index.html](http://events.apple.com.edgesuite.net/0909oijasdv/event/index.html)

The user agent trick is working on this for me. Thanks.

I have tried to open the url directly in Totem, Gxine, Mplayer, and VLC, with no luck in any of them.

---

### Post by andrew.46 on 2009-09-10
Hi cb474,

> **cb474 said:**
> Any suggestions how to play this video?

[http://events.apple.com.edgesuite.net/0909oijasdv/event/index.html](http://events.apple.com.edgesuite.net/0909oijasdv/event/index.html)

The 480 file can be played:

```

mplayer rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49aa1576e344addb3ead1a497aaedf11/0909pihvasb23_1_350.mov

```

while the 320 file can be played:

```

mplayer rtsp://a2047.v1413b.c1413.g.vq.akamaistream.net/5/2047/1413/1_h264_110/1a1a1ae656c632970267e04ebd3196c428970e7ce857b81c4aab1677e445aedc3fae1b4a7bafe013/0909pihvasb23_1_220.mov

```

Depending on the vagaries of the network it might be well worthwhile adding some cache in there:

```
mplayer -cache 2048 -cache-min 80 rtsp etc etc
```

All the best,

Andrew

---

### Post by cb474 on 2009-09-10
Thanks for the suggestion. Unfortunately it didn't work for me. I get:

> $ mplayer rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49aa1576e344addb3ead1a497aaedf11/0909pihvasb23_1_350.mov
MPlayer SVN-r29411-4.4.0 (C) 2000-2009 MPlayer Team
137 audio & 299 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49aa1576e344addb3ead1a497aaedf11/0909pihvasb23_1_350.mov.
Resolving a2047.v1412b.c1412.g.vq.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a2047.v1412b.c1412.g.vq.akamaistream.net
Resolving a2047.v1412b.c1412.g.vq.akamaistream.net for AF_INET...
Connecting to server a2047.v1412b.c1412.g.vq.akamaistream.net[63.147.175.46]: 554...
A single media stream only is supported atm.
rtsp_session: unsupported RTSP server. Server type is 'QTSS-Akamai/5.5.4 (Build/489.13; Platform/Linux; Release/Darwin; )'.
Resolving a2047.v1412b.c1412.g.vq.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a2047.v1412b.c1412.g.vq.akamaistream.net
Resolving a2047.v1412b.c1412.g.vq.akamaistream.net for AF_INET...
Connecting to server a2047.v1412b.c1412.g.vq.akamaistream.net[63.147.175.46]: 80...
Server returned 503: error
No stream found to handle url rtsp://a2047.v1412b.c1412.g.vq.akamaistream.net/5/2047/1412/1_h264_350/1a1a1ae555c531960166df4dbc3095c327960d7be756b71b49aa1576e344addb3ead1a497aaedf11/0909pihvasb23_1_350.mov


Exiting... (End of file)


---

### Post by andrew.46 on 2009-09-10
Hi cb474,

> **cb474 said:**
> Thanks for the suggestion. Unfortunately it didn't work for me.

I attach a screenshot of my own efforts :). I don't recognise your version of MPlayer, is that the Karmic version? I suspect MPlayer needs to be compiled against the LIVE555 libraries for this one...

Andrew

---

### Post by Gen2ly on 2009-09-10
Dam andrew, you do some good stuff.  Just switched to windows for a second to watch this. :D

---

### Post by andrew.46 on 2009-09-10
Hi Gen2ly,

> **Gen2ly said:**
> Dam andrew, you do some good stuff.  Just switched to windows for a second to watch this. :D

Why thank you :). I am going to download this speech tonight in my 'off-peak' hours if only to see Steve Jobs who has returned again, this time from his liver transplant. He is a truly amazing man...

Andrew

---

### Post by SilverDrake11 on 2009-09-10
Ok, I read through all the pages of this topic. There seems to be like four different methods to get the apple trailers working. Can someone find the easiest solution to this problem and post it in specific steps? 

Preferably, something that doesn't involve downloading the trailers or firefox addons. I tried the user agent addon, but no avail with the gecko plugin or the totem plugin.

---

### Post by cb474 on 2009-09-10
> **andrew.46 said:**
> Hi cb474,



I attach a screenshot of my own efforts :). I don't recognise your version of MPlayer, is that the Karmic version? I suspect MPlayer needs to be compiled against the LIVE555 libraries for this one...

Andrew

It looks like you're right about needing the LIVE555 libraries. I'm actually using Arch Linux, but this was the only place I could find anyone figuring out this problem. So that's why my version of MPlayer looks funny (also I checked and it doesn't have LIVE555). Although strangely, I tried downloading RealPlayer and still couldn't get those links to work. By the way, where do you get those links? They're different from what show if you just copy the link location of the buttons. E.g.:
> [http://stream.qtv.apple.com/events/sep/0909oijasdv/0909pihvasb23_1_220_ref.mov](http://stream.qtv.apple.com/events/sep/0909oijasdv/0909pihvasb23_1_220_ref.mov)

---

### Post by andrew.46 on 2009-09-10
Hi cb474,

> **cb474 said:**
> It looks like you're right about needing the LIVE555 libraries. I'm actually using Arch Linux, but this was the only place I could find anyone figuring out this problem. So that's why my version of MPlayer looks funny (also I checked and it doesn't have LIVE555). 

Should not be a big problem to compile those in. The standard method for these libraries is:

```

$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib

```

and this is fairly cross-platform and should work well enough on Arch too.

> By the way, where do you get those links? They're different from what show if you just copy the link location of the buttons.

Well, MPlayer will eventually find the exact link and this can be extracted from the MPlayer terminal output but there is a slightly more cunning way by using the little-known utility *strings*. First download the file itself:
```

wget http://stream.qtv.apple.com/events/sep/0909oijasdv/0909pihvasb23_1_220_ref.mov
```

and then interrogate the file with strings:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]strings 0909pihvasb23_1_220_ref.mov [/COLOR]**
moov
rmra
rmda
rdrf
url 
**[COLOR="Red"]rtsp://a2047.v1413b.c1413.g.vq.akamaistream.net/5/2047/1413/1_h264_110/1a1a1ae656c632970267e04ebd3196c428970e7ce857b81c4aab1677e445aedc3fae1b4a7bafe013/0909pihvasb23_1_220.mov[/COLOR]**
rmdr

```

Nobody can tell me that this technique is not more than a little cool :). 

Andrew

---

### Post by cb474 on 2009-09-10
Thanks for the explanation and quick reply! I'll try this later and report the results.

---

### Post by cb474 on 2009-09-12
Alright, well I finally got this working. It turns out Arch has the Live555 libraries as a package. So that was easy to install. And then I built mplayer from source using the script from the AUR repository in Arch, which was already patched to detect the Live555 libraries. Voila. Nice, since I really don't know much about installing from source and compiling.

That solved the problem. I also found out from the Live555 website that VLC comes with its libraries built into it. VLC just wouldn't play the stream using the link directly from the Apple website, but the rtsp link you provided does work in VLC. Of course, it's nice that mplayer can take the link from the Apple website and figure out itself where to get the stream from.

Thanks again for the help and pointing me in the right direction. I just wonder why Apple doesn't want it's website to work for Linux?

---

### Post by andrew.46 on 2009-09-12
Hi cb474,

> **cb474 said:**
> Alright, well I finally got this working. It turns out Arch has the Live555 libraries as a package. So that was easy to install. And then I built mplayer from source using the script from the AUR repository in Arch, which was already patched to detect the Live555 libraries. Voila. Nice, since I really don't know much about installing from source and compiling.

Great to hear that you have it all working :). I will admit that I have a deep fascination with MPlayer, I like the way you can discover something different about the program almost *every* day. BTW lots of Arch users on these forums...

All the best,

Andrew

---

### Post by rmcellig on 2009-10-25
I am using a Dell Dimension 3000. Where exactly in Firefox can I locate the user agent so that I can try the solution mentioned in this thread?

---

### Post by boulderbum on 2009-11-08
Cool...  thanks, this worked for me!

-BB

> **Morm said:**
> This should help anyone having trouble with the user agent.

You can get the User Agent Switcher for Firefox [here]("https://addons.mozilla.org/en-US/firefox/addon/59").

In Firefox, click Tools - Default User Agent - Edit User Agents. Click New - New User Agent. 

Description: Quicktime 7.6.2
User Agent: QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)

Click Ok - Ok. 

Click Tools - Default User Agent - Quicktime 7.6.2.

Enjoy your trailers!

Note: I'm using the mozilla-mplayer plugin since the last time I used the Gecko player I wasn't able to save movies.

---

### Post by blumagic on 2009-11-21
All,

I am using Jaunty and I have been having similar problems with playing apple trailers from:[http://www.apple.com/trailers/](http://www.apple.com/trailers/). What I have found to get the trailers working is the following...

I uninstalled:

totem-mozilla
totem-plugins
totem

I installed:
sudo apt-get install gecko-mediaplayer

I created a new Default User in Firefox3.0.15
Default user Agent to:
Description: Quicktime 7.6.2
User Agent: QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)

Now I am able to view movie trailers. My only issue now is the Default User doesnt stay with Quicktime after closing and reopening Firefox. I have to go in and manually change it back to Quicktime7.6.2 from the Default. I hope this will help others.



thanks,

blu.....

---

### Post by andrew.46 on 2009-11-21
Hi blumagic,

Good to see you have it all sorted out :). A couple of comments: I suspect you don't really have to remove totem itself, just the plugins. Unless of course you have a great dislike for totem? As regards the change of user-agent in Firefox this might not be necessary, and certainly isn't on my own system. A recent version of the gecko-mediaplayer has the ability to manipulate the user-agent setting, or emulation as the gecko-mediaplayer calls it, by itself. I attach a screenshot to demonstrate this.

All the best,

Andrew

---

### Post by SilverDrake11 on 2009-11-29
I recently updated to Karmic (64bit), and it seems that the problem (for whatever reason) doesn't exist anymore. I when I go see Apple's trailers, totem plays them more smoothly than ever.

---

### Post by heyguy on 2009-11-30
I am also using karmic but failed to play the trailers at apples's website i receive the error 
quicktime reuired

---

### Post by almigi on 2009-12-16
> **heyguy said:**
> I am also using karmic but failed to play the trailers at apples's website i receive the error 
quicktime reuired

I just follow the steps outlined in [this post ]("http://ubuntuforums.org/showthread.php?t=766683") up to step two (option one, Gecko Media Player) and everything works fine.

---

### Post by badger_8007 on 2009-12-21
Just to round it up, I'm using Karmic 9.10 and Firefox 3.5.6, I had the same problem, when I opened the trailer page on Apple Trailers, I only got a black rectangle and the movie never played, if I clicked on that space it showed a message saying "Waiting for video". I tried all the solutions posted here to no avail. What worked for me was to search and remove all the packages related to "mozilla plugin" for the players I have installed (in this case, totem-mozilla, mozilla-plugin-vlc). As I had already intalled the gecko plugin, I think these were interfering with it, so after I uninstalled those packages, restarted firefox, and the Apple trailers worked like a charm, without the need to change the user agent on Firefox.

Hope it helps you!  \\:D/

---

### Post by joplass on 2010-01-23
> **Gen2ly said:**
> Gotta love [stack overflow]("http://stackoverflow.com/questions/1354109/prepend-to-regex-match").  Thanks to Ian there who helped me out.

```
#!/bin/bash
# atget - download trailers from Apple website

# Usage if no parameters give
if [ -z $@ ]; then
  echo " atget <apple-trailer-url>"; exit
fi

# Prepend 'h' before resolution to create a valid url
newurl=$(echo $@ | sed 's/_\([0-9]*[0-9][0-9][0-9]\)p.mov/_h\1p.mov/g')

# Download trailer and save to the desktop
#wget -U QuickTime/7.6.2 "$newurl" -O $HOME/Desktop/${@##*/}

# Play trailer with mplayer (using 200MB cache to be sure trailer is dl'd first)
mplayer -cache 200000 -user-agent 'QuickTime/7.6.2 (qtver=7.6.2;os=Windows NT 5.1Service Pack 3)' $newurl
```

Psychobudgie, I couldn't get the mplayer line to work although that would be preferable.  On my computer if mplayer plays the video file faster than download it gets all kinds of nasty gliches.  Any way to pause mplayer until the download is complete?

and where exactly do you park this script?  I want to give it a try.
Thanks

---


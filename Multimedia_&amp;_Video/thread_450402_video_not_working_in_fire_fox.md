---
title: "video not working in fire fox"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by marco2 on 2007-05-21
Hello everyone!
I have installed ubuntu 7.04 version lately. I have followed the instructions for "how to enable video...." given in the documentation section, as well as those given by sticky at the head of this thread. However, when in fire fox I click on a video, the video frame opens up ok and all of the sudden says "stopped" at the bottom left corner of the frame :(.
My question is how can I resolve this issue?
I must mention here that the Flash Player works OK.
Thank you! :)

---

### Post by tkjacobsen on 2007-05-21
I use the mozilla-mplayer plugin, and it works flawlessly.

---

### Post by marco2 on 2007-05-21
> **tkjacobsen said:**
> I use the mozilla-mplayer plugin, and it works flawlessly.
I checked the installed plugins in Fire Fox ( about:plugins). Totem, mediplayer, movie player real player and flash player all show up in the installed list.
Yet, it seem none works.:(

---

### Post by king_arthur on 2007-05-22
I have exactly the same problem, I think it's a bug.
I have filed a report to launchpad.
Sometimes embedded video's or video streams play beautifully, sometimes I get just a blank screen and the "stopped" warning however, right-clicking on the window and opening the video in a separate totem-player works.

I would  like to stay with totem rather than installing the mplayer plugin but in the end I might have to switch over.

BTW, out of curiosity, **tkjacobsen** does it work for you on the Apple site?
For instance, checking a video [on the iPhone page]("http://www.apple.com/iphone/") initially appears to start but nothing happens until I open it with right-click in a separate totem window.

Even worst the situation with [QT video streams]("http://www.apple.com/quicktime/"). Do they work for anybody?

It doesn't even display the page properly on my computer.


/P

---

### Post by chang47 on 2007-05-22
I am beginning to think MPlayner, VLC Player and Totem can only play simple embedded Quicktime and Windows media.  Anything more sophisticated they cannot handle.  To be honest, I am impressed that they can handle them at all.  Still searching the forum for any seamless integration...

Post something here if you've found good solutions.  Real Player 10 is the only good solution to playing real media.

Thanks.:(

---

### Post by RomeReactor on 2007-05-22
Hi. I seem to recall that the problem with totem-mozilla was a bug in xine. I've used the mozilla-mplayer plugin since Breezy, and has worked great with all media; just make sure you uninstall all other video plugins for Firefox (kaffeine-mozilla, mozilla-helix-player, mozilla-plugin-vlc, totem-mozilla), as more likely than not having multiple video plugins installed will cause conflict.

---

### Post by chang47 on 2007-05-22
To report my progress, I think I've found the perfect one!  It's Totem.  The key is to download all the good, the bad and the ugly gstreamer plugins.  See screen shot for all of them.

Here's what happened.  I downloaded Totem and Totem-mozzila-plugin.  When to Firefox checked the about: plugins.  Everything were there.  Go to Quicktime movie trailer page clicked a trailer.  Nothing excepted a box with play button, slider and sound button.  Waited a while to see if things were slow.  Then I went to CNN and clicked on a news video.  Same thing.  I moused over the player area and right clicked just for kick.  A pop-up with a choice of 'open with player' came up.  The player then asked to download codec... Eventually I got all the codec's this way.

I think the concept is that all the players are more like skins in the Windows world.  If they are gstreamer capable then all of them can play any gstreamer supported formats.  So I would guess the xine's players are the same.  The firefox plugins are just that, a hook.  The player still needs the underlying engines to decode the formats.  So you need to download all the gstreamer plugins, not to be confused with firefox plugins.  These plugins are not those plugins. Get it!!!!:p

iPhone movies now actually play, although I still have problems having all of them play.  The first one always played.  May be my network isn't fast enough, I am on a "lite" broadband. That doesn't make sense either as my Windows machines played without problems.

Anyhow, thought I relay the news.  BTW I am on Xubuntu 7.04 on a Dell Celeron 128MB RAM machine.  So if I can play, you should.

---

### Post by king_arthur on 2007-05-23
chang47 thanks for the report.
>  Anyhow, thought I relay the news.  BTW I am on Xubuntu 7.04 on a Dell Celeron 128MB RAM machine.  So if I can play, you should.       Sounds like you have been more capable than me.. :)

Switching to the mozilla-mplayer plugin does help as most of videos play seamlessly however, the iPhone videos still don't play.

Moreover, I prefer the Totem interface as mplayer does not blend into firefox as well as Totem does.
I had a check to my gstreamer plugins and they all appear to be there however, Totem is based on the  xine-lib libraries or are there different versions?
And if yes, how do I link the Totem plugin to my gstreamer libraries?

Could somebody please  explain this? 

Thank you

/P
_[[IMG]http://img340.imageshack.us/img340/9426/totemvi7.th.png[/IMG]](http://img340.imageshack.us/my.php?image=totemvi7.png)_

---

### Post by tkjacobsen on 2007-05-23
> **king_arthur said:**
> chang47 thanks for the report.
Sounds like you have been more capable than me.. :)

Switching to the mozilla-mplayer plugin does help as most of videos play seamlessly however, the iPhone videos still don't play.

Moreover, I prefer the Totem interface as mplayer does not blend into firefox as well as Totem does.
I had a check to my gstreamer plugins and they all appear to be there however, Totem is based on the  xine-lib libraries or are there different versions?
And if yes, how do I link the Totem plugin to my gstreamer libraries?

Could somebody please  explain this? 

Thank you

/P
_[[IMG]http://img340.imageshack.us/img340/9426/totemvi7.th.png[/IMG]](http://img340.imageshack.us/my.php?image=totemvi7.png)_

If you want to use totem with xine install totem-xine and libxine-extracodecs.

If you want to use totem with gstreamer install totem-gstreamer (and remove totem-xine) and all the gstreamer plugins.

---

### Post by king_arthur on 2007-05-23
> **tkjacobsen said:**
> If you want to use totem with xine install totem-xine and libxine-extracodecs.

If you want to use totem with gstreamer install totem-gstreamer (and remove totem-xine) and all the gstreamer plugins.
We can confirm the problem is definitely xine-related.
I followed your instructions and Totem-gstreamer works like a charm now, even on the iPhone videos. :)

Thanks a ton!

/P
[[IMG]http://img413.imageshack.us/img413/6844/totemgssj6.th.png[/IMG]]("http://img413.imageshack.us/my.php?image=totemgssj6.png")

---

### Post by king_arthur on 2007-05-23
> **chang47 said:**
> iPhone movies now actually play, although I still have problems having all of them play.  The first one always played.  May be my network isn't fast enough, I am on a "lite" broadband. That doesn't make sense either as my Windows machines played without problems.

It's not your network.
I have updated to Totem-gstreamer and can now play the first iPhone video of each section but not the other ones. :o
The other links simply don't seem to respond.

Any clues somebody out there?


/P

---


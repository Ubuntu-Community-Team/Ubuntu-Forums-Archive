---
title: "M-Audio Delta 1010LT Config"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by plotloss on 2006-07-31
Hi, just tried the absolute beginners section, thought it may be best to ask in here.

[http://www.ubuntuforums.org/showthread.php?t=226398](http://www.ubuntuforums.org/showthread.php?t=226398)

Any thoughts?

It is, for want of a better phrase, driving me mad.

---

### Post by mpvano on 2006-08-01
Just a note about delta cards on linux.... (I use them in several servers, including some running breezy and dapper "server" installs).

1. Alsa card splitting/joining and sharing via .asoundrc is extremely clumsy - it only works properly if all the applications are owned by the same user, and can be fussy about sequence of application startup/shutdown. With these cards, it also is fussy about data types and sample rates. It also can break if OSS emulation gets into the picture. I'm not sayng it doesn't work, I'm just saying that in my experience, it's not a general solution for sharing the card. It's useful for some things but takes a LOT of trial and error...

2. if you are using any of these cards, the mixer control options can be very confusing. You might want to install the special mixer written for them called envy24control. it's part of the package called alsa-tools-gui and is available from the standard repositories...

3. Depending on what you are trying to do, you might want to consider jack instead. It's not exactly intended to be a general purpose sound daemon - it's more specialized than that, but what it does, it does very well. It and most of the  more useful jack applications are easily installed under Dapper directly from the repositories with no kernel rebuilds or source builds needed unless you need really bleeding edge features.

4. Beware the fact that the ESD sound daemon is the default sound output for most dapper programs. Turn it off in gnome's sound preferences and be aware that it will be reloaded whenever most Dapper versions of common programs that use sound are used unless you change their default launch commands. This behavior is VERY annoying and is the cause of most of the "my sound works, but not always" complaints found in this forum.

5. Be aware that gnome may install its own .asoundrc and trash yours whenever you use any of it's applets or dialogs that talk about changing the default sound card.

6. The Delta cards are GREAT hardware and an excellent value. I love them myself, but do be aware that they have a little bit of a learning curve - be especially aware that they have special hardware to automatically "try to do the right thing" about being opened by applications requesting different clock rates. Unfortunately this means that they "do the wrong thing" when this happens. You'll have better luck with them locking down the clock rate and using the "plughw" devices in alsa to resample audio IO as needed for applications.

hope this information is useful....

Mario

---


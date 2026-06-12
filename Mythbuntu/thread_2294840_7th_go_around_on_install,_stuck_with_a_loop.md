---
title: "7th go around on install, stuck with a loop"
date: 2015-09-13
forum: Mythbuntu
---

### Post by yonnie on 2015-09-13
Using a Zotac 525atom, 4gram, 500ghdd, with hdmi cable to a 54inch Visio TV & Logitech remote kbd/scratchpad.  Rambling mutterings!  Issues I'm having with mythbuntu 64, 14.04.02?

All I want is a central TV-like system that can show me what's on, on the internet with a program schedule, show the news, maybe play a movie, perhaps an old show.  So far, that isn't going so well.

Maybe this is the 5th or 6th go around as I tried installing mythtv onto a different Linux a couple times and got this looping issue with one of the setup screens after the install had completed.  Nice waste of an entire day, thank you!  So I found mythbuntu and am giving it a whirl.

1st problem: during install, the installer wants to know the wifi AP to connect to, after selecting it, the installer does not indicate that you are connected nor disconnected.  It seems you have to click on the AP about 3 times before a text pops up telling you it is connecting.

2nd problem: Oh crap!  The sleep timer went off during the install, where's the magic button to get the display back on?  (cntl + esc, seems to work when the move the mouse doesn't)

3rd problem: Oh double crap, now the TV went off cause there's no video signal!

4th problem: font size is indirectly proportional to screen size, the bigger the monitor the smaller the text.  Right now the font is too small to read, even at 6 inches away.  They're like two or three pixels in size, Absolutely ridiculous, text looks like a stain or dirt!  Used a different computer to read the same screens presented in settings appearance and chose the force font dpi check box.

5th problem: WTF, press the 'menu' key?  Where on the keyboard is the menu key?  I already told this thing during initial install/setup that I'm using a keyboard, NO, I don't want to use my phone!!!

6th problem: I don't have a TV tuner installed, don't want one, don't need one, don't have any available air-channels here.  Why is this software so dense it can't tell the hardware doesn't exist?

7th problem: frontend keeps crashing, haven't quite figured this one yet.  After asking for country & language & hostname, & username, & password, & etc... , & etc..., it loops, forever!.  Have still to see any sort of video as of yet.  Working on install 7, seems to be fewer problems to just start over than to try to muck with the settings afterwards.

8th install, nope: I've had it, done with this nuisance!  Time to go back to using VLC player or Amorok or Dragon Player and an internet browser!  In case of useful suggestions, I'll keep it where it is for a day.

---

### Post by aelfric55 on 2015-09-14
> All I want is a central TV-like system that can show me what's on, on  the internet with a program schedule, show the news, maybe play a movie,  perhaps an old show.
> 6th problem: I don't have a TV tuner installed, don't want one, don't  need one, don't have any available air-channels here.  Why is this  software so dense it can't tell the hardware doesn't exist?

This is the primary issue: Mythtv is at bottom a powerful PVR suite to record TV (over-the-air, cable, satellite) and play the recordings back later. It has had some live tv capability and rather more local video/music file DVD/CD playback capability bolted on, but everything else is secondary to it being a very good PVR suite for TV. So it assumes a TV tuner, and only in more recent versions can a Mythtv backend run at all without a physical TV tuner installed (by using a dummy tuner file.)

However, if you have no interest in recording TV (OTA, cable, satellite) for later playback, as seems to be the case, then Mythtv by far is not the simplest nor the most effective software choice you could make.

---

### Post by yonnie on 2015-09-14
Thanks for the info.  It would be nice to record some internet tv on a timer and record some shows off the cable as the limited dvr we get from them fills-up too fast and then we have to choose what to erase to make space.  But for the most part, I wanted something that would know where all the shows are and help find real news channels as nothing on tv is real news anymore.  I'm sick n tired of propaganda and opinion presented as news!

---

### Post by aelfric55 on 2015-09-15
Not me; I like my propaganda hot 'n fresh. But for those who don't, the MythNetvision plugin on the frontend of a Mythtv system otherwise set up for cable (with a good Linux-compatible TV tuner card) may be a reasonable  way to go. Wiki page at [https://www.mythtv.org/wiki/MythNetvision](https://www.mythtv.org/wiki/MythNetvision)

There are some risks. Chief among them is that you can never pin your trust on any particular plugin (or script) being supported beyond about a week from Tuesday. A bit like Kodi/XBMC addons in that regard. Otherwise, perhaps worth trying. It may work until it doesn't.

Some of your other problems may also be addressed, e.g. 5. "menu key": after installation this defaults to "m" on the keyboard in most contexts (unless you change it). Complete list of default keyboard shortcuts and their contexts at: [https://www.mythtv.org/wiki/Keybindings](https://www.mythtv.org/wiki/Keybindings) ; and 7. frontend loop: You can't configure the frontend until the backend has been completely set up and is actually running, so the frontend can find it. See: [https://www.mythtv.org/wiki/User_Manual:Index](https://www.mythtv.org/wiki/User_Manual:Index) particularly ch. 3 on configuration.

Good luck.

---

### Post by MoebusNet on 2015-09-16
In case you haven't thrown in the towel yet, I went into Myth Control Center and unchecked 'automatically start Mythfrontend'. That allowed me to adjust font size etc. from the Xubuntu desktop so I could configure back & frontend.

---


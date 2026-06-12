---
title: "Mplayer is driving me nuts!!"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by BigSilly on 2007-10-31
I've been at this for an age, and I cannot find a solution. Please help!

For some reason, I cannot play movie trailers, specifically ones from [this site. ]("http://www.empireonline.com/futurefilms/trailers/")It doesn't matter what I select from any of the menus I simply cannot get the trailers to play. The Mplayer box pops up, it says connecting to whatever, then "stopped". I've tried different types of configuration following the various threads around the forums, I've tried uninstalling and reinstalling it, I've tried different plugins, but nothing. I have all the necessary codecs installed, all the stuff that has been recommended from the Medibuntu repo. 

What can I do? I'm at a total loss!

---

### Post by Jose Catre-Vandis on 2007-10-31
I have just tried all three formats (wmv/quicktime and real) and they all work fine with mplayer-mozilla plugin here. Ok, that just makes you feel worse I know!

You obviously have the mozilla-mplayer plugin installed, but do you have all the codecs installed for video/media playback?

I used Automatix2 to install all of these when I set up my Feisty, or visit the Restricted formats page on the wiki to understand how to install without Automatix.

---

### Post by BigSilly on 2007-10-31
I have a whole host of codecs and plugins installed! I've tried mixing and matching in sheer desperation, but nothing seems to work. I have the W32 codecs, Ubuntu restricted extras, non-free codecs...and goodness knows what else. I can't imagine what I've done wrong!

I might have to re-install the system and start again. Maybe something's conflicting somewhere.

---

### Post by BigSilly on 2007-10-31
Well something's definitely not right somewhere. I've just (against my better judgement) installed Automatix2 and installed Swiftweasel and all the codecs etc, and it's exactly the same. "Stopped". That's all I get when I try to run a video clip. I see there's a lot of complaints about this around the forums, but it's incredibly strange to see that some have no bother at all. 

I'd love to know what's wrong, so if anyone has the faintest idea of how to help I'd be most grateful. Thanks in advance.

---

### Post by BigSilly on 2007-10-31
Help?

---

### Post by Gremlinzzz on 2007-10-31
Did ya configure the plugin right click on screen your viewing or trying to view choose X11 video and alsa audio also install smplayer it adds a extra punch to the codecs.
sudo aptitude install smplayer

---

### Post by BigSilly on 2007-10-31
Thanks for your reply. It would seem my MPlayer is already configured to use X11 and alsa, but it doesn't seem to have made a difference. I've just installed SMPlayer too, but even if I copy the URL of the clip into the program, I'm still getting the same results. It goes quickly to "stop" at the bottom left of SMPlayer.

EDIT: Odd, I also have the desktop Mplayer Movie Player installed, and when I copy the URL into that it says, " ERROR Couldn't resolve name for AF_INET6: /www.substance001.net"

Make any sense to anyone?

---

### Post by Gremlinzzz on 2007-10-31
maybe your missing something
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

---

### Post by BigSilly on 2007-10-31
> **Gremlinzzz said:**
> maybe your missing something
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll

No, after another check it appears I do have all of that correctly. The only difference is libxine-extracodecs, which according to apt is replaced by libxine1-ffmpeg, which I have.

:confused:

---

### Post by BigSilly on 2007-10-31
> **BigSilly said:**
> 

EDIT: Odd, I also have the desktop Mplayer Movie Player installed, and when I copy the URL into that it says, " ERROR Couldn't resolve name for AF_INET6: /www.substance001.net"

Make any sense to anyone?

Does this mean anything? Could this be related to my problem? Cheers.

---

### Post by mankidal on 2007-11-13
im using gutsy. from the 1st installation until 2days ago i was able to play movies fine. all of a sudden i got the exact problem that u guys r having. i realized i was messing around with some players(install then remove etc) before. (hope u guys understand what im trying to tell here)

my point is. i got it working again by terminating some apps running/sleeping in the system>admin>system moniter>process. the app was an uninstalled media player. i dont know why it was still there but after removing several times (kinda sticky) i could play movies just fine. FYI, i switch from using totem to mplayer. 

hope this helps

---

### Post by BigSilly on 2007-11-13
Heh, just spotted this post popping into the forums!

Yes, you're right. It seems to me that I had too many media players installed I reckon, and that was causing some kind of conflict somewhere. So I removed VLC and something else that I can't remember now, and checked the MPlayer settings (I'd got some settings wrong) and everything is fine now. I also think that using Compiz Fusion was causing my Totem player to bug out, but that's a different story!

Thanks for your reply though. :)

---


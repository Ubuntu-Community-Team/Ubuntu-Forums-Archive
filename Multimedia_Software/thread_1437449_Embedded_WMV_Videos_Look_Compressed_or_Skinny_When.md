---
title: "Embedded WMV Videos Look Compressed or Skinny When Viewed on Vista"
date: 2010-03-23
forum: Multimedia Software
---

### Post by TheChisler on 2010-03-23
Hi,
I'm running apache2 on Hardy and Karmic machines.   I converted some .flv's to .wmv's using VLC and embedded them in my index.html file.  Now, when I go to view them from Vista machines (32 or 64, IE or Firefox), they look compressed or skinny like this: [http://imgur.com/kaGre.jpg](http://imgur.com/kaGre.jpg)
When viewed on other Ubuntu or XP machines, they look fine.  Any insight would be greatly appreciated.  Thank you!

---

### Post by FakeOutdoorsman on 2010-03-24
Do you absolutely need WMV?  I would recommend avoiding re-encoding to WMV and using a free Flash player such as JW Player or Flowplayer to play the flv files.  I can provide more information if you are interested in a setup like this.

Alternatively, you can try using FFmpeg to re-encode the FLV to WMV if you still want to do this, and using FFmpeg directly may give you more control over your output.  I can attempt an example if this is what you want.

---

### Post by TheChisler on 2010-03-24
**[SIZE=2]Is there HTML code that is universal (ie most video formats will play on most OS's)?[/SIZE]**

Thanks, FakeOutdoorsman, for your reply.  I've been Googling and searching Ubuntu Forums for a couple of days now.  Basically, what I'm trying to do is host videos on my apache2 web server so that my friends and family can visit my page and watch my videos.  I'd like the videos to be viewable on as many OS's as possible so that even Grandma can just click-and-watch without having to install viewers, packages, etc.  I was testing this using vids I downloaded from Youtube using the Firefox plugin 'VideoDownload Helper'. The reason I was converting to WMV's was because that format seemed to be playable on most of the test machines from which I tried to view them.

note: Videos from my camcorder are in .MOV format, but I'd like to be able to show a variety of formats **OR** convert my vids to a format which is more-or-less universally viewable.

Thanks in advance for potential replies!   -TheChisler

---

### Post by FakeOutdoorsman on 2010-03-24
Currently, the most universal method would be to use a Flash based player like YouTube does:

[Re: how would i go about hosting my own flash vids](http://ubuntuforums.org/showpost.php?p=8839069&postcount=3)

Once you prepare your video as shown above, you can then use the [JW Player Setup Wizard](http://www.longtailvideo.com/support/jw-player-setup-wizard) to help you with the HTML code.

---

### Post by TheChisler on 2010-03-25
Wow, **thanks!**  I was under the impression that embedding a flash player was much more complicated than it really is.  I'm now converting to FLV using WinFF (v. 1.0.4-2ubuntu2 on Karmic) and embedding JW player.  Little or no noticeable buffering!
**WinFF**: [COLOR=Blue]_      [http://winff.org/html_new/](http://winff.org/html_new/)_[/COLOR]
**JW Player**: [COLOR=Blue]_[http://www.longtailvideo.com/players/jw-flv-player/](http://www.longtailvideo.com/players/jw-flv-player/)_[/COLOR]

Thanks again!!!!!
.
.
.
.
.
BTW, I did figure out that the original problem was being caused by using VLC to convert.  Even after a different converter, though, buffering times were horrible, and flash is indeed the way to go.

---

### Post by FakeOutdoorsman on 2010-03-25
Which WinFF preset are you using?  You should know that FLV is just a container format, such as AVI or MP4, and can be utilized by several different encoders.  By default, FFmpeg uses the outdated and inefficient "Flash Video (FLV) / Sorenson Spark / Sorenson H.263" encoder with FLV.  You would get much better results using the example in my link above.

---

### Post by TheChisler on 2010-03-25
To answer your question, I was playing around with both flv settings in WinFF (Fullscreen and Widescreen). On the newer version, 1.0.4 in Karmic, the quality seemed ok. On the older version, 0.45.1 in Hardy, I got ok video but no audio, but following the steps in your link worked superbly.  I tried WinFF because I saw the "ffmpeg" in your conversion code and assumed libfaac and X264 were integrated in to ffmpeg or something.

---


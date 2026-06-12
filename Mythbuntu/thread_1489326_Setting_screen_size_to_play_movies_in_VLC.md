---
title: "Setting screen size to play movies in VLC"
date: 2010-05-21
forum: Mythbuntu
---

### Post by Medieval Cow on 2010-05-21
All right, this might get a bit complicated, so hopefully I can explain it in a way that makes sense. I've switched over to using VLC as the default to play ISO files. I'm running MythTV .21+fixes on Mythbuntu 8.04 (the hardware I'm running won't handle the upgrade to .22 or higher) and the internal player does a fine job of playing the ISO files. However, opening them over the network is hit or miss. Sometimes they open fine, sometimes it just freezes and then eventually kicks back out to the Videos screen. Using VLC as the default, however, they open just fine every time.

So here's the problem. When I use the internal player, it conforms to the settings I entered with the awesome screen setup wizard, and everything fits nicely on my TV. When I open things in VLC fullscreen, it goes past those boundaries, and a bit of the picture goes off the screen on either side. So I played around with vlcrc, turned off going fullscreen, played around with the defaults for the size and x- and y-offsets, turned off the controls by default, and have got it almost perfectly within the confines of my screen. Almost. The only problem now is that a little bit of the gray title bar pokes on to the top of the screen. Once it's open, if I remote desktop in, I can move that up so the titlebar goes off the screen and doesn't show. But I can't set it to start up there. Having the y-offset at 0 puts it so that a little gray bar creeps onto the screen, and it ignores inputs that are negative numbers.

So. Right now I have to choose between going fullscreen and having a bit of picture cut off on either side, or not being fullscreen, having the whole picture, but having a little gray line at the top of the screen. Anyone have any ideas? Ideally I'd like to either force the fullscreen display to be smaller (though I'm not particularly confident in finding a way to make fullscreen not be fullscreen, if you see what I mean). I'd also be perfectly happy if anyone knows a way to force the VLC display to open with the title bar just a little bit off the top of the screen, so it doesn't show on my TV. I don't even mind something kludgy, if I could do that with a script, I could map it to a button on my Harmony remote and just hit that after starting a DVD. Hell, even just making the title bar black so it blends in would be better than nothing.

I guess this is kind of a minor thing, and if I have to deal with it one of those two ways, I'll live. It's just kind of a bummer because I'm *this close* to having it set up perfectly, and it'd stink to get stuck on this one last thing.

---

### Post by andree_b on 2010-05-21
Check this thread
[http://ubuntuforums.org/archive/index.php/t-587789.html](http://ubuntuforums.org/archive/index.php/t-587789.html)
for borderless window.

---

### Post by Medieval Cow on 2010-05-21
Hey, that worked perfectly, thanks! I've been Googling this like crazy for about a week, but I never thought to try plugging in "borderless windows" I guess. Hooray, now it's perfect!

Now to just get my backend machine to play nice with my Advanced Format 2 TB drive, and I can start ripping my DVDs like crazy!

---


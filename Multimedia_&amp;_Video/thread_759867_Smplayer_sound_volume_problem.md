---
title: "Smplayer sound volume problem"
date: 2008-04-19
forum: Multimedia &amp; Video
---

### Post by c-shadow on 2008-04-19
I have this strange problem with smplayer (0.5.62) in gutsy - after loading a file sound is very quiet for a while and then jumps to a normal level. Interval changes, sometimes it's quiet for a couple of seconds and sometimes a minute or two. Every other player  works fine, but I really love this one :)
Tried removing the config files, and installing some newer version which didn't block the gnome screensaver :(
Can anyone help finding a solution? 
Or recommend some version which works well with screensaver?
mplayer version is 1.0-rc2.

---

### Post by rvm4000 on 2008-04-19
> **c-shadow said:**
> I have this strange problem with smplayer (0.5.62) in gutsy - after loading a file sound is very quiet for a while and then jumps to a normal level. Interval changes, sometimes it's quiet for a couple of seconds and sometimes a minute or two. Every other player  works fine, but I really love this one :)

I've never seen that problem, but maybe you have enabled the volume normalization filter. Check out in Preferences->General->Audio.

Otherwise try to select a different audio driver (Preferences->General).

> **c-shadow said:**
> Tried removing the config files, and installing some newer version which didn't block the gnome screensaver :(
Can anyone help finding a solution? 
Or recommend some version which works well with screensaver?
mplayer version is 1.0-rc2.

What's the problem with the screensaver? I know newer versions of mplayer may not disable the screensaver, but you can keep using mplayer 1.0rc2 along with the newest version of smplayer.

---

### Post by c-shadow on 2008-04-23
> **rvm4000 said:**
> I've never seen that problem, but maybe you have enabled the volume normalization filter. Check out in Preferences->General->Audio.

Otherwise try to select a different audio driver (Preferences->General).



Yes, I enabled the volume normalization filter, but it turned out to be the combination with "Change volume on every file" causing the problem :)
Thanks for the hint.

> 
What's the problem with the screensaver? I know newer versions of mplayer may not disable the screensaver, but you can keep using mplayer 1.0rc2 along with the newest version of smplayer.

Yes, exactly that...some time ago I tried a newer version od mplayer and it didn't disable the screensaver....reverted back to 1.0rc2 and am now testing smplayer 0.6.0rc4 (SVN r1120).

---

### Post by rvm4000 on 2008-04-23
> **c-shadow said:**
> Yes, exactly that...some time ago I tried a newer version od mplayer and it didn't disable the screensaver....reverted back to 1.0rc2 and am now testing smplayer 0.6.0rc4 (SVN r1120).

The problem with the screensaver in newer versions of mplayer, I think it can be fixed by adding this line to your ~/.mplayer/config:
```

heartbeat-cmd="gnome-screensaver-command -p"

```

---


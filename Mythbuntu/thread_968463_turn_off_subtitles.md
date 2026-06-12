---
title: "turn off subtitles?"
date: 2008-11-02
forum: Mythbuntu
---

### Post by Hawk__0 on 2008-11-02
mplayer's default command appears to show subtitles.  I cantfind some of the switches in the man pages, and all the ones i can seem to have nothing to do with subtitles.  How do I turn them off?

Also, I tried editing ~/.lirc/mplayer to make it so that my # key on my remote (Hauppauge WinTV PVR-350) presses the "j" key, which toggles subs in mplayer, but it doesn't work.
```
begin
        remote = hauppauge_pvr
        prog = mplayer
        button = #
        config = j
        repeate = 0
        delay = 0
end

```

I also tried changing remote to Hauppauge_350, as thats what irw reports:
> 000000000000178e 00 # Hauppauge_350

and it still doesn't work!

---

### Post by Archmage on 2008-11-03
Are just sure that this are soft-coded subs and not hard-coded subs (this one are in the video-picture and therefore can't be removed).

If they subs are soft-coded in most cases you can simply rename/move/delete the sub-file (idx, sub, srt, whatever) and than play the file again.

---

### Post by Hawk__0 on 2008-11-04
bump

---

### Post by Hawk__0 on 2008-11-05
bump

---

### Post by joho500 on 2008-11-07
You can use mplayer commands. To see them, use ```
mplayer -input cmdlist
``` I think the command you want to use in your LIRC-file is ```
sub-visbility 0, sub-visibility 1
``` This toggles the setting.

Hope this helps.

Cheers,
Joost

---

### Post by apoulos on 2009-01-04
It's not sub-visibility, it is sub_visibility.  The toggle didn't work:

config = sub_visibility 0, sub_visibility 1

This did work:

config = sub_visibility # "v" on a keyboard

However, just in case there are multiple languages in the subtitle, I use:

config = sub_select # "j" on a keyboard

I still wonder why we can't just use:

config = v
or
config = j

Here is a wiki about this stuff:
[http://howto.wikia.com/wiki/Howto_configure_MPlayer](http://howto.wikia.com/wiki/Howto_configure_MPlayer)

By the way, after editing ~/.lirc/mplayer, I reload lirc (sudo /etc/init.d/lirc reload) and restart Mythtv Frontend.

---


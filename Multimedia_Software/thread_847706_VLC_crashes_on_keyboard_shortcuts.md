---
title: "VLC crashes on keyboard shortcuts"
date: 2008-07-02
forum: Multimedia Software
---

### Post by zhimsel on 2008-07-02
For some reason (this has been happening for some time now) when VLC is playing (almost always fullscreen) it will crash if I attempt to use any keyboard shortcuts other than the spacebar (pause/play) or "s" (stop). It locks up the entire system which forces me to ctrl-alt-backspace within a second or two (if I wait too long, I have to hard-reboot). I've tried purging and reinstalling EVERYTHING (AFAIK) related to VLC. I just can't figure out what it is. It wouldn't be too much of a problem, as I generally only use the spacebar to pause, but sometimes I miss the key and hit "n" or "b" or something and it locks up. I also miss being able to skip around using ctrl/alt/meta/shift-arrow. Anyone know a solution to this problem? Or willing to help find one?

---

### Post by zhimsel on 2008-07-04
No one knows?

---

### Post by zhimsel on 2008-07-07
Shameless bump for great justice.

---

### Post by Pedram Veisi on 2008-10-20
I have the same problem.

I'm using SMPlayer but there is a problem with sub/idx subtitles so I need to use VLC.

When it crashes you can use this way:

1)Press Alt+Ctrl+F1 (or F2) for terminal.
2)Use this command to find VLC's process Number:

```
ps -A |more
```

4)Kill it:

```
kill *number*
```

5)Press Alt+Ctrl+F7 and come back.It's OK.

It works instead of loging out or hard reboot but I don't know the reason.Hope someone knows.

---

### Post by rvm4000 on 2008-10-20
> **Pedram Veisi said:**
> I'm using SMPlayer but there is a problem with sub/idx subtitles so I need to use VLC.

What problem?

If you use a recent version of smplayer and a recent version of mplayer, there shouldn't be any problem with sub/idx subtitles at all.

---

### Post by Pedram Veisi on 2008-10-21
> What problem?

If you use a recent version of smplayer and a recent version of mplayer, there shouldn't be any problem with sub/idx subtitles at all.

I don't know.It doesn't load sub/idx subtitles.

SMPlayer version is 0.6.3 and it uses MPlayer 1.0rc2.

Thanks.

---

### Post by rvm4000 on 2008-10-21
MPlayer 1.0rc2 doesn't allow frontends to choose accurately the subtitle track. So subtitle selection may fail.

If you update MPlayer that would probably fix the problem. You can get an updated version of MPlayer for Ubuntu Hardy [**here**](http://ubuntuforums.org/showpost.php?p=5994638&postcount=10) ([more info](http://ubuntuforums.org/showthread.php?t=917700))

---


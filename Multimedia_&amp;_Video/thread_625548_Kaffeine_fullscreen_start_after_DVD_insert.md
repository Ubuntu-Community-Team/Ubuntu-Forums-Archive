---
title: "Kaffeine fullscreen start after DVD insert"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by amonsul on 2007-11-28
Hi!

How its possible to start Kaffeine automatically in fullscreen mode after inserting the  DVD-movie?

Thanks!

---

### Post by mtron on 2007-12-05
> kaffeine --help
Usage: kaffeine [Qt-options] [KDE-options] [options] [file]

A media player for KDE 3. Can use multiple backends for playback, default (and recommended) is xine.

Generic options:
  --help                    Show help about options
  --help-qt                 Show Qt specific options
  --help-kde                Show KDE specific options
  --help-all                Show all options
  --author                  Show author information
  -v, --version             Show version information
  --license                 Show license information
  --                        End of options

Options:
  -p, --play                Start playing immediately
  -f, --fullscreen          Start in fullscreen mode
  -m, --minimal             Start in minimal mode
  -a, --audiodriver <argument> Set audio driver [default]
  -x, --videodriver <argument> Set video driver [default]
  -d, --device <argument>   Set Audio-CD/VCD/DVD device path. [default]
  --verbose                 Output xine debug messages
  -w, --wizard              Run installation wizard
  --tempfile                tempfile to delete after use

Arguments:
  file                      File(s) to play. Can be a local file, a URL, a directory or 'DVD', 'VCD', 'AudioCD', 'DVB'.

so to play a dvd in fullscreen:
```
kaffeine -p -f DVD
```

---


---
title: "Can't get youtube -dl to work"
date: 2014-04-10
forum: Multimedia Software
---

### Post by rtroxel2 on 2014-04-10
I downloaded the YouTube downloader youtube -dl, but when I typed the test command into my terminal, I received these errors:

roy@roy-EP45-UD3L:~$ youtube-dl [https://www.youtube.com/watch?v=_iMmE8cwsvw](https://www.youtube.com/watch?v=_iMmE8cwsvw)
[youtube] Setting language
[youtube] _iMmE8cwsvw: Downloading video webpage
[youtube] _iMmE8cwsvw: Downloading video info webpage
[youtube] _iMmE8cwsvw: Extracting video information
Traceback (most recent call last):
  File "/usr/lib/python2.7/runpy.py", line 162, in _run_module_as_main
    "__main__", fname, loader, pkg_name)
  File "/usr/lib/python2.7/runpy.py", line 72, in _run_code
    exec code in run_globals
  File "/usr/bin/youtube-dl/__main__.py", line 7, in <module>
  File "/usr/bin/youtube-dl/__init__.py", line 536, in main
    
  File "/usr/bin/youtube-dl/__init__.py", line 520, in _real_main
    
  File "/usr/bin/youtube-dl/FileDownloader.py", line 475, in download
  File "/usr/bin/youtube-dl/InfoExtractors.py", line 80, in extract
  File "/usr/bin/youtube-dl/InfoExtractors.py", line 405, in _real_extract
  File "/usr/bin/youtube-dl/InfoExtractors.py", line 405, in <genexpr>
KeyError: 'sig'

Can anyone explain what I did wrong?

Thanks, in advance,

Roy

---

### Post by mc4man on 2014-04-10
Generally speaking support for youtube-dl & similar is not supported in this forum, see here
[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---


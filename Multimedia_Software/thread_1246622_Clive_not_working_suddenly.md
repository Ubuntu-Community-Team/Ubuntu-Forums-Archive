---
title: "Clive not working suddenly"
date: 2009-08-21
forum: Multimedia Software
---

### Post by ROY.G.BIV on 2009-08-21
```
**$ clive http://www.youtube.com/watch?v=aS_IYe5JTZ4**

/usr/lib/python2.6/dist-packages/clive/modules.py:114: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
clive 1.0.2 20081014  [Linux]
/usr/lib/python2.6/dist-packages/clive/cache.py:183: DeprecationWarning: BaseException.message has been deprecated as of Python 2.6
  if 'table exists already' in err.message:
http://www.youtube.com/watch?v=aS_IYe5JTZ4&fmt=18                       121.7KB
error: extraction url (&video_id) not found
error: Traceback (most recent call last):
  File "/usr/bin/clive", line 29, in <module>
    Clive().main()
  File "/usr/lib/python2.6/dist-packages/clive/main.py", line 49, in main
    Nomad().run(self._say)
  File "/usr/lib/python2.6/dist-packages/clive/nomad.py", line 96, in run
    self._check_raw_urls(raw_urls)
  File "/usr/lib/python2.6/dist-packages/clive/nomad.py", line 261, in _check_raw_urls
    self._show_queue(raw_urls)
  File "/usr/lib/python2.6/dist-packages/clive/nomad.py", line 402, in _show_queue
    Progress(None)._byteshuman(total_bytes),
  File "/usr/lib/python2.6/dist-packages/clive/progress.py", line 92, in _byteshuman
    i = int(math.floor(math.log(bytes,1024)))
ValueError: math domain error

```

Anyone know why its doing that? I've tried re-installing it, but it still gives that message. This just happened out of the blue for no reason that I can tell... It was working fine..

---

### Post by jwaffolter on 2009-08-21
take a look at this [http://ubuntuforums.org/showthread.php?t=1239750](http://ubuntuforums.org/showthread.php?t=1239750)

---

### Post by ROY.G.BIV on 2009-08-21
Thanks, that did the trick!

---


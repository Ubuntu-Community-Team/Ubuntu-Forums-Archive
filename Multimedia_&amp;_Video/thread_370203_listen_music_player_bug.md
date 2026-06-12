---
title: "listen music player bug?"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Uolirod on 2007-02-25
I have listen 0.4.3-1 installed and while it works reasonably well if I run it from a terminal it seems to output this regularly.  I was hoping that someone might be able to tell me what it means and if I can do something to rectify it.

```
Error catched in a thread: 
Traceback (most recent call last):
  File "/usr/lib/listen/thread_queue.py", line 84, in process_queue
    try: func(*data_func)
  File "/usr/lib/listen/context_web.py", line 581, in fetch_info
    list_btn.append(self.make_btn_artist(artist_name,artist_url,artist_match,artist_image))
  File "/usr/lib/listen/context_web.py", line 689, in make_btn_artist
    sock = urllib.urlopen(image_url)
  File "urllib.py", line 82, in urlopen
    return opener.open(url)
  File "urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "urllib.py", line 297, in open_http
    if not host: raise IOError, ('http error', 'no host given')
IOError: [Errno http error] no host given
```

---

### Post by wesley_of_course on 2007-03-02
Wesley here ;

   Maybe ????????     [http://www.ubuntuforums.org/showthread.php?t=126080&page=25](http://www.ubuntuforums.org/showthread.php?t=126080&page=25)


    page 14

---


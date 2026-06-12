---
title: "Default volume is muted Why???"
date: 2009-01-25
forum: Multimedia Software
---

### Post by yusuo85 on 2009-01-25
whenever i boot my ubuntu machine the sound is always muted by default how can i change this

---

### Post by Sam Lars on 2009-01-25
When you have the volume set where you want it, try
```
sudo alsactl store 0
```
in a terminal.

---

### Post by jsast21 on 2009-10-22
I had the same problem, but when I ran 

```
sudo alsactl store 0
``` 

I get the following error:

alsactl: get_control:209: Cannot read control info '2,0,0,Master Playback Volume,0': No such file or directory

Can someone please point me in the right direction?

Thanks.

Joe.

---


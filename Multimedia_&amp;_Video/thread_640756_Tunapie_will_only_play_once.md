---
title: "Tunapie will only play once"
date: 2007-12-14
forum: Multimedia &amp; Video
---

### Post by ubnewbie2 on 2007-12-14
When I first start Tunapie, I can play one stream, but if I stop it, and try to play another, it does nothing. If tunapie is run from the command line, the following error is reported when I try to play the second stream.


```
Traceback (most recent call last):
  File "/usr/share/tunapie/tunapie2_main.py", line 1041, in OnTunapieToolBarPlayTool
    if (self.videoplayer.find("totem")<0 or self.tvradio.GetValue()==0):
AttributeError: 'TunapieFrame' object has no attribute 'tvradio'

```

---

### Post by Dave Otter on 2007-12-14
Are you using Gutsy.If so I had the same problem and had to uninstall Tunapie and then reinstall the older verion used inn Feistyl

---

### Post by ubnewbie2 on 2007-12-14
> **Dave Otter said:**
> Are you using Gutsy.If so I had the same problem and had to uninstall Tunapie and then reinstall the older verion used inn Feistyl

Yes I am using gutsy.  So how do I install an older version than what synaptic finds for me?

---

### Post by Dave Otter on 2007-12-15
go to Tunapie web site download from there

---


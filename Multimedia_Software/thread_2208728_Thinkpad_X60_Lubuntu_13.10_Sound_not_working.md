---
title: "Thinkpad X60 Lubuntu 13.10 Sound not working"
date: 2014-03-01
forum: Multimedia Software
---

### Post by wiel0033 on 2014-03-01
Posting this in case others had the same issue as me (it's already solved) - 

Thinkpad x60 - the sound wasn't working (or was working very sporadically) - the below thread worked for me in fixing the issue - specifically - editing the alsa-base.conf file

[http://ubuntuforums.org/showthread.php?t=1399453](http://ubuntuforums.org/showthread.php?t=1399453)

Specifically: (from that posting)

> Also, you can try specifying the model keyword:
>     [INDENT]Code:[/INDENT]
    gksu gedit /etc/modprobe.d/alsa-base.conf 
Note - this method didn't work to edit the file in Lubuntu, so I located the file via the file manager, opened the folder as root (it's in the tools menu), then followed the instructions below.[INDENT]
[/INDENT]
> [INDENT]Add the following line to the end of the file, then save and restart:[/INDENT]
    [INDENT]Code:[/INDENT]
    options snd-hda-intel model=thinkpad 
Thanks!

---


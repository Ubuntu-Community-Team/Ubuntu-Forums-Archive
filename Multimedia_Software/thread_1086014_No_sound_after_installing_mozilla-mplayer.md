---
title: "No sound after installing mozilla-mplayer"
date: 2009-03-03
forum: Multimedia Software
---

### Post by zahy on 2009-03-03
Hello 
I just installed mozilla-mplayer on my hardy heron kernel 2.6.24-23-generic. I am using Dell D630 and up to now, sound worked great.  

I did 
```
sudo apt-get install -S mozilla-mplayer
```

Restarted and got no sound. 
The volume control has a red x on it. 

```

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.
```

This is the lspci listing of the sound controller. 

 ```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

```

And when I run 
```
asoundconf list
``` 
I get nothing. 

Where do I go from here? 

Thanks

---

### Post by wolfen69 on 2009-03-03
why did you do -S to install? **sudo apt-get install mozilla-mplayer**  would suffice.

---

### Post by zahy on 2009-03-03
OK. 

First, of course wolfen69, it was only a "mis paste." 
no -s needed. 

problem solved

I just did a 

```
sudo apt-get dist-upgrade gstreamer0.10-alsa
```

---


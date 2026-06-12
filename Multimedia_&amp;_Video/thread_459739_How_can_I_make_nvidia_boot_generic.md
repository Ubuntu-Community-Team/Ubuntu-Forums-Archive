---
title: "How can I make nvidia boot generic?"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by topsites on 2007-05-31
Ok, I am tired of trying to configure xorg and what have you, but at one time my system had to have booted without the latest and greatest drivers and it did ok then.  That is, what driver does Ubuntu use when it's first installed, and how can I make it use this (or really any) generic graphics driver just so I can get some gnome happening?

On that same note, what is the textual interface command for Envy?

---

### Post by thelinuxguy on 2007-05-31
You can use vesa as the video driver and it should give you a decent 1024x768 without acceleration. 
```

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "vesa"
EndSection

```

---

### Post by tseliot on 2007-05-31
> **topsites said:**
> Ok, I am tired of trying to configure xorg and what have you, but at one time my system had to have booted without the latest and greatest drivers and it did ok then.  That is, what driver does Ubuntu use when it's first installed, and how can I make it use this (or really any) generic graphics driver just so I can get some gnome happening?
set the driver to "nv" in the Section Device of your /etc/X11/xorg.conf

> **topsites said:**
> On that same note, what is the textual interface command for Envy?
```
sudo envy -t
```

---

### Post by topsites on 2007-05-31
> **tseliot said:**
> set the driver to "nv" in the Section Device of your /etc/X11/xorg.conf


```
sudo envy -t
```

Ok, thanks for the replies, I'll try the generic tip next, I did figure out the envy -t thing and all that to no avail.

I mean I've spent 3 days trying to get this stupid nvidia card to work, I have tried every single driver (from legacy to normal to new) all with nv and nvidia and many other settings I tried as well, one at a time and this config and that config.  I must've been through the entire process of updateing and upgrading and then removing and reverting a good 3-4 dozen times, I've got 40 or 50 pages of printed and hand-written notes, step-by-steps and all, NOTHING has worked.

So I'm just going in with the generic driver and try that, if it still doesn't work then I'm starting over with a fresh install of the OS, idk what else to do, could be I installed one too many packages, too.

Thanks again, very helpful.

---

### Post by topsites on 2007-06-01
Actually, nothing I tried worked, but I did find a new trick mentioned someplace...

When re-installing Ubuntu from the Iso'd CD, one can manually (and carefully) preserve the existing partition by moving it, provided there is enough space left for both, which I've done.

I suppose, once I move the important files I can then re-partition again, but before I do that I'm burning a Cd-Rom with the files lol.

---


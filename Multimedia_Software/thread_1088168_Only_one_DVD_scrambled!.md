---
title: "Only one DVD scrambled!"
date: 2009-03-05
forum: Multimedia Software
---

### Post by eighty6gt on 2009-03-05
Weird one, IMO.  I have libdvdcss2 installed.  Every DVD I play works except for one, the second disc of "Trailer Park Boys Season 4"!!  The menus work, the behind the scenes/extra features work, but the episodes are scrambled with green dots and garbled sound.

The disc works fine in a windows laptop I have.

Did some digging, found out how libdvdcss works, it seems that it did not "crack" the copy protection on this disc properly, and it hasn't tried again because the keys are cached on the hard disk.

Is there a way to clear the cache?

---

### Post by mc4man on 2009-03-06
The cache is in your home folder -> .dvdcss. Either delete the appropriate folder inside or delete .dvdcss itself, doesn't matter.

You could start vlc like this to try a different method to crack keys (lasts till you reboot

```
export DVDCSS_VERBOSE=2 && export DVDCSS_METHOD=title && vlc dvd://
```

If the disk isn't in your default device then  this and then media -> open disc
```
export DVDCSS_VERBOSE=2 && export DVDCSS_METHOD=title && vlc
``` 

The relevant info will be displayed in the terminal

If you'd rather have info saved then (remove red if problem
```
export DVDCSS_VERBOSE=2 && export DVDCSS_METHOD=title && vlc [COLOR="Red"]dvd://[/COLOR] > vlc_output.txt 2>&1
```

Or delete .dvdcss and try another player, then vlc

---

### Post by eighty6gt on 2009-03-07
Seriously good information, thank you very much, first command worked great.

I can't seem to see the cache directory in my home folder though.  No big deal.

---

### Post by mc4man on 2009-03-07
> I can't seem to see the cache directory in my home folder though. No big deal.

It's a 'hidden dir', Ctrl+h when in home dir.,  or this in terminal to enable showing. (with other useful setting's options
```

nautilus-file-management-properties
```

---

### Post by eighty6gt on 2009-03-07
Hah I had that dialog open but didn't look hard enough for "show hidden."

Thanks again.

---


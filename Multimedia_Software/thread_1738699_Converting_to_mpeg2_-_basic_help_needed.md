---
title: "Converting to mpeg2 - basic help needed"
date: 2011-04-25
forum: Multimedia Software
---

### Post by castalla on 2011-04-25
I have installed various converters - the latest I tried was Arista - there's a preset for DVD PAL.  However, adding to queue fails - presumably because the appropriate codecs or whatever are not installed.  

I need advice on how to enable the appropriate codecs for this conversion type.

Thanks

---

### Post by handy on 2011-04-25
Hopefully this Restricted Formats page will get you out of trouble:

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

---

### Post by castalla on 2011-04-25
I installed the extras - makes no difference.  When I select Add to Queue there's nothing added ....

---

### Post by ron999 on 2011-04-25
> **castalla said:**
> I have installed various converters - the latest I tried was Arista - there's a preset for DVD PAL.  However, adding to queue fails ...
Hi
Have you tried using FFmpeg instead?
Like this:-
```
ffmpeg -i *[COLOR="Red"]filename[/COLOR]* -target pal-dvd output.mpg
```

---

### Post by castalla on 2011-04-25
Yep ... produced a massive file 3 times bigger than the original - and sort of defeats the point of a gui frontend!   Why isn't there anything as easy as Freemake or Super?!!!   I used winff which works - just puzzled why arista can't do the same.

---

### Post by ron999 on 2011-04-25
> **castalla said:**
>  I used winff which works 
So is your problem solved?

---

### Post by castalla on 2011-04-25
Solved in so far as I can convert using one program but not another ... installing the extras was a false trail as winff worked previously.  In fact most other posts seem to suggest that extras are superfluous in Linux Mint ...

---

### Post by handy on 2011-04-25
Great you got a solution. :)

Could you use the thread prefix [SOLVED] ?

---

### Post by castalla on 2011-04-26
It isn't solved in any satisfactory way - it's more or less a workaround!

---

### Post by castalla on 2011-04-26
Solved - forget the rest, use TransArmageddon!

---


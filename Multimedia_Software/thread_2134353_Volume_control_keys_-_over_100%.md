---
title: "Volume control keys - over 100%"
date: 2013-04-10
forum: Multimedia Software
---

### Post by Abke on 2013-04-10
I've got Ubuntu running smoothly for over a couple of months now. The built-in speakers in my Acer Aspire S3 aren't very loud, but by 'boosting' them it's more acceptable. I can do so by configuring the Sound Settings and changing the Output volume over 100% with a simple sliding bar thing. But, the function keys on my keyboard only allow me to change that Output Volume between 0 and 100%. So everytime I need to lower the volume for whatever reason and I want to increase it over 100% again, I have to go into the sound settings and change it; a bit frustrating.

Is there any way I can change the range of my function/volume keys on my keyboard? I'm running Ubuntu 12.04 and, as far as I know, everything on default (except for some modifications noted in [http://www.linlap.com/wiki/acer+aspire+s3](http://www.linlap.com/wiki/acer+aspire+s3))

Thanks in advance.

---

### Post by stinkeye on 2013-04-11
Don't have solution but you may be able to create a script
using pacmd commands.


eg 
This lists my outputs 
```
pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'
```

I only have a headset and the command numbers this sink as "[COLOR=#ff0000]0[/COLOR]".

This command sets the volume to full boost
```
pacmd set-sink-volume [COLOR=#ff0000]0[/COLOR] 100000
```

...while this sets it at the 100% mark
```
pacmd set-sink-volume 0 66666
```

---

### Post by Abke on 2013-04-11
That works for me! Made a new shortcut to boost it to max. It should also be possible to get the volume and than change it in a few steps to the maximum, but simply boosting it to max is enough for me now.

Thanks!

---


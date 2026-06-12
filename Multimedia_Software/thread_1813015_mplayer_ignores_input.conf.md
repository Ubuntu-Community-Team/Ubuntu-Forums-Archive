---
title: "mplayer ignores input.conf"
date: 2011-07-27
forum: Multimedia Software
---

### Post by chitresh4u on 2011-07-27
I am using Ubuntu 11.04 (natty) 32 bit pae kernal. My mplayer (just the plain old mplayer, no gui or frontend) is ignoring ~/.mplayer/input.conf. I then tried removing /etc/mplayer/input.conf thinking that root's input.conf might be interfering. It did not work. I then even tried copying my input.conf to /etc/mplayer/input.conf. It did not work either.
Here is my input.conf
```

##
## MPlayer input control file
##

RIGHT seek +15
LEFT seek -15
PGUP seek +600
PFDWN seek -600
. seek +60
, seek -60
ENTER vo_fullscreen
UP volume +1
DOWN volume -1


```

 Any idea what is wrong? Am I missing anything here ??

---

### Post by chitresh4u on 2011-08-20
Found the problem after so long. One of the key was wrong & hence mplayer was ignoring the whole file. Notice "PFDWN" in the config file. mplayer also reported this in the terminal output. But unfortunately I did not notice it.
```
Unknown key 'PFDWN'
```


> **chitresh4u said:**
> I am using Ubuntu 11.04 (natty) 32 bit pae kernal. My mplayer (just the plain old mplayer, no gui or frontend) is ignoring ~/.mplayer/input.conf. I then tried removing /etc/mplayer/input.conf thinking that root's input.conf might be interfering. It did not work. I then even tried copying my input.conf to /etc/mplayer/input.conf. It did not work either.
Here is my input.conf
```

##
## MPlayer input control file
##

RIGHT seek +15
LEFT seek -15
PGUP seek +600
PFDWN seek -600
. seek +60
, seek -60
ENTER vo_fullscreen
UP volume +1
DOWN volume -1


```

 Any idea what is wrong? Am I missing anything here ??

---


---
title: "Launch X server specifying screen resolution"
date: 2008-12-07
forum: Multimedia Software
---

### Post by Zakhafr on 2008-12-07
Hello,

I used the WoW tutorial to launch it in a separate X server.
```

#!/bin/sh
 
export WOW_PATH=~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/ 
 
gksudo true || ( exit 1 ) 
sudo X :3 -ac -terminate &
cd "${WOW_PATH}"        
sleep 2          
DISPLAY=:3 `which wine` WoW.exe -opengl
```

My problem is that the X server initialises at my max screen resolution 1600x1200.

If I play in this resolution, the game will be slow due to my graphic board.

So question is: **is there a way to launch the X server and specify an initial screen resolution such as 1280x1024?** (instead of default resolution being the max supported resolution)


Kind regards

---


---
title: "make primary monitor permanent"
date: 2011-05-08
forum: Multimedia Software
---

### Post by Lucas32 on 2011-05-08
I have a pc with two monitors connected to my ati video card.
i'm running ubuntu 10.10 and when i boot up, the primary monitor keeps switching to my right monitor.
so i run the following script to change that:
```

#!/bin/bash
# Author: Andrew Martin
# Credit: http://ubuntuforums.org/showthread.php?t=1309247
echo "Enter the primary display from the following:"			# prompt for the display
xrandr --prop | grep "[^dis]connected" | cut --delimiter=" " -f1	# query connected monitors
 
read choice								# read the users's choice of monitor
 
xrandr --output $choice --primary					# set the primary monitor

```

so what do i need to do to make this change permanent?

---


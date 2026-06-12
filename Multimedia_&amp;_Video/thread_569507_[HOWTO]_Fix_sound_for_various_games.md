---
title: "[HOWTO] Fix sound for various games"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by nlindblad on 2007-10-07
Today I wrote a small shell utility for enabling sound in various games. I've seen this particular tip in earlier posts but I thought I'd put together a script to get sound working for games like Enemy Territory, RTCW and possibly others aswell.

```

#!/bin/bash
if [ ! $(whoami) = 'root' ]
        then
                echo "Root-privileges required"
                exit 5
fi
APP="${1}.x86"
echo -n "Fixing sound for application ${APP}  "
echo "${APP} 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "${APP} 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "${APP} 0 0 disable" > /proc/asound/card0/pcm1c/oss
echo "[ OK ]"

```

Fix sound for **Enemy Territory**:
```

sh sound-fix-sh et

```

Fix sound for **RTCW**:
```

sh sound-fix.sh wolfsp

```

---


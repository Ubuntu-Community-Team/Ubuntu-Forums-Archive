---
title: "Alsamixer settings resetting on reboot"
date: 2009-10-23
forum: Multimedia Software
---

### Post by Woodsyx on 2009-10-23
So for some reason my front and surround options in the alsamixer are always muted and at zero volume forcing me to have to manually do it ever time i reboot. Is there some way I can make the changes permanent.

Thanks

---

### Post by Neezer on 2009-10-23
try this:
```

sudo alsactl store 0

```

Got if from here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

If you are doing it for your nth card, change the 0 to n-1. if you only have 1 card, 0 should be fine....

Hope that helps.

---


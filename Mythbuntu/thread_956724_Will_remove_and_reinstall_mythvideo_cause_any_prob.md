---
title: "Will remove and reinstall mythvideo cause any problems?"
date: 2008-10-23
forum: Mythbuntu
---

### Post by larsolav on 2008-10-23
Hello!
I am having problems with [a funky mythvideo issue.]("http://ubuntuforums.org/showthread.php?t=951590") 
So now I wonder if maybe reinstalling mythvideo maybe may solve the issue.

Will doing the following cause any greater problems with MythTV?

```
sudo aptitude remove mythvideo
sudo aptitude install mythvideo
```

Thanks for any input!

Cheers

Lars

---

### Post by ian dobson on 2008-10-24
Hi,

If your just removing Mythvideo/reinstalling it, it shouldn't cause any problems. If you remove mythbackend or mysql then that could wipe out your database/recordings.

Regards
Ian Dobson

---

### Post by larsolav on 2008-10-24
Thanks Ian,
I will give it a try tonight!

---


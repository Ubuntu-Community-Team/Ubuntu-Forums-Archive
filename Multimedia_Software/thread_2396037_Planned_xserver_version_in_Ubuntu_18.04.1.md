---
title: "Planned xserver version in Ubuntu 18.04.1"
date: 2018-07-10
forum: Multimedia Software
---

### Post by kishore3 on 2018-07-10
Planned xserver version in Ubuntu 18.04.1
Team
Do we know what will be the xserver version in Ubuntu 18.04.1, do we have plans to upgrade xserver from 1.19.6 to 1.20?

---

### Post by deadflowr on 2018-07-10
Same as what's in 18.04.
They don't upgrade the hardware stack until point release .2, which will get whatever X stack 18.10 gets.
Then .3 will get whatever 19.04 gets and so on. 
Ending with the .5 release which will get the stacks that the next LTS has, pre-.2 point release.
So
18.04.1 = same as 18.04
18.04.2 = what 18.10 will use
18.04.3 = what 19.04 will use
18.04.4 = what 19.10 will use
18.04.5 = what 20.04 will use
And it'll end at whatever the original stack is for 20.04 for .5.

---

### Post by kishore3 on 2018-07-10
Thank you!

---


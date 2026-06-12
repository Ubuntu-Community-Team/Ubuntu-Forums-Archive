---
title: "Misleading ubuntu software center: ffox sitll 4 b12"
date: 2011-03-17
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by meanpt on 2011-03-17
:( .. and any reinstallation willl brings back the  b12 release; on the other hand, syinapitc already shows the last rc1

---

### Post by cariboo on 2011-03-17
The Software Center uses the same sources list as synaptic, so you should seem the latest firefox version in it.

---

### Post by meanpt on 2011-03-17
:(:( ... I know I should, but I don't :(

---

### Post by cariboo on 2011-03-17
If you click the more info button, it says rc-1

---

### Post by coffeecat on 2011-03-17
> **cariboo907 said:**
> If you click the more info button, it says rc-1

This is an interesting one. Not in mine, it doesn't.

Synaptic tells me I have '4.0~rc1+build1+nobinonly-0ubuntu1'. The more info button in Software Centre tells me 'Firefox 4.0 Beta 12'. Below that it says 'Used: 5 times' and below that "Installed on 2010-12-06".

6th December would have been the date I installed this system, and I'm prepared to believe I used the installed version of Firefox only 5 times before it was upgraded, but I know  I've used Firefox more than 5 times on this machine. :) Practically every day since 6th December, I think.

Looks like a glitch in the way Software Centre presents its information.

@cariboo907, did you by chance install that system when Firefox was already a RC?

---

### Post by kerry_s on 2011-03-17
i think your just tripping over nothing.

---

### Post by cariboo on 2011-03-17
> **coffeecat said:**
> This is an interesting one. Not in mine, it doesn't.

Synaptic tells me I have '4.0~rc1+build1+nobinonly-0ubuntu1'. The more info button in Software Centre tells me 'Firefox 4.0 Beta 12'. Below that it says 'Used: 5 times' and below that "Installed on 2010-12-06".

6th December would have been the date I installed this system, and I'm prepared to believe I used the installed version of Firefox only 5 times before it was upgraded, but I know  I've used Firefox more than 5 times on this machine. :) Practically every day since 6th December, I think.

Looks like a glitch in the way Software Centre presents its information.

@cariboo907, did you by chance install that system when Firefox was already a RC?

No, I think this install is a couple of months old, I don't remember exactly when I installed it. I see the same as kerry_s sees.

---

### Post by chrisccoulson on 2011-03-18
software-center gets its information from app-install-data. The issue is that app-install-data probably needs updating with the new Firefox desktop file (the one that doesn't say beta 12). That usually happens quite frequently, so I wouldn't worry about what you see now.

---


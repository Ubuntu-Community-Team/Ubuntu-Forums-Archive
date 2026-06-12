---
title: "recordMyDesktop does not record sound"
date: 2017-05-23
forum: Multimedia Software
---

### Post by marchello_lippi2 on 2017-05-23
Hi all, 

recordMyDesktop does not record sound -- any ideas why and how to fix? 

If I click Advanced -> Sound then I can see "DEFAULT" in Device field. Should I change it to something else? 

Please tell me what other details I should provide. 

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial

---

### Post by marchello_lippi2 on 2017-05-23
Soved using 

```

[COLOR=#000000]1. Click the "Advanced" button[/COLOR]
[COLOR=#000000]2. Select the "Sound" tab[/COLOR]
[COLOR=#000000]3. In the "Device" box, re-type "DEFAULT" as "default"[/COLOR]
[COLOR=#000000]4. Now the sound works![/COLOR]

```
[https://ubuntuforums.org/showthread.php?t=1428157](https://ubuntuforums.org/showthread.php?t=1428157)

Sorry, bad search before asking.

---


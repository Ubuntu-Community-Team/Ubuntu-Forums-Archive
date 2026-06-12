---
title: "Vlc not working"
date: 2010-01-14
forum: Multimedia Software
---

### Post by bobbyshafter on 2010-01-14
Running Ubuntu 9.10 ,installed vlc via synaptic work fine.
Using the preference setting i download and install a new skin.
When i launch vlc 2 version open ,one with the new and one with the default skin.Vlc is lock up.

I tried uninstalling and reinstalling still the same help.

---

### Post by boriskarloffinablender on 2010-01-14
> **bobbyshafter said:**
> Running Ubuntu 9.10 ,installed vlc via synaptic work fine.
Using the preference setting i download and install a new skin.
When i launch vlc 2 version open ,one with the new and one with the default skin.Vlc is lock up.

I tried uninstalling and reinstalling still the same help.

try this.

```
sudo rm /usr/share/vlc/skins2/nameofskin.vlt
```

replace the nameofskin part with the skin name :)

---

### Post by mc4man on 2010-01-14
to reset to default settings
```
vlc --reset-config
```

or to set to one or other - you shouldn't really run both at once
```
vlc -I qt4
```
```
vlc -I skins2

```

Not all skins are compatible, if that's the issue ..? then try a different one if desired

---

### Post by bobbyshafter on 2010-01-15
Thanks reset to default work "vlc --reset-config"

---


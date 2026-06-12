---
title: "Flash/firefox"
date: 2012-08-17
forum: Multimedia Software
---

### Post by ArminasAnarchy on 2012-08-17
Hi all.

I was recently reading some articles that suggested install  kubuntu-restricted-extras package. I had flash installed already in  Firefox, and wasn't too bothered about the fonts, but thought it would  be useful for DVD/ .mp3 playback.

I've also got the package flashplugin-installer installed, both it and the restricted extras package are fully updated.

The problem is however that Firefox is now not registering the Flash  player as being installed  - Flash isn't displayed in my addons, and nor  it playing any flash videos (e.g. Youbtube).

Presumably the issue is something about the flash plugin installation having moved? Just what is going on here [IMG]http://www.kubuntuforums.net/images/smilies/huh.gif[/IMG] ?

Regards,

AA.

---

### Post by unevenflow on 2012-08-17
Hey, open terminal and try:

```
sudo apt-get purge flashplugin-installer

sudo apt-get install flashplugin-installer
```

---

### Post by ArminasAnarchy on 2012-08-17
> **unevenflow said:**
> Hey, open terminal and try:

```
sudo apt-get purge flashplugin-installer

sudo apt-get install flashplugin-installer
```

Cheers :) Has done the trick - any idea with what actually went wrong in the first place though?

---


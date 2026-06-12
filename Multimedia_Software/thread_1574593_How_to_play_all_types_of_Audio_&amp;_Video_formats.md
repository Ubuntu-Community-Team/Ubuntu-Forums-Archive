---
title: "How to play all types of Audio &amp; Video formats in Ubuntu"
date: 2010-09-14
forum: Multimedia Software
---

### Post by kishorekannan on 2010-09-14
How to play all types of Audio & Video formats in Ubuntu, Help..

---

### Post by sikander3786 on 2010-09-14
Install ubuntu-restricted-extras. It will install codecs for most of the audio and video formats, additionally flash, java, fonts etc (check local laws for copyright on certain formats). Also install VLC, a very capable media player. Type in terminal,

```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras

```

```

sudo apt-get install vlc

```


[COLOR="DarkRed"]**_EDIT:_**[/COLOR] Still if some formats are left out or you want to install the codecs some other way, just open up using your favorite media player and if codecs are available on the repositories, you will see a pop asking to install codecs for the required formats, you can keep on installing from there also.

---


---
title: "direct rendering failed suddenly!!!"
date: 2006-07-27
forum: Multimedia &amp; Video
---

### Post by mailmaldi on 2006-07-27
i did a server install & then did apt-get dist-upgrade & then apt-get install ubuntu-desktop

all worked beautifully...logged in my system & checked for direct rendering

glxinfo | grep rendering...

it showed Yes....

after that i ve only installed 
gcc g++ make elinks gkrellm unrar gdesklets gdesklets-data bum 3ddesktop 915resolution

and ve done ctrl + alt + F7 a couple of times & now suddenly my direct rendering has been disabled....

glxinfo shows NO....help!!!

additional to this i ve only Fetched xserver-xgl package not installed..

---

### Post by mailmaldi on 2006-07-27
and ve done ctrl + alt + F7 a couple of times & now suddenly my direct rendering has been disabled....

i mean ctrl + alt + bsp

---

### Post by tseliot on 2006-07-27
> **mailmaldi said:**
> ...additional to this i ve only Fetched xserver-xgl package not installed..

What do you mean?

---

### Post by mailmaldi on 2006-07-27
all i meant was that although glxinfo | grep rendering showed Yes after the fresh install...it showed no after i did all those things...

i solved it anyway did dpkg-reconfigure xserver-xorg

---


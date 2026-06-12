---
title: "Kodi won't run programs on Ubuntu 14.04"
date: 2015-10-28
forum: Multimedia Software
---

### Post by Dyffo on 2015-10-28
I have been using Kodi ( XBMC ) for the last couple of years. This was running on Linux Mint.
I have changed my allegiance and transferred to Ubuntu 14.04, since which time I cannot get Kodi to function.
I have tried the variants of Kodi Helix 14 and isengard 15.
The programs load from the repositories, but when I try to run them, they just draw a complete blank. They seem to attempt to load and start, then just "do nothing".
Any ideas as to what I am doing wrong.

---

### Post by blm-ubunet on 2015-10-31
Launch from terminal & increase verbosity of logging.
Could be expected that good s/w will log to stdout.
But as kodi also builds for windows there may not be any stdout.. you may need to create/modify file "advancedsettings.xml" to control logging options:
[http://kodi.wiki/view/Log_file/Advanced](http://kodi.wiki/view/Log_file/Advanced)

Or look in
$HOME/.kodi/temp/kodi.log
or
/var/log/kodi/

---

### Post by Dyffo on 2015-11-01
Hi - thanks for this - however  advice from the Kodi forum was to install , as below.
sudo apt-get install librtmp1

This solved all my problems.

---


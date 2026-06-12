---
title: "Ubuntu 12.04.1 TV Time no sound"
date: 2012-12-17
forum: Multimedia Software
---

### Post by jtheb on 2012-12-17
I have TVTime installed on 12.04 on a flash drive and this program works fine.
Today I installed 12.04.1 on my desktop and have no sound in TVtime.

Any thoughts
I see TVtime has a folder in /etc/tvtime and a hidden file .tvtime in the home directory.
That seems strange.

---

### Post by critcris on 2013-02-16
[hrvooje (hrvooje-gmail)]("https://launchpad.net/%7Ehrvooje-gmail")             wrote             on 2009-11-11:                                                            [ #12]("https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/472770/comments/12")                                                               Here is what I did in 9.04 :
 tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -

---


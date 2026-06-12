---
title: "HandBrake Rips DVD's with chapters out of order and repeats."
date: 2009-12-23
forum: Multimedia Software
---

### Post by osc1882 on 2009-12-23
So I used to have no problem ripping dvd's with handbrake and I don't think anything has changed on my end... that I know of. But now when I go to rip a dvd it claims that the DVD has 99 titles and when I rip what it finds... it's the movie but the chapters are all out of order ( from the real movie) and like it will repeat parts of the movie many times. Does anyone have any idea what is going on?

---

### Post by mc4man on 2009-12-23
It's purely a structure protection scheme. There are several types that will employ bogus VTS's and titles, most are easily dealt with.

For those you just need to determine what Titleset/title is the real movie and just rip that. While there are several ways to find that out, usually vlc can tell you (start actual movie -> playback tab -> title) or even most standalone hardware dvd players.

There is one type of s.p. that actually uses multiple VTS's for the movie, in that case you have no chance of ripping properly in linux. (fairly rare atm

---


---
title: "Want to convert record albums to mp3"
date: 2011-09-07
forum: Multimedia Software
---

### Post by dmargerum on 2011-09-07
I'm new to Ubuntu. I would like to convert my record collection into mp3 format so i can put on USB stick/mp3 player. Any ideas what software to use (Audacity?). Also do I need some kind of audio capture device?

---

### Post by K1251 on 2011-09-07
Here's what I did (I'm not saying this is a brilliant method, but it does the job):

[LIST]
[*]Install Audacity (are you familiar with it? have you used it on other platforms?)
[*]Connect an audio lead from the headphone socket of the record player to the LINE IN socket of your computer.
[*]Record each side and use Audacity to edit out the worst clicks. Audacity has a fairly decent plugin for this.
[*]Split track into sections and export each one as an mp3.
[*]You'll need to download the LAME mp3 encoder. To do this, type the following into Terminal:
```
sudo apt-get install lame
```
[/LIST]

Hope this helps!

-K

---

### Post by SoFl W on 2011-09-07
I would use FLAC instead of MP3 but not every portable audio device supports FLAC.

---


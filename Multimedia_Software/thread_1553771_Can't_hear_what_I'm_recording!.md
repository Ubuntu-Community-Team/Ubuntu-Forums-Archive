---
title: "Can't hear what I'm recording!"
date: 2010-08-15
forum: Multimedia Software
---

### Post by CJ_Hudson on 2010-08-15
Hi,
I can't hear what I'm recording in Audacity. Please can someone help/suggest something helpful to solve this problem?
I have tried changing the output in the sound preferences panel but this does not work either.
I'm using Lucid Lynx Ubuntu.

---

### Post by lidex on 2010-08-15
Try paprefs. It may not be installed, in which case:
```
sudo apt-get install paprefs
```
To run:
Alt+F2
```
paprefs
```
On the 'simultaneous output' tab, check/select the option there.

Also:
[http://ubuntuforums.org/showpost.php?p=9329166&postcount=27](http://ubuntuforums.org/showpost.php?p=9329166&postcount=27)

---

### Post by CJ_Hudson on 2010-08-16
Thanks, that's fabulous 
EDIT:
Er... actualy I still can't get it to work. I got Pulse Audio Preferences up and running,and checked the appropriate box, but still no change. Then I tried changing the setting in Audacity as suggested in the link:

"Hi All:

I did a fresh install of Lucid from Hardy this evening and I was able to get sound to word very easily for the apps that matter to me. Here is what I did:

1. Audacity: edit > preferences > device. Then I chose the sound card I wanted to use. Then: edit > preferences > host. Then I chose ALSA.

2. Then on that speaker icon on the upper panel, sound preferences > hardware then I chose my soundcard. ALso, sound preferences > output then I chose my soundcard, again.

Sound now works very well.

Lucid is really great for musicians! Audacity has all of the nice features a musician would routinely want! Especially effect > change tempo

I hope Lucid works out for you, too!

Many thanks for the contributors to this thread who provided hope that I could get Lucid working well!

Phil SMith
Duluth, GA"

but that didn't work either.

It may also help you to know when helping me find a solution that I don't have a separate sound card, just the built-in 'intel' one on the motherboard.

Any further assistance gratefully recieved.

---

### Post by CJ_Hudson on 2010-08-17
Bump

---

### Post by cchhrriiss121212 on 2010-08-17
Edit>preferences>recording then check the software playthrough box.

---

### Post by CJ_Hudson on 2010-08-18
Thanks, that's great.

---


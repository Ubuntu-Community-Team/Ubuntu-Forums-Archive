---
title: "percussion doesn't appear on midi"
date: 2012-06-01
forum: Multimedia Software
---

### Post by pdvrosado on 2012-06-01
I don't know if u guys get this, but i used to compose music on guitar pro on windows, and i dont know why, any midi file played on ubuntu, doesn't show the percussion. It's impossible to hear it, how can i solve this?

---

### Post by shantiq on 2012-06-02
which software?   are you using Rosegarden?   if not i suggest maybe to try that

---

### Post by pdvrosado on 2012-06-02
Im using tux guitar for composing. the problem is that when i play a midi file, and it opens up on the movie player, i can hear guitars (which soound awesome overdriven in linux), but i can't hear the percussion. I only hear the hi-hat and the snare, the bass drum and toms can't be heard. And i think that the bass guitar can't be heard either..

---

### Post by pdvrosado on 2012-06-02
I will try to install rosegarden and see if that's the problem

---

### Post by pdvrosado on 2012-06-02
Nope, it's not from that. Rosegarden can't open the midi file, i can't import it. This most be a error from the midi codec or something right?

---

### Post by shantiq on 2012-06-02
you need timidity   if you have not already got it       > sudo apt-get install timidity or synaptic



play this way   your midi file      ```
timidity yourfilename.mid
```



for Rosegarden you need to start timidity first too thus


```
timidity  --iA
```



[**read this for more info**]("http://ubuntuforums.org/showpost.php?p=11717628&postcount=2")

---

### Post by pdvrosado on 2012-06-02
not solved :/ timidity does the same thing. I can't hear the bass drum and the bass gutiar. I can only listen to the guitars, drumm plates and snare....

---


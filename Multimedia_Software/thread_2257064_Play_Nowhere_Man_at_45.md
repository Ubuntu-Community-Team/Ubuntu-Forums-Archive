---
title: "Play Nowhere Man at 45"
date: 2014-12-16
forum: Multimedia Software
---

### Post by Mark_Lester on 2014-12-16
Once upon a time, long long ago, I had a simple stereo. It was black. It had a a balance control, a bass and a treble.
I also had a copy of Rubber Soul.
If I played Nowhere Man at 45rpm on it, turned the balance all one way, the bass full up and the treble right down, it came out funky as hell.
I have tried sox with speed +1.7, that works fine, bass +20 seems to improve things a touch, but treble -20 doesnt seem to do very much at all,.
The base line should come out above everything else, that's whats all this is about, and it just isnt.
Does anyone know a recipe for this ?.

---

### Post by Mark_Lester on 2014-12-16
this recipe is a bit better, though it's ended up crackly, and actually there stil isnt the bassline.
sox <orignal> <output> mcompand "0.005,0.1 -60,-20 0 0 0" 1600 "0.005,0.1 -60,-60 0 0 0" speed 1.7

---

### Post by MartyBuntu on 2014-12-16
I'm not sure exactly what you're asking...

---

### Post by papibe on 2014-12-16
Hi Mark_Lester.

Have you tried VLC?

It has both speed control, and a graphic EQ.

Just a thought.
Regards.

---

### Post by Yellow Pasque on 2014-12-16
Well, a quick peek at Wikipedia shows Rubber Soul was released in both mono and stereo formats initially. Then, when it was released on CD in '87, George Martin redid the the stereo mix because he didn't like the original one. I'm guessing your vinyl copy was in mono and the digital copy you have now is stereo. That might explain why you can't hear the bass too well on the right channel. When I use the balance knob on my stereo on Nowhere Man, it's the same for me (my source is the 2009 CD box set, which has a remastered version of the '87 stereo mix).

It might be interesting to see if you can purchase the track from the remastered mono's ( [https://en.wikipedia.org/wiki/The_Beatles_in_Mono](https://en.wikipedia.org/wiki/The_Beatles_in_Mono) ) and repeat the experiment.

---

### Post by Bucky Ball on 2014-12-16
Try Audacity. It's in the repos.

---

### Post by paulisdead on 2014-12-20
This thread is awesome.

---


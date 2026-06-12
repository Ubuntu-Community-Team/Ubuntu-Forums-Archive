---
title: "Connecting multiple sound cards together (to create a linux based software mixer)"
date: 2009-01-09
forum: Multimedia Software
---

### Post by the_fragile_left_side on 2009-01-09
Hey,

I basically want to be able to have multiple sound cards be able to connect to each other, for example:

Sound card A has 1 line-in, 1 line-out.
Sound card B has 1 line-in.
Sound card C has 1 line-in.

I want to have Sound card B and Sound card C's line-in to be heard on Sound card A's line-out. I would also like to be able to set the volume at which these line-in(s) are heard at, making it multi channel mixer.

I remember back when I used BeOS there was a simple application to do this kind of stuff (though it was probably just an easy way to plug into the already amazing BeOS sound system). What project / application would I be looking at to do this, ALSA, JACKD, etc?

Note: In the future, I would also like to be able to connect another computer's output sound to this computer via network on a Gigabit (wired) network.

---

### Post by markbuntu on 2009-01-09
Pulseaudio can do this, so can jack. It is not so simple as just clicking a few buttons though not so difficult if you know how to edit files. And once you get it set up it is a easy as clicking a few buttons.

Pulseaudio can easily handle multiple sound cards. You would need to create a virtual device to combine them but unfortunately there is no easy way in pulseaudio to connect sinks (outputs) directly to sources (inputs).

With jack alone you would need to use netjack but I don't now how to do that.

But, you could use pulseaudio and jack together to do what you want to do fairly easily. First, you would need to create a virtual device in pulseaudio to combine the sinks (inputs) using the pulseaudio module-combine. There is info on how to do that here ( The example of module-combine is for combining sinks but works just as well for sources, just change sink to source)

[http://pulseaudio.org/wiki/FAQ](http://pulseaudio.org/wiki/FAQ)

Next you would need to connect that virtual source to the sound card A sink which you can do with jack. Along the way, once the sound is in jack, you could add effects, do a voice over, play along, or record it.

To learn how do that you can look in the ** Ubuntu Studio and jack** section here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

You can also use pulseaudio or jack to set up network streaming and capture. There is a lot of information and a zillion links in the 10,000 page guide.

---


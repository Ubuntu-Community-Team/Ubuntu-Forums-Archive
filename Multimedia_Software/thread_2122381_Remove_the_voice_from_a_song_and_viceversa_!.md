---
title: "Remove the voice from a song and viceversa !"
date: 2013-03-05
forum: Multimedia Software
---

### Post by DjRadu on 2013-03-05
Is there any way in linux (Ubuntu Studio) to remove the voice from a song and vice versa to keep the voice and remove the music ? IN windows are many ways but since i have forevere "divorced" windows i want to learn in Linux,Ubuntu.The music filles i would be processing would be *.Mp3 and maybe *.Ogg and *.Wav !
Thank you ! :)

---

### Post by black veils on 2013-03-05
[http://www.howtogeek.com/56335/how-to-remove-vocals-from-music-tracks-using-audacity/](http://www.howtogeek.com/56335/how-to-remove-vocals-from-music-tracks-using-audacity/)

---

### Post by DjRadu on 2013-03-12
[ 						 							]("http://ubuntuforums.org/member.php?u=1646668")[**[COLOR=#000000]black veils[/COLOR]**]("http://ubuntuforums.org/member.php?u=1646668") Thank you,but some deeper stuff is there ? :-)

---

### Post by black veils on 2013-03-12
what do you mean?

---

### Post by Splashmania on 2013-03-12
when you are doing this you are canceling phases

---

### Post by anymedsrx on 2013-03-12
linux is really cool i hope there must be some solution for the same.

[acne cream]("http://www.anymedsrx.com/tretinoin-cream/")

---

### Post by d_in_Conduct on 2013-03-13
There is no sure-fire way to remove vocals from most music files, no matter which system you are using.  Some early Beatles recordings, especially the ones re-done in German, have the voices in one stereo track and instruments in the other, but you won't find much of that anywhere else.  The how-two black veils suggested sounds like it's too simple to be any good, but it's the best way there is.  There are programs that claim to remove vocals, but they really don't.  

Assuming that the instruments in the recording you are working on are spread around the stereo field and the vocals are dead-center, inverting one track will move all frequencies 180-degrees out of phase.  All frequencies that were identical in hz and amplitude (loudness) between the two tracks will cancel out when one track is inverted.  You may also lose the bass, kick drum, snare, and anything else that is placed dead-center.

You can try an EQ plugin to remove all sounds in the vocal range, but you take out everything else in that range, too.  You would probably have to apply it several times to get it all.  I don't know of any EQs that work in real-time in Linux, so you can't just sweep across the frequencies to find the vocals.  With Audacity, use the Analize > Plot Spectrum on a small portion that contains as much voice and little else to find the frequency to cut, then start EQing from there.

It's rare to be able to remove vocals from a song completely.

---


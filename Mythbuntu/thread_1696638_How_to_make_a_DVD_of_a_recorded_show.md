---
title: "How to make a DVD of a recorded show"
date: 2011-02-27
forum: Mythbuntu
---

### Post by benlyboy on 2011-02-27
Hi all

I have a question that is maybe not really about mythbuntu it's self but as it is related I was hoping that someone could help.

I have a few recordings I would like to save as DVD's, so ether I can keep them, or loan then to a friend to watch. I want the DVD's to be playable in a standard DVD player rather than just on a computer.

The system I want to use to make these DVD's is a ubuntu system, so I'm looking for a way to do this in Linux.

I did install QDVDAuthor but I'm not really sure if this will do what I need to, and if so how to use it.

I used mythweb's direct download to down load the file so the formate of the file i'm working with is mpeg  

Thanks for any help

---

### Post by howefield on 2011-02-27
Try Devede.

It will turn your file into an iso which can then be burned as an image to a DVD.

---

### Post by klc5555 on 2011-02-28
I agree with howefield about using Devede. I use it myself all the time, particularly since mytharchive became pretty much useless around about myth 0.20.2, mostly because of audio sync issues on dvb recordings.

But you may wish to prepare a mythtv cutlist for the recordings, in order to mark the commercials in the recordings, and then use mythtranscode (mythtranscode --mpeg2 --honorcutlist -c[channel] -s[starttime] (or -i[inputfile]) ) to prepare a .tmp file of the mythtv recording with the commercials physically removed according to the cutlist. Then you'd feed this final commercial-free .tmp file to Devede to make your dvd iso file. 

The mythtranscode wiki is here: [http://www.mythtv.org/wiki/Mythtranscode](http://www.mythtv.org/wiki/Mythtranscode)

and to prepare the original cutlist of commercials: [http://www.mythtv.org/wiki/Editing_Recordings](http://www.mythtv.org/wiki/Editing_Recordings)

---

### Post by benlyboy on 2011-03-03
Thanks guys
Sorry it took me a few days to reply, but it's been one of those weeks

I installed devede and it seems it is just what I was looking for. I made a DVD last night and it worked great...will play with the commercials remove next...thanks howefield and kic5555 for the help

---


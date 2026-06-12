---
title: "Playing multiple audio streams through separate outputs. Help."
date: 2015-04-21
forum: Multimedia Software
---

### Post by Colcear_Ionut on 2015-04-21
As the title says, i'm hoping someone could tell me how could I play multiple audio files through separate outputs.
For example: Play file1 through center jack, play file 2 through line jack, etc.
I tried fiddling with mplayer, as I saw someone saying this is possible, but I can't figure it out as i'm a new linux user.
Thanks :)

---

### Post by Bucky Ball on 2015-04-22
*Thread moved to **Multimedia**.*

I've did this about eight years ago but using Windows and Cubase for a 5.1 mix. If you are wanting to access each of the 5.1 channels separately, you are basically trying to do the same thing I did. Never used mplayer so not familiar, but you are going to need some software that can identify and utilise all of your 5.1 outputs. All I can think of that might be able to do this is [Ardour]("http://ardour.org/"), but that may be overkill for what you're doing (you would set up your three files on three tracks of Ardour then route them to the appropriate output channels).

Have you tried installing Jack and fiddling with the routing on that? Jack is in the repositories.

Hopefully someone who has experience doing what you're wanting to do with Linux can jump in soon. I don't use Linux to do anything like this, but that's not to say it isn't possible.

---

### Post by Colcear_Ionut on 2015-04-22
> **Bucky Ball said:**
> *Thread moved to **Multimedia**.*

I've did this about eight years ago but using Windows and Cubase for a 5.1 mix. If you are wanting to access each of the 5.1 channels separately, you are basically trying to do the same thing I did. Never used mplayer so not familiar, but you are going to need some software that can identify and utilise all of your 5.1 outputs. All I can think of that might be able to do this is [Ardour]("http://ardour.org/"), but that may be overkill for what you're doing (you would set up your three files on three tracks of Ardour then route them to the appropriate output channels).

Have you tried installing Jack and fiddling with the routing on that? Jack is in the repositories.

Hopefully someone who has experience doing what you're wanting to do with Linux can jump in soon. I don't use Linux to do anything like this, but that's not to say it isn't possible.

Can you tell me how you did it with Windows and Cubase? Also, is Cubase able to output through multiple sound cards at once?

---

### Post by Bucky Ball on 2015-04-22
> **Colcear_Ionut said:**
> Can you tell me how you did it with Windows and Cubase? Also, is Cubase able to output through multiple sound cards at once?

1/ No. It was eight years ago and have no idea how I configured Cubase for 5.1 output. It is of the hazy past. No doubt there are 'how-tos' out there if you do a little research. Best to just boot Cubase with all your speakers plugged in, load three audio files into three Cubase tracks and get crackin' and book learnin'. Perhaps start [here]("https://duckduckgo.com/?q=cubase+surround+mix"). ;)

2/ No idea, sorry, but I see no reason why it wouldn't. Again, research and experiment.

Support with Cubase is, though, not the stuff of this forum section so best to post in a Cubase forum for that to increase your chances of support ...

---


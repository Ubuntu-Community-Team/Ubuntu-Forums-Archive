---
title: "Audigy LS Surround Sound"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by ondre on 2006-09-20
I'm a recently converted Windows user and one thing I'm having difficulty coping with is the lack of 5.1 surround for my Creative Audigy LS

I was very close to posting what I had hoped was a HOWTO on how to get it to work but unfortunately, freezing apps, loss of sound and the inability to load gnome properly dashed that idea.

While searching on Google, I found this [forum post]("http://www.linuxquestions.org/questions/showthread.php?t=380677") which suggested to create a file in the home folder called .asoundrc

In the file I pasted:
> ##################begin of .asoundrc file
pcm.sound-blaster{
type hw
card 0
}

pcm.sb {
type plug
slave.pcm "audigy"
}

pcm.audigy {
type dmix
ipc_key 1234
slave {
pcm "hw:0,0"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

ctl.sound-blaster {
type hw
card 0
}

#the following lines create a multichanel sound device called default

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
pcm.51mix {
type route
slave.pcm surround51
slave.channels 6
# Front-left
ttable.0.0 1
# Front-right
ttable.0.1 1
# Center
ttable.0.2 1.0
ttable.1.3 1.0
# Rear-right
ttable.0.4 1.0
ttable.1.4 1.0
# Rear-left
ttable.0.5 1.0
ttable.1.5 1.0
}

###########end of .asoundrc file

and then I restarted **alsa-utils** with:
>  sudo /etc/init.d/alsa-utils restart

So far so good, my 5.1 is working great if not better than in Windows.

All of a sudden though, and I'm not sure what triggers it yet, I have no sound or all my apps freeze (even non-Audio/Video apps) when opening them.

At this point I'm force to reboot and when I log into gnome, it doesn't go past the login screen.

To resolve this I go into failsafe Terminal, delete .asoundrc, reboot and I'm good.

*Can someone please offer advice as to how to get the surround sound working with the Audigy LS based on the information I've given?
*Would it also be too much to ask to be able to enable full duplex?

Thanks very much for your time.

ondre.

---

### Post by ondre on 2006-09-30
Any ideas?

---

### Post by FrostyAddict on 2006-10-21
Hello, ondre.  I have the same card installed on my computer.  I tried switching to Linux a couple years ago and couldn't get the card to work.  It turned out that it had its own special chipset seperate from the other Audigy models, so the emu10k1 module wouldn't work.  At the time, the only driver available wasn't free and had a disclaimer saying that it may not completely work--so I didn't buy it (I think it was from Open Sound System).  Then after a few months, a version of ALSA came out that supported it.  So I got a live cd-- a SLAX beta with the proper version and encountered a weird problem: instead of having volume controls for the rear channels, it had a single unnamed bar that didn't appear to do anything.  I tried a number of distros with later versions of ALSA, but that one SLAX beta was the only one that seemed to have any support for the Audigy LS, and even then, only for the programs that used ALSA.  Since I couldn't get any Linux variety to recognize the LS (or my TV tuner), I had to go back to windows on this computer.  Today I installed Ubuntu 6.06 (because I was curious) and the sound only works 80% of the time, no matter what program is playing a sound.  Also, the soundcard's response is a little sluggish when it does work.  This is far better than I ever managed to get it to perform before, but it is still unacceptable.  From what I've seen in these forums, there are a bunch of people with similar problems and no answers.  

Anyway, sorry for making a story out of this.  I recommend that if you want to switch to Linux, you should get a sound card that is known to work well in Linux (this applies to other hardware too).  I know you didn't want to hear that, but then again I didn't want to say it either.  If anyone does know how to fix this, I'd be grateful to know as well.

One more thing, old versions of the driver for this card caused my XP side to randomly hard-shutdown without warning (like once a week).  XP didn't give any clues as to the cause either.  Installing the latest driver fixed it completely.  Come to think of it, this card has caused me a lot of trouble.  But it can put out some good sound, I have to give it that.

---

### Post by ondre on 2006-10-21
Excellent reply! I had been thinking lately about replacing it but money and compatibility are huge factors.

---


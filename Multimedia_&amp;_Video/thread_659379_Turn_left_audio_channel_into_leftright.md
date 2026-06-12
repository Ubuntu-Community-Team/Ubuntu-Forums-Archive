---
title: "Turn left audio channel into left/right"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Mud.Knee.Havoc on 2008-01-05
I'm converting some old VHS tapes into DVDs with my new tv tuner card.  My VCR isn't even stereo... so all of my video that I'm converting has sound coming out of only one speaker.

There's got to be an easy way to duplicate the channel so the same mono sound comes out of both speakers.  My searches aren't coming up with much due to the generic nature of my search terms. :(

I've used Audacity to do a similar thing to get songs running properly in Frets on Fire :guitar:, but not sure which tools I'd use when I'm dealing with video/audio together.

Any hints are appreciated!

---

### Post by aktawa on 2008-01-05
Hi,

You could try to add these lines to your .asoundrc file (or generate one)

> 
pcm.duplicate {  #the name of the new plug
	type plug
	slave {
		pcm "default" #the name of the standard sound device
	}
    ttable.0.0 1  # send left channel_in to left channel_out
    ttable.0.1 1 # send left channel_in to right channel_out
}


and set as output device"plug:duplicate" in your program

---

### Post by gromit190 on 2008-02-11
Okay so that's how you do it with a video or whatever.. But what about the sound output? How can I change the settings so that my left/right-output is inverted?
(Sound that is supposed to go to the left speaker, comes out on the right speaker)

Anyone?
By the way, I'm using Windows XP... Where do i change these settings?

---

### Post by aktawa on 2008-02-12
Is this just temporary or do you want to make it permanent? If you are running the alsa sound system (that should be the default), you can create a file in your homw folder called
".audiorc", where you can alter your sound settings. 

For example following .audiorc creates a new device (also called pcm or plug) with the name "switched"  which has the left channel switched with the right channel. This plug can be set as output device in most of the applications (mplayer, xine, amarok...)

```

pcm.switched {   #the name of the new plug
  type plug
  slave {
    pcm "default" #the name of the standard sound device
  }
  ttable.1.0 1 # send right channel_in to left channel_out
  ttable.0.1 1 # send left channel_in to right channel_out
}

```

You can test it by (speaker-test is in the package alsa-utils) 

```
speaker-test -c 2 -D switched

```

---


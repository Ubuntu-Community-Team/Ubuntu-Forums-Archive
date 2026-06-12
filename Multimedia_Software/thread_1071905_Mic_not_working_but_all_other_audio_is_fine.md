---
title: "Mic not working but all other audio is fine"
date: 2009-02-16
forum: Multimedia Software
---

### Post by crunchfighter on 2009-02-16
I'm trying to get my mic working on 64 bit 8.10.  I've tried it in Sound Recorder and Cheese with no luck.

Other video and audio files play fine through Totem Video Player.

Opening the volume control panel, I find this:
[IMG]file:///home/craig/Desktop/Screenshot-Volume%20Control:%20HDA%20Intel%20(Alsa%20mixer).png
[/IMG]
Notice how the mic icon is x'd out.  Unfortunately, when I adjust this panel, changes aren't saved.

I saw some posts that others had the same problems, but no solutions.

Any ideas?

---

### Post by crunchfighter on 2009-02-16
And how do I insert a saved image?....  Not this way apparently.

---

### Post by Reeman on 2009-02-17
Sometimes the old way is the best, way just open up a terminal and type alsamixer..depending on your soundcard the mike could be muted and being blocked by the audio server which is pulse in the case of Ubuntu. 

I have seen this problem before especially with pulse it has a nasty habit of doing things that you cannot change. I had to removed it from my install and now I just let programs access alsa without pulse. You will lose the Ubuntu Desktop audio stuff but just about everything else seems to work properly! If you are using OSS and pulse then things can really get wacky. Remember to to do an alsactl -store after getting the mike working.

If you shut down the Ubuntu Desktop audio in /preferences/sound then things might work properly. 

The best way to find out is to first kill the pulse audio server processes and see if it is causing the problem..if there is someone on this forum who knows how to stop the pulse audio server from loading or atleast how to make it give up dsp control I will be very greatfull. The same crap happens with the artsd in KDE it just plain ordinary causes havoc! I have seen it throw locks on /dev/dsp and make it so programs that use jackd or alsa just have not got a chance. 

Until the various linux desktops develope some sanity in the use of sound servers we will just have to put up with having to shut the crap off and use more simple proven tools to control sound devices!

---

### Post by mikewu on 2009-02-17
I actually had the same problem a few days ago. Here's what someone else suggested. 

alsamixer -V full
Arrow over to mic and then press the space bar. It should show L-R Capture. Press m to mute the mike. This prevents feedback from the microphone.

Scroll over to capture and press space to bring up the L-R Capture. Move the slider up to 100% with the up arrow key.

Hit escape to exit and save.

That got it to work for me, maybe it will for you too.

Good luck!

---


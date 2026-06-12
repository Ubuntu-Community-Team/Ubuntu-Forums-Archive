---
title: "Audacity unstable in Ubuntu, is Pulseaudio's fault?"
date: 2009-12-19
forum: Multimedia Software
---

### Post by Luigino Bracci on 2009-12-19
Hi everybody,

We are using Audacity 1.3.9 and 1.3.10 in our radio station, with Ubuntu Jaunty 9.04; we have six producers editing complex audios with multiple tracks and up to one hour length. Unfortunely, Audacity gets frozen very frequently (three or four times at a day, for every user), sometimes at the moment of start playing or stop playing an audio.

Finally, I got a way to duplicate the Audacity hangups: 
1) In preferences, check that you are using ALSA/default as the output device.
2) Load an audio with 5 or 6 tracks (you can do it importing an MP3, then copying the track and pasting it 4 or 5 times).
3) Press spacebar as fast as you can, 10 or 20 times.

Spacebar is the key to start/stop playing audio. 

I've reported this to the audacity-devel mailing list [1]; they told me that the problem is an unresolved deadlock "when stopping and starting streams repeatedly somewhere between Audacity, our PortAudio ALSA layer, ALSA's pulse output plugin, and the Pulse client libraries". The problem hasn't been solved yet, because it's not easy to know what is the cause.

The hangups disappears when I choose ALSA/hw:0,0 as the output device. But we are using soundcards without hardware mixing capabilities, and choosing ALSA/hw:0,0 blocks the audio in other applications (Firefox/Flash, etc.). We are using  Intel Corporation ICH7 integrated audio controllers.

I want to try some workarounds. Should I try to remove Pulseaudio from out systems and try ESD or Alsa/dmix? Are there other solutions? Does somebody have a similiar trouble?

[1] [http://sourceforge.net/mailarchive/forum.php?thread_name=200912181409.49839.businessmanprogrammersteve%40gmail.com&forum_name=audacity-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=200912181409.49839.businessmanprogrammersteve%40gmail.com&forum_name=audacity-devel)

---


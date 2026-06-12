---
title: "mplayer audio radio stream recording poor quality with pulsing noise"
date: 2009-04-02
forum: Multimedia Software
---

### Post by ubunter760 on 2009-04-02
I have been recording a audio stream for a while with decent quality using a windows based software, so I know the stream source is good.  When I started recording the stream with mplayer, the sound quality has a lot of noise and spikes (sounds like someone is shaking a maraca or baby rattle in the background).  Could someone take a listen at this short sample and let me know if there is:

1)  Something that could be amiss in my hardware that I should check for
2)  A command line or software configuration that might reduce or eliminate the noise in my stream recording
3)  A filter program that I can add to my script that will clean up the audio after it is finished recording

---

### Post by andrew.46 on 2009-04-02
Hi,

That noise is certainly a little annoying. Can you give the commandline you have used to record this stream / stream location / MPlayer version ?

Andrew

---

### Post by ubunter760 on 2009-04-02
This is the command I am using to capture:

mplayer "http://wmc1.den.liquidcompass.net/WRIFFM?MSWMExt=.asf" -ao pcm:file=/tmp/mystream.wav -vc dummy -vo null ;

The location of the stream is also found with: 

mmsh://wmc1.den.liquidcompass.net/WRIFFM?MSWMExt=.asf

I am using mplayer 2:10~rc2-0ubuntu17

---

### Post by andrew.46 on 2009-04-03
Hi ubunter760,

Good and bad news I guess. I tried the stream with the svn MPlayer and whether simply playing the stream or saving it to wav there is that annoying scraping / 'maracas' noise. So that eliminates 1 and 2 of your original post.

Unfortunately I am not aware of software that would filter out this noise. Have you considered emailing the people streaming the broadcast and telling them there is a problem?

Sorry not to be more help,

Andrew

---

### Post by ubunter760 on 2009-04-03
It's strange.  When I try the stream through my Windows box, the sound is crystal clear.  

[http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WRIFFM&playerType=wmp](http://den-a.plr.liquidcompass.net/standard_plr/audio_player.php?id=WRIFFM&playerType=wmp)

---

### Post by ubunter760 on 2009-04-08
Does anyone else have an idea why this sounds crystal clear when I open [http://wmc1.den.liquidcompass.net/WRIFFM?MSWMExt=.asf](http://wmc1.den.liquidcompass.net/WRIFFM?MSWMExt=.asf) with Windows Media or Winamp on a Windows box, but sounds like crap in Ubuntu?

---


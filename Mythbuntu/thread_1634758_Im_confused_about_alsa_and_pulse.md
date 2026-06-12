---
title: "Im confused about alsa and pulse"
date: 2010-11-30
forum: Mythbuntu
---

### Post by iitywygms on 2010-11-30
I am contemplating a fresh install of mythbunt .24 using maverick.
I am confused as to what I should pursue concerning sound.
I run a separate frontend backend setup.
My frontend machine is a acer revo and I use the spdif out.
The frontend machine will also run boxee and firefox with flash. (youtube)
Should I use alsa or pulse when setting it up with a fresh install?
Will mythbuntu even have pulse installed by default.
I am assuming that pulse is the way of the future.  (From what I have read).
Yet I read that myth shuts off pulse and uses alsa only. Is that still true?
Will pulse deliver "better" sound?
Any advise would be appreciated.
Thanks

---

### Post by thatguruguy on 2010-12-01
> **iitywygms said:**
> I am contemplating a fresh install of mythbunt .24 using maverick.
I am confused as to what I should pursue concerning sound.
I run a separate frontend backend setup.
My frontend machine is a acer revo and I use the spdif out.
The frontend machine will also run boxee and firefox with flash. (youtube)
Should I use alsa or pulse when setting it up with a fresh install?
Will mythbuntu even have pulse installed by default.
I am assuming that pulse is the way of the future.  (From what I have read).
Yet I read that myth shuts off pulse and uses alsa only. Is that still true?
Will pulse deliver "better" sound?
Any advise would be appreciated.
Thanks

Pulseaudio is an audio server.  It sits on top of ALSA.  I don't run boxee, but I do use flash for youtube and hulu desktop with no problems.

Mythbuntu does have pulseaudio installed by default. As of 10.10, OSS (Open Sound System, a different sound system from ALSA) has been removed from the kernel.

As of .24, mythtv has much better pulseaudio support, and no longer shuts off pulseaudio.

Whether pulseaudio delivers "better" sound is up for debate, but it does offer more and different methods of controlling your audio.  Since it adds an additional layer, it can theoretically create a lag for audio for such programs as tvtime. I personally haven't noticed any lag. Lag is not a problem in mythtv, however, since mythtv doesn't directly stream tv from the tuner.

---

### Post by iitywygms on 2010-12-01
> **thatguruguy said:**
> Lag is not a problem in mythtv, however, since mythtv doesn't directly stream tv from the tuner.
It does not stream directly from the tuner... meaning that it is buffered first and then sent to the tv?  Can I say that the same would be true watching an avi file or something like that? Since the avi is stored on the hard drive, which is the same thing as the buffer used in mythtv?
I would imagine then that the lag may be present if watching a video on youtube or something, since it is not buffered on the drive, correct?

---

### Post by nickrout on 2010-12-01
> **iitywygms said:**
> It does not stream directly from the tuner... meaning that it is buffered first and then sent to the tv?  Can I say that the same would be true watching an avi file or something like that? Since the avi is stored on the hard drive, which is the same thing as the buffer used in mythtv?
I would imagine then that the lag may be present if watching a video on youtube or something, since it is not buffered on the drive, correct?

LiveTV in myth is a recording like any other. So the stream is saved to hard drive and then played. There is therefore a time delay.

The real answer to your question is that I believe that pulse will decode and re-encode any digital sound streams, meaning your lovely ac3|dts|hd-audio streams will be played with, which in turn is undesirable.

But it may be that some other software will not work with alsa and forces you into pulse, in which case you may have to compromise your digital sound purity.

But the good thing is it's easy to switch from alsa to pulse while you are playing around without the need to install or uninstall any other software.

So just set up myth, choose the alsa device that is right for your setup, and if it doesn't work with boxee etc you can change it in the myth setup.

---

### Post by nickrout on 2010-12-01
PS I have a revo 1600 and it has no spdif, only hdmi or analogue - what model is yours?

---

### Post by thatguruguy on 2010-12-01
> **iitywygms said:**
> It does not stream directly from the tuner... meaning that it is buffered first and then sent to the tv?  Can I say that the same would be true watching an avi file or something like that? Since the avi is stored on the hard drive, which is the same thing as the buffer used in mythtv?
I would imagine then that the lag may be present if watching a video on youtube or something, since it is not buffered on the drive, correct?

First of all, youtube DOES buffer videos.
Secondly, no, you won't notice a lag with avi or other files.

---

### Post by iitywygms on 2010-12-01
> **nickrout said:**
> 
The real answer to your question is that I believe that pulse will decode and re-encode any digital sound streams, meaning your lovely ac3|dts|hd-audio streams will be played with, which in turn is undesirable.
That is important to me.  I know it is up for debate but I like everything pure.  So I will be using alsa only.  Even if I have to sacrifice boxee to do so.
I will get the exact model of my acer when I get a chance.

Another question.  Does myth even look or use the asound.conf file anymore?  I noticed when I was screwing around that nothing I put in asound.conf would affect myth, but it did affect mylayer and boxee.

---

### Post by thatguruguy on 2010-12-01
> **iitywygms said:**
> That is important to me.  I know it is up for debate but I like everything pure.  So I will be using alsa only.  Even if I have to sacrifice boxee to do so.
I will get the exact model of my acer when I get a chance.

Another question.  Does myth even look or use the asound.conf file anymore?  I noticed when I was screwing around that nothing I put in asound.conf would affect myth, but it did affect mylayer and boxee.

If you're referring to /etc/asound.conf, then the answer is yes.  If you're referring to a file created as .asoundrc in your home directory, it (apparently) can be used by the frontend, but not by the backend.

---

### Post by iitywygms on 2010-12-01
Why then could I put anything I wanted in /etc/asound.conf and mythtv would not stop producing sound or anything, but modifying /etc/asound.conf would cause mplayer and others to fail.  I never had to touch a thing or rescan for audio devices in mythtv.
I know it is a good thing myth is so robust.  I am just trying to understand.
I do not have a asoundrc in my or myths home directory.

---

### Post by iitywygms on 2010-12-01
> **nickrout said:**
> PS I have a revo 1600 and it has no spdif, only hdmi or analogue - what model is yours?

my bad.  The revo is in the bedroom.
this model is ZOTAC - MAGHD-ND01-U

---

### Post by thatguruguy on 2010-12-01
My /etc/asound.conf reads as follows:
```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

I don't have boxee, but this works for myth .24, vlc and tvtime.

---

### Post by iitywygms on 2010-12-02
I found a asound.conf that works for boxee and everything else.
I just wonder if it is affecting the sound of mythtv.  I guess if I can't tell, it's not.

---

### Post by iitywygms on 2010-12-02
Finally, the real fix is found.
Edit /etc/modprobe.d/alsa-base.conf
add this to the bottom.
options snd-hda-intel model=ALC888

I now have sound everywhere. With no asound.conf needed.
:) 
Thanks to everyone for your help.
Although this thread was not started to solve the boxee problem lol.

---


---
title: "Internet radio via Rhythmbox stutters"
date: 2010-07-25
forum: Multimedia Software
---

### Post by JonasDK on 2010-07-25
Hello everyone

I like to listen to internet radio using Rhythmbox, especially NRK Alltid Klassisk that you probably know if you have looked at the default internet radios in Rhythmbox. The problem is that the streaming stops after a few dozen seconds or a few minutes and that Rhythmbox then starts buffering. Sometimes it continues afterwards, sometimes it doesn't. This is also the case with other internetradios sometimes.
Can I help this by changing the 'Network Buffer Size (kB)' option under the Playback preferences? I have set it on 1Mb but nothing seems to help.
I have broadband internet. Is this a problem on the side of NRK itself?

Thanks for the help,
Jonas

---

### Post by ron999 on 2010-07-25
Hi
You could try playing the radio station NRK Alltid Klassisk using a different media player such as VLC or mPlayer.
Then you can decide if it's Rhythmbox that's causing the trouble.

Here are the commands:-

```
vlc http://radio.hiof.no/nrk-alltid-klassisk-172.ogg

```
and
```
mplayer http://radio.hiof.no/nrk-alltid-klassisk-172.ogg
```

---

### Post by JonasDK on 2010-07-25
Thanks for your reply ron999!

I have install mplayer and used the command you suggested.
I am listening to NRK since, and I have had one little strutter in the very beginning.
Data appears in the terminal when listening to the radio, what does the last percentage mean?
I guess that the last percentage means how much the buffer is filled.
It dropped to 0% when it strutted in the beginning.

While typing this the radio stopped. The last percentage dropped to 0% again, strutted a bit and then stopped. In the terminal window it said:
```
nop_streaming_read error : Resource temporarily unavailable
Exiting... (End of file)
```I just re-entered the command and it continued playing. I'm happy that it lasts longer than Rhythmbox but I'm just afraid that the connection to NRK is the problem.

Thanks for the terminal commands! :)
Jonas

---

### Post by ron999 on 2010-07-25
> **JonasDK said:**
>  I'm just afraid that the connection to NRK is the problem.


Yes, I agree with you.
And mPlayer seems to handle the problem a little better than Rhythmbox.

---

### Post by JonasDK on 2010-07-27
Because I had problems with other radiostations too, I found out that the problem wasn't NRK itself. It was because of an instable wireless connection.

Just to clear this out.
Problem solved. :smile:

---


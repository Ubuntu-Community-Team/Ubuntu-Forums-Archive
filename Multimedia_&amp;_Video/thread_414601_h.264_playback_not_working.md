---
title: "h.264 playback not working"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by horse127 on 2007-04-20
hi all,

installed 7.04 today and trying to get h.264 playback working smoothly, if the program doesnt crash or give me an error it runs at ~2fps.

Tried VLC, gxine, mplayer and totem.

its in a MKV container if that makes any difference.

how do it get this working properly?

Cheers
Paul

---

### Post by ubuntu27 on 2007-04-20
Did you install the restricted codecs for your specific Ubuntu version?

Here, follow the following link:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)



Also, I recommend you to use Xine, and not toem or other player. Mplayer seems to be good, but it just too complicated. 
Install Xine.... pardon me, I forgot the name [I am not using my comp]. But it should be a stand alone application that starts with Xine (not gxine).


EDIT: The package name is xine-ui

Open the terminal which is located at Application Menu/Accesories/Terminal    in Ubuntu

and type


```
sudo apt-get install xine-ui
```

or

```
sudo aptitude install xine-ui
```

---

### Post by horse127 on 2007-04-20
thanks significantly better but just not 100% play back speed is still say 15 fps

---

### Post by ubuntu27 on 2007-04-20
SOrry, I don't know how to boot playback speed. Hope someone will reply to this.


How much RAM do you have by the way?

---

### Post by horse127 on 2007-04-20
512mb with a 1.6ghz p3.

think that may be the issue, all other avi's etc play fine and other HD media works 99% of the time.

Cheers
Paul

---

### Post by stefangr1 on 2007-04-20
Yes, that's definitely the problem. I don't know what resolution the movie you're trying to play is, but h264 takes much more system resources than mpeg or even avi. I think especially your processor is to slow. I have an athlon 3500+, and that's only just enough to play 720p h264 movies. Btw.: I think the memory isn't the problem, coz usually it's the processor that hangs at 99% or so, while mplayer uses only 10% or less at the memory.

---


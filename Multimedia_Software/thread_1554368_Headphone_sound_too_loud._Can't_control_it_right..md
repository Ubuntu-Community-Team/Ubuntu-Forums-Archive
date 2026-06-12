---
title: "Headphone sound too loud. Can't control it right."
date: 2010-08-16
forum: Multimedia Software
---

### Post by nelfer on 2010-08-16
Hi,

I have a laptop DELL Latitude D600. The sounds works great and I can control it with the laptop buttons (increase/decrease/mute volume).

I just upgraded to Ubuntu 10.04. In prior versions, I could control independently the volume for the speakers and for the headphones. And I was able to "join" them together so that when I increase the volume, it increases in both.

Now in 10.04 I can't find where to join them. But that's fine. The problem I have now is that the volume for the headphones seems to be a 10x multiplier of the "master" volume. For example, in order to hear "normal" on the headphones, the master volume has to be almost on mute. If I increase to 1/4 of the way out, the sound is too loud for a human being.

I went to alsamixer to see what's going on and started with everything at 0.

So I put my mouse on top of the volume control on the taskbar and with one "click" on the wheel (to increase volume) I get this:

```
Item: PCM [dB gain: 0.00, 0.00]                      Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;               &#9474;
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;  &#9474;               &#9474;
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;  &#9474;               &#9474;
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               >
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               &#9474;
&#9474;     &#9474;  &#9474;     &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;     &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;               &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;    pre 3D     &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;                       &#9474;MM&#9474;     &#9474;OO&#9474;               &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;                       &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9474;
&#9474;     0<>0      0      65<>65     0        0               74<>74 
```


Headphones: 65
PCM: 74

That's just one 'click' of the wheel... and the volume control shows almost nothing on the volume bar (the tooltip says Output: 5% -75.70 dB.

In the past the 5% gain in the output was proportional for the headphones. But now it's multiplied by a lot. This makes the volume control useless when using headphones. I have to go to alsamixer to adjust manually.

And to top it off, the new Ubuntu doesn't have the "old" volume control where you can see the level of each output element.

Any help will be appreciated (at least to make the volume increase/decrease proportional).

Thanks.

---

### Post by georgeen on 2010-08-16
Have you tried deleting .pulse folder in your user's home directory and re-login?, sometimes that works for some weird audio problems.

---

### Post by nelfer on 2010-08-17
I'll try that and let you know

---

### Post by Fromanator on 2010-09-29
I am also having this problem as well on a Dell D600, I can not join both master and headphone like in previous ubuntu versions (I am also using 10.04). This laptop is strange in that the master doesn't control the headphone at all, so in previous versions in Ubuntu you could join the two for adjustment. Also I did notice like nelfer that increasing it a little bit is ear bleedingly loud. Any suggestions?

---

### Post by lidex on 2010-09-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

Also have a look here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---


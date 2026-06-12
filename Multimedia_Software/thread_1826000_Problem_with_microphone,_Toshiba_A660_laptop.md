---
title: "Problem with microphone, Toshiba A660 laptop"
date: 2011-08-16
forum: Multimedia Software
---

### Post by marcogh79 on 2011-08-16
[COLOR=Black]Hi,

I have a Toshiba Satellite A660 laptop with Ubuntu 10.04.
I am sure that the internal microphone works because when I reboot into Windows it works fine. It does not work in Ubuntu instead.
I tried three things that were suggested in other threads of this forum.

1) Action: I checked all the volumes, made sure that the microphone is not muted and selected the proper device as "Analog Stereo Duplex".
Result: no improvements.

2) Action: I installed PulseAudio to better manage the volumes.
Result: no improvements.

3) Action: in the Terminal, I executed the line " [/COLOR][COLOR=Black]sudo gedit /etc/modprobe.d/alsa-base.conf " and then added the line " [/COLOR][COLOR=Black]options snd-hda-intel model=toshiba " at the bottom of the page that opened. I saved, closed and rebooted.
Result: no improvements.

Now, as I know it is useful in order to receive help, I executed in the Terminal the command " [/COLOR][COLOR=Black]wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh " .
The link to where data were uploaded is " [/COLOR][COLOR=Black]_[http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb](http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb)_ " .

Please, does anybody have any other suggestion about what to do?

Thank you.
[/COLOR]

---

### Post by lidex on 2011-08-18
> **marcogh79 said:**
> [COLOR=Black]Hi,

I have a Toshiba Satellite A660 laptop with Ubuntu 10.04.
I am sure that the internal microphone works because when I reboot into Windows it works fine. It does not work in Ubuntu instead.
I tried three things that were suggested in other threads of this forum.

1) Action: I checked all the volumes, made sure that the microphone is not muted and selected the proper device as "Analog Stereo Duplex".
Result: no improvements.

2) Action: I installed PulseAudio to better manage the volumes.
Result: no improvements.

3) Action: in the Terminal, I executed the line " [/COLOR][COLOR=Black]sudo gedit /etc/modprobe.d/alsa-base.conf " and then added the line " [/COLOR][COLOR=Black]options snd-hda-intel model=toshiba " at the bottom of the page that opened. I saved, closed and rebooted.
Result: no improvements.

Now, as I know it is useful in order to receive help, I executed in the Terminal the command " [/COLOR][COLOR=Black]wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh " .
The link to where data were uploaded is " [/COLOR][COLOR=Black]_[http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb](http://www.alsa-project.org/db/?f=f238ca40e3c334cb978dad11a707c92c74497eeb)_ " .

Please, does anybody have any other suggestion about what to do?

Thank you.
[/COLOR]
Is that analog or digital mic? You should change the auto model to:
```
laptop-amic
or
laptop-dmic

```

---

### Post by marcogh79 on 2011-08-23
Hi Lidex,

I tried the codes you suggested me, but I could not made it work.

I solved the problem passing to Ubuntu 11.04 :p. Now everything seems to work fine, even the wireless networks that had disappeared with the 10.04.

Thanks.

---


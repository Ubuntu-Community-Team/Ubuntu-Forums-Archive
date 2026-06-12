---
title: "Multichannel FLAC audio through S/PDIF on Ubuntu with pulseaudio or ..."
date: 2013-04-09
forum: Multimedia Software
---

### Post by play3man on 2013-04-09
Hi. I have an external sound card Sound Blaster X-Fi Surround 5.1, Ubuntu 12.10. I have ripped SACD to .flac files with 176.4khz/24bit and all audio files are in 5.1.

This card supports khz rate and bit depth up to 96khz and 24bit. So.. How I can get:

- when I will play audio in 48khz it will transmit it to the receiver in 48khz and when I will play audio in 96khz and more it will transmit it in 96khz (I can get 96khz when I manualy change settings in /etc/pulse/daemon.conf, but i want it so, it will be changing automatically depending on what I actually playing)
- How I can play .flac multichannel files? I tried change settings in /etc/pulse/daemon.conf but it still shows on receiver only 2 channel PCM.

I can play DTS 5.1, DD 5.1 or Dolby Prologic when I set it in Pulse audio control panel without any (big) troubles. Thanks for the answer.

---

### Post by The Bright Side on 2013-05-29
You won't get that done over S/PDIF. You can only play DD and DTS with optical cables. Any other sound would have to go through analogue.

With analogue, the signal is passed through to your receiver unprocessed. A new problem you may run into then is that it'll sound pretty bad, which is what I'm currently experiencing with my SACD FLACs over the same card, using VLC. I guess it depends on your receiver.

Let me know if this helps, or if you need more info.

---

### Post by play3man on 2013-05-29
In fact S/PDIF is an optical cable. 

In mean time a figuret out of the first problem. I tried some combinations of settings in VLC and when I play music in VLC it's sending to the receiver true sample rate of the music is playing. It is not 100% fix, but it works.. Yes, it would be quite better when this Ubuntu (pulseaudio) could do automatically in any player without any setup.

The second problem. I think thats the real problem is in receiver and optical cable. Receiver will not accept multichannel 96kHz (and more) through optical cable. This and any other HD audio sources in multichannel must be sended to the receiver through HDMI.

---

### Post by The Bright Side on 2013-05-29
> **play3man said:**
> In fact S/PDIF is an optical cable.

Yeah, that's what I was saying. Shoulda made it clearer. The S/PDIF (optical) cables will only give you 5.1 for DD or DTS streams, everything else is stereo or silent (e.g. I tried to play back some DTS-encoded WAV files through VLC back when I was still on optical, and it never worked).

Regarding point 1, you're correct. VLC is the only player I've found so far that will reliably play back all the multichannel sources I feed it. I tried 5.1 and 4.0 FLAC, 5.1 and 4.0 WAV, DTS-encoded WAV, 5.1 OGG, 5.1 WMA, DTS, DD, even MLP, all kinds of resolutions - the whole palette. Never any problem with VLC.

Agree with your conclusion about #2, that's the same thing I found. HDMI will send any-res PCM sound to the receiver just fine (tried and confirmed with my Oppo blu-ray player), but try to find a sound card with HDMI support that actually works in Ubuntu... I haven't been successful so far. If you can get HDMI to work, it will be integrated into your onboard card, or graphics card. It seems Ubuntu does recognize those. Me, I still prefer the analogue connection.

Your receiver (which one is it?) will probably have 6-channel analogue inputs with RCA connectors, like e.g. this here.
[http://www.knowingme.org/6ch-in.jpg](http://www.knowingme.org/6ch-in.jpg)

Our X-Fi Surround 5.1 Pro card has these outputs:
[http://img3.elmir.ua/img/80543/1280/1024/zvukovaya_karta_usb_creative_x-fi_surround_5_1_pro_70sb109500002.jpg](http://img3.elmir.ua/img/80543/1280/1024/zvukovaya_karta_usb_creative_x-fi_surround_5_1_pro_70sb109500002.jpg)

So you'll run a regular stereo RCA cable from the card's "Left"/"Right" outputs to the receiver's Front L/R inputs:
[http://ecx.images-amazon.com/images/I/41BPIZrGaOL.jpg](http://ecx.images-amazon.com/images/I/41BPIZrGaOL.jpg)

The "Rear" and "C/Sub" outputs need the following cable each (it's a 3.5mm stereo to RCA L/R cable):
[http://www.frontx.com/pro/c216_042p2.gif](http://www.frontx.com/pro/c216_042p2.gif)

After you've hooked them up, use Ubuntu's sound settings to test them (you may have to switch the way you connected the C/Sub and Rear cables):
[http://i.stack.imgur.com/lBf4c.png](http://i.stack.imgur.com/lBf4c.png)

Does this help?

---

### Post by The Bright Side on 2013-05-29
One thing you may wanna play around with is pavucontrol (PulseAudio Volume Control). It's in the repositories. An alternate sound settings program that allows you to tinker with a lot of settings for the X-Fi Surround card. For instance, you can regulate every channel's volume independently, including the LFE, and choose from a large variety of sound profiles.

Only negative: at least in 13.04 64-bit, it breaks Ubuntu's own sound settings (they work again after you uninstall pavucontrol, so you're safe).

It may not solve your original problem, but it certainly gives you a whole lot of control over the X-Fi Surround Pro 5.1 and perhaps it gets you a step or two forward.

---

### Post by play3man on 2013-05-29
Thank you for your help. I already tried PulseAudio Volume Control and it works. I have receiver only with optical input (no HDMI). I think that Ubuntu can send from my HDMI output in notebook HD sound with no problem in multichannel. But I can't test it :(. Yes there is one way with analogue multichannel input. But it need lots of cables and I never get true DTS or DD. So I satisfied with only 2ch 96kHz audio at least as yet. And when I ever will have a HDMI receiver I hope it will works great :)

---


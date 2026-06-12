---
title: "Send video to chromecast and audio to soundcard"
date: 2014-11-05
forum: Multimedia Software
---

### Post by gabriel35 on 2014-11-05
Hello all,

Anybody knows how can I do to casting in any of this ways?

[LIST]
[*]Video to chromecast and audio to soundcard
[*]Video and audio to chromecast and audio to soundcard
[/LIST]

I have an M-Audio soundcard connected to a Thonet Vander monitors, so I wish to use them to play the sound.

My TV has no audio output to connect the audio monitors. Anyway I want the original sound from the soundcard, not from the TV's sound system.

System Info:
Ubuntu 12.04 64 bits
Google Chrome [COLOR=#303942][FONT=Ubuntu]Version 38.0.2125.111 (64-bit) with Google Cast extension.[/FONT][/COLOR]

Thanks all.
Gabriel.

---

### Post by papibe on 2014-11-05
Hi gabriel35. Welcome to the forums ):P

You may just need an HDMI splitter (or multiplier). I've read most of them (but not all) work with Chromecast.

For instance: [HDMI Splitter Amplifier 1 In to 2 Out Dual Display]("http://www.amazon.com/CNE86960-HDMI-Splitter-Amplifier-Display/dp/B0015YRMXI/ref=cm_srch_res_rtr_1").

Regards.

---

### Post by gabriel35 on 2014-11-06
Hi papibe, thank you!

I know about HDMI splitters (last day I saw this product: [http://www.ebay.com/itm/HDMI-to-HDMI-SPDIF-RCA-L-R-Audio-Extractor-Converter-/360713631249](http://www.ebay.com/itm/HDMI-to-HDMI-SPDIF-RCA-L-R-Audio-Extractor-Converter-/360713631249)), but I don't want to spend money.

Any free solution? Something like cast only the video signal and send the audio signal through the computer soundcard?

Thanks!

> **papibe said:**
> Hi gabriel35. Welcome to the forums ):P

You may just need an HDMI splitter (or multiplier). I've read most of them (but not all) work with Chromecast.

For instance: [HDMI Splitter Amplifier 1 In to 2 Out Dual Display]("http://www.amazon.com/CNE86960-HDMI-Splitter-Amplifier-Display/dp/B0015YRMXI/ref=cm_srch_res_rtr_1").

Regards.

---

### Post by papibe on 2014-11-06
I can't think of anything concrete....

But if you are casting local content from a computer to the chromecast:

I know VLC can do multicast, .i.e., cast to multiple devices. Also, I read somewhere that they are working on Chromecast support.

There maybe something there, although you would have to do more research.

Regards.

---

### Post by andrew.46 on 2014-11-06
> **papibe said:**
> I know VLC can do multicast, .i.e., cast to multiple devices. Also, I read somewhere that they are working on Chromecast support.



This is available in the development version of vlc under Linux but I don't have a chromecast device to properly test it :(. I attach a screenshot....

---

### Post by gabriel35 on 2014-11-07
Thank you guys, I will test that VLC dev version.

---

### Post by andrew.46 on 2014-11-07
> **gabriel35 said:**
> Thank you guys, I will test that VLC dev version.

There is a guide for the development version of vlc somewhere on these Forums but there are a couple of caveats:

[LIST=1]
[*]It is not for the faint-hearted
[*]It should only be used in a Virtual Machine, it involves the installation of bleeding edge applications and is thus not suitable for a production installation.
[*]
[/LIST]

Otherwise I believe it is a lot of fun :)

---


---
title: "Large Media project"
date: 2015-02-16
forum: Multimedia Software
---

### Post by RadTurtle on 2015-02-16
Hello,

We are currently using Windows XP with Winamp to run our audio in different zones of our park, and for obvious reasons we are trying to switch over to a better solution. The idea was to have 1 computer for each zone "hosting" the music, and then have a computer for each amp broadcasting the music. We are looking for a way to get this done. 99% of the things I have seen are designed for houses. We are on a much larger scale. Our main reason for switching is you can hear the lag in the audio from amp - amp. 

Would anyone be able to point me in the right direction?

---

### Post by Bucky Ball on 2015-02-16
Are you asking if there is a Ubuntu solution?

You will get a lag, depending on the distance you are cabling. You need an amp at the host end to work as a 'relay'. 

Host>amp>computer>amp>speakers might fix your problem. You could use one server to host all the music, but not sure what the specs would have to be. Also a tricky setup as you would then need to feed the server into a series of stereo pairs on a mixer (1/2, 3/4, 5/6 etc.) and be capable of outputting each stereo pair to an amp, then to the appropriate computer at the other end.

Without further details of how you're getting the sound from the host to the client computers, hard to suggest much. Please inform if this has anything to do with Ubuntu. Thanks.

---

### Post by RadTurtle on 2015-02-16
Is there something out there that can grab a stream and control the delay?

---

### Post by Bucky Ball on 2015-02-16
Read my last post, please.

---

### Post by RadTurtle on 2015-02-16
I am not doing anything to my infrastructure. But what I am trying to do is Host>Client>AMP>Speakers

I am wondering if anyone knows of a program, or script that can help with the delay without me spending money buying AMP's that can do this. I am trying to do this using Ubuntu.

---

### Post by Bucky Ball on 2015-02-16
*Thread moved to **Multimedia**.*

You might have more luck here.

---

### Post by tgalati4 on 2015-02-16
You can use *sox* to add a delay and send that to another device such as /dev/audio2.  Point your sound card to use /dev/audio2 for playback.

The basic issue is that TCP/IP protocol is not syncronous.  Packets get sent and can take their sweet time getting to their destination.  This will result in audio delay and noticeable "phasing" in the sound quality.  The delays you set using *sox* would be based on the distance from "ground zero" of your sound system to your distant speakers.  Then you would add a few milliseconds of delay to account for network delays.  But network delays will be constantly changing depending on network traffic.  Because the speed of sound is about 1100 feet/sec, a 2 millisecond delay is about 2 feet of distance.   Phasing is noticeable at around 20 ms and echos are apparent at 40 ms or greater.  Ping your remote computers to see what the network delays are.

The professional solution is to use Cobranet or QLAN, an ethernet-like protocol that contains a syncronized clock signal--and the expensive equipment that can decode and play these protocols.

To reduce the delay problem, consolidate your speakers into a massive cluster at ground zero, raise them as high as possible and point them down to cover the park in a 360 degree fashion.  Use arrays or beam-controlled speakers to get even coverage in both near-field and far field.

An alternative strategy is to put your subwoofers in the center of the park at ground level and point them in a 360 degree pattern.  Then use your mid-range speakers in a ring around the park at a fixed radius.  This allows you to use one delay for the ring (with minor tweaking to account for network delays).  Use a second ring (or arc) to get the outlying areas of the park with a second delay setting.  With this arrangement, all you care about is getting the bass beat to match the beat of the mid-range speakers.  Make sure the midrange speakers don't overlap in coverage so you can't hear "phasing" between zones.

Be aware that accoustic delays will vary with temperature and humidity, so daytime delays will be different from nighttime delays.

---


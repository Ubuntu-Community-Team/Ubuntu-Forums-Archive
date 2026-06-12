---
title: "“FItSs” when starting a MythTV prgm w/ Digital Audio Track"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by jboehm on 2007-05-02
Hi,

I followed the standard mythtv wiki how to for this.
[http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound)

My default is mixed-digital.  Myth is set to pass thru to default. 

All was well under Ubuntu Edgy but after upgrading to Feisty Fawn I get a “buffer fill” noise the first time I start a program with a Digital Audio Track. It also happens if my last recording had Prologic Audio and my new program has Dolby Digital audio.

I’m guessing when I named it a “buffer fill” noise.  It sound like “FFFiTs.”  It last about a 1/2 second then the audio track continues normally.  This is the same behavior I got when I was first configuring digital audio and was playing with `ALSA:spdif`.

Thoughts,
Jon

PS. On the positive side DTS pass thru works under Feisty.  It never worked under Edgy.

---

### Post by jboehm on 2007-05-07
Here is the reply I received from the ALSA mailing list.  Don't know what to
do with it but its another data point.

---------------
You're probably hearing Dolby Digital data being played as though it
were raw PCM data.  This can happen if the wrong control bytes are set
on the IEC958 interface, or if part of the AC3 stream that tells the
decoder what kind of stream it is receiving is never sent.  I'm not
sure what else can cause the problem; I have the same problem
sometimes after seeking in xine, with an emu10k1.  Since it looks like
you are using dmix as well, dmix might be interfering with the
transition from PCM to AC3.

On 5/4/07, Jon  wrote:
> Hi,
>
> Config:
> Ubuntu Feisty Fawn (server) upgraded from Edgy
> using SPDIF connection onboard GA-965P-S3 ALC883
> asound.conf configured with this how to [http://mythtv.org/wiki/](http://mythtv.org/wiki/)
> index.php/Configuring_Digital_Sound
>    where Alsa:default = dmix-digital
>
> Using mythtv, when i switch from a prologic recording to a Dolby
> Digital recording I get a 1/2 second of LOAD, speaker popping,
> distortion then the audio track plays normally.  I sound kind'a like
> "FFiSTT"
>
> I'm new to this but I'm guessing this might be bad data while the
> buffer fills the first time??  It does not happen with two back to
> back DD tracks.
>
> Another data point, under Edgy, I saw similar behavior when I
> directly used ALSA:SPDIF.  The problem went away when I used the
> above asound.conf.  Not so lucky under Feisty.  :-(
>
> Thanks for the help,
> Jon

---


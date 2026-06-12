---
title: "DTSHD and TrueHD as Multichannel PCM asound.conf"
date: 2010-08-24
forum: Multimedia Software
---

### Post by odin89 on 2010-08-24
Hello,
I have a Onkyo Tx-sr 308 and a ATI HD4350 Graphic Card.
They are connected with HDMI.
Is it possible to play Dolby Truehd and DTS-HD as "Multichannel PCM"?
With Windows it is no Problem but with Linux my Receiver only get 2 Channel if i play a Truehd or DTS-HD File.
Is there someone who can help me?
Normal DTS and DD works with 6 Channels.

odin89

---

### Post by The Flying Penguin on 2010-09-09
I would like to see this guys question answered as I have great interest in it.

From my understanding there is no way to bitstream or send out PCM in Linux when it comes to DTS-HD or True-HD because of this whole protected audio path deal. I'm guessing what is happening when you try to playback HD audio, is that the DD stereo track is being selected by whatever program your using. What program are you using?

But [http://www.mythtv.org/wiki/High_Definition_Disk_Formats](http://www.mythtv.org/wiki/High_Definition_Disk_Formats) claims they are supported under Myth. Scroll down to "Playing Hi-Definition Material". I know that contradicts what I just told you and everything I have read. I'm guessing that just means it can play it but not necessarily output it via HDMI and is surely down sampled.

Perhaps you can try it out and let me know? I'm still saving up for a Pioneer VSX-1120-K so I am unable to test any of this out since my old receiver only has optical and coax inputs.

Even in Windows, HD audio is down sampled. The only way to get perfect HD sound is using a card like the Asus&#8217; Xonar HDAV 1.3 which provides a protected audio path for the audio. I may be wrong though, I don't follow things in the Windows world too close anymore ;)

And btw, I have the same ATI card as you. I bought it when my HTPC was running Windows. Now I use a Nvidia G210 for the vdpau in Ubuntu. The ATI just sits on the shelf.


EDIT:
Ok, I've been doing some more research on this. FFMPEG is now capable of decoding TrueHD. DTS-HD is still a not working. You will just use the DTS core. As a workaround, you can convert the DTS-HD to FLAC and send it out over multichannel PCM. TrueHD should decode and output via PCM. XBMC and MPlayer both use FFMPEG.

I think the reason DD and DTS work fine for you is because you are bitstreaming those to your receiver. You cannot bitstream HD audio in Linux yet (if ever). I'm guessing whatever program you are using is reverting to DD 2 channel or it is trying to send out the TrueHD by way of PCM but you have your channels muted. Run Alsamixer and unmute all your channels so PCM will work.

To even get any kind of audio working over G210's hdmi, I had to compile Alsa 1.0.23. Perhaps that would be a step in the right direction for you. Check Alsamixer first though.

That's the best guess I have.

---


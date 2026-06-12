---
title: "SPDIF worked, now dead"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by doloctona on 2006-06-03
Ok.. I just installed Ubuntu yesterday and was completely amazed to get proper output through SPDIF (coax) to my amplifier..  Anyway, after some amount of time I did the dumbest thing possible and opened up the sound mixer thing (from the speaker in the system tray)..

I went to playback, added Digital-1 to the controls and then clicked it.. my MP3 stopped playing immediately (at least, it kept playing but no sound came out of the speakers).. I tried to play a movie in Totem (which DID work before with SPDIF sound output), and had the same issue.. it played the movie without problems but no sound came through the SPDIF.

I have messed endlessly with the alsamix console tool, as well as the GUI one, the desktop mixer and all kinds of stuff.. no luck.

I guess the only thing that would work would be 

1) Re-install.. no biggie but I'd prefer to know how to fix this properly without a re-install every time

2) Re-install the alsa, OSS and ESD sound libraries etc. to restore the working 'astate' file, or whatever other config file has been messed up.. this would be better..

3) If anyone with an ALC850 has had this exact issue.. what solution did you come up with?  It's an onboard card on the Asus A8V Deluxe.


Thanks in advance..

James

---

### Post by doloctona on 2006-06-03
Ok.. Don't ask me how exactly, but with a lot more fiddling just with the basic "Volume Control" program (accessed via System tray), I managed to convince it to do IEC958 playback again...

Now to backup my astate and never, EVER mess with the volume controls again :)

---

### Post by deodatus on 2006-06-04
I found something like this on a Fedora forum.
Open terminal:
#*sudo alsaconf*
follow instructions, then:
#*sudo gst-register-0.8* 
This registers all the GStreamer plug-ins among other things I don't know of.
*reboot*.  It wouldn't work until I rebooted.

---

### Post by Osamabingandhi on 2006-06-05
you write this in some of the posts i am looking at....sudo alsaconf. I am trying to get my spdif work for more sources than dolby digital ones, mp3's and such.

This alsaconf don't work for me. Is there an application that i need to install first? I have tried to find a program that i can adjust some sound settings for my card but haven't found any. I am trying to get sound to work, don't like to log into windows xp everytime i want to listen to music.....don't like microsoft, but like music:)

---

### Post by martinielsen on 2006-07-18
Hi!

I wonder how you got the S/PDIF to work in the first place? I also have the Asus A8V Deluxe and have just installed Dapper Drake 6.06, and my S/PDIF will not make a sound. If i boot to Windows XP everything works fine. I spent many hours searching Google for a solution, with no luck. Like you i messed endlessly with the alsamix console tool and the sound mixer from the system tray and tried to get some sound from the "IEC859" (S/PDIF?) device. But not matter what i do i can't get any sound out. I'm not sure that the CD player that came with Ubuntu (Sound Juicer) supports S/PDIF, but at least system sounds should work on S/PDIF shouldn't it? In the Volume Control Preferences there are 4 different IEC859 devices: "IEC859", "IEC859 Output" and "IEC859 Playback AC97-SPSA"x2. Very strange that the "IEC859 Playback AC97-SPSA" is a mono channel :confused: 

Can you help me out here? I'm desperate ](*,) 

Martin

---

### Post by krazyd on 2006-07-19
sudo alsamixer

unmute the IECxx and I have spdif! So simple!! :D
Thanks for the tips here guys

---

### Post by climbing18away on 2006-09-05
I think i have that same card, i bought it a while ago and threw out the box and no longer know what it is, but it has the spdif in and out, and it's never worked for me, i'm just trying to use my computer as a dvd/movie player (media center) but without the spdif working i might have to install windows for it to work...anyone know of a real fix?

---


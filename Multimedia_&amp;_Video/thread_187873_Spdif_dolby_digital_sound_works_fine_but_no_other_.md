---
title: "Spdif dolby digital sound works fine but no other sound"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by Osamabingandhi on 2006-06-03
I installed all wiki restricted formats and then in totem i changed the sound setting for AC3 pass through. But after that i cannot listen to anything else than dolby digital sources. No Mp3 or avi files...I have tried to change the setting in totem player back to stereo but it doesn't help.](*,) 

Anyone with a similar problem but managed to fix it? I have an old (5 years) Sound blaster Live! with spdif output.

Would be really nice if someone could help me :)

P.S. same problem as this post: [http://www.ubuntuforums.org/showthread.php?t=168893&highlight=dolby+digital+sound](http://www.ubuntuforums.org/showthread.php?t=168893&highlight=dolby+digital+sound) D.S.

---

### Post by Osamabingandhi on 2006-06-08
I think i may have come up with a solution to my problem. I have not tried this yet so it may or may not be the solution. When i had just installed ubuntu sound worked through the spdif plug with PCM with no problem until i used totem player and enabled AC3 pass through, and therefore dolby digital works too. The conclusion is that totem player is the devil :twisted: and corrupted my soundsettings...

To play two sources that compete over the spdif plug may corrupt things, or as i have come to believe that it is the totem player. To use totem player and activate this AC3 pass through to get dolby digital may be the problem. I will make a fresh install and uninstall totem player and install xing-player or/and myth-end. I liked the zoom thingy in totem player, but i guess that function is in other programs. I hope i can make a fresh install today...and see i my faith in the devil proves right :)

---

### Post by homek on 2006-06-19
Have you solved this problem? I just lost my PCM playing capability through spdif.

---

### Post by Osamabingandhi on 2006-06-22
sorry no...i am going to make a new installation of ubuntu and not use the ubuntu movieplayer totem. Instead I plan to use xine player and hopefully that program can use the spdif without destroying pcm-sounds(mp3 and all other sound than dolby digital). If you feel like fixing your pcm sound i have no answear exept to reinstall and  not to change any sound settings like ac3 sound spdif in any program exept xine...But also know that i am not sure this will work either. I will tell you as soon as i try my reinstall and know if it works or not, hopefully this weekend.

---

### Post by Osamabingandhi on 2006-10-30
I fixed it by not enabling pass through in totem-player, that was what messed up my sound. I only use xine movie player and turn on spdif in the program, i think it worked in vlc also. I use edgy edge now by the way.

---

### Post by bobo1on1 on 2006-11-18
I frequently have the same problem, the spdif output goes to dolby digital and doesn't want to turn back to pcm.

Whenever this happens I use the following command:

cat /dev/urandom | ac3dec -R

Because of the -R option ac3dec sets the spdif output to pcm and because of the random data it receives ac3dec will segfault, the output stays at pcm if you're lucky, if not try repeating the process.
Another option is to cat an avi file that has an ac3 stream.
Afther that I need to turn off the IEC958 Optical Raw option off in the mixer.

You have to do sudo apt-get install alsa-tools first to install ac3dec.

---

### Post by ict on 2007-01-09
Sorry for pushing this old thread. I'm experiencing the same problem right now. I tried setting xine to pass-through, which worked, but now no PCM sound is transferred via SPDIF.
I found varios forum postings in the Ubuntu Forums, but no solution.
Please help me!

thanks
ict

---

### Post by smarf on 2007-11-25
*bump*

Hi there, I have exactly the same problem. Most of the times, I can re-enable PCM output to SPDIF with the already posted
  cat /dev/urandom | ac3dec -R
but hopefully there is a better way of setting SPDIF back to PCM.

Anyone with a _real_ solution to this problem? Thanks in advance!

Using XUbuntu Gutsy with intel-hda-driver.

---

### Post by iggee85 on 2007-12-01
Wow, this is a really roundabout way to fix a simple problem.

I got SPDIF working on my ALC883 soundcard and PCM and AC3 was outputting perfectly. Then Totem crashed once and I lost PCM sound. To get it fixed, I did what bobo suggested although I used an AC3 .avi file since urandom didn't work.

But yeah, to echo smarf, is there another (right) way to restore PCM sound?

---

### Post by CarloMagno on 2008-01-31
Just to add my experience,

I have a similar problem in my frontend, whenever I play a movie encoded in DD (AC3) the sound through the spdif is perfect, no complaints from my amplifier, but after that, if I try to play another movie, be the audio encoded in mp3 or AC3, there is no sound and the icon in the amplifier that identifies the type of the signal is blank...No sound in any player (mplayer, gxine, totem, system sounds..). I am using Gutsy x64 in an AMD64 with Realtek 889 sound chip in the motherboard (Gigabyte GA-MA69-S2H), optical spdif out to amplifier.

I don't exactly comprehend what the command bobo1 suggested does, but it works, I have to execute the comand
 cat /dev/urandom | ac3dec -R

until I get at least one execution with the message ** CRC failed - skipping frame ** and after that the sound returns.

Thanks bobo1 for the roundabout solution.

---


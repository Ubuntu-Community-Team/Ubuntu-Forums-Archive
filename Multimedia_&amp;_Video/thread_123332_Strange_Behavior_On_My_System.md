---
title: "Strange Behavior On My System"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by short4lif2 on 2006-01-29
On my computer, I have an integrated sound card.  My motherboard is an Asus P4S800, with a SiS648FX SiS 963L chipset and the sound is ADI AD1980 6-channel audio CODEC S/PDIF out interface.  The sound works pretty much perfectly fine, but if, let's say, amarok is playing music, and I try to use any other sound program like XMMS or skype, amarok is the only program that can use the sound and the other programs are silent.  Similarly, if Skype is open, and I have just finished a call, and i try to play music in Amarok it says that there is an error.  What I do is close skype, reopen amarok, start the music and open skype again.  That works but then the problem reverses, skype can not access the sound card.  Now, on windows, with properly configured sound, many different programs can access the sound card at once, and I am sure that there is a way to configure Kubuntu the same way.  Does anyone know how?  I tried looking for an ALSA driver but I could not find one.

---

### Post by dickohead on 2006-01-29
There are threads around on using multiple sound sources, i had the same issue, you need to do some config file editing and it fixes it right up! Just do a search for "multiple sounds" or similar.

---

### Post by Sutekh on 2006-01-29
Try these HOWTOs/Threads

[Ubuntu Forums - howto multiple sounds at once]("http://www.ubuntuforums.org/showthread.php?t=101125")

[Ubuntu Forums - Have an audigy? Want multiple sounds without ESD? Do this!]("http://www.ubuntuforums.org/showthread.php?t=104388")

[Ubuntu Forums - Happy ALSA, OSS, ESD, with Duplex - Sound Settings]("http://ubuntuforums.org/showthread.php?t=44753") - (check last pages for relevance to Ubuntu 5.10)

---


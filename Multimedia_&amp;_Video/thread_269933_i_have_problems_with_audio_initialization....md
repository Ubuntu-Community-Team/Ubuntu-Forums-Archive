---
title: "i have problems with audio initialization..."
date: 2006-10-02
forum: Multimedia &amp; Video
---

### Post by DeathLord on 2006-10-02
Hello , as you may see i'm new here .. i installed ubuntu 2 days ago and with great help from my friends ..i understand few commands and the way that linux system operates.. 
I have problems with my sound card initialization .. In the beginning i didn't know what the heck is wrong .. but now i maybe locate the problem .. 
--
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
--
I saw the "comprehensive... /for audio setup" but something always goes wrong..
with two words let's say .. i can't play any audio file on my system .. 
i've tried everything that i found about the issue
Can you help me to dig my sound up .. ?


Thanx in advance, and sorry for my english !

---

### Post by DeathLord on 2006-10-02
ok i have new information ... 
in general .. i have two sound cards .. first is onboard and i had disabled it from bios ..
the second is .. creative labs 24live .. sound blaster audigy ls or (ca0106)
i found one guide how to install a drivers but now .. i dont have even a drivers for the card.. when i click on the sound control icon .. it gives me 
this message "No volume control GStreamer plugins and/or devices found."
i think i have Gstremer plugins ... 
well as far as i'm concerned .. prior to this moment .. alsamixer detects my onboard card and i read from the "comprehensive guide how to change the cards priority or smtn'" i dont know what i have done but now i dont have anything .. 
xine glithces .. mp3 support as well  nothing damn :(
"alsamixer: function snd_ctl_open failed for default: No such device"
"xine was unable to initialize any audio drivers."

---

### Post by baloo56 on 2006-10-03
> **DeathLord said:**
> ok i have new information ... 
in general .. i have two sound cards .. first is onboard and i had disabled it from bios ..
the second is .. creative labs 24live .. sound blaster audigy ls or (ca0106)
i found one guide how to install a drivers but now .. i dont have even a drivers for the card.. when i click on the sound control icon .. it gives me 
this message "No volume control GStreamer plugins and/or devices found."
i think i have Gstremer plugins ... 
well as far as i'm concerned .. prior to this moment .. alsamixer detects my onboard card and i read from the "comprehensive guide how to change the cards priority or smtn'" i dont know what i have done but now i dont have anything .. 
xine glithces .. mp3 support as well  nothing damn :(
"alsamixer: function snd_ctl_open failed for default: No such device"
"xine was unable to initialize any audio drivers."
My computer has the same audio hardware as you have in yours. Unfortunately, I have never been able to get it to work under Linux (previous to Ubuntu Dapper I was using Suse 10.1). When I installed Ubuntu last week (very pleased with it so far) I could only get sound from the front left speaker in a 5.1 surround speaker setup. Card was recognized and the correct driver (CA0106) was installed. I played with the alsamixer settings but nothing gave me sound out of anymore than the FL speaker. I hope someone can suggest a work around. 
lspci | grep audio gives:
0000:04:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
lsmod | grep snd gives:
snd_ca0106             34212  3
snd_rawmidi            25504  1 snd_ca0106
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93216  1 snd_ca0106
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  12 snd_ca0106,snd_rawmidi,snd_seq_device,snd_ac97_ codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_ac97_bus            2304  1 snd_ac97_codec
snd_page_alloc         10632  2 snd_ca0106,snd_pcm

---

### Post by baloo56 on 2006-10-04
Problem Solved. One of the things that attracted me to Ubuntu and Linux in general with the great help Forums. If you have a problem chances are somebody else has experienced the same problem and been kind enough to document & post it. My Creative Labs 24 live .. Sound Blaster audigy ls and 5.1 surround sound problem was solved by following the posting at:
[http://www.ubuntuforums.org/showthread.php?t=184814](http://www.ubuntuforums.org/showthread.php?t=184814) (Hope it helps solve your problem).

---


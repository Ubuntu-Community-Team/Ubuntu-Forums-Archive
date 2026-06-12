---
title: "Skype 64-bit - Mic volume and video"
date: 2009-07-31
forum: Multimedia Software
---

### Post by pezonik on 2009-07-31
I've just installed Skype using skype-static-oss_2.0.0.72-0medibuntu4_amd64. The problem is that the mic volume is too low. They can barely hear me. I recorded something using the Sound recorder and the volume is also very low.

There's another problem. When I start my camera I can't see myself. The other people can see me well enough, but I can't.

Thanks.

---

### Post by igorzwx on 2009-07-31
"I've just installed Skype using skype-static-oss_2.0.0.72-0medibuntu4_amd64"

I also have skype-static-oss installed,
and it works well for me.
The only difference is, perhaps, that I have another
sound system.

I have Ubuntu 9.04 with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

If you have not OSS4, you may better try another Skype
from the same Medibuntu.

If you want to compare different sound systems, 
you may try to install OSS4.
This make sense **only if** your hardware is supported by OSS4

**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 

If your soundcard is in the list of supported hardware, you may
install another Ubuntu 9.04 in dual boot
and make experiments there following this instruction:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

You may also read this:

[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

[LIST]
[*][Open Sound System - Home page]("http://www.opensound.com/")
[*][Building the Open Sound System From Source]("http://www.4front-tech.com/wiki/index.php/Building_OSSv4_from_source")
[*][Sorry State of Sound in Linux]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html")
[*][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")
[*][OSS is dead. Long live OSS!]("http://4front-tech.com/hannublog/?p=5")
[/LIST]

---

### Post by pezonik on 2009-08-01
igorzwx:
I installed OSS4 using the OpenSoung guide. The sound is OK, but now the mic is dead. And the nice African intro disappeared.
I found this thread
[http://www.4front-tech.com/forum/viewtopic.php?t=3250&highlight=capture](http://www.4front-tech.com/forum/viewtopic.php?t=3250&highlight=capture)
but I don't understand the solution.
Thanks

---

### Post by Arup on 2009-08-01
OSS4 works quite well for me, I was having low mic issues as well with ALSA and my Yamaha sound card. With OSS, you need the Skype OSS version installed and it works fine with my cam and mic.

---

### Post by adamitj on 2009-08-01
Try this:```
$ alsamixer -D hw:0
```and high all volume levels.

For mobo's with front jack panels, Skype just can't identify the right volume levels. Also try to change your skype sound settings to find your right device.

---

### Post by pezonik on 2009-08-01
adamitj:
Is that for the terminal? I dont' get it, sorry.

And, another problem: I don't get any sound from YouTube anymore.

Should I go back to ALSA?

---

### Post by adamitj on 2009-08-02
> **pezonik said:**
> adamitj:
Is that for the terminal? I dont' get it, sorry.

And, another problem: I don't get any sound from YouTube anymore.

Should I go back to ALSA?

Sure, all command lines must be typed in terminal.

It seems that your OSS installation doesn't work successfully. Go back to ALSA and try to high your volume levels. As I said before, just use ALSA and try to change your default sound device inside Skype (as shown in the attached picture).

---

### Post by pezonik on 2009-08-02
Thanks adamitj.
I reinstalled ALSA. The African welcome sound and YouTube are working fine. I'm sorry about the terminal question, I was distracted by the $ sign and I tried it while I had OSS installed.
According to alsamixer the mic level is 100. It should be working fine, but the volume is still low. There's an option called "Mic boost" but I don' know how to turn it on. On top of that, Skype doesn't give me many options for the sound devices, just "/dev/dsp".
Should I try something like PulseAudio? I don't know much about it.

---

### Post by pezonik on 2009-08-02
I checked the "MIc boost" option and the sound is loud enough. Thanks for everything.
I still wonder about PulseAudio. Any suggestion?
I still have one of the problems I started with. I can't see myself with my camera.

---

### Post by igorzwx on 2009-08-02
Perhaps, it is too late to answer your question, because OSS4 is already deinstalled.

You may try to install two Ubuntu 9.04 in dual boot,
one with ALSA, another with OSS4 and try them out.
One of them may work, perhaps.

---

### Post by igorzwx on 2009-08-02
Hi Arup!

"With OSS, you need the Skype OSS version installed"

Try Ekiga too.
Fantastic performace!

---

### Post by adamitj on 2009-08-03
> **igorzwx said:**
> Perhaps, it is too late to answer your question, because OSS4 is already deinstalled.

You may try to install two Ubuntu 9.04 in dual boot,
one with ALSA, another with OSS4 and try them out.
One of them may work, perhaps.

I didn't suggest OSS because all the times I had problems with Skype (6 or 7 times in different computers) it wasn't ALSA incompatibility. It was just the wrong device driver selected in Skype sound settings or the sound volume. Moreover, if the sound is working outside Skype, ALSA is working fine.

I still thinking it's device misconfiguration. Did you tried to change your device in Skype sound settings? How many hardware drivers you are able to see there? You can change them and click on button "Make a test call" to validate your combinations.

HINT: I never was able to use Skype with default devices, so I think you should consider change them.

---

### Post by igorzwx on 2009-08-03
Hi [adamitj]("http://ubuntuforums.org/member.php?u=466453") !

I did not understand a word in your message.

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by adamitj on 2009-08-04
> **igorzwx said:**
> Hi [adamitj]("http://ubuntuforums.org/member.php?u=466453") !

I did not understand a word in your message.

[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

Why? Is my english so bad?
Now I can't understand you...

---

### Post by bluestix on 2009-08-31
I got 64Bit Skype working on 9.04 with an X-Fi card using the Creative Beta driver:


[http://ubuntuforums.org/showpost.php?p=7878068&postcount=3]("http://ubuntuforums.org/showpost.php?p=7878068&postcount=3")

---


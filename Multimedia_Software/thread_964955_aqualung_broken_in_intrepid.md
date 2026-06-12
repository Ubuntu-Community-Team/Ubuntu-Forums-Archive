---
title: "aqualung broken in intrepid"
date: 2008-10-31
forum: Multimedia Software
---

### Post by joris1977 on 2008-10-31
Hi,

Since I upgraded to Intrepid my favorite musicplayer: aqualung isn't working properly anymore. When i start the player, i get this output:

joris@ace:~$ aqualung
No output driver specified, probing for a usable driver.
Probing JACK driver... JACK server not found
Probing ALSA driver... OK
XML document of the wrong type

Aqualung doesn't crash, but it takes a long time to react when i click on the next song buton. Even hitting the stop button takes 10 seconds to stop playing. Also the timer behaves strange.

Are other people having the same issue? 
And does somebody have a fix?  

I liked aqualung a lot for it's easy to use playlists and the gapless  playback.

I already made a bugreport about this issue. You can find it here: [https://bugs.launchpad.net/ubuntu/+source/aqualung/+bug/288334/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/aqualung/+bug/288334/+viewstatus)

---

### Post by sandrokottos on 2008-11-01
Same here. This is so for the one from Intrepid or self compiled from the latest SVN (and this worked fine on Hardy).
I have a different fault, it won't save any settings to its .aqualung folder - and yes I have looked at the permissions, and have deleted the folder allowing it to be recreated. It will play but the ladspa plugins won't work - well not all of them - no sound. When I compile either the current SVN or the same beta that's in Intrepid there are lots of warnings about buffer overflows being certain in what look like file write functions. If I run it from a terminal it indicates overflows when it exits (I assume trying to save its settings). If I go into settings in Aqualung it crashes immediately when I come ot of settings, nvitinng me to recompile with debug on so that the source of the crash can be found. Thinking of posting on the aqualung mail list.

Sandro

---

### Post by sandrokottos on 2008-11-01
Well,

Compiling with debug on gives a program that behaves itself. Plugins work and it saves the configuration OK. Compile with debug off and it crashes with buffer overflows.

I've posted the results to the aqualung mailing list. Now running the latest svn with debug on.
-- 
Sandro

---

### Post by joris1977 on 2008-11-01
Thanks for your reply sandrokottos. I am not sure that your issue is the same as mine. 

I never compiled aqualung, maybe i will give it a try, but it doesn't look like a very easy program to compile. 

If you get a fix from the aqualung mailist than it would be real great if you would share it here in the forum.

---

### Post by T86 on 2008-11-03
I fixed problem with Aqualung by installing ubuntustudio-audio-plugins and ubuntustudio-audio from synaptic package manager (I didn't change output - Alsa @ 44100 Hz). It works also with oss before instaling these packages, but I couldn't set it as default output.

---

### Post by T86 on 2008-11-03
Sorry, false alarm, after restart it returned to same condition.

---

### Post by sandrokottos on 2008-11-04
I have been in touch with the developers. My problem seems to relate to buffer overflow in font storage, that only appears if aqualung is compiled with optimisation - hence it's OK in debug. I have been given two patches to try to debug the problem and I have emailed the results of applying them. I will post any more news when I have it.

-- 
sandrokottos

---

### Post by T86 on 2008-11-07
It works with Jack:guitar:

---

### Post by joris1977 on 2008-11-10
I got rid of the "XML document of the wrong type" message by deleting the .aqualung file, but this doesn't solve the issues i am having with aqualung. 

I will update the bug report. Hopefully the patches sandrokottos got will work for him and maybe they will solve my problems as well...

---

### Post by lastchancetosee on 2008-11-16
For the record: I have the same problem that sandrokottos described.

---

### Post by sandrokottos on 2008-12-10
A fix. The latest svn version R-1040 has the buffer overflow fixed. I'm afraid it's a download and roll your own though - no binaries. The aqualung page shows all the litrabries you need - it's quite straightforward. I build my own deb with checkinstall,

-- 
Sandro

---


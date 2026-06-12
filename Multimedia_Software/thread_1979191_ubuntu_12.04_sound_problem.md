---
title: "ubuntu 12.04 sound problem"
date: 2012-05-12
forum: Multimedia Software
---

### Post by adityeah on 2012-05-12
Hi, 

I am using an intel DG31PR motherboard that has realtek audio. Ever since I have installed Ubuntu 12, the audio is not working right. I hear the sound (from the speaker) but its mostly absent. Basically there is a lot of stuttering/choppiness. If I use a headphone, it works fine. 

I have my alsa diagnostic tool output up at: [http://www.alsa-project.org/db/?f=ba499573f672309636489535508a9446c277a2a3](http://www.alsa-project.org/db/?f=ba499573f672309636489535508a9446c277a2a3)

I have tried all I could but nothings working for me. I must mention that before this I was using xubuntu 11 which worked just fine (I never updated it because I found that one of the updates to xubuntu 11 caused the same problem that I am facing now).

Any help would be appreciated. I would be forced to look back at other options if this does not get solved soon. 

Thanks!

Aditya

---

### Post by adityeah on 2012-05-13
Really, is there no one who can help me with this? Please?

---

### Post by adityeah on 2012-05-14
Since no one replied I started snooping around myself. Till now what I have found is that the alsa output thinks that I have a Realtek ALC662 but in reality what Intel DG31PR comes with is  ALC888. So that might be a problem, I am guessing.

Right now I do not have access to my system but soon I will and will try and see a fix for that. Will update it here.

---

### Post by sirriffsalot on 2012-05-14
Hey mate!

Since your headphones are working fine I would guess it is rather a problem with the way the sound is going to your speakers, obviously.. I am probably stating the obvious, but have you played around with different mixers (e.g. gnome alsa mixer, alsamixer in terminal [command: # alsamixer] etc) to see if that sorts things out?

---

### Post by adityeah on 2012-05-14
ah, we have a reply at last.

Yes, I did some tweakings with alsamixer (only alsamixer, nothing else) and did not help.

The sound from the speaker is MOSTLY absent and when I hear some, for those microseconds that its there, its choppy. 

Any help or thoughts appreciated!

---

### Post by mörgæs on 2012-05-14
Moved to the multimedia forum.

---

### Post by fat yak on 2012-05-14
Have you looked in the software centre for a different sound system to try? or uninstall what you currently have and reinstall it??

---

### Post by adityeah on 2012-05-14
Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic

That was all. I think I had tried it earlier too but somehow it was not working. Maybe I had tried too much.

But I think the problem was indeed that it was trying to use the  ALC888 as ALC662 and that was not happening.

Thanks for the responses. Now I can stick to Ubuntu and try to get friendly with Unity

---

### Post by mattgeb84 on 2012-06-17
how the heck do you add that line to the end of that file

---

### Post by mörgæs on 2012-06-18
If you tell exactly what you tried and the problems you encountered it would be easier for people to help you.

---

### Post by flemur13013 on 2012-06-21
> added this line at the end of /etc/modprobe.d/alsa-base.conf:
options snd-hda-intel model=genericI was going to say "that worked for me!" then I got a brief sound glitch when I hit the "Reply" button....your solution seems to have improved things at least.

Anyway, sound was working fine until a 12.04 update....now to research how to install the original (CD) OS software without a complete reinstall.

Edit: I had the nVidia video drivers disabled for playing with (messed-up) flash; re-enabling them seems to have fixed the sound glitch; I left the above line in the alsa-base.conf file...

---

### Post by HarounChildericEggeberth on 2012-06-22
Thanks for your work adityeah! This edit solved a similar problem I had with audio choppiness coming from a built-in Intel soundcard.

@mattgeb84: to edit the alsa-base.conf file, go to Terminal and type:

gksudo gedit  /etc/modprobe.d/alsa-base.conf

This opens an editor that will let you edit the file (even though it is read-only). Add the line to the very end of the file and save your changes. I had to restart my computer for the edit to take effect. Remember to undo the change if it fails or has no effect!

---

### Post by Erdnalex on 2012-07-06
I had the same problem and this fixed it for me, thanks !

---

### Post by rooski15 on 2012-07-06
Fixed my sound! Thank you!
However, and on a totally unrelated note, my sound in virtualbox still has the same problem that my entire system had before the fix. Hmm.

---

### Post by mechsin on 2012-07-21
> **adityeah said:**
> Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic

That was all. I think I had tried it earlier too but somehow it was not working. Maybe I had tried too much.

But I think the problem was indeed that it was trying to use the  ALC888 as ALC662 and that was not happening.

Thanks for the responses. Now I can stick to Ubuntu and try to get friendly with Unity

I second this solution although my problem was not as sever as having no sound. My music would just skip/stutter at random intervals. I added the line to the alas-base.conf rebooted and everything seems to work fine now. At least after 30 minutes of testing. :D 
I have a Asus P6T Deluxe V2 motherboard.

---

### Post by era506 on 2012-07-28
> **adityeah said:**
> Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic

That was all. I think I had tried it earlier too but somehow it was not working. Maybe I had tried too much.

But I think the problem was indeed that it was trying to use the  ALC888 as ALC662 and that was not happening.

Thanks for the responses. Now I can stick to Ubuntu and try to get friendly with Unity

THANK YOU! This was driving me crazy! Sound doesn't skip now and I didn't even have to reboot! Just edit the file and play something :D

P.D. I have an Intel DZ77GA-70K motherboard, I know the sound is Realtek but no idea which model :confused: Anyway, it works now :D

---

### Post by DareBear666 on 2012-08-14
Hi Adityeah,

Thanks so much! +1

This had been bothering me for 3 months or so and I had not sat down to resolve it seriously. Today I got ready to invest some time on it but this fix worked right away. Again, thanks!

> **adityeah said:**
> Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic

That was all. I think I had tried it earlier too but somehow it was not working. Maybe I had tried too much.

But I think the problem was indeed that it was trying to use the  ALC888 as ALC662 and that was not happening.

Thanks for the responses. Now I can stick to Ubuntu and try to get friendly with Unity

---

### Post by anto27373 on 2012-08-19
thanks, adding that line fixed my infrequent stuttering sound problem as well !!

---

### Post by era506 on 2012-09-01
> **era506 said:**
> THANK YOU! This was driving me crazy! Sound doesn't skip now and I didn't even have to reboot! Just edit the file and play something :D

P.D. I have an Intel DZ77GA-70K motherboard, I know the sound is Realtek but no idea which model :confused: Anyway, it works now :D


Well this worked until I tried my headphones and I got sound on both, headphones and speakers...
I remembered that I saw an update a while ago that said something about Intel HDA sound so I removed that line from /etc/modprobe.d/alsa-base.conf and so far sound doesn't skip and plugging in my headphones "mutes" the speakers as expected :)

EDIT: it seems I jumped into conclusions too quickly... I'm still getting skipped sound from time to time... I'll guess I'll just turn the speakers off while my headphones are plugged in then... :(

---

### Post by pmansfield on 2012-09-20
Adding that line worked for me as well, thanks!

---

### Post by Routhinator on 2012-10-01
I'm adding myself to the list that this has fixed issues for.

I want to add a few points about this.

- This did not affect me until an update came down about a month ago. I have never had sound problems with any previous Ubuntu version.

- Reinstalling 12.04 off the CD and refusing updates fixes the issue, however the issue returns as soon as updates are done.

- This issue is related to video skipping and flash video problems that have been popping up in the forums, on AskUbuntu, and around the internet. I have been trying to fix this issue for weeks, and went down flash troubleshooting paths and the like, with no success.

- Removing PulseAudio in favour of ALSA also fixed the issue for me, however this was not a 'preffered' solution in my eyes as it is a system change and not a true fix. This does seem to indicated that although the fix is to change an ALSA setting, the problem actually seems to lie with a misunderstanding between ALSA and Pulse, as ALSA works just fine without Pulse involved in the equation.

---

### Post by randomdrake on 2012-10-02
> **adityeah said:**
> Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic

That was all. I think I had tried it earlier too but somehow it was not working. Maybe I had tried too much.

But I think the problem was indeed that it was trying to use the  ALC888 as ALC662 and that was not happening.

Thanks for the responses. Now I can stick to Ubuntu and try to get friendly with Unity
Perfect! This was one of the last things preventing my Ubuntu experience from being awesome. The stuttering sound was forcing me to listen to Pandora on my mobile device instead of being able to be plugged into my computer.

This also fixed a separate issue I was having with the volume. For some reason the volume was low enough that I had to boost it up above 100% in the sound manager which would distort the sound somewhat. Don't have to do that anymore either!

Here's the motherboard I was running my sound through:
```
randomdrake:~$ sudo dmidecode -t 2
# dmidecode 2.11
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: P8P67 LE
	Version: Rev X.0X
	Serial Number: 110119580001965
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0
```

Thanks so much!

---

### Post by grizzou on 2012-10-14
> **adityeah said:**
> Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic



The tips that save my life... today GREAT THANKs adityeah :KS:KS:KS:KS:KS

---

### Post by adityeah on 2012-10-20
Gee. wow. 

I did not return to this post after May 14 and look what happened! 

I am glad I could be of help to you all! Thank you for all your messages! I have never done something like this so I am just happy. :guitar:

---

### Post by eeeric on 2012-11-11
Another satisfied customer. I've got a fresh install of Debian Wheezy (installed 10 nov 2012). Using ALSA. No pulseaudio installed. Was getting glitches every couple of seconds when playing mp3's.

Adding 
options snd-hda-intel model=generic
to
/etc/modprobe.d/alsa-base.conf
and rebooting fixed it.

Thanks.

---

### Post by tonygil on 2012-11-19
same problem here: after 12.04 updates, sound stopped working (both rear and front panel).  ubuntu documentation is VERY VERY bad and inefficient.  

there is no real hardware config gui that i can find (only the pathetically superficial sound preferences).

scream at me all you want, geeks: ubuntu is OK as a backup system, but it is far from being major league stuff until it can reliably deal with simple tasks like configuring audio.

:confused:

---

### Post by KaptRoger on 2012-12-15
Well this was the real fix for me with my NVidia chip set.  Now my sound is good, and gapless(!), but.......

I have now lost my surround sound and subwoofer.  

It is a bit of a shame that currently it seems to be one (good sound) or the other (surround sound with glitches).

---

### Post by moises on 2013-01-29
Thanks a lot. Appending "options snd-hda-intel model=generic" to /etc/modprobe.d/alsa-base.conf did the trick also for me.

---

### Post by trallallero on 2013-02-16
Ubuntu 12.04 :(

Wish to downgrade to 10.04.

---

### Post by mörgæs on 2013-02-16
If it is a way of saying 'something does not work, please help' then a clear description of the problem would be a better approach.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by trallallero on 2013-02-16
The problem ? the problem**s**, I'd say.
I should open *a couple* of threads :)

Anyway: I have a pc with front and rear audio outputs and if I plug the headphones in the front plug, the audio goes away and cannot come back anymore even if I unplug the headphones.
I have to open the Sound settings panel and reset the volume, device, etc.

But this only sometimes... it happens that the volume goes to zero so I just have to increase it, it happens that I have to plug the jack only a bit (mono) not all to make it work, it happens that vlc stops playing when I plug the jack.

This in a pc used by my family. I don't have time to fix it as I work far away from home and come back only on the week-ends.
Every time my family calls me with Skype, the audio doesn't work as the volume and microphone level are set to zero. They have to reset them every time... really not nice.

I've tried the solution found on this thread but didn't solve the problem: the microphone of the webcam is not available anymore.

OT: just to explain why I'm really upset with Ubuntu 12:
Beside other problems, on my laptop, after having upgraded Ubuntu, I'm forced to use windows as the wi-fi device is not recognized anymore and there's no way (without loosing an entire day) to fix the problem.

---

### Post by mörgæs on 2013-02-16
> **trallallero said:**
> 
I should open *a couple* of threads 

Indeed. Don't mix several problems into the same one.

A thorough hardware description along with your experiences with various Buntu releases (12.04 / 12.10 / 13.10 development) would also help. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by froids on 2013-03-27
> [COLOR=#000000]*options snd-hda-intel model=generic*[/COLOR]

Works like a charm! For now, at least...
Thanks.

---

### Post by swartur2012 on 2013-07-01
I had this disturbing noise since ubuntu 12.04 installation. The issue considered to be a bug and explained here in a better way - [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/990605](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/990605) .
My problem was solved using solution posted here. Thanks a lot !

---

### Post by Luis_Arjona on 2014-01-12
> **adityeah said:**
> Solved! ):P

Here's what I did:

added this line at the end of /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=generic

That was all. I think I had tried it earlier too but somehow it was not working. Maybe I had tried too much.

But I think the problem was indeed that it was trying to use the  ALC888 as ALC662 and that was not happening.

Thanks for the responses. Now I can stick to Ubuntu and try to get friendly with Unity


Thanks for your solution :KS  it has helped me to half solve a sound problem in a netbook with a Realtek ALC269VB.
I had no internal micro input and a very strong skeeek as the only output. After apending the line as you did I recovered sound in my internal speakers. I still have to sort out the microphone problem but getting rid of the skeeek was a great relief. (Sorry for wrtting this two times. I do not undestand how this works. I write my reply and then int appears on a different place. I answer with quote in order to make it useful to anybody with a similar problem to the one I had)

---


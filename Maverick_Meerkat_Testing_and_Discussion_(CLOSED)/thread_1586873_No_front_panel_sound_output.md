---
title: "No front panel sound output"
date: 2010-10-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jimbob on 2010-10-02
I have no sound output from the speaker/headphone jack on the front panel of my computer.  Also I notice the headphone selector in the alsamixer graphics panel is grayed out.

---

### Post by cariboo on 2010-10-02
In some cases you may have to switch the output in System->Preferences->Sound Preferences->Output. I've got a Realtek ALC888 sound chipset, I have to change the output if I ever wanted to use headphones.

---

### Post by jimbob on 2010-10-03
I tried all possible combinations and still can get nothing from the front panel sound output jack.
  When I run the speaker test from the rear panel it shows only left and right speakers and the test only produces sound from the right speaker.

---

### Post by cariboo on 2010-10-03
DOes your sound preferences look like the included screenshots?

---

### Post by jimbob on 2010-10-03
Yes, mine looks just like yours except I do not have the HDMI controller in either case.

---

### Post by keypox on 2010-10-03
I have similar issue, I get sound from headphones and speakers when plugged in.  Changing to headphones turns off both.

---

### Post by peacewithall on 2010-10-04
I have this problem too, using onboard sound (VT1780S), under sound preferences my front jack was picked up as, 'headphones', now 'headphones is not there. I can only guess the last pulseaudio, or other sound updates broke it. The front jack is no longer working, alsamixer shows 'headphones' but it's greyed out, if I mess around with the 'Independent' switch the 'headphones' level seems to activate (is no longer grey), but still no sound. This was working not too long ago, both jacks played sound at the same time. Slightly annoying when I need to use a headset for calls.

Edited to add:
I disabled pulseaudio, the same thing was happening which I sort of guessed as the headphones were greyed out in alsamixer. I'm not sure ALSA received any updates, but I am sure we had a kernel update not too long ago, I would boot into an older kernel, but in my efforts to keep things clean I removed all old kernels, and the repo's seem to have removed all old kernels as well, which isn't a great idea for testers :/. I suspect the kernel though, as the source of this problem. I have noticed a lot of un-answered posts on these forums on this subject, and I know some people were seeking a fix for speakers to mute while headphones were plugged in, I can only guess a kernel update to fix that, has unfortunately broken any sound at all, from the front jack for us.

---

### Post by peacewithall on 2010-10-04
OK I kind of fixed the problem, well at least got it back to how it used to be.

I entered the BIOS, and from there found an option under 'Onboard Device Configuration', from there I found 'Front Panel Select', the default was set to, [HD Audio], so I tried setting it to [AC97].

I rebooted and got my ears deafened by the Ubuntu tune playing directly from my headphones !!, I found the volume control did not control sound level at first, so I had to open alsamixer, and 'undo' my previous setting of switching 'Independent' to on. back to it's default 'OFF'.

I have heard some people having front jack sound problems that enable <Smart 5.1>, so thats disabled as well.

I also notice that the headphones level is now greyed out once again, even though sound now works perfectly, and with volume control. Only drawback is that sound plays from both front and back panels, but most good speaker sets have an off switch, so I'm happy once again :).

---

### Post by jimbob on 2010-10-06
> I entered the BIOS, and from there found an option under 'Onboard Device Configuration', from there I found 'Front Panel Select', the default was set to, [HD Audio], so I tried setting it to [AC97].

Thanks, this worked for me also although the headphone jack in alsamixer is still grayed out.

I was looking at the list of sound drivers from lsmod that were loaded in 10.4 vs. those in the 10.10 release and see that there are  five drivers that no longer appear in 10.10.  They are snd_pcm_oss, snd_mixer_oss, snd_seq_dummy, snd_seq_oss and soundcore.  I have no idea if these could be related to the problem or not.

---

### Post by lidex on 2010-10-07
> **jimbob said:**
> Thanks, this worked for me also although the headphone jack in alsamixer is still grayed out.

I was looking at the list of sound drivers from lsmod that were loaded in 10.4 vs. those in the 10.10 release and see that there are  five drivers that no longer appear in 10.10.  They are snd_pcm_oss, snd_mixer_oss, snd_seq_dummy, snd_seq_oss and soundcore.  I have no idea if these could be related to the problem or not.

Anyone here with problems please run alsa-info script. These issues are hardware specific. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jimbob on 2010-10-08
@lidex

  Ran the script.  Here is link to output:

[http://www.alsa-project.org/db/?f=6fc3faac2ccba8d80af293674b5534ad9169c16a](http://www.alsa-project.org/db/?f=6fc3faac2ccba8d80af293674b5534ad9169c16a)

Thanks.

---

### Post by lidex on 2010-10-08
> **jimbob said:**
> @lidex

  Ran the script.  Here is link to output:

[http://www.alsa-project.org/db/?f=6fc3faac2ccba8d80af293674b5534ad9169c16a](http://www.alsa-project.org/db/?f=6fc3faac2ccba8d80af293674b5534ad9169c16a)

Thanks.

That looks OK, but I see your codec is VIA VT1708S. I'm seeing a lot of problems with no real solutions. Try this. 
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by freacert on 2010-10-08
same problem here

did i new install with 10.04, had the problems before, and remembered it had something to do with independent hp. 
but, not now. No sound at the front, can get the mic to work. 
my output [http://www.alsa-project.org/db/?f=3a4ed8e0b867a6ca6b8a2d1d9d6ec5a67bea4db9](http://www.alsa-project.org/db/?f=3a4ed8e0b867a6ca6b8a2d1d9d6ec5a67bea4db9)
same via vt1780b chipset. 
sound seems to come out only of the side channel.

did what lidex proposed, no luck. 
will check the bios now.

---

### Post by freacert on 2010-10-08
> **peacewithall said:**
> OK I kind of fixed the problem, well at least got it back to how it used to be.

I entered the BIOS, and from there found an option under 'Onboard Device Configuration', from there I found 'Front Panel Select', the default was set to, [HD Audio], so I tried setting it to [AC97].



and that did not work for me either..


Sorry to enter this maverick meerkat testing and discussion forum, found the same problem on lucid, hope to find a solution here or there.

---

### Post by Yumi on 2010-10-08
Sorry, posted to the wrong thread

---

### Post by freacert on 2010-10-08
> **freacert said:**
> and that did not work for me either..


Sorry to enter this maverick meerkat testing and discussion forum, found the same problem on lucid, hope to find a solution here or there.


looks like after many times switching independent hp on off it all of a sudden works.
But have to do that when there is no sound playing. Great. Good clean ubuntu machine running again!!!

---

### Post by rajeev1204 on 2010-10-08
> **freacert said:**
> and that did not work for me either..


Sorry to enter this maverick meerkat testing and discussion forum, found the same problem on lucid, hope to find a solution here or there.


Here is what i know .Many newer motherboards support HD audio through the front ports for supported cabinets, in case you have a normal PC case like most people on earth do, just go to bios and change it to AC 97 audio and it should ouput from front ports also, but this will not stop audio from speakers so you have to turn the volume on speakers off .So unlike previous systems where speaker output mutes on connecting front panel , today that only happens if its HD audio in front panel . 

Someone posted this before but i just want to say its the same for my motherboard too.

---

### Post by jimbob on 2010-10-09
@lidex

  I ran the code in your post #12 above and it gave me output on both front and rear jacks so that is good enough for me.  Thanks.

Only strange thing is that the headphone selection in alsamixer is still grayed out.

---


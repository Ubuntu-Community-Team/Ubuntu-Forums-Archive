---
title: "Problem: the voice is filtered out from headphone playback"
date: 2009-05-04
forum: Multimedia Software
---

### Post by m_alnaanah on 2009-05-04
I have install ubuntu 9.04. it was great and light.

but there is a problem with sound play back from headphone.

when playing certain sound the human voice is filtered out and other sound type (like music) is played.

this problem only happen when I plug the headphone.

when sound is played from speaker it's OK.
Any help please.

this is the type of my sound card (using lspci -v)


00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
	Subsystem: IBM Device 02f7
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	I/O ports at 3400 [size=64]
	Memory at d03c0800 (32-bit, non-prefetchable) [size=512]
	Memory at d03c0400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

---

### Post by bobince on 2009-05-04
> **m_alnaanah said:**
> when playing certain sound the human voice is filtered out and other sound type (like music) is played.

It's not quite clear what you mean here. Do you mean using certain applications causes the sound played by other applications simulataneously to stop? If so, this is typically two applications trying to use the sound card through ALSA at once and can usually be fixed by telling them to share nicely with PulseAudio instead.

Or do you mean that when you play some songs the vocal is inaudible? In this case the problem is typically that you're listening to out-of-phase stereo material in mono: the left and right tracks subtract from each other, removing the content that is the same on each track (ie. content placed in the centre of the soundstage, which is where the vocal usually is). This could be a wiring problem.

---

### Post by m_alnaanah on 2009-05-07
Thanks Alot Bobince.

The problem was the second one (the vocal sound is inaudible), I changed the level of one channel and the problem is gone.Also  I changed the headphone and the problem is gone too. 

thank you for your help.

best wishes.

---

### Post by torboxz on 2010-10-18
Hi,

I got the exact same problem. Wiring is probably not the problem. I've install Ubuntu on 3 machines and it's the same. The voice is filtered out.

Interestingly, if I move the balance slider on the sound preference (output tab) to the left or right, the voice came back which I don't want because it's not stereo. If the slider is in the middle, the voice is filtered (just like karaoke mode- :confused:).

Please, help.

---

### Post by robert shearer on 2010-10-18
something is **out of phase**, maybe a configuration.

For troubleshooting purposes can you install 'potamus' and open a music file with it.

Then while playing use the drop-down box at top left to toggle through the settings. (OOPS or Phase should correct the problem) report which works and from there we can perhaps diagnose the overall setting that is causing the odd sound behavior.

---

### Post by torboxz on 2010-10-18
Thanks Robert for the quick reply.

I've installed potamus and 'Phase' has corrected the problems. After days reading here and there, finally, a solution. Even though it's not fixed yet, :smile: I can't stop smiling. Are we getting closer to the solution?

Regards,
torboxz

---

### Post by robert shearer on 2010-10-18
Progress ! good.


[COLOR="Red"]EDIT..[/COLOR] before doing any of the below try the suggestion from the other thread you posted on....
[http://ubuntuforums.org/showpost.php?p=9990202&postcount=4](http://ubuntuforums.org/showpost.php?p=9990202&postcount=4)

(for future reference please don't post the same query to several threads as we all end up duplicating efforts or trying to sort things without having all the details. :(

 At the very least include a **link** to the other thread/s. 

The **best** thing you could have done would be to have started a new thread and included links to the other two. :) )

Now, before getting too involved with configurations, lets just clarify a few things.
I am going to make a few assumptions so correct me if any are incorrect.....:)

1) as you have said...> I've install Ubuntu on 3 machines and it's the same. then, assuming that these are different computers with differing hardware and sound cards ?, we could rule out a hardware problem.

2) as there seem to be no other reports of this problem on the forums (searched forums and google) then we could probably rule out an Ubuntu O/S problem.

3) you have not mentioned any apps that this occurs with or any that it doesn't so I guess it is system-wide.

4) you haven't mentioned any sound apps you may have installed or modified so I presume that these are standard out-of-the-box installs and set-ups.

5) when you run the **live cd** the sound problem is the same as when the o/s is installed ?

  this would indicate that there is something about your install, common to all your installs, that is setting up sound wrong.
Looking at what may be common across all three the only thing that comes to mind is the install media.

Presuming you downloaded the iso and burnt it to disc then used it to install ?.
 Was the download from the Ubuntu site or elsewhere ?

Perhaps the Iso is corrupted **or** the snapshot you have had a sound glitch that was fixed and only appeared for a short time.

If it is possibly, try downloading a current iso from the Ubuntu site and run as the live cd to see if the problem is still there.

If it is fixed then reinstall on one of your computers using that cd and see if the problem is fixed on the install.

---


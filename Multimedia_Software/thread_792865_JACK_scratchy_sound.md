---
title: "JACK scratchy sound"
date: 2008-05-13
forum: Multimedia Software
---

### Post by The 77 on 2008-05-13
Hi! I've seen a lot of posts about this and none solved my problem.

I know the information im gonna give its pretty vague, but im at work right now (and not in my ubuntu machine).

I have UbuntuStudio 8.04 installed on a PC. Sound plays excelent!

But everytime i try to do ANYTHING through JACK sounds really bad. 

For example, i start ZynAddSubFx and play a couple of notes in the VK and it sounds fine. Then if i start JACK (close and start again ZynAddSubFx)it sounds like crap. Tried with Ardour and same thing, Hydrogen and Ardour and same thing....i hate this.

I'm not having any kind of xruns, i tried with every possible option (lowering or rising frames, etc). I'm running the realtime kernel. 

Changed sound cards (just to check hardware issues) and nothing.

Its not problem of Mic or Line either. Cause when i plug for example a mp3 player (or my guitar...or bass or w/e) everything sounds perfect. 

And its not UbuntuStudio, cause i have a pc right next to this troubling one and everything works perfect.

Anyone could lend a hand over here please (im tired of reading and reading and reading and not solving anything).

---

### Post by earos.dk on 2008-05-13
I don't know if Ubuntu Studio is default using the RT kernel, but IMO this is mandatory when using Jackd. Here it works wonderful with IEE1394 FireWire, indeed.

Kind regards,
[www.earos.dk](www.earos.dk)

---

### Post by MetalMusicAddict on 2008-05-13
Can you try adding **nohz=off** to your grub line?

Example:

Terminal: sudo nano /boot/grub/menu.lst
```
[SIZE="1"]title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=d01c8f74-2cb0-4f2e-940e-8428084b03f3 ro quiet splash **[COLOR="Red"]nohz=off[/COLOR]**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet[/SIZE]
```

---

### Post by The 77 on 2008-05-13
Uh! Im gonna try that the minute i get home and report back!! Thanks for that (for sure i didnt try that!)

Probably not, but worth the shot: when i installed ubuntu | ubuntu studio i had to use noapic or i would get "kernel panic".

Could this be related too? (the other pc i have ubuntustudio on, didnt gave such a problem)

---

### Post by The 77 on 2008-05-13
Ok, i tried that one.....and still no luck....i'm in pain here!!! I want my good ol' Jack Sound!!!

Any other ideas?

---

### Post by markbuntu on 2008-05-14
I had this problem and I think it has to do with ALSA. I fixed it in jackcontrol but I don't remember how. Something to do with the changing the driver from h:0.0 ALSA to the h:0.1 (sound card specific), something like that.

I had a lot of problems with jack and Ubuntu Studio in general running on 8.04. I think a lot of configurations got broken in the changeover and Studio is not entirely adjusted to the changes that 8.04 wrought.

---

### Post by Stochastic on 2008-05-15
can you post a screenshot of your jack settings?

---

### Post by The 77 on 2008-05-15
Attached you'll find the screenshot.

I've tried playing with frames, and with interfaces, inputs and outputs...and nothing.


One last thing, I changed my motherboard and nothing....(i had a spare one) i'm getting a little tired :(

---

### Post by The 77 on 2008-05-17
bump!

---

### Post by Stochastic on 2008-05-17
Try unchecking "Soft Mode" "No Memory Lock" and "Monitor" as well as raising the realtime priority from 10 to about 80.  Also you may want to try what markbuntu suggests of declaring the exact device rather than piping to alsa's default mixer.

---

### Post by DaVince21 on 2008-05-17
> **The 77 said:**
> Hi! I've seen a lot of posts about this and none solved my problem.

I know the information im gonna give its pretty vague, but im at work right now (and not in my ubuntu machine).

I have UbuntuStudio 8.04 installed on a PC. Sound plays excelent!

But everytime i try to do ANYTHING through JACK sounds really bad. 

For example, i start ZynAddSubFx and play a couple of notes in the VK and it sounds fine. Then if i start JACK (close and start again ZynAddSubFx)it sounds like crap. Tried with Ardour and same thing, Hydrogen and Ardour and same thing....i hate this.

I'm not having any kind of xruns, i tried with every possible option (lowering or rising frames, etc). I'm running the realtime kernel. 

Changed sound cards (just to check hardware issues) and nothing.

Its not problem of Mic or Line either. Cause when i plug for example a mp3 player (or my guitar...or bass or w/e) everything sounds perfect. 

And its not UbuntuStudio, cause i have a pc right next to this troubling one and everything works perfect.

Anyone could lend a hand over here please (im tired of reading and reading and reading and not solving anything).

I experienced the same thing and managed to fix it by changing the input device to hw1. I think I had to raise the amount of periods per buffer to at least 4, too.
Don't forget to manually set both your input and output device!

---

### Post by teledyn on 2008-05-27
I am running  2.6.24-16-rt and I can set the Realtime options with QJackctl, but when I do, I can no longer run Creox as it complains of not being able to lock down memory; when I set jackd off from realtime, I can run creox, but as reported here, the sound is really bad.

I am using a dual-core 2GHz machine, and this is the only app running; I can't see real load being the issue.

---

### Post by teledyn on 2008-05-27
> **teledyn said:**
> I am running  2.6.24-16-rt and I can set the Realtime options with QJackctl, but when I do, I can no longer run Creox as it complains of not being able to lock down memory; when I set jackd off from realtime, I can run creox, but as reported here, the sound is really bad.

I am using a dual-core 2GHz machine, and this is the only app running; I can't see real load being the issue.
aha ... I set it Realtime, but UNselected "lock memory" (and boosted priority to 45) and it's nice and smooth now, even with multiple effects.

---


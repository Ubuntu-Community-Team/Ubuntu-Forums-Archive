---
title: "Webcam &amp; Microphone - Aspire One D150"
date: 2009-05-14
forum: Multimedia Software
---

### Post by sc0g on 2009-05-14
Evening,

I just installed Ubuntu 9.04 Netbook Remix on my Acer Aspire One D150-1165. I am having an issue with:

- Microphone will not record; Sound capture setting is set to "HDA Intel ALC272 Analog (ALSA)" 
- Cheese webcam is choppy when recording video; I believe this may be a result of the microphone not working
- Wifi LED doesn't illuminate (I read some other threads about this issue on the Aspire one, but I actually like the fact that it is off/not working)

I found this [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/354620) about the microphone issue, but don't know or haven't found any solutions yet.

So far, I have only found one topic in the forums about the D150 model so I wanted to start this thread for some help.

BTW, this little netbook runs Ubuntu 9.04 Netbook remix very nicely... Other than the microphone issue, I am extremely pleased with my $326 purchase :-) Any help would be greatly appreciated.

---

### Post by pokpig on 2009-05-18
I have the exact model and can confirm that internal mic is still not working.

Changing sound setting doesn't help. 

Also there is only Front Mic option in the option tab of the volume control. The front mic in this case turns out to be the mic jack on the left. I try plug in an ext. mic in that and sound recording is working well. However, it would be a lot better if internal mic can work. 

any suggestion would be deeply appreciated.

update: 

On further searching, like [this post]("http://newyork.ubuntuforums.org/showthread.php?t=1140402")... I am convinced that an update to kernel 2.6.30 should be able to solve the problem. I have not tried it myself since it's not in the stable repo yet. 

I seriously want to understand why in some more details.

---

### Post by sc0g on 2009-05-23
Hey,

Hooking up an external microphone works like a charm; like you said, it's the internal mic that's not working.

I read a post somewhere (too lazy to find it at the moment, just search for D150) about upgrading to the lastest version of ALSA on [http://www.alsa-project.org](http://www.alsa-project.org)

By the way, concerning Cheese not recording video... I simply lowered the resolution of the webcam in Cheese (Edit > Preferences) and it works fine, only issue is that it's not recording audio from the internal mic! External mic works good!

;)

---

### Post by junglist313 on 2009-06-16
I just purchased this same model (quite pleased as well btw) and have noticed this same issue. I poured over every option in alsa mixer :neutral:, skype :-k, volume control applet ](*,), contemplated switching back to moblin :cry:, then I found this thread \\:D/. I was wondering if you are all still having the same issue or if anyone has found a workaround (other than the external mic). Thanks!

---

### Post by mer.man on 2009-06-19
I am also having an issue with the built-in webcam on my aspire one (ZG5) running Ubuntu NR.  All I get is color bars in cheese.  In the source list I I get is USB 2.0 Camera (/dev/video0).
 
Any suggestions?

I'm a bit of an Ubuntu Noob but lovin it so far.

---

### Post by sc0g on 2009-06-19
> **mer.man said:**
> All I get is color bars in cheese.  In the source list I I get is USB 2.0 Camera (/dev/video0).
 
Any suggestions?

Have you tried changing the resolution within Cheese? Since you're having the color-bars issue, I don't know if this will help, but it's worth a shot... Your model (ZG5) is somewhat different than mine (D150) so you may have a slightly different camera than me.

Run the command *lspci* and *lsusb* and post the output here so I can compare your camera type with mine.


> **junglist313 said:**
> I just purchased this same model (quite pleased as well btw) and have noticed this same issue. I poured over every option in alsa mixer :neutral:, skype :-k, volume control applet ](*,), contemplated switching back to moblin :cry:, then I found this thread \\:D/. I was wondering if you are all still having the same issue or if anyone has found a workaround (other than the external mic). Thanks!

At this point, I have not found any solution to the microphone issue, and I've only spent less than 2 hours total on trying to find the issue... only hooking up an external mic works for right now...

However, I did find this post ([http://ubuntuforums.org/showthread.php?t=1141529](http://ubuntuforums.org/showthread.php?t=1141529)) where the guy manually installed the latest ALSA drivers and claims it's working... I'm not sure if I am going to take that route or not.

---

### Post by tomreid on 2009-07-16
Hi All - I'd just love to find a solution to this. You won't believe the hours I have spent on this, as it always bugs me if I can't fix something. 

I use skype a lot and as there was so many forum posts about audio capture on 8.10 and 9.04 I assumed it was a skype problem and wasted hours of my life trying to fix skype, when the problem all along was the overall audio input settings on the Acer. I plugged an external mic in today and it worked, wow.

Anyway, there seems to be no consistent answer out there about how to get the internal mic working, so I'll keep searching, or just bug a mic and headset if I need to use this soon.

cheers

---

### Post by sc0g on 2009-07-16
> **tomreid said:**
> Hi All - I'd just love to find a solution to this. You won't believe the hours I have spent on this, as it always bugs me if I can't fix something. 

I am about to test the solution posted in this topic: [http://ubuntuforums.org/showthread.php?t=1141529](http://ubuntuforums.org/showthread.php?t=1141529)

I will let you know the results ASAP.

---

### Post by rreyes3000 on 2010-03-29
It's been awhile since I have tried to solve this. Has anyone found a solution?

---

### Post by sc0g on 2010-07-13
rreyes3000,

After installing Ubuntu 10.04 Netbook Remix and changing a few Input settings, I was able to get the internal microphone working.

However, as soon as I applied a few updates, **the internal mic stopped working again!** I think I'm going to try downloading the latest ALSA drivers and give that a shot...

---

### Post by libssd on 2010-07-13
AA1 D150, purchased June 2009. Installed Desktop 10.04 about a month ago, and current with all available updates. Everything works, including suspend, camera, and microphone (except with Skype, but that's due to Skype's lousy software).

If you find a 2.5" SATA 32gb SSD on sale, go for it -- performance is very nice, and the drive just drops in (you have to transfer the bracket from the HDD, but that takes 60 seconds). <20 second boot; <5 second shutdown. The SATA I bus on the D150 (and probably all netbooks) is limited to 140 mb/sec, so the SSD can't live up to its full potential, but it can always be moved to another machine at a future date. I LOVE my AA1 with a fast SSD!

---

### Post by roy913 on 2010-08-19
> AA1 D150, purchased June 2009. Installed Desktop 10.04 about a month ago, and current with all available updates. Everything works, including suspend, camera, and microphone (except with Skype, but that's due to Skype's lousy software).

10.04 provides out-of-the-box experience with aspire one D150 except for skype. the solution for using built-in mic in skype is to replace pulse audio with alsa. (Check out: [http://www.4geeksfromnet.com/2009/12/replace-pulse-audio-with-alsa.html]("http://www.4geeksfromnet.com/2009/12/replace-pulse-audio-with-alsa.html") )

The only shortcoming is that you have to adjust the volume by gnome alsa mixer instead of handily using the icon on the panel.

---


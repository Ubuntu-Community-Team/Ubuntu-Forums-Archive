---
title: "Running Wubi, upgraded to Karmic, sound doesn't work"
date: 2009-12-11
forum: Multimedia Software
---

### Post by ZucchiniMuffin on 2009-12-11
Hello, everyone! I tried to get some live help in the IRC room, but it was pretty busy in there and my question got lost in the sea of chatters, so I'm hoping I can get some help here. I've read a lot of sound support threads, but while they've helped me get a better idea of what the problem is, I don't quite understand the solution.

WARNING: I am totally a newbie to Ubuntu. Not to say that I'm computer-illiterate, but I do feel like I'm out of my element while troubleshooting. So while I've gone to different sites and followed instructions to help, I think I need a little more hands-on help.

Backstory: I have a secondhand Toshiba Satellite laptop running Windows Vista (ugh), given to me for free. This thing barely runs with Vista. It freezes a lot and constantly disconnects from the internet, I can't have more than 2 programs open at once, and it sometimes just shuts down from the sheer effort of being on. I was considering wiping it and trying Ubuntu, but as a non-Linux type I was rather unsure about trying something new. I learned about Wubi, which I promptly installed, and suddenly I was running Jaunty Jackalope and things were AWESOME. As long as I ran Ubuntu, the laptop has been working like a dream. I couldn't believe it was the same computer! So my plan was that I would try it out for a few months, and if I really liked it, I'd just wipe the whole thing and run Ubuntu as a single boot. I plan to do this, probably soon. This brings me to the problem at hand.

Current Issue: When I upgraded to Karmic Koala, Ubuntu stopped recognizing my audio hardware, and now I have no sound. When I run Vista, I do still have sound, so it does not seem to be a hardware issue. When I go to System - Preferences - Sound, there is nothing listed under hardware.

Then I went [here]("https://help.ubuntu.com/community/SoundTroubleshooting") and here is what happened:
-I opened terminal to type in "aplay -l", and it said "LIST OF PLAYBACK HARDWARE DEVICES" with absolutely nothing else. That's it. It doesn't say "no soundcard found" or anything like that - just absolutely nothing.
-Then I typed in "find /lib/modules/`uname -r` | grep snd" and it said "command not found," but then immediately gave me a huge long list of items as the site said it should. So I figured that was probably up to snuff.
-Then I typed in "lspci -v | less" and it did give me info on my audio device.
-Then I went through the steps to figure out the whole ALSA repository thingie to see if my soundcard is supported. I learned that my module is snd-hda-intel, driver version 1.0.20, codec was LSI something or other (I can of course look this up again), but then I could not find any codec info in the ALSA-configuration.txt page I had pulled up. So I couldn't continue there.
-Then I started to read about manual installation on the site and tried the command to manually start the audio driver. No luck. Then I followed the command to refresh/reinstall the driver. No luck. Then when I looked at the next bit of instruction, it said "good luck to you" if I was going to follow them, and I realized I had no idea what I was doing and came here.

If someone's willing to help me out, that would be SUPER awesome. Let me know what you think, and what I can do! I'm willing to go through the steps above again and paste here what I read on terminal.

Also: I'm planning to wipe my entire drive at some point and just use Ubuntu as a single boot, since I rarely use Vista. The only thing I use it for at this point is for playing videos, since my sound no longer works on Ubuntu. So if I do switch over entirely, will it be likely that I'll continue to have sound issues? That's the only thing that's kept me from doing it. I hate Vista and have no real reason to keep it, since everything I use is compatible with Ubuntu anyway.

Thanks in advance! Sorry it was so long-winded... wanted to make sure I got all the info out there!

---

### Post by gordintoronto on 2009-12-11
If you boot from a Karmic Live CD, can you play the sample files?  If so, you should be able to install from the live CD, and have sound on the installed system.

Let me also add: for some reason, the default installation will partition your hard drive so it has a swap partition and a Linux partition.  You can do a manual partition, to have a swap partition, a / (root) partition of maybe 10 GB and a /home partition of the rest.  This has major advantages in the future when new releases appear.

---

### Post by ZucchiniMuffin on 2009-12-15
I made a Karmic boot CD, and sound did not work there either - when running it from the CD or trying out the sample files. I was sure this problem had started as soon as I'd upgraded to Karmic with Wubi, and I know you can't roll back versions - just need to reinstall (right?). So, since I was planning to wipe this computer of Vista and do a single boot with Ubuntu, I figured I should try making a Jaunty live CD. The sound worked just fine when booting from the CD, and all the sample files worked, so I am now running Jaunty and all's well. Thanks very much!

So this solves my problem - I now have an OS I'm happy with (even if I've still got a lot to learn) and I have working sound. However, I'm still totally not sure what the heck I would do if I did want to upgrade to Karmic one day, since I've just got no clue how to make it recognize my audio hardware. But Jaunty does, and it's working fine for me, so I'll stick with it for now!

Thanks for your help and response. I figured I'd update in case anyone else finding this thread has a similar problem.

PS, I could not do the partition thing! It asked me a lot of questions about manual partitioning that I didn't understand (told ya I'm a total newb :P), so I just let it go to the default. I hope this ends up being okay!

---


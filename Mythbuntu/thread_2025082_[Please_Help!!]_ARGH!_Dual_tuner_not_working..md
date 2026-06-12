---
title: "[Please Help!!] ARGH! Dual tuner not working."
date: 2012-07-14
forum: Mythbuntu
---

### Post by JamerTheProgrammer on 2012-07-14
MythTV isnt working properly again.....
I have 2 really annoying problems with MythTV (Im using Mythbuntu 10.10):

Sometimes when I start up I get an error saying that the tuner is busy but it isnt recording (This can be fixed by a reboot)

At the moment I cannot record one thing and watch another channels (Although, If I am watching Channel 4 I can watch ITV and all the other Channel 4 channels just not BBC and some others)

Im going to have to switch to Windows if this bloody thing wont stay put and work properly. I cannot afford to give my family a bad impression on this media centre thing (It was hard enough getting them to warm up to the idea).

What the hell can I do to fix this?
I havent changed any settings at all. It was working fine yesterday, today it isnt.
Upgrading MythBuntu to 12.04 isnt an option because It doesn't work on any Ubuntu above 10.10.

I beg of you, please help me!
Thanks!

I hope I can get this to work... I had to work 7 hours to get it to work with my tuner and 3 hours customising it to suit my family.
PS:
Just thought I would note I was working on this for several hours on end (Believe me it is not fun at all) and having failure after failure after failure. So thats why I was a tad bit annoyed in the post.

---

### Post by JamerTheProgrammer on 2012-07-14
Duplicate Thread 
-Snip-

---

### Post by overdrank on 2012-07-14
Hi and please do not create multiple threads on the same issue. Threads merged.

---

### Post by JamerTheProgrammer on 2012-07-14
> **overdrank said:**
> Hi and please do not create multiple threads on the same issue. Threads merged.

Oh dear, sorry about that! I ment to edit that post not make a new one.

---

### Post by tgm4883 on 2012-07-14
I'm going to have to guess at a bunch of stuff here, because you haven't told us all the info (what tuner you have, do you have any other tuners, etc). 

The issue you are likely having is that during boot your dual tuner is coming up as a different device number (eg. /dev/video1 instead of /dev/video0). This is causing MythTV to have issues, as the device at the location it knows about (eg. /dev/video0) is not the type of device it expects.

Further, it sounds as if you don't have your dual tuner setup properly inside MythTV, as you mention that you can only watch other channel 4 channels when you have a channel 4 recording going. The reason you can watch these other channel 4 channels is because of multirec (That is a good thing). The issue is that it seems you don't actually have the second half of your dual tuner setup or possibly your dual tuner only supports recording from one tuner at a time (ie. it's a hybrid tuner, not a dual tuner).

Lastly, I wasn't going to recommend moving to 12.04 (although I usually do recommend staying on LTS releases), but it seems rather odd that your device is supported in an older version of Linux and not a newer version. Device support isn't usually removed from newer releases.

Again, this is all just educated guessing since we don't have the important information.

:EDIT:

Apparently I forgot to add the link to making udev rules, which will resolve the issue of the device coming up in a different location (eg. /dev/video1) that it did previously.

[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

---

### Post by nickrout on 2012-07-15
> **JamerTheProgrammer said:**
> MythTV isnt working properly again.....
I have 2 really annoying problems with MythTV (Im using Mythbuntu 10.10):

Sometimes when I start up I get an error saying that the tuner is busy but it isnt recording (This can be fixed by a reboot)

At the moment I cannot record one thing and watch another channels (Although, If I am watching Channel 4 I can watch ITV and all the other Channel 4 channels just not BBC and some others)

Im going to have to switch to Windows if this bloody thing wont stay put and work properly. I cannot afford to give my family a bad impression on this media centre thing (It was hard enough getting them to warm up to the idea).

What the hell can I do to fix this?
I havent changed any settings at all. It was working fine yesterday, today it isnt.
Upgrading MythBuntu to 12.04 isnt an option because It doesn't work on any Ubuntu above 10.10.

I beg of you, please help me!
Thanks!

I hope I can get this to work as MythTV is awesome when it works... I had to work 7 hours to get it to work with my tuner and 3 hours customising it to suit my family.

Using words like "bloody" and "what the hell" are not likely to get you much help. Please be polite.

---


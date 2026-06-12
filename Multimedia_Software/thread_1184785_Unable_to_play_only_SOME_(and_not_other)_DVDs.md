---
title: "Unable to play only SOME (and not other) DVDs"
date: 2009-06-11
forum: Multimedia Software
---

### Post by RipRapRob on 2009-06-11
Hi there

I use my Ubuntu installation for (amongst other things) playing DVDs (so yes; I've installed the "Ubuntu restricted extras").

All DVDs I've played until yesterday have played just fine.


But yesterday I purchased Monty Python Flying Circus season 1 and 2 on DVD and for some reason I get an error saying "And error occured" and "Could not read from resource" when using Movie Player.

I've tried with all the discs from the set: Same error.

I've installed VLC but VLC won't play the DVD either (no error message - it just won't play it).

The Ubuntu computer has Windows installed too, and if I boot into Windows the DVD plays just fine in VLC, so it's not the hardware or the discs.

I've tried searching for a solution, but I haven't found other where the problem only occurred on *some* DVDs.

I'm using Ubuntu 9.04 and I have libdvdread4 installed and, as mentioned; the "Ubuntu restricted extras".

The hardware is a Dell Latitude D610 and the DVD-drive the standard internal one.

Help?:(

Rob, Denmark

---

### Post by Therion on 2009-06-11
How about the **libdvdcss2** and **W32 Codecs** packages... Installed?  If not, they need to be.

```
sudo apt-get install libdvdcss2 w32codecs
```
See if that helps.

By the way... Hows the weather in Denmark?

---

### Post by RipRapRob on 2009-06-11
Thank you for taking the time to help me.

The weather in Denmark is crap today; rainy and windy (also known as 'a typical Danish summer day' ;))

I tried your solution but I get:

```
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

```

I then tried

```

rob@rob-laptop-ubuntu:~$ sudo apt-get install w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
```

I've tried searching for the two packages in Synaptic Package Manager but I can't find it there. Am I missing some repositories?

Rob, Denmark

---

### Post by netJackDaw on 2009-06-11
Try to add the medibuntu repositories to your software sources. Check out [http://www.medibuntu.org](http://www.medibuntu.org) so you ge it all right!

---

### Post by Therion on 2009-06-11
Step 1: ```
sudo wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

Step 2: ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Step 3: ```
sudo apt-get install libdvdcss2 w32codecs
```

Oh, and run your Update Manager too.  Check to make sure the Medibuntu Repo checkbox is ticked "ON" under the Updates tab.  You'll probably have lots of new software updates now that the Medibuntu repository has been added.

---

### Post by RipRapRob on 2009-06-11
After following the steps above still can't play DVDs in Movie Player (I get "An error occured" and "Internal data flow error") but in VLC it works just fine.

Therefore; Thank you SO much you guys :-)

The weather has gone worse though; can you help with that too? ;-)

---

### Post by Otto Mobeal on 2009-08-20
I am a serious novice and was able to do much of what you guys were talking about, but what is VLC and where do I find it?
  I can get some limited play from the dvd player on the cartoon Happy Foot, but after a minute or two the picture disappears - I can still hear it, but not see it.  
I cannot get anything on another DVD.

Gateway MX3560
Ubunut 9.04

---

### Post by RipRapRob on 2009-08-21
> **Otto Mobeal said:**
> I am a serious novice and was able to do much of what you guys were talking about, but what is VLC and where do I find it?


It's a media player.

Applications >> Add/remove >> search for VLC

;-)

/Rob

---


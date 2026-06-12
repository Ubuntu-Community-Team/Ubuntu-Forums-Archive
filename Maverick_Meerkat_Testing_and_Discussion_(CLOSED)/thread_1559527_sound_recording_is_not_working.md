---
title: "sound recording is not working"
date: 2010-08-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rwabel on 2010-08-23
This issue was already with the 10.04 version and now still with 10.10. Sound works perfectly, but I cannot record anything except via line in. I've tried both microphone (internal and external), they are not muted as well.

I've tried with the Mandriva Live CD and I can perfectly record sound over the microphone and it also works fine under Windows.

My Laptop is a ACER Aspire 5538 and it's using snd_hda_intel. I've already tried to mute one channel, as described in several threads.

Not sure what I can do for testing or solving this issue.

---

### Post by kyleabaker on 2010-08-23
> **rwabel said:**
> This issue was already with the 10.04 version and now still with 10.10. Sound works perfectly, but I cannot record anything except via line in. I've tried both microphone (internal and external), they are not muted as well.

I've tried with the Mandriva Live CD and I can perfectly record sound over the microphone and it also works fine under Windows.

My Laptop is a ACER Aspire 5538 and it's using snd_hda_intel. I've already tried to mute one channel, as described in several threads.

Not sure what I can do for testing or solving this issue.

Sound recording does work, just not for your microphone apparently. You should file a report at [LaunchPad]("https://launchpad.net/ubuntu/+filebug") or take the plunge and fix it yourself like I did (for a different mic of course). ;)

---

### Post by rwabel on 2010-08-23
I would like to take the plunge and fix it...try several things, ready many threads and blogs. However nothing helped.

I should open it against pulseaudio I guess, but I cannot do that as it's not a genuine Ubuntu package

---

### Post by kyleabaker on 2010-08-23
Does your laptop also have a webcam or only the mic?

---

### Post by rwabel on 2010-08-23
it also has a webcam which works perfect

---

### Post by kyleabaker on 2010-08-23
> **rwabel said:**
> it also has a webcam which works perfect

Then its probably the same problem that I had with my webcam. It took me probably around a week to debug and test fixes with the guy who maintains the web cam drivers, but [I eventually got it working]("http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/") and sent him the changes so it should be working for everyone else from here on out.

This is usually the best way to go about fixing things like this so it helps everyone else who has the same problem and you won't have to patch it in the future. ;)

I suggest you do the following:
1. Subscribe to the "linux-media[at]vger.kernel.org" mailing list:
-- [http://www.linuxtv.org/lists.php](http://www.linuxtv.org/lists.php)
2. Send an email to the list with a title describing your problem and webcam/mic model numbers.
3. Wait for replies and work with them to debug the problem.

They are the most knowledgeable people around for webcam/mic related issues. The biggest thing to remember, if they can help you, is to be patient...but you should be able to figure out the problem with them.

----------

Just for laughs (to see if it changes anything) you should try installing the latest webcam drivers to see if its already been fixed upstream..

If you want to test this, download the latest "gspca-x.x.x.tar.gz" file from:
[http://moinejf.free.fr/](http://moinejf.free.fr/)

Extract it, open a terminal, change directories to it and type the following to install it:
```
make
sudo make install
```

Reboot after this and test your sound and video. This basically just installs a newer version of what you've already got installed. If it doesn't work in this or breaks your web cam then that means it won't work in the future or will break your webcam anyway soon...so if it breaks things or doesn't work then you should definitely contact the mailing list to see if they can fix it.

------------------

If they can't fix it then you should just file a report on it at LaunchPad.

Good luck and cheers.

---

### Post by simosx on 2010-08-23
Go [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
Post launchpad URL when created.

---

### Post by rwabel on 2010-08-23
@kyleabaker
I've tried it, but didn't help. However nothing did break.

@simosx
Thanks for this link. This is the link [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/623031]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/623031")

---


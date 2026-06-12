---
title: "Banshee 2.2 and amazon"
date: 2011-10-18
forum: Multimedia Software
---

### Post by linuxlover42 on 2011-10-18
Ok, I just upgraded from ubuntu 11.4 to 11.10, and one thing really ticks me off. While banshee 2.0 (included with 11.4) could download  the .amz files from the amazon cloud player, it seems that banshee 2.2 (included with 11.10) cannot. Whenever I try I get something to the effect of "The amazon downloader file is not valid"

If anyone has a solution please help me out.

---

### Post by linuxlover42 on 2011-10-18
hmm, forgive me, it seems that i cannot download the fire because I'm running a 64 bit system and amazon thinks it should give me 64 bit .amz files. anyone know a way around this?

---

### Post by linuxlover42 on 2011-10-19
then again, I tried it on a 32 bit system with the same result... hmm...

---

### Post by mykrob on 2011-10-19
Having a similar problem. I downloaded the .deb file from the Amazon site and can't satisfy the dependencies to install it.

So how do I get Banshee to download my music from Amazon like it used to?

---

### Post by linuxlover42 on 2011-10-19
clamz is also giving me a weird error message. The .amz files from the cloud player are slightly different from the regular ones. I would say this has something to do with the OS but I tried it on a linux mint 11 (which is more similar to ubuntu 11.04 that 11.10) and got the same result.

The error from clamz is 

```
ERROR: Invalid base64 data in AMZ file 'Amazon-MP3-1318990736.amz'

0 of 1 AMZ files downloaded successfully.
```

---

### Post by linuxlover42 on 2011-10-19
I have a temporary fix untill this can be rectified. Install the windows version of the amazon mp3 downloader with wine. Then open the .amz file with it. It will give you an error and crash when it tries to add the songs to the Windows Media Player but it will download the music.

Cheers:guitar:

---

### Post by pemadorje on 2011-10-21
I'm having the same issue. When I try to download something from the Amazon Cloud Player after making a purchase, it's asking me to install the Amazon MP3 downloader (same on either 32 or 64 bit). I don't recall ever seeing this on 11.04. Seems like pretty basic functionality. Anyone else seeing this or have a solution that doesn't invalid installing the windows version?

---

### Post by Jay-Cee on 2011-10-22
I am having the same issue since I upgraded to Ubuntu 11.10.

---

### Post by pemadorje on 2011-10-27
It turns out that this was due to the following bug.

[https://bugzilla.gnome.org/show_bug.cgi?id=661467]("https://bugzilla.gnome.org/show_bug.cgi?id=661467")

I went ahead and added the Banshee daily ppa, ppa:banshee-team/banshee-daily and ran updates to get the fix. 

It now works fine again.

---


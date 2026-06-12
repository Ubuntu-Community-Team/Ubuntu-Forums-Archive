---
title: "Creating an ISO from a VIDEO_TS directory"
date: 2011-03-05
forum: Multimedia Software
---

### Post by metalguy639 on 2011-03-05
I've searched but I can't seem to find something that is specific to what I'm looking for. I need to create an ISO from a VIDEO_TS folder on my hard drive. How would I go about that?

---

### Post by jerome1232 on 2011-03-05
I'm at a Windows machine at the moment so I can't check the exact options you need to pass it program growisofs can do what you want, I've used it before and it works great.

Here's an online man page for it, you can get this help document by typing man growisofs after installing it.

[http://www.linuxcommand.org/man_pages/growisofs1.html](http://www.linuxcommand.org/man_pages/growisofs1.html)

---

### Post by MepisReign on 2011-03-06
You need to consider that probably with the growisofs command you will create an ISO image yes, but will only contain the VIDEO_TS directory, once you burn that ISO image to a disc it won't play on a regular dvd player, since the AUDIO_TS directory will be missing.
What I would do is the next:

1. Install k3b ---- sudo apt-get install k3b
2. Open k3b and choose New Video DVD Project
3. Place all the files contained inside the original VIDEO_TS directory within the VIDEO_TS directory in k3b.
4. Burn the disc or create an ISO image, depending on your needs. I would strongly suggest that if you are going to burn the disc choose at maximum burning speed 4X, that way the resulting disc will not "jump" at the time that your are watching the video.

I don't know if Brasero or Gnomebaker are capable to do this, that's why I'm suggesting k3b.

Hope this helps,

MepisReign

---

### Post by ron999 on 2011-03-06
Hi
I agree with **MepisReign** above. K3b is the way to go.

If you want to do the job from command line you need your VIDEO_TS directory and an _empty_ AUDIO_TS directory inside a folder (named "DVD" or similar).
Then use command 
```
genisoimage -dvd-video -v -o DVD.iso DVD
```

This will create an iso named **DVD.iso** from the **DVD** folder.

---

### Post by metalguy639 on 2011-03-06
> **MepisReign said:**
> You need to consider that probably with the growisofs command you will create an ISO image yes, but will only contain the VIDEO_TS directory, once you burn that ISO image to a disc it won't play on a regular dvd player, since the AUDIO_TS directory will be missing.
What I would do is the next:

1. Install k3b ---- sudo apt-get install k3b
2. Open k3b and choose New Video DVD Project
3. Place all the files contained inside the original VIDEO_TS directory within the VIDEO_TS directory in k3b.
4. Burn the disc or create an ISO image, depending on your needs. I would strongly suggest that if you are going to burn the disc choose at maximum burning speed 4X, that way the resulting disc will not "jump" at the time that your are watching the video.

I don't know if Brasero or Gnomebaker are capable to do this, that's why I'm suggesting k3b.

Hope this helps,

MepisReign

I've already done that. I'm wanting to make an ISO image to burn so I can burn the dvd without having to reauthor it since k3b will NOT burn it :( I always use k3b. 

Brasero comes up with some stupid error message saying its missing a gstreamer plugin that is already installed so it has not been helpful either. 

Are there any other burning programs I can try that burn dvd's?

---

### Post by metalguy639 on 2011-03-06
> **ron999 said:**
> Hi
I agree with **MepisReign** above. K3b is the way to go.

If you want to do the job from command line you need your VIDEO_TS directory and an _empty_ AUDIO_TS directory inside a folder (named "DVD" or similar).
Then use command 
```
genisoimage -dvd-video -v -o DVD.iso DVD
```

This will create an iso named **DVD.iso** from the **DVD** folder.

Thanks, I'm assuming the last DVD in the code would be the DVD directory where the output iso would end up?

---

### Post by cchhrriiss121212 on 2011-03-06
I've used xfburn many times for this task, and it has yet to fail on me:
Select new data composition
Add the video_ts and audio_ts
Burn

---

### Post by ron999 on 2011-03-06
> **metalguy639 said:**
> Thanks, I'm assuming the last DVD in the code would be the DVD directory where the output iso would end up?
Nope
It's the name of the folder that holds your VIDEO_TS and AUDIO_TS directories.

---

### Post by metalguy639 on 2011-03-06
> **cchhrriiss121212 said:**
> I've used xfburn many times for this task, and it has yet to fail on me:
Select new data composition
Add the video_ts and audio_ts
Burn

Ok I'll give that a try. I have it already installed on the machine. Thanks.

---

### Post by metalguy639 on 2011-03-06
Thanks for the help, looks like the IFO file is bad so I guess I'm stuck with reauthoring it :(

---

### Post by lemik on 2012-04-24
Here is the answer:
[http://ubuntuforums.org/showpost.php?p=9557968&postcount=10]("http://ubuntuforums.org/showpost.php?p=9557968&postcount=10")

---


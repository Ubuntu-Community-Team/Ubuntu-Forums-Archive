---
title: "Maybe it's time to give up on Ubuntu and Linux for audio work"
date: 2007-01-25
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-01-25
I've been struggling for almost 4 weeks trying to get Ubuntu, Audacity, and my M-Audio card to work together. Right now, I can record but have no software control of the levels. I can playback but only have individual channel control in the Envy24 control with no ganging of the sliders and no level control whatsoever in Audacity. I've post here and on the Audacity forum but solutions don't seem to exist. I've spent hours at the ALSA site but haven't found a solution. Perhaps none exist. 

I have installed the ALSA drivers, Envy24control, and configured ALSA to use the M-Audio card. With all the various config files involved and the archaic commands, I have no idea where to start troubleshooting. Perhaps there is another distro better suited to audio work. I've had excellent results using Audacity with W98. I was hoping to leave the Windows world and hoping Linux would provide the door to do that. I'm not so sure anymore. 

Sorry for the rant. If anyone has any suggestions, I'd be glad to hear them. I'm willing to keep trying for a while but the frustration level is rising.

---

### Post by Unterseeboot_234 on 2007-01-25
I too spent some time trying to configure a soft synthysizer so I could convert .wav into .midi. This is trivial in java using Java Media Foundation API. Not so trivial in Linux. I have read articles about heavy-duty audio work stations, however, those setups are dedicated hardware/custom software.

You might try [URL="http://linux-sound.org/one-page.html"]
**Linux and Sound**[/URL]

I was looking for a software for you, called something like Studio64. My gripe was it was a live CD, not part of a running Linux desktop. Or, you can do like I did, set the project on the back burner and wait for Ubuntu Studio, supposedly coming out April 2007.

---

### Post by f_s on 2007-01-25
Hi

I'm also about to dump the whole Ubuntu thing.

Seems like not even simple CD ripping/mp3 functions do run smooth,a s all my mp3 files are having partial "errors" (noise and crackel) .

Frustrating.

Sorry for not being able to tell anything usefull. 

F

---

### Post by Patrick K on 2007-01-25
> **Unterseeboot_234 said:**
> .

You might try [URL="http://linux-sound.org/one-page.html"]
**Linux and Sound**[/URL]

I was looking for a software for you, called something like Studio64. My gripe was it was a live CD, not part of a running Linux desktop. Or, you can do like I did, set the project on the back burner and wait for Ubuntu Studio, supposedly coming out April 2007.

Thanks for the link. A lot of links to info. I'll have to peruse them. I've bookmarked it and will spend some time there.

Ubuntu Studio might be good to check out. Since I can still use windows for recording, I could wait for it. I hope the first version isn't plagued by bugs. 

OpenSUSE has been suggested as a viable distro for audio work. I don't know if that is so. I looked at Novell's OpenSUSE page and it seems much more oriented to standard productivity apps (word processing, spreadsheets). 

I sure would like to get the M$ yoke off my neck :). Although, I must admit, W98 has work great for me for many years.

---

### Post by zirconx on 2007-01-25
I've been having audio problems, too.  Playing music gets all choppy when I try to do anything else while its playing.  I think I'm going to try an Apple next.

---

### Post by kebes on 2007-01-25
Although this doesn't solve your problem right yet, you may be interested to know that a new variant of Ubuntu, called "Ubuntu Studio" is being worked on:
[http://ubuntustudio.org/](http://ubuntustudio.org/)

It will (reportedly) include a kernel optimized for real-time sound work, and have all the best packages for audio/video editing installed and configured properly.


Like I said, this doesn't solve your problems in the short term, but at least it shows that there are others interested in optimizing Ubuntu to be a better OS for serious audio work.

---

### Post by Tux Aubrey on 2007-01-25
Have you looked into a distro optimised for multimedia - I intend checking out [dyne:bolic ]("http://http://www.dynebolic.org/") myself.  Looks interesting.

---

### Post by Patrick K on 2007-01-25
> Have you looked into a distro optimised for multimedia - I intend checking out dyne:bolic  myself. Looks interesting.
I haven't yet but I plan on it. I'm going to quit trying to get Ubuntu to work for the time being. Ubuntustudio looks interesting but is a ways off. 

BTW, the link you posted doesn't seem to work.

---

### Post by Tux Aubrey on 2007-01-26
Link to dyne:bolic:

[http://www.dynebolic.org/](http://www.dynebolic.org/)

(user error)

(damn that stupid user!)

---

### Post by damu on 2007-01-26
Using linux myself for audio production, I gave my 2 cents [here]("http://www.ubuntuforums.org/showpost.php?p=2048788&postcount=5") and [here]("http://www.ubuntuforums.org/showpost.php?p=1937993&postcount=2").

---

### Post by Patrick K on 2007-01-26
> Using linux myself for audio production, I gave my 2 cents here and here.
Thank you for your thoughts. I read your post. Very interesting. I'll take a look.

> [http://www.dynebolic.org/](http://www.dynebolic.org/)

This is very interesting. I'll give it a try. I like that it doesn't need to install to it's own partition to run. 

I'm making a list, and checking it twice, of the suggested OS to try. 
So far:
Ububtu studio
64 Studio
Studio to Go
Dyne:Bolic

Any others?

---

### Post by christhemonkey on 2007-01-26
Jacklab [http://jacklab.net/](http://jacklab.net/)
64studio [http://64studio.com/](http://64studio.com/)
Dyne:Bolic [http://www.dynebolic.org/](http://www.dynebolic.org/)
Demudi/Agnula [http://demudi.org/](http://demudi.org/)
Planet CCRMA [http://ccrma.stanford.edu/planetccrma/software/](http://ccrma.stanford.edu/planetccrma/software/)
Musix [http://musix.org.ar/en/](http://musix.org.ar/en/)

Are the dedicated audio distros i know of.

and soon ubuntustudio will join them ([http://ubuntustudio.org/](http://ubuntustudio.org/))

---

### Post by Patrick K on 2007-01-26
Thanks, I'll add them to the list.

---

### Post by Patrick K on 2007-01-26
I downloaded the dynebolic iso and ran it. I looks like it will need a bit of configuring. The screen was wacky with the provided drivers and I wasn't able to get my M-Audio card working. The AC'97 worked fine. I didn't try any apps yet. I'll do some research, hopefully there are solutions to these problems.

---

### Post by Patrick K on 2007-01-28
Re: Dyne:Bolic. This is a pretty screwy OS. I "nested" it (that is provided it a place on my HD to store configuration files) but it doesn't seem to use them. All the config changes I made were gone on the next bootup. I ran Ardour, which comes with it, and was able to record and play back. However, the screen resolution was so far off that it was difficult to work with. Plus I had to reconfigure Jack every time I started Ardour.

I also installed Ardour on Edgy. It runs well but I really need a tutorial. I did a net search but didn't turn up any usable ones. Most concerned using hydrogen, whatever that is. Nothing that explained the various controls. There isn't much on the Ardour site. 

I installed Jokosher ([http://www.jokosher.org/](http://www.jokosher.org/)) and it doesn't seem quite ready for the big show. It does look to have potential, being simple and somewhat like Audacity. I haven't yet been able to record since it says I need another file which doesn't seem to be on Jokosher's site. Oh well, I posted on their forum but the last post was a week ago, so I might be uninstalling it if I don't an answer in a few days. 

On to the next test subject.

---


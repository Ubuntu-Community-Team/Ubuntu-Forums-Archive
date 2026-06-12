---
title: "Change sound managers in Lubuntu?"
date: 2014-09-22
forum: Multimedia Software
---

### Post by Mike_Walsh on 2014-09-22
I think this is the right forum to post this; if not, admins, could you please move it? Thanks.

I'm running 3 distros; Ubuntu, Zorin's Core OS 9 (based on Trusty), and Lubuntu.

Ubuntu and Zorin both use the Pulse Audio sound manger; I like it, because it's quite progressive, and volume steadily increases as you move the slider up the scale.

Lubuntu uses the Alsa sound mixer; and while I'm happy with it (no problems of any kind), it's not as progressive. You tend to have to be in the upper 20% of the scale before you get much in the way of volume, and from that point on, it tends to increase all of a sudden; requires quite a light touch on the mouse while you're adjusting it.

Is it possible to replace the Alsa sound mixer with the Pulse Audio sound manager; and if so, how would I go about it? I know Lubuntu's a lightweight distro, but I'm using it on what, for 10 years ago, was a top-of-the-range 'rig'; and, as such, I don't mind adding a little bit of weight to the system.

Any advice would be appreciated...thanks.

Regards,

Mike.

**Edit;** having just looked in the Software Centre, is it as simple as installing the Pulseaudio manager, and the system tray applet? If so, how do I remove the Alsa sound mixer; can it be done without upsetting the rest of the system?

Really, I just need some advice as to whether this is possible (should be easy enough, if it's simply a case of removing, then replacing), as I don't really have the time to spare at the moment to re-install, if I should happen to break it..! (Funerals, and various other family-related stuff looming just over the horizon...(!)):rolleyes:

---

### Post by Dennis N on 2014-09-22
You don't uninstall any alsa packages. You just install the packages **pulseaudio** and **pavucontrol** and it will be working.

---

### Post by ajgreeny on 2014-09-22
That is what I did when I installed Lubuntu 12.04 and also now 14.04.
Both work very well.

---

### Post by Mike_Walsh on 2014-09-22
Thanks for replying, Dennis. THAT was quick...(!)

It's as simple as that, is it? Hmmm; sounds fairly straight forward, then. I take it that can be done via the terminal, yes? I'm starting to find it's so much quicker AND easier for doing a lot of stuff, I must admit. (Never thought I'd hear myself saying that a few months ago; my days of using MS-DOS command line stuff was a LONG time ago, and I got fat & lazy, doing things the Windows way...;))

Do I need to replace the systray applet volume control, or does the installation replace it? I can't be the only one to have noticed the afore-mentioned 'quirk' with the control....

(BTW; thanks for the tip about moving the wallpapers with root permissions; works really well!) 

I started off using Ubuntu ALL the time; but I'm finding myself using Lubuntu more & more these days.....I DO like it. :D


Regards,

Mike.

---

### Post by Dennis N on 2014-09-22
You don't need to change anything. The panel volume control still works normally. Now you also have pulse audio volume control available from the applications menu for more functionality during playback or recording.

Install by terminal or Synaptic Package manager. Several other packages will be automatically installed with them.

---

### Post by Mike_Walsh on 2014-09-22
> **Dennis N said:**
> You don't need to change anything. The panel volume control still works normally. Now you also have pulse audio volume control available from the applications menu for more functionality during playback or recording.

Install by terminal or Synaptic Package manager. Several other packages will be automatically installed with them.

Well, that was easy. Installed via terminal:-

```
sudo apt-get install pulseaudio pavucontrol
```

Works really well, too. The systray volume control's much more progressive now, and it's nice to have the functionality of the other PulseAudio stuff back, as well.

Cheers, Dennis. As always...you're a star. Kinda hoped YOU'D answer this one..! ;)

Much appreciated. I'll mark this as 'Solved'. Good on yer!


Regards,

Mike.

---

### Post by Mike_Walsh on 2014-09-22
> **ajgreeny said:**
> That is what I did when I installed Lubuntu 12.04 and also now 14.04.
Both work very well.

You're right, AJ. It DOES work very well...I'm quite chuffed! I'm at the 'fine-tuning' stage now; I've got all the installs & big stuff sorted out, and I'm just getting things exactly how I like them, these days...

Regards,

Mike.

---

### Post by Dennis N on 2014-09-22
Thanks...happy to be of help.

---

### Post by Mike_Walsh on 2014-09-22
I've always liked background music when I'm working; I don't think I'm alone in this respect, neither. I listen to Smooth Jazz on RadioTunes quite a lot (what used to be Sky.fm). It's always been a bit of a juggling act; there's the volume control on the speakers; the volume control on the system itself, and THEN you've got the volume control on the site's music player, too. Before we sorted this out, I was having to set the site's volume fairly low. and then carefully set the system volume JUST right, before re-adjusting the site's volume to where I wanted it...

I can now set the speakers halfway, leave the site's volume where it is by default (halfway), and I can make all the adjustments on the system control, since it's easier to operate with PulseAudio installed.....MUCH better!

Thanks again.


Regards,

Mike.

---

### Post by ajgreeny on 2014-09-23
If you listen to online radio a lot, and would like a small radio player which sits in your system tray, install **radiotray** from the repos.  It's a great little utility that takes no screen space, but can be configured to play just about any radio station you want.

---

### Post by Mike_Walsh on 2014-09-24
Thanks for that, AJ. I'll have a look at it.....and if it's in the repos, I'm guessing it's been 'vetted'; so should be reasonably good, yes?

I'll let you know how I get on with it. Cheers!

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-09-24
VERY neat little player, AJ; nice one!

It's far less of a resource hog than if I play directly from the websites themselves.....something like 60 or 70% less, in fact; an important factor with a single-core processor. Though, in all fairness, I've yet to find anything running under Linux that my old Athlon WON'T handle.

XP used to be a WHOLE different ballgame; compared to Linux, Redmond stuff wants so MUCH in the way of resources before it will condescend to get off its posterior and actually DO anything..! :rolleyes:

It's yet another reason why I have absolutely no intentions of ever returning to Windows. Why should I, when there's so much good stuff to play with, running Linux? ;)

Thanks, AJ; appreciated.

Regards,

Mike.

---

### Post by Mike_Walsh on 2014-09-24
I'm probably in danger of going off-topic with this; but does anybody use Radio Tray?

I'm wondering how you add/change stations on it. I knew the pre-programmed Sky.fm URLs wouldn't work, since they've now become RadioTunes; but it doesn't appear to be as simple as merely editing the URLs in 'Preferences'.

Everytime I try that, I get this message coming up on-screen:-

[ATTACH=CONFIG]256648[/ATTACH]

Mean anything to anybody?


Regards,

Mike.

---

### Post by ajgreeny on 2014-09-24
Well I certainly use radiotray, but not for sky.fm.

Having looked it seems that sky.fm use flash for the audio which radiotray will not play, but a search seems to suggest you can register free to Radio-tunes and maybe get a stream that radiotray will play.
[http://www.radiotunes.com/settings](http://www.radiotunes.com/settings)

I will leave you to look into that in more detail; I am not going to register with something I don't need just to find that out.

---


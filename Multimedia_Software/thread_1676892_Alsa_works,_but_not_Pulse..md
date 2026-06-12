---
title: "Alsa works, but not Pulse."
date: 2011-01-27
forum: Multimedia Software
---

### Post by mightyball on 2011-01-27
I've been beating my head against this for months. Read dozens of threads, tried many things, gone through the "Troubleshooting PulseAudio" thread, reinstalled, nothing seems to fix it.

This is a fresh install of 10.10 (although I had the problem on 10.04 as well). I have installed MythTV on here (via apt-get, its not MythBuntu), and use the system primarily for that. Myth works great, sound in everything, no problems. 

However, not much else can play sound. Firefox (youtube), totem, mplayer, all nothing. Either just no sound or crash. If I can set them to use Alsa (eg: VLC), then they work. 

System is an [Asus P5B]("http://www.asus.com/product.aspx?P_ID=YwIVDOTcvIMHZdTy") and on-board sound. I've also got an Nvidia GT210 and would like to use the HDMI out, but can't get anything at all to go through this. Don't know if thats related or not. Sound problems existed before adding the GT210.

One strange thing is, I can go into Preferences -> Sound -> Hardware and click "Test Speakers". Of course nothing plays. However, if I then set the onboard card to "Off", and then back to "Analogue Stereo Duplex", then click "Test Speakers", the left speaker works (right is still silent). But from then on, Pulse apps can play sound, until next reboot. Having FF open on a youtube video or something similar prevents Myth from playing sounds however.

What can I do to get sound working sanely? I don't need optical out, surround or anything. Simple stereo will be fine at this point, via either the onboard or the GT210.

---

### Post by lidex on 2011-01-27
See this thread for hdmi:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
For pulse:
[http://ubuntuforums.org/showpost.php?p=10129602&postcount=9](http://ubuntuforums.org/showpost.php?p=10129602&postcount=9)

---

### Post by mightyball on 2011-02-02
> **lidex said:**
> See this thread for hdmi:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)
For pulse:
[http://ubuntuforums.org/showpost.php?p=10129602&postcount=9](http://ubuntuforums.org/showpost.php?p=10129602&postcount=9)

Thanks for the reply. I will have to give the HDMI stuff a try soon. The pulse link however is basically the opposite of what I needed (pulse was not working, so putting myth on pulse would result in my only functioning app breaking as well).

However! I seem to have fixed it. I installed the latest nvidia drivers (270.18 beta) from a PPA, and now pulse works in all apps! So it appears that something in the nvidia drivers was interfering with sound.

---


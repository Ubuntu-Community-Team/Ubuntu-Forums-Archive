---
title: "Alsa Isn't Working With Intrepid, Need Solution For Sharing Sound W/Different Apps"
date: 2009-02-06
forum: Multimedia Software
---

### Post by HotDogBunToo on 2009-02-06
Well everytime I try testing Alsa in System->Preferences->Sound I kept getting an error saying
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

Kept getting the same thing for PulseAudio and after reading that PulseAudio is a wrapper for Alsa for sharing sound with it I got rid of it to make sure it's just ALSA getting this error and perhaps just get ALSA working first at the very least

Don't get me wrong, I am getting sound since everything eventually outputs fine in OSS, but my main issue is sharing sound and having to close one/several app(s) sometimes so another app can use the sound since OSS has it's hangups with this between Amarok, Firefox (flash pages), VLC, and Totem Movie Player along with my virtual machines (VMWare & VirtualBox).  Any combination of the two is sure to yield a conflict of "Sound device is busy, another app is using it" or something of this effect.  

[Thus I tried reinstalling Alsa]("http://ubuntuforums.org/showpost.php?p=5277136&postcount=1") with no change from the error message and my ultimate goal is to eventually get my sound being able to tap into my integrated sound device with no conflicts, any ideas?  I THINK going the PulseAudio is a possible route since I hear that it's able to allow many apps to access it with little/no "sound device is busy" annoyances - but with crappy ALSA not working for me & it uses that how can I do this?  Can it use my working OSS output instead?

---

### Post by markbuntu on 2009-02-06
Pulseaudio is not a wrapper for alsa. It is a replacement for the alsa sound server that uses the low level alsa hardware drivers directly. ALSA replaced OSS so, if you are using OSS, you are really using a alsa oss wrapper with little of the functonality of either alsa or pulseaudio. 

Unfortunately Ubuntu did a terrible job implementing pulseaudio but that can be fixed so pulseaudio works the way it is supposed to.

If you want to get your sound configured properly go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you need more help or want more information go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Do not forget to look in the links.

---

### Post by HotDogBunToo on 2009-02-07
Hey markbuntu

Thanks for the detailed writeups, was following much of what you said with a few snags & hiccups then suddenly missed one part of what you wrote (and goofy me I had read your tutorial before & didn't follow this one specific step since it looked too simple to work lol - silly I know :( )

**"One easy way that some people have fixed their sound problems is by creating a new user in System/Administration/Users and Groups and then logging in with that"**

Turns out that doing this ALSA & Pulseaudio is working like clockwork for the new user.  Soooo now that it's just a matter of user config files, any idea what config files I should carry over to old user?

p.s. you don't have to respond to this thread since I also reposted this reply to the other thread as u requested, I'll just post in here & edit as Solved when this is figured out - thanks.

**_EDIT_**

Since new account works just the way I want it to, I just moved my documents & useful config files (firefox history, bash history, etc.) from old account's home directory to this new one lol.  Was too lazy & impatient to figure out which config file was which so moving everything makes this from a work around to a solution.  So for anyone stumbling across this problem in google - markbuntu's advice is useful, ESPECIALLY the bit of information concerning creating new account lol.

---


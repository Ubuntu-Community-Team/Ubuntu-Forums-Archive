---
title: "no sound in certain applications"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by qiemem on 2007-01-04
Hi,
Just installed edgy on an old Compaq Presario. Everything is working surprisingly well except for certain sound issues. While system sounds and music from say Rhythmbox works fine, I get no sound from games, amarok, or flash videos. Flash works great except for sound (installed flash 9 via .deb provided by Adobe). 

Now note:
```

$ lspci|grep audio
00:03.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
00:14.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)

```
As you can see, I have to sound cards on board. To get sound to work at all, I had to go into system->preferences->sound and change all the devices from Autodetect to YMFPCI (the Yamaha sound card). Changing to ALSA, OSS, ESD, etc eliminates sound altogether. 

I feel like there should be a pretty straight forward solution to this. I simply have to tell ALSA and xine (for amarok) which soundcard to use. Or at least that's what I've been thinking. I just don't know how to do that, or if I'm on the right track.

Anyway, help would be very appreciated. This is my sister's computer and flash is kind of essential to her. So ya, help me convert her to Linux!

---

### Post by sgx on 2007-01-04
Try installing alsaoss, a wrapper program letting alsa
use oss things...some apps still default to OSS, if still no luck in general, pick the better of the two cards, get it working with everything, then add the second one back in, if you really love pain, or have a great need, and see if it is picked up in configuration programs that show the first one is really there...and google for example...
alsa xine problem "multiple soundcards" 

replace xine with app  of your choice...hope this helps...

---

### Post by qiemem on 2007-01-05
Thanks sgx! Installed alsaoss and everything started working immediately. Games, amarok, flash, everything.

I should note that I also changed that FIREFOX_DSP in /etc/firefox/firefoxrc to aoss instead of auto. So if anyone has similar trouble, follow these steps.

1) open up terminal and enter:
```

gksudo gedit /etc/firefox/firefoxrc

```
change "auto" (or "none" or whatever it is) to "aoss". Save it and quit.

2) go back to terminal and enter:
```

sudo aptitude update
sudo aptitude install alsaoss

```

This worked for under edgy, using flash 9 beta 2.

---

### Post by sgx on 2007-01-06
Great that its working...I see others in other forums give that advice,
so  I am just a noisy, if sometimes useful, sqawking parrot...
awk!  alsaoss! awwkkk!!!
Have a great 2007!

---

### Post by qiemem on 2007-01-08
The sounds gone out again, exact same problem. 

Looking at packages, it appears as though there is no "aslaoss" package, though I'm sure I installed it the other day. It's even in my terminal history. There is a package called alsa-oss which I have installed, but no alsaoss. Plus, I have no trace of alsa-oss in terminal history.

I can't understand why the sound would go out after working fine. Any ideas?

---

### Post by moeFinley on 2007-01-14
Weird.  For me the package is called alsa-oss.  Does the sound work if you install alsa-oss?

---

### Post by qiemem on 2007-01-14
I could just be misremembering. Who knows. Ya, I do have alsa-oss installed.

So I've learned a bit more about the problem. Sometimes its there and sometimes its not. Whenever I turn on the computer, I'd say there's about a 1 in 3 chance that I'll have sound. As far as I can tell, its random. Once its on, its on for the whole session. Even if I log out and log back in... Actually I think I might remember a couple times when it went after logging out of one account and logging back in to another, but I can't be sure... Anyway, I have no idea what could be causing on this. Any ideas?

---

### Post by moeFinley on 2007-01-14
A great way to specify the output is to create a  */etc/asound.conf*  file.  I'm not 100% how to do this but I think it's something like this.  There is a [great guide here]("http://alsa.opensrc.org/.asoundrc") if it's not.

```
pcm.card0 {
  type hw
  card 0
}

pcm.!default {
  pcm "hw:0,0"  #this points to sound card 0 device 0 (other devices for example could be optical out
}

#  aplay -l  will show you which cards which
```

This is what I'm using at the moment which get Skype working for me

```
pcm.card0 {
  type hw
  card 0
}

pcm.dmixer {
  type dmix
  ipc_key 1025
  slave {
    pcm "hw:0,2"
    period_time 0
    period_size 2048
    buffer_size 32768
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.skype {
  type asym

  playback.pcm "dmixer"
  capture.pcm "card0"
}

pcm.!default {
  type plug
  slave.pcm "skype"
}
```

---


---
title: "daemon takes audio for himself, can't play audio"
date: 2009-03-02
forum: Multimedia Software
---

### Post by renebs on 2009-03-02
Hi,

I have installed speech-dispatcher on my UBUNTU 8.10 box just to use the command "spd-say SOMETHING"

However, after rebooting I found I can't hear audio files anymore. What I mean is the following (with the speech-dispatcher running)

Running: 
$mpg321 music-file.mp3 

Does not produce "audio" output

However, if I run:
$sudo mpg321 music-file.mp3

I do get audio output. 

If I do a SUDO KILL speech-dispatcher I can play audio normally. 

Following some other thread I have added (at least I think I did) my name to the pulse group and still that hasn't worked (for me). 

Thanks for reading. If you any suggestion in how to solve this problem please give a reply.

P.S: I have added the resulst of aplay -l and lspci -v

---

### Post by renebs on 2009-03-02
Hi,

I also noted another feature of Ubuntu 8.10 (I was using 6.10 for a long time and now, new computer = new fresh install of ubuntu)

I use MPD to listen to music in my computer. If I do a LOG-OUT of Gnome, and try to hear music in another "session/(vt2 is my preferred one  (CTRL+F2) the audio won't work!

Can anyone try to explain what is wrong here?

---

### Post by markbuntu on 2009-03-03
There have been some big changes in the ubuntu sound scheme since 6.10. For one thing the daemons are no longer allowed to run systemwide with root privledges unless you tell them to explicitly so the daemons exit when you log out.

You also need to explicitly allow access to sound services for your users and root.

---

### Post by renebs on 2009-03-03
> **markbuntu said:**
> There have been some big changes in the ubuntu sound scheme since 6.10. For one thing the daemons are no longer allowed to run systemwide with root privledges unless you tell them to explicitly so the daemons exit when you log out.

You also need to explicitly allow access to sound services for your users and root.

Thanks. Some of these changes I noted (not that I knew how things worked before with detail...). This issue with the group I had noted before (I followed [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) this before). 

Do you think I should be in the same group as speech-dispatcher? Or something of that sort?

---

### Post by markbuntu on 2009-03-03
From looking at the OP you are definitely having some sort of permissions issue. Speech dispatcher may be running as root so check its permissions too.

You can try creating a group "audio" and making your user and root members though supposedly that is no longer necessary. Also, you need to be a member of all the pulse groups

pulse
pulse-rt
pulse-access

can you see speech dispatcher in the pulseaudio volume control when it is running?

---

### Post by renebs on 2009-03-03
> **markbuntu said:**
> From looking at the OP you are definitely having some sort of permissions issue. Speech dispatcher may be running as root so check its permissions too.

You can try creating a group "audio" and making your user and root members though supposedly that is no longer necessary. Also, you need to be a member of all the pulse groups

pulse
pulse-rt
pulse-access

can you see speech dispatcher in the pulseaudio volume control when it is running?
First thanks much for helping out here.

So my user is on those groups, take a look:

```
$ groups myusername ; groups speech-dispatcher
myusername adm dialout cdrom audio dip video plugdev scanner fuse lpadmin pulse pulse-access pulse-rt admin sambashare vboxusers
audio

```


Remember that if I reboot (since speech-dispatcher is on /etc/init.d) I have no audio. 

I kill it, log-out, login I can play music (right now using MPD for instance). So, following your suggestion I did:

```
 sudo /etc/init.d/speech-dispatcher start
[sudo] password for myusername: 
 * Starting Speech Dispatcher speech-dispatcher                                 
[Tue Mar  3 17:37:58 2009 : 803667] speechd: Speech Dispatcher 0.6.7 starting
[Tue Mar  3 17:37:58 2009 : 804736] speechd: Directory .speech-dispatcher not found in home
                                                                         [ OK ]
myusername ~/private/papers/stochastic_games/continuum of players $  pg speech-dispatcher
myusername     19094  0.0  0.0   3236   784 pts/0    S+   17:38   0:00          |               \_ grep speech-dispatcher
114      19086  0.0  0.0  11468   696 ?        Ssl  17:38   0:00 /usr/bin/speech-dispatcher
myusername ~/private/papers/stochastic_games/continuum of players $  spd-say testing
```

So, there is also another part of the result (of the above experiment) which is: did speech-dispatcher appeared on PulseVolumeControl? Yes it did. 
However, the speech-dispatcher did not say testing. It said a long sentence complaining about some configuration. Note that this doesn't happen from a fresh start. That is speech-dispatcher works fine without any error...

Oh, and also, starting speech-dispatcher after (killing-it+logout+login-again) does not "break" the audio system. That is, I can still use the audio. 

I am still clueless. I did look for any know bug with speech-dispatcher or configuration error and haven't found any...

---

### Post by markbuntu on 2009-03-03
Well then, maybe you should remove speech dispatcher from starting at /etc/init.d and have it start from login. Or if you really need it to start at boot, closing that instance (which seems to be running as root) and starting a new user instance after login.

I am not really up on this speech dispatcher thing but that is how it looks to me.

I can see how that would be very handy for the visually impaired, but applications should not generally be running as root in userspace.

---

### Post by renebs on 2009-03-04
Thanks. 
That's what I was planning as a backup. But one question, if I use the updaterc.d remove command (to take out the speech-dispatcher inicialization script) what should I add to the "at login startup" in gnome?? Just a link to the binary file speech-dispatcher or should I copy the script to another place and run at at log-in only?

---

### Post by markbuntu on 2009-03-04
It depends on what the init script does. If it sets some operating parameters then you should run it at login instead of just calling the binary.

---

### Post by tuvw014 on 2009-03-04
[Ed Hardy Clothing](http://www.ed-hardy-shirts.com)
[cheap Ed Hardy clothing](http://www.ed-hardy-shirts.com)
[Ed Hardy shirts](http://www.ed-hardy-shirts.com)[cheap ghd hair straighteners](http://www.hairstraightenersstore.co.uk)
[ghd hair straighteners](http://www.hairstraightenersstore.co.uk)

---

### Post by Dr.Suave on 2009-03-05
Try going to system > admin > users and groups, selecting your user, clicking properties, then navigating to the "user privileges" tab and see if you're being denied access to audio devices or something similar.

You could see what privileges root has as well, but it sounds like root's not having any problems with accessing audio.

---


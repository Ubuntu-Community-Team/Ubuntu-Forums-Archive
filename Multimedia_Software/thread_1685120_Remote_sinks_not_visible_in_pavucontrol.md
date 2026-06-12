---
title: "Remote sinks not visible in pavucontrol"
date: 2011-02-10
forum: Multimedia Software
---

### Post by alexbj on 2011-02-10
Hi,

Haven't found a solution to this and hope I've researched properly.

So, I've to machines running Ubuntu 10.10. One of them (a htpc) shares its local pulseaudio sinks, and I want the other (a laptop) to direct its audio to it.

So, on the htpc, I've ticked "Enable network access to local sound devices" in paprefs. On the laptop, I've ticked "Make discoverable PulseAudio network sound devices available locally".

The result is that, in padevchooser and pabrowser, the laptop sees the remote sinks. However in pavucontrol they are not visible. If I set one of the remote sinks as default in padevchooser, local applications (tried totem, vlc and spotify) cannot play audio.

Any ideas?
Thanks,
Alex

---

### Post by alexbj on 2011-02-10
OK it turns out the line 
```
#load-module module-native-protocol-tcp
```
in /etc/pulse/default.pa was uncommented from previous attempts. Commenting out that line again (as the instructions say to do when using paprefs) made the remote sinks visible in pavucontrol. 

Now, selecting remote sinks does not stop applications from playing audio, but unfortunately there is no sound on the remote machine. I am sure that the local sound works there, on the selected sinks, as tested with e.g. mpd.

Other ideas?
Alex

---

### Post by alexbj on 2011-02-10
New development... I reinstalled pulseaudio, noted that the remote output channels are muted by default in pavucontrol, umuted them and... voila! 

I guess the lesson is that manually loading module-native-protocol-tcp in /etc/pulse/default.pa messes things up if you use paprefs. People probably knew this, though, so sorry for cluttering the forum.

Alex

---

### Post by runesvend on 2013-01-09
I can't get this to work in Ubuntu 12.04/13.04. I've enabled Network Access and Network Server in paprefs on both computers, but a remote sound card doesn't show up in pavucontrol.

---

### Post by overdrank on 2013-01-10
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


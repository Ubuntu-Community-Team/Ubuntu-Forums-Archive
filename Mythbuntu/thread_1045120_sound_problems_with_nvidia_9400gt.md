---
title: "sound problems with nvidia 9400gt"
date: 2009-01-20
forum: Mythbuntu
---

### Post by orduek on 2009-01-20
Hi,
I added Nvidia 9400GT to my Mythbuntu 8.10 computer. I connect it through DVI to my TV.
But, since then I have no sound (through regular motherboard sound) and I have static on my TV.
My guess is that the new card trying to send sound through HDMI, and hence, aborting the normal sound card.
how can I solve this one?

---

### Post by orduek on 2009-01-21
does anyone experiecned this?
I'm thinking maybe something wrong with the card itself (hardware)?

---

### Post by enchesss on 2009-01-21
not really sure but:

Have you connected the sound cable from the motherboard to the video card?

if so

there have been some people complaining about the fact that some tvs do not like HD sound even though they have good HD res.

Even some expensive HDTVs wont play HD sound through the HDMI and you have to use a separate stereo.

Does your tv have HD sound capability?

---

### Post by orduek on 2009-01-21
I didn't connect the sound cable from motherboard to the graphic card.

When I load the OS using the integrated graphic card the sound is good (thourgh normal ac97 sound that goes to a reciever).
The problem appears only when I load the OS through the Nvidia card.

looks like I need to blacklist some Nvidia sound thing somewhere or something like that.

---

### Post by orduek on 2009-01-21
guys, any ideas?
someone else has a 9400gt?
I need to know if its the card, maybe something in the BIOS setting I should change.
Am I missing something here?

---

### Post by orduek on 2009-01-22
I saw something on an option to disable HDMI sound from graphic card using specific EDID - but the explanation is to windows users.
Any isea how can I do it with mythbuntu?

---

### Post by fryed_1 on 2009-02-01
I have a 9800gt and got the same problems.  My only option to get sound through the TV was to use the SPDIF internal cable.  It plugs into the mobo and vid card to allow sound to pass through.

It's actually Nvidia's drivers that cause this problem.  If the GPU supports the SDPIF passthrough, then it will set it to do it automatically and there is no known way to turn it off easily.  You can verify this is the problem by uninstalling the Nvidia drivers, and sound "should" come back.

---

### Post by jyavenard on 2009-02-01
I have the exact same issue with the 9400GT, and I also read about people with similar issues on the nvidia forum. So I don't think this is a faulty card.

My setup is as follow:

9400GT -> DVI -> HDMI -> TV
  \------ Analog sound -> TV --> Amplifier -> speakers

(my TV allows on one input video on hdmi and sound on analog)

I had the same setup earlier with another video card. No problem I would get sound on the TV and amplifier.

Since I've switched to the 9400GT, the TV (Sony Bravia LCD) will display a message about unknown sound input (or something to that extent)... And because of this will not accept the analog sound input.

I'm not sure how the video card could output sound on the DVI output but it does !!!
The 9400GT doesn't let you connect it to the internal SPDIF connector.

---

### Post by orduek on 2009-02-02
Finally I find some companions in my problem.
It causes me to stay with my motherboard graphic card which has its own problems.
any chance of fixing it?

---

### Post by orduek on 2009-02-03
The Support of INNO3D said its probably a faulty firmware and I need to change the card.
I'll try that and let you know.

---

### Post by orduek on 2009-02-15
after replacing the card to tnother 9400 GT - same problem.
how can I solve this one? the card is unusable.

---

### Post by denmich1997 on 2009-03-01
How did you get your 9400 to show up.  I've fresh installed and everything else I can think of.  right now running in 800x600, that's all that is available.  What drivers are you using.

---

### Post by orduek on 2009-03-02
I'm still unable to work it out properly.
waiting for some help somewhere.

---

### Post by nickrout on 2009-03-02
The matter is dealt with comprehensively on the mythtv-users mailing list.

The nVidia graphics card sees via edid that the TV will accept audio over HDMI, so it puts an empty audio signal in the HDMI stream.

The TV sees the empty audio stream and thinks "I'm getting audio over HDMI, switch off the analogue input"

Hence you get no sound.

You need to use a custom edid that fools the graphics card into NOT putting the empty audio stream in, then the TV will accept analogue sound.

[http://www.gossamer-threads.com/lists/mythtv/users/373493#373493](http://www.gossamer-threads.com/lists/mythtv/users/373493#373493)

---

### Post by orduek on 2009-03-04
Thanx.
But, I think my problem is somhow little different.
especially because whenever I load my system from the Nvidia card, I can't get sound - even before installing the drivers and even when loading from VGA.
I get a "no sound device" in Mplayer.

---

### Post by kreegor on 2009-03-04
I had exactly the same problem. My old 8400gs died so I bought a 9400gt to use instead. I think it is a disaster card because after 3 or 4 goes at installing mythbuntu 8.10 and 8.04 I ended up getting another 8400gs.

---

### Post by orduek on 2009-04-04
any solution?

---

### Post by nasha on 2009-04-05
Nickrout, i think this may also be the cause of my current audio problem, as im also running a 9400gt via DVI > HDMI. Currently following the mythtv mailing list instructions

---

### Post by nasha on 2009-04-05
This indeed solved my issue, thanks for the info!

---

### Post by orduek on 2009-04-05
Nasha: can you explain how you sloved your issue?

---

### Post by nickrout on 2009-04-05
> **orduek said:**
> Nasha: can you explain how you sloved your issue?

read post #14 above.

---

### Post by orduek on 2009-04-13
looks like my problem has something to do with my BIOS settings.
I bought a new 8400gs and still has the same problem.
Which makes me think something's wrong with my setting in the bios.
I have a P5Q-EM motherboard (ASUS).
any advices?

---

### Post by orduek on 2009-04-13
OK I think I solved it. 
for future reference : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292743](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292743)
thats whats helped me:

open /etc/modprobe.d/alsa-base
add the line: options snd-hda-intel probe_mask=1
save and reboot.
works like a charm :)

---

### Post by orduek on 2009-04-15
OK, Hope that's my last problem.
I'm can hear sound through my analog sound but every now and then I get crackling noises from the TV, although I'm using the 8400GS and not the 9400.
Any idea as to why?

---

### Post by orduek on 2009-04-17
anyone?

---


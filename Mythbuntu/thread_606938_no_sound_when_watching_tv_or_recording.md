---
title: "no sound when watching tv or recording"
date: 2007-11-08
forum: Mythbuntu
---

### Post by h8train on 2007-11-08
my sound is on all the time, even when not in mythfrontend adn not recording. if I mute line in then no sound at all.  is there a fix other than just turning my speakers off?

Thanks

---

### Post by tgm4883 on 2007-11-08
Thats a common problem with software encoders.  Try muting the capture line

---

### Post by Zelgadis on 2007-11-08
If you're using the pcHDTV 5500, then you'll probably have to do what I did.  I removed the sound cable and had it capture sound directly from the card.  I also had to change the sound sample rate under recording profiles to 48000 instead of 32000 so that the sound wouldn't sound absolutely horrible.

If you're using a different card, then I'd assume that you're on your own.  I have yet to find any solution that didn't amount to simply muting the capture line and setting it to record.  I had asked for help on this same problem previously and got no reply.

---

### Post by tgm4883 on 2007-11-09
> **Zelgadis said:**
> If you're using the pcHDTV 5500, then you'll probably have to do what I did.  I removed the sound cable and had it capture sound directly from the card.  I also had to change the sound sample rate under recording profiles to 48000 instead of 32000 so that the sound wouldn't sound absolutely horrible.

If you're using a different card, then I'd assume that you're on your own.  I have yet to find any solution that didn't amount to simply muting the capture line and setting it to record.  I had asked for help on this same problem previously and got no reply.

Thats cause that is what you do.  The reason for the delay is that it is playing live audio, but the video is delayed because when you watch a program (even live tv) you are watching what has already been written to the hard disk.

---

### Post by Zelgadis on 2007-11-10
> **tgm4883 said:**
> Thats cause that is what you do.  The reason for the delay is that it is playing live audio, but the video is delayed because when you watch a program (even live tv) you are watching what has already been written to the hard disk.

I understand perfectly why the sound and TV don't sync.  I'm telling you that Muting the Line In does absolutely no good if MythTV is **not** capturing the sound.

After I found out I could capture sound directly from the card and not mess with the sound cable, I stopped bothering to figure out why I couldn't get MythTV to capture sound from Line In.

I found the following page to be helpful with getting the sound to work. [http://www.mythtv.org/wiki/index.php/PCI_TV_audio#Driver_Configuration](http://www.mythtv.org/wiki/index.php/PCI_TV_audio#Driver_Configuration)

Edit:  When I think back on it, I might have solved the problem with Line In not being captured by changing the audio device for the tuner in the back end setup.  I can't remember what I had set as the audio device back then.  This makes me think that maybe this guy didn't know to go into Myth Backend and edit the audio device for his tuner to match with his sound card in addition to muting Line In.  Even though this issue is listed in the wiki for Mythbuntu, it doesn't mention *anything* about going into Myth Backend.  I really think there should be something explaining about how to match up the correct device with the correct setting(/dev/dsp0,1,2,etc.).  It could be difficult for a beginner to figure out what that means and how to match it up with the correct device.  I always have to look in the sound mixer to figure out what number my devices were assigned to.  [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-6d34b9d499edd07bd0274db073efa1eed8c1067a](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-6d34b9d499edd07bd0274db073efa1eed8c1067a)

---

### Post by h8train on 2007-11-10
ok I don't mind turning my speakers off when not watching live tv (wich I never do on mythtv) but when I attempt to watch recordings through mythfrontend, i hear the live tv. So I mute line in and then when I watch recordings I have no sound like there was never sound recorded for the recording. I have a tvwonderpro tuner card and have a line comming out of my tuner card and into my onboard sound "line in". 

What other info can I provide for some help?
Sound works on my mythbuntu install.
Sound works when watching live tv if I have "line in" un-muted.
My recordings have no sound at all with line in un-muted or with it muted.
I'm not retarded but may have over looked somthing simple.
I am begging for help as I had a mythtv box running before on Fedora core 4 but a general Fedora update broke my mythtv install, and I basically never recovered.

I can do a regular install like I did before with fedora core 4 that worked but would like to have this "clean and simple" install of mythbuntu so I can benefit from having only what is needed with out all the BS.


Thanks for your help everyone.

*

---

### Post by h8train on 2007-11-12
<bump>

---


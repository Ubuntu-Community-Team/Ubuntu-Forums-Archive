---
title: "M-Audio Delta 44 Gui Mixer application"
date: 2008-10-02
forum: Multimedia Software
---

### Post by jukingeo on 2008-10-02
Hello all,

After all my troubles with sound devices in the past, I decided on buying an M-Audio Delta 44 on the basis that others stated that the card is normally automagically recognized and plays right out of the box.

I am happy to say that the M-Audio Delta 44 DID live up that expectation and I now finally have sound in Ubuntu Studio AND my other Linux applications as well (Puppy Linux).

However, I noticed one thing...the mixer (speaker icon on the taskbar) doesn't work.  It seems the audio applications control the output directly, but there is no control over the sound on a system level, unless I use the text based (Terminal) Alsamixer.   I don't want to use this thing.  I would like to have a mixer that I can select from the taskbar.  Thusfar I tried three gui versions of Alsamixer and none are working right.  Is there a specific gui mixer that I have to download in order to get full access to the Delta 44's in's and out's?

The M-Audio Delta 44 is a 4 input and 4 output audio device.  The "Jack" application does recognize this device as such and the applications that work with Jack do have control over the in's and outs.  I just don't have a gui mixer to control the system sounds.

Any suggestions?

Thanx,

Geo

---

### Post by noctrex on 2008-10-09
Hi, I'm interested in this soundcard as well, could you please tell me on what version you're using it on? k/ubuntu? hardy/feisty? 32/64bit?

I noticed you're using alsamixer for that, what graphical mixers did you try (gnome-alsamixer, gamix)?

---

### Post by jukingeo on 2008-10-13
> **noctrex said:**
> Hi, I'm interested in this soundcard as well, could you please tell me on what version you're using it on? k/ubuntu? hardy/feisty? 32/64bit?

I noticed you're using alsamixer for that, what graphical mixers did you try (gnome-alsamixer, gamix)?

I am using it on Ubuntu Studio Hardy, Puppy Linux 4.0, and the latest version of Dynebolic.  Yesterday I did a test run of OpenSuSE 11.0 and it works there as well.  So I guess it would be safe to say that it is truly Plug-N-Play for most Linux distributions.

The downside is that I have yet to find a gui mixer that I like that works with it.  The text based Terminal Alsa-Mixer is working the best right now, but I don't like it.  Most of the gui based mixers simply do not work.

I have been tipped off that that Envy24Control mixer MAY work, as that is a gui mixer designed for mix based sound devices.  I have not tried it as of yet, but I did notice that Ubuntu Studio does come with the Envy 24 Control mixer already set up.  So I am assuming that all I have to do is get my card to work with it.

So we will see how that goes.

Edit:  I just tried out the Envy24Control and it is working fine.  It takes a while to figure out how to set it up and most channels are muted right off the bat, so you would get a false sense that the application isn't working.  At any rate if you already have Envy24control set up, you just open it up and do this:

1) Click on the ANALOG CONTROL tab to bring up the analog controls to around 100 (all of them).
2) Click on the PATCHBAY ROUTER tab to bring up the controls to set up the patch bay.  Set HW out 1 and HW out 2 to Digital Mixer
3) Click on the Monitor PCM tab and look at the first two mixer control sets that are labeled PCM OUT 1 and PCM OUT 2.   This is where things get tricky.   The controls represent a stereo mix, however the output for each channel on the Delta 44 is MONO.  If you bring up both output together, you will get a PCM mono mix.  For stereo unmute the LEFT side of PCM OUT 1 and the RIGHT side of PCM 2, now you can bring up the stereo mix using the left control of PCM OUT 1 and the RIGHT control of PCM 2.

That should do it for the digital set up for a standard stereo output.  The only thing that I noticed that may be a shortcoming is that the channel 3 & 4 outputs of my Delta 44 can't be selected to the digial mixer output, but it does have direct PCM outputs.

The Monitor Input is self explanitory as that tab adjusts the input gain on the four channels.  I have still yet to try this, but at least at this point in time I have gui control of my levels.

As a final touch I dragged the Envy24Control icon in my start menu to the taskbar.  I then right clicked on the taskbar icon and chose to "Lock To Panel".  Hopefully it will stay there on next boot up.

So at least that takes care of sound control in Ubuntu Studio.   Now I am wondering if I can use Envy24Control in my other Linux distributions :).

Geo

---

### Post by likse on 2008-10-13
In my experince envy24control is the one and only way to go with the Maudio 44. It worked well on fedora a few years ago, as well as in Ubuntu recently. Takes a while to figure out, but on the other hand, the Maudio 44 isn't exactly your ordinary boring soundblaster 16bits either. You have some lovely music listening  ahead of you I think, just be patient and experiment with envy24control.

---

### Post by jukingeo on 2008-10-14
> **likse said:**
> In my experince envy24control is the one and only way to go with the Maudio 44. It worked well on fedora a few years ago, as well as in Ubuntu recently. Takes a while to figure out, but on the other hand, the Maudio 44 isn't exactly your ordinary boring soundblaster 16bits either. You have some lovely music listening  ahead of you I think, just be patient and experiment with envy24control.


Hello,

There are a few kinks I still have to work out with the Delta 44, but I find it actually sounds better in Linux than Windows.  Windows I still have a stuttering (distortion) problem with some games.   I have not tried the Delta 44 in Linux with games yet.  This time around I just loaded on the bare bones Ubuntu Studio and didn't load anything else on.   I knew I was going to update my video card around the same time I purchased the Delta 44.  So I wanted to make sure both installations took and work fine.   Luckily, this time around both the new video card AND the Delta 44 installed beautifully into Linux.  I had very little work to get the new ATI video card to work, and as I said above the Delta 44 was automagically recognized.

I know the Delta 44 isn't a Soundblaster 16...far from it.  Keep in mind I came from a Soundblaster X-Fi, which is no toy.  That card could go to 192k and had full DSP effects.  So the Delta 44 is a step down (in the context of using the X-Fi in Windows).  But the Soundblaster X-Fi requires a huge procedure to get to work in Hardy.  I DID get it to work though.  Despite the fact that I had a working X-Fi, I felt a bit short changed because I am still feeling out Linux distributions in general and the X-Fi didn't work in the other Linux distributions I have.  It is technically a 'forced to work' situation in Hardy as the X-Fi isn't really a supported Linux device.

However, the Delta 44 has been working in all of the distributions and applications I have tested thusfar.  The other day I even tried it in a Live CD version of OpenSuSE 11.0 (Red Hat) and it works there too.

I still have a ways to go to see how everything works.  In regards to Envy24Control...the big confusion lies in the patchbay/mute button configuration that Envy comes set up with.  Everything is muted and the patchbay is set up wrong.  A little reading and playing around with it got it working fine.

Even though I regard myself as above average in computers when it comes to Windows OS, everything was thrown out the window (pun intended) when it came to Linux.  So now if directions are slightly vague, I get thrown off.   That seems to happen a lot here.  Most Linux Gurus forget that there are many many newbies here and Linux is not really the most intuitive of operating systems...not by a long shot.   So simple grade school step by step procedures are a must.  What I am getting at is the the directions for setting up Envy could be much better (in addition to many other application set ups).

Now I would like to get Envy to work in Puppy Linux, but that was originally a Slackware based distribution and uses .pet packages.  Thusfar, I don't see an Envy package designed to work with Puppy.

The main reason why I am interested in Puppy is for I/O system control and some game systems such as MAME.  Puppy works extremely fast and I think it would be much better for me to use that as a base to run older arcade style games or control applications for a virtual organ project.  It's speed also opens the door to running Wine...which I believe would be much faster in Puppy than Ubuntu.

Ubuntu Studio I am using strictly as my 'housekeeping' OS and of course for DAW experimentation.

Windows XP I am mainly going to still use for audio critical work and of course games that will not run in Linux.

Geo

---


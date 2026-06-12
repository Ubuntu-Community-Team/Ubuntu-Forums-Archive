---
title: "Surround sound enabled...now stereo uses all channels"
date: 2009-04-10
forum: Multimedia Software
---

### Post by amrbekhit on 2009-04-10
Hello all,

I've spent today getting 5.1 surround sound to work in Ubuntu 8.10 after I installing Unreal Tournament 2004 and finding that there was no 3D sound.

Anyway, after searching around on the web I found [this link]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/") and have followed its instructions.

However, it's not quite right. In order to test the sound, I downloaded a 5.1 AC3 sound file from [this page]("http://www.lynnemusic.com/surround.html") and tried to open it up in Totem (I changed the sound preferences to 5.1), Rythmbox and mplayer but none of them could play it right - using the PulseAudio Volume Meter to monitor the sound I noticed that each channel was being played using a combination of front, rear and centre speakers, but not individually as should be. Also, when playing regular stereo files using these players, the sound is output to ALL channels, rather than just the left, right and LFE ones.

Running **speaker-test -c 6** and **speaker-test -Dplug:surround51 -c6 -l1 -twav** display correct behaviour.

However, what's weird is that if I open the directory with the sound file in Nautilus and then hover my mouse over the sound file to get an audio preview, the file is played perfectly!

My sound card is a Sound Blaster Live! 24-bit, embedded into my MSI K8N SLI Platinum motherboard.

Any ideas?

Thanks

--Amr

PS. I still can't get 3D audio to work in Unreal Tournament 2004, despite modifying the UT2004.ini file and setting 3daudio to true - it just output stereo sound. Any ideas on that?

---

### Post by amrbekhit on 2009-04-16
*Bump*

---

### Post by amrbekhit on 2009-04-24
*meep* help me...

Unfortunately, this problem persists even after upgrading my pc to 9.04 using the alternate cd installation method.

---

### Post by amrbekhit on 2009-05-05
Surely I'm not the only one on earth to use ubuntu, have surround sound AND have this problem. Even a 'I'm having this problem too!' post would be welcome...grumble...

---

### Post by BigPincer on 2009-05-11
Hi.. i have the same problem with an auzenteck xplosion dts (C-media 8770) on a fresh 9.04. 
Any idea ?

---


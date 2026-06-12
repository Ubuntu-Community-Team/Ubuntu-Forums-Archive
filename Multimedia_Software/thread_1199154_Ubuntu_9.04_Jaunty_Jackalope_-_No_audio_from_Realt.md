---
title: "Ubuntu 9.04 Jaunty Jackalope - No audio from Realtek ALC880 (snd-hda-intel)"
date: 2009-06-28
forum: Multimedia Software
---

### Post by Caiwyn on 2009-06-28
I've got fresh install of Jaunty, and I want to use the onboard sound from my motherboard.  The motherboard is a K8NGM2-FID from MSI Computer.  The chipset is nForce4, and the audio chip is a Realtek ALC880.  I am trying to use the S/PDIF output to my receiver.

The snd-hda-intel module is loaded, and I can see the controls in alsamixer.  I have unmuted the IEC958 control, which should control digital output via the S/PDIF connection.  There is also a IEC958 D control which was already unmuted.

I have gone into System->Preferences->Sound and changed all the playback and capture devices to "ALSA - Advanced Linux Sound Architecture."  Unfortunately I still can't seem to get any sound to come through.

Can anyone help me with this?

---

### Post by Caiwyn on 2009-07-01
Seeing all sorts of posts about sound problems with snd_hda_intel in Jaunty.  Has nobody figured out a way to get S/PDIF output working?

---

### Post by Caiwyn on 2009-08-01
I think my motherboard had its sound chip burned out.  I replaced it with a new board and things are working much better even though the sound chip is another Realtek ALC88x.

For those who haven't figured this out, here is how to get S/PDIF working on on these systems:

1. Click the sound icon in the upper right corner of the screen.
2. Click on the "Volume Control" button to open the Volume Control window.
3. Select the "Switches" tab.
4. Click the "Preferences" button to open the Volume Control Preferences window.
5. Check the "IEC958" box and then hit the "Close" button.
6. Back in the Volume Control window you should now see an IEC958 option under the "Switches" tab.  Check that box, and hit the "Close" button.

That's it!  You should now be hearing sound from your coaxial or optical sound ports.

---

### Post by dmayan on 2009-08-19
Worked great for me on Kubuntu 9.04

many thanks!!

---


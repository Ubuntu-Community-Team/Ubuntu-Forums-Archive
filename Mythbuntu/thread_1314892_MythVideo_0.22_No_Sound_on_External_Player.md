---
title: "MythVideo 0.22 No Sound on External Player"
date: 2009-11-04
forum: Mythbuntu
---

### Post by tim273 on 2009-11-04
Hello Everyone,

I just updated from Ubuntu 9.04 to 9.10 (with MythTV installed).  I have VLC setup as my external video player and all worked fine in 9.04.  When I upgraded the sound stopped working when I tried to play a video from MythVideo in VLC.  I tried the same vlc command line string in a terminal and the sound worked fine.  I tried mplayer as the external player and again no sound.  Any ideas?

Thanks,
Tim

---

### Post by suffice on 2009-11-05
maybe it has something to do with this

says that the external players dont work with storage groups

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide#Disadvantages](http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide#Disadvantages)

---

### Post by uniden9 on 2009-11-05
I had a similar problem playing local avi and iso via vlc.  I used pulse audio on 9.04 and prior ubuntu release and have vlc configure to use pulse audio as well. To get it to work, I had to edit the myth user .bashrc and I did the .profile in the users local home directory.  I don't believe the .profile is required, but was quite frustrated at the time.

I added the following to the end of the file.
export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

And now vlc would play sound in mythtv.  Very odd because you can play the file locally, by this I mean not through mythtv, via vlc/gnome and no issues with the sound. But I had to add the above for the sound to work in the .22 version of myth.  I had no issues in .21 with pulse audio.  It must be chroot or something similar now.  

Also for to get vlc to work correctly with pulse audio at all, I had edit the 
/etc/default/pulseaudio
And set the 
DISALLOW_MODULE_LOADING=0

Otherwise vlc will not play pulse audio correctly.

Please note that I have the vlc-plugin-pulse package installed, and vlc configured to use it.

---

### Post by Dannr on 2009-11-28
Thanks! That solved my issue (Ubuntu 9.10, MythTV 0.22, trying to get VLC going as external player). For future reference and others:
> **uniden9 said:**
> [...]
I don't believe the .profile is required, but was quite frustrated at the time.
[...]

This was in fact necessary for me -- with the "export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1" only in .bashrc it didn't work; with the line only in .profile it did work.

---


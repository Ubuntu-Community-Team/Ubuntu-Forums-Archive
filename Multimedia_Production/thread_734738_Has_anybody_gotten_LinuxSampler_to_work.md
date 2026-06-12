---
title: "Has anybody gotten LinuxSampler to work?"
date: 2008-03-25
forum: Multimedia Production
---

### Post by dfro on 2008-03-25
I cannot get gigedit or linuxsampler working in Ubuntu Studio Gutsy. Has anyone got it working?

While trying to compile linuxsampler, I run into this error:

checking for SQLITE3... No supported MIDI input system found!
Sorry, LinuxSampler only supports the following MIDI drivers at the moment:
ALSA, MIDIShare, CoreMIDI.
If you think you have one of those available on your system, make sure you
also have the respective development (header) files installed.

...........................................

While trying to compile gigedit, I get this error:

checking for GIG... configure: error: Package requirements (gig >= 3.2.0) were not met:

Requested 'gig >= 3.2.0' but version of gig is 3.1.1

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GIG_CFLAGS
and GIG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Thanks for any comments,
dfro

---

### Post by cmay on 2008-03-25
hi .
what or  how many midi inputs do you have.
do you use jack ?
i use the linux sampler in 64studio whitout any problem. 
i am trying to get my ubuntustudio to find my soundcard right now so i have not tried anything in ubuntu just yet.
but i suspect i should work fine there just as well.

---

### Post by dfro on 2008-03-25
I have UbuntuStudio Gutsy running on an Intel based computer that I built.  I am using a Delta 1010 sound card. Yes, jack is working fine on my computer.

I cannot get LinuxSampler or Gigedit compiled or installed in UbuntuStudio.

I have tried the .deb packages on the LinuxSampler site and I am getting all kinds of dependancy problems.

It seems that removing qsampler and its dependancies has helped some people, but that removes the ubuntustudio-audio package, which I am sure is being used by many other programs.  I should avoid removing this package, correct?

dfro

---

### Post by cmay on 2008-03-25
hi again
sorry that i mistaked qsampler for linuxsampler.
i have a bit trouble seeing since i have  my eyes operated.
the linux sampler i dont know. 
if there is a midiport in the soundcard and it is plugged and ready to play trough jack it should work fine.
well the packaged your asked to remove you should not remove i think. i did that by mistake also when i first tried to install drivers for my soundcard. i had to simply reinstall ubuntu again. mostly because i really dont see that well and if somethings bug me i just sometimes find it more easy to reinstall if i dont have anything important on my harddisk.

i wonder about the compiling that you mention ?.
i nerver really compiled that much from source. 
is there any directions whit the sources that you try to compile.
maybe the anwer is somewhere . 
to be honest the first look at the post it looks like the error message indikates that there are no usable midi input found anywhere but i dont think that i can help you that much since i dont know the card and the linuxsampler that i thourgt for some reason would be qsampler. 
however the error messages indicates pretty clearly somethings are missing or not fit for the purpose.
i hope that you find the right anwer somehow 
and please forgive me for mistaking the two linux samplers.
best of luck

---

### Post by Drunky on 2008-03-26
[http://www.cockos.com/forum/showthread.php?t=15238](http://www.cockos.com/forum/showthread.php?t=15238)

This is a really good thread.

It's in the Reaper forums but its a tale of Alex Stone as he is beginning his odyssey into Linux music.

As a professional in the music business he needs lots of help to setup and run Ubuntu Studio while getting things such as LinuxSampler to run.

Studio Dave Phillips is involved as are the developers from LinuxSampler.

I don't remember which page number it occurs, but Dave helps Alex get LinuxSampler complied and running with assistance (via email if I remember correctly) of the LinuxSampler developer.

Hope this helps.

---

### Post by dfro on 2008-03-26
Drunky,

Thanks for the link.  I skimmed the forum and I did not catch any detailed info on how the various linuxsampler remnants were removed from UbuntuStudio. They did get it working, though.

I do not understand .deb packages. Lets say you have package-A which needs package-B. Both are installed on your system and running happily.  Then you "apt-get install" package-C, which requires package-B, also. You then try to remove package-C. Synaptic will now remove package-C along with package-B  and thus break package-A, correct?

Thanks,
dfro

---

### Post by viciouslime on 2008-04-11
> **dfro said:**
> Drunky,

Thanks for the link.  I skimmed the forum and I did not catch any detailed info on how the various linuxsampler remnants were removed from UbuntuStudio. They did get it working, though.

I do not understand .deb packages. Lets say you have package-A which needs package-B. Both are installed on your system and running happily.  Then you "apt-get install" package-C, which requires package-B, also. You then try to remove package-C. Synaptic will now remove package-C along with package-B  and thus break package-A, correct?

Thanks,
dfro

No, the package manager will realise that package A still needs B and so only C will be removed. If you want .deb packages for linuxsampler you can get i386 ones from the official site or AMD64 ones from my site.

---

### Post by hogiewan on 2008-04-14
viciouslime, I tried your amd64 for liblinuxsampler and it gave me "Error: Dependency is not satisfiable: libjack0"  However, libjack0 and libjack0-dev are installed on my system.

---

### Post by hogiewan on 2008-04-14
I seem to have gotten somewhere.  After getting this message:
> Sorry, LinuxSampler only supports the following MIDI drivers at the moment:
ALSA, MIDIShare, CoreMIDI.
If you think you have one of those available on your system, make sure you
also have the respective development (header) files installed.

I installed libasound2-dev in Synaptic, and that seems to have worked

---

### Post by hogiewan on 2008-04-15
now I get this while compiling linuxsampler:
>  undefined reference to `gig::DimensionRegion::GetParent() const'


Yes, I've compiled/installed libgig

---

### Post by viciouslime on 2008-04-19
> **hogiewan said:**
> viciouslime, I tried your amd64 for liblinuxsampler and it gave me "Error: Dependency is not satisfiable: libjack0"  However, libjack0 and libjack0-dev are installed on my system.

Are you using hardy?

---

### Post by hogiewan on 2008-05-13
> **viciouslime said:**
> Are you using hardy?

well, now I am - installed, but no time to test it right now

---

### Post by hogiewan on 2008-05-21
just to follow up - I did get linuxsampler to work.  Thank you very much for those packages, vicious. 

Now, does anyone have any good string (violin, cello, sections) gig files?

---


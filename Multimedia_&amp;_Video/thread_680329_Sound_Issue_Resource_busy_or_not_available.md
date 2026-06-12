---
title: "Sound Issue: Resource busy or not available"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by CollinAnderson on 2008-01-27
Hello,

When I go to System->Preferences->Sound and then click Test I am getting this error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.

Most programs will look like they are playing music, but nothing comes out of the speakers.

Most of my information should be on these two pages:

[http://pastebin.ca/875520](http://pastebin.ca/875520)

[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N200_0769ALU](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N200_0769ALU)

I also tried a USB headset and that worked mostly fine, but the built in audio does not work. 

Any ideas?

Thanks,
Collin Anderson

---

### Post by lhardyl on 2008-01-28
I am having the very same problem with my newly installed 7.10

when i run 'lspci' i can find my audio controller

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)

i admit i' an utter nub at this so it may very well be something simple, but help is appreciated

thanks in advance

---

### Post by tpost001 on 2008-04-19
I can just add to the list.  I get the same error message, although I can hear the drum beat of the Ubuntu log in and Skype firing up, but after that it is dead.  No CD player no wav files, nothing.  When I look at System>Preferences>Hardware Information, I can also see that my audio device has been detected.  

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)

I downloaded Kmix and made sure that everything was set right and nothing turned off, but nothing helps.  Any help from you gurus out there?  Is it possible this is a problem with amd64 type computers?  I had no problems installing and getting audio on my i386 laptop and desktop.

---


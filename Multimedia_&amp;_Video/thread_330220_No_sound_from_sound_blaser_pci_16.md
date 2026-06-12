---
title: "No sound from sound blaser pci 16"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by Shadeline on 2007-01-02
I have used "Comprehensive_Sound_Problems_Solutions_Guide_files" and also done what Alsa says to do in it's files.. with no avail.  Please help.

I have no sound from using Ubuntu linux, had a similar problem with Mandrake linux (fixed it, but forgot how). Windows XP uses the Sound Blaster PCI 16 card with no trouble.

Any words of wisdom will be many Thanks!

Thank you for your time in this matter :KS

---

### Post by ingo on 2007-01-04
google is your friend:

[http://www.google.co.uk/search?hl=en&q=Sound+Blaster+PCI+16+linux&btnG=Google+Search&meta=](http://www.google.co.uk/search?hl=en&q=Sound+Blaster+PCI+16+linux&btnG=Google+Search&meta=)

---

### Post by az on 2007-01-04
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)

---

### Post by sgx on 2007-01-04
A few different companies made soundblaster 16s, and  not with identicle chipsets! So if a knoppix cd/dvd doesn't play the kde theme jingle
in your headphones/speakers, frisbeetoss your problem soundcard, stay out of Mickey Ds and Starbucks for a week, and buy an Envy based soundcard...A knoppix CD more than 3 feet from your keyboard is just excersize waiting to happen!!! My earlier post in the 'midi with a softsynth' thread may
offer a useful example, or dive in to the google link kindly posted earlier...but I vote the old 'No Knoppix-No Good' brand of technical support...

---

### Post by johnpipe on 2007-01-06
> **sgx said:**
> A few different companies made soundblaster 16s, and  not with identicle chipsets! So if a knoppix cd/dvd doesn't play the kde theme jingle
in your headphones/speakers, frisbeetoss your problem soundcard, stay out of Mickey Ds and Starbucks for a week, and buy an Envy based soundcard...A knoppix CD more than 3 feet from your keyboard is just excersize waiting to happen!!! My earlier post in the 'midi with a softsynth' thread may
offer a useful example, or dive in to the google link kindly posted earlier...but I vote the old 'No Knoppix-No Good' brand of technical support...

I too, like to use Knoppix Live for trouble shooting and testing ... but there is a "Gotcha!".  Old hardware vs New Knoppix can result in no sound with some MB/Soundcard combinations, including cards known to be supported. There have sometimes been kernel issues involved here, as well as XFree86/X.org conflicts with some older hardware.That's why I keep earlier Knoppix versions around; if a new one won't play sound, double check with an older version. For example, I've got a SB Live! that works fine with Knoppix 3.7 using OSS, and doesn't work "out of the box" with Knoppix 4.0 using ALSA (and Xorg, which turns off the soundcard on my old hardware, requiring a work-around)

HTH, johnpipe

---

### Post by johnpipe on 2007-01-15
Shadeline, if you are still struggling with your soundblaster, check this howto and see if the symptoms match; if so, the fix is there.  If not, please post the full soundcard output of lspci -v.

HTH, Johnpipe

[http://www.ubuntuforums.org/showthread.php?p=1975248&highlight=johnpipe#post1975248]("http://www.ubuntuforums.org/showthread.php?p=1975248&highlight=johnpipe#post1975248")

---


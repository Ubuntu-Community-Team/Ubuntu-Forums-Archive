---
title: "Coverting records (vinyl) to digital"
date: 2007-07-01
forum: Multimedia Production
---

### Post by blmartin777 on 2007-07-01
Need some advice or help. My dad wants to convert all his records to digital. Does anyone have experiance with that here? He is a avid music person, has very high price stereo so is very into a good clean sound. What are the options.

Thanks

---

### Post by morgan_greywolf on 2007-07-01
You need a turntable or stereo with a 'line-out' jack.  You can connect this to the line-in jack on your sound card.  From there, you can use an audio recorder like Audacity or Ardour to capture the sounds.  Once recorded in Audacity, you can export the audio out to an Ogg Vorbis or MP3 file, if you have the appropriate codecs installed.  Once you have an OGG or MP3, you can use Serpentine to burn these to CDs, if you like.

Audacity is the easier route to go because you don't need to deal with the intricacies of setting up Jack or a realtime or low-latency kernel.  OTOH, Ardour is likely to yield a higher-quality recording because you get finer-grained control over output levels from the turntable by using a mixer application like JackEQ.  Additionally, both Ardour and Audacity have the ability to cleanup clicks and pops from old records.

You might want to consider trying UbuntuStudio, available from [http://ubuntustudio.org;](http://ubuntustudio.org;) it comes with the low-latency kernel by default and all the necessary applications, including Audacity, Ardour, Jack, QJackCtl, Patchage, JackRACK and JackEQ.  There also exists a realtime kernel, a link to which is posted in the sticky posts at the top of this forum.

---

### Post by blmartin777 on 2007-07-01
If you use the line in and ardour how does the sound turn out? Is it professional quality?

---

### Post by morgan_greywolf on 2007-07-01
You can get professional quality results with either Audacity or Ardour, but I will say that, IMHO, it's much easier to get professional-quality results with Ardour due to the amount of flexibility available by using the JACK Audio Connection Kit.

---

### Post by blmartin777 on 2007-07-01
We are going to be dealing with a laptop here. Is the soundcard going to be a good enough quality to handle this?

Thanks

How is it being converted from analog to digital? Is the kernel doing that or the software?

---

### Post by morgan_greywolf on 2007-07-01
Many modern laptops have completely adequate sound cards, although for good professional-quality results a sound card supporting at least 24-bit audio is recommended.  Even with many on-board sound cards though, provided you have adequate processing power, you can get very nice results.  What chipset does your onboard audio use?  (hint:  you can get it from 'lspci')  But in any respect:  try it.  You have nothing to lose.

The A->D conversion happens on the audio hardware.  That's why something like a Soundblaster Audigy will give the best results. But many onboard audio chipsets have very nice A->D conversion, so again, I'd just try it.  You have nothing to lose, but perhaps the cost of a cable you'll need anyway if you decide to go the Audigy route.

---

### Post by yabbadabbadont on 2007-07-01
You may want to check out the "gramofile" program.  It does a very good job of cleaning up hiss, pops, and clicks from vinyl recordings.

```
/home/daffy $ aptitude show gramofile
Package: gramofile
State: not installed
Version: 1.6-7
Priority: extra
Section: universe/sound
Maintainer: Daniel Kobras <kobras@debian.org>
Uncompressed Size: 262k
Depends: fftw2 | fftw2-double, libc6 (>= 2.3.4-1), libncurses5 (>= 5.4-1)
Recommends: mctools-lite
Suggests: cdrecord
Description: Transfer sound from gramophone records to CD
 GramoFile enables you to record audio from (for example) gramophone records, process the signal and listen to the results.
 Because sound files in .WAV-format are used, it is possible to exchange the files with many other programs. Cdrecord(1) can
 burn CD-Recordables of these, so you can make CDs with the music of your favorite records.  The user interface of GramoFile
 has a windows-like look-and-feel, making it fairly easy to use. 
 
 One of the most important parts of GramoFile is the ability to process digital audio signals. Through the application of
 several filters it is possible to accomplish a significant reduction of disturbances like ticks and scratches. These filters
 have been programmed in such a fashion that they can be applied in any order (and multiple times) in a single run, thus
 avoiding the use of temporary files. It is possible to adjust the properties of each filter independently, so in every
 situation an optimal result can be achieved. 
 
 Another interesting feature is the track splitting. Just make one .wav file of an entire side of an record and GramoFile will
 detect where the individual tracks are located. This happens fully automatically, without need to set any options. More
 experienced users may fine-tune the algorithm, or change the detected track starts and ends, but generally that will not be
 necessary. Track-times are saved in an editable (plaintext) .tracks file, that will be used during the signal processing to
 produce one processed .wav file for each individual track. 
 
 To record and play .wav files, modified versions of brec(1) and bplay(1) by David Monro are included. These programs provide
 buffered recording and playback, so all will go well even on a highly loaded system. Both programs have been modified to
 support the standard GramoFile user interface.  Brec also got a `graphical' peak level meter, and bplay a running time
 display.

```

---

### Post by morgan_greywolf on 2007-07-03
I've heard of gramophile before, but haven't tried it.  It seems like a multitrack recorder with the appropriate plugins would give you much more flexibility.  But I'll bet gramophile is easier to get up and running quickly.

---

### Post by dabl on 2007-07-03
I use Audacity + Gnome Wave Cleaner (gwc) on a low-latency kernel Ubuntu system.  My onboard sound system is the Intel HDA, on a STAC 92xx chip, with ALSA mixer.

Audacity seems to do a good job of the basic capture, and also it will "normalize" the level, and you can "insert silence" in the lead-in and lead-out ends of each track.  But I don't recommend the de-clicking or denoising features of Audacity.  gwc is much better for de-clicking, de-crackling, and denoising.

I assume you're referring only to 33.3 rpm vinyl albums, which are fairly straightforward to capture.  Good quality cartridge, stylus, and turntable > stereo receiver/pre-amp > line-in jack to your sound card. If you want to digitize 78s, there's a whole 'nother world of issues to deal with, due to non-standard equalization and the stylus needs to be special for that purpose.  But "Yes", you can get a very high quality result, bearing in mind that the music won't ever be any better than the source vinyl that you copied it from ....

:)

---

### Post by jacob01 on 2007-07-06
although the quality wont be good you could try using a capture device made by pinicle
but no matter what you do the quality wont be good if its coming from a vinal

---


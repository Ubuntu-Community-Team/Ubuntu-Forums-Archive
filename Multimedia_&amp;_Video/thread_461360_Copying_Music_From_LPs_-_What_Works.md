---
title: "Copying Music From LPs - What Works?"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by ebozzz on 2007-06-01
Does anyone know of suitable application that will allow you to copy music from LP format? I've got as TON of old music that I would love to copy to CD-ROM. Thanks!

---

### Post by crispy_420 on 2007-06-02
Audacity...

Now you just need to worry about hardware. You'll either need a turntable that has a built in pre-amp (can be bought for about $40 refurbished online) or the hard way. The hard way involves a receiver that has a "phono" input and a turntable. You would hook up a turntable to the receiver via the standard cable. Then using the "tape out", connect to line-in/mic on computer. That will take a RCA to mini headphone (3/8"?) cable. With either method you would have to have your sound card setup to accept the line-in, that usually involves turning on that connector. Then just setup audacity to record that input.

---

### Post by ebozzz on 2007-06-03
> **crispy_420 said:**
> Audacity...

Now you just need to worry about hardware. You'll either need a turntable that has a built in pre-amp (can be bought for about $40 refurbished online) or the hard way. The hard way involves a receiver that has a "phono" input and a turntable. You would hook up a turntable to the receiver via the standard cable. Then using the "tape out", connect to line-in/mic on computer. That will take a RCA to mini headphone (3/8"?) cable. With either method you would have to have your sound card setup to accept the line-in, that usually involves turning on that connector. Then just setup audacity to record that input.

Thanks for the reply. I am now on the hunt for the first option!

---

### Post by yabbadabbadont on 2007-06-03
As for the software to use:
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
I've used it successfully in the past.

---


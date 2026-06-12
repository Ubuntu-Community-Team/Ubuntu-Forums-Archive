---
title: "K3b burns Audio CDs with &quot;unknown&quot; tracks"
date: 2012-05-03
forum: Multimedia Software
---

### Post by ianmillington on 2012-05-03
Hi

I am running kubuntu 12.04 on a Dell inspiron 630m laptop.

When I want to burn an MP3 album, I drag the tracks into the lower pane and all relevant data is there (title artist time etc). However, when I burn the CD all the track information is lost, the tracks are now known only by their track number. The tracks play fine in an ordinary CD player. 

One thing I would add is that until I selected "always hide" (and I don't seem to be able to get it back) every time I launched K3b I got a message about installing a package (mp3 support) to "enhance functionality" of K3b. On acceptance the Mp3 support package would be downloaded and apparently installed. However on next launch the whole thing would be repeated. 

I have deleted the K3b profile in my home partition but that hasn't worked either. In the K3b settings MAD support is shown being installed.

Any clues folks?

---

### Post by GSD4ME on 2012-05-08
I too have this same fault - again Ubuntu 12.04, again a laptop (Fujitsu Amilo).

Have tried the audio CD on the PC and in my car - neither shows the relevant information

Cannot find anything in the help information on the k3b site nor in any other areas.

---

### Post by Yellow Pasque on 2012-05-08
I assume you folks have libk3b6-extracodecs and lame packages installed?

---

### Post by GSD4ME on 2012-05-08
I have the former, but I don't think that I have the latter

Silly question, I know, but would the LAME package cure the problem?

---

### Post by ianmillington on 2012-05-08
Thanks for the reply. Yes I have both installed.

Further info, the computer plays MP3s just fine either in Amarok or even the applet in the right-hand pane in Dolphin, so I don't think it's a question of there being no MP3 support.

However, my theory is it could be a problem with CDDB access. Amarok's fine but KSCD for example shows all playing tracks to be unknown and the artist to be unknown. In K3b when I drag the titles into the project pane it becomes populated with the data but this is not reflected in the burned disk. Also clicking the query CDDB button clears the data. I'm stumped.

---

### Post by jeiworth on 2012-05-11
Hi,

I noticed the same problem and did a search on cddb in the package list: results that after installing the kde-config-cddb package k3b now behaves as expected, also this adds a CDDB Retreival config option in the Multimedia settings of System Settings. Hope it helps.

---

### Post by GSD4ME on 2012-05-12
jeiworth

nope - still get the same 'feature' - ie nothing works regarding display/storage of track information.

I may well contact the authors and ask them.
Or go to Brasero

---

### Post by ianmillington on 2012-05-14
Same for me I am afraid - the package was already installed

---

### Post by evilsoup on 2012-05-14
It sounds like you are creating an audio CD. This converts the files to uncompressed .WAV files, which can't contain metadata. Plop a commercial CD in your drive and you'll see they are the same way.

If you want to just put a bunch of .MP3s on a CD (which will play on some CD players), then you need to burn it as a data CD. That should preserve the metadata.

---

### Post by ianmillington on 2012-05-14
No, the resulting files are Mp3s. Apart from that, everything else is unknown.

---


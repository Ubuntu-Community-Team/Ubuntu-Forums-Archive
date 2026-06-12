---
title: "Is there a lame equivalent program for creating .flac audio files?"
date: 2019-05-01
forum: Multimedia Software
---

### Post by greg2lapa on 2019-05-01
I'm using cdparanoia to rip CD to .wav files. I then use lame to turn each .wav file into an MP3 file.Is there an equivalent program to lame for turning each .wav file into a .flac file?Lame has a really good reputation, and I was wondering if there is something with just as good a reputation for making .flac audio files.

---

### Post by TheFu on 2019-05-01
Do you mean like "flac"?   Or is this a trick question?

---

### Post by greg2lapa on 2019-05-01
> **TheFu said:**
> Do you mean like "flac"?   Or is this a trick question?I have .wav files. I want to convert them to .flac files. Which program is good to use to do this?If I want to convert .wav files to .mp3 files, I can use the program "lame". Which program converts .wav to .flac?

---

### Post by TheFu on 2019-05-01
**flac** is the name of the program.

---

### Post by greg2lapa on 2019-05-01
> **TheFu said:**
> **flac** is the name of the program.Ah, thank you for explaining. I've never done it before and didn't realize its name is also the program as its name describes it as a codec. Thanks!

---

### Post by TheFu on 2019-05-01
> **greg2lapa said:**
> Ah, thank you for explaining. I've never done it before and didn't realize its name is also the program as its name describes it as a codec. Thanks!

Google "flac linux" ... its been around along time.  It has lots of options. The manpage seems fairly good.

---

### Post by Yellow Pasque on 2019-05-02
> **greg2lapa said:**
> I'm using cdparanoia to rip CD to .wav files. I then use lame to turn each .wav file into an MP3 file. Is there an equivalent program to lame for turning each .wav file into a .flac file?

If you use abcde ripper, you can accomplish all of this in one step. You can use the .conf file found here: [http://www.andrews-corner.org/linux/abcde/index.html](http://www.andrews-corner.org/linux/abcde/index.html)
Just change to OUTPUTTYPE="mp3,flac" (and any other changes you want to make such as naming format).

> Lame has a really good reputation, and I was wondering if there is something with just as good a reputation for making .flac audio files.

FLAC is lossless, so the main job of a FLAC encoder is compression, as opposed to lossy formats (mp3, AAC, Vorbis), where the encoder has to use more advanced algorithms to figure out what information to discard. FLAC is also free of patents.
So the default "flac" encoder has been the the best option since the beginning (2001).

---

### Post by SeijiSensei on 2019-05-02
Kubuntu has a nifty method for handling CDs. Opening a CD in the Dolphin file manager presents the files in as many formats as the machine supports. So there is a "FLAC" pseudo-folder with images for each track on the CD.  There is also an MP3 and Ogg Vorbis folder.  Copying the tracks in the FLAC folder to another location automatically makes .flac versions.

---

### Post by speartip on 2019-05-04
Or if you find abcde too demanding, Asunder is in the repos and will also rip your CDs to flac in one step.

---

### Post by Rodney9 on 2019-05-04
Sound convertor will do the job as well.

---

### Post by shantiq on 2019-05-18
&#10122; place your .wav files in a folder
&#10123; open a terminal   Install flac {the program} *ONLY DO THIS ONCE *  ```
sudo apt install flac
``` 
&#10124; cd to the folder where wavs are

```
 ex:    cd Music/mywavfiles
```

&#10125; Run >>>    ```
for f in *.wav; do flac "$f"  "${f%.wav}.flac"; done
```

[COLOR=#b22222]* if you want to remove wavs after conversion run this instead:*[/COLOR]

```
 for f in *.wav; do flac "$f"  "${f%.wav}.flac"; done && rm *.wav
```

---

### Post by andrew.46 on 2019-05-19
> **Yellow Pasque said:**
> If you use abcde ripper, you can accomplish all of this in one step. You can use the .conf file found here: [http://www.andrews-corner.org/linux/abcde/index.html](http://www.andrews-corner.org/linux/abcde/index.html)
Just change to OUTPUTTYPE="mp3,flac" (and any other changes you want to make such as naming format).

I have only just now realised that this conf file does not really have a direct link so I have amended this [with this link...]("http://www.andrews-corner.org/linux/abcde/index.html#all_codecs") On my next days off I will add a few words about using abcde in the manner of:  abcde -o 'mp3,flac' from the command line using this conf file.

---


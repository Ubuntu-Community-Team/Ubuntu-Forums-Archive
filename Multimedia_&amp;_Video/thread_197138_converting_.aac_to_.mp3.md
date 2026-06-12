---
title: "converting .aac to .mp3"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by Adam Golebiewski on 2006-06-15
Hi,

I try to convert .aac file into .mp3 but I cannot do this in my Dapper. Could you tell me how can I do it?
I tried mplayer -ao pcm infile.aac -ao pcm:file=outfile.mp3 but it gives me an error in Terminal.

thanks in advance
Adam from Poland

---

### Post by whatever on 2006-06-15
use mplayer to convert .aac to .wav and pass the .wav to lame

---

### Post by Tarken on 2006-06-15
I wrote a script a while back to make this slightly easier. You can find it here:

[http://tarken.lyrical.net/files/aac2mp3](http://tarken.lyrical.net/files/aac2mp3)

---

### Post by Adam Golebiewski on 2006-08-15
> **Tarken said:**
> I wrote a script a while back to make this slightly easier. You can find it here:

[http://tarken.lyrical.net/files/aac2mp3](http://tarken.lyrical.net/files/aac2mp3)

I run your script with "sh aac2mp3" in a folder where I have one file "1.aac" and I got a massege: "No files with extension m4a in this directory."

could you fix it?

I changed an extension from .aac into .m4a and then runned your script. I waited and waited and saw one new file (1.wav) in the folder with only 16kb. CPU went on 100% and nothing happened. Your script did not end but the file 1.wav was still 16kB. I waited another couple minutes and I ceased it without any sollution. Could you help?

Could you write what instructions should I write to change aac into wav?
Is it "mplayer -really-quiet -ao pcm 1.aac -ao pcm:file=1.wav" ?

Adam

---

### Post by Adam Golebiewski on 2006-08-15
> **whatever said:**
> use mplayer to convert .aac to .wav and pass the .wav to lame

ok but how could I do it?
When I write 

mplayer -ao pcm infile.aac -ao pcm:file=outfile.wav

then I get

FAAD: error: Unexpected channel configuration change, trying to resync!
FAAD: Failed to decode frame: Unexpected channel configuration change

So, what should I do then?
Adam

---

### Post by thx84 on 2006-08-29
> **Tarken said:**
> I wrote a script a while back to make this slightly easier. You can find it here:

[http://tarken.lyrical.net/files/aac2mp3](http://tarken.lyrical.net/files/aac2mp3)

well your script crashes when converting audio files with commas.

Let's take an example:

Sitting, waiting,whising.m4a converts into Sitting (the rest of the title after the comma is simply ignored) and then the script looks for a wav file that doesn't exist: **Could not find "Sitting,Waiting,Wishing.wav"**

to be able to convert this file, I have to rename it before running aac2mp3
you see any way to fix it?

---

### Post by forezt on 2008-04-04
Here's a simple script based on one I found from [this]("http://www.linuxforums.org/forum/redhat-fedora-linux-help/28511-convert-m4a-mp3.html") thread:

```
#!/bin/bash
current_directory=$( pwd )

#Remove spaces
for i in *.[Mm]4[Aa]; do mv "$i" `echo $i | tr ' ' '_'`; done

#Remove caps
for i in *.[Mm]4[Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with faad or mplayer 
echo Processing file: $i 
for i in *.m4a ; do faad $i; done

# Convert to MP3 
for i in *.wav; do lame $i; done

# Remove temporary files
rm *.wav;

```

To use this script, paste it into a file and make it executable. Then cd into the directory with your aac/m4a files and execute it.

- This will give you one 128kbps mp3 for each aac/m4a file. If you'd like something a little higher quality, you can find the options in lame's man page.

- You need to have faad and lame installed to use this script, which you can get from the multimedia repositories.   

- This script doesn't preserve metadata. You'll have to tag the new mp3 files.

---


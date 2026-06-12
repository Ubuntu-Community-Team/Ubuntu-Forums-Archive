---
title: "Create a Script"
date: 2008-10-07
forum: Multimedia Software
---

### Post by mingohills on 2008-10-07
I want to create a script that will run for converting files from .m4a to .mp3 

Right now, I run the following code in the terminal after I have navigated to the appropriate directory.
```

for i in *.[Mm]4[Aa]; do mv "$i" `echo $i | tr ' ' '_'`; done

for i in *.[Mm]4[Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

echo Processing file: $i; done

for i in *.m4a ; do faad $i; done

for i in *.wav
do
lame -h -b 192 "$i" "$i.mp3";
done

for i in *.mp3
do
x=`echo "$i"|sed -e 's/wav.mp3/mp3/'`
mv "$i" "$x"; done	

```

What I want to do is have the whole thing run as a command directed at a subdirectory, OR even better to run over the directory.  I am fairly novice at this so I admit that I may not be on the right track.  Can I create a file that runs this script?  Any help or suggestions would be incredibly helpful.
Thanks in advance.

---

### Post by Sub101 on 2008-10-07
Obviously without running through you code I can't know for certain. But the basics of it would be:

```

[B]#!/bin/bash

echo "What is the directory?"
read DIR

cd $DIR[/B]

for i in *.[Mm]4[Aa]; do mv "$i" `echo $i | tr ' ' '_'`; done

for i in *.[Mm]4[Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

echo Processing file: $i; done

for i in *.m4a ; do faad $i; done

for i in *.wav
do
lame -h -b 192 "$i" "$i.mp3";
done

for i in *.mp3
do
x=`echo "$i"|sed -e 's/wav.mp3/mp3/'`
mv "$i" "$x"; done
```

---

### Post by mingohills on 2008-10-07
and does that create a command, i.e. whatever I name the script file?  I am sorry I am little slow.  But if I create that file and save it.  Can I just run a terminal command directing it to the correct directory?

For example.  If I name it "convertM4A"

Can I enter the command:  convertM4A /my/specific/directory

That is what I am attempting to do, have a command line converter. Of course, I am a little slow.


The problem arose because when I had itunes on my last computer it organzed and renamed everything into separate folders. (No big deal), but to run my script I have to go to each album director individually.  Right now "cd ~/the/specific/directory and then I just C&P the script and let it run. Any suggestions would be helpful for the general process.  Thanks again for your help!!

---

### Post by Sub101 on 2008-10-07
oh. Save it as "WHATEVER".sh. Right click on it ==> Properties ==> Permissions and check the box Allow executing file as program.

Please note that I haven't checked the original file works.

From there you can either double click and "Run in Terminal" or you can cd to the directory you have saved it and run it with ./"WHATEVER".sh (ie add ./ before it"

---

### Post by mingohills on 2008-10-07
Thank you so much for your help.  I got it running.  It took me a bit.  I did as you said, fixed the permissions and I exported the PATH and voila.  Of course, I found a script that was already done and skips a step in the process, but trial and error is the only way to really understand.

Thanks again for your help.

---

### Post by haydnc on 2008-10-07
Just out of curiousity was there any reason you didn't use the pre-existing script nautilus-audio-convert which is in the repository and does (with appropriate codecs installed) the m4a to mp3 conversion?

---

### Post by mingohills on 2008-10-07
One last question (for Now)

It is very troublesome dealing with spaces.

Where you prompted for the directory.  I type in..

/home/mydirectory/Music/Andre\ 3000/The\ Album\ Title

Because itunes saved it with spaces, however it is understand \ as the end of path.  Is there a syntax that fixes that?

Thanks.

---

### Post by mingohills on 2008-10-07
I had no idea it existed.  What's the name of the converter?  You said it runs in nautilus?

I guess I just followed google trail that lead me to script, so I ASSumed that there wasn't anything prepackaged in nautilus or otherwise.  

In the spirit of speeding up the process, I would love to know where that is.

Thanks.

---

### Post by minky311 on 2008-10-07
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
Have you taken a look at this sticky specifically the audio & video conversion.

---

### Post by haydnc on 2008-10-07
If you open up Synaptic Package Manager and do a search for nautilus-audio-convert it should just be there.

When you click on it to select it for installing you should also see recommended and suggested other packages to install - basically they extend the range of conversions that can be done.

Once installed to use the script you just right click on the audio file(s) in question and select nautilus-audio-convert from the scripts sub-menu, it asks you a few questions then takes care of the rest.

---

### Post by mingohills on 2008-10-09
Thanks for your help guys.  Just an fyi, my script works great and at the same speed as the nautilus converter, BUT it loses tag info.  I have to run Picard.  The nautilus converter great, but it has a pop up for every stage of the conversion which is very annoying if you are trying to convert an entire album.  

Thanks again for your help.

---


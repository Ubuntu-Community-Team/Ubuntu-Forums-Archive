---
title: "Convert WAV to MP3 with lame commands in terminal?"
date: 2009-03-07
forum: Multimedia Software
---

### Post by Pipps on 2009-03-07
I would like to convert a WAV file to mp3 format, in the terminal, using my already installed lame codec. How should I do this?

I must be able to use the lame command: *'-V 3 --vbr-new'*.

I've spent half an hour searching Google but I can't find exactly what I'm looking for. So I hope someone wouldn't mind helping me here. Thank you.

---

### Post by albandy on 2009-03-07
lame -V2 input.wav output.mp3

---

### Post by Pipps on 2009-03-07
I had tried that, and this was the reason for my posting this thread: I receive the following error message:

```
lame: excess arg Full
```

What does this mean? Could it be that my input WAV file has spaces in the name, as opposed to underscores? Or would it be some other issue?

---

### Post by albandy on 2009-03-07
I see you typed V 3 before, this should no have spaces

---

### Post by Pipps on 2009-03-07
Should I include the text: '--vbr-new', afterwards, as well?

---

### Post by mc4man on 2009-03-07
To get around any name issues open the folder containing .wav's at a directory prompt. (either cd to it or use the right click "open in terminal" ( install nautilus-open-terminal and restart

Basic command (red is where any valid lame commands go

```
for f in *.wav; do lame [COLOR="Red"]--vbr-new -V 3 [/COLOR] "$f" "${f%.wav}.mp3"; done
```

A slight variation

```
mkdir temp && for f in *.wav; do lame --vbr-new -V 3  "$f" ./temp/"${f%.wav}.mp3"; done
```

or make a simple script (showing how to add add. lame parameters

```
#!/bin/bash
mkdir temp
for f in *.wav; do lame --replaygain-accurate -q 0 --vbr-new -V 3  "$f" ./temp/"${f%.wav}.mp3"; done

```

You can adjust if needed, to save to a different place replace the ./temp/ with path ect., ect., whatever you want

---

### Post by Pipps on 2009-03-10
> **albandy said:**
> I see you typed V 3 before, this should no have spaces
When I used no spaces, I receive the same error message.

---

### Post by Pipps on 2009-03-10
> **Pipps said:**
> Should I include the text: '--vbr-new', afterwards, as well?
I found that this did not improve the problem.

---

### Post by Pipps on 2009-03-10
> **mc4man said:**
> Basic command (red is where any valid lame commands go

```
for f in *.wav; do lame [COLOR="Red"]--vbr-new -V 3 [/COLOR] "$f" "${f%.wav}.mp3"; done
```
Hi Mc4man

I have tried to use your suggested basic script. I am finding myself very confused before I've even started. For instance, what does each section of the long command actually do?

- There is "for f in *.wav;";
- And ""$f" "${f%.wav}.mp3";".

Surely there is a far more simple WAV to mp3 conversion command than this?

---

### Post by mc4man on 2009-03-10
> Surely there is a far more simple WAV to mp3 conversion command than this? 

It's actually a very simple way.

Do you have a folder with .wavs inside?

If so, do you know how to cd to that folder in a terminal? (directory prompt

---

### Post by Pipps on 2009-03-10
Yes and Yes. Opening a terminal in a specific folder containing four WAVs seems to be the easy part! :)

It's the terminal command that I'm struggling with!

Thank you for your help here!

---

### Post by mc4man on 2009-03-10
Copy this command and at the *directory prompt for your folder*  paste into the terminal and press enter.

```
mkdir temp && for f in *.wav; do lame --vbr-new -V 3  "$f" ./temp/"${f%.wav}.mp3"; done
```

---

### Post by Pipps on 2009-03-10
Whoa...! That is one impressive command! 

I don't know what it did, but it worked! I could see the lame progress bars flickering across my screen just like the old days!

And now I have a nice batch of freshly processed mp3s. 

Thank you, Sir! :)

---

### Post by lumitoro on 2009-03-11
In Intrepid i just used (with all the lame and gstreamer codecs installed):
**lame -V3 input.wav output.mp3** and it's rocking in my cell phone :D

PS.:Used **Send to** in the **file.mp3** dropdown menu, and selected bluetooth, my cell phone codename and i'm good to go with my **LMMS** ring:D. The previous command was nice command indeed and it's purpose is to convert a directory and not a single file like i did with the difference that i didn't need to use the **--vbr-new** option. By the way...thanks to all of you i was able to be successful in this "simple" :( task, of converting .wav to .mp3. For ever grateful...

---

### Post by Pipps on 2009-04-02
> **mc4man said:**
> Copy this command and at the *directory prompt for your folder*  paste into the terminal and press enter.

```
mkdir temp && for f in *.wav; do lame --vbr-new -V 3  "$f" ./temp/"${f%.wav}.mp3"; done
```

This really is a brilliant terminal command!

May I ask, is there any way that it could be tweaked or inverted, to allow it to be run it in exactly the same way in order to convert mp3 back into WAV?

---

### Post by alexandari on 2009-04-02
I know this is a little out of the thread but why dont u just use Sound Converter? it`a very simple and easy program... :)

---

### Post by Pipps on 2009-04-02
Good suggestion! My view now is that nothing could possibly be as simple, as satisfying or as processor-friendly as pasting a command line terminal and finding a new folder pop-up full of the nicely processed lame mp3 files! :)

---

### Post by Pipps on 2009-04-22
I should report that Mc4man further helped me to understand that the reverse equivalent of the above terminal command, to convert mp3 up into WAV, is as follows:

```
mkdir temp && for f in *.mp3; do ffmpeg -i "$f" ./temp/"${f%.mp3}.wav"; done
```

Hope this helps someone! It certainly helped me! :)

---


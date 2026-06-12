---
title: "Getting Sound Recorder to record as mp3"
date: 2011-06-03
forum: Multimedia Software
---

### Post by cybrsaylr on 2011-06-03
Just installed Natty and always used Sound Recoder to directly record as mp3 files on previous Ubuntu versions. I forgot what you have to do to get mp3 added to the option list on Sound Recorder. Can someone tell me what has to be done so Sound Recorder will again save all my recordings as mp3 files?

---

### Post by cybrsaylr on 2011-06-11
Still need some help.

Installed gsteamer plugin and mp3 option, was added to Sound Recorder.
However the mp3 bitrates and times it renders are erratic and incorrect. Bitrates act like Variable Bitrates and run from 40-120, can't seem to get them higer to 192 or 320 as a Constant Bitrate, which I prefer. And a 4 minute song shows up as 8 minutes but plays as 4 minutes. 

What is needed to correct this? It didn't happen on earlier versions before Natty.

---

### Post by cybrsaylr on 2011-06-12
Bump.

Anyone?

---

### Post by cybrsaylr on 2011-06-13
Bump again....

---

### Post by cybrsaylr on 2011-06-14
Well I partially solved it.

Installed lame, it took awhile. 
Now I get consistent bitrates of 100-112 and song times are accurate. No more low bitreates of 40 or 50 with a 3 minute song showing a time of 6 minutes.

But I would like to get higher bitrates, like 192 or more out of Sound Recorder. 
Can somebody tell me how?

---

### Post by cybrsaylr on 2011-06-16
BUMP!

Come on people.
Can anyone help out here?

---

### Post by Yellow Pasque on 2011-06-17
```
gnome-audio-profiles-properties
```
After that, you can edit the mp3 profile or create a new one for VBR. The pipeline should look something like:
```
audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc vbr=4 vbr-quality=6 ! xingmux ! id3v2mux
```
Where quality=
```
vbr-quality         : VBR Quality
                        flags: readable, writable
                        Enum "GstLameQuality" Default: 4, "4" Current: 4, "4"
                           (0): 0                - 0 - Best
                           (1): 1                - 1
                           (2): 2                - 2
                           (3): 3                - 3
                           (4): 4                - 4
                           (5): 5                - 5 - Default
                           (6): 6                - 6
                           (7): 7                - 7
                           (8): 8                - 8
                           (9): 9                - 9 - Worst

```
More info: gst-inspect-0.10 lame | more

---

### Post by cybrsaylr on 2011-06-17
> **Temüjin said:**
> ```
gnome-audio-profiles-properties
```
After that, you can edit the mp3 profile or create a new one for VBR. 
OK, I created a new VBR that showed up in the selection box.
Then when I tried adding the codes below in terminal and it just kicked out errors and nothing happened.
What did I do wrong?

The pipeline should look something like:
```
audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc vbr=4 vbr-quality=6 ! xingmux ! id3v2mux
```
Where quality=
```
vbr-quality         : VBR Quality
                        flags: readable, writable
                        Enum "GstLameQuality" Default: 4, "4" Current: 4, "4"
                           (0): 0                - 0 - Best
                           (1): 1                - 1
                           (2): 2                - 2
                           (3): 3                - 3
                           (4): 4                - 4
                           (5): 5                - 5 - Default
                           (6): 6                - 6
                           (7): 7                - 7
                           (8): 8                - 8
                           (9): 9                - 9 - Worst

```
More info: gst-inspect-0.10 lame | more[/QUOTE]


PS: When I open Sound Recorder the VBR option is not added to the list of options.

---

### Post by cybrsaylr on 2011-06-17
Here is what terminal shows:

> rr@rr-Studio-XPS-8000:~$ gnome-audio-profiles-properties
rr@rr-Studio-XPS-8000:~$ audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc vbr=4 vbr-quality=6 ! xingmux ! id3v2muxvbr-quality         : VBR Quality
bash: audio/x-raw-int,rate=44100,channels=2: No such file or directory
rr@rr-Studio-XPS-8000:~$                         flags: readable, writable
flags:: command not found
rr@rr-Studio-XPS-8000:~$                         Enum "GstLameQuality" Default: 4, "4" Current: 4, "4"
No command 'Enum' found, did you mean:
 Command 'enum' from package 'enum' (universe)
 Command 'nnum' from package 'stda' (universe)
Enum: command not found
rr@rr-Studio-XPS-8000:~$                            (0): 0                - 0 - Best
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (1): 1                - 1
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (2): 2                - 2
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (3): 3                - 3
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (4): 4                - 4
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (5): 5                - 5 - Default
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (6): 6                - 6
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (7): 7                - 7
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (8): 8                - 8
bash: syntax error near unexpected token `:'
rr@rr-Studio-XPS-8000:~$                            (9): 9                - 9 - Worst



---

### Post by Goveynetcom on 2011-06-17
Curious, but why not record to another format that isn't lossy (like FLAC or something) then convert to whatever bitrate mp3 later?

---

### Post by cybrsaylr on 2011-06-17
> **Goveynetcom said:**
> Curious, but why not record to another format that isn't lossy (like FLAC or something) then convert to whatever bitrate mp3 later?

So I can skip that extra conversion step.
I used Sound Recorder with Karmic and it directly recorded and saved the music file as 128 bitrate mp3 which was fine for my purposes. That was a couple years ago and I forgot what had to be done to modify sound recorder.

With Natty sound recorder saves files to ogg or a couple other formats then I have to convert it to mp3 with sound converter. I wanted to avoid this extra conversion step as was possible with Karmic.

---

### Post by Yellow Pasque on 2011-06-17
> **cybrsaylr said:**
> Then when I tried adding the codes below in terminal and it just kicked out errors and nothing happened.
What did I do wrong?

Those aren't codes to be put in the terminal (except the first one). I simply used the code blocks to maintain spacing/formatting..

---

### Post by cybrsaylr on 2011-06-17
I put your first code in terminal:
> gnome-audio-profiles-properties

Then wasn't really sure what to do with the other codes you posted.

After putting the above code in terminal a pop up box came up. I then created a new VBR entry in that box and the pipeline was empty. Then tried adding your second code:
> audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc vbr=4 vbr-quality=6 ! xingmux ! id3v2mux
into the pipeline and still nothing happened.

Then when sound recorder was opened the options remained the same and the newly created VBR option was not added. 

What did I do wrong?

---

### Post by Yellow Pasque on 2011-06-17
Hmm. You might have to manually add the profile using gconf-editor (this is why I'm moving away from gnome).
```
sudo apt-get install gconf-editor
gconf-editor
```
Navigate to /system/gstreamer/0.10/audio/global/profile_list and add the name of your custom profile.

---

### Post by cybrsaylr on 2011-06-17
OK I installed install gconf-editor
gconf-editor

Then used your first code:
> gnome-audio-profiles-properties
which allowed me to create a VBR option that was added to sound recorder list as:

 VBR (.wav type)

Tried a short sample recording to test it and it failed to play!
Got this message from a pop up box in sound recorder:

> Could not determine type of stream.

---

### Post by Yellow Pasque on 2011-06-17
So what pipeline did you use? The exact one I posted?

---

### Post by cybrsaylr on 2011-06-17
> **Temüjin said:**
> So what pipeline did you use? The exact one I posted?

You know that seems to fluctuate!

Had to do it a couple times to make it stick.
At first if placed something in the pipeline but I didn't check it closely with what you posted above.

Now I just checked in again in terminal with your first code and VBR is there but the pipeline is blank again showing only identity and Profile Description shows: <no description> and File extension shows: wav!

The other options in that pop up box it shows: 
CD Quality, AAC
CD Quality, Lossless
CD Quality, Lossy
etc

Are not blank and are filled in with details.

---

### Post by cybrsaylr on 2011-06-19
Well I seem to be going backwards from this in post #5 of this thread.
> Installed lame, it took awhile. 
 Now I get consistent bitrates of 100-112 and song times are accurate. No more low bitreates of 40 or 50 with a 3 minute song showing a time of 6 minutes.

From fooling around with settings in terminal, I am back to getting those low 40-60 bitrates with song times being double or more of what they should be with Sound Recoder! 

The only way I can correct it is to set Sound Recorder to save recordings as ogg then convert ogg to mp3 with Sound Converter. This works great but it involves extra steps not needed with Karmic. With Karmic Sound Recorder saved music files as mp3 straight away with none of these low bitrate and wrong song times issues.

---

### Post by cybrsaylr on 2011-06-21
Since there seems to be no easy fix for this with Natty, is there any other as easy to use linux sound recording program that will save what you record as an mp3 file at a good quality level?

---

### Post by cybrsaylr on 2011-06-22
Are there no other easy to use apps like sound recorder for this?

---

### Post by Yellow Pasque on 2011-06-22
I like Audex.. but it's a Qt app

---

### Post by cybrsaylr on 2011-06-22
Just installed Audex.
It looks nice and can see what it does.
However I don't see it having any capability to record all sounds being played by my PC like Sound Recorder does. This is the feature I'm searching for.

I don't see any way for Audex to be configured to record audio played, say online radio, then saving it as mp3 files, unless I missed it.

---

### Post by Yellow Pasque on 2011-06-22
Sorry, I was thinking of sound-juicer, not sound recorder. :\

---

### Post by cybrsaylr on 2011-06-28
Bump.
Anyone has any fresh ideas to fix this mp3 bug with Sound Recorder?

My workaround is save files as ogg with Sound Recorder, then use Sound Converter to change the ogg file to a high quality mp3 bitrate, which is an extra step and a pain not needed to do on versions before Natty.

Would like to be able to use Sound Recorder again to save files directly as a good quality mp3 bitrate.

---


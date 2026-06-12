---
title: "Recording Electric Sheep"
date: 2010-05-04
forum: Multimedia Software
---

### Post by verbal.kint on 2010-05-04
Does anyone know how I would go about recording the electric sheep screensaver? (i'm running it manually in mplayer)

I suppose I could use screen capture software but it seems a bit crude and I would prefer not to lose video quality


Any ideas?

---

### Post by verbal.kint on 2010-05-06
Ok the best solution I was able to come up with was figuring out the order that the downloaded clips play and then stiching them together.

Run the electric sheep client in debug mode:

```
electricsheep --debug 1
```

In the terminal you will get a load of debug information, what you are looking for are the lines that say

```
playing 00244=01423=01324=01251.avi
```
(in the terminal profile preferences you might want to increase the amount of scrollback lines because the early debug info will dissappear off after about 6 minutes of video)

The numbers in the filename are explained [here]("http://electricsheep.wikispaces.com/Filename+format") but you dont need to know what they mean to complete the process.

These are the actual video files being played, they are stored in  ~/.electricsheep

if you make note of all these file names you will have a list of the video files and the order in which they played.

To stitch them together you need to use avimerge. To use this you will first need to install the transcode application

```
sudo apt-get install transcode
 sudo apt-get install transcode-utils 
```

Then to join the videos use the command:
```
avimerge -o OUTPUT.avi -i INPUT_1.avi INPUT_2.avi
```

---


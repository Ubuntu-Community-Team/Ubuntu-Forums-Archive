---
title: "Audio Editing / Mastering"
date: 2008-07-07
forum: Multimedia Software
---

### Post by eArquilla on 2008-07-07
So as to not scare people off with an extremely long post, I'll have a short and long version. Skip the long if time is an issue. Read the long if you want to understand my situation more precisely (and chuckle at an audio newb)

Short:
I need help understanding the theory of music editing AND an example of putting that theory into practice using ubuntustudio apps, most importantly (I think) for my needs: ardour, audacity, and jamin. 

I have basic knowledge of how to connect jack and record in ardour. I don't understand any theory behind music mastering in jamin, what the aim is, how you want the spectrum to look, etc.

Long:
I've had UbuntuStudio installed since it's release, upgrading with each release and to the 64 bit edition. I successfully got my Presonus Firebox working with it. I don't have a single -problem-, more of a question about how to use the software to it's fullest potential.

I think that most of the open-source software developers assume their audience has knowledge of recording, editing, and mastering with closed-source apps. I, however, have just begun.
I'm 19 and have played guitar for quite a few years, however, I have never been in a recording studio or had knowledge on how to correctly edit music.

What I have generally done is create one track in ardour and record from a condenser mic in the middle of my basement. Then my drummer, bassist, and I simply jam.

I moved to Denver for the summer (for a job), thus I'm experimenting on trying to record the way a professional would. So recently, I've been:

Creating 2 mono tracks in ardour, one for rhythm guitar and one for lead. I record each one separately, of course. I then export each track individually and open it in audacity. There I amplify the track to a desired volume (obviously never above 0.0 dbs) and use the noise reduction effect (getting the noise profile from a few seconds of silence). 

After doing this to each track, I export them to a file, open them in ardour, and create a third track for Jamin'. Here is where I really guess. I know how to get Jack to work it's magic and get the tracks into Jamin'. I'll play the whole song through once, make sure the tracks don't go past 0.0 db, and then take note of the highest db of each fequency in the spectrum tab.

I have messed around with the compressor and equalizer settings incessantly, trying to discover myself how to get the music to sound the way I want. So other than, 'do whatever sounds good to you', how should I adjust these settings? I feel like I'm butchering the sound most of the time and usually leave the file the way it was originally. I've read many, many pages of editing theory and such. I ran across one site with recommended compressor settings for different instruments, but it was not for multiband compression, so I was clueless as to how one goes about adjusting the compressors for all three ranges of frequencies.

My technique thus far has been to look at the spectrum, if something seems relatively high, which is usually the high frequencies for the audio's I've been using, I'll set a high threshold for the high frequency compression and set the ratio to 6:1 or so. Using acoustic guitars, the bass is usually very low to non-existent, so I really don't know what to do. I end up setting the threshold to -20 or so and the ratio to 1.2:1. The middle frequencies are generally consistent, so I set that to a -20 threshold and 1.5:1 ratio.

I'm not sure how to throw in the equalizer into this. My guess has been to try to either 'equal' out the spectrum, or make the lows and highs equal with the middle frequencies higher, like a pyramid shape. I understand you adjust as necessary for your own individual taste, but I need a starting point! I have no idea where to begin; i need a median I can later adjust to find my preferences.

Questions:

Is it just common sense that there shouldn't be loud low frequencies on a two track-acoustic?

If a threshold, let's say on the mid, is at -20, is this affecting the mids at any time the entire audio level is above -20, or simply when the mids are above -20? another newb question, i'm assuming it has to be when the entire audio level is above -20, because for my audio's at least no individual frequency goes above -30.

Can Jamin' effectively do what I am doing through audacity (i know it can increase volume output, but what about removing excess noise? is this done with effective compressing?)

Should each track in ardour be mono if I am planning on mastering them to a single track? is there a difference? If I add a drum beat with hydrogen, should that be mono and all three be mastered to a single track?





If anybody can help me with this, or point me in the right direction, please reply. UbuntuStudio seems so powerful and I feel like I was only scratching the surface, and now I'm scratching it the wrong way.

I simply cannot find examples on people taking their tracks and manipulating them with all of these open source apps with detailed descriptions of each step and why they did it. 

Thanks in advance!

---

### Post by roaldz on 2008-10-07
Hey,

It seems you are not a complete noob in this, I think you´re on the good way.
First of all, try not to look at waveforms and spectrums too much, this mislead you. 
I would suggest to add an insert to your master channel.
In the case you don´t know what an insert is: it is a small loop in the signal. Signal goes from A to B, but you put the insert between A and B, so the device connected to that insert can modify the signal before it´s sent to B. In this case it will be JAMin.
Be sure to config JAMin _NOT_ to send output to the system bus, only from and to ardour.
This way you can just play your session and JAMin will work live on your signal.

On the noise story:
The first thing I do if I get noise at a recording, I check my source. How come this noise is there? Is it an unbalanced cable? Is it a crappy microphone? Is it the Semi-acoustic guitar thats the bummer? Is it my Pre-amp? One thing I know for shure: Better to prevent than to recover. Are you shure your sources are noise-clear? 
To answer your question: JAMin cannot remove noise. Maybe ardour can, if you use a GATE plugin (I assume you know what a gate is, otherwise: ask).

On the threshold Q:
If you set your mid-threshold too -20dB in JAMin, it will only respond to peaks above -20dB in the specified mid-range. So if you pump trough an enormous bass, below the mid freq, the mid-compressor will not respond. Otherwise it would be useless.

Exporting question:
I would just pan the guitar tracks a little, and record the Hydrogen beat on a stereo track (or more), and create a wide stereo image. You can enhance this image with JAMin. Just fiddle around a bit.

Oh and by the way, if you open up Ardours mixer, every channel strip has a peak level indicator. It will turn red if your signal gets above 0dB. Also, JAMin has a look-ahead brickwall limiter, so if you put jamin on an insert on the master channel, make sure the JAMin limiter is set correct (on 0dB) you won´t get peaks above 0dB in your final mix.

More questions? just ask.

Roald

---

### Post by simtaalo on 2008-10-07
for audio editing i recommend trying out sweep.

link here for help on mastering with jamin
[http://jamin.sourceforge.net/en/tutorial.html](http://jamin.sourceforge.net/en/tutorial.html)

---


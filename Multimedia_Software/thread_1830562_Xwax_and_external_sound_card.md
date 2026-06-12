---
title: "Xwax and external sound card"
date: 2011-08-21
forum: Multimedia Software
---

### Post by fullscr33n on 2011-08-21
[B]SOLVED: The steps I took

1. Plug in M-Audio Conectiv
2. Go to Sound Preferences
3. Select M-Audio runtime DFU from Input and Output tabs
4. Connect your turntables to the Conectiv sound card as follows: 
     -Left Turntable deck plug into Input B and reverse Red and White leads (red into white and white to red)
     -Right Turntable deck plug into Input A and reverse Red and White leads (red into white and white to 
       red)
     -Connect outputs to your mixer normally. (e.g. Output A to Left channel, *line input*, Output B to     
       Right Channel, *line input*)
5. Open the terminal and start Xwax
     - ```
$ xwax -l ~/Music -a hw:1,0 -a hw:1,1
```
     *I didn't specify the timecode since I'm using Serato 2nd editing which is the default*
6. Enjoy the music.[/B]



Hey all, I've jumped back in after a few years and trying to learn to use Ubuntu. I have 11.04 installed on my laptop after a new hard drive install. My main use for it is to dj with it. I've been using Torq 1.0.7 on it under windows vista until recently. I'd like to use xwax since all I need is a vinyl emulator. 

I'm still new at this but I have gotten xwax installed and understand how to start the program through the terminal. I'm using my M-Audio Connectiv as my sound card. 

So far just going into my sound settings in Ubuntu, my internal default card shows up like it should. [sound_pref01.png attachment]

Then when I plug in my Connectiv via USB it shows up in my sound settings, which is good. :D [sound_prefs02.png attachment]

My internal sound card is still selected as default, which is ok, [sound_input01.png attachment] but I'm not sure how to set my external one as the one to be used. I'm not sure if you need to enter the commands upon program launch in the terminal or if you have to switch it someplace else..? [sound_input02.png attachment shows when I select it I still get no input signal when sound is put through it.]

To run xwax you need to enter ```
$ xwax -l ~/music -a hw:0
```

You can make this more complex also by entering the type of timecoded vinyl you are using..e.g. serato_2b

-l is signifing a path to your music...which i still can't get right..am I supposed to put ```
-l home/christopher/music
``` or what IS the correct way to put the path in?
 -a is to specify the hardware you are using and here's where my questions really start.

I'm guessing you have to create a configuration file for your ALSA? The ./asoundrc file? Does everyone have one or do you need to create it? Just after plugging it in, I can select my m audio card and select test speakers and I hear the sounds out of each speaker. So I know the sound is working out of it, but only out of the A outputs.  (meaning for inputs I have deck A L and R and then Deck B, L and R...then the same for outputs. Two sets of in's and out's)

I can't get any signal in though. If I take a turntable output and go straight into the mic input of the laptop I can get a signal in, but this is like using both sound cards some how...

I just need to know how to probably make a ./asoundrc file that would specify this card and its settings so when I run xwax I can put in something like 

```
$ xwax -t serato_2b -l ~/music -a hw:1 -a hw:2
```

plughw:Audio4DJ,0,0
plughw:Audio4DJ,0,1

if youre using the audio4 sound card I guess,..

I'm just confused on this part...what you're supposed to type specifically and how to configure it. Anyone have experience with this and could help out?

Thanks

-Chris

---

### Post by fullscr33n on 2011-08-21
The connectiv seems to be supported under linux as per this article

[http://createdigitalmusic.com/2007/06/i-can-use-my-conectiv-under-linux-but-not-vista-why-again/]("http://createdigitalmusic.com/2007/06/i-can-use-my-conectiv-under-linux-but-not-vista-why-again/")

but I dont know how to edit the ./asoundrc file to get this right

>  I had no issues getting it up and running on my 8-year-old Linux box. I powered my ancient Dell running FC5 down, connected the USB cable, and booted back up. Sure enough, it was recognized as a USB audio device. A few modprobes and .asoundrc edits later, I’ve got it working with Alsa, Jack, etc.

---


---
title: "NO sound recording in Audacity, have tried everything (I think...)"
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by stoodleysnow on 2007-09-16
Hello
I'm in a right pickle here.:-k
I need to record from tape to CD. So I have a jack lead from the headphone socket of my Panasonic Hifi to the LINE IN on the 82801H (ICH8 Family) HD Audio Controller, which is built into my Asus P5B motherboard, running the following spec:
Intel Core 2 Duo 2.13Ghz 64bit Dual Core CPU, LGA775
1GB Kingston DDR2 RAM
Nvidia GeForce 7600GS Graphics card
Aforementioned built in HD Audio
500GB SATA HDD
DVD ROM
DVD RW
Pinnacle PCTv (SAA7133 Philips) TV Card
Usb card reader
Eizo Flexscan L371 monitor (DVI)
550W PSU
etc.
It's well cooled, and runs Ubuntu 7.04 64bit with Compiz Fusion (love it):)
SO WHY WILL IT NOT DO THE SIMPLE TASK OF RECORDING THE AUDIO?:confused:
I have already got it to play back via Hifi--Sound Card--Speakers, but Audacity can't record it.
I've tried many (if not all) of the suggestions I can find. But no matter what setting I change or what input I select, in Volume control, Alsamixergui or Audacity, the wave graph remains flat or at best produces weak static. The Mic input meter at the top pics up the signal fine, it just doesn't get recorded. I love audacity, It works fine (up to press) on my old laptop, so what have I done wrong? Alsa, Alsa-OSS, Jack, Jack Rack, Jack-EQ and a few dozen other related apps are all Installed. I'm at my wit's end!](*,)
IS A SIMPLE RECORDING TOO MUCH TO ASK??!!:mad:](*,)
HELP!!!:confused::confused:

---

### Post by stoodleysnow on 2007-09-17
Bump.
Sorry, but I do need help with this.
Please.

---

### Post by steevc on 2007-09-17
I had a similar problem. Eventually I found that there was an extra channel on the mixer (Kmix or alsamixer) that needed to be set to record as well as the line-in. I'm not sure, but it may have been called Capture. I can check when I'm at home tonight in around 5 hours time if you can wait until then.

---

### Post by stoodleysnow on 2007-09-17
I've already tried that:(
Thanks for replying though.:KS
I have three options in Alsamixergui: Capture 0 (or just Capture), Capture 1 and Capture 2. I don't know which is which, and have tried various combinations of enabling to no avail.:confused:

---

### Post by stoodleysnow on 2007-09-18
Sorry, but...
bump.:(

---

### Post by dabl on 2007-09-18
Yep, Audacity + alsamixer can be a major frustrator!  Sometimes the least obvious thing is what turns it on.

On the "Switches" tab, have you tried muting the "output" channel?

Also, on the mixer, open "Edit > Preferences" (or perhaps it's the reverse of that) and make sure that all the boxes are checked.

---

### Post by stoodleysnow on 2007-09-19
On the switches tab it says 'headphones (o)'
                                   and    'mono (o)'

and every box in the preferences is checked.

---

### Post by dabl on 2007-09-19
> **stoodleysnow said:**
> On the switches tab it says 'headphones (o)'
                       

I haven't seen that -- it doesn't sound right.  What do you have on the "Input" tab?  Mine has 2 channels: "Capture" and "Mux".

---

### Post by sirskeleton on 2007-09-19
I have the same problem but the imput tab doesnt even show up in audicity.

---

### Post by stoodleysnow on 2007-09-20
My inputs tab says 'IEC958 (adjust bar)', 'Capture 0 (adjust bar)', 'Capture 1 (adjust bar)', 'Capture 2 (adjust bar)'.
I have all the inputs and outputs selected on the Alsa mixer, the OSS mixer and the TV Card settings. (I.e. I can see them all to adjust them) I've tried reinstalling all Alsa programs, no luck. ESD is switched off in the Sounds Dialogue. What can I do?:confused:

---

### Post by stoodleysnow on 2007-09-21
bump...

---

### Post by Stochastic on 2007-09-21
If Audacity is giving you so much trouble have you tried a different wav editor such as Rezound or Ardour?  If those also have troubles then you've narrowed the issue down to your soundcard driver, if not then the issue is clearly in Audacity's settings.

---

### Post by stoodleysnow on 2007-09-23
How would I go about replacing the sound card driver?:popcorn:

---

### Post by dabl on 2007-09-23
OK, 1 more notion to try:

In your mixer, on the "Switches" tab, mute the "Line in as Output" channel (I think that's what it says -- I'm looking at Kmix in Kubuntu, but it's similar in the Ubuntu mixer).  I'll cross my fingers ....   :)

---

### Post by stoodleysnow on 2007-09-24
Err... no.
:???:](*,):cry:

---

### Post by senor_smile on 2007-09-25
I had the same problem, and for me it was another program running that used the MP3 codec(or so I think).  I had another mp3 player open and sound wouldn't play.  when I closed the program sound played.

---

### Post by stoodleysnow on 2007-09-25
And I only have Audacity open.
Nowt else.:(

---

### Post by alterpinguin on 2007-09-25
if you dont know what you are doing, you are always lost:
1. you have to be shure you are not blocking the only!? audio-device with another program.
2. you have to use a mixer-utility to change the soundcard-settings
3. you have to listen to the audio-input while you are changing the soundcard-mixer-settings and search for the right input-source and level.

you have only one soundcard and think its working? with the loaded drivers, then you should be able to test the functions with "arecord" and "aplay" utilities:

in a terminal to enter the commandlines test:
aplay /usr/share/sounds/startup.wav
- it plays the sound thru the default hardware 
- if you hear nothing, you are totally wrong and have to fix this first.

aplay --device=hw:0,0 /usr/share/sounds/startup.wav
-should do the same, because if you have only one soundcard, it should be the no.0

arecord -vv -f cd -t wav | aplay -
- this uses "arecord" to record from the default device in cd-quality and plays it at once through aplay ! ! ! take care the usage of "-vv" makes some growing noise and is only to show you have no errors stopping the way of the recording.

next you try it with "-v" only and you start your mixer-utility and try different settings till you can hear some sounds of your ?input-line, ?micro ... whatelse you use!

last check the "arecord" man-page and other help-docs about it, it has options to specify the size of the recording-buffers, which may need to be increased to avoy any dropouts, if you computer is doing something else while you are recording.
btw. this: "--device=hw:x,y" thing, its a double-minus-sign! is a way to specify different soundcards (x-value) and their sub-channels(y-value), look at "aplay -l" output.

---

### Post by RichP0169 on 2007-09-30
In windows I do remember there being a tab to set "What you hear" "Line In" "Mic", etc in Audacity...I don't have that either...I have sound...but the big deal for me is I cannot seem to get the wave level high enough, it's frustrating, because I make music and I have to revert back to a laptop with windows.  It's really wierd, Is capture the same as the wave level?  If so, then even with that slider all the way it's just not enough...keeping an eye out to see if anyone has a good fix for this....

---

### Post by dabl on 2007-09-30
You need to look closely at Audacity, after you have the level as high as you can get it with your alsa mixer.

There's a graphic of a speaker and a microphone, each at the end of a slider -- it is on the top line of the graphic menu bar on my Audacity 1.3.3. That slider will boost either the output (speaker) or the input (microphone), so you can use that as your last boost.

I've found the "line in" level on the ALSA mixer to be the most powerful level boost, so use that first.

---

### Post by stoodleysnow on 2007-10-02
I've boosted them all.
I see plenty of graphics moving to the music at the top, just no actual recording being made in the waveforms beneath. I just get the same pattern of static regardless.:confused:

---

### Post by stoodleysnow on 2007-10-16
Meh, I'll just upgrade to Gutsy on Thursday and see if that sorts it. :-P
:)

---

### Post by gurkha on 2007-10-21
Have you tried this? 
In volume control(or whatever its called), select "Edit"-->"Preferences" and then check "Input Control". You'll get a new tab in Volume Control called "Options" where you can select your input source for recording. I selected "Line" and then, all of the sudden recording in audacity worked fine.

---

### Post by trjnhrse44 on 2007-10-23
Are you using alsa in audacity?  Last time I checked audacity choose OSS by default when installed and not alsa.  Most modern cards wont work until you choose alsa under edit, preferences in audacity.  Pick the option for your soundcard with an alsa driver (not just a specific i/o) under both playback and record

---

### Post by clonek on 2007-10-24
Setting my input source to "mix" seemed to work for me. I had it set the "Line" but oddly enough Audacity wouldn't record anything.

---

### Post by shirsch on 2007-10-29
Been there, done that, have the T-shirt.  I'm sorry, but the Audacity package available for Gutsy is just, plain broken.  I was able to easily get recording going by downloading the vanilla Audacity sources from their web site and installing it in /usr/local manually.  

Worked almost immediately!

---

### Post by mocha on 2007-10-31
> **stoodleysnow said:**
> Meh, I'll just upgrade to Gutsy on Thursday and see if that sorts it. :-P
:)

Just wondering if Gutsy worked for you.  I have exactly the same problems with an Asus P5B-E.

---

### Post by shirsch on 2007-10-31
> **mocha said:**
> Just wondering if Gutsy worked for you.  I have exactly the same problems with an Asus P5B-E.

Interesting.  I was fighting with a P5B Deluxe (Intel HDA audio) running Gutsy.  As I mentioned in my posting above, I had to remove the Ubuntu package and build Audacity from a vanilla tarball (get it from their project website).

That brought things to life immediately.  I'm busy capturing a record album as this is being written.  Sound quality is super!

There is a piece missing somewhere in the Ubuntu package.

---

### Post by mocha on 2007-11-01
> **shirsch said:**
> Interesting.  I was fighting with a P5B Deluxe (Intel HDA audio) running Gutsy.  As I mentioned in my posting above, I had to remove the Ubuntu package and build Audacity from a vanilla tarball (get it from their project website).

That brought things to life immediately.  I'm busy capturing a record album as this is being written.  Sound quality is super!

There is a piece missing somewhere in the Ubuntu package.


Are you able to record the "analog mix" AKA "stereo mix" internal audio that comes from things like webpages, Skype, audio files, etc?  No matter what mixer settings I use, or specifying different "model=" lines in the alsa config, I cannot get any internal mix audio to record.  I don't have a problem with external devices or playback.  The only thing I can think of at this point is that there is a bug in the AD1988 drivers at least in the Feisty 2.6.20 kernel.  I'm planning to try compiling the latest kernel, but in the meantime I'm trying to find someone else that has the same problems.  :confused:  Many searches on this problem are revealing nothing.

---

### Post by ramkumail on 2007-11-02
Hi,
 the problem with my mic is that i cannot record anything in audacity but when i unmute analog mixing in gnome alsa mixer i can hear whatever i speak back in the speaker which means mymicrophone is detected. if i open a command interface alsa mixer i cannot see mic in capture sections (only front mi mic boost ice.. are there)but in all tabs mic appears (with oo below the bars). :confused:

yahoo!!!
 I got it working. changed the input type(last items under all tab) to mic.
sorry that i was so stupid that i didnot find this and was suffering for almost a month which explains i am total linux noob. My mother board is asus P5B. i am mentioning it beacuse many have problems configuring this mic on this mother board. very happy now!!!
 Thanks to all those who helped me to arrive at this solution.:popcorn:

---

### Post by Footer on 2007-11-09
Wow, am I glad I found this thread!  I've been struggling with this for a week now and it turns out that this thread pointed me in the right direction.  Turns out that my input source was incorrect in Kmix.  I was using 'Line' since that's where my source is coming from.  However, all apps (Audacity, Kwave, Krecord) were recording either silence or the signal at a barely audible level.  Once I changed the input source to 'Mix', all was well.  Audacity is recording the source in a somewhat choppy format while Krecord and Kwave record just fine.  But that's the least of my problems and shouldn't be too difficult to figure out (sampling rate?).

Thanks to all those who offered their insight on this issue.  It's a stinker!

:)

---


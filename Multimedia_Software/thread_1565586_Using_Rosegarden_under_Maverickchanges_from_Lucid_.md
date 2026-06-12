---
title: "Using Rosegarden under Maverick/changes from Lucid need help change settings"
date: 2010-09-01
forum: Multimedia Software
---

### Post by shantiq on 2010-09-01
ok so i have been using rosegarden on lucid/karmic/jaunty

and i never used Jackd since it is to the non-highly-technical a remarkable pain in the butt


i compose entirely through midi and the sound has always played through timidity

see   this reading from Lucid

```

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]
    128,0 - (TiMidity, TiMidity port 0)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)		(WRITE ONLY) [ctype 1, ptype 2, cap 66]
```


jack-driver never worked before anyway with rosegarden

now there is a jackd2 on maverick


and when one opens rosegarden and goes edit/preferences it gives you midi ok audio ok

which never happened before
it was always midi ok audio not ok

which to me makes no difference since i do not record audio on rosegarden

BUT and thaT is for me the problem it NOW takes the midi to   (from Maverick)

14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]    [COLOR="Red"]instead of timidity[/COLOR] and nothings sounds



```
 JackDriver::initialiseAudio - JACK server not running
PluginFactory::instance(dssi): creating new DSSIPluginFactory
LADSPAPluginFactory::discoverPlugins - discovering plugins; path is [/home/shantiq/.dssi] [/usr/local/lib/dssi] [/usr/lib/dssi] 

  ALSA Client information:

    14,0 - (Midi Through, Midi Through Port-0)			(DUPLEX) [ctype 2, ptype 655362, cap 99]

AlsaDriver::setCurrentTimer((auto))
extractVersion: major = 1, minor = 0, subminor = 23, suffix = ""
AlsaDriver::versionIsAtLeast: is version 1.0.23 at least 1.0.14? yes
extractVersion: major = 2, minor = 6, subminor = 35, suffix = "generic"
AlsaDriver::versionIsAtLeast: is version 2.6.35-19-generic at least 2.6.20? yes
Using low-resolution system timer, sending a warning
    Current timer set to "system timer"
    WARNING: using system timer with only 250Hz resolution!
AlsaDriver::initialiseMidi -  initialised MIDI subsystem


```



so my question is how to point the midi to timidity as it used to be?


i know the whole thing is complicated but i understand that pointing to timidity should be easy   i simply do not know how to


all clever suggestions welcome

---

### Post by shantiq on 2010-09-08
i have looked around further and still no clue as yet

would any of you know how to point rosegarden to timidity?

i am convinced that it must be a simple operation but i have not as yet found the answer

---

### Post by shantiq on 2010-09-09
ok sorted does it automatically now goes to timidity
i do not know why but hey cool



ok and then it not going to timidity anymore   big puzzle

---

### Post by shantiq on 2010-09-14
ok and then it not going to timidity anymore   big puzzle:KS

---

### Post by cchhrriiss121212 on 2010-09-14
Is there any reason you are using Maverick when it has not been released as a stable OS yet?
I don't know much on timidity, but I could help you set up jack if you like? I promise it will not be painful as long as you have a bit of patience.

---

### Post by shantiq on 2010-09-14
> **cchhrriiss121212 said:**
> Is there any reason you are using Maverick when it has not been released as a stable OS yet?
I don't know much on timidity, but I could help you set up jack if you like? I promise it will not be painful as long as you have a bit of patience.


chris  because it allows me access to software like VLC 1.1.4 with no fuss it is the default package   and other more advanced software as standard   i always aim for the most advanced package available


as regards rosegarden i only use it to compose midi   i use ardour for recording live instruments


if you think i can use jack for hearing midi; routing my midi to be heard through jack;

and you have the patience to explain in detail how to do it
i would gladly accept        so far jackd has always been a scarecrow to me


on a slightly different note
this is [COLOR="DarkRed"]the music[/COLOR]  i make with [rosegarden midi]("http://shan.bandcamp.com/track/opening-candy") 



thanx for your kind offer


shan

---

### Post by cchhrriiss121212 on 2010-09-14
The first thing to do is install jack, which you can do from synaptic. If you have jack2 in there, then go for that one as it works better with newer cpus (the ones with 2 or more cores). You should only ever have one version of jack installed at one time, so don't install both to compare them or something.
These are the packages to install:
jackd
jackd2
qjackctl
patchage
plus any others that are pulled in as dependencies

I don't have Maverick, but I think when jack is installed it should ask you about configuring realtime permissions, which you should agree to (if it doesn't then you will need to set it manually, which I will explain if needed).

Then open jack from the menu and press start and see whether it runs.

---

### Post by shantiq on 2010-09-14
ok stage one completed


opened it with command-line qjackctl
since i cannot remember what the commandline is for jackd2

i installed 2   see picture


will need to manually add   configuring realtime permissions   since i distinctly recall turning it down when i installed ubuntu-studio


stage 2 when you are ready

---

### Post by cchhrriiss121212 on 2010-09-14
Using qjackctl is what I would actually recommend, I could not imagine how anyone uses jack from the CLI. Do you open everything you use from terminal?
The odd thing I see from your screenshot is that you already seem to have jack running in RT mode, so you must have made the adjustments yourself at some point.
Could you post the output of:
```
cat ~/.jackdrc
```
Just so I can check the rest of your settings.

Now all you need do is start up Rosegarden and a synth of your choosing and link them up! Open up patchage and you will see a visual representation of all your available input and output connections for both hardware and software. Blue boxes show audio connections and green ones will show MIDI. Use the refresh and arrange options if you get a cluttered screen.

---

### Post by shantiq on 2010-09-14
```
cat ~/.jackdrc
/usr/bin/jackd -dalsa -dhw:0 -r44100 -p1024 -n2

```


i do not use a synth i write everything on the matrix editor note by note then save to midi then  convert to wav


i use no instruments at any point


but do you mean like qsynth + qjackctl + patchage and connect ?


will try it and report


thanx

---

### Post by Joshun on 2010-09-18
Hi there,
I too am using the Maverick beta.
I highly recommend using the newer release of Rosegarden (10.04 Abraham) as it is much more stable than the 10.02 one in the ubuntu repos. You can get it from debian [here]("http://packages.debian.org/sid/rosegarden"). (you have to take off the older one first though)

Also, for what your doing, i would recommend lmms (LinuxMultiMediaStudio) as it does pianoroll (like matrix) editing and exports directly to wav or ogg. It can import midi also if you need that.

You can start jack simply by doing: ```
jackd -d alsa
```
If you need rosegarden with timidity, you have to trick it into not starting jack. To do this, first start another timidity server by doing in terminal ```
timidity -iA
```. Then start rosegarden and connect to one of the timidity ports (you have to keep trying to find the right one).

Joshun

---

### Post by shantiq on 2010-09-18
thanx joshun will certainly try all of that

---

### Post by cchhrriiss121212 on 2010-09-18
> **shantiq said:**
> 
i do not use a synth i write everything on the matrix editor note by note then save to midi then  convert to wav

i use no instruments at any point

You will be using a synth or soundfont of some kind at some point whether you realise it or not. MIDI files do not make any sounds without an instrument. I'm not familiar with Rosegarden, but I'm guessing that when you export to wav, it must make use of some soundfont you have installed by default.

Wouldn't you like to use controlled instruments as a part of your music?

---

### Post by shantiq on 2010-09-26
> **Joshun said:**
>  ```
timidity -iA
```. Then start rosegarden and connect to one of the timidity ports (you have to keep trying to find the right one).

Joshun


this works a charm and i do not understand why but the for the first time ever it also plays through my lexicon box which is cool

and it does not mind me doing ```
timidity -iA
``` after i have loaded rosegarden


here is a screenshot

---

### Post by shantiq on 2010-10-05
```

```also found a useful trick which allows one to convert the midi obtained at the end of the process to a 24-bit wave for higher sound quality


```
timidity --output-24bit   filename.mid -Ow -o filename.wav
```


or better even since midi files coming off rosegarden are low on volume with volume correction


```
timidity --output-24bit -A400 filename.mid -Ow -o filename.wav

```        volume is between 0 ( no sound) and 800

---


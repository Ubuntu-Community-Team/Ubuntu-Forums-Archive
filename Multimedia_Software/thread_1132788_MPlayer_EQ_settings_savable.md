---
title: "MPlayer EQ settings savable??????"
date: 2009-04-22
forum: Multimedia Software
---

### Post by cycle_mycle on 2009-04-22
Does anyone know how to get MPlayer to save the settings of the EQ so that they don't need to be set every the time?

There has to be a way, it's hard to believe that such a fine piece of software can leave out a detail like that.

I think it's going to be one of those "It's so simple that I can't see it" things.... (probably I should post on "Absolute beginner" section)

anyway - help! - thanks.

---

### Post by andrew.46 on 2009-04-22
Hi cycle_mycle,

I will admit with some shame that I have never used the 'equalizer' settings for MPlayer despite having been a keen fan of this great program for some time :-). However I note that the man page gives an example for placing such settings in the $HOME/.mplayer/config:

```

# Use Matrox driver by default.
vo=xmga
# I love practicing handstands while watching videos.
flip=yes
# Decode/encode multiple files from PNG,
# start with mf://filemask
mf=type=png:fps=25
# Eerie negative images are cool.
**[COLOR="Red"]vf=eq2=1.0:&#8722;0.8[/COLOR]**

```

This should provide a start? I imagine sound settings would be something like: 'af=equalizer=etc etc' but I have not tested this.

Andrew

---

### Post by mc4man on 2009-04-22
While i also never used an equalizer in mplayer I was curious about a slight difference wnen it's enabled versus disabled.

With it enabled then audio is played back with "AO: [alsa] 48000Hz 2ch floatle (4 bytes per sample)" (or 6ch floate

With it not enabled same source is played with "AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)" (or 6ch s16le

Not 100% clear on difference technically, didn't notice any soundwise

Used this in ~/.mplayer/config for a flatline (just to enable, also this is the default in smplayer

af=equalizer=0:0:0:0:0:0:0:0:0:0


remember once trying some values other than 0, seemed to work ok

---

### Post by andrew.46 on 2009-04-22
Hi mc4man,

> **mc4man said:**
> Used this in ~/.mplayer/config for a flatline (just to enable, also this is the default in smplayer

af=equalizer=0:0:0:0:0:0:0:0:0:0

I a had a decent search but I cannot find these defaults, which I imagine are in a config file somewhere. What is the name of the file?

Thanks for your trouble,

Andrew

---

### Post by mc4man on 2009-04-22
Heh Andrew
From the mplayer log in smplayer

> /usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 67108876 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/doug/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -volume 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 6 -af scaletempo,equalizer=0:0:0:0:0:0:0:0:0:0 -channels 6 -sid 1 /home/doug/Desktop/audio samples/Beethovens nionde symfoni (Scherzo)-1.wma

MPlayer SVN-r29188-4.3.2 (C) 2000-2009 MPlayer Team

As far as changing values I can't remember (should be some of my saved terminal history files on the hardy machine. As I remember most were straight single numbers, some were to decimals. (memory is failing it seems

Edit : now I *remember* the single values I was setting for a 10 band were in vlc, not mplayer. For mplayer I believe I may have set it in smplayer, copied the values and then added to the line in the config. Don't recall how that worked out as I don't use it anyway

Do you know what the diff. is from floate to s16le is ?


Edit : note that I didn't add any options to smplayer audio wise other than to use alsa and start at 100% volume

---

### Post by mc4man on 2009-04-23
@cycle_mycle
If you use smplayer you can set a custom equalizer setting as the default.
Don't believe here's a way (in smplayer) to store multiple settings

The values shown in smplayer equalizer, if added to a mplayer config in the equalizer=0:0:0:0:0:0:0:0:0:0 format should be divided by 10

---

### Post by cycle_mycle on 2009-04-24
Wow! this turned out to be an interesting discussion, thanks a bunch!

Here's the section from my mplayer.config file that I think is being refered to by you guys:

##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=pulse,alsa,

# Use SDL audio driver with the esd subdriver by default.
#ao = sdl:esd

# Specify the mixer device.
#mixer = /dev/mixer

# Resample the sound to 44100Hz with the lavcresample audio filter.
#af=lavcresample=44100

# Specify default audio codec (see -ac help for a list).
ac=mad,


So I change the "#af=lavcresample=44100" first by uncommenting and relacing it with "af=equalizer=0:0:0:0:0:0:0:0:0:0" ?

Am I getting this right?

And then changing each 0 with a value corresponding to the individual levels of freqs?

---

### Post by andrew.46 on 2009-04-24
Hi cycle_mycle,

If you dig into the man pages you will see the *exact* frequencies being manipulated by these settings:

> 
              No. frequency
              0    31.25 Hz
              1    62.50 Hz
              2   125.00 Hz
              3   250.00 Hz
              4   500.00 Hz
              5    1.00 kHz
              6    2.00 kHz
              7    4.00 kHz
              8    8.00 kHz
              9   16.00 kHz


There is also a commandline example in the man pages:

> 
EXAMPLE:
mplayer -af equalizer=11:11:10:5:0:-12:0:5:12:12 media.avi
Would amplify the sound in the upper and lower frequency
region while canceling it almost completely around 1kHz.


and I guess if you were using this exact setting in your config file it would be:

```
af=equalizer=11:11:10:5:0:-12:0:5:12:12
```

with each integer representing a gain in decibels for each of the frequency bands with a possible range of -12 to 12. Don't forget that there is an equalizer for video as well that also has many, many settings starting with 'vf=eq2=' etc etc :-). Is this not incredible software??

Andrew

---

### Post by cycle_mycle on 2009-04-24
Hi Andrew

Thanks for your excellent knowledge in helping me figure this out. I did it by command line as you said and it seems to work. I'm not sure because I can't open the EQ when it's done cli...

But there is much better sound, seems it would be due to the EQ settings.

But also I would rather do the opening of files through the gui because I'm not the only one watching videos and to get my wife to use the command line is... well... you know....

So actually I'm back to square one. I entered the text in mplayer.conf:

af=equalizer=-8:-6:-4:4:8:8:3:1:-3:-6

My settings need to be mids up and lows/highs down.

Once again it can't be proven because in the gui EQ settings are all flat, whether they are adjusted and not being represented is not sure.

This is an intriguing discussion isn't it?

And yes this is incredible software.

Thanks for all your help, I guess I'm just going to have to sift through the man pages, I was hoping to get an easier solution.

Thanks again!

---

### Post by andrew.46 on 2009-04-24
Hi cycle_mycle,

> **cycle_mycle said:**
> Thanks for all your help, I guess I'm just going to have to sift through the man pages, I was hoping to get an easier solution.

Well there might be an easier way.... Do you use SMPlayer? If not install it and have a look at the audio equaliser settings which, as mc4man mentioned in his previous post, has a setting 'Set as default values'. I attach a screenshot showing details. Perhaps this might be more what you are after?

Andrew

**Edit:** My apologies mc4man for temporarily overlooking the fact that you had *already* suggested this.... I am getting old and slow :-).

---

### Post by cycle_mycle on 2009-04-26
Ok, that was easier, I can't say it was all that clean though.

I was able to install SMPlayer and set it so that it saves the settings. Now MPlayer is broken but SMPlayer works. 

It does give a warning that MPlayer isn't at the newest version and some features have been turned off. (????)

I was hoping not to have KDE stuff and Gnome stuff mixed up but that seems like the price I have to pay. It does work well I admit that. Maybe I just have to go with Kubuntu after all.

Thanks for all your help, mc4man looks like you had the winning suggestion after all and I'm grateful, thank you very much.

See ya round guys!

---

### Post by andrew.46 on 2009-04-26
Hi cycle_mycle,

> **cycle_mycle said:**
> It does give a warning that MPlayer isn't at the newest version and some features have been turned off.

The repository version of MPlayer, which I suspect you are using, is almost 2 years old now. There is a litany of reasons why this is so but the result is always a little unfortunate.

You may very well get enough functionality from the version you have in which case you should be happy :-). However if you start bumping against some limits it may be worthwhile having a look at [rvm's PPA]("https://launchpad.net/~rvm/+archive/ppa") where he generously provides not only packages for SMPlayer but MPlayer as well. Another alternative would be to hunt out a guide for the svn MPlayer which I believe can be found somewhere on these forums...

But if you are happy with your current setup stay there and enjoy a great program :-). BTW the qt4 libs you have downloaded are quite small and should have no great effect on your system.

All the best,

Andrew

---

### Post by cycle_mycle on 2009-04-28
Well this has been an adventure. I learned a bunch! Way to go team!

I see that after installing smplayer that the levels go as far as 120 db so the 20 or so db wasn't making a whole lot of difference.

And the other thing is, the graphical EQ shows "flat" but it is actually at the levels placed in the mplayer.conf file.

I'm still experimenting but so far have wound up at:

af=equalizer=10:20:40:80:100:100:80:40:20:10

So there you go....

Thanks andrew.46 and mc4man for all your help.

---


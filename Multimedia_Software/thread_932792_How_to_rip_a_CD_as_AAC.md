---
title: "How to rip a CD as AAC?"
date: 2008-09-28
forum: Multimedia Software
---

### Post by SlaughterDog on 2008-09-28
Alright, I won an iPod shuffle. I'm pleased to see that Rythmbox can put music on it. But, seeing as the iPod only plays MP3 and AAC, and MP3 is a horrid format that should have died years ago, I need help ripping CDs as AAC. 

I see there's a GNOME profile for ripping AAC but it doesn't come up in the choices for ripping in either Rythmbox or Sound Juicer. So, how do I rip AAC? Perhaps there's some conf file I can edit to get AAC in the lists of choices?

---

### Post by hansdown on 2008-09-28
Hi SlaughterDog.

This video should help.

[http://ca.youtube.com/watch?v=zHIYKGfyYuY](http://ca.youtube.com/watch?v=zHIYKGfyYuY)

---

### Post by mc4100 on 2008-09-28
> **hansdown said:**
> Hi SlaughterDog.

This video should help.

[http://ca.youtube.com/watch?v=zHIYKGfyYuY](http://ca.youtube.com/watch?v=zHIYKGfyYuY)

This video won't help, simply because AAC isn't showing up the in the prefernces window; if you're sure all the proper codecs are installed, then create a new profile...
In the Gstreamer pipeline box, paste:
```
audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4
```
And set the extension to ".m4a".

---

### Post by SlaughterDog on 2008-09-28
Oh, lemme guess, the codecs don't come installed by default. How do I install them? And when I do, will it automatically let me choose AAC in the rip type list?

---

### Post by mc4man on 2008-09-29
You need faac (a lib will install with it - libfaac0

```
sudo apt-get install faac
```


edit; while i never have used rhythmbox a quick check shows it does aac fine. Should be no need to create a profile unless you want to lower the file size. The default seems to be -q 0.5  (approximately  1mb per min.

---

### Post by SlaughterDog on 2008-10-01
Alright, I've got the codec installed, but can you tell me a bit about how to set the quality? You mentioned -q 0.5 but can you tell me a bit more about that? I'm used to doing things on Windows where I just punch in a bitrate like 320k.

---

### Post by mc4man on 2008-10-02
i never use rhythmbox for ripping (rubyripper) nor aac much, so I can't tell you how you change the quality(bitrate) with that app (up or down
A little fooling around suggests rhythmbox is encoding aac at around 128k.

The -q i mentioned was somewhat based on using neroAacEnc for linux from the cli (not really suitable for cd's (128k = -q 0.385

If you want higher quality acc using either grip or rubyripper i can help you there to some extent.

Grip also is able to use neroAacEnc (using a target bitrate (easy to do /understand

---

### Post by SlaughterDog on 2008-10-04
I used Sound Juicer, and am playing it back with Rythmbox and Totem. It has a wah-wah effect for some reason, so I wonder if the codecs were not good, for either encoding or playing. 

I just tired putting it on the iPod and the iPod won't play it. I also tried using Rthymbox to plop an mp3 on. 

Well, as much as I hate MP3, I'm going to have to use it I guess. No biggie I guess, considering I'll only use it in crappy iPod headphones anyway.

edit: so how do I change the rate at which it encodes? It's doing them as 128Ks.

---

### Post by mc4man on 2008-10-06
If you want to use either rubyripper or grip then I can show you how to adjust the bitrate (cbr) or 'quality' (vbr). (using neroAacEnc
I got rubyripper also able to use neroAacEnc as the encoder and using the -q settings it does very well. Am actually considering using instead of flac your use on a decent pc sound system.

As far as rhthymbox and sound-juicer can't help, though a little fooling around shows that editing the audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4 line 'improperly' in either app or in gconf will only result in losing the ACC option altogether (you get one shot at it

For neroAacEnc
dl from here
[http://www.nero.com/eng/down-ndaudio.php](http://www.nero.com/eng/down-ndaudio.php)
unpack and for grip put the neroAacEnc file in either home directory or /usr/bin (rubyripper requires /usr/bin
(** make it executable** (run chmod +x on it 

Settings in grip 
Click on the confige tab, then the encode tab. Choose other from the Encoder: drop down

Use this, red is adjustable (grip is touchy about 'mistakes' copy and paste


```
-if %w -of %m -br [COLOR="Red"]320000[/COLOR] -2pass
```


Set the extension to m4a
By default grip will save to a folder in home named ogg, may be changed carefully, you don't need to create the folder first, just provide path
(what I'm posting also numbers the tracks(in blue

Ex. saving to Music folder in home, numbering tracks[COLOR="Red"][/COLOR]

In the 'Encode file format box'
```
[COLOR="Red"]~/Music[/COLOR]/%A/%d/[COLOR="Blue"]%t[/COLOR] %n.%x
```

Under the options tab in the M3U file format box adjust save location also
If you have reason to want the M3U in the music folder with the songs use this format

```
[COLOR="Red"]~/Music[/COLOR]/%A/%d/%d.m3u
```

I'd suggest using grip a few time to test before changing anything (also try the default faac encoder

For rubyripper (neroAacEnc must be in /usr/bin

open RR and click on preferences, click codecs tab.
Check the other box and enter this. (RR will create and save to an 'other' folder in home (note RR will encode to multiple formats at once so ck. or un ck. as desired

```
neroAacEnc -q 0.[COLOR="Red"]75[/COLOR]  -if %i -of "%o.m4a"  -w --artist "%a" --title "%t" --genre "%g" --album "%b" --track %n --year "%y" %i -o "%o".m4a
```

Red is adjustable - leave the 0. and use anything from 24 - 95 (likely overkill
A setting of -q 0.385 is around 128k, a setting of -q 0.78 is about 320 LC ( note this is a vbr setting.
The naming convention is what i like, adjust to suit


If you have any problems ,mistakes in grip then you can set back to default state by going into home folder, scroll to bottom and delete any .grip files you find (up to 4 or 5 I think) and try again or not

Edit
faac in grip

using -q seems best though it responds better to using xxx than 0.x
This produces around 192 k LC (setting  - quantizer quality
```
-q [COLOR="Red"]180[/COLOR] -o %m -w --artist %a --title %n --genre %G --album %d --track %t/%N --year %y %w
```
The increment in br isn't too logical, around 340 produces 256k (screen 2
or 
This way produces an average - not as good a method I don't think
```
-b [COLOR="Red"]192[/COLOR]k -o %m -w --artist %a --title %n --genre %G --album %d --track %t/%N --year %y %w
```
this produces around 160k LC

---

### Post by SlaughterDog on 2008-10-06
Thanks for the help, people.

I am still trying to use Rythmbox to put the files on my iPod, and I found that sometimes the ipod will play, sometimes it won't, but it also seems that it plays ogg files!

Edit: My bad! the ipod doesn't play ogg files, rather, rythmbox converts automatically to mp3 when it puts it on the ipod.

---

### Post by FakeOutdoorsman on 2008-10-06
I use abcde to rip to ogg vorbis, flac, and mp3 while automatically adding the tags.  It can also encode aac, but I've never tried that:

[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

---

### Post by andrew.46 on 2008-10-31
Hi FakeOutdoorsman!

> **FakeOutdoorsman said:**
> I use abcde to rip to ogg vorbis, flac, and mp3 while automatically adding the tags.  It can also encode aac, but I've never tried that:

[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

I have actually beefed up the andrews-corner abcde page a little and included musepack as well. I was considering adding a faac section as well in a week or so although I believe better aac encoding is allowed by the Neroaac encoder. But the abcde script does not support this :(.

  Andrew

---

### Post by FakeOutdoorsman on 2008-10-31
> **andrew.46 said:**
> Hi FakeOutdoorsman!

I have actually beefed up the andrews-corner abcde page a little and included musepack as well. I was considering adding a faac section as well in a week or so although I believe better aac encoding is allowed by the Neroaac encoder. But the abcde script does not support this :(.

  Andrew
Hey Andrew,

Thanks for the update on your abcde page.  I don't encode to aac often (excluding video).  What advantages does Neroaac have over faac?

---

### Post by andrew.46 on 2008-10-31
Hi:

> **FakeOutdoorsman said:**
> Hey Andrew,

Thanks for the update on your abcde page.  I don't encode to aac often (excluding video).  What advantages does Neroaac have over faac?

Well, my own tests show that neroaacenc *sounds* better than faac but a better test is seen on the [faac website]("http://www.audiocoding.com/faac.html") where the creator of faac says:

> Note that the quality of FAAC is not up to par with the currently best AAC encoders available.

And you will note a link (admittedly a dead one) to 'Nero AAC Codec' at the top of this page.

As for abcde I have actually just uploaded yet another update as I have finally worked out how to set single-artist and various-artist settings. Took a while :-). The faac section should be easy enough but I like to test a lot and the encoding can take a while on my old computer.

  Andrew

---

### Post by Yashiro on 2009-02-28
Nero is slightly better than FAAC that's certain. Mostly due to some echo and munging on Metal/High Frequencies. Bass wise FAAC is less clear and more grungy too. On some tunes this is actually better.

If the music is for use on a portable device it really doesn't matter if you use Nero or FAAC though. FAAC's default settings produce smaller files, if you're a lazy sort. If you want better quality from a lossy codec switch to Ogg. (q5 to q8). 

**Has anyone worked out how to use abcde with the Nero AAC encoder yet? **
With full tagging support. It must be possible but I gave up fishing through the config file after an hour of failed tests. It must be simple and I'm not seeing it.

Getting NeroAAC to work with Grip took some messing around but it works perfectly.
Just add NeroAacEnc as other, and NeroAacTag into the Encode filter command.
```
usr/local/bin/neroAacTag %m -meta:artist="%a" -meta:album="%d" -meta:track="%t" -meta:title="%n" -meta:genre="%G" -meta:year="%y"
```

Additionally, If anyone needs updated CDParanoia packages you can get them pre-packaged from the Debian Lenny pages.

After trying Juicer, abcde, manual scripts and Grip I prefer Grip.
It reminds me of EAC which I used alot in my Windows days.

---

### Post by jmdennis on 2009-03-14
I appreciate the extra information for grip.  I did the first one that was suggested but did not have the neroAacTag information so when I opened up banshee it did not recognize the artist or album.  I have also used atunes as well and it will recognize the nero aac encoder and even gives you instructions on how to set this up.  It will also tag them properly as well.  The one thing I did not like about this is that it did not get the information that was needed such as the genre and the year so this had to be entered but over all a good program.  Does grip recognize the quality listing as I would rather use this the the bitrate?

---

### Post by SuperSonic4 on 2009-03-14
```
faac -w -s -q 200 <input file>
``` will work from a wav file and will encode to m4a. It doesn't seem to work with mp3 and I'm not totally sure how to retain the metadata

-w : encode to m4a
-s : optimise the m4a file
-q : vbr quality (200 equates to about 190kbps)

---

### Post by Yashiro on 2009-03-14
> Does grip recognize the quality listing as I would rather use this the the bitrate?
Yes.

---

### Post by andrew.46 on 2009-03-15
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> I use abcde to rip to ogg vorbis, flac, and mp3 while automatically adding the tags.  It can also encode aac, but I've never tried that:

[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)
[http://www.andrews-corner.org/abcde.html](http://www.andrews-corner.org/abcde.html)

You may be interested to see that I have *finally* added an AAC section to the abcde web page:

[http://www.andrews-corner.org/abcde.html#aac](http://www.andrews-corner.org/abcde.html#aac)

I held off for some time until I noticed the other day that there was actually an Ubuntu patch that allowed automatic tagging of aac files, something that was broken in the 'release' version of abcde. Pity there is no 'upstream' to submit this patch to :(.

Just for a bit of fun you could try the 'combo' version and really see the magic of abcde at work:

[http://www.andrews-corner.org/abcde.html#combo](http://www.andrews-corner.org/abcde.html#combo)

How cool is that!!

Andrew

---

### Post by FakeOutdoorsman on 2009-03-17
> **andrew.46 said:**
> Hi FakeOutdoorsman,



You may be interested to see that I have *finally* added an AAC section to the abcde web page:

[http://www.andrews-corner.org/abcde.html#aac](http://www.andrews-corner.org/abcde.html#aac)

I held off for some time until I noticed the other day that there was actually an Ubuntu patch that allowed automatic tagging of aac files, something that was broken in the 'release' version of abcde. Pity there is no 'upstream' to submit this patch to :(.

Just for a bit of fun you could try the 'combo' version and really see the magic of abcde at work:

[http://www.andrews-corner.org/abcde.html#combo](http://www.andrews-corner.org/abcde.html#combo)

How cool is that!!

Andrew
Excellent!  Although I must admit I'll stay with OGG.  I actually ran across your abcde page and promptly used those configs long before I knew you were that Andrew.  I made some aliases to switch between config files:
```
alias ogg='rm -f ~/.abcde.conf && cp ~/.abcde.conf.ogg ~/.abcde.conf'
alias mp3='rm -f ~/.abcde.conf && cp ~/.abcde.conf.mp3 ~/.abcde.conf'
```

---

### Post by andrew.46 on 2009-03-17
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> I actually ran across your abcde page and promptly used those configs long before I knew you were that Andrew.

Well I have almost completed the section of the abcde page that deals with Speex encoding as well :-). Mind you even the Ubuntu abcde lacks the correct patch for the speexenc tagging I have found. I have it working well now once I found the right patch, or more correctly pieces of *several* patches.

> I made some aliases to switch between config files:
```
alias ogg='rm -f ~/.abcde.conf && cp ~/.abcde.conf.ogg ~/.abcde.conf'
alias mp3='rm -f ~/.abcde.conf && cp ~/.abcde.conf.mp3 ~/.abcde.conf'
```

Very nice. I was thinking about putting something together like that. Have you had a look at the '-c' option in abcde which might make it all a bit neater? I have not tested this but that was the path I was going to follow.

Andrew

---

### Post by FakeOutdoorsman on 2009-03-17
> **andrew.46 said:**
> Hi FakeOutdoorsman,
Very nice. I was thinking about putting something together like that. Have you had a look at the '-c' option in abcde which might make it all a bit neater? I have not tested this but that was the path I was going to follow.

Andrew
Hi Andrew,
Ahh...thanks for the tip.  I should read the man pages more often.

---

### Post by andrew.46 on 2009-03-18
Hi FakeOutdoorsman,

> **FakeOutdoorsman said:**
> Hi Andrew,
Ahh...thanks for the tip.  I should read the man pages more often.

I thought you might have missed that particular entry in the man page :-). [Speex section now in place]("http://www.andrews-corner.org/abcde.html#speex") and I think my abcde labours are at an end. Incidentally I suspect that Speex encoding through abcde may very well be broken in Ubuntu, the patch applied by Luke Yelavitch does not completely fix the problem. I solved the problem by extending his patch with another I filched from Fedore. The lack of any concern or bug reports is probably a good demonstration of how many people actually encode to Speex with abcde I guess :-).

Andrew

---


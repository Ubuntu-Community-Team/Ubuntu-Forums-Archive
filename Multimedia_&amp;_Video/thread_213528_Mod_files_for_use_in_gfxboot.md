---
title: "Mod files for use in gfxboot"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by Henrik on 2006-07-11
Hello,

I'm wondering if any of you would be able to help me find some simple sound samples for use on the live CD. [This spec](https://wiki.ubuntu.com/Accessibility/Specs/LiveCdAccess) describes our plans for making a boot menu suitable for visually impared people. We plan to have the different menu options represented by different sounds. 

For whatever reason gfxboot only understands mod files (I guess much of gfxboot is assembler code from old demos). As there are several kinds of these, I don't even know what kind gfxboot wants or to what extent it matters. From  the code I think it wants 11kHz samples.

I'd appreciate it if someone could shed some light on modfiles for me, which apps on ubuntu would be best for making them from wav samples, say. And also it would be great if people had good ideas for the actual samples. I need about 8 sounds that are quite distinct from each other, but only 1-2 seconds long and not too ear-drum-splitting :)

Thanks for any help!

---

### Post by Sheik Yerbouti on 2006-07-11
Here is a web site with creative commons licensed sounds [http://freesound.iua.upf.edu/](http://freesound.iua.upf.edu/). 

I have played around a bit with skale tracker (mod tracker) and it looks pretty good.

[http://skale.binarydeception.com/](http://skale.binarydeception.com/)

---

### Post by Henrik on 2006-07-12
Unfortunately all the samples on that page seem to be under the [CC Sampling license](http://creativecommons.org/licenses/sampling+/1.0/) which is too restrictive for our use. We might be able to get a sample licensed as GPL or even public domain if we ask the artist individually though.

For the Skale tracker I could only find a Windows version, is that right? Anyone have experience with Rosegarden?

---

### Post by Sheik Yerbouti on 2006-07-12
Yeah the zip file for skale tracker has both a Windows and Linux x86 binary so it is just one file. 

I use Rosegarden as my primary tool on Linux it is quite good. However I am not sure it will save a mod file for you. It is a midi sequencer however there are as I undestand it midi to mod conversion tools. 

Mods are like sequenced midi but with the original samples wrapped up in the file along with the definition of when and how to play them. Midi is just like a music score and contains no sample data (you may already know this if so sorry).

Here's a good about the mod article

[http://www.linuxjournal.com/article/4349](http://www.linuxjournal.com/article/4349)

Maybe I will take a look at this tonight when I get home. See what I can come up with.

---

### Post by Henrik on 2006-07-13
Cool!

I stopped off at [http://www.modarchive.com/](http://www.modarchive.com/) yesterday and visited their IRC channel. They were helpful in explaining mods to me a bit and sent me something called milkytracker.

---

### Post by Sheik Yerbouti on 2006-07-14
Ok so here is what I came up with.

[menusounds]("http://www.allenjeter.com/menusounds.tar.gz")

They are 11khz mod files.

I created them with my hardware synth. So they belong to me and I am giving them to you so you can do whatever you wish with them.

Cheers

---

### Post by Henrik on 2006-07-15
Cool! these are very nice! Quite distinct. I've uploaded them [here](https://wiki.ubuntu.com/Accessibility/Specs/LiveCdAccess) and sent them to our gfxboot developer.

ROCK!

---


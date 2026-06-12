---
title: "Problem with sound quality"
date: 2007-05-10
forum: Multimedia &amp; Video
---

### Post by psychoadonis on 2007-05-10
Just got Feisty working... all's well (yet) except the sound.

When I first tried to play a mp3/divx/xvid video, totem asked me if I wanted to download soem drivers. The list showed 3 packages out of which 1 was popular the other 2 were not. I installed all 3 anyway.

Now the songs do play, but the quality is very bad. The problem is certainly not with the speakers coz they play well on windows.

Please help.

---

### Post by blueturtl on 2007-05-10
Do you have PCM volume set to 100%? Most soundcards overload if you set PCM to full power and it causes the sound to distort badly.

---

### Post by Benitez on 2007-05-10
[SIZE="3"]
I am also having sound problems; whenever I try to play either a mp3 file or video file, the sound works completely fine. The only problem is that there is some sort of crackling noise.

At first, I thought it was that something may have happened to the files; however, I downloaded some of them again to my laptop and they still have the same problem. I also very recently upgraded to Feisty, and I thought that maybe it had something to do with parts of files (possibly?) being overwritten; however, I am not sure what is causing this...

Does anyone else have a problem like this?
[/SIZE]

---

### Post by ADT on 2007-05-10
As blueturtl said, it's to do with PCM volume being too high.

Open a terminal

type:
alsamixer

Alsamixer allows you to change volume settings.

Use the up and down arrow keys on the keyboard to change the PCM volume.
Change PCM so it has a dB gain of 0.00 which is a volume of 74.

Do the same for the master volume (dB gain of 0.00)

That worked for me.

---

### Post by psychoadonis on 2007-05-11
Hi, thanks...

I reinstalled Ubuntu (removing XP et al).
Now the problem is that I can't hear any sound at all. I tries the alsamixer thing, to no effect. No matter at what volume I set it at, I cant hear anything.

The only sound is a few bursts of static (when the volume in the movie/song suddenly goes up/down).

---

### Post by blueturtl on 2007-05-11
Does sound from others sources play ok (mp3s, CDs, the Ubuntu startup sound)?
What kind of soundcard do you have?

Have you tried other video players like xine-ui or mplayer?
They can be installed using the Synaptic package manager in System->Administration or in the command like with 'sudo apt-get install xine-ui mplayer'.

---

### Post by psychoadonis on 2007-05-11
Sound from everything sounds the same. mp3s, DVDs, divx/xvid files, even Ubuntu startup.

In hardware information, it says that the sound card I'm using is SB450 HDA Audio made by ATI Technologies Inc.

And I tried playing with "gxine" and "Kaffeine". Same problem.

---

### Post by blueturtl on 2007-05-11
Ouch. Ati does not play well with Linux. I'm sorry bud but you may be out of luck.

You could try another distribution (Mepis, Mandriva etc) and see if they also have a problem with your sound card. Since it works in Windows we know the hardware is not faulty. If it works on any other Linux system we know the problem is probably driver-related.

If you want the easy way out, you could shell a few bucks to buy a used SoundBlaster Live! or Audigy.
Otherwise Google and these forums may be your best friend. Sorry I can't be of more help. :(

---

### Post by otual on 2007-05-13
Thanks ADT re your earlier post regarding alsamixer

I had the machine playing really well then must have turned the PCI level up too high. without even realising. Was starting to get really frustrated as I've just worked out how to use Rhythmbox to play music stored on one of the machines on my network (about 70GB)  

Its back to normal again thanks again 

:guitar:

---

### Post by niktheblak on 2007-05-13
> **Benitez said:**
> 
Does anyone else have a problem like this?

I do. I even made a [thread]("http://ubuntuforums.org/showthread.php?t=440955") about it. Haven't been able to solve the problem though.

---


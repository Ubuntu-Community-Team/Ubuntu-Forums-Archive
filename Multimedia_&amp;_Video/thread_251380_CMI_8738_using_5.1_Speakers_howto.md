---
title: "CMI 8738 using 5.1 Speakers howto ??"
date: 2006-09-05
forum: Multimedia &amp; Video
---

### Post by zmoink on 2006-09-05
Hi ...

I have a Genius Soundmaker Live 5.1, who's chipset is a CMI 8738 .

However alsa configurations, doesnt let me change to the 5.1 speakers set ... only to 4 speakers.
In this way, only my rear (left and right) and front (left and right) speakers play anything, letting apart the bass and the the rear center speakers unused ...
Has anyone with this chipset solve this issue ??

The goal is to have the 5.1 speakers set fully working ... :-D 

All the speakers are working because in Windows (the O. S. that sucks):(  the sound system fully works ... so the problem is really from the configuration or the driver ...

has anyone solve it ??
Any clew ??


cheers ...

PS :

I used ubuntu dapper (6.06) and my lspci exit is :

**0000:00:0b.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)**


Ps2 :
This is not a new problem because since i bought this soundcard, a few years ago, this issue remains ... so i think that isn't a "bug" of alsa, but yes, lack of information ... or configuration for the several variants of this soundcard ...

---

### Post by amrypma on 2007-01-03
I am also very interested in how to do this.

---

### Post by zmoink on 2007-01-03
well it seems that nobody knows the answer ... :(

---

### Post by pseudonym on 2007-01-03
Hi, I once owned a motherboard with this sound chip. It was only the 4-channel variety but during my Linux travels I remember coming across [this]("http://opensrc.org/alsa/index.php?page=cmipci") document written by the ALSA developer responsible for the 'cmipci' module.

Basically, to enable 6-channel output, you'll need to write a .asoundrc file which you put in your home directory. This file gives you more advanced control over your ALSA configuration. The above document shows you how to create one, among other things.

HTH :)

---

### Post by zmoink on 2007-01-04
i'll see if it works ... thanks!!!

---

### Post by gaiterin on 2007-03-13
Hi.
I have the same problem.
The url not exist :(
Can you put your .asoundrc file?
Thanks very much!
Mar.

---

### Post by italoivo on 2007-03-23
i did my pci cmi 8738 sound card work with my 5.1 using the .asoundrc file found here [http://alsa.opensrc.org/Cmipci](http://alsa.opensrc.org/Cmipci)

---

### Post by gaiterin on 2007-03-23
My solution is here:
[http://ubuntuforums.org/showthread.php?t=385794](http://ubuntuforums.org/showthread.php?t=385794) ;)

---

### Post by Chymera on 2007-07-27
aha, very clever and creative of you, pointing to others' explanations which seem to run around in circles. Its about the 3rd time im running through all the 5.1-CMI8738-related threads around here and the fact remains that no one has been able to make a single straight-forward post. Ive tried making new threads, talking about fixing the issue in gutsy, reviving old threads. and all that anyone has managed to do is either point to some ancient discussion on the alsa website, or to a guide which probably applies to some linux distro from the first 3 years of this millennium, OR, more frequently just said it should be natural for alsa to work. WELL ITS NOT! ITS F*IN' BUSTED, it dosnt work and im not the only one complaining.

The only ppl who seemed to say it worked for them mostly had only one post :-/ that seems strange to say the least... 
So how, if at all, did you get it to work?

---

### Post by ^rooker on 2007-09-23
I'm using the same soundcard - and here is how **it works for me** (running Ubuntu Dapper):

"asoundconf list" says:
> Names of available sound cards:
CMI8738MC6

I've used a combination of the above posted .asoundrc and the one mentioned in this [ALSA multi-channel Audio mini-HowTo]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml"). Here's the result:

```
# upmixing:
pcm.ch51dup {
	slave.pcm surround51
	slave.channels 6
	type route
	ttable.0.0 1
	ttable.1.1 1
	ttable.0.2 1
	ttable.1.3 1
	ttable.0.4 0.5
	ttable.1.4 0.5
	ttable.0.5 0.5
	ttable.1.5 0.5
}

pcm.duplex {
	type asym
	playback.pcm "ch51dup" # upmix first
	capture.pcm "hw:0"
}

# change default device:
pcm.!default {
	type softvol
	slave.pcm "duplex"
	control {
		name "Software Master"
		card 0
	}
}

# for aoss
pcm.dsp "duplex"
pcm.dsp1 "duplex"
```

Here's how I've tested it:
1) surround 5.1 mode:
```
speaker-test -c 6 -D surround51
```

2) default 2 channels upmixed to replay on all 6 speakers:
```
speaker-test -c 6 -D default
```

---

### Post by Azyx on 2007-11-12
Thanx. It worked, I think :). But I'm not familiar with terminology off 5.1 sound.
When it test LFE, i don't hear anything..When I run speaker-test my subwoofer always sounds, exept when LFE is tested.

How do I regulate the different speaker?

/Azyx

> **^rooker said:**
> I'm using the same soundcard - and here is how **it works for me** (running Ubuntu Dapper):

"asoundconf list" says:


I've used a combination of the above posted .asoundrc and the one mentioned in this [ALSA multi-channel Audio mini-HowTo]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml"). Here's the result:

.asounic-file

Here's how I've tested it:
1) surround 5.1 mode:
```
speaker-test -c 6 -D surround51
```

2) default 2 channels upmixed to replay on all 6 speakers:
```
speaker-test -c 6 -D default
```

---

### Post by xzero1 on 2007-12-03
I use the digital output from my 8738 based soundcard. I can get 5.1 sound playing some dvds, but not with any games or apps. Does this code work with digital output? I have tried your code but it does not seem to work -- no sound. Any ideas?

---

### Post by gaiterin on 2007-12-04
Hi!
You must configure the application for 5.1 (Example Totem) ;)
You only hear 5.1 if the video recorded in 5.1 (DVD, Divx AC3, etc).
A normal Divx is 2.0 ;)
Regards.
Marquinos.

---

### Post by xzero1 on 2007-12-08
Thanks for the help, but since I use the digital output your configuration does not work for me.  If I understand it correctly, the posted .asoundrc is a stereo upmix to 5.1 channels. What I was looking for was a "Dolby Digital Live" type of solution. I have found something that purports to do this : [http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF)]("http://gentoo-wiki.com/HOWTO_Dolby_Digital_Out_(AC3,_SPDIF)")

The only game I have installed is Nexuiz and though it seems to sound better, it does not work on anything higher than "stereo".  Perhaps its the game.

---

### Post by Yellow Pasque on 2007-12-08
Some cards work better under OSSv4. For example, when I switched, I finally had my headphone jack on my M-Audio Revo working with a separate volume control. If anyone wants to give it a try, the link is in my sig.

---

### Post by gaiterin on 2007-12-08
Hi!
Did you see this?
[http://ubuntuforums.org/showthread.php?t=385794](http://ubuntuforums.org/showthread.php?t=385794)
Regards.
Marquinos.

---


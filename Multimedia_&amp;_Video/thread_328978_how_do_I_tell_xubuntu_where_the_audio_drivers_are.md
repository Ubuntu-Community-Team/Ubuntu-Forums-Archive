---
title: "how do I tell xubuntu where the audio drivers are?"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by akajonesy on 2006-12-31
how do I get the drivers for my sound card to register with xubuntu? 
Im using the CS4237b (Cirrus logic/Crystal) integrated sound card.

I've done everything I've found online, but still no joy.
I'm fairly certain the files are installed, but not a clue how to tell xubuntu to use them.

---

### Post by pseudonym on 2006-12-31
Hi, It's an ISA sound chip, right? Have you done something similar to this (it's for a soundblaster)? - ```

add snd-sb16

to /etc/modules then create a new file:

gedit /etc/modprobe.d/sound

and enter this line:

options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5

sudo update-modules

reboot 
```

---

### Post by akajonesy on 2007-01-01
tried it. Didn't work.

I did follow the instructions found both in the alsa-project site as well as in the "comprehensive sound problems solution" site in the ubuntu forums, and neither worked.
I have found some files with the same name as that for the ALSA drivers (from alsa-project.org) in the "/lib/modules/2.6.17-10-generic/kernel/sound/isa" folder and Im just wondering if there is something I'm not doing to tell xubuntu to look there for the drivers...

---

### Post by pseudonym on 2007-01-01
You don't have any other ISA cards in the machine (bad idea)? Did you go into your BIOS and reserve 'ISA Legacy Resources' (or similar) for the card?

I once had a PII with an onboard ISA Crystal audio. It worked OK with Debian, but it was a lot of trouble to get going, and had pretty crappy sound quality. In the end I just disabled it in the BIOS, and bought a $2 PCI soundblaster card on ebay, and wondered why I didn't do that in the first place :)

---

### Post by akajonesy on 2007-01-01
No other soundcard in there.
It's an older laptop (which is why I went with xubuntu) that I use for basic office work stuff. 
As is, it's running a fair bit faster than it did on Windows 2000 (what it had been on before).
I don't really NEED the sound working since I can always just use the mp3 player, but I am new to linux and am using this as a learning experience.

Frankly, it's a bit unfair to try to get xubuntu using hardware that's not really supported, but like I said, learning to do the hard stuff makes the easy stuff easier. :) 

For what it's worth it's a Dell Latitude Cpi 300Mhz w/128 of RAM. So as you can see, not exactly state of the art. Heck I think the graphic chip is only 2megs or somesuch.

---

### Post by pseudonym on 2007-01-02
I don't really know anything about laptops, but I'm sure there is still some cheap but better and easier to set up sound solution out there for you.

You're right that learning the hard stuff makes the easier stuff easier. But if the hard stuff involves a lot of headaches getting a particular piece of no longer manufactured and supported hardware working (I mean just the soundcard, not the laptop), with an almost certain likelihood of underwhelming results even if you do, and there is likely to be a better option readily available, then it makes more sense to jump to the easy stuff in IMHO.

But I'm sure you've already thought of all this, anyway. :)

---

### Post by akajonesy on 2007-01-02
> **pseudonym said:**
> But if the hard stuff involves a lot of headaches getting a particular piece of no longer manufactured and supported hardware working (I mean just the soundcard, not the laptop

true, but I'm ALMOST sure that the drivers are already included (leastwise it's in the ALSA list, and there are instructions on their web site to instal them). I just can't figure out (yet) how to make the OS aware that it's there. :)

---

### Post by Cathead Fred on 2007-01-02
Hi akajonesy,

  Have you searched Linux On Laptops? Your answer could be there. A quick check of their website revealed this link: [http://eulex.0nyx.com/cs4237b.html](http://eulex.0nyx.com/cs4237b.html)

  You can also try Tuxmobil.org at the sound section: [http://tuxmobil.org/sound_linux.html](http://tuxmobil.org/sound_linux.html)

  Post your progress.

  Good Luck,
 
 Cathead Fred

---

### Post by gtmaneki on 2007-01-02
This sounds like a similar problem I was having when I instialled Xubuntu 6.06 on a ThinkPad that had a CS4237 sound card.  LordRaiden's [**howto here**]("http://www.ubuntuforums.org/showthread.php?t=205449&highlight=intel+audio+driver") helped me out quite a bit.  It's a long post that addresses a lot of problems, so I'll post a summary from his guide that helped me:

[LIST]
Download the necessary packages: sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
[*]Configure: sudo dpkg-reconfigure alsa-source
[*]Select the applicable drivers. I have read that both CS4326 and CS4232 work, so I selected these.
[*]Compile: sudo module-assistant a-i alsa-source
[*]Module load: modprobe cs4236 io=0x530 irq=5 dma=1 dma2=0 mpuio=0x330 mpuirq=7 synthio=0x330 synthirq=7 (Note that these parameters came from the [**ThinkWiki**]("http://www.thinkwiki.org/wiki/Category:380XD") website and are specific for the ThinkPad 380XD.  You may need something else instead.)
[*]Test with alsamixer.
[*]To make sure this module loads at start, type sudo vi /etc/modules . In this new file, type snd-CS4236 and save.
[*]Save the alsamixer settings: sudo alsactl store 0
[/LIST]

I hope this helps!  I was tearing my hair out for the better part of a week until I found this solution.

---

### Post by akajonesy on 2007-01-02
cathead fred: I KNEW I'd seen a site for linux on laptops someplace... Thanks for finding it for me again! :D 

gtmaneki: I actually did follow that tutorial, but no dice. Thing is, I THINK the sound is in a different modules folder from what is in the tutorial. Im still not clear on the file structure in linux though, so I may be misinterpreting what Im seeing. ](*,) 
I tried a bunch of stuff, so I'm thinking I may also be giving conflicting instructions to the thing, so I'm going to try what cathead wrote, and if that doesn't work, reinstall and try LordRaidens tutorial again.

---

### Post by akajonesy on 2007-01-03
reinstalled and trying lordraidens howto but now I can't apt-get alsa-source (says cant find package).... argh.

---


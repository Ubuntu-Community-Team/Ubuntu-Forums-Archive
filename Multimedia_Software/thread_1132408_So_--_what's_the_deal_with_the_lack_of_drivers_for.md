---
title: "So -- what's the deal with the lack of drivers for Ubuntu???"
date: 2009-04-21
forum: Multimedia Software
---

### Post by lilychef on 2009-04-21
Hello, all!

In a nutshell -- I'm really tired of trying to figure out how to get my audio card to work.... I'm a recent Windows convert, and although completely sold on Ubuntu, I'm NOT happy with how difficult it is to get hardware working... I have what I consider to be a pretty high-level  audio card... I had all sorts of cool mixers and setting adjusters that came with it and worked with Windows, and now, with Ubuntu, all I have is 2.1 sound with no surround and no mixer, speaker control, etc... Pretty lame... It's a Creative X-Fi Extreme Audio, and yes - I'm already aware of the fact that drivers are "hard to some by" or "nonexistent", or in such a Beta mode that I can't afford to take a risk trying to install one..... but so what -- I want good audio!!!!!!!

Here's the deal:  rather than trying to get this P.O.S. card working right, is there a resource that references PREFERRED AND SUPPORTED HARDWARE for Ubuntu????  I even had to use an "unsupported driver" for my video card as well, and even it doesn't work great all of the time.....  Only with VLC...  I mean, I'd rather simply purchase the stuff that works and not worry about it rather than spending countless hours searching through forum posts to try to find (and ignorantly execute) 'fixes' for my issues...

I do NOT have the time to learn "architecture" or "programming" for Ubuntu.... Kudos to those who do, because they keep the system stable and secure, but I need a system that WORKS...  I am neither ignorant, nor stupid, and am capable of figuring out some pretty complicated computer stuff if necessary, but it shouldn't BE necessary... At least with Windows XP (God forbid I'm actually saying something GOOD about that awful OS), everything worked and the support was readily available...

For SURE I can't be the only one out there with similar frustrations...

Please - somebody just tell me in plain English what hardware to buy and I'll do it.  I'm tired of having choppy video and shitty sound...

Thanks in advance.

---

### Post by fballem on 2009-04-21
> **lilychef said:**
> Hello, all!

In a nutshell -- I'm really tired of trying to figure out how to get my audio card to work.... I'm a recent Windows convert, and although completely sold on Ubuntu, I'm NOT happy with how difficult it is to get hardware working... I have what I consider to be a pretty high-level  audio card... I had all sorts of cool mixers and setting adjusters that came with it and worked with Windows, and now, with Ubuntu, all I have is 2.1 sound with no surround and no mixer, speaker control, etc... Pretty lame... It's a Creative X-Fi Extreme Audio, and yes - I'm already aware of the fact that drivers are "hard to some by" or "nonexistent", or in such a Beta mode that I can't afford to take a risk trying to install one..... but so what -- I want good audio!!!!!!!

Here's the deal:  rather than trying to get this P.O.S. card working right, is there a resource that references PREFERRED AND SUPPORTED HARDWARE for Ubuntu????  I even had to use an "unsupported driver" for my video card as well, and even it doesn't work great all of the time.....  Only with VLC...  I mean, I'd rather simply purchase the stuff that works and not worry about it rather than spending countless hours searching through forum posts to try to find (and ignorantly execute) 'fixes' for my issues...

I do NOT have the time to learn "architecture" or "programming" for Ubuntu.... Kudos to those who do, because they keep the system stable and secure, but I need a system that WORKS...  I am neither ignorant, nor stupid, and am capable of figuring out some pretty complicated computer stuff if necessary, but it shouldn't BE necessary... At least with Windows XP (God forbid I'm actually saying something GOOD about that awful OS), everything worked and the support was readily available...

For SURE I can't be the only one out there with similar frustrations...

Please - somebody just tell me in plain English what hardware to buy and I'll do it.  I'm tired of having choppy video and shitty sound...

Thanks in advance.

Hopefully, this will help: [https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)

and welcome to ubuntu!

---

### Post by Pappy2003 on 2009-04-21
Here is a list of hardware here- [http://www.fsf.org/resources/hw](http://www.fsf.org/resources/hw)

---

### Post by lilychef on 2009-04-21
Thanks so much you guys for such a quick response!!  Will check it out and report back!

---

### Post by lilychef on 2009-04-21
So this is really the only thing I'm definitively seeing, unless I'm reading too much into it.... I've noticed that with most threads we're supposed to infer certain knowledge and simply "know what to do", which is most frustrating....



Make - Creative Labs
	

Model -Sound Blaster Awe 32/64
	

Chipset driver - snd-sbawe
	

Auto-detected - No
	

Works - Yes
	

Ubuntu Version - v5.10 (Breezy), v6.06 (Dapper), 8.10 (this is the only one I've mseen amongst ALL brands that specify 8.10 - am I to assume that Ones that work for Hardy (8.4) will work for Intrepid?)
	

Comments - Type "sudo nano /etc/modules" in terminal, then add "snd-sbawe" at a separate line, save, quite, restart. For 8.10- additionally add user (here x) to group audio by "sudo adduser x audio" and reboot.  (WTF? MORE stuff to 'program?)
	

Last updated - 2009-04-02

---

### Post by pbpersson on 2009-04-21
The deal with drivers in Linux is this - companies who manufacture the chips and the cards (video, audio, and network) know exactly how they work inside and THEY produce the drivers for Windows.  They do NOT provide the drivers for Linux and they refuse to release the specifications for the cards/chips so anyone else can write drivers because it is top secret proprietary information.

The drivers that exist in Linux therefore have been created mostly through trial and error by dedicated developers who do this as a hobby and work long hours into the night with little thanks or appreciation.

There are some cases where you might have to perform some configuration to get a driver to work with your card.

I have built three Ubuntu machines and all the drivers have worked perfectly and I didn't need to do anything.  However, the video, sound, and network controllers are built into the motherboard and I consulted the hardware list before I bought the motherboards.

Typically if something works on Hardy it will work on Intrepid.  If you have questions about a particular sound card, Google it with "Ubuntu" before the sound card and see what you get.

```
ubuntu "Sound Blaster Awe 32/64"
```

---

### Post by pbpersson on 2009-04-21
That appears to be an old ISA card.  Why are you looking at the specs for something from that long ago?  :o

---

### Post by Wiebelhaus on 2009-04-21
Community Supported:

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by wsonar on 2009-04-22
I've never had a problem with audio drivers in ubuntu on several systems I had a few buddies that had issues where the proper sound channel levels where not set correctly usually double clicking the sound icon on the panel and choosing the proper device and making sure the levels are set correctly
helps this issue

---

### Post by wolfen69 on 2009-04-22
start a new thread in the cafe, and ask what surround sound card people are using.

---

### Post by lilychef on 2009-04-22
> **pbpersson said:**
> That appears to be an old ISA card.  Why are you looking at the specs for something from that long ago?  :o

Because that's where the links provided SENT me....  Duh.

---

### Post by pbpersson on 2009-04-22
> **lilychef said:**
> Because that's where the links provided SENT me....  Duh.

NO.....my question is......are you using hardware from nine years ago?

This is 2009 now

---

### Post by lilychef on 2009-04-22
Ok... Thanks, guys....  I think I have somewhere to start now... and it looks like I'm from from done figuring  it all out.... But my beef remains-- that issues like this aren't made clear when peeps are switching over to Ubuntu....    Once again, you don't have to convince me that Microsoft is evil and the linux OS reigns supreme, but then again, people should be made aware that switching over isn't as easy as apple pie....  For example,  I spent three days trying to get Ubuntu installed on a friend's computer, and another day convincing him that it was better than Windows, when it was easy as pie to get it installed on mine.... and here I am with state-of-the-art hardware on a home-built, AMD system, and I can't get the sound and video working right....   It just makes the whole thing suspect, that's all....  Don't get me wrong -- I'm gung-ho and a permanent Linux convert, for sure; I just don't think I should have to go to school to learn how to get it working properly....

Just my two bits.  Thanks again....

---

### Post by lilychef on 2009-04-22
pbpersson - I have a Sound Blaster X-FI Extreme card that I bought less than a year ago.... And it DOESN'T WORK....  Hello?  I was looking at options from two different lists that people posted as compatible hardware, and I only found the one that said it was explicitly compatible with Intrepid....  See?  That's the problem -- there's nothing CURRENT, outside of the forums, that helps people convert their systems to Ubuntu!

---

### Post by lilychef on 2009-04-22
BTW, pbpersson... Your cat shares a strikingly similar resemblance to mine! Ha!

---

### Post by lilychef on 2009-04-22
.

---

### Post by lilychef on 2009-04-22
.

---

### Post by pbpersson on 2009-04-22
The problem with Ubuntu - and the problem with Windows - is that when you stray off the road the terrain is very rugged.

It is just that in Windows, the road is much wider and it's much easier to never stray from the appointed path - if you know what I mean.

I Googled your card on several sites, saw a whole lot of people asking questions, but no real answers.

---

### Post by lilychef on 2009-04-22
Right -- and what a shame, cuz it sounded GREAT on Windows... I found several complicated "fixes" to try a couple of rogue (or beta) drivers, but I have just enough experience with Ubuntu to NOT try that ****....  I think I'll try this "Cafe" thing to get some direct answers from peeps who are having perfect success with their sound and vid cards.... Didn't really want to spend more money, though, but it's worth it to FIALLY get awway from Windows permanently... UGH!

---

### Post by Yellow Pasque on 2009-04-22
If you want fully supported hardware, buy a system made for Linux/Ubuntu (e.g. System76 or Dell). Otherwise, you have to do your homework. Since supported hardware info changes so fast, maintaining an accurate, comprehensive guide would be very difficult.

As for the X-fi:
[http://www.phoronix.com/scan.php?page=news_item&px=NzE2Ng](http://www.phoronix.com/scan.php?page=news_item&px=NzE2Ng)

The lead developer of OSS said:
> SB X-Fi is one of the last new consumer sound cards in the market. It has an impressive feature list on paper. Unfortunately, the EMU 20k chip is extremely complex. It has dozens of different processing units connected by a freely reconfigurable ring bus. In addition it has a DSP unit that is completely undocumented. Also different X-Fi cards have different peripheral chips connected to the 20k chip. Figuring all that out seems to be something that may take few years of full time work. In addition keeping track of the changes in recent/future card models makes the driver a moving target. The current X-Fi driver of OSS is based on a simple DOS based manufacturing test program provided by Creative. It supports only older card models and limited functionality. Unfortunately this seems to be the best that can be done unless we manage to hire a group of 5-10 sr driver engineers to do the job.

---

### Post by lilychef on 2009-04-22
Thanks, Temujin.... Finally a reply I can understand.... and that article was pretty telling.... Guess I'm gonna have to start over in the peripheral dept...  and I thought Creative was the definitive manufacturer... Whatever!  Ha!   But do tell -- what  sound and vid cards do YOU use?  HA!

---

### Post by Yellow Pasque on 2009-04-22
Sound: My primary use for sound is music playback through decent headphones along with some light DVD playback.I use an M-Audio Revolution 5.1 that I bought in 2005. I'm not even sure if they still manufacture/sell it, and it doesn't have all the fancy Dolby decode stuff that one would expect nowadays. Nevertheless, it is well supported by both ALSA (>= 1.0.18) and OSS4.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16829121122](http://www.newegg.com/Product/Product.aspx?Item=N82E16829121122)

Video: My video needs aren't too demanding - light DVD playback and zsnes are the heaviest tasks I do. I generally use ATI cards because of my philosophical distaste for Nvidia. Right now, I use an X1300 and open-source drivers, and I'm perfectly content with its stability/performance (I gave up on Catalyst/fglrx a long time ago). Users that need advanced video decoding or heavy 3D performance will probably be happier with Nvidia.

---

### Post by jocheem67 on 2009-04-22
Hi there, just for your information, creative is an old-school pain in the butt regarding drivers, on linux_ and_ windows..

And their cards aren't that good btw..at least I think so.

I'm using an older m-audio delta 1010, which is still fully supported..however I understand that the new m-audio cards aren't fully supported anymore.

Why not looking for an usb card, maybe the easy solution?

---

### Post by lilychef on 2009-05-05
I found this thru Creative's website while searching for more options with my creative card, and I'm not sure what to make of it....  This is the first page that offers a driver for the x-fi cards:

[http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

But it specifically says it does NOT support the X-Fi Extreme Audio, which is of course what I have... ha!  Figures.  But below the section on compatibility, they DO list the Extreme Audio and a link to a ALSA project driver for the CA-106 (my extreme audio card), here:

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)

This all looks very confusing to me.... I don't know much about programming Linux, but it seems to say I can install something that will work with my card... Does anybody have any advice on whether I can try this ALSA module thing?  And if so, help me through it?   I'm just trying to avoid having to buy another sound card to get 5.1...  Right now I'm not getting center or surround.... Thanks!

---


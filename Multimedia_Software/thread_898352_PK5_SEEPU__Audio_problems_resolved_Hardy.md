---
title: "PK5 SE/EPU  Audio problems resolved Hardy"
date: 2008-08-23
forum: Multimedia Software
---

### Post by s57nev on 2008-08-23
Audio on Hardy works directly after installation. Problems arise when you try to use CD / mic and other devices. I use CD input for my tvcard. CD input didn't exist at all. There ware also some mic volume problems. This bug was really show-stopper.First some info: 

$ dmesg | grep hda_intel 

hda_codec: Unknown model for ALC883, trying auto-probe from BIOS... 

Problem is that this model of sound card isn't recognized. 

$lspci -v

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


SOLUTION:

sudo gedit /etc/modprobe.d/alsa-base

Add one new line specifying soundcard type for proper modules to load:

options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
#myoptions
**options snd-hda-intel model=6stack-dig**

Hope this helps. It works for me.

---

### Post by spider_0k on 2008-08-23
Truth is I don't really know! I have been reading forums following step by steps for months. This is a core issue and I'm sad that Ubuntu is failing to address it. I stopped short at reinstalling ALSA. I believe ons should not have to do this except under very unusual circumstances. I would like to be a Ubuntu evangelist but for modern computer users sound and video are essential.
The quick and dirty solution is to have a manufacturer who's (cheap)sound cards work "out of the box". I for one would be happy to buy a reasonably priced sound card, that I knew would work. However I do have a spare soundblaster clone, even that is not fully functional. I hope this is placed nearer to the top, I would love to introduce Linux my friends and family.
Today I had another clicky day, after following the above tip there were "noises" from the speakers , when using Mic input. So, after two hrs of clickety click I can now use my SIP phone! To all of you reading this in despair, clickety click will get you there. I'm sorry I can't give a more definite solution. Be more active in the forums even to say my ..... doesn't work (with a few more details) will help those who do know where the bigger problems lie for us end users.
Take heart Clickety click
Philip
P.S
Thanks s57nev

---

### Post by s57nev on 2008-08-25
Well I wouldn't go there. There are plenty of motherboards around that just work. I usually check hardware compatibility lists before I buy a new computer. This way we thank to manufacturers that make effort for Linux compatible devices and buy a new one.This is what I recommend to new users.  

7 years ago when I started with Linux there ware plenty of hardware issues that we had to solve ourselves.I remember manualy writing x86config manually. I don't even want to mention dial up configuration.... Now even Laptops work almost out of the box if you buy a compatible one. 

Probably the biggest problem about hardware out of the box compatibility is **US users not reporting problems and solutions in a open source spirit any more**.We expect things just to work and use our programs created by the big company's and others around the world. I trust in young people eager for knowledge with lot's of time to advance this kind of things.
 

It's just like on search engines: 

1. define problem correctly (this usually means using right tools to get a proper string like (dmesg | grep audio)
2. search for a right answer within forums

Again hacking is for those who don't use hardware compatibility forums and just buy stuff from shelves. Beginners beware.

Don't let terminal scare you to go away.

Enjoy !

---

### Post by spider_0k on 2008-08-26
Thank you for the reply and for the most part I agree. I wasn't referring to myself in my post. I'm a habitual fiddler, I have "broken" my installation many times. Before I understood what was happening or how to find out what had happened, I would just reinstall. Now I know better, thanks to these forums. To my point:

Ubuntu is a distro that has picked up many "new" users and many more disaffected winbloat users. If we aren't more effective in helping them they will return to winbloat. There is no shortage of help, but just as you mention about search engines, its knowing what question to ask. Often I have know what my problem is, I just can't figure out the right form of question and with so *much* help out there, where to ask the question.

Regarding reporting of problems, I often don't know why something doesn't work, so I find reporting the problem very difficult. Like our current problem. My sound card works ok, I mean just ok (missing the 5.1 dolby thingi). I can do everything soundwise, but there is no input from the mic when using sip phones skype and real sip phones. where is the information regarding the problem that I  can report?

Finally; Phew! Compatible hardware is extra difficult for me as I am in China and much of the hardware either isn't here or is a slightly different model, just for China.

I keep thinking of more to say, but I'm aware of drifting off topic!

Regards
Philip

---


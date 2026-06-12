---
title: "UA-25 soundcard problem"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by gijzelaar on 2006-10-05
gijs@park:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: UA25 [UA-25], device 0: USB Audio [USB Audio]
Subdevices: 1/1
Subdevice #0: subdevice #0


gijs@park:~$ alsamixer
No mixer elems found

playing something with rythmbox works, but the gnome volume panel doesn't see a sound card. Tried edgy and dapper, some problem....

anybody a suggestion?

---

### Post by mpvano on 2006-10-05
If it's really card 1, the command for alsamixer is 
alsamixer -c 1

You also need to be aware that many USB sound cards have NO mixer elements. Especially those from Edirol that have input and output controls on their panels. In most cases, however, the current alsa driver will "fake" controls for such devices, but only if it recognizes them.

Another question you need to ask yourself is "What is card 0 in my system?" You can get very confused if there's already a default card in use.

One more hint: The gnome mixer on the Ubuntu panel doesn't display all the control options for most mixers. It has a "change device" submenu in the "File" menu. Once you have selected a device, you may need to use the "preferences" dialog to enable display of some of the controls.

I find it interesting that you have a card 0 existing! I suspect that this is a modem or some other device with an alsa driver, but not an actual sound card. This too, can be confusing. Many "soft" modems work this way. Don't forget that the alsa mixer may or not be present for these devices, and that it doesn't act like a sound card. The options are often for things like allowing the modem to pick up the phone.

hope these tips help sort you out....

Mario

---

### Post by gijzelaar on 2006-10-06
thx for the reply!

but.....

gijs@park:~$ alsamixer -c 1
No mixer elems found

and I can't come into the preferences dialog of gnome-volume-manager:
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.



i forgot to tell, that it worked on my laptop, with the same card. But I was using breezer back then....

---

### Post by ua25 on 2007-10-27
I have the exact same problem :-(

---

### Post by ua25 on 2007-10-29
A .asoundrc file with this in my home directory solved it (running gutsy 7.10) :-)
Change card x to the appropriate number for your system.

pcm.!default {
  type		plug
  slave.pcm	"softvol"
}

pcm.softvol {
  type softvol
  slave {
	pcm	"dmix"
  }
  control {
	name	"PCM"
	card	1
  }
}

---

### Post by Sinkadus on 2007-10-30
I have the same card. Thats right, hardware controls. But can be faked by alsa.

how about recording then, i have not been able to solve that... Audacity for example recognized the card perfectly by name and all, but crasches bigtime every time. And in Ardour i get nothing.


Edit: after wrighting text above, recording worked in normal mode (44.1 - 16 bit) after installing gutsy! JOY!!! 

That sample rate and bit resolution works for me because i plan to use the UA-25 for recording on the field with mics. (ADK A51, and it actually powers two of them!) to be cut and used in AKAI S-3000XL samplers.

So this is a happy day. Cheers!

---


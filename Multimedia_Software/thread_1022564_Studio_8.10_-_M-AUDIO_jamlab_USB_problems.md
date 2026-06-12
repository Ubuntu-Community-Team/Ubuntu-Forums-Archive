---
title: "Studio 8.10 - M-AUDIO jamlab USB problems"
date: 2008-12-26
forum: Multimedia Software
---

### Post by TTC1 on 2008-12-26
Hi there,

I just installed Ubuntu-Studio a few days ago and I am using this M_audio Jamlab USB interface as my main sound module.

My problem is that I only have one channel operating (having sound)
I remember ansewring a question, at the install time, about sound devices, it was asking me if I wanted 1 or 2 devices, or something like that. I wasn't sure and  answer with 1. I have the feeling that it is related somehow.

Now, after quite a bit of searching thru the internet, I came up with someone having the same problem but within a Mandriva distro.
He kinda tracked down the problem to the amixer config.

My result of "amixer -c0 contents":

numid=1,iface=MIXER,name='PCM Playback Switch'
  ; type=BOOLEAN,access=rw------,values=1
  : values=on
numid=2,iface=MIXER,name='PCM Playback Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=319,step=0
  : values=77,158
  | dBscale-min=-127.50dB,step=0.39dB,mute=0
numid=3,iface=MIXER,name='Mic Capture Switch'
  ; type=BOOLEAN,access=rw------,values=1
amixer: Control hw:0 element read error: Invalid argument

numid=4,iface=MIXER,name='Mic Capture Volume'
  ; type=INTEGER,access=rw---R--,values=2,min=0,max=292,step=0
  : values=255,264
  | dBscale-min=-127.99dB,step=0.50dB,mute=0

Now, if you look at numid=2 you see values=77,158
If I change the value 77 to 158 the second channel comes into action.
But, obviously it is only temporary and upon next reboot it reverts back to its original setting at 77.

In Mandriva, he used the file /etc/rc.local to put in the change.
I just can't find that file in Ubuntu. I'm assuming Ubuntu is using another file to register these settings.

I haven't had any luck so far finding where the hell these settings are saved in Ubuntu.

Another thing that puzzles me.
When I boot into Windows (I'm dual booting on this machine), my USB interface makes some initialization noises that come out from both channel but when I boot into Linux, I hear noise from only one channel.
I have a feeling that the drivers may have been compiled into the kernel with the wrong info in them.

Anyways, anyone can help me out with this here?
I am not very knowledgeable with Linux. I know my way around within Windows but Linux is another beast to master.

Thanks for any help.

---

### Post by TTC1 on 2008-12-29
Geez! No one can even steer me in a direction to find a solution for my problem?

There got to be someone out there that experienced a similar situation.

At least can someone tell me where to look to solve it?
I'm no Linux guru, I'm just starting out.
Any help would be greatly appreciated.

Thanks!

---


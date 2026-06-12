---
title: "distributed whole house audio - alsa problems"
date: 2012-04-03
forum: Multimedia Software
---

### Post by sjhupp on 2012-04-03
Hi, hoping someone who understands alsa could help me please. I want to set up my server to enable some whole house audio, meaning I basically require my sound card to be able to output either multiple stereo output channels, or even individual mono channels for different audio player programs, instead of the usual multichannel output for one app to use (say configure 4 stereo pair outputs on 8 channel card).

I've done some research, and it's covered here:
[http://forums.whirlpool.net.au/forum-replies.cfm?t=1889949](http://forums.whirlpool.net.au/forum-replies.cfm?t=1889949)

Now I've got ubuntu desktop installed, and the logitech squeezecentre server, after deciding that should cover my requirements (controlled by a phone, independent or synchronised output, simple)
I plan to run multiple squeezeslave instances via cli on the server, with each outputting audio to specific audio output ports/jacks/channels. These would then feed into amps with speakers running to each room/zone I wanted. All good in theory!

But this is where I'm in trouble :confused:
I think I need alsa to do this, and have found some example configs from someone doing the same thing:
[http://forums.slimdevices.com/showthread.php?t=86253](http://forums.slimdevices.com/showthread.php?t=86253)
but I have no /etc/asound.conf or asound.rc files. Even creating them fails to change anything (after a reboot) shown with aplay -l or squeezeslave -L (listing available audio devices).
Could someone please help me how to create these virtual devices in alsa with the slave.pcm dmixer setup. The ttable moving stereo to the other jacks makes sense at least.
Thanks!

---

### Post by sjhupp on 2012-04-08
Anyone? please?
Just need to know how to get alsa to use the config file?
Or can pulseaudio do something similar?
:icon_frown:

---

### Post by ridetheteapot on 2012-04-08
honestly can't help you, i had never thought about even trying that before (8 channel analog -> 4 identical stereo). /etc/asound.conf is where alsa will look for your config (or ~/.asoundrc), but it does not exist in the default ubuntu install, you'll have to create it.
I also do not know if pulse will do it, but i would think it would, due to its nature (you can reroute signals all around).

I do think however it would just be way easier to use the "pete y testing"s recommendation and just get a speaker selector. You probably ruled this out for one reason or another already though...

---

### Post by sjhupp on 2012-04-09
> **ridetheteapot said:**
> honestly can't help you, i had never thought about even trying that before (8 channel analog -> 4 identical stereo). /etc/asound.conf is where alsa will look for your config (or ~/.asoundrc), but it does not exist in the default ubuntu install, you'll have to create it.

Trying to do it with 4 different stereo pairs actually - using the ttable setting it looks easy to basically swap channels, or direct them to pairs.
As per the links above, others have it working successfully.  It's just that I created the /etc/asound.conf file but it doesn't seem to make any difference wrt output options?!
I must be missing something :\
Don't think a speaker selector will help, as the matrix function I need can be essentially done via  alsa ttable mappings, and wouldn't cost me a ridiculous amount of money!
All the audio software (squeezeserver/clients/remote control) works great, I was just hoping to not need to buy a new board with lots of pci slots for multiple sound cards.
Instead of 1 card as output per zone/room, I wanted to use alsa ttable mappings to get multiple stereo outputs from a single 6 or 8 channel sound card.
Thanks anyway.

---

### Post by ridetheteapot on 2012-04-10
I wrote a reply, then i reread your last post a realized the word different.
> Trying to do it with 4 different stereo pairs actually

Was going to say i would try also (have a 5.1 card and 2 amps, so actually half what you'r trying)... But I don't think I'm up for the mission now that i get it.

I do have 3 stereos in my house though, but i've just been using the lan for my audio transport. obviously not what you need either, latency is pretty unreliable on the network.

_____Edit____
either way though, wouldn't hurt to drop your asound conf here...

---

### Post by sjhupp on 2012-04-10
No worries.
I have used Mac, PC, soundbridge and android clients over the lan (fixed & wireless mix), all all work  great individually, but they don't all sync properly.  I can play somgs on any combination of them, which is great, but ultimately it needs consistent sync for full house playback. This is where a single pc with multiple clients would be great (and also make use of a low power itx via setup to run it all).
Found some more alsa dmix plugin info and will try to follow the wiki and adapt it somehow, possibly over the weekend:
[http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html](http://www.alsa-project.org/alsa-doc/alsa-lib/pcm_plugins.html)
It has to work eventually!!
:P

---

### Post by Yellow Pasque on 2012-04-10
I recently saw someone trying to do something similar on ALSA mailing list: [http://article.gmane.org/gmane.linux.alsa.user/36269](http://article.gmane.org/gmane.linux.alsa.user/36269)

---

### Post by gtippitt on 2012-04-10
You need to look at the documentation and examples for the hidden file .asoundrc in your home directory.  The link below has an example of how to do the opposite by combining multiple stereo devices into a virtual multi-channel device.  There are probably more examples that will do what you need.  I didn't have time to look further right now, so I wanted to post this as a place you could look for more help.

The .asoundrc file gives you tons of flexibility to configure ALSA.  I was trying to get 5.1 to work with an old Creative USB Extigy device a year or so ago and played around with the asoundrc until I found out the PA and ALSA drivers for Extigy were stereo only.

[http://www.alsa-project.org/main/index.php/Asoundrc#Virtual_multi_channel_devices](http://www.alsa-project.org/main/index.php/Asoundrc#Virtual_multi_channel_devices)

Good Luck,
Greg

---

### Post by sjhupp on 2012-04-10
Thanks Temüjin and gtippitt!
Will try both approaches and report back.
Cheers.

---

### Post by sjhupp on 2012-04-12
Woohoo!!! :guitar:
Major progress - base functionality working :D

Ok, so on my desktop, I have the following (excuse the post length!)

simon@Lister:~/squeezeslave$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And my /etc/alsa.conf (creating 4 stereo pair outputs with jack colours)

simon@Lister:~/squeezeslave$ sudo cat /etc/asound.conf 

pcm_slave.homezones {
  pcm "hw:0"
  rate 44100
  channels 8
  periods 128
  period_time 0
  period_size 1024
  buffer_size 4096
}

pcm.green {
  type dmix
  slave homezones
  ipc_key 1001
  bindings [ 0 1 ]
}

pcm.black {
  type dmix
  slave homezones
  ipc_key 1001
  bindings [ 2 3 ]
}

pcm.yellow {
  type dmix
  slave homezones
  ipc_key 1001
  bindings [ 4 5 ]
}

pcm.blue {
  type dmix
  slave homezones
  ipc_key 1001
  bindings [ 6 7 ]
}

Then from the squeezeslave client play (cli) I can see:

simon@Lister:~/squeezeslave$ ./squeezeslave -L
Output devices:
  0: (ALSA) HDA Intel: ALC883 Analog (hw:0,0) (11/46)
  1: (ALSA) HDA Intel: ALC883 Digital (hw:0,1) (11/46)
  3: (ALSA) Logitech USB Headset: USB Audio (hw:1,0) (11/46)
  4: (ALSA) front (11/46)
  5: (ALSA) surround40 (11/46)
  6: (ALSA) surround41 (11/46)
  7: (ALSA) surround50 (11/46)
  8: (ALSA) surround51 (11/46)
  9: (ALSA) surround71 (11/46)
 10: (ALSA) iec958 (11/46)
 11: (ALSA) spdif (11/46)
[B] 12: (ALSA) green (46/46)
 13: (ALSA) black (46/46)
 14: (ALSA) yellow (46/46)
 15: (ALSA) blue (46/46)[/B]
*16: (ALSA) default (42/46)
 17: (ALSA) dmix (42/42)
 18: (OSS) /dev/dsp (11/46)
 19: (OSS) /dev/dsp1 (11/46)

Then I can run multiple instances of the squeezeslave client, for now just connecting to localhost server:

simon@Lister:~/squeezeslave$ ./squeezeslave -m00:00:00:00:00:01 -nblack
simon@Lister:~/squeezeslave$ ./squeezeslave -m00:00:00:00:00:02 -nyellow
simon@Lister:~/squeezeslave$ ./squeezeslave -m00:00:00:00:00:03 -nblue
simon@Lister:~/squeezeslave$ ./squeezeslave -m00:00:00:00:00:04 -ngreen

And the Logitech Media Server gui shows up the four separate clients!
They can each play different songs*, and they can all be synced to play the same song!!

* my only issue is the blue output doesn't play anything yet - something is not 100% in my config, as pretty sure it's an 8 channel card, but the other 3 work fine, so maybe only 6. Meh, good enough for proof of concept I say!

Now to work out if I need to have mono sounds for each zone instead. If so I assume I need to combine the L & R from each pair, or maybe just state channels 1? Further play time...
:p

---

### Post by Yellow Pasque on 2012-04-12
You may need to retask the blue jack using: [http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

Unfortunately, the utility is not available for Lucid, which is what you appear to be using.

---

### Post by sjhupp on 2012-04-12
Thanks Temüjin, looks very useful! Not sure how many actually use the microphone port, so be nice to use it as an output.
The blue port, however, is not a microphone port for me - I have 5 output ports (1 is the mic) and optical (Foxconn P9657AA-8EKRS2H). Not too concerned yet though, but that little util will be great on the end box to get another output port.

I am using Lucid on my current box, but I'm only testing the solution - will install on a little itx box when ready (or maybe my microserver if I can find a nice sound card to fit).
Then I'll prob put 12.04 on when released proper.

I also have to sort out the hardware to amplify the outputs before passing off to some ceiling speakers, but not completely planned that out yet.

---

### Post by iponeverything on 2012-04-12
> **sjhupp said:**
> Thanks Temüjin, looks very useful! Not sure how many actually use the microphone port, so be nice to use it as an output.
The blue port, however, is not a microphone port for me - I have 5 output ports (1 is the mic) and optical (Foxconn P9657AA-8EKRS2H). Not too concerned yet though, but that little util will be great on the end box to get another output port.

I am using Lucid on my current box, but I'm only testing the solution - will install on a little itx box when ready (or maybe my microserver if I can find a nice sound card to fit).
Then I'll prob put 12.04 on when released proper.

I also have to sort out the hardware to amplify the outputs before passing off to some ceiling speakers, but not completely planned that out yet.

you should document the project on-line -- sonos might pay you to go away.

---

### Post by sjhupp on 2012-04-12
> **iponeverything said:**
> you should document the project on-line -- sonos might pay you to go away.

Lol! :D
Prob will write it all up once I have it working to my (or the wife's) satisfaction.
Was thanks to a couple others writing up their solutions that got me thinking about it, and having a crack.
I'm just too tight to pay thou$ands for something that in theory looks fairly simple to implement.

Will see if my little 12v $10 stereo amp does the job I have planned for it... could make for a nifty pc install if it pans out ok.

tbc...

---

### Post by sjhupp on 2012-04-28
Just a quick update.
Xonar DX sound card (8ch) installed in microserver, and config updated to supply 4 pairs of outputs down the 4 output ports, top to bottom:

port1 [ 0 1 ]
port2 [ 6 7 ]
port3 [ 4 5 ]
port4 [ 2 3 ]

So these can be used with my 4 squeezeslaves no problems.
However, have been trying to come up with a way to spit out 8x mono channels instead, noting they're be given a stereo source to play.
So I assume I need to route from stereo to mono, and bind to a single channel, maybe using ttable to take half the L & R and put them both on one channel.
Sounds good in theory ... but nfi how to put the config right :(

Anyway know how to make a slave output mono to a single channel, from a stereo (music) input??

Will put 12.04 on shortly, and try that other hack to turn an input into another output (Xonar DX has 1 input 4 outputs).

---


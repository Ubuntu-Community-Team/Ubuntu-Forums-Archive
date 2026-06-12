---
title: "Firewire Audio Interface : which one shall I buy ?"
date: 2008-03-30
forum: Multimedia Production
---

### Post by theophane on 2008-03-30
Hi there !

I've got an M-Audio Fasttrack usb card that works well, but I intend to sell it because it has a pretty huge latency and only one XLR entry.

I'm looking for a -cheap- Firewire Audio Interface with 2 XLR entries; assuming I only run Linux.

I found these two that seem to be Linux compatible : 

[LIST=1]
[*]PreSonus FireBox
[*]PreSonus Inspire 1394
[/LIST]

Any piece of advice ?

Cheers :guitar:

---

### Post by robeast on 2008-03-30
I hadn't heard about the Inspire being compatible, but the Firebox works with the Freebob drivers. You'll probably want to check out the M-Audio Firewire Solo, the Firebox and the Echo Gina and see which one suits your needs. They are all similar in function and price. I have a list of linux compatible audio hardware at [http://linuxstudiopro.com](http://linuxstudiopro.com) that you might find helpful.

---

### Post by theophane on 2008-03-30
> **robeast said:**
> I hadn't heard about the Inspire being compatible, but the Firebox works with the Freebob drivers. You'll probably want to check out the M-Audio Firewire Solo, the Firebox and the Echo Gina and see which one suits your needs. They are all similar in function and price. I have a list of linux compatible audio hardware at [http://linuxstudiopro.com](http://linuxstudiopro.com) that you might find helpful.

First of all, thanks for answering.

BTW, could you tell me what kind of latency will I get on such devices ?
Will I be able to add back-up vocal to my tracks ?
I went to a music store yesterday and the guy in-there told me that with a firewire interface, there would be almost no latency. (is that true?)

The M-audio solo is cool, but it only has 1 XLR plug. They have the Firewire 410 that seem to be **awesome**, but it is a Linux Hostile certified device :)

---

### Post by Stochastic on 2008-03-30
I wouldn't rely on Robeast's listing to find which soundcards are compatible, it's incomplete and fairly new (no offence Robeast, I like the idea of encouraging linux audio compliant hardware purchases, but your site is not a complete list).

Go to the driver source:  [http://www.ffado.org](http://www.ffado.org) is what all firewire audio devices will be using soon as a driver (it's the new website and name for the freebob driver).  They have an excellent list of devices there.

As for latency questions, yeah there'll be almost no latency but you'll always have some (your computer specs play a role in this too).  On my Presonus Firepod I've been getting latency as low as 6ms.  Most pro-systems shoot for a latency below 10ms.

Back-up vocals are entirely within the possibilities of almost any linux audio software system.

---

### Post by theophane on 2008-03-30
> **Stochastic said:**
> 

Back-up vocals are entirely within the possibilities of almost any linux audio software system.

No, I mean recording back-up vocals to a couple of main instruments and vocals tracks without having any latency troubles.

And thank you for the link, I'm reading through at the moment. I've already found a interesting model : **QuataFire 610**. It appears to be "Linux compatible" on the manufacturer's website.

---

### Post by Stochastic on 2008-03-30
To get things properly synced with any recording, low latency helps, but you can always go in after you've recorded and move the track forward to sync if there's any major offset.  With almost any firewire device though you'll get a low enough latency not to notice an offset.

---

### Post by robeast on 2008-04-01
I know, stochastic, I've been spending so much time on the friggin interface that I haven't had a chance to add the new devices I've scrounged up! And don't even get me started on Internet Explorer. Check out the new update, waaaaay more info on the devices and a lot of interface and back-end enhancements. I don't plan on listing FFADO devices until the drivers are released.

---

### Post by theophane on 2008-04-01
One last question, if I buy a device with two XLR plugs such as the QuataFire 610, will I be able to record two different tracks at the same time ? (one track per XLR plug, for easy post recording editing)

---

### Post by Stochastic on 2008-04-01
Theopane: Yes, you'll get one mono track per XLR input.

Robeast:  Might I suggest putting some links on the site to compatibility listings or instructions on how to install?  That way if you're not able to do a update regularly then others can still find all the information.  Also the FirePod has officially been discontinued, but now Presonus is selling the FP10 (which is the same thing but under a different name).

---

### Post by theophane on 2008-04-03
Cool, thank you for all these very useful explanations, my SM57 is on its way.
I need to find a cheap QuataFire 610 now...

---

### Post by theophane on 2008-04-03
The Focusrite Saffire LE is reported as supported... will it be supported out-of-the-box on Ubuntu Studio 8.04 ?
I haven't found a thread or something where someone says it actually works.

Any info on that ?

I want to be 100% sure the device will work under Linux before I buy it.

---

### Post by Stochastic on 2008-04-04
When I was using the Saffire LE it was nearly perfect out of the box.
The only bug I experienced was that the internal hardware mixer hadn't been coded into the drivers yet (I submitted some changes to FFADO so this may be fixed in that code, but you'll need to do some compiling to get that).  What this meant was that the eight outputs worked as four pairs of the same L/R output.  Everything else worked perfect - though the onboard DSP that you're paying for in the Saffire LE's price tag isn't supported either.  Those two issues were enough for me to return the card in exchange for a Presonus FirePod.

---

### Post by theophane on 2008-04-04
Ok, then which firewire card should I go for ?
I need 2 XLR inputs to plug my sm57&58. All I want is to record acoustic guitars and vocals. I also want it to be working out-of-the-box.

Once again, thank you :guitar:

---

### Post by Stochastic on 2008-04-04
The Saffire will do that for you but it's a bit pricey if that's all you're looking for.

---

### Post by theophane on 2008-04-05
The Presonus Inspire 1394 might also do the job, and it is way cheaper, but will it work ?

---

### Post by Stochastic on 2008-04-05
the inspire is listed on both the [freebob](http://freebob.sourceforge.net/) and [ffado](http://www.ffado.org) (the new reincarnation of freebob) websites.  The listing on ffado is the same as my working firepod so I would be fairly confident in saying it'll work.  But if you have troubles, return the thing and get a different card.

---

### Post by theophane on 2008-04-05
I'll buy it on eBay.com and have it shipped to France. The € v. $ difference makes the thing way cheaper. For example, the Saffire LE is sold $507,68 here in France while it costs $250 on ebay.com. 

So I'll definitely buy it on eBay, and returning it is not an option.

That's why I want to be 100% sure it will work :)

---

### Post by Stochastic on 2008-04-05
Well then I'd log onto the FFADO dev lists/irc and start up a discussion with the developer to see what exactly they mean by "reported to work".  I know they've been given some presonus devices to develop their drivers.

The other option would be to buy one from a store in france (or rent), try it out and then return it with some lame excuse like "I really couldn't stand the harshness of those preamps".  Then make a more educated purchase on ebay.

---

### Post by theophane on 2008-04-07
After much reflexion, I just purchased an Edirol FA-66 on ebay. 
I read a lot of kick-*** reviews and various feedbacks reporting it was working out-of-the-box under Linux.

Now it's time to wait... and hope my [_Fast Track USB_]("http://cgi.ebay.fr/M-AUDIO-Fast-Track-USB-maudio-fasttrack_W0QQitemZ180229318236QQihZ008QQcategoryZ21775QQssPageNameZWDVWQQrdZ1QQcmdZViewItem") will go...

---

### Post by theophane on 2008-04-17
Just received my FA-66, and it is obviously not working out of the box.

I cannot get jack to work properly. Here are the settings I use :

[[img]http://pix.nofrag.com/1/7/2/da6b06e10d78af103d23932f0b96e.png[/img]](http://pix.nofrag.com/1/7/2/da6b06e10d78af103d23932f0b96e.html)

And here is jack's output when it crashes :

[[img]http://pix.nofrag.com/6/c/c/95941b10a893939269aeb851f4368.png[/img]](http://pix.nofrag.com/6/c/c/95941b10a893939269aeb851f4368.html)

Some help would be much appreciated  :guitar:

---

### Post by Stochastic on 2008-04-17
Firewire audio is not usable straight out of the box, some setup is required.  Have you given permission to the audio user to access raw firewire?  Can you turn verbose message output on and repost your errors?

---

### Post by theophane on 2008-04-18
> **Stochastic said:**
> Have you given permission to the audio user to access raw firewire?

yes


> **Stochastic said:**
> Can you turn verbose message output on and repost your errors?


```
theo@studio:~$ jackd -R -P60 -p128 -t2000 -u -dfreebob -dhw:0 -r48000 -p256 -n3 -D
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
libiec61883 warning: iec61883_cmp_create_p2p_output: Failed to set the oPCR[0] plug for node 1.
FreeBoB ERR: Could not start streaming threads
LibFreeBoB ERR: Could not do CMP for connection 0
DRIVER NT: could not start driver
cannot start driver
jackd watchdog: timeout - killing jackd
Aborted (core dumped)
```

Once again, thank you for your help :)

---

### Post by Stochastic on 2008-04-18
Hmm, looks like some library troubles, I've never seen that error before so I'm only intuitively troubleshooting at this point.  

My first instinct is to do the following:
Try going into Synaptec package manager (in System -> Administration), do a search for libiec61883, right click the box next to it and choose mark for re-installation.

But after I did a bit of searching on google I found that error tends to be associated with the library not being able to make a connection through the firewire.  Quite often this can be resolved by resetting the bus (try unplugging and re-plugging your firewire cord, or rebooting) or in a worse case was due to a poor firewire cable.

One issue with jack is that each time it crashes, the firewire device needs to be reset again.  For my Firepod, simply unplugging and re-plugging the firewire cable takes care of this.

---

### Post by theophane on 2008-04-19
So, after a couple of problems with Ubuntu Studio, I switched back to Ubuntu (Hardy Beta). I installed jack and ardour (i686) and audacity.

Jack seems to work but I can't record anything...
Ardour is just not recording and audacity says :"Error while opening sound device. Please check the input device settings and the project sample rate."

 My FA-66 is set to record at 48000hz, and so is audacity

Here is Jack's output :

```
13:28:13.742 Patchbay deactivated.
13:28:13.844 Statistics reset.
13:28:13.919 ALSA connection graph change.
13:28:14.109 ALSA connection change.
13:28:32.965 Startup script...
13:28:32.966 artsshell -q terminate
13:28:33.695 Startup script terminated with exit status=256.
13:28:33.695 JACK is starting...
13:28:33.695 /usr/bin/jackd -v -dfreebob -r48000 -p256 -n2 -D
13:28:33.697 JACK was started with PID=6405.
getting driver descriptor from /usr/lib/jack/jack_freebob.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_dummy.so
jackd 0.109.2
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
new client: freebob_pcm, id = 1 type 1 @ 0x8070018 fd = -1
Freebob using Firewire port 0, node -1
new buffer size 256
LibFreeBoB MSG: FreeBoB Streaming Device Init
LibFreeBoB MSG:  Using FreeBoB lib version libfreebob 1.0.7
LibFreeBoB MSG:  Device information:
LibFreeBoB MSG:  Device options:
LibFreeBoB MSG:   Port                     : 0
LibFreeBoB MSG:   Device Node Id           : -1
LibFreeBoB MSG:   Samplerate               : 48000
LibFreeBoB MSG:   Period Size              : 256
LibFreeBoB MSG:   Nb Buffers               : 2
LibFreeBoB MSG:   Directions               : 0
showDevice: not implemented
13:28:34.439 ALSA connection graph change.
FreeBoB MSG: Register MIDI IN port dev1c_MidiPort_1
FreeBoB MSG: Register MIDI OUT port dev1p_MidiPort_1
FreeBoB MSG: Streaming thread running without Realtime scheduling
FreeBoB MSG: Registering audio capture port C0_dev1c_MicIn1 left
registered port system:capture_1, offset = 1024
FreeBoB MSG: Registering audio capture port C1_dev1c_MicIn1 right
registered port system:capture_2, offset = 2048
FreeBoB MSG: Registering audio capture port C2_dev1c_LineIn 3+4 left
registered port system:capture_3, offset = 3072
FreeBoB MSG: Registering audio capture port C3_dev1c_LineIn 3+4 right
registered port system:capture_4, offset = 4096
FreeBoB MSG: Registering audio capture port C4_dev1c_SpdifIn left
registered port system:capture_5, offset = 5120
FreeBoB MSG: Registering audio capture port C5_dev1c_SpdifIn right
registered port system:capture_6, offset = 6144
FreeBoB MSG: Don't register capture port for dev1c_MidiPort_1
FreeBoB MSG: Registering playback audio port P0_dev1p_LineOut 1+2 left
registered port system:playback_1, offset = 0
FreeBoB MSG: Registering playback audio port P1_dev1p_LineOut 1+2 right
registered port system:playback_2, offset = 0
FreeBoB MSG: Registering playback audio port P2_dev1p_LineOut 3+4 left
registered port system:playback_3, offset = 0
FreeBoB MSG: Registering playback audio port P3_dev1p_LineOut 3+4 right
registered port system:playback_4, offset = 0
FreeBoB MSG: Registering playback audio port P4_dev1p_SpdifOut left
registered port system:playback_5, offset = 0
FreeBoB MSG: Registering playback audio port P5_dev1p_SpdifOut right
registered port system:playback_6, offset = 0
FreeBoB MSG: Don't register playback port dev1p_MidiPort_1
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
FreeBoB MSG: MIDI threads running without Realtime scheduling
FreeBoB MSG: MIDI queue thread started
libiec61883 warning: Established connection on channel 0.
You may need to manually set the channel on the receiving node.
libiec61883 warning: Established connection on channel 1.
You may need to manually set the channel on the transmitting node.
6405 waiting for signals
13:28:34.500 ALSA connection change.
13:28:35.917 Server configuration saved to "/home/theo/.jackdrc".
13:28:35.919 Statistics reset.
13:28:35.922 Client activated.
13:28:35.926 JACK connection change.
13:28:35.937 JACK connection graph change.
new client: qjackctl, id = 2 type 2 @ 0xb7f1a000 fd = 17
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client qjackctl: wait_fd=16, execution_order=1 (last client).
-- jack_rechain_graph()
new client: PortAudio, id = 3 type 2 @ 0xb6d27000 fd = 20
13:28:44.293 JACK connection graph change.
++ jack_rechain_graph():
client freebob_pcm: internal client, execution_order=0.
client qjackctl: start_fd=7, execution_order=0.
client PortAudio: in subgraph after qjackctl, execution_order=1.
client qjackctl: wait_fd=19, execution_order=2 (last client).
-- jack_rechain_graph()
13:28:46.977 JACK connection graph change.
registered port PortAudio:in_0, offset = 0
registered port PortAudio:in_1, offset = 0
13:28:47.013 JACK connection change.
13:28:47.980 JACK connection graph change.
13:28:48.024 JACK connection change.
```

---

### Post by theophane on 2008-04-20
So, there is a progression here.

I've installed all Ubuntu Studio -audio- packages, and I've been able to record.

The problem now is that Jack crashes all the time. Ardour says jack stops because it runs too slow, and here is the output :

```
JACK: unable to mlock() port buffers: Cannot allocate memory
```
 
I might be able to finally record something sometime soon, yay :)

---

### Post by theophane on 2008-04-25
So, it finally works under Ubuntu Studio 8.04 64bit. Now I need to understand how Ardour works. I also need to understand how Jack works, I found out it had connections between recording inputs and ardour and I must admit it's a bit complicated for a newbie.

That's all for now, rock'on :guitar:

---

### Post by theophane on 2008-05-03
Ok, so after a week of usage or so, this FA-66 is obviously not working on Linux. 
Jack crashes **all the time** and this Edirol card is just unusable. 
I've tried each and every single possible setting and whatever I do, this card is just not working.

I'm "running" this FA-66 on an Acer Aspire 7720G, Intel Core 2 Duo 2.0Ghz, 2Gb ram, and the weird chipset of my laptop might be responsible for this whole mess.

That's all for now... :mad:

---


---
title: "Jack Audio Server"
date: 2007-05-15
forum: Multimedia Production
---

### Post by josesanders on 2007-05-15
I just upgraded from Feisty to Ubuntu Studio by installing all of the packages found in Synaptic under a search for ubuntustudio.  It installed a ton of software, but nothing seems to start up.  Apparantly, many of the programs rely on a Jack audio server, and it is not running.  Is this a package that was supposed to come with ubuntu studio that I somehow missed?

All that I really want to do is set up a multiple track recording program.  I want to be able to record one track, then listen to it while I record additional tracks.  I posted a thread about my failed attempts to do this with Audacity:
[http://ubuntuforums.org/showthread.php?t=443961](http://ubuntuforums.org/showthread.php?t=443961)

---

### Post by btartsa on 2007-05-15
Qjackcontrol is what you seek. Or you can start jackd from a terminal...man jackd.

---

### Post by josesanders on 2007-05-15
Thanks, that did it.  Now I can start the programs.  Does anyone know how to use these?  They are incredibly complicated and not at all intuitive.  I was hoping there would be something easy to use like audacity, but that actually works for multitrack recording.

---

### Post by jondecker76 on 2007-05-15
I'm still learning too, but I can tell you what has been helpful for me to understand the jackcontrol utility.

Open up jack control. Now press the "connect" button. This brings up a connection window that shows your soundcard inputs/outputs as well as inputs and outputs of audio applications. At this point the connections list is empty... so lets start the jack server by pressing the start button

You will now see that the connections window shows your soundcard on both the output ports and input ports (on mine it is labeled as "alsa_pcm")

Ok, now open Hydrogen, then file->Open Demo
Open any demo you want

Also notice that on your connection list Hydrogen appeared on your output ports, and most likely it is already connected to your alsa pcm input ports.

If you press play on hydrogens transport (or the jack control transport) the drumloop starts playing.

Then to make it even more fun, now open up Jack Rack. Again you will notice that it shows up in the connections list. So lets add an effect in jack rack. Click on add, then Time->Delays->TAP stereo echo, then when the parameters for the plugin come up, click on enable

Of course nothing happened yet because we have to route the output from hydrogen to the input of Jack Rack, then the output of JackRack to the input of the soundcard in the connections list.
To do this, click on Hydrogen in the Output Ports, and the alsa_pcm on the input ports so that they are both highlighted. Then click the disconnect button. Now highlight the Hydrogen Output Port and the Jack Rack input port, and hit the connect button, then do the same from the Jack Rack output port to the alsa_pcm input port.

You should have sound again, this time being processed by the plugin. Play with the parameters to see the difference in sound!


Sorry if this is oversimplified or if you already understand routing in Jack, but small practices like this  have helped me understand how jack operates.

Now I just have to figure out how to use some of the other software and start recording!

---

### Post by btartsa on 2007-05-16
josesanders, try setting up multiple desktops and organizing all your apps that way...it helps me see whats going on much more clearly. Typically I run ardour on desktop 1, the ardour mixer on 2, patchage on 3, and qjackctl on 4. Also, make your connections easier  by making them with ardour, then flipping over to pachage to see the results.

---

### Post by alikbalik on 2007-05-16
i'm using ubuntu studio and m-audio ozone with jack server. i manage to start processing with the card but i have few questions? which one do you think (alsa, oss?) should i use??

i can use oss easily but i think in alsa there can be more to come =)

thanx.

---

### Post by Pocadotty on 2007-05-16
Alikbalik you should be using Alsa, which is a more advanced driver then OSS.  Provided that your system is using alsa now that is.  Double click the speaker in the top panel to find out what your using.

josesanders,
JACK is rather intimidating at first because it is fairly complex.  After a little while you should start to like it because it gives you a HIGH level of control.  JACK is vital for most of the programs because they are designed to work together, through JACK. This is vital.  To get a MIDI sequencer working together with a Synthesizer, you need to use JACK.  JACK is the hub of the Linux sound studio.

To manage connections I like using Patchage because I like doing things graphically whenever I can.  The human brain is more suited to managing things graphically after all.

Programs that use JACK will create a connection object which contains all its connections.  This is what you see in Patchage or the connect window of JACK.  In Patchage, Audio connects are blue, and midi connections are green).  

Fallow jondecker79's tutorial and you'll start to get how JACK works.

---

### Post by Jeff BR on 2007-05-22
Hello all! I´m a beginner in UNIX and I would like to have some help on how to install / configure my M-AUDIO OZONE. I´m using UBUNTU 7.04 and I´m trying to make my M-AUDIO OZONE work with the system. The problem is that I can not see the USB AUDIo or something similar in PREFERENCES->SOUND. It seems like the system is not recoginized the OZONE (that corresponds to an external sound card as well as MIDI controller). I saw some posts in the internet with some tips like:
- install/use the OSS driver that is the one that M-AUDIO recommends;
- install the firmware loader  ( [http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/) );
- use JACK;
- use ALSA;

None of the itens above worked. 
I need to configure the OZONE as my sound card as well as midi controller for some programs like ARDOUR and HYDROGEN.

Thanks in advance!

---

### Post by barbe-et-hache on 2007-05-23
Hi Jeff,

you can follow [this]("http://ubuntuforums.org/showthread.php?t=447744") thread. It should work with  your m-audio ozone as well. Use the usb-audio driver like for the m-audio fast track.

This thread is for ubuntu studio, just don't select the realtime option in jack. To be abble to use the realtime option in ubuntu feisty, follow [this]("http://ubuntuforums.org/showthread.php?t=451380")  thread.

Good luck!

---

### Post by Jeff BR on 2007-05-29
Hi!
Thanks for the response. I will check the posts you mentioned and I will return.
In fact I found the reason of my initial problem. I had installed in my PC three sound cards: the INTEL (on board), one M-AUDIO DELTA 1010LT connected via slot PCI and finally the M-AUDIO OZONE via USB. When you have both DELTA 1010LT and OZONE connected, only the DELTA 1010LT is recognized (I had the same problem in Windows). Now I just pull out the DELTA 1010LT and the UbuntuStudio (ALSA) showed the USB (OZONE) as an option to connected. Nice, but it worked until yesterday... :((( 
For some reason I am not having the USB option anymore (it shows only the on board sound card -INTEL- as the only option). I tried to connected OZONE in different USB ports (my PC has 8 ports) but it is not working. I have also installed the firmware loader DFU but irt is still not working. The only difference from yesterday is that I made the automatic update in UbuntuStudio today and I could see same updates related to low latency (but I don think that this is the problem...)
I will try to read the posts but, if someone have something in mind regarding this, please help me.
Thanks again!!!

---

### Post by claytor on 2007-06-06
I am new to the linux game, and I must say I really like the ease of UbuntuStudio.

However, I cannot seem to have both my JACK server running AND any other audio source (movie, youtube, music etc...).  If I have audio going, then i get a connection error when I try to start my JACK server.  If I have a JACK server running, I can't hear anything else except what audio I have going on in jackbeat or Audacity.

Is this just a hogging of the audio card?  Do I need to scold all involved and send them to bed with no cookies?  

I am sure it is an easy fix...Any ideas?

******EDIT******
I just changed my all my Devices in Sound Preferences to ALSA, and now I am able to use the JACK server and hear all other sources of audio...lol still a couple issues with the audio capture, but I think I am getting there...

---


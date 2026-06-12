---
title: "MythTV, Digital Cable Boxes and RF Blasters"
date: 2012-12-15
forum: Mythbuntu
---

### Post by sudanmas on 2012-12-15
I received an HD receiver from my CabCo (a Motorola DCX700) several weeks back and I have started to look at how to integrate it into my Myth TV setup before their analogue cable services are discontinued on January 1st 2013.

I'm running a Hauppage 250 on a single front/backend box.

The cabco told me the unit used IR and through a helpful suggestion of one of the forums users, I sourced a cheap IR Blaster.  Quickly figured out after I unpacked the HD receiver that the box uses RF instead of IR :-(

I've done a lot of googling and can't find anything that would allow my myth system to send RF signals to the HD receiver to change channels.

Any suggestions?

---

### Post by chadk5utc on 2012-12-15
per the site specs on  the Motorola it should have IR remote no mention of RF remote? in any event they do make adapters the hard part will be finding one that linux supports. [http://www.motorola.com/Video-Solutions/US-EN/Products-and-Services/Video-Consumer-Premise-Equipment/All-Digital-Set-Tops/DCX700_US-EN](http://www.motorola.com/Video-Solutions/US-EN/Products-and-Services/Video-Consumer-Premise-Equipment/All-Digital-Set-Tops/DCX700_US-EN)

---

### Post by sudanmas on 2012-12-15
Yeah, I saw that connector when I setup the box, but according to the cabco's tech support that port along with the USB and ethernet ports, are disabled.

I'll try it anyway I suppose and see what happens.

Tks

---

### Post by sudanmas on 2012-12-18
Turns out the IR port on the Motorola DCX700 is active.  I found out how to access the Motorola's diag menu and it verifies that the port is indeed running => Press the Power button and then press OK twice to access the menu.

I have my H'pge 250's IR Receiver plugged into the back of the DC box (had to use a 2.5mm to 3.5 headphone adapter).   The MyBlaster Serial device is plugged into com1 of the mythbox.

I downloaded MyBlaster serial scripts from sourceforge ([http://sourceforge.net/projects/myblaster](http://sourceforge.net/projects/myblaster)) and running the provided perl scripts lights up the MyBlaster Serial's IR Sender, but when I hold the IR blaster against the IR receiver and run either the channel changer or code checker scripts nothing happens on the DC box.

I noticed that when the IR blasters light comes on it remains steady.  From what I've been able to find I gather it's supposed to flash to simulate the pulses that come from the RF remote.

I'm not sure where to go from here - any suggestions?

---

### Post by nickrout on 2012-12-19
I think you are doint it wrong. The blaster plugs into your backend via USB. The blaster has a IR emitter that usually plugs in via an earphone like socket. The emitter sits in front of the IR reciver of the STB.

---

### Post by sudanmas on 2012-12-19
> **nickrout said:**
> I think you are doint it wrong. The blaster plugs into your backend via USB. The blaster has a IR emitter that usually plugs in via an earphone like socket. The emitter sits in front of the IR reciver of the STB.

Hi

The blasters from IRBLASTER.Info come in a couple flavors - both USB and serial port.  The blaster cable I bought has a serial connector on one end and the emitter on the other.  The serial port version is easier to work with I was told so that was the one I purchased.

My DC box doesn't natively operate via IR.  It uses an RF remote.  But the IR headphone connector in the back does allow you to bypass the RF receiver and allow the box.  At least that's how I understand it from [http://www.irblaster.info/motorola_rx.html](http://www.irblaster.info/motorola_rx.html)

---

### Post by klc5555 on 2012-12-20
Since you're trying to use an IR blaster to communicate through the IR port of the DCX700, you're using LIRC.

The problem would likely be that there doesn't seem to exist a lirc.conf file with the specific IR codes for the DCX700-M. Normally this might not be much of a deterrent --you'd record the out put from the supplied IR remote pertaining to the box, and use this to compose your own lirc.conf. But your cableco did not intend for the IR port to be used, and so did not supply an IR remote that you could record from.

So your one available recourse might be to adapt extant lirc.conf files designed for Motorola boxes closely related to the DCX700, in the hope that one of these may more-or-less get the job done. One such that could be tried is the config for the DCT700, which is discussed here: [https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script) Configs for the DCT2000 or DCH3200 are also possibilities.

I don't know what other approach you can take. Unless you can find a cheap universal IR remote that includes the configuration for the DCX700 that you irrecord from.

---

### Post by sudanmas on 2012-12-21
> **klc5555 said:**
> Since you're trying to use an IR blaster to communicate through the IR port of the DCX700, you're using LIRC.

The problem would likely be that there doesn't seem to exist a lirc.conf file with the specific IR codes for the DCX700-M. Normally this might not be much of a deterrent --you'd record the out put from the supplied IR remote pertaining to the box, and use this to compose your own lirc.conf. But your cableco did not intend for the IR port to be used, and so did not supply an IR remote that you could record from.

So your one available recourse might be to adapt extant lirc.conf files designed for Motorola boxes closely related to the DCX700, in the hope that one of these may more-or-less get the job done. One such that could be tried is the config for the DCT700, which is discussed here: [https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script](https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script) Configs for the DCT2000 or DCH3200 are also possibilities.

I don't know what other approach you can take. Unless you can find a cheap universal IR remote that includes the configuration for the DCX700 that you irrecord from.

That's something to go on - I'll give that approach a try.  The DCX700 is relatively new, so it may take a while for a specific .conf to be written for it.  In the interim I'll try script for one of the other boxes you mentioned.

---

### Post by nickrout on 2012-12-22
Just use lirc to record a conf file from the remote that came with the stb. Contribute it back to the lirc project. Become an open source contributor.

---

### Post by klc5555 on 2012-12-23
> **nickrout said:**
> Just use lirc to record a conf file from the remote that came with the stb. Contribute it back to the lirc project. Become an open source contributor.

To recap the initial post: the cable company provided an RF remote, as the box is primarily RF but retains secondary IR support. That's the crux of the problem. Though the IR port on the box also happens to be active, the cable company did not intend for it to be used, and so did not provide an IR remote. The OP has nothing to irrecord a lirc.conf from.

---

### Post by sudanmas on 2013-01-06
I am back at the DC Box / Mythtv issue and I wanted to confirm that I'm on the right track.

From what I've been reading here and elsewhere, I should be controlling my Serial IR Blaster via LIRC.  I understand that I should first have Serial LIRC loaded, which I currently do not.  

I've found instructions on how to do this here:

 [http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install](http://www.mythtv.org/wiki/Ubuntu_Serial_Lirc_Install)

But they appear to be specific to Feisty Fawn and I'm running Lucid Lynx 10.04 LTS

Should those install instructions work anyway?

---


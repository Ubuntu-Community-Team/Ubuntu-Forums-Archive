---
title: "New Hauppauge HVR-2250 OTA video corruption/partial lock problem"
date: 2010-12-14
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2010-12-14
This is an ugly update from [prior post]("http://ubuntuforums.org/showthread.php?t=1643131")

In the prior post, a 10dB inline coax amplifier added to solve video corruption (partial lock) problem on one tuner (2) on one channel (40-1) for over the air local broadcasts.

An unexpected result was new one channel (3-1) video corruption (partial lock) problem on the another channel on the other tuner (1).

The reliable and stuffy pseudo 1080p 47LX196 Toshiba television's signal strength meter says 3-1 signal is strongest of received, and 40-1 is the weakest received.  Itself has no problems locking on all channels with or without an inline coax amplifier.

I sure could use some suggestions or help here.  Is there an internal RF problem with the RF splitter?  Is one of the tuners out of whack?  Is my HVR-2250 broken?  Are all HVR-2250s Broken? :???:

---

### Post by klc5555 on 2010-12-15
> **keepitsimpleengr said:**
> This is an ugly update from [prior post]("http://ubuntuforums.org/showthread.php?t=1643131")

In the prior post, a 10dB inline coax amplifier added to solve video corruption (partial lock) problem on one tuner (2) on one channel (40-1) for over the air local broadcasts.

An unexpected result was new one channel (3-1) video corruption (partial lock) problem on the another channel on the other tuner (1).

The reliable and stuffy pseudo 1080p 47LX196 Toshiba television's signal strength meter says 3-1 signal is strongest of received, and 40-1 is the weakest received.  Itself has no problems locking on all channels with or without an inline coax amplifier.

I sure could use some suggestions or help here.  Is there an internal RF problem with the RF splitter?  Is one of the tuners out of whack?  Is my HVR-2250 broken?  Are all HVR-2250s Broken? :???:

Probably the amplified 3-1 is swamping the tuner (1) by being too strong. 

I don't use the 2250, but began to have a similar problem with a couple of 1600s that I use, now that the amplification issue with their cx18 driver is seemingly fixed. The two digital halves of the tuner could no longer receive a couple of stations (partial lock) until I took them off the amp.

Final solution was to split the line just before the amp : the swamped digital halves of the two 1600s got the straight feed with no amp, everything else including the analog side of these same 1600s, a pchdtv-5500 and an avermedia a180 continued to get the amp. And all tuners appear to be happy.

Maybe you'll need to split your tuner (1) away from the amp.

---

### Post by ktmom on 2010-12-15
I feel you pain.  I have the same card and found thta the tuner can be narrow minded as to what it's willing to accept.  That said, your problem more than likely has nothing to do with the card per se.  You need to look at what type of antenna you are using and where it is positioned relative to the two stations.  

Doing a quick look at antennaweb.org, for your city in your user location, those two stations are 6 degrees off from each other (to the center of the incorporated area, YMMV).  You might try re-aiming your antenna directly towards or to the side of the weaker station and away the strong one to reduce the signal coming in.  I didn't look to see what the transmitter powers are for the two stations, but that can present a challange also.

Additionally, you need to be concerned about scattered signal reflecting off area buildings.  I live in Florida so I have no experience with the issue of the signal scattering due to the mountain ranges to your east.  It's possible for your attenna to be picking up an out-of-phase signal reflected off something (such as local buildings) and making it even harder for the tuner to lock. 

Try looking at a local digital OTA forum and see what antennas, amps and pointing advice they recommend.

---

### Post by Barry_IA on 2010-12-15
> **keepitsimpleengr said:**
> 

In the prior post, a 10dB inline coax amplifier added to solve video corruption (partial lock) problem on one tuner (2) on one channel (40-1) for over the air local broadcasts.

An unexpected result was new one channel (3-1) video corruption (partial lock) problem on the another channel on the other tuner (1).

The reliable and stuffy pseudo 1080p 47LX196 Toshiba television's signal strength meter says 3-1 signal is strongest of received, and 40-1 is the weakest received.  Itself has no problems locking on all channels with or without an inline coax amplifier.

I sure could use some suggestions or help here.  Is there an internal RF problem with the RF splitter?  Is one of the tuners out of whack?  Is my HVR-2250 broken?  Are all HVR-2250s Broken? :???:

KeepItSimpleEngr:

I've been fooling around with OTA reception here in the Quad Cities metropolitian area (Davenport/Bettendorf, IA; Rock Island/Moline IL).  It seems too much signal as well as not enough signal will cause problems.  Not enough and the signal level is below spec; too much and the AGC goes into overdrive and shuts off.

As for the HVR-2250, seems it needs to display at least 2.2 dB, 2.3 and 2.4 are preferred.  (I've never seen a higher S/N ratio.)    Unfortunately the HVR-2250's don't appear to have a S-meter option (is that on a wish list?  ;) ).

As for the mechicals, you might want to try a different splitter.  Watch your frequencies:  if your local stationars are still using VHF (one is locally) then  RF2 is 54 MHz at it's low end,  RF13 is 216 MHz at it's high end.  Otherwise they're using UHF frequencies: RF14's low side is 470 MHz and RF 51's high end is 698 MHz.  Different splitters have different insertion loss.  You are generally better off using as few splitters as possible: use one 4-way splitter instead of two or three 2-way splitters.

BTW, to complicate things the RF channel is generally not the same as the station's reported channel.  Locally Channel 6.1 is at RF36.  Look for your stations by call sign in Wiki -- they seem to have been a pretty good job of reporting the RF channels.

---

### Post by keepitsimpleengr on 2010-12-15
> **Barry_IA said:**
> …It seems too much signal as well as not enough signal will cause problems.  Not enough and the signal level is below spec; too much and the AGC goes into overdrive and shuts off.

As for the HVR-2250, seems it needs to display at least 2.2 dB, 2.3 and 2.4 are preferred. … if your local stationars are still using VHF (one is locally) then  RF2 is 54 MHz at it's low end,  RF13 is 216 MHz at it's high end.  Otherwise they're using UHF frequencies: RF14's low side is 470 MHz and RF 51's high end is 698 MHz.  …

OK…

xmit towers for 3-1 and 40-1 are 13.5 and 14.5 miles away, about 0.5° apart, &#8776;2000' above sea level.  I'm 47' above sea level, 16' antenna height, no higher ground between.  Checked on Google earth.  On a clear day all tower tops can be seen about 3-5° above the horizon.

The only obstruction/reflection point is the [General Mills plant]("http://www.panoramio.com/photo/10496383") 50° ccw and 0.5 mi away.

Antenna is a powered [Winegard GS-2200]("http://www.winegard.com/kbase/upload/GS-2200.pdf") with high directionality especially at higher frequencies.

From [antennaweb.org]("http://www.antennaweb.org/aw/Welcome.aspx")

[FONT="Courier New"]Channel/Compass Heading/Miles From/RF Channel/Frequency(MHz)
·6.1 · 292° · 14.5 · ·9 · VHF high-band 186-192
10.1 · 285° · 13.1 · 10 · VHF high-band 192-198
31.1 · 285° · 13.1 · 21 · UHF band 512-518
13.1 · 285° · 13.1 · 25 · UHF band 530-536
[COLOR="DarkRed"]·3.1 · 293° · 13.5 · 35 · UHF band 596-602
40.1 · 292° · 14.5 · 40 · UHF band 626-632[/COLOR]
58.1 · 295° · 12.8 · 46 · UHF band 662-668[/FONT]

Notice the two problem channels are [COLOR="DarkRed"]co-located in frequency[/COLOR]. 

I have tried:
antenna&#8943;coax&#8943;antenna p/s&#8943;coax&#8943;splitter(1)&#8943;2250;(2)&#8943;TV
and
antenna&#8943;coax&#8943;antenna p/s&#8943;coax&#8943;splitter(1)&#8943;[COLOR="Purple"]inline amp[/COLOR]&#8943;2250;(2)&#8943;TV
and
antenna&#8943;coax&#8943;antenna p/s&#8943;coax&#8943;[COLOR="Purple"]inline amp[/COLOR]&#8943;splitter(1)&#8943;2250;(2)&#8943;TV

next I'll try:
antenna&#8943;coax&#8943;antenna p/s&#8943;[COLOR="Purple"]inline amp[/COLOR]&#8943;coax&#8943;splitter(1)&#8943;2250;(2)&#8943;TV

The frustrating part of this problem is that the 2250s have one input with an internal splitter for the two tuners.  With the inline amp (10dB) the stronger 3-1 channel loses lock on one of the tuners, and unamplified the weaker 40-1 loses lock on the other tuner.  Obviously the gain/loss/sensitivity is very different for the two tuner channels.

So…

Anybody know anythig about RF coax attenuators or Tilt Compensators?    &#8943;[&#8213;»here]("http://www.hometech.com/hts/products/video/attenuators/index.html")

Perhaps the Winegard is distorting the high power transmission and I should replace it with an unpowered?

Should I try Hauppauge support?  :confused:

---

### Post by Barry_IA on 2010-12-16
Hi KeepItSimpleEngr!

> **keepitsimpleengr said:**
> 
xmit towers for 3-1 and 40-1 are 13.5 and 14.5 miles away, about 0.5° apart, &#8776;2000' above sea level.  I'm 47' above sea level, 16' antenna height, no higher ground between.  Checked on Google earth.  On a clear day all tower tops can be seen about 3-5° above the horizon.
The only obstruction/reflection point is the [General Mills plant]("http://www.panoramio.com/photo/10496383") 50° ccw and 0.5 mi away. 
  
Not seeing a problem, though possibly signal bounces off the General Mills plant.   Admittedly a WAG but with weird problems like you and I are having....



> [FONT=Courier New]Channel/Compass Heading/Miles From/RF Channel/Frequency(MHz)
·6.1 · 292° · 14.5 · ·9 · VHF high-band 186-192
10.1 · 285° · 13.1 · 10 · VHF high-band 192-198
31.1 · 285° · 13.1 · 21 · UHF band 512-518
13.1 · 285° · 13.1 · 25 · UHF band 530-536
[COLOR=DarkRed]·3.1 · 293° · 13.5 · 35 · UHF band 596-602
40.1 · 292° · 14.5 · 40 · UHF band 626-632[/COLOR]
58.1 · 295° · 12.8 · 46 · UHF band 662-668[/FONT]Not seeing Xmtr Power; here I'm having drop out problems with one of the three stations transmitting at 1,000 KW and they're at the same antenna farm.


  


> I have tried:
antenna&#8943;coax&#8943;antenna p/s&#8943;coax&#8943;splitter(1)&#8943;2250;(2)&#8943;TV
and
antenna&#8943;coax&#8943;antenna p/s&#8943;coax&#8943;splitter(1)&#8943;[COLOR=Purple]inline amp[/COLOR]&#8943;2250;(2)&#8943;TV
and
antenna&#8943;coax&#8943;antenna p/s&#8943;coax&#8943;[COLOR=Purple]inline amp[/COLOR]&#8943;splitter(1)&#8943;2250;(2)&#8943;TV

next I'll try:
antenna&#8943;coax&#8943;antenna p/s&#8943;[COLOR=Purple]inline amp[/COLOR]&#8943;coax&#8943;splitter(1)&#8943;2250;(2)&#8943;TVI'll probably have a few really nasty comments stating I'm nuts for doing this but what I did was add a passive antenna (!).  Amplified antenna to one input of an RF _coupler_, passive antenna to the other input. Output of the coupler goes to the splitter to the two HVR-1600 tuners + HVR-2250 tuner.

I also have a 25 dB RF amplifier with it's gain about 1/3 on the output of the passive antenna.  So it's passive antenna --> amplifer --> input B of RF coupler.  Seemed it might be a little complicated to visualize with only the verbage and you know how ASCII drawings can turn out!


> The frustrating part of this problem is that the 2250s have one input with an internal splitter for the two tuners.  With the inline amp (10dB) the stronger 3-1 channel loses lock on one of the tuners, and unamplified the weaker 40-1 loses lock on the other tuner.  Obviously the gain/loss/sensitivity is very different for the two tuner channels.Yes, I have also noticed that.  My two HVR-1600 tuners have different channel line ups.  Figuring as long as I get the entire OTA line-up one way or another....



> Anybody know anythig about RF coax attenuators or Tilt Compensators?I've not heard of a 'Tilt Compensator' before -- interesting!  What I would do, especially as in the experimental phase, is find a variable RF attenuator.  I have an old/antique one with switches labeled 3 dB, 6 dB and 12 dB.  Flipping through various combinations allows for 0 dB, 3 dB, 6 dB, 9 dB, etc.

Good Luck!

---

### Post by keepitsimpleengr on 2010-12-23
So I rounded up a Windows 7 Premium 64bit and a spare HD, and installed it on this HTPC.

Reception problems even worse.

:sad:

---

### Post by Barry_IA on 2010-12-24
> **keepitsimpleengr said:**
> So I rounded up a Windows 7 Premium 64bit and a spare HD, and installed it on this HTPC. Reception problems even worse. :sad:

Ouch.  I'm thinking maybe check out the antenna input in it's entirety.  Is it possible to connect a TV to the coax end which is now connected to the input of the HVR-2250?  (And speaking of connections,  a really stupid question: you are using the correct  input, right?!)  Connecting a TV (or DTV Converter Box + TV) would let you see what's going in to the HVR-2250.  I've had faulty manufactured cables before.

Hope it's something simple!

---

### Post by LowSky on 2010-12-25
poorly shielded cables can cause a heap of problems from interference. So can poorly aimed antennas and using too many splitters.

---

### Post by keepitsimpleengr on 2010-12-28
It is now apparent that the problem is the RF font end of the HVR-2250.

The TV at the coax end has no problems locking on to all channels, with or without the inline amplifier.

The 2250, which internally splits the RF into two paths, has unbalanced paths.

With the inline amplifier, the weak station has no problem with either of the two 2250 paths, but the strong station loses lock with tuner 0.

Without the inline amplifier, the strong station has no problem with either tuner, but the weak station loses lock with tuner 1.

The conclusion is the sensitivity and tendency to overload is much greater with tuner 0 than with tuner 1.

As it stands now, I'm using the inline amplifier and giving up using tuner 0 on when receiving the strong station.  This works out better than the alternative, because so few recordings are made with the strong station.

---

### Post by Barry_IA on 2010-12-29
> **keepitsimpleengr said:**
> With the inline amplifier, the weak station has no problem with either of the two 2250 paths, but the strong station loses lock with tuner 0.

Without the inline amplifier, the strong station has no problem with either tuner, but the weak station loses lock with tuner 1.

<snip>

As it stands now, I'm using the inline amplifier and giving up using tuner 0 on when receiving the strong station.  This works out better than the alternative, because so few recordings are made with the strong station.

That might be the best solution for the time being.  You might want to delete the strong station from tuner 0's lineup so you don't accidentally record on the wrong tuner.  Do the same for the weak station.  

Another option might be to get a high-Q attenuator for the strong station to weaken the signal.  The only ones I've seen (but I haven't looked in 20+ years!) would pretty much wipe out the station.  ...Went to check if any values on the two I have besides frequency; none, but what I have are 'traps'.  You don't want that!  (So the cheapest way and probably the easiest is to delete the stations in the individual tuner's lineups.)

---

### Post by keepitsimpleengr on 2011-01-19
Out of town for three weeks, and on return discovered even the HDTV was not receiving all channels.  Replaced the antenna (an older version of Winegard GS-2200 powered with a new GS-2200) and now getting strong signal on all HDTV channels.

Suspect that was entire problem, but cannot be sure until Watch TV (Live TV) starts working, a separate post!!

---

### Post by keepitsimpleengr on 2011-01-21
> **keepitsimpleengr said:**
>  Replaced the antenna (an older version of Winegard GS-2200 powered with a new GS-2200) and now getting strong signal on all HDTV channels.!

Confirm old Winegard powered antenna was the problem.

---

### Post by Barry_IA on 2011-01-22
[FONT=Palatino Linotype]Nothing like having what seems to be working properly not work properly! <g>

Might want to mark this thread as "Solved" to assist others where searching for solutions to similar problems.  ;)
[/FONT]

---

### Post by azich on 2011-01-26
I was able to get an HVR-2250 working on Ubuntu 11.04 2.6.35-24-generic by substituting the basic hg clone / make / make install with something a bit more complicated but ultimately successful for me:

```

0. `sudo apt-get install v4l-conf`
1. `hg clone http://kernellabs.com/hg/~stoth/saa7164-v4l`
2. Use this as v4l/.config: [http://pastebin.com/4GPrszBV](http://pastebin.com/4GPrszBV)
4. `make`

5. For all files with implicit declaration of function 'usb_buffer_free', add the following to the top after the #includes.

#define usb_buffer_alloc(a, b, c, d) usb_alloc_coherent(a, b, c, d)
#define usb_buffer_free(a, b, c, d) usb_free_coherent(a, b, c, d)

6. Repeat steps 4 and 5 until you no longer encounter the 'usb_buffer_free' errors.

7. You should now encounter the 'struct net_device' errors. Download the full linux-source-2.6.35, decompress it, and copy the following to the v4l directory.

linux-source-2.6.35/drivers/media/dvb/dvb-core/*.h
linux-source-2.6.35/drivers/media/dvb/dvb-core/*.c

8. `make`
9. You may encounter more 'usb_buffer_free' errors, if so, repeat steps 4 and 5 again until it goes away.
10. `sudo make install`
11. `sudo modprobe -r saa7164; sudo modprobe saa7164` or `reboot`

```

Here is the relevant section of the kernel log after the modprobe: [http://pastebin.com/rWB6WBhB](http://pastebin.com/rWB6WBhB)



Hope this helps!

---


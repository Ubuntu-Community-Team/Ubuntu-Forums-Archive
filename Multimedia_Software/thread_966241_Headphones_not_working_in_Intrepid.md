---
title: "Headphones not working in Intrepid"
date: 2008-11-01
forum: Multimedia Software
---

### Post by exclipy on 2008-11-01
My headphones aren't working after upgrading to Intrepid.  I plug them in and the speakers turn off but nothing is heard through the headphones.  I've looked at other threads, where the solution is to unmute the "Surround" slider in the volume control, or to disable/enable "Headphone as Line Out", but neither of these work for me.

I'm on a Dell Studio 15 laptop.

---

### Post by Izkata on 2008-11-02
Dell Studio 1535, exact same problem.

Headphones do not work in Intrepid, although the speakers do get muted.

The fixes posted so far (unmute Surround and toggle "Headphone as line out") do not work.  If I turn on "Headphone as line out", the speakers unmute.

It worked perfectly in Hardy.

EDIT:  In addition, it works perfectly on the Intrepid LiveCD.  But not after being installed, apparently...

---

### Post by cisoprogressivo on 2008-11-02
Same problem here with Studio 15 (Inspiron 1535) headphone jack doesn't work anymore in Intrepid.

---

### Post by hutuworm on 2008-11-02
Dell D430, no sound from headphone, even installed the latest ALSA driver 1.0.18 from source.

---

### Post by hutuworm on 2008-11-02
> **hutuworm said:**
> Dell D430, no sound from headphone, even installed the latest ALSA driver 1.0.18 from source.


lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 0201
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by Marsalsa on 2008-11-03
also on a dell Studio 1535

same problem, no solution so far,
sound works perfectly through speakers
plugging in my headphone mutes the speakers, but doesn't give sound through headphone

---

### Post by iLoveRuby on 2008-11-03
Same problem.  Headphones not working after upgrading from 8.04 to 8.10.

lspci -v expcerpt:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 8284
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at ffdf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

---

### Post by iLoveRuby on 2008-11-03
(See post #4 here: [http://ubuntuforums.org/showthread.php?t=891823](http://ubuntuforums.org/showthread.php?t=891823))

I got my headphones to work by opening **Volume Control**, selecting my **Alsa Mixer**, clicking **Preferences**, checking **Surround**, and then turning up the **volume for Surround**.

---

### Post by Marsalsa on 2008-11-04
> **iLoveRuby said:**
> (See post #4 here: [http://ubuntuforums.org/showthread.php?t=891823](http://ubuntuforums.org/showthread.php?t=891823))

I got my headphones to work by opening **Volume Control**, selecting my **Alsa Mixer**, clicking **Preferences**, checking **Surround**, and then turning up the **volume for Surround**.

do you also have a studio?

It doesn't seem to work for me...

---

### Post by iLoveRuby on 2008-11-04
> **Marsalsa said:**
> do you also have a studio?

It doesn't seem to work for me...

No, my machine is a custom-built laptop from [www.linuxcertified.com](www.linuxcertified.com).  

Try opening Volume Control and enabling Surround (and turn up the Surround Volume) for the different "**Devices**" that you can select from the drop-down menu.  For me, I had to select a **Device** other than the default one.  (If you haven't already done this.)

When you enter ```
lspci -v
``` into your shell prompt, what does it say beside "*Audio device*"?

---

### Post by exclipy on 2008-11-04
As I said in the original post, turning up the volume for "Surround" doesn't do anything.  Also, the other devices in the drop-down menu do not have a Surround option.

The common theme for people who have this problem so far is the Dell Studio 1535.

This is what lspci -v says for me:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 0254
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6dfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```


If I can't get this fixed soon, I may have to downgrade to Hardy (as anyone with a Studio 15 knows, the built-in speakers are really tinny).  Is it possible to downgrade safely?

---

### Post by speed32219 on 2008-11-04
Also, post output of cat .asoundrc in your home directory.

---

### Post by exclipy on 2008-11-04
.asoundrc doesn't exist in my home directory.

---

### Post by eldersoares on 2008-11-04
I have similar problems, one of the jacks doesnt work and the one that works, doesnt mute the integrated speakers when active. dell studio 1535

---

### Post by exclipy on 2008-11-04
Neither of the jacks works for me.

---

### Post by Marsalsa on 2008-11-05
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 029f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by l1th1um on 2008-11-05
thanks, the 'surround' things work for me. but, when i plug the headphone, i've to manually mute the front volume, so the sound just come from my headphone not also from my speaker

---

### Post by cisoprogressivo on 2008-11-05
I opened a bug on launchpad:
[https://bugs.launchpad.net/dell/+bug/294418](https://bugs.launchpad.net/dell/+bug/294418)

---

### Post by mbeach on 2008-11-06
same issue here on a 1735 studio.  In Hardy, the 'surround' slider did control one of the headphone jacks.  In 8.10, can only get sound from the headphones if I enable the headphones as line out jack switch (but mute the 'front' slider, otherwise sound comes from the laptop speakers).

lspci -v
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Dell Device 0256
	Flags: bus master, fast devsel, latency 0, IRQ 21
	Memory at f6dfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

incidentally:
the jack closest to the front of the machine does not seem to get any sound, only the second one (closest to the mic jack) gets any sound - controlled on the headphone slider.  The surround slider seemingly controls nothing now.

---

### Post by Izkata on 2008-11-06
> **exclipy said:**
> If I can't get this fixed soon, I may have to downgrade to Hardy (as anyone with a Studio 15 knows, the built-in speakers are really tinny).  Is it possible to downgrade safely?
No.  Backup your home folder somewhere else, and format the partition for a clean install.

I tried installing over it in a downgrade-fashion, and created some sort of Zombie 'Buntu - it somehow no longer understood how packages worked, and I couldn't do anything.

---

### Post by exclipy on 2008-11-07
> In 8.10, can only get sound from the headphones if I enable the headphones as line out jack switch (but mute the 'front' slider, otherwise sound comes from the laptop speakers).

the jack closest to the front of the machine does not seem to get any sound, only the second one (closest to the mic jack) gets any sound - controlled on the headphone slider. The surround slider seemingly controls nothing now.

Ah, yes.  Thanks for that!  That's how it is on my machine.  I'm happy enough having figured out how to get sound to come out of my headphones :)

---

### Post by pyronordicman on 2008-11-08
I have the same problem, but the posted solutions do nothing for me.
My laptop is a Gateway T-1623 with an ATI X1200 audio controller.

[INDENT]01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Subsystem: ATI Technologies Inc Radeon X1200 Series Audio Controller
	Flags: bus master, fast devsel, latency 64, IRQ 19
	Memory at cfdec000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
[/INDENT]

The headphone output worked fine in Gutsy and Hardy.  I also have no special settings in ~/.asoundrc.

---

### Post by tripuz on 2008-11-09
Same problem for me on a Studio 1535:
[LIST]
[*]the first jack (the left one) works, but I can't find a way to mute the internal speakers when I connect it to the headphones. 
[*]the second jack (the right one) does mute the internal speakers when I plug the headphones in, but I can't hear anything from them :confused:
[/LIST]

---

### Post by marioquark on 2008-11-09
same problem on dell studio 1535

i think it should be good to edit the file **/etc/modprobe.d/alsa-base**
and set to the end of the file the correct model name:

**options snd-hda-intel model=**????

but i don't know what model to set... :confused:

---

### Post by Horshamite on 2008-11-10
New user here and all. One of the best ways to enable the headphones without downloading patches etc, is to go into preferences, and enable everything available, be it playback, recording etc. Once everything has been enabled, go into switches and enable duplicate front. Go into playback, unmute everything that is muted. Then, three sliders affect headphone volume: PCM, Surround and VIA DXS. PCM adjusts speakers when headphones are unplugged, also acts as a volume control for headphones. Surround only adjusts headphones. VIA DXS does pretty much the same thing.

Only issue I have now is that, with no headphones in volume control either with Fn + (volume up/down) the volume can be adjusted. But with headphones in, this function doesn't work. To higher or lower volume control you have to manually adjust the settings in Surround preferably.

---

### Post by tripuz on 2008-11-10
> **Horshamite said:**
> Once everything has been enabled, go into switches and enable duplicate front.

Thanks for the suggestion. Unfortunately, I have no "duplicate front" switch in my preferences...I know this sounds weird (sounds...lol :) ), but I also have no "line out as output" switch, which was suggested in another post.
Well, I'll wait for some updates and see what happens!

---

### Post by Horshamite on 2008-11-10
Well, I did have a series of updates come through, and one did have ALSA mentioned in its file name. This was about 1 hour ago.

---

### Post by romaluca on 2008-11-13
I have the same problem
dell 1535

Are there news?
thanks

---

### Post by Kulgan on 2008-11-14
No news as far as I've heard :(

I haven't been able to find any combination to turn off the speakers while keeping sound on the headphones. Rather annoying in libraries... And classes...

---

### Post by philetus on 2008-11-14
Does "Flags" mean something is wrong?

 lspci -v

00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
	Subsystem: Giga-byte Technology Device ae01
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	I/O ports at d800 [size=256]
	I/O ports at dc00 [size=256]
	Memory at f4000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

---

### Post by Blarion on 2008-11-17
Meep. Same problem here. When I plug in my headphones, the sound still comes out of the speakers...

---

### Post by cisoprogressivo on 2008-11-21
Now the bug is public:
[https://bugs.launchpad.net/dell/+bug/294418](https://bugs.launchpad.net/dell/+bug/294418)
Please subscribe it.

---

### Post by mbeach on 2008-11-21
My work around from my post above worked for awhile - but recently (sometime around Nov 11th) both headphone jacks in my Dell Studio 1735 stopped working - no sound out of either. Both jacks worked in Hardy, each controlled by its own volume slider (surround and headphones). Then upgrade to Intrepid (upgrade, not full install) knocked out the frontmost jack, but the second jack worked if the headphone as line out switch was checked and "front" volume muted (to silence the main speakers). I think the loss of headphones came with the kernel upgrade (2.6.27.7.11) to 2.6.27.8.12 but I can't be sure.

UPDATE: Intrepid seems to be not picking up the HDA Intel as the default card - I think it may be selecting an ATI HDMI card as the default.  I was able to get sound out of the middle headphone jack after installing gnome-alsamixer but only matched with the laptop speakers - ie headphones and speakers are on one control, and the speakers are not muted.  The gnome alsamixer appears to only see the "Silicon Image Sil1392 HDMI" card.  

Enabling "Multimedia Systems Selector" under System -> Preferences, the HDA Intel card does not appear, although it is listed in the volume control (alsa mixer).

---

### Post by mbeach on 2008-11-25
With an update to kernel (2.6.27.8.12) to 2.6.27.10.13, the front most headphone jack mutes the speakers when plugged in and volume is controlled by the 'front' slider. The 'front' slider also controls the laptop speakers when the headphones are not plugged in. The headphone as line out switch appears to do nothing when the front jack is used.

The headphone jack further from the front also works but it is dependent on the headphone as line out switch. With that switch deactivated, the laptop speakers are muted, and sound comes through the headphones. When it is checked, sound comes through both the headphones and the speakers. Volume still controlled on the 'front' slider.

Perfect for me. Resolved.

---

### Post by Kulgan on 2008-11-25
Installed updates, reinstalled (using proposed repo). Did you have to manually edit menu.lst?

No change here... :/

---

### Post by salefish on 2008-11-25
I believe that I have the same problem. I will go a little more in depth with my explanation. 
  I am using a Toshiba Satellite L35-2366 with Ubuntu 8.10 and Windows XP dual boot. My headphones, that do not work, are Logitech ClearChat Pro USB.
  When I plug in my headphones the graphic of the volume lowering sometimes pops up, but never lowers more than a quarter of the way. I can also hear static in the headphones, and if I speak into the microphne attached I can hear it in the headset.
  When I open my volume master control via double clicking on the task bar volume icon, the drop down device menu indicates that it recognizes that the headphones are plugged in. Though they are not selected. I can manually select them and it does not make any difference.
 [COLOR="Red"] I go to system/preferences/sound  and change the playback from auto detect to logitech usb headset via alsa and hit test, I get the error message "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback." I switch the output to logitech usb via OSS and hit test I can hear sound. [/COLOR]
  I switched all sound to OSS and the only sound I can get in the headset is when I hit test. All other sound comes from the computer speakers.

---

### Post by apw on 2008-12-01
I have a Dell Stupid 15 (model 1537) which suffers from this issue.  I have found that the Intrepid -proposed kernel 2.6.27-10.20 with the following added to /etc/modprobe.conf/alsa-base sorts things out:

     options snd-hda-intel model=dell-m6

With this I get sound in both headphone sockets and the one nearest the front turns off the speakers as expected.

---

### Post by cisoprogressivo on 2008-12-01
As I wrote on launchpad:
Studio 1535 with Kubuntu 8.10 works now everything fine
Studio 1537 with Ubuntu 8.10, but with Pulseaudio unistalled, doesn't work.

---

### Post by Kulgan on 2008-12-01
Thanks, apw (aka Andy Whitcroft? :P )

That works great, also on 1537. Thanks again!

---

### Post by ZaHACKieL on 2008-12-13
I have a Dell Studio 1735. I confirm that issue. When I connect the headphones to the first (left) output , the speaker mute. The second output (center) doesn't work at all....if I connect something there, nothing happens. I noticed that in Vista that center ouput doesn't work either.

Since yesterday i've been having a weird issue. My speaker stopped working, even when the OS detected the card and audio. It didn't work in Vista either. Now, to make it work, I have to turn on the "Headphone as Line Out" option....only then the speaker works.

You can read my full story here:

[http://ubuntuforums.org/showthread.php?p=6355568](http://ubuntuforums.org/showthread.php?p=6355568)

---

### Post by cisoprogressivo on 2008-12-13
@Zahackiel: kill pulseaudio. I solved in this way.

---

### Post by ZaHACKieL on 2008-12-13
> **cisoprogressivo said:**
> @Zahackiel: kill pulseaudio. I solved in this way.

Which ploblem did you solve doing that? the headphones-not-working issue? or the one I told about the speakers working only with the headphone as line out option turned on? thanx !

---

### Post by Marsalsa on 2008-12-24
I'm now working with kernel 2.6.27-11-generic (installed with synaptic via ticking updates->pre-released updates in the Software Sources)

everything is now working as it shoulds, two headphone outputs and both mute the speakers

---

### Post by ZaHACKieL on 2009-07-29
> **Marsalsa said:**
> I'm now working with kernel 2.6.27-11-generic (installed with synaptic via ticking updates->pre-released updates in the Software Sources)

everything is now working as it shoulds, two headphone outputs and both mute the speakers

I can confirm that it works as it shoulds with the 2.6.28-13-generic kernel

---


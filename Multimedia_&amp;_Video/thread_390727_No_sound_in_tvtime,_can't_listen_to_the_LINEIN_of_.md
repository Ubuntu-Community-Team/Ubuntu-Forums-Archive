---
title: "No sound in tvtime, can't listen to the LINEIN of the audio card?"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by highmighty on 2007-03-22
Hi all,

I'm having a problem with TVTIME, the video signal (e.g. my satellite) works fine but there is NO AUDIO  :(

By looking at the output of lspci and dmesg, it looks like the capture card is partially detected (*** UNKNOWN/GENERIC ***  [card=0,autodetected]), it detects the VIDEO controller as a Bt848 chipset but the AUDIO controller part of the capture card is not detected nor loaded... what should I do?

I've tried force loading a specific card model ([http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV](http://www.linuxtv.org/v4lwiki/index.php/Cardlist.BTTV)) with command-line options (e.g. "modprobe -v bttv tuner=2 card=41") for example, the radio part now "seems" enabled but still, tvtime won't let me hear any audio...

lspci:
************************************************
02:04.0 Multimedia video controller: Brooktree Corporation Bt848 Video Capture (rev 11)
************************************************

dmesg with bttv autodetection:
************************************************
[17179598.744000] bttv0: Bt848 (rev 17) at 0000:02:04.0, irq: 217, latency: 32, mmio: 0xec6ff000
[17179598.744000] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[17179598.744000] bttv0: gpio: en=00000000, out=00000000 in=00feffc3 [init]
[17179598.748000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[17179598.748000] bttv0: using tuner=-1
[17179598.748000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179598.752000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179598.752000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179598.756000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17179598.760000] bttv0: registered device video0
[17179598.760000] bttv0: registered device vbi0
************************************************

dmesg with bttv card# 41 force-loaded:
************************************************
[17183024.920000] bttv0: Bt848 (rev 17) at 0000:02:04.0, irq: 217, latency: 32, mmio: 0xec6ff000
[17183024.920000] bttv0: using: AVerMedia TVPhone 98 [card=41,insmod option]
[17183024.920000] bttv0: gpio: en=00000000, out=00000000 in=00feffc3 [init]
[17183024.928000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[17183024.928000] bttv0: Avermedia eeprom[0x0000]: tuner=2 radio:no remote control:no
[17183024.928000] bttv0: using tuner=2
[17183024.928000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17183024.928000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17183024.932000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17183024.988000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17183025.032000] tuner 0-0061: chip found @ 0xc2 (bt848 #0 [sw])
[17183025.032000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17183025.068000] bttv0: registered device video0
[17183025.068000] bttv0: registered device vbi0
[17183025.068000] bttv0: registered device radio0
************************************************

Here are the details of what I've gathered so far:

It's definitely a Bt848 chipset, the company name is AverMedia but I don't know exactly which model it is: I think it's either a TVPhone, a TVCapture 98 or TVPhone98, it has 3 video input type (television, composite or s-video), it also has a FM radio tuner and an IR port (w/ remote), there is an audio IN on the card (where I plug the audio L/R cable of my satellite) and also an audio OUT which is plugged in the LINEIN of my Creative Audigy sound card.

I can easily see my video signal (e.g. my satellite) with TVTIME by switching the video source from TELEVISION to COMPOSITE1 but there is no option that would allow me to switch the AUDIO source to the LINEIN of the Audigy sound card (where the audio signal of the satellite comes).  And FYI, in Windows, it sure works with DScaler, there is a menu that allows me to switch the AUDIO INPUT TYPE to EXTERNAL (e.g. LINEIN).

I surely tried SOX ([http://tvtime.sourceforge.net/help.html#audioconnect](http://tvtime.sourceforge.net/help.html#audioconnect)) but it seems that there is nothing else loaded other than /dev/dsp for my audio input filename?!

I've read a lot and tried several options without any luck so far... could you guys and gals help me please!

Thank you for your time,

highmighty

---

### Post by highmighty on 2007-03-26
Any thoughts anyone?

I can't wait to totally switch to Ubuntu...

Thank you all for your time,

highmighty

---

### Post by highmighty on 2007-03-28
Hi all,

Is there something wrong in my post?  Can someone help me please?  Does someone have any ideas?

Thank you all for your time,

highmighty

---

### Post by fenian on 2007-03-28
Open the sound control panel (left click icon on desktop,open volume control),make sure the line in isn't muted out.

---

### Post by highmighty on 2007-03-30
Nope, there is nothing muted out under the "playback or capture" tab of the volume control...

It looks more to be a problem with the audio part of the capture that isn't loaded properly (or at all), I think _I should_ see something like this under lspci: [COLOR="Red"]Brooktree Corporation Bt848 **audio** Capture[/COLOR]

HELP!

Thanks to all,

highmighty

---

### Post by tuke81 on 2007-04-01
Uhoh what is the output of command **lsmod | grep snd**?

Bt878 alsa sound driver should be in the kernel:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Brooktree&card=.&chip=Bt878%2C+Bt878a&module=bt87x](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Brooktree&card=.&chip=Bt878%2C+Bt878a&module=bt87x)
So are that loaded(snd_bt87x)?

If it is you should check are there bt878 audio device in **cat /proc/asound/cards**
If you see right card there, you can adjust it by command **alsamixer -c #**(where # is the card number, i.e alsamixer -c 1). Or if you like to do it in gui install alsamixergui(it is on universe) and open card mixer in terminal by typing **alsamixergui -c #**

---

### Post by highmighty on 2007-04-02
Thanks tuke81

Here's what you've asked for...

**lsmod | grep snd**:

snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  5 snd_emu10k1_synth
snd_rawmidi            27264  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_ac97_codec         97696  1 snd_emu10k1
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  5 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd                    58372  19 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              11232  1 snd

**cat /proc/asound/cards**:

0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xd000, irq 225

So no, it looks like **snd_bt87x** isn't loaded...

What should I do next?


Thank you for your time!
highmighty

---

### Post by tuke81 on 2007-04-02
Hmm you said that card can be  [[COLOR="Blue"]TVPhone[/COLOR]](http://www.bttv-gallery.de/high/M1A8-C-front.jpg_avermedia_tvphone.jpg), [[COLOR="blue"]a TVCapture 98  or TVPhone98[/COLOR]](http://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/AVerMedia_TVPhone98.jpg/800px-AVerMedia_TVPhone98.jpg)(it is the same card. And of cource lspci -v | grep Bt878 should tell the cards pciid.). [There]("http://tldp.org/HOWTO/BTTV/cards.html") is a list of supported cards.
So it can be card=13 aswell. So try to load it, before you try other things. Those cards should be well-supported in linux, so modprobing the right card could be only thing that you need. 

[http://www.linuxtv.org/v4lwiki/index.php/TVCapture_98](http://www.linuxtv.org/v4lwiki/index.php/TVCapture_98) is something about of that kind of cards.

EDIT: Oh and also tvphone is card=6. [http://www.bttv-gallery.de/high/](http://www.bttv-gallery.de/high/) (if somewhere your card should be there) If dmessage shows right the chip in your card is bt848 and so your card must be avermedia tvphone.

---

### Post by highmighty on 2007-04-03
Thanks again!

I finally found the proper capture card name, it's an **[Avermedia M108-A]("http://www.bttv-gallery.de/high/Avermedia_M108-B_bt848_and_M118-A_pic16c54.jpg")**.

Then, I first tried modprobing card=6 then card=13 and then card=40. No positive result. I then modprobed a bunch of the listed card (e.g. card=1 to card=50) because I couldn't find the exact M108-A model listed... and unfortunately, none of them enabled the audio capture part of the card even though some enabled the IR port... no use for the moment :) 

I tend to say that the problem must be elsewhere... don't you think?

Also, still no **snd_bt87x** under **lsmod | grep snd**... but does this sound driver refers to the bt878 chipset only (mine is a bt8**4**8 )?

Here are the chipsets found on the card: Bt848KPF and FR1236

Here is the output of **dmesg** after modprobing bttv to **card=6** and **tuner=2**:

[17185216.684000] bttv: driver version 0.9.16 loaded
[17185216.684000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17185216.684000] bttv: Bt8xx card found (0).
[17185216.684000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 217
[17185216.684000] bttv0: Bt848 (rev 17) at 0000:02:04.0, irq: 217, latency: 32, mmio: 0xec6ff000
[17185216.724000] bttv0: using: AVerMedia TVPhone [card=6,insmod option]
[17185216.728000] bttv0: gpio: en=00000000, out=00000000 in=00447fc3 [init]
[17185216.768000] tuner 0-0061: chip found @ 0xc2 (bt848 #0 [sw])
[17185216.804000] bttv0: using tuner=2
[17185216.804000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17185216.804000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17185216.804000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17185216.808000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17185216.828000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17185216.844000] bttv0: registered device video0
[17185216.844000] bttv0: registered device vbi0
[17185216.848000] input: bttv IR (card=6) as /class/input/input13
[17185216.848000] bttv-input: bttv IR (card=6) detected at pci-0000:02:04.0/ir0

What's next? ](*,) 

Thank you for your time,

highmighty

---

### Post by tuke81 on 2007-04-03
> **highmighty said:**
> 
...
Also, still no **snd_bt87x** under **lsmod | grep snd**... but does this sound driver refers to the bt878 chipset only (mine is a bt8**4**8 )?

Here are the chipsets found on the card: Bt848KPF and FR1236

Here is the output of **dmesg** after modprobing bttv to **card=6** and **tuner=2**:

[17185216.684000] bttv: driver version 0.9.16 loaded
[17185216.684000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17185216.684000] bttv: Bt8xx card found (0).
[17185216.684000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 17 (level, low) -> IRQ 217
[17185216.684000] bttv0: Bt848 (rev 17) at 0000:02:04.0, irq: 217, latency: 32, mmio: 0xec6ff000
[17185216.724000] bttv0: using: AVerMedia TVPhone [card=6,insmod option]
[17185216.728000] bttv0: gpio: en=00000000, out=00000000 in=00447fc3 [init]
[17185216.768000] tuner 0-0061: chip found @ 0xc2 (bt848 #0 [sw])
[17185216.804000] bttv0: using tuner=2
[17185216.804000] tuner 0-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[17185216.804000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17185216.804000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17185216.808000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17185216.828000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17185216.844000] bttv0: registered device video0
[17185216.844000] bttv0: registered device vbi0
[17185216.848000] input: bttv IR (card=6) as /class/input/input13
[17185216.848000] bttv-input: bttv IR (card=6) detected at pci-0000:02:04.0/ir0
...


Ok you can forget that snd_bt87x, as there is no such chip on your card. Card=6 looks indeed a right card according to your dmesg output. I'm not sure what is the part that handless audio capture in that card, but maybe it's module btaudio that you have to modprobe next so try it: **sudo modprobe btaudio** and check the dmesg | tail again.

[http://tldp.org/HOWTO/BTTV/modprobe.html#SND](http://tldp.org/HOWTO/BTTV/modprobe.html#SND)
[http://tldp.org/HOWTO/BTTV/recording.html](http://tldp.org/HOWTO/BTTV/recording.html)

---

### Post by kelsos on 2007-04-03
Hello, I also have a no sound problem with tvtime, my tv card is "Chronos Video Shuttle II" the one based on the Philips saa7134. I can't really find what the problem is, cause i can get sound from the radio with Gnome Radio just fine.
--Edit--
after some playing around i found that in composite mode i can get sound (from card's line in) but it was rather low in volume and i had the speaker at he max....

---

### Post by highmighty on 2007-04-03
Dude, it works!!

I honestly don't know what I did but it finally works like a charm!  :)

I sure loaded the btaudio module and then set LINEIN volume to 100% and tadam!

I now need to automate everything at bootup, how should I do that if my specs are these?

[B]modprobe bttv card=6 tuner=2
modprobe btaudio
LINEIN playback volume set to 100%[/B]

For the LINEIN volume to be set to 100%, I tried **alsactl store** while it was at 100% but it didn't worked, whenever tvtime starts, it puts it back to 50%, any ideas?

Thanks so much again!

highmighty, [I]happy camper
[/I]
P.S. Ubuntu NOW rocks!

---

### Post by tuke81 on 2007-04-03
Glad to hear. For those modules you can safetly but them to /etc/modules file, without modprobe ofcourse. somelike this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
bttv card=6 tuner=2
btaudio

```

For that soundvolume issue might be tvtime program spesific issue also. See tvtime config files are there any settings for default soundvolume. I don't know anything about tvtime so I can't help you with that, sorry.

---

### Post by tuke81 on 2007-04-04
Just being curious: [http://www.die.net/doc/linux/man/man5/tvtime.xml.5.html](http://www.die.net/doc/linux/man/man5/tvtime.xml.5.html)
> <option name="AudioBoost" value="-1"/> 
This option sets the audio boost. This is a percentage for how much to set the volume coming out of the capture card. By default, tvtime does not set the audio at all. However, because the volume sometimes does not have a sane default, or is reset by other applications, you can use this value to have it always set to your favorite volume. Use -1 to have tvtime not touch the volume.
Maybe you can adjust volume by editing ~/.tvtime/tvtime.xml file with some xml capable text editor and add there(or modify existing):
```
<option name="AudioBoost" value="100"/>
```
Dunno, maybe just maybe this could help. :-k

---

### Post by highmighty on 2007-04-04
Thanks so much, I'll give it a try for sure!

Have a good day!

highmighty

---

### Post by highmighty on 2007-04-04
**<option name="AudioBoost" value="100"/>** doesn't work, tvtime always puts LINEIN back to 50% at startup...

Also, autoloading bttv and btaudio modules doesn't seem to work, I always need to manually **rmmod bttv** to then load my specific settings...

Here's the content of my **modules** file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
fuse
[B]bttv card=6 tuner=2
btaudio[/B]

What could be the problem?

Thank you for your time,
highmighty

---

### Post by tuke81 on 2007-04-04
Oh it's loading it automaticly in boot, I don't know very much about that what file makes it load at boot, theres should be some file in the folder /etc/modprobe.d/ which it has been loaded. But I'm totally lost while updates from hoary to edgy(there are some changes make in the boot sequence, that I don't know anything about them). 

Maybe you can blacklist it by adding **blacklist bttv** to file /etc/modprobe.d/blacklist and it might load succesfully with lines in the /etc/modules.

---

### Post by n_hendrick on 2007-04-04
hey, have you tried adjusting the volume of "analog mix" in alsamixer....I had a similar problem with tvtime and for some reason even if I had the volume up on the other options it would not recognize it in tvtime unless I had the analog mix option enabled and turned up.

---

### Post by highmighty on 2007-04-04
Everything works fine now, I blacklisted bttv and it then loaded the ones found in the **modules **file at bootup instead :)

Also, I found out that the **AudioBoost** option is only related to the built-in **tvtime** volume setting and not the audio card volume setting, which is why it had no effect on my end, the **AudioBoost** was already defaulted to 100%.

And n_hendrick, same here, I need both **Analog Mix** and **Line-in** enabled and set to 100% in order for tvtime to work properly.

True happy camper now :)

Thanks all,

highmighty

---


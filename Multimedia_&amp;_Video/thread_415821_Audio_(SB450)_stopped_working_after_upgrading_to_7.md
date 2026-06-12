---
title: "Audio (SB450) stopped working after upgrading to 7.04"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by julian.coccia on 2007-04-20
Hi there!

I have just upgraded my Samsung R40 laptop to 7.04 and everything went fine except for the audio. The audio was autodetected and always worked fine under 6.10 but now it doesn't work.

According to lspci:
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

However, this seems to be a full Intel system (I've read somewhere it's actually an Intel-HDA chipset), so I'm not sure which driver is supposed to load (I wish I would have done an lspci before upgrading)

I have nothing in my dmesg, and the loaded modules are listed below. 

If anyone knows what is going on, I would appreciate your help.

Regards,
Julian

lsmod | grep snd
snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

---

### Post by opacha on 2007-04-20
Same problem here. I've tried everything including upgrading to the ALSA beta drivers which for some reason caused update manager to stop working.
 lspci
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

lsmod|grep snd

snd_hda_intel          22552  1 
snd_hda_codec         213376  1 snd_hda_intel
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56324  13 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm



Thanks in advance,
Omar

---

### Post by djails on 2007-04-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Same problem here, I own a Toshiba A100 with a ATI SB450 sound chipset:
```
lspc -nnv
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

The sound used to work in edgy (alsa 1.0.12rc1, kernel 2.6.17-11) but it doesnt in feisty (alsa 1.0.14rc1, kernel 2.6.20-15). Alsamixer only shows controls for the modem (off-hook and caller-id) and nothing more (no PCM,  mic, the usual sound card stuff):

```
amixer
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

```

I also tried to install alsa-driver-1.0.14rc manually with a small improvement: the mixer shows the normal sound card senses but there is still no sound out of those speakers.

---

### Post by opacha on 2007-04-21
Thanks djails,
But my alsamixer shows everything as it should. PCM, Master, and the caller id etc stuff. I've tried every combination of mute and unmute, headphones, nothing is working here. I think I have a different problem.
-Omar

---

### Post by Ianman on 2007-04-21
Yep I have the same problem. Got an Audigy sound card that worked fine in 6.10 but now with FF it doesn't work at all. Seems to be detected just fine but just can't here anything. If I use lspci -v I see this:
01:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
        Subsystem: Creative Labs SB0090 Audigy Player/OEM
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at c400 [size=32]
        Capabilities: <access denied>
Is there any other information we can compare?

---

### Post by shironeko on 2007-04-21
Same problem here. After upgrading the sound stopped working.

It worked perfectly in Edgy and does work in the Live (beta) CD.

---

### Post by opacha on 2007-04-21
Do you mean sound works with the edgy live CD? Because my sound doesn't work with the Feisty live CD, nor with full installation. Generally feisty seems a bit buggier than usual. I feel like even Dapper was quite more stable than this. I'm also having to restart on occasion because that x-server whatever desktop thingy comes up and asks me if i want to debug. Shutdown sometimes hangs too, and for some reason sometimes application launchers I add to the panel disappear after startup. I hope there are some good updates soon.
-Omar

---

### Post by julian.coccia on 2007-04-21
More info:

Sound works with Live CD 6.10, but it doesn't with Live CD 7.04.

Also, from 6.10 lspci reports:
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)

While 7.04 reports:
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

In addition, I see quite a few more modules loaded in 7.04 than in 6.10:

Ubuntu 6.10 automatically loads:
```
ubuntu@ubuntu:~$ lsmod | grep snd
snd_hda_intel          20116  1 
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm

```

While 7.04 loads:
```
snd_hda_intel          21912  0 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
```

I hope this helps...

Regards,
Julian

---

### Post by opacha on 2007-04-21
Julian,
I'm pretty new to Ubuntu and linux being in and out since dapper, but here's a crazy idea that might work. Copy your alsa-base file and blacklist file when you load the edgy live cd to the directory for Feisty. See if that corrects it. If so, I'm going to have to burn an edgy cd or get a copy of them from you. Oh, it's probably a good idea to keep copies of the originals to switch back if it doesn't work. Let me know if it works asap, I'd like to try with the edgy cd too.
-Omar

---

### Post by kadallas on 2007-04-21
I have a toshiba a105 s1013 laptop and I have had the same experience.  I had sound in dapper and edgy, but no sound in feisty fawn.  I go through the sound debugging instructions I found in ubuntu documentation and everything seems to be fine, but I have no sound.  Perhaps I don't understand the output of the various commands in the instructions.   It does seem that my sound card is detected and the right kernel module is installed, but the alsa mixer seems to have problems.:( 

KAD

---

### Post by shironeko on 2007-04-22
> **opacha said:**
> Do you mean sound works with the edgy live CD? Because my sound doesn't work with the Feisty live CD, nor with full installation. Generally feisty seems a bit buggier than usual. I feel like even Dapper was quite more stable than this. I'm also having to restart on occasion because that x-server whatever desktop thingy comes up and asks me if i want to debug. Shutdown sometimes hangs too, and for some reason sometimes application launchers I add to the panel disappear after startup. I hope there are some good updates soon.
-Omar

Sound worked on my laptop with Feisty Live CD, but not after the installation...
I've got no clue...

I think that maybe Feisty requieres a newer version of alsa or alsamixer...
Let's hope we can find an answer soon. I just installed Ubuntu on my mother's laptop, and If she doesn't get sound soon she'll probably switch back to windows X_x
I shouldn't have updated her laptop... everything worked fine on Edgy,,,,

---

### Post by nomeat on 2007-04-22
Same here with audigy and I installed Feisty only because of Ubuntu Studio.

Everything seems to show up in the settings correctly, even with third party software.
I can choose the Audidgy midi Uart, set latency etc, but no midi in and no sound out !
Dapper worked just fine. Never really had to bother about the sound drivers and I thought in Feisty
everything would be better and simpler for the humble user :(

I am glad to see here that others share the same problem with me.
It is just strange that nobdy noticed anything in the beta versions.

---

### Post by Mike Balsom on 2007-04-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'll add my comments here as I have the same problem.

I think it must be something in the kernel, as julian found [Here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/103379") there is a known bug with the ATI SB450 on-board sound chip.

I have found a sort of work around though.

I installed feisty through the update manager prompt, so I'm not sure how many people this will apply to.

When I reboot, I still have options for the previous kernel releases available on my grub menu, selecting to boot with my previous kernel 2.6.17-10, and the system comes up and sound works fine.

alsa-info output from the two different kernel loads attached, for anyone who it will help:

[ATTACH]30433[/ATTACH]

[ATTACH]30434[/ATTACH]

Mike

---

### Post by peter07 on 2007-04-22
Same problem here :(

EDIT:

Have somebody tried the newest ALSA??

---

### Post by karhulitos on 2007-04-22
> **peter07 said:**
> Same problem here :(

EDIT:

Have somebody tried the newest ALSA??

Same here, I've tried Alsa 1.0.14 rc3 and no help. I've tried all suggested here in the forum regarding hda-intel and no help.. :( Enjoying the silence

---

### Post by opacha on 2007-04-22
Tried the newest alsa, sound DOESNT work with the edgy livecd, I think maybe the kernel fix is the only option-- and I dont know how to do that.
-Omar

---

### Post by taural.cw on 2007-04-22
Have the self-same problem with the Samsung R40 and sound drivers.

Have tried every fix I could find on the forum but still basking in silence. Volume control wont even detect the PCM slider and testing the sound output plunges the window into obscurity.

As with almost everyone else the problem was not there with Edgy so I'm confused as to how it has been allowed to occur in Feisty.

If I get any further with it I'll let you all know.

](*,)

---

### Post by julian.coccia on 2007-04-23
Booting with the previous kernel works fine, as long as you haven't tried the alsa update. In that case, run make uninstall for alsa-drivers and then mark all alsa packages for "reinstall" in Synaptic. Apply, reboot, select the previous kernel and done.

---

### Post by karhulitos on 2007-04-23
I don't know if my problem is a duplicate but made a bug of my own. At least I guess they'll close mine if it's duplicate.

[https://bugs.launchpad.net/ubuntu/+bug/109236]("https://bugs.launchpad.net/ubuntu/+bug/109236")

---

### Post by djails on 2007-04-23
To all of you with a ATI SB450 sound problem in feisty:
If your sound card is an ATI SB450 in a toshiba laptop like mine which used to work in edgy but not in feisty anymore, here is the solution given to me on the alsa-devel ML:
```

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

```
It worked for me. The probe_mask param allows the correct discovery of the sound codec, which otherwise is masked by the modem.
if it does the job for you, make it permanent by adding "options snd-hda-intel probe_mask=8 model=auto" at the end of /etc/modprobe.d/alsa-base
Let me know if it works for you.

For reference:
```

lspci -nnv -s 00:14.2
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by lazyrussian on 2007-04-23
I get the following message when i type in the rmmod command.

```

ERROR: Module snd_hda_intel is in use

```

---

### Post by dustman on 2007-04-23
> **djails said:**
> To all of you with a ATI SB450 sound problem in feisty:
If your sound card is an ATI SB450 in a toshiba laptop like mine which used to work in edgy but not in feisty anymore, here is the solution given to me on the alsa-devel ML:
```

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

```
It worked for me. The probe_mask param allows the correct discovery of the sound codec, which otherwise is masked by the modem.
if it does the job for you, make it permanent by adding "options snd-hda-intel probe_mask=8 model=auto" at the end of /etc/modprobe.d/alsa-base
Let me know if it works for you.

For reference:
```

lspci -nnv -s 00:14.2
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

geez man....you're a genius :D....got it working in no time....now I can listen to my Sasha and Digweed as much as I want :)) Thanks....owe u one ;)



Cheers!

Radu

---

### Post by tomazela on 2007-04-23
it worked for me too!
thanks!

---

### Post by dustman on 2007-04-23
> **lazyrussian said:**
> I get the following message when i type in the rmmod command.

```

ERROR: Module snd_hda_intel is in use

```

Reboot in recovery mode....:D and you will be able to make it happen

---

### Post by dustman on 2007-04-23
dunno if the sound fix did this, but now my DVD-ROM doesn't get mounted....and before I fixed the sound, it did....so....another bug? :|

---

### Post by lazyrussian on 2007-04-23
heh sorry for being noobish, but how do I boot in recovery?

---

### Post by lazyrussian on 2007-04-23
nvm! I figured it out and IT WORKED!!!!!!!!!!!!!!!!!!!!!!!!!!!! haha finalyl after 5 days with no sound it works :)

---

### Post by Mike Balsom on 2007-04-23
I'll add another affirmative to that solution
Nice work djails

Thanks

Mike

---

### Post by peter07 on 2007-04-23
> **djails said:**
> To all of you with a ATI SB450 sound problem in feisty:
If your sound card is an ATI SB450 in a toshiba laptop like mine which used to work in edgy but not in feisty anymore, here is the solution given to me on the alsa-devel ML:
```

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

```
It worked for me. The probe_mask param allows the correct discovery of the sound codec, which otherwise is masked by the modem.
if it does the job for you, make it permanent by adding "options snd-hda-intel probe_mask=8 model=auto" at the end of /etc/modprobe.d/alsa-base
Let me know if it works for you.

For reference:
```

lspci -nnv -s 00:14.2
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

This doesn't work for me :(

After that:
example aplay:
```
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
aplay: main:550: b&#322;&#261;d otwierania audio: No such file or directory
```

tail -2 /proc/asound/oss/sndstat
```
Mixers:
0: Generic ffff ID ffff
```

dmesg:
```
...
[ 26.512000] hda_codec: invalid dep_range_val 0:7fff
[ 26.512000] hda_codec: invalid dep_range_val 0:7fff
[ 26.512000] hda_codec: invalid dep_range_val 0:7fff
... (many times)
```

My card: 
```
lspci -nnv | grep SB450
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
```

Help

---

### Post by Anaea on 2007-04-23
> **djails said:**
> To all of you with a ATI SB450 sound problem in feisty:
If your sound card is an ATI SB450 in a toshiba laptop like mine which used to work in edgy but not in feisty anymore, here is the solution given to me on the alsa-devel ML:
```

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

```
It worked for me. The probe_mask param allows the correct discovery of the sound codec, which otherwise is masked by the modem.
if it does the job for you, make it permanent by adding "options snd-hda-intel probe_mask=8 model=auto" at the end of /etc/modprobe.d/alsa-base
Let me know if it works for you.

For reference:
```

lspci -nnv -s 00:14.2
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

Almost fixed it for me.  I'm not getting sound errors, my volume switch is actually responding, and alsamixer is looking like it ought to, but I'm not getting any actual sound either out of my speakers or through my headphone jack.  I'm going to run through the sound troubleshooter one more time to see if this changes things for me at all.  Anybody have any better ideas?

Just for reference:
```
@Marduk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

lspci -v
```
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device ff00
        Flags: bus master, slow devsel, latency 64, IRQ 19
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```

dmesg:
```
[   40.076000] hda-intel: Invalid position buffer, using LPIB read method instead.
```

My user account has permissions to access sound resources, and when I test the sound settings under administration>preferences>sound the test box opens up, the progress bar stops about a quarter of the way through, but no sound and the test never finishes.

---

### Post by Uranium235 on 2007-04-23
Ok that's the exact same thing that's going on with me Anea.  I have tried all of the posted solutions and I'm getting nowhere.  I'm just about ready to install 6.10. :/

---

### Post by Anaea on 2007-04-23
I've got it.  djails was mostly right, I just had to tweak one little thing.  
```

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
```

and then in /etc/modprobe.d/alsa-base
```

options snd-hda-intel probe_mask=8 model=3stack
```

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*]  spot too.  

Good luck, and thanks to everybody for helping out on this.  I was about to give up and start building kernels.

---

### Post by Uranium235 on 2007-04-23
Well I tried that as well, and now absolutely nothing happens.  When I try to test the audio it simply locks up.  I'm getting closer and closer to going to 6.10. :/

---

### Post by peter07 on 2007-04-24
> **Anaea said:**
> I've got it.  djails was mostly right, I just had to tweak one little thing.  
```

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
```

and then in /etc/modprobe.d/alsa-base
```

options snd-hda-intel probe_mask=8 model=3stack
```

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*]  spot too.  

Good luck, and thanks to everybody for helping out on this.  I was about to give up and start building kernels.

This doesn't work to :( The same errors...

---

### Post by Mamong on 2007-04-24
I had Xubuntu 6.10. Sound was fine. Went to Ubuntu 6.10 briefly, sound worked. Upgraded through Ubuntu to Feisty Fawn, I've lost my sound. Running a Toshiba Satellite A100 with the ATI SB450 sound card. Ubuntu picks it up and whenever I play something, no sound. If I try to playback a sound it says "Couldn't connect to Sound Server" (That is offline). I've tried heaps of different formulas, including those in these threads, NOTHING has worked.

Please help me. I'm only a newbie to Linux and don't understand all the code but I am eager to get this sound working.

---

### Post by karhulitos on 2007-04-24
I mentioned I'll do a bug report of this to see if they accept it. Now it's in confirmed status so I guess best is to wait for the fix in kernel. None of the workarounds helped me so far. Acer Aspire 5044WLMi is my case here.

I was 99% sure the Toshiba bug mentioned earlier in this thread was exactly same as mine, but for my great surprise they accepted mine as separate bug.

Do all different PC model owners now need to file bug reports?

---

### Post by toddowen on 2007-04-24
The code below finally fixed the sound on my daughter's Toshiba A135-S2276 laptop.

Thanks, djails and Anaea.

--Todd

> **Anaea said:**
> I've got it.  djails was mostly right, I just had to tweak one little thing.  
```

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
```

and then in /etc/modprobe.d/alsa-base
```

options snd-hda-intel probe_mask=8 model=3stack
```

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*]  spot too.  

Good luck, and thanks to everybody for helping out on this.  I was about to give up and start building kernels.

---

### Post by Uranium235 on 2007-04-24
I actually had a friend of mine connect to my PC and fix it (mostly, I still have no front jack output) He said he's going to write down exactly what he did to get it working, then I will post it here.

---

### Post by peter07 on 2007-04-25
I'm waiting for you're solution. I have still no sound :(

---

### Post by Mamong on 2007-04-25
> **peter07 said:**
> I'm waiting for you're solution. I have still no sound :(

Neither do I, it's getting frustrating! :(

---

### Post by Uranium235 on 2007-04-25
Well he's on a completely different time frame being halfway across the globe, so I'm waiting on him right now, but I do know that it involves a patch for the realtek chipset, and the problem lies in the fact that the alsa drivers are using the same address for the sound card AND the modem.

---

### Post by maddentim on 2007-04-26
> **Anaea said:**
> I've got it.  djails was mostly right, I just had to tweak one little thing.  
```

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
```

and then in /etc/modprobe.d/alsa-base
```

options snd-hda-intel probe_mask=8 model=3stack
```

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*]  spot too.  

Good luck, and thanks to everybody for helping out on this.  I was about to give up and start building kernels.
I got it working!  Thanks to the suggestion to use: 

sudo modprobe snd-hda-intel probe_mask=8 model=3stack

instead of 

sudo modprobe snd-hda-intel probe_mask=8 model=auto

I also did it in recovery mode straight off the grub menu as root instead of as my normal user.

I am not sure which did it the change to 3stack or the recovery mode...  Not going to mess with it now that it is working!

---

### Post by rrwo on 2007-04-26
FYI, I discovered that the audio will only work if I start up from a cold boot.  See [http://ubuntuforums.org/showthread.php?t=424354](http://ubuntuforums.org/showthread.php?t=424354)

---

### Post by Uranium235 on 2007-04-26
It involved more than just that, with my hardware.  Like I said, my friend had to patch the drivers and I believe he manually edited the driver's code.  He did all of this on a secure shell I had set up for him.  I still don't have it working through the headphone jack though, which is what I really need.

---

### Post by b4silence on 2007-04-27
> **Anaea said:**
> I've got it.  djails was mostly right, I just had to tweak one little thing.  
```

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
```

and then in /etc/modprobe.d/alsa-base
```

options snd-hda-intel probe_mask=8 model=3stack
```

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*]  spot too.  

Good luck, and thanks to everybody for helping out on this.  I was about to give up and start building kernels.

Hello!

I couldn't get it working neither djails's way nor Anaea's way...

It is done by running the commands on the recovery mode but how do you test if its working? Reboot? Any command?

Any way I added both options snd-hda-intel probe_mask=8 model=auto and options snd-hda-intel probe_mask=8 model=3stack in different occasions to alsa-base, did reboot and it hadn't solve my sound problem :S

I have an ACER Aspire 5051 WXMi and with a fresh Feisty installation I got soundo.. but only on the SPDIF output... :S

Is there anyone that has this specific problem/notebook and got the sound to work?

---

### Post by peter07 on 2007-04-27
Temporary solution for L30-134, which I found:

> At last, I have sound output on L30-134 laptop.

In my case, solution was to load snd-hda-intel with model=6stack-digout option.
Now, "front" channel controls speakers volume and "surround" channel controls phone jack. "Internal speaker" seems also working correctly.

Sound recording was not tested.

My sound chip is identified as ALC861-VD (Vendor Id: 0x10ec0862) but it has also Subsystem Id: 0x1179820d, not 0x1179ff31.
from:
**[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2821](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2821)**

Loading snd-hda-intel with model=6stack-digout option helped. Now "internal speaker" seems working correctly, but headphones jack no :confused:

---

### Post by kors on 2007-04-27
```

options snd-hda-intel probe_mask=8 model=auto

```
Solved the issue on Samsung R40. Thanks for help.

---

### Post by gualinux on 2007-04-27
Thanks a lot people, my toshiba l-35 works with snd-hda-intel model=6stack-digout, :) . The last thing its that the headphones out dont work, neither in edgy or feisty, any idea?

---

### Post by avai on 2007-04-27
I'm operating 7.04.

The first two command lines work and allow adjustment of the audio, but when I input for the directory /etc/modprobe.d/alsa-base, I receive the following message:

bash: /etc/modprobe.d/alsa-base: Permission denied

How should I proceed? I still receive no sound and have checked on its mute status.

---

### Post by cminor9 on 2007-04-28
I had this problem also, have an Audigy ZS card on a 2 year old Dell.  I took a different approach.  I went into System -> Preferences -> Sound, and on the devices tab I chose options from the select boxes and pressed Test until I found one that sounded right.  The ALSA option did not work for me,   So I chose ACD Capture /Standard PCM Playback for each option.  When I pressed Test, I heard a tone.  I left the Device set to my Audigy Card.  Well, I am listening to music now!  It sounds right, though I have not tested if the 5.1 works properly at a high volume (don't wanna wake the kiddos).  At a low volume it sounds right.

---

### Post by Anaea on 2007-04-28
> **avai said:**
> I'm operating 7.04.

The first two command lines work and allow adjustment of the audio, but when I input for the directory /etc/modprobe.d/alsa-base, I receive the following message:

bash: /etc/modprobe.d/alsa-base: Permission denied

How should I proceed? I still receive no sound and have checked on its mute status.

Did you try putting sudo in front of the command?  That will give you the option of being root for that command which should take care of the permissions.

```
sudo /etc/modprobe.d/alsa-base
```

and then when it prompts you to, put in your password.

---

### Post by peter07 on 2007-04-28
> **gualinux said:**
> Thanks a lot people, my toshiba l-35 works with snd-hda-intel model=6stack-digout, :) . The last thing its that the headphones out dont work, neither in edgy or feisty, any idea?

I have the same problem - I'm working on it :).
First of all try new version of BIOS from toshiba website.

---

### Post by Ianman on 2007-04-28
I just solved my sound issue! In my case, I opened the Alsa mixer and umuted everything as mentioned here:
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I then switched to the Switches tab and noticed an option:
Audigy Analog/Digital Output Jack

In my case it was enabled. As soon as I disabled this option sound started to work! Do any of you guys have this option? Does it make a difference?

---

### Post by peter07 on 2007-04-28
> **gualinux said:**
> Thanks a lot people, my toshiba l-35 works with snd-hda-intel model=6stack-digout, :) . The last thing its that the headphones out dont work, neither in edgy or feisty, any idea?

From alsa bugtracker:
> 
Run alsamixer, find "surround" channel, unmute (key 'M') it and increase volume until you clearly hear sound. It should work (if you have the same chip). Gnome-mixer may hide some unused mixer settings, but they are also available after turning them on in parameters.
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2821](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2821)

It works for me :)

---

### Post by salopar on 2007-04-28
my laptop is a toshiba a100 va1
with 6.10 , every time i hibernate/suspend/sleep or switch user , im loosing sound
after upgrating to 7.04 , no sound , i tried all solution above and some from other
forum , still got no sound

my lspci and dmesg , aplay is the same has above

---

### Post by Mamong on 2007-04-28
I've still got no sound. Tried a coldboot. Tried running the commands in Recovery Mode and it just says the Modules are not there. Tried unmuting in alsamixer, makes no difference. Rhythmbox doesn't play and MoviePlayer just says "Cannot connect to Sound Server". 

I'd really like some help. I read and followed the Ubuntu guide to Debugging Sound Problems to no avail. I'm starting to get desperate, even Beryl is working! Please someone help. :mad:

---

### Post by Uranium235 on 2007-04-29
Well I have sound out of the PC speakers, but no front output, and I know why.  The alsa drivers have the front/pcm outputs mixed up.  Unfortunately I do not know how to fix this.

---

### Post by avai on 2007-04-29
I receive the following response from inputting **sudo /etc/modprobe.d/alsa-base**:

sudo: /etc/modprobe.d/alsa-base: command not found

---

### Post by Anaea on 2007-04-29
Try
```

sudo gedit /etc/modprobe.d/alsa-base: command not found
```

---

### Post by marcov64 on 2007-04-30
> **Ianman said:**
> 
I then switched to the Switches tab and noticed an option:
Audigy Analog/Digital Output Jack

In my case it was enabled. As soon as I disabled this option sound started to work! Do any of you guys have this option? Does it make a difference?

Yes. It made the difference for me.
Now it work.
Thanks

---

### Post by Anessen on 2007-05-03
I have a new Toshiba L30-10Y Laptop with a Realtek ALC861VD chipset (according to alsamixer). I have tried the previous fixes:

```
snd-hda-intel probe_mask=8 model=auto
snd-hda-intel probe_mask=8 model=3stack
snd-hda-intel probe_mask=8 model=6stack-digout
```

All that happens, is that I lose what options I do have in my volume controls, and I am left with a single PCM volume control that does nothing. In alsamixer, the sound chipset is then listed as Generic. Also, after making any of the above changes, I also get the message 
```
hda_intel: azx_get_response timeout, switching to single_cmd mode
``` during startup, and a ton of errors to do with hda-intel in a row when using those.

No sound from either speakers or headphone port using the default drivers. Speakers work in Vista Basic (came with the laptop).

I get options to do with the modem in my volume settings, so should I try something else in the "model" parameter?

---

### Post by Anessen on 2007-05-04
OK, I downgraded to 6.10 just to get my sound to work. Is this being looked into?

---

### Post by Anessen on 2007-05-04
I apologise for the triple post, but this is worth bumping the thread for:

I found the following on the bug report

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88570)

> I think I solved my problem with sound by installing an unpatched kernel from [http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/)
see:
 [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)
cheers

This has solved my problem on my Toshiba L30-10Y laptop. The internal speakers are tied to the Front channel, and the headphone port is tied to the Surround channel. Both of them are working at proper volume. I recommend just hiding the unused controls.

---

### Post by gualinux on 2007-05-04
I solve the problem of my exta-speakers (the sound out headphone jack) in this way:
Select the control volume, of the menu bar 
Open preferences 
A window opens  with : Select the device and track to control
 You have to try the with the HDA ATI SB (Alsa mixer) all the options, because, for me the Surround option is the one that drive the headphones-external speakers

  I think that the trick is to find out what is the sound "class" that you want to manage.

MY LAPTOP IS A TOSHIBA SATELLITE L-35

Hope work for someone else.

---

### Post by thorei on 2007-05-08
Hi, all this solutions don't work for me. I bought a new laptop with a ATI SB450 soundchip and installed Feisty on it. I had no sound, so I searched the forums and found this thread. 
I tried the ubuntu 6.10 Live CD as well as kubuntu 6.06 Live CD and I have no sound with them as well. But my soundcard works, I have sound on Vista that came with it.
Then I got the newest alsa drivers and installed them, no change as well.
I can't use the hack that worked for a lot of people. Here's what I get:

[HTML]user@medion:~$ sudo rmmod snd-hda-intel
user@medion:~$ sudo modprobe snd-hda-intel probe_mask=8 model=auto
user@medion:~$ aplay '/home/user/Desktop/test.wav' 
ALSA lib confmisc.c:769:(parse_card) cannot find card ''
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:545: audio open error: No such device
user@medion:~$ sudo rmmod snd-hda-intel
user@medion:~$ sudo modprobe snd-hda-intel probe_mask=1 model=auto
user@medion:~$ aplay '/home/user/Desktop/test.wav' 
Playing WAVE '/home/user/Desktop/test.wav' : Unsigned 8 bit, Rate 22050 Hz, Mono[/HTML]

(playing but no sound)

I tried basically all options. For me, the model= option makes no difference. I can put in whatever I want. More interesting is the probe_mask option. Apparently, it tells the driver which codec to choose. I found out, that if I put in straight numbers (2,4,6 or 8 ) he doesn't find my soundcard any more (see output). If I put in unstraight numbers like 1,3 etc. everything seems to work fine, the soundcard is detected and I can play songs, however there's still no sound coming out of the speakers. There's another option: position_fix=x (x being the number entered in probe_mask=) which should tell the driver only to use that specific codec, but i tried all out and still no sound. If I leave all the options out and load the module just like that it detects the card as well but no sound.
In alsamixer everything is on 100, I spent almost 15 hours on this problem now and I'm desperate. i don't want to work with a system with no sound. I'm thinking about trying fedora or sth like that. I don't know what else I can try. i'm not an expert in linux and my knowledge is finished at this point.

Thanks four your help

---

### Post by Uranium235 on 2007-05-08
I have also tried everything imaginable to fix this, and I get no joy.  I'm a musician and I really need to use sound and front output really.  PCM speakers just won't get the job done for me.  So bumping this up and asking if anyone's got a SURE fix to this for my hardware.  Toshiba L35S-1054, ATI SB450.

---

### Post by Pietr The Engineer on 2007-05-08
I have a slightly different audio problem.
I can't get feisty Rhythmbox to work with my old Mp3 library(w2000pro/Realplayer MP3 across the network).
Edgy worked fine once the codecs were installed.
Oddly, Rhythmbox still works fine with Ogg files via SoundJuicer, but crashes on MP3.
Is there a copyright protection in the new system?
Incidentally, as soon as the Upgrade to 7.04 appeared(arounmd midnight on day before) I lost all sound in Edgy.
To fix it I went to an analogue driver(I am using legacy hardware, an Optiplex GX115 with on-board sound and video)and hit all the mute buttons OFF.:confused:

---

### Post by karhulitos on 2007-05-16
I wanted to come back to tell that latest Alsa alsa-driver-1.0.14rc4 fixed my sound problem on Acer Aspire 5044WLMi with Feisty.

I did this:

```
sudo apt-get install build-essential ncurses-dev gettext
```

```
sudo apt-get install linux-headers-`uname -r`
```

```
cd ~ 
mkdir alsa-src
cd alsa-src
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc4.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14rc4.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14rc4.tar.bz2
```

```
sudo /etc/init.d/alsa-utils stop 

tar xvf alsa-driver-1.0.14rc4.tar.bz2
tar xvf alsa-lib-1.0.14rc4.tar.bz2
tar xvf alsa-utils-1.0.14rc4.tar.bz2
```

```
cd alsa-driver-1.0.14rc4 
./configure --with-cards=hda-intel
make
sudo make install

cd ../alsa-lib-1.0.14rc4
./configure
sudo make install

cd ../alsa-utils-1.0.14rc4
./configure
sudo make install
```

Reboot.

Sound.

---

### Post by stchman on 2007-05-16
> **Anaea said:**
> I've got it.  djails was mostly right, I just had to tweak one little thing.  
```

 sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
```

and then in /etc/modprobe.d/alsa-base
```

options snd-hda-intel probe_mask=8 model=3stack
```

From poking on the forums it looks like other people have had success using toshiba, or test in the model=[*]  spot too.  

Good luck, and thanks to everybody for helping out on this.  I was about to give up and start building kernels.

Thanks a bunch.  THe 3stack in the alsa-base file WORKED.  You rock!!!!!!  I have a Toshiba laptop A135-S2246 with the SB450 audio card.  Did you also figure out how to turn off the laptop speakers while using headphones as the speakers still play when I put headphones in?

Thanks.

---

### Post by Anaea on 2007-05-16
Nope, I'm still having that problem, but I haven't tried much with it either.  I'll let you know if I run across something.

---

### Post by stchman on 2007-05-16
> **Anaea said:**
> Nope, I'm still having that problem, but I haven't tried much with it either.  I'll let you know if I run across something.

Thanks, the headphone thing can be annoying.  There is a checkbox marked Headpones so I figure there should be a checkbox marked Speakers.

Thanks again.

---

### Post by Uranium235 on 2007-05-16
I installed the new Alsa Drivers and I am still getting no sound.  Starting to get a bit frustrating. :/

---

### Post by Serjudo on 2007-05-17
my solution:

1. Edit /boot/grub/menu.lst
2. Add this option to the adequate entry: acpi=ht
3. Reboot

My sound card is the alc861 vd and works ok!!

good luck!

---

### Post by cweth on 2007-05-23
i have the Toshiba a100 and was wondering if someone was able to find a solution. none of these other solutions work for me.

---

### Post by kwame on 2007-05-26
Apologies if this is a bit off-topic. Followed the instructions and I've got my sound working now but there is lots of distortion and 'crackling' unless I set the volume low.  Did not have this issue with Edgy. Any advice?

Using a Satellite A135 A2266
Soundcard info from lspci -v:
```
00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff00]
        Flags: bus master, slow devsel, latency 64, IRQ 18
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

---

### Post by ed67 on 2007-05-26
I'm following this thread closely because I have the same problem, no sound on my Toshiba laptop.

We're getting closer, the suggestions above removed the "x" from my volume control, but I still have no sound.

PCM is the only option when I double click the volume icon.  I'm feeling some modem issues because it lets me check caller id and off-hook.  But this just doesn't seem right.  Why is there modem stuff here?  It's not a modem it's a sound card.

One question:  when I boot in recovery mode, I eventually just get the command line, is that right?  So I type in the commands (sudo rmmod snd-hda-intel and then sudo modprobe snd-hda-intel probe_mask=8 model=auto or 3stack makes no diff).  Then what do I do?  I reboot to load the gui, is that right?  Are my changes I typed in still active?  Doesn't seem like they would be.........

Thanks

---

### Post by cweth on 2007-05-27
i believe you're supposed to test the sound from the command line in recovery mode. what i did was i put a wav file and called it test.wav in the home directory. then after i put in:

sudo modprobe snd-hda-intel probe_mask=8 model=auto

then i open up alsamixer, and turn all the volumes up high, and then I typed:

aplay test.wav

and then it pretends to play my sound file, but produces no sound. :-/

---

### Post by chenel on 2007-05-29
> **Ianman said:**
> I just solved my sound issue! In my case, I opened the Alsa mixer and umuted everything as mentioned here:
[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

I then switched to the Switches tab and noticed an option:
Audigy Analog/Digital Output Jack

In my case it was enabled. As soon as I disabled this option sound started to work! Do any of you guys have this option? Does it make a difference?

Did it for me!  Nice catch!

---

### Post by SuperSam on 2007-05-30
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: DFI Inc Unknown device 3110
        Flags: slow devsel, IRQ 16
        Memory at fe024000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

That's what I get when I type lspci -v I've tried at least 10 different methods to get my sound working and still no luck, any ideas?

P.S:

When I double click on the speaker in the top right corner (which is muted) I get the error

```

No volume control GStreamer plugins and/or devices found

```

---

### Post by kuripot on 2007-06-03
This fix worked for me:

[http://ubuntuforums.org/showthread.php?p=2710147](http://ubuntuforums.org/showthread.php?p=2710147)

on a Toshiba Satellite A135 s2386

---

### Post by peter07 on 2007-06-17
> **peter07 said:**
> From alsa bugtracker:

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2821](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2821)

It works for me :)

After kernel update (from ubuntu updates) - headphone jack doesn't work again :/

---

### Post by johntkucz on 2007-06-21
> **dustman said:**
> geez man....you're a genius :D....got it working in no time....now I can listen to my Sasha and Digweed as much as I want :)) Thanks....owe u one ;)



Cheers!

Radu

I have a mx3701 gateway with the same ATI stac9200 chip; methinks it's confusing the modem with the soundcard but can't rearrange that.

Hi when I tried 

sudo rmmod snd-hda-intel

I got, device is in use

but 
sudo modprobe snd-hda-intel probe_mask=8 model=auto
processed, but with no avail.

---

### Post by superhaus on 2007-06-21
I am going to try this tonight on my laptop.

---

### Post by peter07 on 2007-06-21
I've tried model=toshiba and it was a good choice (everything was working), but after switching off my computer all my problems came back. I didn't change anything in configuration, but again no sound from headphones jack :/

---

### Post by srilyk on 2007-07-17
Okay, I can't remember what Gateway model I have, but I have this
> 00:14.2 Audio device [0403]: ATI Technologies Inc SB450 HDA Audio [1002:437b] (rev 01)
        Subsystem: ATI Technologies Inc SB450 HDA Audio [1002:437b]
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


Anyway, I tried all of the things mentioned here - tried uninstalling/installing a lot of stuff, nothing worked, but I was able to install alsa version 1.0.14, restarted my lappy, and now it works!

This is what I did... 
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
tar -xjf alsa-driver-1.0.14rc3.tar.bz2
cd alsa-driver-1.0.14rc3
./configure
make
sudo make install
```

Then I did a full reboot, started up and SOUND! wooo!

Oh and I'm running Feisty Fawn 7.04...

Hope this helps!

---

### Post by sunken on 2007-07-18
> **srilyk said:**
> Okay, I can't remember what Gateway model I have, but I have this


Anyway, I tried all of the things mentioned here - tried uninstalling/installing a lot of stuff, nothing worked, but I was able to install alsa version 1.0.14, restarted my lappy, and now it works!

This is what I did... 
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14rc3.tar.bz2
tar -xjf alsa-driver-1.0.14rc3.tar.bz2
cd alsa-driver-1.0.14rc3
./configure
make
sudo make install
```

Then I did a full reboot, started up and SOUND! wooo!

Oh and I'm running Feisty Fawn 7.04...

Hope this helps!

I have a noname laptop with ATI Technologies Inc SB450 HDA Audio.
All I did was:
1. sudo pico /etc/modprobe.d/alsa-base
2. added to the end of file: options snd-hda-intel model=3stack
3. reboot

---

### Post by mdougher on 2007-07-18
Thanks, I got my sound working.

FYI: Ubuntu updrade from 6.10 to 7.04 stopped sound from working.  I got it working via this thread by the following:

ps -ef   egrep -i  "snd|sound|volu|aud"

I killed the volume tool and then

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel model=6stack-digout

sudo alsa mixer
      Tab to select All
      Unmute several items that were not there before including Surround.

Matt D.

---

### Post by nduper on 2007-09-01
Hallo everybody,
I have a Toshiba L30-10T and I am going mad trying to make work my audio as all of you around here . I tried many different distros and now I am trying Ubuntu studio.
This is the way (VERY WEIRD) how my audio works (both front and phones):
add "options snd-hda-intel probe_mask=8 model=3stack" in /etc/modprobe.d/alsa-base
reboot
with this option I have only PCM audio control
open again alsa-base
comment or cancel "options snd-hda-intel probe_mask=8 model=3stack"
turn off the computer
boot... and there it is: front audio works, headphones are controlled by surround sliders and front audio is off when minijack is inserted.
WHAT CAN I SAY? SILLY!
Andybody has an idea what is going on?

I forgot to say, maybe it was not clear, I have to do this operation every time I turn on the computer , if I want to have the audio working. If not I have only front right audio and the headphones become the computer loudspeaker (the beep one ).
I hope that this experience will be useful to somebody with more knowledge to fix this so annoying problem with SB450.

This is my lspci:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge

00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)

00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)

09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

---

### Post by nduper on 2007-09-01
This is my alsa-base (if it helps):

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
# Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
# non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
#options snd-hda-intel probe_mask=8 model=3stack

---

### Post by nduper on 2007-09-01
Ok, I've solved this problem by adding these to alsa-base:
options snd-hda-intel model=toshiba probe_mask=1
options snd_hda_intel model=uniwill-m31

Looking for the solution for the "[ 25.792704] hda_codec: invalid dep_range_val 0:7fff" I found one spanish forum where the expert was saying to add these two options. I did it and now I dont have this message (dmesg) (hda_codec: invalid dep_range) and my audio works ok.
To be honest it is not perfect because I have surround audio options and this is not the hw I have on my laptop (Toshiba L30-10T) but anyway I am happy :).
I hope this will help other people

---

### Post by LinkCloud on 2007-09-15
**Using Acer Ferrari 5006:**

This is the fix I use for SB450, I hope I made it newbie proof.

Open a terminal and paste the following.
```
gedit alsa_setup.sh
```

Copy and paste this script into that file, save it, and close it.
alsa_setup.sh
```
#!/bin/sh

# This script will recompile the ALSA drivers for Ubuntu
# This procedure was gotten from
# https://help.ubuntu.com/community/HdaIntelSoundHowto
#
# Authored by Bob Nelson  admin@stchman.com
#
# Edited by LinkCloud  linkcloud@hotmail.com
#
# This script updated 9/15/2007


script_name="alsa_setup.sh"

# Script must run as root 
if [ $USER != "root" ]; then
	echo "You need to run this script as root."
	echo "Use 'sudo ./$script_name' then enter your password when prompted."
	exit 1
fi

# Install the required tools
sudo apt-get -y install build-essential ncurses-dev

# Install your kernel headers
sudo apt-get -y install linux-headers-`uname -r`

# Change to users home folder
cd ~

# Get the files from alsa-project.org
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.14.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.14.tar.bz2

# make a new folder 
sudo mkdir -p /usr/src/alsa

# Change to that folder
cd /usr/src/alsa

# Copy the downloaded files to the newly made folder
sudo cp ~/alsa* .

# Unpack the tar archive files
sudo tar xjf alsa-driver-1.0.14.tar.bz2
sudo tar xjf alsa-lib-1.0.14.tar.bz2
sudo tar xjf alsa-utils-1.0.14.tar.bz2

#Compile and install alsa-driver
cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

# Compile and install alsa-lib
cd ../alsa-lib-1.0.14
sudo ./configure
sudo make
sudo make install

# Compile and install alsa-utils
cd ../alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

# Remove the archives as they are no longer needed
rm -r -f ~/alsa-driver-1.0.14.tar.bz2
rm -r -f ~/alsa-lib-1.0.14.tar.bz2
rm -r -f ~/alsa-utils-1.0.14.tar.bz2

# Add the following line to the file, replacing '3stack' with your model
sudo echo -e '\n' >> /etc/modprobe.d/alsa-base
sudo echo "options snd-hda-intel model=3stack" >> /etc/modprobe.d/alsa-base

# Reboot the computer
sudo reboot
```

* Place alsa_setup.sh into your home folder and run these commands
```
sudo chmod 755 ~/alsa_setup.sh
sudo sh alsa_setup.sh
sudo rmmod snd-hda-intel
```
* [If you get an error then that just means the hardware is active, proceed.]
```
sudo modprobe snd-hda-intel probe_mask=8 model=3stack
sudo gedit /etc/modprobe.d/alsa-base
```
* Add the following line at the very end of the file
* [It may already be there]
    o options snd-hda-intel model=3stack
    o save and exit
    o reboot the machine and your sound card should be working.

* To fix your volume to control your surround do the following
    o System >> Preferences >> Sound
    o Devices tab >> Default Mixer Tracks select the Device that you see visually in the upper right hand corner and ctrl click Surround.

* This should fix your sound for sb450!

---

### Post by emshains on 2007-09-15
well what should i do ???

I have an ancient 3 pentium(500mhz) with an yamaha sound card and none of this works, but i had sound  when i had  Feisty Fawn 7.02...

why the hell should i needed to update my kernel???? Oh why ??? Oh why????


well do you have any ideas to solve my noobish problem???



P.S. I am a noob with linux...

---

### Post by apparle on 2007-09-16
Hello guys I have a funny problem,
The result of *lspci* is SB400 which must be SB450. What should I do

---

### Post by wannadumpwindows on 2007-10-02
For those of you out there with this problem with Toshiba's, I had the exact same problem and tried everything I could find to my wits end. Then I found this: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2494603]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2494603")
It worked perfectly for my Toshiba A105-S2236 went through one time, did everything it said word for word. Give it a go . . . .

---

### Post by stedevil on 2008-03-06
I have fully working sound on my
Toshiba Equium L30-149 (PSL35E-002002N5) with the ATI SB450 (ACL861VD) soundchip
Some of you seem to have the same hardware, so check out this thread if things are not working for you.

[http://ubuntuforums.org/showthread.php?p=4462175#post4462175](http://ubuntuforums.org/showthread.php?p=4462175#post4462175)

---


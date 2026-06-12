---
title: "!Help! Can't get SB Live 24 bit external sound in Feisty"
date: 2007-04-06
forum: Multimedia &amp; Video
---

### Post by LordAtreus on 2007-04-06
I have the Creative lab SB Live! 24 bit external card which connects to my USB port. 
It was working fine under Edgy but I dove into Feisty and can't get the darn thing to work properly now. 

Strange thing is the unit is detected by Feisty under the sound configuration, however I get no sound from direct USB-AUDIO or ALSA. 
Also an odd thing is when I power on the computer the _blue light_ (power) on the unit comes on after grub but quickly goes off again as the rest of the loading continues. 
It never did that in edgy. 

I've googled the hell out of my problem and can't see anyone else having this issue. 
I hope someone can shed some light on what it may be.
I'm thinking it may be some kind of conflict but I get no errors in my logs
Hope someone can help out...


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lsusb -v | grep Cre
Bus 002 Device 003: ID 041e:3040 Creative Technology, Ltd 
  idVendor           0x041e Creative Technology, Ltd
  iManufacturer           1 Creative Technology

lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
container               5248  0 
asus_acpi              17308  0 
battery                10756  0 
dock                   10268  0 
video                  16388  0 
ac                      6020  0 
button                  8720  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
backlight               7040  1 asus_acpi
ipv6                  268704  10 
af_packet              23816  2 
nls_utf8                3072  3 
ntfs                  107764  3 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
fuse                   46612  0 
joydev                 10816  0 
snd_usb_audio          79744  1 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  2 snd_usb_audio,snd_pcm_oss
snd_page_alloc         10888  1 snd_pcm
snd_usb_lib            17280  1 snd_usb_audio
snd_hwdep               9988  1 snd_usb_audio
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usbhid                 26592  0 
hid                    27392  1 usbhid
soundcore               8672  1 snd
nvidia               6837140  32 
xpad                    9988  0 
agpgart                35400  1 nvidia
pcspkr                  4224  0 
i2c_nforce2             6784  0 
k8temp                  6656  0 
i2c_core               22784  3 i2c_ec,nvidia,i2c_nforce2
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  8 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sata_nv                21252  6 
pata_amd               14092  0 
ata_generic             9092  0 
libata                123032  3 sata_nv,pata_amd,ata_generic
scsi_mod              142348  4 sg,sd_mod,sr_mod,libata
floppy                 59524  0 
ehci_hcd               34188  0 
ohci_hcd               22532  0 
generic                 5124  0 [permanent]
forcedeth              46728  0 
usbcore               134280  7 snd_usb_audio,snd_usb_lib,usbhid,xpad,ehci_hcd,ohci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

---

### Post by edisman on 2007-04-17
I have the exact same issue as described above. Anyone have a solution? I have googled around for answers but can't find anything specifically for this issue.

---

### Post by Bashed on 2007-04-19
Same exact problem here

---

### Post by yurnotsoeviltwin on 2007-04-21
Me too.  Does anyone have a solution to this?  Please?

---

### Post by Bashed on 2007-04-22
Can someone please explain how to get this working with complete 5.1 functionality?

---

### Post by Bashed on 2007-04-28
ALSA mailing list claimed it was not a bug in their system, but Ubuntu which does sound likely since it did (ALSA) work in Ubuntu 6 according to many others (I did not test myself).

I'm using SB live external 24bit USB. 

>   Did you try the speaker-test like Ingo Mueller recommends?
   
  If the test sounds work but system sounds don't it cannot be an ALSA bug.
   
  Lee
  

My response:

> It detects my card, or so I assume that is what "usb audio"
  represents. I do not see actual "sb live 24bit usb" or something of that sort otherwise. Plus, strange that others suddenly have this issue in Ubuntu 7 on the same card?



What I noticed is during boot up, the card's blue light goes on, then later during boot up it goes off, clearly indicating something is not right.

---

### Post by allyourzigg on 2007-04-29
I have this problem too, Generally when I do an UPgrade I expect an upgrade, not a downgrade. not that I'm not happy with most of the things the devs have done so far, but in something thats supposed to be progressing I consider this a major downgrade.

---

### Post by Bashed on 2007-04-30
I guess no one cares to help. ALSA denies it, and this community is not really helping.

---

### Post by allyourzigg on 2007-04-30
How can alsa so blatantly ignore this type of bug? It is next to impossible to use this card in any normal way without extraneous setup (that is if you would like to use it with esd or some other sound daemon ). I wish there was some way to bring this usb-audio driver problem to the attention of someone that has the power to do something about it. My system setup would be perfect if it wasn't cursed with this sound problem.

---

### Post by Bashed on 2007-05-01
Perhaps you all should email them as I did.

---

### Post by allyourzigg on 2007-05-01
I think I will, also I would think that a community as big as Ubuntu would have some kind of influence with the biggest Linux audio project in existence. Maybe some Ubuntu devs could email the alsa project and complain?

---

### Post by Bashed on 2007-05-03
Any updates or solutions?

---

### Post by akersj on 2007-05-04
I am using Ubuntu 7.04 working with the Creative 24-bit External USB Soundcard.

My work-around is as follows:

- Boot up with the soundcard attached
- Login and wait for Gnome to finish its stuff
- Unplug the soundcard
- Wait a couple seconds
- Plug it back in again

Works like a charm for me.  Granted it's not a long-term fix but I can put up with this until the powers-that-be acknowledge a bug with their drivers ...

---

### Post by Bashed on 2007-05-04
Please clarify the below if you can:

You get absolutely full 5.1 surround sound on live! 24 bit external watching dvd's, movie clips, music?

Are you using 32bit or 64bit?

What software do you use for music, dvd's, video clips?

---

### Post by Bashed on 2007-05-04
Please provide a few screenshots of your sound settings too, thanks

---

### Post by allyourzigg on 2007-05-05
Using a slightly modified /etc/asound.conf I have gotten mine working without the unplug trick, I am on Linux Square-D 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU
and the asound.conf I used is below
```
pcm.dmix51 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0666
slave {
pcm "hw:1,0"
channels 6
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
}

ctl.dmix51 {
type hw
card 0
}

pcm.stereo {
type plug
slave.pcm "dmix51"
ttable.0.0 1
ttable.1.1 1
}

pcm.!default {
type route
slave.pcm "dmix51"
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.1.4 1
ttable.0.5 1
ttable.1.5 1
}

pcm.duplicate {
type plug
slave.pcm "dmix51"
slave.channels 6
route_policy duplicate
}

```
I don't know about surround sound but this seems to work for me at the moment, and it works well. I have esound running and can hear multiple sounds at once with minimal cpu usage (.4%) everything seems to be normal so I think this works well. Problem was that the sound card reporteed hw0,0 to be the output but it is actually hw1,0 in my case even with no other sound cards.

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

### Post by akersj on 2007-05-05
Hey, I will try my best to answer your questions however I only jumped ship to Linux a couple days back so bear with me !!  I'm on a 32 bit platform.

I don't get 5.1 surround sound - the front speakers work only as far as I can tell.  I would test with a DVD for 5.1 sound but my setup is refusing to play DVD's for some reason.  The software I'm using is the Totem Media Player that comes with Ubuntu .. however sound works on Firefox or any other application for that matter.

If you let me know what screenshots you would like (newbie guide please!) I will try my best to get them.  However, I haven't changed any sound settings from the default Ubuntu install !

---

### Post by allyourzigg on 2007-05-05
akersj; you need to install the DVD codecs in order to play dvds on a freshly installled version of ubuntu check out this link for info on how to do that
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

---

### Post by akersj on 2007-05-05
Thanks for that, DVD playback works fine now !

The mystery continues with the soundcard though.  5.1 sound works in films... with the following caveats:

- All front sound comes out the rear left speaker
- Rear left comes out of the front left
- Rear right comes out of the front right
- Nothing comes from the front centre speaker
- Nothing comes from the rear right speaker

Weird considering standard sound comes out the front speakers as normal !

---

### Post by akersj on 2007-05-06
Further to my last post I have been fiddling around and managed to get the soundcard working at startup.  Well, partially anyhow...

- Sound works in GAIM and RhythmBox. But not FireFox or GNOME
- The blue light does NOT light up on the soundcard itself.
- The test sound does not work

Quite what I've done I don't know but if there's settings I can provide that will help anyone else please post and I will be happy to oblige!

---

### Post by allyourzigg on 2007-05-06
Just so you know, the way it's setup for me now, I think even the blue light works. recording is untested.

---

### Post by Bashed on 2007-05-06
> **allyourzigg said:**
> Using a slightly modified /etc/asound.conf I have gotten mine working without the unplug trick, I am on Linux Square-D 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU
and the asound.conf I used is below
```
pcm.dmix51 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0666
slave {
pcm "hw:1,0"
channels 6
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
}

ctl.dmix51 {
type hw
card 0
}

pcm.stereo {
type plug
slave.pcm "dmix51"
ttable.0.0 1
ttable.1.1 1
}

pcm.!default {
type route
slave.pcm "dmix51"
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.1.4 1
ttable.0.5 1
ttable.1.5 1
}

pcm.duplicate {
type plug
slave.pcm "dmix51"
slave.channels 6
route_policy duplicate
}

```I don't know about surround sound but this seems to work for me at the moment, and it works well. I have esound running and can hear multiple sounds at once with minimal cpu usage (.4%) everything seems to be normal so I think this works well. Problem was that the sound card reporteed hw0,0 to be the output but it is actually hw1,0 in my case even with no other sound cards.



I get 5.1 surround with your solution BUT I still have to unplug, plugin the usb after startup. It still does not automatically boot up on startup.

---

### Post by allyourzigg on 2007-05-06
oh, ok well I guess I can blame my bootup situation for that, I have to use the live cd to "boot from first hard drive " because grub never got installed right, maybe thats it? I don't know but I'm glad I could at least be of some use.
:)

---

### Post by Bashed on 2007-05-07
What about these errors?

```
ALSA lib pcm_direct.c:1477:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card

```

---

### Post by tidalwav1 on 2007-05-07
Using the modified asound.conf made my SB Live! work perfectly (granted, I'm only using the front channels, I have a 2.1 setup [not 5.1].)

---

### Post by allyourzigg on 2007-05-07
> **TalkJesus said:**
> What about these errors?

```
ALSA lib pcm_direct.c:1477:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card

```

I don't know.... but mine works great so I don't mind so much. I forgot to mention that I only use 2 channels so maybe thats it? Sorry I couldn't be more helpful.

---

### Post by akersj on 2007-05-11
I can also confirm that the modified asound.conf works near perfectly.  The only issue I get is "crunching" on high amplitude sounds.  Turning the volume down to half on all programs seems to fix this however.

Any 'proper' fixes welcome!

---

### Post by cmankiewicz on 2007-05-13
Not sure if anyone posted this yet but I believe you can avoid having to unplug/re-plug by modifying the following file:

/etc/modprobe.d/alsa-base

Line:   options snd-usb-audio index=2

Change to:    options snd-usb-audio index=0

It still does that weird thing where it finds it during boot, looses it, and finds it again but without the blue light.

I continue to have the problem where if I do a 5,1 test, I get sounds coming out of the wrong channels (e.g.  front left comes out of left rear, etc).  

Waiting for real fix.....:mad:

---

### Post by dingleberry420 on 2007-07-27
> **cmankiewicz said:**
> Not sure if anyone posted this yet but I believe you can avoid having to unplug/re-plug by modifying the following file:

/etc/modprobe.d/alsa-base

Line:   options snd-usb-audio index=2

Change to:    options snd-usb-audio index=0

It still does that weird thing where it finds it during boot, looses it, and finds it again but without the blue light.

I continue to have the problem where if I do a 5,1 test, I get sounds coming out of the wrong channels (e.g.  front left comes out of left rear, etc).  

Waiting for real fix.....:mad:

My value was a -2 but changing it to 0 still worked.  At least I have 2.1 sound now. :shrug:

---

### Post by BatsShadow on 2007-07-31
Did anyone find anything else?  I have a Lexicon Alpha USB audio device and I am having the same problem:  device lights up then turns off on boot.  If I unplug/replug it works.

The previous suggestion about changing the alsa-base file did not work for me.

---

### Post by tim71 on 2007-09-28
I have the same sound card and noticed one thing - it works even when the blue light is not on after the end of bootup sequence. But of course unplugging and reconnecting brings the light back on...

---

### Post by holiday on 2007-09-28
I have this card working - for now. I refuse to accept the latest kernel update because it's broken people's sound. 

First thing, if you have an onboard sound card, turn it off in the BIOS. When your machine starts up, look quick for how to enter the BIOS setup. It might be called Set Up on the bottom of your screen. This is the machine startup, not Ubuntu. In the BIOS setup, look for something that looks like you can turn off the onboard sound card with, and turn it off. Something about audio probably, but maybe sound. They're different. 

If your card used to work then you have the drivers. If it's never worked then search around for how to install drivers. Here's a good link that will tell you about finding drivers. 

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

You have to read down a bit.

The final fix though was to re-order the sound cards. There's a utility you can get through apt-get that will set the order of the sound cards. I don't remember the exact name and version but you can try this in a console window. There may be a Wizard you click and scroll through, but I don't have the patience, so here:

$ apt-cache search <your idea here>

And it will pop up. There may be a couple of hundred other pops, but if you grep through them, and read, you'll probably find it. 

Like you might go:

$ apt-cache search soundcard

Well, not really, but this is an example so... 

And you get too many lines to read through.

So you go again:

$ apt-cache search soundcard | grep -i order

The i means don't worry about the Capital Letters. Order is the same as order.

Or maybe "sound card": not sure. 

This will reduce the number of hits, and you'll spot one that's just what you're looking for. Maybe the first time. 

When you find it, set your default sound card to the Sound Blaster. Save it, close it, and pull it up again to make sure it's set. Some of these dialogs work a little different. I'm not saying this one does, I'm just saying it's a habit I've taken on since playing in Linux. 

I set up my system.preferences.sound to everything saying "ALSA - Adv.. etc" and set the Device to my SB Live. 

It's probably a good idea to reboot. You can try this:

$ sudo /etc/init.d/alsa-utils restart

This will restart the alsa sound system so that it reads from the config files you just changed, but the alsa restart usually doesn't work. You have to reboot. It looks like too many applications, including some system highways,  cache too many of their settings at boot. Given the speed of our computers this is an antiquated economy - but there is so much to do. Withering windows to design. 

Ah well. We either live with things not being done or we do them ourselves. This is Linux. 

But it would be great if we'd decide together that we are going to work on one thing. How many dvd players do we have, and how many have all the functionality of any dvd player packaged with any pc or notebook you buy?  

How many do we need? 

But - where's the fun of knowing that every time I click on an mp3 I know it's going to play. Explaining to guests is an exercise of our tending to erect softskills. 

I've said enough. Maybe I'll download the kernel update after all. Something to do on the weekend.

---


---
title: "Bam! No sound!"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by Culito on 2006-08-17
I've been cruising along for quite some time now in Dapper, without any sound troubles.  It's always just worked.  Then I boot up a few days ago, and I see a little red "x" next to my volume control.  Hm?  I click it, and I get this:

No volume control GStreamer plugins and/or devices found.

Wha?

I've been piddling around since then and I can't figure it out.  I've went through the comprehensive guide, without any luck.  I have onboard sound.  I checked in BIOS and it's enabled.  Dmesg is giving me some errors:

[   36.086254] AC'97 codec ready error [0xf4000]
[   37.102152] NET: Registered protocol family 17
[   37.845830] AC'97 codec ready error [0xf4000]
[   39.605407] AC'97 codec ready error [0xf4000]
[   40.038057] eth1: Media Link On 10mbps half-duplex
[   40.822933] AC'97 0 does not respond - RESET
[   40.879290] AC'97 0 access is not valid [0x0], removing mixer.
[   41.636929] AC'97 codec ready error [0xf4000]
[   43.396507] AC'97 codec ready error [0xf4000]
[   45.156084] AC'97 codec ready error [0xf4000]
[   45.753720] NET: Registered protocol family 10
[   45.754023] lo: Disabled Privacy Extensions
[   45.754395] IPv6 over IPv4 tunneling driver
[   46.359833] AC'97 0 does not respond - RESET
[   46.416218] AC'97 0 access is not valid [0x0], removing mixer.
[   47.171611] AC'97 codec ready error [0xf4000]
[   48.931184] AC'97 codec ready error [0xf4000]
[   50.690765] AC'97 codec ready error [0xf4000]
[   51.870483] AC'97 0 does not respond - RESET
[   51.926682] AC'97 0 access is not valid [0x0], removing mixer.
[   52.682290] AC'97 codec ready error [0xf4000]
[   54.441870] AC'97 codec ready error [0xf4000]
[   56.201455] AC'97 codec ready error [0xf4000]
[   56.205515] Trident4DWaveAudio: probe of 0000:00:01.4 failed with error -5

Do I have to re-install my codec?  How would I do that?

Aplay -l:
**** List of PLAYBACK Hardware Devices ****

That's all it gives me.

lspci -v:
0000:00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
        Subsystem: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator
        Flags: medium devsel, IRQ 11
        I/O ports at d800 [size=256]
        Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>
I think that's my card.  Or is it?  I've never had to look for it until now. I've even installed a fresh set of drivers using:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils.
No dice.
Anybody have any suggestions?  I'm hoping it's not a motherboard problem.

---

### Post by Culito on 2006-08-17
I an "aadebug" script.  Here's what it tells me:

ALSA Audio Debug v0.1.0 - Thu Aug 17 20:48:16 CDT 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux Culito 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux
Loaded Modules --------------------------------------------
snd_mpu401              6728  0
snd_trident            44196  0
snd_ac97_codec         93088  1 snd_trident
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_trident,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd_page_alloc         10632  2 snd_trident,snd_pcm
snd_util_mem            4608  1 snd_trident
snd_mpu401_uart         7808  2 snd_mpu401,snd_trident
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_trident,snd_rawmidi
snd                    55268  10 snd_mpu401,snd_trident,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x300, irq 10
 33:       : timer
 40: [1- 0]: raw midi
 32: [1- 0]: ctl
cat: /proc/asound/hwdep: No such file or directory
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC1  midiC1D0  timer

CPU -------------------------------------------------------
model name      : AMD Duron(tm) Processor
cpu MHz         : 892.579

RAM -------------------------------------------------------
MemTotal:       240180 kB
SwapTotal:      698788 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
0000:00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)


So, yeah...off to do more searchin'

---

### Post by Culito on 2006-08-18
I guess nobody has any ideas, so I'm just gonna make this my "Diary of Torture".

So from the ALSA website, it says my driver is supposed to be "snd_trident", which seems to be already loaded.  In lsmod I get snd_trident, snd_ac97_codec, snd_pcm_oss, among others.

But, check it:  By a whim or complete mistake, I typed in "sudo modprobe trident", did a gnome-panel killall, and checked my dmesg.  Hey!  My volume control popped up, and look at this!

[   55.481870] Trident 4DWave/SiS 7018/ALi 5451,Tvia CyberPro 5050 PCI Audio, version 0.14.10j-2.6, 02:57:06 Aug  3 2006
[   55.483004] PCI: Found IRQ 11 for device 0000:00:01.4
[   55.483061] trident: SiS 7018 PCI Audio found at IO 0xd800, IRQ 11
[   55.690714] ac97_codec: AC97  codec, id:  (Unknown)
[   56.105068] gameport: Trident 4DWave is pci0000:00:01.4/gameport0, speed 2209kHz

That wasn't there before.  Where that leads me, I don't know, becuase my sound STILL doesn't work.  But I have a volume control now, and the only device it lists is "0: Unknown (OSS Mixer)".

---

### Post by xpod on 2006-08-18
with all the stuff you seem to be trying you seem like you know a lot more tham me but having suffered similar problems yesterday with my onboard sound i just thought i`d ask....have you checked in  SYS-PREFERNCES-MULTIMEDIA SYSTEM SELECTOR??

I messed around with the alsamixer and the rest of the settings in there to no avail then tried some of the guides on here regarding alsa and oss.

And after getting those oss packages out of synaptic and messing around with those guides i somehow got it back on......Unfortunately i cant tell you exactly what i did......Complete pc noob,But thats where i started up top.

just thought i`d wish you luck as i was in the same boat yesterday.
Sorry i cant be of any "real" help

---

### Post by Culito on 2006-08-18
Heh, I probably don't know any more than you do, but I just dive in usually end up worse than when I started.

I don't have a mulitmedia system selector under my preferences...Crap, am I supposed to!?

And thanks for the post.

---

### Post by xpod on 2006-08-18
Well it aint something i put there....come with the install.

[ATTACH]14508[/ATTACH]


I still had to do a bit more than just play with it`s settings mind you BUT yeah i reckon you should have it...

---

### Post by Culito on 2006-08-18
The plot thickens.

---

### Post by glennric on 2006-08-18
Open Applications -> Accessories -> Alacarte Menu Editor
and look under System -> Preferences.
The Multimedia Systems Selector is there, it just isn't made visible by default in Dapper.  Check it to make it so.

Edit: Or you can just run gstreamer-properties from a terminal.

---

### Post by xpod on 2006-08-18
Heres what my lspci -v says about my sound

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
        Subsystem: Giga-byte Technology GA-7VAX Onboard Audio (Realtek ALC650)
        Flags: medium devsel, IRQ 201
        I/O ports at e000 [size=256]
        Capabilities: <available only to root>


I really dont know how else i can help but if your still toiling away tommorow I`ll pop in for moral support but for now i need some sleep.
I`ve been on holiday for two weeks and i aint moved off this bloody thing.
It`ll be good to get back to work for a break....lol...good luck for now


EDIT:THERE you go...now you`ll be in buisness.....zzzzzzzzzzzzz

---

### Post by Culito on 2006-08-18
Glennric:  I'll be damned!  So I selected ALSA and 'test'....drumroll..."couldn't open resource for writing".  Reboot - no difference.  I got a few other tricks to try yet...

---

### Post by glennric on 2006-08-18
Do you have the file /etc/asound.conf?  I noticed that this doesn't appear on a fresh install of Dapper.

If not try this:
```
sudo gedit /etc/asound.conf
```

and paste in
```
pcm.card0 {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1025
slave {
pcm "hw:0,0"
period_time 0
period_size 2048
buffer_size 32768
rate 48000
}
bindings {
0 0
1 1
}
}

```

Then save and exit.

---

### Post by Culito on 2006-08-18
I didn't have an asound.conf.  I made one and rebooted.  No difference.  I thought you might have won!

The wierd thing is my driver is supposed to be 'snd-trident', right?  Well, if I remove that module, and modprobe in 'trident', the sound card is immediately recognized, at least in dmesg.  Still doesn't work, though.

My last-ditch effort is to edit grub and take out 'snd-trident' and replace it with 'trident'.  Haven't figured out how to do that yet (or if it's a good idea).

---

### Post by glennric on 2006-08-18
Hmm, you could try editting /etc/modules and adding trident to that.  Then it will load on boot.

---

### Post by Culito on 2006-08-18
Did that - it works *better*...as in the keyboard volume control works too...but it loads after the snd-trident tries to load and screws everything up.  I dunno...maybe i'm looking too deep into this...I think I'm done messing with it today-I'm gettin' fed up!

Thanks for your help.

---

### Post by glennric on 2006-08-18
One last thing then I give up for the day to.  You could add the line

```
blacklist snd_trident 
```

to /etc/modprobe.d/blacklist

---

### Post by Culito on 2006-08-18
Thanks, I'll try that...
One last thing-whenever I run gedit or anything else from terminal, when I get back, there's this:

ALSA lib pcm_hw.c:1305: (_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819: (snd_pcm_dmix_open) unable to open slave

Somethin' for ya to chew on until I return.

---

### Post by john.ennew on 2006-08-19
Just so youdon't feel you are suffering alone, I am having the same problems, my sound card stopped working this morning and I am pretty sure I did not do anything to the setup yesturday (...)

Double clicking the sound icon in the system tray I get "No Volume control GStreamer plugins and/or devices found."

When I run the commands aplay -l I get:
```

aplay: device_list:221: no soundcards found...

```

When I run lspci -v I get:
```

...
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
Subsystem: ASUSTeK Computer Inc.: Unknown device 1713
Flags: bus master, medium devsel, latency 0, IRQ 4
I/O ports at ee00 [size=256]
I/O ports at e000 [size=64]
Memory at ffaff800 (32-bit, non-prefetchable) [size=512]
Memory at ffaff400 (32-bit, non-prefetchable) [size=256]
Capabilities: <available only to root>
...

```

I alsoe tried:
```

sudo modprobe -v -r snd_intel8x0
sudo modprobe -v snd_intel8x0

```

Here, a popup appears afterwards saying that a new soundcard has been detected and I should set it as default, but when I go to System->Preferences->Sound, the default sound card box has no options in it and running 'aplay -l' still reports no sound device. I have tried restarting as well after running the modprobe commands and running gst-register-0.8 as suggested on other sites, but nothing works, I still have no sound. I also tried the KDE and Xfce desktops at the login prompt but these do not have sound either.

In Multimedia Systems Selector, clicking 'test' on the default output plugin returns:
```

Autodetect: Could not establish connection to sound server

```

(nb. I still get sound in Windows so the card and speakers do work).

Thanks,
John

---

### Post by john.ennew on 2006-08-19
OK, I found a fix for me :)

There is a user group called audio and all users which are to have control of the audio device must be a member of that group.  I have no idea how my user account stopped being a member of that group, but adding it back and restarting the computer brought back the sound.

Work instructions:
System->Administration->Users and Groups
Choose the Groups Tab
Make sure the box "Show all users and groups" is ticked and scroll down the window to find the audio group (it's not in alphabetical order)
Highlight it and click Properties
Add all group members which need audio by highlighting the name in the left collumn and clicking add so they appear in the right collumn.
Click OK, OK and restart the computer.

Hope this helps someone,
John

---

### Post by Culito on 2006-08-19
Eh, I think I'm having a hardware failure of some sort.  I have drivers installed, the hardware is there and detected, I'm in the audio group.  I think I'll find someone with an old soundcard pop it in, disable my onboard audio, and see if I can get it working.  That's the only thing I can think of to do next...I'm out of ideas here.

---

### Post by glennric on 2006-08-19
> **Culito said:**
> Eh, I think I'm having a hardware failure of some sort.  I have drivers installed, the hardware is there and detected, I'm in the audio group.  I think I'll find someone with an old soundcard pop it in, disable my onboard audio, and see if I can get it working.  That's the only thing I can think of to do next...I'm out of ideas here.

Sorry, I can't think of anything else to do either.

---

### Post by xpod on 2006-08-19
If you HAD sound then your like me and many others who seem to "cruise along" without a care(?)suddenly to wake up and realise our sound has vanished.
This seems really common with the sound for flash videos etc.

There will no doubt BE a simple fix BUT like moi you`ll probably spend days trying to suss out a problem that is really but the click or three of a mouse button away..(or a line of code?)

SODS LAW....(or murphys if you like)....
Hope you suss it soon.....:confused: :-k :p .....IT`s all good

---

### Post by Culito on 2006-08-20
xpod, you're probably right.

Anyhoo, I disabled my onboard sound the other day, and I still get this in my Device Manager:
Platform Device (snd_gereric.1) and underneath it:
UART ALSA Control Device
UART OSS MIDI Device
(null) OSS MIDI Device

What is this stuff?  Is the modem sound trying to take over?

---

### Post by xpod on 2006-08-21
Yeah i got them too in device manager.....thats your sound contollers(or whatever their called)
Those are the choices you get to pick from in the "multimedia system selector".
Your sounds "there" by the look of it but im not so sure you should turn your onboard sound off in your bios if thats all you have.
Thats something im still trying to figure myself as i seen somebody else on another thread giving advice to that effect but that was cause the bloke in question had a separate soundcard of some decription i think, hence his problem but i dont think you should be turning it off if thats all you got?

Mabey someone who obviously knows better than us could tell us????????
Does using either alsa or alsa-oss(or WHATever their called?)mean that you should disable onboard sound....I dont think it does but im usually wrong.
ive ONLY been playing with pc`s for "months" so THATS my excuse](*,) :p

Plus....MINE works...I just dont know how to "explain" it to MYSELF never mind someone else...lol

EDIT2:HA...typical,It seems that although i do have sound on everything like flash or rythmbox i now dont have it on the games you get on ubunto.
I.E...armagetron or tux etc......Me and my big mouth......Ach well,if everything "worked"....THEEEEEN i`d reckon there was something wrong..lol

---

### Post by Culito on 2006-08-21
Good times, eh?

Well, My onboard sound is labeled as "SiS PCI Audio Accelerator (Rev 02)."  It shows up in the hardware profile if it's enabled in the BIOS.  I think this stuff might be the MIDI interface through the game port, or something to do with the modem sound (UART is a serial interface, I think). Just guessing, though.  It doesn't matter if I select ALSA or OSS or whatever in the Systems Selector, It still gives me errors.

---

### Post by xpod on 2006-08-21
Hi again,still at it then...I really wish i could actually help but im one for just stumbling across my answers as it is so other than recalling things i "clicked" im afraid thats about as much as you`ll getf rom me ...just now.

---

### Post by Culito on 2006-08-21
Heh, that's ok!
If I have a major breakthrough, I'll post it here, but I'm kinda stuck until I get a decent PCI soundcard...

---

### Post by cajunaggie on 2006-08-23
I'm having the same issue as the rest of you. It didn't show up until after I installed the latest update, so I'm working if it had something to do with that bugged update.
I rebooted after the update and I found myself removed from the sudoers list, also with no sound. Some smart people told me how to fix the sudo issue so now I'm working on the sound thing. I'll let you know if I find anything.

---

### Post by cajunaggie on 2006-08-23
Thanks to John.Ennew for your help! Turns out I had the same audio users issue. Thanks for the pointer. =D>

---

### Post by Culito on 2006-08-23
Glad you're problem wasn't so bad.
I'm workin' on a week without music so far.  I am supposed to be getting a soundcard from a friend tonight - I hope that works out.

---

### Post by Culito on 2006-08-24
With luck running out, and after about 3 rum&cokes, I have purchased a CREATIVE ENSONIQ 2.1 XP DIGITAL AUDIO PCI SOUND CARD off of eBay for $.99.  It better freakin' work.

At least after shipping I'm only out $9.99.

---

### Post by CassioBunana on 2006-08-26
Hi Culito, I've just read your post...I guess I've exactly your problem...Have you finally solve it? I've tried to rebuild alsa, muting almost everyhting, check group permission but no result!

Andrea

---

### Post by theoritic on 2006-08-26
I dont know if this works for anyone or if this is the right place to do it. But what i did was i went to terminal, "sudo alsamixer" then once im in i just arrowed over to "line Jack Sense"  mine said it was off i just turned it on, and restarted the computer.  And it worked.

---

### Post by Culito on 2006-08-26
sudo alsamixer gives me an error:
alsamixer: function snd_ctl_open failed for default: No such device
So the summary is, after all this fiddling, is that the device is listed, the proper drivers are loaded, and still all the apps give me a message that there is no hardware/devices to open.  I'm thinkin' hardware failure.
Interestingly, the hardware listed in lspci is a "SiS Audio Acclerator", but I cracked open my case and the sound chip is a VIA 1612.  I might try some VIA drivers.
Anyway, I've already ordered a cheap Ensoniq soundcard off of eBay for $.99.  (After making sure it was supported by alsa.)  We'll see what happens when I get that baby installed.

---

### Post by deadgoon on 2006-08-29
I hope this helps you out.  Check out the following HOWTO:

[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

I was having a similar problem to yours. I was messing around with the Sound settings (System>Preferences>Sound) and accidently unchecked the "Enable software sound mixing (ESD)" box.  After closing it out I realized my mistake and went back to it and rechecked it... no sound.  I restarted X... no sound.  I restarted the computer... sound... but only on the login screen.  When I logged in... no sound.  I knew my card wasn't defective because I had the login page sound, but I couldn't figure it out.  First I saw your post and after more searching I found the HOWTO above.  I followed the instructions exactly and my sound magically started working again.  I didn't even have to restart.  I should have checked between each step to see which one did it, but I didn't think of it at the time.  Let us know if it works.

---

### Post by Culito on 2006-08-30
Hey deadgoon,
Thanks - I'm glad to see my post pop up every once in a while.

But, no dice.  My problems occur at bootup:


[   35.814717] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   37.574299] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   38.754012] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:1934: AC'97 0 does not respond - RESET
[   38.810222] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:1943: AC'97 0 access is not valid [0x0], removing mixer.
[   39.565821] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   41.325397] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   43.084978] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   44.264697] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:1934: AC'97 0 does not respond - RESET
[   44.320905] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:1943: AC'97 0 access is not valid [0x0], removing mixer.
[   45.076504] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   46.836085] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   48.595664] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   49.775384] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:1934: AC'97 0 does not respond - RESET
[   49.831589] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:1943: AC'97 0 access is not valid [0x0], removing mixer.
[   50.587190] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   52.346770] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   54.106351] ALSA /usr/src/modules/alsa-driver/pci/trident/../../alsa-kernel/pci/trident/trident_main.c:3246: AC'97 codec ready error [0xf4000]
[   54.110418] Trident4DWaveAudio: probe of 0000:00:01.4 failed with error -5

Something about AC'97, the hardware and the snd-trident module not getting along.  I'd be surprised to ever hear sound again, even with a new soundcard, after all the tweaking I've done.

---

### Post by Culito on 2006-08-31
Alright, so I popped in my new used eBay Ensoniq es-1370 pci card and I have sound.  Woo hoo.

---

### Post by KhaaL on 2006-09-05
glad to see your sound back :) too bad there was no solution discovered as it would have been intresting to see what caused it in the first place...

anyway, welcome (back) to the world of sounds and music :p

---

### Post by NPALeech on 2006-10-20
> **john.ennew said:**
> OK, I found a fix for me :)

There is a user group called audio and all users which are to have control of the audio device must be a member of that group.  I have no idea how my user account stopped being a member of that group, but adding it back and restarting the computer brought back the sound.

Work instructions:
System->Administration->Users and Groups
Choose the Groups Tab
Make sure the box "Show all users and groups" is ticked and scroll down the window to find the audio group (it's not in alphabetical order)
Highlight it and click Properties
Add all group members which need audio by highlighting the name in the left collumn and clicking add so they appear in the right collumn.
Click OK, OK and restart the computer.

Hope this helps someone,
John

Many thanks for that tip. I'm not sure why my username was removed from the group to begin with, but that fixed my problem. (I hadn't posted in this thread, but I did have that problem anyway.)

---

### Post by Glendon on 2006-10-21
I lost my sounds as well awhile back. Apparently I screwed up my groups somewhere along the line as once I followed john.ennew's suggestion and added my user to the audio user group (and rebooted) my sound came back.

Thanks!

---


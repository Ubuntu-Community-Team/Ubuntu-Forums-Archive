---
title: "DOSBox 0.72 and MIDI Support"
date: 2007-11-20
forum: Multimedia &amp; Video
---

### Post by imec on 2007-11-20
Hello, I have been looking and looking for a solution to my problem. I searched the forums and couldn't find the solution, so I'm apologizing in advance if this topic has already been discussed. Anyways, I can't seem to be able to get General MIDI support in DOSBox 0.72 under Linux Mint 4.0 (Ubuntu Gutsy). I have installed timidity but I don't understand what I am supposed to do now (I supposedly need to link DOSBox to the MIDI files that come with the install, but I can't find them). Currently, Adlib and basic Sounder Blaster are supported (I also have downloaded the necessary files for Gravis Ultrasound, but the instruments usually sound worst in most games). Sound Blaster AWE32 isn't supported, which I don't really mind. But MPU-401 (which I believe is what you would call general MIDI) isn't supported in a single game (examples: Abuse, Hexen, Heretic, and Doom), which I really, really want. So, do any of you guys know what I need to do? I couldn't find the solution and have been trying all sorts of crazy things, but to no avail (including setting the default sound driver to alsa in the dosbox.conf). Thank you for your time.

---

### Post by imec on 2007-11-26
(Update)
Alright, after running timidity (timidity -iA -B8,2 -Os) it binds itself to device 128:0. I updated my dosbox.conf's midi section as followed:

mpu401=intelligent
device=alsa
config=128:0

DOSBox and Timidity are now synced, but I receive the following error (in the terminal):

ALSA lib pcm_dmix.c:866:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')

For some odd reason, MPU-401 support worked perfectly when I first installed Timidity (how happy I was), after rebooting the system it no longer works (I didn't modify anything). So it's very strange, I don't know. Do you guys know what's going on?

---

### Post by imec on 2007-11-27
Okay, problem solved. It seems that before running Timidity the first time you need to set the modprobes as follow:

sudo modprobe snd-seq-device
sudo modprobe snd-seq-midi
sudo modprobe snd-seq-oss
sudo modprobe snd-seq-midi-event
sudo modprobe snd-seq

Since I no longer use Ubuntu I had to switch to init 2 with ctrl+alt+f2 and login as root. Uninstalling and then reinstalling with the modprobes fixed the problem instantly, very cool.

---

### Post by imec on 2007-11-29
I have been fooling around with Soundfonts, and I highly suggest Airfont-180 (it's better than Unison, SGM2, and Crisis) since it's free and even surpasses some of the other fairly expensive soundfonts out there (Sound Implants 24MB, Z3ta, Papelmedia 2006, etc..). Although I'm saving up the rest of my money for the SONiVOX 250MB soundfont that I have heard so much about. Anyways, to use soundfonts clear your /usr/share/timidity/timidity.cfg (you can keep the options put get rid of the directories and default configs) and type in the following:

soundfont /home/yournamehere/.soundfontdirectory/soundfont.sf2

Also, the volume seems alittle too low so you can increase it by adding the following to your timidity.cfg:

opt A 200

I'll tell you guys what I think of SONiVOX once I get it.

---

### Post by Malor on 2008-05-14
Hi, I just wanted to pass along that this was an extremely useful thread, in that it solved the problem for me.  But, as is often the case with Linux these days, many of these steps can be handled for you automatically.  You don't have to work this hard!

To get Dosbox 0.72 MIDI working with Ubuntu 8.04:

[LIST=1]
[*]Go into Synaptic Package Manager and install these packages:
[LIST=A]
[*]dosbox
[*]timidity
[*]fluid-soundfont-gm
[*]fluid-soundfont-gs
[/LIST]
[*]Open a command prompt, and type **sudo gedit /etc/timidity/timidity.cfg**
[list=A]
[*] The last line in the file says "source /etc/timidity/freepats.cfg".  Put a # mark at the beginning of that line to comment it out.  We're going to use a soundfont instead. (which we installed in the prior step.)
[*]On the next line, type: **soundfont /usr/share/sounds/sf2/FluidR3_GM.sf2**
[*]Save and exit
[/list]
[*]Restart timidity with **sudo /etc/init.d/timidity restart**
[*]If you don't already have a dosbox.conf you want to use, type **dosbox** and hit enter.  Dosbox will pop up.  At its command prompt, type: **config -writeconf dosbox.conf**.  This will generate one for you.  Then type **exit** to quit dosbox.
[*]Type **gedit dosbox.conf**.
[*]Click the Find button, type **mpu401=** and click Find.  You should see a line highlighted.  Close the search popup.  
[*]The three lines starting with mpu401= should look like this:
```
mpu401=intelligent
device=alsa
config=128:0
```
[*]Save and exit[/list]

Ok, MIDI sound should now work in DOSBox.  You will most likely want to edit the dosbox.conf file further, to mount your dos game directory as your C drive, but the part I'm addressing here is now fixed.

It's possible that the correct kernel modules *might* not get loaded the very first time you run timidity.  You *might* need to either do the modprobe commands a few posts back, or reboot the box.  They will definitely be loaded correctly after a fresh reboot, so that's one-time-only thing.

If you have a GS-capable game, you have also installed a GS patchset as well. (GS is an advanced version of General MIDI.)  If you have any games that will support it, you can modify the timidity.cfg to load **FluidR3_GS.sf2** instead of **FluidR3_GM.sf2**.

edit: also note that if you're an advanced timidity user, and need to give it other arguments, put them in the file /etc/default/timidity, in the quotes after TIM_ALSASEQPARAMS, and restart it as above.  The defaults seem fine for dosbox.

---

### Post by 45acp on 2008-06-12
I finally got midi to work thanks to Malor's guide but the music stutters very bad. Is there a fix for this?

---

### Post by Malor on 2008-06-14
You might be asking DOSBox to run faster than it's able to on your system.  You'll get stuttery sound when you do that.  

In general, use the 'dynamic' CPU core, which is enormously faster than the other types, and start out fairly slow.  Most machines nowadays can support 16000 cycles on the dynamic core.  A good Core2 at 2.4Ghz should comfortably be able to run at 100,000, fast enough for virtually any DOS game, even ones like Magic Carpet and MDK.  

The other CPU cores are MUCH slower, but a bit more compatible.  If you need one, I'd suggest starting at 1/10th of your dynamic speed, and then adjusting from there.

---


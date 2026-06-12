---
title: "Sound Problems Through Dell Docking Station"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by npmeyer on 2006-01-17
Hey all,

I have a Dell Inspiron 8500 and I've just switched to Ubuntu from Fedora Core 4 and so far I love it!

However, I do have a problem getting sound through the jack on my docking station.  I get great sound through the laptop's built in speakers and through speakers when plugged in to the headphone jack on the laptop, but when speakers are plugged into the sound jack on the docking station, I can't get any sound.  This was a problem with Fedora too until they fixed it in Fedora Core 4.  Maybe somebody knows how Red Hat and Company figured it out.

I found an older post to this effect where several people claimed to be experiencing the same problem, but no one ever posted a solution.  Does anyone know how to get this working?  I played with the mixer settings, turning every channel up, and still couldn't get anything.

---

### Post by jcpeart on 2007-01-26
I am using LinuxMint Bea on a Dell laptop and having the identical problem with no sound through the jack on the docking station.

---

### Post by dwangoac on 2007-02-16
Well, I found a workaround, but it's not exactly a good one.

In alsamixer, enable the switch marked "IEC958".  This enables direct SP/DIF output to the headphone jack, which means it's FULL VOLUME, ALL THE TIME.  Caps for emphasis, of course.

I gave up and just started plugging my headphones in to the side of my laptop, but I'd like to get this working.  If you have headphones / speakers with a volume controle, however, this solution might work for you.

Best of luck,

A.C.
******

---

### Post by Meson on 2007-10-22
Are the any updates to this issue?  I'm tired of the not being able to adjust my volume.

---

### Post by GrammatonCleric on 2008-03-04
You should be able to adjust the volume if you change the Volume Applet from Master to PCM.

-GC

---

### Post by Switch92 on 2008-03-18
Hey all,

I have a Dell Latitude D520 with a docking station and I'm experiencing the same problem.  When I have the system on the docking station sound comes through the laptop's speakers not the desktop speakers.  (With the speakers plugged into the headphone jack of the docking station.)  Does anybody else have any ideas how I can fix this so that it can 'sense' when docked use desktop speakers?

---

### Post by GrammatonCleric on 2008-03-19
This is how I got my Dell D820  to work with the Docking station audio port....

With the laptop docked...


1. Right click on "**Volume Applet**" (the little speaker on the Gnome panel).

2. Select "**Open Volume Control**."

3. Now select **Edit** -> **Preferences.** 

4. Put a check mark next to **IEC958.** 

5. Click **Close**.

6. Click on the **Switches** tab in the **Open Volume Control **window.  

7. Put a check next to the **IEC958** option.

8. Select "**Playback Tab**" and mute "**Master**" (i.e. click on the little speaker icon below the Master level.)

9. Lower the volume level of the current **PCM **and close the **Open Volume Control **window.

10. Connect your speakers or head phones to the headphone audio port on the left side of the Dell Docking station.

11. Right click on "**Volume Applet**" (the little speaker on the Gnome panel) again.

12. Select **Preferences**.

13. In the window that appears select **PCM** then click **Close **(this changes the ** Volume Applet** to control **PCM** volume instead of the **Master**).

14.  Now try to play something, If the volume level is to loud left click on the **Volume Applet** and lower the level.

15.  When the laptop is undocked you will need to the set Volume Applet (step 13)  back to use the **Master** volume as well as** un-mute** it.

Enjoy,
-GC

---

### Post by Switch92 on 2008-03-19
Okay, I will try this when I get home...  Although last night when I was messing with it I couldn't find the 'Switches tab in the Open Volume Control window'.  I'll try again, hopefully it was just fatigue!

Thanks!

---

### Post by GrammatonCleric on 2008-03-19
Let me know if this works for you.  I plan on adding this little howto to the Community Documentation.


-GC

---

### Post by Meson on 2008-03-19
> **GrammatonCleric said:**
> This is how I got my Dell D820  to work with the Docking station audio port....

I've been using the IEC switch to get audio through speakers connected to the docking station, however controlling the PCM certainly does not control the volume for me.  I can really only mute or unmute.  Volume needs to be adjusted from the control on the speakers.  Some applications let me control volume with their own slider (like VLC and Rythmbox).

---

### Post by GrammatonCleric on 2008-03-19
> **Meson said:**
> I've been using the IEC switch to get audio through speakers connected to the docking station, however controlling the PCM certainly does not control the volume for me.  I can really only mute or unmute.  Volume needs to be adjusted from the control on the speakers.  Some applications let me control volume with their own slider (like VLC and Rythmbox).

Hmmm.. setting the Volume Applet to PCM works like a charm for me. What is the is the Model and Part number of your dock?

Mine is ...

Model Number = PR01X
Part Number = 2U444 A01

-GC

---

### Post by Switch92 on 2008-03-23
Hey GC, here's my problem.  I right click on 'Volume Control' and then 'Edit' then 'Preferences'.  When the box comes up, the only options that are available are 'Master', 'PCM', 'Capture', 'Capture Mux', and 'Input Source'.  So I can't put a check mark next to IEC958...  I tried to add more sound options through 'Applications' and 'Add/Remove'.  I added about every sound option but it's still not showing up.

Thanks,
Michael

---

### Post by Switch92 on 2008-03-25
GC,

Model Number = PR01X

Part Number = 2U444 A01

Our devices are identical.

---

### Post by GrammatonCleric on 2008-03-25
Hmmm... our laptops appear to have same audio chipset too (i have the D820)...  something is different.  Here's what I see....
[URL="http://ne0t0ky0.org/misc/Screenshot.png"]
Screenshot 1[/URL]

and 
[URL="http://ne0t0ky0.org/misc/Screenshot1.png"]
Screenshot 2[/URL]


-GC

---

### Post by Meson on 2008-03-25
I too have the same model and part number for my docking station.

My sound card seems to be different though, it's labeled as Intel 82801DB-ICH4, not HDA Intel.  My options are a little different in the preference window... I have a lot more.  But the one I'm most curious about is I'm missing IEC958 Capture.

I'd just like to clarify, that I do get sound out of my external speakers, but I  cannot control the volume.

GC, are those screen shots from Gutsy or Hardy?

If anybody has had any different experience with Pulseaudio and Hardy, please post.  I installed Hardy Beta and had no new luck, but then I'm not entirely familiar with Pulseaudio.  Everything seemed to work the same, my sound device was controlled through ALSA....

---

### Post by GrammatonCleric on 2008-03-26
The screenshots are of Gutsy.   That said this past weekend I imaged my laptop and upgraded to Hardy and  I still had the same sound options in Hardy.  Because the several things are still not working right in Hardy (i.e. networkmanager vpnc plugin the big one for me) I've restored my laptop back to my Gutsy image.

-GC

---

### Post by GrammatonCleric on 2008-03-26
Out of curiosity, can you both run the following commands and post the output?

Command 1:

```

lsmod | grep -i snd

```Command 2:

```

lspci 

```Command 3:

```

cat /etc/modprobe.d/alsa-base 

```-GC

---

### Post by Meson on 2008-03-26
Hmm, maybe it all just boils down to the sound card difference - I have a D800, I'll try out my brother's D810 and friend's D820 if their willing to try out *nix.   Can anyone else with an "HDA Intel" post their experience?

---

### Post by Meson on 2008-03-26
```
matt@matt-laptop:~$ lsmod | grep -i snd
snd_intel8x0           34972  1 
snd_ac97_codec        100644  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
```

```
matt@matt-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5650] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

```

```
matt@matt-laptop:~$ cat /etc/modprobe.d/alsa-base
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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

```

---

### Post by GrammatonCleric on 2008-03-26
You have a different chipset.  

I'm running...
[FONT=monospace]
**Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)**

as you appear to be running the ...
[/FONT]
**Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller**


from the command line, if you run **alsamixer**  what options do you see?

-GC

---

### Post by Meson on 2008-03-26
Attached.

---

### Post by GrammatonCleric on 2008-03-26
In alsamixer the option next to the IEC958 (IEC958 P) have you tried adjusting it's sound level (the up or down arrows)?  I'm betting that it is IEC958 PCM.

-GC

---

### Post by Meson on 2008-03-26
One more thought..., what firmware is installed in your docks everyone?

I'm pretty sure I've got A04.

---

### Post by Meson on 2008-03-26
> **GrammatonCleric said:**
> In alsamixer the option next to the IEC958 (IEC958 P) have you tried adjusting it's sound level (the up or down arrows)?  I'm betting that it is IEC958 PCM.

That option is kind of interesting.  For my line-level sound to work, either the IEC958 Playback option must be muted, or the volume needs to be all the way down.  Once I raise the slider/unmute I get nothing from my externals.

---

### Post by GrammatonCleric on 2008-04-01
Here's a stab in the dark.  

Recently I was trying to get my Bluetooth headset working with Skype.  One of the things that was suggested in Bluez howto was a custom .asoundrc for the headset  in my home directory.   When I created such a file I was no longer able to control the volume level for my dock port from the Volume Applet.  So I removed the .asoundrc file and rebooted.  After the reboot I was able to control the dock sound port volume again.  

Do any of you have a custom .asoundrc file in your home directory?

-GC

---

### Post by Switch92 on 2008-04-01
Hi GC,

I can check, but I don't believe I have any custom .asoundrc file in my home directory.  I am new to this OS and if it takes doing something outside of the basic install I haven't done it.  I'll reply after I check though!

Thanks

---

### Post by Meson on 2008-04-01
I don't have a custom .asoundrc file, but maybe I do want one.

GC, if figure out what setting in this file re-enables your volume control, please post.

---

### Post by Switch92 on 2008-04-09
Hey GC, 

Can you tell me where exactly I would find that file?  I checked in 'home' in 'filesystem' but the only item in there is a folder with my name on it.

Thanks!

---

### Post by Meson on 2008-04-09
It would be in /home/yourusername

So possible /home/switch92/.asoundrc

---

### Post by drown on 2008-04-11
Hi,
I'm using a D600, with the dell docking station.  I experience exactly the same thing as Meson, including the strange behaviour of the IEC958 slider.  It's not a huge problem, but it is a slight inconvenience!
I'll keep playing around, and keep you posted if anything happens.

---

### Post by GrammatonCleric on 2008-04-26
Well made the migration to Ubuntu 8.04 Hardy, and the new PulseAudio sound system, so far everything is still working.  Actually it is even better.  Before I would have to manually mute the "Master" volume control when switching between docked and undocked, this now works flawlessly without any manual intervention.  

So far so good....

-GC

---

### Post by Meson on 2008-04-26
You're lucky.  Switching to Hardy for me doesn't affect the way I need to control my volume.  But it does take my one step backward.  The audio sounds horrible.  It sounds like the speakers have been blown out or something.

I've seen suggestions like lower your PCM volume to fix this, but because the audio seems to be traveling to my speakers at line level, I can't fix it.

---

### Post by Meson on 2008-04-26
You're lucky.  Switching to Hardy for me doesn't affect the way I need to control my volume.  But it does take my one step backward.  The audio sounds horrible.  It sounds like the speakers have been blown out or something.

I've seen suggestions like lower your PCM volume to fix this, but because the audio seems to be traveling to my speakers at line level, I can't fix it.

---

### Post by Switch92 on 2008-04-26
GC, I have to blow my box up cuz the HD partitioning isn't how I want it.  So I'll install hardy and see if that fixes my sound problem too.

---

### Post by Switch92 on 2008-05-01
Hey all,

I just upgraded to Ubuntu 8, HH.  I followed GC's post #7 from March 19th and I now have sound through desktop speakers.  Note: his instructions will not work for Ubuntu 7, GG.  That was my previous version and I was never successful (because the options didn't show.)  With Ubuntu 8 follow GC's instructions verbatim and you should be in good shape.  Thanks, GC!

Michael

---

### Post by GrammatonCleric on 2008-05-02
> **Switch92 said:**
> Hey all,

I just upgraded to Ubuntu 8, HH.  I followed GC's post #7 from March 19th and I now have sound through desktop speakers.  Note: his instructions will not work for Ubuntu 7, GG.  That was my previous version and I was never successful (because the options didn't show.)  With Ubuntu 8 follow GC's instructions verbatim and you should be in good shape.  Thanks, GC!

Michael

Awesome! And it just occurred to me -- sorry -- that I had the "Pre-release (proposed)" repo updates enabled  when I had Gutsy installed. 

-GC

---

### Post by craig_d on 2008-05-07
Just wanted to say thanks!  Followed your instructions and got my Dell Latitude D820 and D/Dock headphones jacks working perfectly in Ubuntu Hardy 8.04.

Thanks again,
Craig

---


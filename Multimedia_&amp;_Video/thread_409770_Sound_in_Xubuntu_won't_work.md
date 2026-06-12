---
title: "Sound in Xubuntu won't work"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by buckdog05 on 2007-04-14
I have a Compaq Presario 7360 from the Windows 98 era. Do I need to install something or buy a new sound card?

I tried playing audio from Flash in Firefox and from a CD in Xine. The cd seemed to skip, with it playing at like 10x. When I try to play an audio stream in Xine, the program freezes.

The sound card in it is integrated, and I tried another (PCI) from an old Gateway, although I did not bother to connect it to the cd-rom drive. Is this essential? I can get the model number on the new one if it would be important.

The sound did work in Widows 98. There are no sound ports on the modem, which I pulled to put the new sound card in it's place (I heard that sound comes through modem on some older Compaqs.)

Here is what I got from LSPCI relating to sound:
00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
00:0d.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)

Also, when I go into "sound" in the settings, all of the items are checked but have ",0" next to them, does this mean that they are muted. Do I need to enable the PCI device somehow?

Thanks, I love your Operating System!

---

### Post by Brendantb on 2007-04-15
Hi,

Have you downloaded the nonproprietary codecs for CDs, etc.? Xubuntu doesn't come with these by default. There is a list in the guide that comes preloaded in Firefox.

---

### Post by buckdog05 on 2007-04-15
Do I need a codec to play audio from Flash in Firefox.  Flash installed without a problem, and I do not hear any other sounds, although maybe nothing else is supposed to make a sound, because I do not have the CD codecs and maybe there is not a startup sound?

Thanks!

---

### Post by Brendantb on 2007-04-15
Hi, 

When you switch the computer in, there should be a "drum roll" at the log in window. Do you hear that?

---

### Post by buckdog05 on 2007-04-15
No, glad to be talking to someone with the same OS.  I am happy to get a new sound card, do you think that I should?

I am just worried that I'll buy one and it still won't work.

Does flash sound work with just installing the firefox plugin (Video works for me, albeit slowly)

---

### Post by Brendantb on 2007-04-16
Hi, 

Sorry about the delay... 

If you don't have system sounds, then you have a configuration problem. From looking round the boards, this is not uncommon unfortunately. I wouldn't rush into buying another sound card until you are sure you will be getting a card that is supported. However there are a few other things that you can do first to see if your sound card is detected. 

Post the results of code: 
      
aplay -l

This will list the detected sound cards. 

Your sound settings are normal, mine had a (0) appended too. 

The best way to test the sound is to use an MP3 file, if you have access to one. You can import a test file from another computer or from a windows partition, or you could even find on on the net. Download the Sound Juicer app, and all its dependencies, and that will enable MP3 support in Xubuntu. 

I don't know about the flash plugin for firefox, but that is a peripheral matter if your sound card isn't working. The main thing to do is to find out as much as possible about the particular card, and then find out if it can be enabled by adding some code to the /etc/module file. 

There are other threads about sound cards that you might want to look at: 

[http://ubuntuforums.org/showthread.php?t=407914&highlight=sound+card](http://ubuntuforums.org/showthread.php?t=407914&highlight=sound+card)

Remember that in Xubuntu, the editor is nano, and not gedit as in Ubuntu. 

Cheers,

---

### Post by dannyboy79 on 2007-04-16
to find out what chipset your onboard audio uses, put this into the command line and paste back what it returns.

lspci -v

this should show us all the pci info on your motherboard. also, did you check out the comprehensive sound guide located here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by buckdog05 on 2007-04-16
card 0: PCI [ESS Allegro PCI], device 0: Allegro [Allegro]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


It still feels cool to post from Linux!

Where do I go from here?  I did not hear the startup sound.card 0: PCI [ESS Allegro PCI], device 0: Allegro [Allegro]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by buckdog05 on 2007-04-16
Info from new Lspci command:
00:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
        Subsystem: Ensoniq Creative Sound Blaster AudioPCI64V, AudioPCI128
        Flags: bus master, slow devsel, latency 64, IRQ 10
        I/O ports at 1480 [size=64]
        Capabilities: <access denied>

00:0d.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 10)
        Subsystem: Compaq Computer Corporation Unknown device b207
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at 1000 [size=256]
        Capabilities: <access denied>

---

### Post by buckdog05 on 2007-04-16
Yes, Yes, and more YES!!!!
After following steps in the sound guide, I got sound to come right out of the onboard sound card.  I am thrilled, you are such a nice community, and I truely thank you for all of your help.

Linux has saved many computers that I have worked with from the dump, and is a true alternative to Windows.

Rock on!

One thing, the problem turned out that the sound was MUTED!  MUTED, how crazy is that?  I ran the alsamixer command and changed the boot options (see guide) to fix it, but why the heck was it muted in the first place?

Sound works perfectly in Flash and on YouTube, thanks!

---

### Post by dannyboy79 on 2007-04-18
> **buckdog05 said:**
> Yes, Yes, and more YES!!!!
After following steps in the sound guide, I got sound to come right out of the onboard sound card.  I am thrilled, you are such a nice community, and I truely thank you for all of your help.

Linux has saved many computers that I have worked with from the dump, and is a true alternative to Windows.

Rock on!

One thing, the problem turned out that the sound was MUTED!  MUTED, how crazy is that?  I ran the alsamixer command and changed the boot options (see guide) to fix it, but why the heck was it muted in the first place?

Sound works perfectly in Flash and on YouTube, thanks!


that is a common problem. there have been so many users that end up saying they go into alsamixer and find that the PCM or VOL is muted, glad you're up and running and HEARING.

---

### Post by jeffemmert on 2008-04-23
I had a similar problem using Ubuntu 7.10 and Mandriva Spring 2008 on a Gateway laptop with an ESS Allegro 1988 sound card. Neither o/s would run the right channel of the sound card, but when I rebooted in XP Pro, it worked fine. After reinstalling Ubuntu 7.10 for the third time using the same live CD, the audio problem cured itself.

---


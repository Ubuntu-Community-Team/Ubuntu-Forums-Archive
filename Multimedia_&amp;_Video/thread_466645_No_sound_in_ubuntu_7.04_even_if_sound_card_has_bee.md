---
title: "No sound in ubuntu 7.04 even if sound card has been recognised"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by comprendrelinux on 2007-06-06
Hi!Im new to ubuntu and I have to say that I find Feisty Gr8!

However I have no sound at all. I use Audigy 2 ZS and it has been recognized. I did uncheck the Analog/digital output jack but nothing. i did reboot but still... Im desperate. Im wondering if the alsa driver has been installed correctly.

In system-sound-preferences, when i click test I cant hear anything and the it doesnt move.
Any suggestion???????????

---

### Post by paulg on 2007-06-07
Run this command in a terminal window and post the output. Then we will know if your card is detected and the module is loading.

```
cat /proc/asound/cards 
```

Also, if your motherboard has a built in soundcard you may need to disable it in your BIOS.

~pAul.

---

### Post by exspiro on 2007-06-07
hi,

im having a similar prolbem.

output:

 cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb0000000 irq 21

thanks

---

### Post by dennis.ayala on 2007-06-11
Same problem here...

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x8c080000 irq 23


Dennis

---

### Post by meenfreem on 2007-06-12
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd2bf8000 irq 193

same problem here. Haven't tried disabling the sound in BIOS yet though.

---

### Post by daphenom on 2007-09-16
hi! I just recently switched to Ubuntu.... I finally got tired of that MS crap...

Im loving everything except that my laptop doesnt have any sound.. here is the output of the command..

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at 0xe0100c00, irq 17

---

### Post by angliski on 2007-09-16
Same for me
Cat produces: 0 [Ck804               ]: NFORCE - NVidia CK804
                                                         NVidea CK804 with ALC850 at 0xec201000, irq 21

Hope you can help
Thanks
Steve

---

### Post by rast4man on 2007-09-17
Same prob here. :(

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0b40000 irq 21

---

### Post by duruttye on 2007-10-02
So, any  of you solved the problem????
If yes, than how?

---

### Post by auquicu on 2007-10-02
Same problem here.

% cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xffaf8000 irq 22

---

### Post by Guthjain on 2007-10-02
Ok.  I'm going to chime in here since I just installed my Audigy Z2s over lunch and made it work in Fiesty 7.04 - which I have had on my new homebrew AMD64 system for exactly two days.

That's all the experience I have with Linux, btw.  Two whole days.  

1.  I'm not an expert.  Should an expert appear, listen to him/her :)
2.  I absolutely hated my integrated 7.1 audio output off the motherboard.  It leaked wierd digital ambient noises into the speaker system like micro-crickets.  It also made a nasty little 'thrumm' when I scrolled down a page in Firefox.  So it had to go.  All I had left to put into the motherboard was my old Audigy Z2s PCI card.  Which I'd taken out because it was leaning against my SATA drive cable interface.  

Step 1. I assume you've unplugged your audio cable from your onboard sound jack.  If not...unplug your audio cable.  I also assume you've put your Audigy card in.  Plug your cable into the proper jack of the Audigy.  I screwed up and put the cable in the wrong jack my first time refiring up, but then, I'm notorious for that.

Step 2.  If you were using onboard audio, like I was, go into your BIOS at startup and disable onboard audio.  This is actually really easy to do and won't damage anything permanently.  Even I could do it.  Hit save and exit.

Step 3. Once into Fiesty's desktop, go to the Sounds area...I think it's under Administration or something...it's not hard to find...and select your card from the list of sources at the bottom.  If it's NOT on the list of sources at the bottom.  [If it's not there, quit reading now and search the forums on how to autodetect your cards.  I didn't have to do this, nor did I download anything other than the ALSAmixer front end program.]

Step 4.  You can do as you like with autodetect in Sounds but I selected the ALSA option for playback.  Hit test.  You will hear a bloody loud tone if your card is now working.  

Step 5.  If you use ALSA, get the ALSAmixer from the Synaptic Manager or the ADD/REMOVE box in Applications.  Run it after install.  If your Audigy is working, you will see it listed in the ALSAmixer overhead.  If it is, open a song or something up on your preferred audio program and see what happens.  If the sound is still missing or not pleasant to the ear, pay around a bit with the controls on the mixer [they're easy to pot up and down] and see if anything is muted or screwy.  

That's it.  If a complete noob to Ubuntu like me can do it, you can too.   And if this does not work for you, keep hunting.  

Cheers

Guthjain

---

### Post by docfl on 2007-10-02
Ok Im having the same issue, sound works on the windows partition, but Ubuntu the sound is not working. This is what comes up in terminal
don@don-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 18
don@don-laptop:~$ 
when I put in the command to show the devices, it shows this:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I had it working when I first installed Ubuntu then when I ran updates, it quit working.
Thanks for the assist.
docfl

---

### Post by Dave Otter on 2007-10-02
Same problem here . Sound is fine in  Ubuntu 6.06 but when I install Feisty sound disappears.
        Can't fi nd a solution,so if anyone finds one I would love to hear it

---

### Post by divdude on 2007-10-03
install gnome-alsamixer (sudo apt-get install gnome-alsamixer)
uncheck everything there except IEC958.
See the attached image.

---

### Post by fadastic on 2007-10-03
Try these steps: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)


You probably have the multiple soundcard issue.

---

### Post by duruttye on 2007-11-18
Hey guys!

I upgraded to 7.10 and the problem was solved.
I had to make a brand new installation, because the upgrade messed up everything, so be careful:)

Hope this helps some of you!
Take care!

---

### Post by robertooo on 2008-04-24
hi, i'm new to ubuntu and 

i having a similar prolbem.

output:

cat /proc/asound/cards
0 [I82801AAICH    ]: ICH - Intel 82801AA-ICH
                      Intel 82801AA-ICH with CS4299 at 0x2000, irq 10
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x220, irq 5

any help........

---


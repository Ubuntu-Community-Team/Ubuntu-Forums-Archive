---
title: "[SOLVED] Sound problem"
date: 2008-06-26
forum: Multimedia Software
---

### Post by borobudur on 2008-06-26
I had no problem in Gutsy with my sound, in Hardy the microphone to use skype doesn't work anymore. 
I'm not sure if it was after I installed Zattoo TV Player :confused: 

I tried everything already over the GUI, the mic never worked anymore.

Then I installed the *gnome-alsamixer* and since then I don't have sound anymore at all :(
I removed it again and reinstalled the *alsa-base* but still no sound.

Has anyone an idea what to do? A reinstallation of the whole system would be quit terrible.

---

### Post by erginemr on 2008-06-26
I believe the programs you have installed have only changes the sound levels or zeroed some of them (incl. microphone). So, you should check out
```
alsamixer
```
from the terminal to rule out this possibility.

Besides, when you double-click on gnome volume control speaker icon, ther should be settings to choose the default source for recording.

---

### Post by borobudur on 2008-06-26
That corresponds to the Graphical User Interface (speaker icon). No, that doesn't help me.

With *cat /proc/asound/cards* I get this:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xcccf8000 irq 17
 1 [Bt878          ]: Bt87x - Brooktree Bt878
                      Brooktree Bt878 at 0xcffff000, irq 23

```Any other suggestions?

---

### Post by erginemr on 2008-06-26
What are the outcomes of the following remaining three commands?
[http://ubuntuforums.org/showpost.php?p=4575682&postcount=2](http://ubuntuforums.org/showpost.php?p=4575682&postcount=2)

---

### Post by borobudur on 2008-06-26
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```lspci | grep -i audio
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
01:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```amixer info
```
Card default 'Intel'/'HDA Intel at 0xcccf8000 irq 17'
  Mixer name    : 'Realtek ALC882'
  Components    : 'HDA:10ec0882'
  Controls      : 43
  Simple ctrls  : 24

```PS: sorry that Turky lost yesterday :(

---

### Post by erginemr on 2008-06-26
> **borobudur said:**
> 
PS: sorry that Turky lost yesterday :(

Thank you very much. :) I was also sorry when Switzerland and Austria were eliminated because they were the hosts of the tournament (the whole event lost much of its spirit when both teams were gone). But unfortunately this is the way this game is all about. One has to lose. This time, it was our turn to lose. The only thing that really bothers me is that we needed this victory badly. Germany had already won the cup 3 times. God knows when we shall have such an opportunity in the future. Gosh :( anyway...


No promises, but I will try to find out a solution for the sound problem. Mmm, more later... But if worse comes to worst, I'd say, back up all you can, and do a clean install.

---

### Post by erginemr on 2008-06-26
1. OK. You should first try this one:
[http://ubuntuforums.org/showpost.php?p=4582215&postcount=42](http://ubuntuforums.org/showpost.php?p=4582215&postcount=42)

2. If it doesn't work, then this one:
[http://ubuntuforums.org/showpost.php?p=4574654&postcount=10](http://ubuntuforums.org/showpost.php?p=4574654&postcount=10)

3. The second item refers to updating ALSA with an easy script, 
[http://ubuntuforums.org/showpost.php?p=4582204&postcount=41](http://ubuntuforums.org/showpost.php?p=4582204&postcount=41)

but you also need to add a line to a config file: 
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

From the above link, 
```
ALC882/885
3stack-dig 3-jack with SPDIF I/O
6stack-dig 6-jack digital with SPDIF I/O
arima Arima W820Di1
targa Targa T8, MSI-1049 T8
asus-a7j ASUS A7J
asus-a7m ASUS A7M
macpro MacPro support
mbp3 Macbook Pro rev3
imac24 iMac 24'' with jack detection
w2jc ASUS W2JC
auto auto-config reading BIOS (default)
```

4. I forgot to ask your pc/laptop brand and model. So, you should check the above line, edit the file /etc/modprobe.d/alsa-base with:
```
gksu gedit /etc/modprobe.d/alsa-base
```

and add the following line to the end of the file:
```
options snd-hda-intel model=3stack
```
replacing 3stack with the corresponding parameter from the above list. 

5. Restart your computer each time.

6. In your attempts, among other things you should also try: auto, 3stack, 3stack-dig

7. This is basically all there is to it. I hope you will get your sound back with this. But you can alwys do a clean install. Here is another document for you to have a look: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Yet, the above steps pretty much covers all there is in this final document.

So, good luck!...

---

### Post by borobudur on 2008-06-26
Thanks [erginemr]("http://ubuntuforums.org/member.php?u=252441") in the first place!

I have my sound back as it was without the microphone in skype. 

Step 1 didn't help but the reinstallation brought it back and I had with all 3 different options the same results. 

Do you have any suggestion what I could try with the mic?

---

### Post by erginemr on 2008-06-26
Nope, except furnishing the above config file with the proper parameter, so that ALSA is correctly informed about the capabilities of your sound card.

Can you also please double click on the volume icon and select microphone related items from the preferences in the menu? Enabling capture related items from the list will also populate the volume control tool with new tabs. Sorry, but this is my best bet...

---

### Post by borobudur on 2008-06-27
I have tried everything over the GUI already. Mic won't work like this.

But I still have the ubuntu 7.10 installation on a other HD. I could check the alsa-base file and compare (that's the installation which worked fine). 

Is there any other config file I should rescue?

---

### Post by borobudur on 2008-06-27
I forgot to tell you: Yesterday after I reinstalled the alsa driver package it didn't work at the beginning, even after the reboot. Then I changed to OSS and the sound was back, then I could also switch to alsa and it worked suddenly (strange!)

---

### Post by erginemr on 2008-06-27
> **borobudur said:**
> I forgot to tell you: Yesterday after I reinstalled the alsa driver package it didn't work at the beginning, even after the reboot. Then I changed to OSS and the sound was back, then I could also switch to alsa and it worked suddenly (strange!)

What can I say, except that Ubuntu is full of surprises. :confused:

They have even included a replacement sound system, PulseAudio in Hardy Heron, whose interaction with ALSA is now a blackbox to me.

---

### Post by borobudur on 2008-06-27
Hey [erginemr]("http://ubuntuforums.org/member.php?u=252441"), did you see post #10? 
Thaks!

---

### Post by erginemr on 2008-06-27
Yes, but unfortunately I am at the end of my wits and have no other tricks up in my sleeves. So, all I can do is pray for you. ;)

Comparing the two config files is always good idea, notwithstanding the fact that Ubuntu substructure has apparently undergone some radical changes between Gutsy and Hardy.

---

### Post by borobudur on 2008-06-27
I'll give it a try and inform you about the success...

---

Okay I found this as difference:
```
options bt87x index=-2                          |    options snd-bt87x index=-2
options cx88_alsa index=-2                      |    options cx88-alsa index=-2
```

---

### Post by borobudur on 2008-06-27
I'll be damned! The mic works again :guitar:
The problem was solved with one of these options:
```
options snd-bt87x index=-2
options cx88-alsa index=-2

```Thanks so much for your help! 
Regards from sunny Switzerland
borobudur

---

### Post by erginemr on 2008-06-27
Well, this is some Great News!! Kudos to You! :KS

Take care yourself. Aufwiedersehen! :popcorn:

---


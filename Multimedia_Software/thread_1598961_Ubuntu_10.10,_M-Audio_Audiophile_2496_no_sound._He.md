---
title: "Ubuntu 10.10, M-Audio Audiophile 2496 no sound. Help!"
date: 2010-10-17
forum: Multimedia Software
---

### Post by Digidis on 2010-10-17
After installing Ubuntu 10.04 on my daughter's computer, I really like how fast it is. Today I freshly installed 10.10 on my main machine which has an audiophile 2496 as a soundcard, and the inboard audio is disable in bios. My ATI video card has some kind of audio out with HDMI. I hope that is not interfering.

I've tried a few of the solutions from a search, but no sound. Can someone please tell me (step by step like I am a six year old) how to configure a new install of 10.10 with this audiocard? I will greatly appreciate it!

Thanks!

---

### Post by Digidis on 2010-10-17
Sorry for a BUMP, I'm still without sound and nothing seems to be working! Other than that Ubuntu is great.

---

### Post by jblock312 on 2010-10-17
left click on the speaker icon, then sound preferences, then hardware.
Does your soundcard show up?
If it does, then the alsa script needs to be changed in order for this card to have analog output. The reason is the 2496 is a 10- channel card, and alsa will only recognize a 2- channel card.
Do a search for "help with M-Audio Delta Audiophile 2496 setup" There are step-by step instructions for changing the script.

One other thing- after suspend, the card will not work. Restart is necessary. So far, that issue has not been fixed.

Hope this helps.

---

### Post by Digidis on 2010-10-17
JBlock, a million thanks! I previously found that thread but the first time it didn't seem to work, redoing it magically fixed everything.

---

### Post by jblock312 on 2010-10-19
Glad to hear it worked for you.
The Delta is a great card.

---

### Post by dangene57 on 2010-11-04
There is an easier way to get analog sound preference in Ubuntu 10.10 and it does not require removing pulseaudio. It only requires two short lines of code added to alsa. Thanks to Alexandre Touret I have fixed my m-2496 sound card. Google Bug #515874 and see Alexandre's solution. It worked for me. I now have Digital stereo input and Analogue stereo output in sound preferences and SOUND! I did not have to add the options snd ice1712... line. Don't forget to reboot after you make the change and then reset your sound preferences.

---

### Post by jblock312 on 2010-11-08
> **dangene57 said:**
> There is an easier way to get analog sound preference in Ubuntu 10.10 and it does not require removing pulseaudio. It only requires two short lines of code added to alsa. Thanks to Alexandre Touret I have fixed my m-2496 sound card. Google Bug #515874 and see Alexandre's solution. It worked for me. I now have Digital stereo input and Analogue stereo output in sound preferences and SOUND! I did not have to add the options snd ice1712... line. Don't forget to reboot after you make the change and then reset your sound preferences.

Just to eliminate confusion, we're talking about the same thing. I should have been more specific. 
The thread is #1540891- #3, where detailed instructions are given for installing these 2 lines.
I agree that removing pulseaudio is not necessary.

---

### Post by tru infini on 2010-11-15
does that same fix work the input on ubuntu 10.10?
on my systems check it says this is my sound device:
0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfe7f4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfe9e8000 irq 19

---

### Post by jblock312 on 2010-11-17
Yes, the same fix works on 10.10.
However, it looks like your 2496 is not listed.
What do you get when you type   "cat  /proc/asound/cards" in the terminal?

---

### Post by tru infini on 2010-11-18
I've fixed the problem with a healthy dose of 10.04. I'll stick with what's been covered for now. thanks anyways.

---

### Post by DukeOfDream on 2011-04-05
Hello...i just installed ubuntu 10.10...i have an Audiophile 2496 pci card as my main audio and it is not working...i have the onboard-motherboard soundcard disabled from bios...if i go to sound prefences and click hardware i only see my graphics card hdmi sound...i've tried many guides without much luck and reinstalled ubuntu 3 times to redo any changes from one guide  to another...The card is working perfectly fine under windows...can anyone help me?These are some outputs from commands...

lspci -v | grep -i audio              gave me this:

01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
06:00.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile 2496

aplay -l         gave me this:


**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Any help deeply apreciated!thanks

---

### Post by DukeOfDream on 2011-04-06
anyone?

---

### Post by makwana on 2011-04-06
i have some what same problem. in sound preferences hardware column is empty.
in terminal cat: /proc/asound/cards shows No such file or directory
ubuntu-bug audio shows
1507
symptom script /usr/share/apport/symptoms/audio.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport/ui.py", line 54, in thread_collect_info
    package = symb['run'](report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 28, in run
    package, card = soundcard_query(report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 206, in soundcard_query
    for card in open('/proc/asound/cards'):
IOError: [Errno 2] No such file or directory: '/proc/asound/cards'
what could be the reason??

---

### Post by DukeOfDream on 2011-04-06
My only luck was to install the oss(Open Sound System) provided here: [http://www.opensound.com/](http://www.opensound.com/)
then i somewhat have audio...if i run the command "osstest" i get a beautifull sound...I also have sound(a very crappy one) when tried to watch a video on youtube...other than that no sound at all...i tried running some mp3s...the program seems to play them but i do not hear anything...also i cannot control the output since the audio icon shows nothing...if i go to sound prefences, there is nothing shown in the hardware tab(it was showin my Ati hdmi output earlier but i blacklisted it),same in the input tab and last in the output tab it displays dummy output which is selected...any help?do i need a special mixer or something?

---

### Post by DukeOfDream on 2011-04-08
Anyone can give a little help?

---

### Post by lidex on 2011-04-10
> **DukeOfDream said:**
> Anyone can give a little help?

Did you read the thread from the beginning?

---

### Post by DukeOfDream on 2011-04-10
Of course i did...if i haven't read the thread i would post a new thread!plz forgive me for my bad english...The problem is that my card is not shown anywhere except here "lspci -v | grep -i" i added these two lines and followed instructions from multiple threads with no luck...i can post here every guide i used if that helps...

---

### Post by shalamabobbi on 2011-05-25
FYI

My first go round I removed pulseaudio and added alsamixer and envy24 though that search brought up another software labeled with another name which I installed. 

Everything worked fine, stereo good, etc. 

Whether related to this or not I do not know, but the next time I restarted my PC my password no longer worked and I had to do a new clean re-install.

---


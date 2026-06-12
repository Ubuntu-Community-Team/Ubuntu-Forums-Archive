---
title: "headphones and speakers work at same time Ubuntu 8.10"
date: 2009-04-02
forum: Multimedia Software
---

### Post by D3M3NTU on 2009-04-02
Hi.I have installed Ubuntu 8.10 i saw it at a friend and i like it, at first i had problems with wireless connection but i manage to make it work and now i have a new problem.When i plug in the headphones i still hear sound from internal speakers. If i mut the headphones i dont hear sound from speakers and if i mut the master volume same story.

When i type this command in terminal **lspci -v | less** it shows everything about the laptop.I will put here only about the sound card.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
        Subsystem: Micro-Star International Co., Ltd. Device 3fea
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I have a MSI EX600X laptop with 3gb ram, Nvidia 8400M GS 256mb, dual core 2ghz with 2mb cache L2, and i have dolby home theater in laptop too(i read it in the laptop manual plus i have the emblem on him).I hope you can help me with this problem because its fu****g anoying.

Thx and im waiting for a reply with the resolve of my problem.I hope its soon.

---

### Post by DeMus on 2009-04-02
> **D3M3NTU said:**
> Hi.I have installed Ubuntu 8.10 i saw it at a friend and i like it, at first i had problems with wireless connection but i manage to make it work and now i have a new problem.When i plug in the headphones i still hear sound from internal speakers. If i mut the headphones i dont hear sound from speakers and if i mut the master volume same story.

When i type this command in terminal **lspci -v | less** it shows everything about the laptop.I will put here only about the sound card.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
        Subsystem: Micro-Star International Co., Ltd. Device 3fea
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I have a MSI EX600X laptop with 3gb ram, Nvidia 8400M GS 256mb, dual core 2ghz with 2mb cache L2, and i have dolby home theater in laptop too(i read it in the laptop manual plus i have the emblem on him).I hope you can help me with this problem because its fu****g anoying.

Thx and im waiting for a reply with the resolve of my problem.I hope its soon.

I presume you had Windows on this laptop before you started using Ubuntu. With Windows did the speakers switch off when you plugged in the headphones?
If so, it is something related to Ubuntu.

In the top panel you see a loudspeaker icon. Double click it to open the volume control.
Through Edit - Preferences you can choose which controls are visible. Choose the headphones, as well as the master, the PCM and front. I know this is not the solution but through these controls you are able to mute the sound coming from your speakers. Maybe there is some extra software (maybe a driver) which settles this automatically, but I don't know it.

---

### Post by SHENGTON on 2009-04-02
Hello good afternoon. :)

Try to check as well the port if where did you put the heatphones. The socket for the headphone is pink and for the speaker is blue-green. Maybe you just misplugged.

Take care and God bless. :)

---

### Post by D3M3NTU on 2009-04-02
Yes i have windows too ....but i dont wanna use windows no more so i put ubuntu too....and in windows the headphones work just fine....and your solution doesnt work because if i mute one of those options i dont get sound from speakers or headphones.

So i dont know what to do but its realy anoying.I work at a desk office and i cant listen some music without the rest hearing.I Know its an ubuntu problem because i saw it at many people but non of them resolved it.

Hope i will get my problem fixed real soon, i dont wanna give up ubuntu but at this rate with this problem if it persists i think im going back to windows cause i dont have any other choise. :mad::mad: :(

---

### Post by D3M3NTU on 2009-04-02
> **SHENGTON said:**
> Hello good afternoon. :)

Try to check as well the port if where did you put the heatphones. The socket for the headphone is pink and for the speaker is blue-green. Maybe you just misplugged.

Take care and God bless. :)

My headphones color is green...the microphone color is pink and the other is blue. On windows on the green jack its the headphones...but i tryed already and jacked in on everything and still nothing....only when i plug in the green jack i head sound from speakers and headphones...if i put in the rest i dont hear a thing.

---

### Post by bcschmerker on 2009-04-02
> **D3M3NTU said:**
> Hi.I have installed Ubuntu 8.10 i saw it at a friend and i like it, at first i had problems with wireless connection but i manage to make it work and now i have a new problem.When i plug in the headphones i still hear sound from internal speakers. If i mut the headphones i dont hear sound from speakers and if i mut the master volume same story....

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
        Subsystem: Micro-Star International Co., Ltd. Device 3fea
        Flags: bus master, fast devsel, latency 0, IRQ 21
        Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I have a MSI EX600X laptop with 3gb ram, Nvidia 8400M GS 256mb, dual core 2ghz with 2mb cache L2, and i have dolby home theater in laptop too....It may be something inherent to your sound hardware and the Kernel modules that support it.  I recently upgraded my [Everex gPC mid-tower](http://www.everex.com/) to an [Elitegroup GeForce6100SM-M](http://www.ecsusa.com/) ([nVIDIA nFORCE 405](http://www.nvidia.com/) south bridge) with 2.9 GHz [Advanced Micro Devices Athlon X2](http://www.amd.com/) MPU, and the [Realtek ALC-660VD](http://www.realtek.com.tw/) in my rebuilt system has an unusual combination of parameters available to the ALSA Mixer application (/usr/bin/alsamixer), viz.

(1) Master Level and Mute
(2) Headphone Mute
(3) PCM Gain
(4) Front Output and Mute Level (this is what I use for my sidetone settings)
(5) Front Microphone Gain, Mute and 3-stage Boost (I run my headset microphone into this input)
(6) Line In Gain and Mute (2-channel)
(7) CD/DVD In Gain and Mute (2-channel)
(8) Mic Gain, Mute and 3-stage Boost (2-channel; I currently run a Nady DKW-3 into this input)
(9) PC Speaker Gain and Mute
(10) Capture (analog gain)
(11) Digital Capture (gain)
(12) Record Source Select:  Mic, Front Mic, Line In, CD/DVD In

On my Everex, I can shut down the headphones and still have the rear Line Outs operational, but vice versa is not an option at this time due to the way that the HDA nVIDIA Module interacts with the ALC-660VD.  What functions are available to ALSA Mixer for the Intel 82801H sound chip?  This info may help me find a workaround for your situation.

---

### Post by D3M3NTU on 2009-04-02
I will put links with screenshots of my options cause im not that good in linux(i have about 1 month of using linux) to explain correct.

1) : [http://img8.imageshack.us/my.php?image=screenshothbr.png](http://img8.imageshack.us/my.php?image=screenshothbr.png)
2) : [http://img8.imageshack.us/my.php?image=screenshot1rct.png](http://img8.imageshack.us/my.php?image=screenshot1rct.png)
3) : [http://img8.imageshack.us/my.php?image=screenshot2mal.png](http://img8.imageshack.us/my.php?image=screenshot2mal.png)
4) : [http://img8.imageshack.us/my.php?image=volumecontrolhdaintel.png](http://img8.imageshack.us/my.php?image=volumecontrolhdaintel.png)


Hope it will help you so you can help me :( :(

---

### Post by heffo_j on 2009-04-02
Hi there,

I don't want to sound a pessimist but this has been a long term problem with the kernel and the Intel drivers. 

In my case I have learned to live with the speakers not muting with the headphones plugged. In fact there is no difference between the audio out and headphones.

Your card MIGHT have a fix but you will have to do a lot of searching, in particular on the ALSA website. You may get an answer there. They will know if your specific card can be configured.

Best of luck

John

---

### Post by bcschmerker on 2009-04-02
> **heffo_j said:**
> Hi there,

I don't want to sound a pessimist but this has been a long term problem with the kernel and the Intel drivers. 

In my case I have learned to live with the speakers not muting with the headphones plugged. In fact there is no difference between the audio out and headphones.

Your card MIGHT have a fix but you will have to do a lot of searching, in particular on the ALSA website. You may get an answer there. They will know if your specific card can be configured.

Best of luck

JohnI concur with heffo_j.  From [img8.imageshack.us/my.php?image=volumecontrolhdaintel.png](http://img8.imageshack.us/my.php?image=volumecontrolhdaintel.png), it appears that HDA Intel has even fewer parameters available to ALSA than even HDA nVIDIA on my rebuilt Everex.  The fact that your output mutes are acting as though they are ganged, has me stumped for now.  Which reminds me:  I'll need to check with the ALSA Project on an improved set of module Source packages for the Realtek ALC-66x/86x sound chips, as my ALC-660VD will have to hold the fort until ALSA has beta drivers available for the Creative Labs Sound Blaster X-Fi Fatal1ty (PCI Express x1; development started late 2008).

---

### Post by D3M3NTU on 2009-04-02
Thx hope you will find something usefull...cause i will look myself but the fact that im a beginner i dont know what to look exactly for. :(  :((

---

### Post by DeMus on 2009-04-03
> **SHENGTON said:**
> Hello good afternoon. :)

Try to check as well the port if where did you put the heatphones. The socket for the headphone is pink and for the speaker is blue-green. Maybe you just misplugged.

Take care and God bless. :)

On my PC, frontpanel, the green socket is for the headphones, and the pink one for the microphone.

---

### Post by DeMus on 2009-04-03
> **D3M3NTU said:**
> Yes i have windows too ....but i dont wanna use windows no more so i put ubuntu too....and in windows the headphones work just fine....and your solution doesnt work because if i mute one of those options i dont get sound from speakers or headphones.

So i dont know what to do but its realy anoying.I work at a desk office and i cant listen some music without the rest hearing.I Know its an ubuntu problem because i saw it at many people but non of them resolved it.

Hope i will get my problem fixed real soon, i dont wanna give up ubuntu but at this rate with this problem if it persists i think im going back to windows cause i dont have any other choise. :mad::mad: :(

Okay, you hate Windows to, can understand that.
I tried what you wrote on my desktop and all is working fine, so it is not an Ubuntu matter. It's either settings in Ubuntu, or your hardware responds differently than mine.
Let's try to find out:

What settings did you choose in the mixer panel?
Double click the loudspeaker icon so the mixer opens.
Click on File - Change Device
For me it's working with HDA Intel (Alsa mixer) chosen.
Here I get the most controls, which can be switched on/off by means of menu Edit - Preferences.

On which output did you connect your speakers? Are they the front ones? I noticed that the little speakers in the monitor, which are connected to the side output don't mute when I plug in a headphone. The ones on the master output (front output) do mute nicely.

Hope this helps.

---

### Post by D3M3NTU on 2009-04-04
At my laptop the sockets are in front so i have the following colors : green (in windows its the headphones) ping (microphone) and blue (dont know whats with this one never used it). In the sound preferences i have selected HDA Intel (Alsa mixer) i have sound but when i plug in the headphones i have sound in bouth, i tryed with **CAPTURE ALSA PCM ON FRONT:0**same story...in a word with every option from the sound devices the same s**t happens....and i dont wanna use windows anymore because i dont wanna play games and waste my time. I did that a long time so i wanna quit games and in the procces learn linux and stuf like this.

But its a little anoying when i wanna see movies at work because i cant without letting the rest of the world knowing. So if someone has a solution for me i would apreciate.

Thx.

---

### Post by bcschmerker on 2009-05-19
> **DeMus said:**
> On my PC, frontpanel, the green socket is for the headphones, and the pink one for the microphone.My now-[Elitegroup GeForce6100SM-M](http://www.ecsusa.com/)-powered Everex reuses the front audio sub-panel from the VIA 'board originally supplied, which is wired consistent with DeMus' description.  The rear panel under ALSA/PulseAudio, using HDA nVIDIA (sound chip:  [Realtek ALC-660-VD](http://www.realtek.com.tw/)), has three 3.5mm jacks:  Line Out (green), Line In (blue), and Mic In (pink, stereo); the (rear) Line In, (rear) Mic In and Front Mic In have their own sidetone gains and mute switches, with Mic and Front Mic having their own record switches (none for Line In).  Although I ran a Line Out to Line In patch cable for remote recording at [SingSnap](http://www.singsnap.com/), an external mixer can also be patched to the sound chip at the rear panel.

Addendum:  The same is also true of the Realtek ALC-889 on the [Gigabyte MA78GM-S2HP](http://www.gigabyte.com.tw/) (Advance Micro Devices 780G chipset; replaces the Elitegroup/nVIDIA hardware), using HDA ATI SB, with the additions of Rear, Side, Center and LFE gains and mutes to the controls cited above.

---

### Post by The Thug on 2009-08-06
Don't know if anyone has found the solution.

I have the same problem but running 9.04 on my laptop which works perfectly in every other sense.

Can anyone help ?

---

### Post by Ice Dragon on 2009-08-06
I also have the same problem on 9.04, it makes it very hard to watch youtube at work when sound comes through the laptop speakers as well =(

---

### Post by Netik09 on 2009-08-06
I have an MSI GX630 and I have the same problem. I'll keep looking for a solution. I'll post here if I get it to work properly.

---

### Post by The Thug on 2009-08-06
I upgraded ALSA to vers 1.2 and still no luck.

---

### Post by jbruced on 2009-08-06
Interesting,

I have a question for hardware Gurus out there.

Isn't a head phone jack nothing but a simple connection (switch) that connects ground to ground, left channel to a source, right channel to another source, and also activate a cutoff switch for the main audio channel?

There are no components withing headphones to communicate data to a sound card/PC, it just receives analog voltage waves.

Am I missing something?

Bruce

---

### Post by martinbaselier on 2009-08-06
The cutoff switch is done by software on some sound cards. With those cards you either need to set a switch in the mixer applet or you need to add an option to the kernel module for your card.

To check if there's a switch, just turn on all switches in your mixer applet and then test if one of them makes a difference. 

To add an option to the kernel module:

First you have to find out which module you are using:

```
sudo lshw -c multimedia
  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 module=**oss_hdaudio**

```
In my case, I'm using oss_hdaudio (I prefer ossv4  because of the better sound quality.)

To find out the available options:
**modinfo oss_hdaudio**
You will have a different module, so replace oss_hdaudio with the module of your card.

Now create a file to configure the module:
sudo gedit /etc/modprobe.d/soundcard.conf

in the file write something like this:
options oss_hdaudio hdaudio_jacksense=1

Then save and exit.

reload the driver:

modprobe -r yoursouncardmodule
modprobe yoursoundcardmodule


Use a relevant option you found with modinfo and of course the name of the kernel module that's relevant to you.

---

### Post by Netik09 on 2009-08-08
It's not exactly what I was looking for, and it might not work for you guys, but I got sound in my headphones while muting the speakers. 

What I did was install **GNOME ALSA Mixer** through Synaptic Package Manager (*gnome-alsamixer*). In **Gnome Alsa Mixer**, I unchecked 'speaker' located at the bottom. This muted my laptop's speakers but I still get awesome sound from my headphone and line-in jacks.

If I need sound from my speakers, I just check 'speaker' again. It's not awesome, but at least I can use my laptop on campus and not bother anyone with loud music.

I hope it works for you guys too. It would be so cool if I mange to help somebody! :)

*Forgot to mention that I'm using Jaunty Jackalope 9.04 on an MSI GX630.

---

### Post by The Thug on 2009-08-12
> **Netik09 said:**
> It's not exactly what I was looking for, and it might not work for you guys, but I got sound in my headphones while muting the speakers. 

What I did was install **GNOME ALSA Mixer** through Synaptic Package Manager (*gnome-alsamixer*). In **Gnome Alsa Mixer**, I unchecked 'speaker' located at the bottom. This muted my laptop's speakers but I still get awesome sound from my headphone and line-in jacks.

If I need sound from my speakers, I just check 'speaker' again. It's not awesome, but at least I can use my laptop on campus and not bother anyone with loud music.

I hope it works for you guys too. It would be so cool if I mange to help somebody! :)

*Forgot to mention that I'm using Jaunty Jackalope 9.04 on an MSI GX630.

Thanks for help but my version of Alsa Mixer didn't have "speaker" at the bottom.

Probably a soundcard issue, mine being a Realtek ALC 268

---

### Post by Netik09 on 2009-08-12
I'm using 0.9.7

---

### Post by dpkn on 2009-08-12
hi
i just started using ubuntu recently.
when ever i put in my headphone or ext speaker jack my laptop speakers work but headphones or ext speakers dont work any help pls?

---

### Post by Bystroi on 2009-08-22
I got the same issue with my MSI GX700 but I got it fixed my adding a line...
```

options snd-hda-intel model=3stack-6ch

```...to /etc/modprobe.d/alsa-base.conf

I found the full instructions how to do this from here: [http://ubuntuforums.org/archive/index.php/t-713428.html](http://ubuntuforums.org/archive/index.php/t-713428.html)

It still works bit strange though: You got to select headphones manually as they are not detected automagically, and when "headphones" is ticked in Volume Control, you get audio from both speakers and headphones, and when not ticked only from headphones.

At least I can listen to music without forcing everybody else to listen as well. :P

---

### Post by badboyssilim on 2009-10-10
same problem here, trying to shut the laptop mic down...aint't working. i'm using Ubuntu 9.04
Do you  already have a solution? i'm new in linux, for soem minor details it works great.

---


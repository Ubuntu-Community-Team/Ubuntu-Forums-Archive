---
title: "Microphone not working in Ubuntu 10.04"
date: 2010-05-25
forum: Multimedia Software
---

### Post by Ubuntini on 2010-05-25
Hi, i have Ubuntu 10.04 on a HP Pavillion DV6 laptop and the internal microphone does not work. All the other stuff works out of the box, sound, wireless and camera, but not this. I have put it upto the max in pulseaudio. It worked in 9.10 though :(

---

### Post by adam99x on 2010-05-25
Have you gone into the Ubuntu Software Center and downloaded the Generic Sound Card <Allows you to select the default ALSA sound card>.  I went nuts last after installing 10.04... called my cousin on skype and i could hear him just fine, but couldn't talk back.  after getting that Generic Sound Card, i was able to talk to him.  Give it a shot.

---

### Post by ndo on 2010-06-05
There IS no "Generic Sound Card," be specific.

---

### Post by lidex on 2010-06-05
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by ayc on 2010-06-07
I am using Dell Vostro v13 and I had  the same problem. I was looking for a solution everywhere. The previous post #4, which is also the most simple and short solution among the other solutions on other forums, worked perfectly for me. 
Thanks.

---

### Post by flying_174 on 2010-06-09
This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There should be 2 sliders, and a input tester at the bottom. Speak into the mic. you will know if it is working. If it is not, slide the slider that says Front Left, to 0%. Now speak. If the mic works here your good to go. 

Hope this helps.

---

### Post by saviouz on 2010-06-15
> **flying_174 said:**
> This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There should be 2 sliders, and a input tester at the bottom. Speak into the mic. you will know if it is working. If it is not, slide the slider that says Front Left, to 0%. Now speak. If the mic works here your good to go. 

Hope this helps.
This worked for me too! I'm using a Compaq Mini 700EL

---

### Post by DavidG24 on 2010-07-19
> **flying_174 said:**
> This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There should be 2 sliders, and a input tester at the bottom. Speak into the mic. you will know if it is working. If it is not, slide the slider that says Front Left, to 0%. Now speak. If the mic works here your good to go. 

Hope this helps.

hey mate,

just wanted to give you a big thumbs up - I'm new to Linux and was stoked at finding a simple easy fix for this issue - Cheers

---

### Post by max_max_mir on 2010-08-08
Before you mess with all that and install new programs, make sure you check the following (which was the problem I had on my Gateway MT3421).

1. Go to System -> Preferences -> Sound
2. Click on the Input tab
3. Make sure Mute is unchecked (it is checked by default, and this prevents the mic from working).

---

### Post by tonymwangi on 2010-08-19
**Re: Microphone not working in Ubuntu 10.04** 			
 			 			 		   		 		 		Before you mess  with all that and install new programs, make sure you check the  following (which was the problem I had on my Gateway MT3421).

1. Go to System -> Preferences -> Sound
2. Click on the Input tab
3. Make sure Mute is unchecked (it is checked by default, and this prevents the mic from working).

Before installing/making changed to your computer, better check this first. It worked for me

---

### Post by lidex on 2010-08-19
> **tonymwangi said:**
> **Re: Microphone not working in Ubuntu 10.04** 			
 			 			 		   		 		 		Before you mess  with all that and install new programs, make sure you check the  following (which was the problem I had on my Gateway MT3421).

1. Go to System -> Preferences -> Sound
2. Click on the Input tab
3. Make sure Mute is unchecked (it is checked by default, and this prevents the mic from working).

Before installing/making changed to your computer, better check this first. It worked for me

Good advice for a first step. Hopefully those who have reached this point have gone through the troubleshooting guides and eliminated all the basic steps, such as this. Another thing to try is this:
```
ubuntu-bug audio
```
Reference:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by bugfinder on 2010-08-22
> **flying_174 said:**
> This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There should be 2 sliders, and a input tester at the bottom. Speak into the mic. you will know if it is working. If it is not, slide the slider that says Front Left, to 0%. Now speak. If the mic works here your good to go. 

Hope this helps.
Hi fly_174, i have installed Ubuntu 10.04 on my computer. Every thing works fine except the mic. I'm not expert in Linux and till now all through my life i have been working on Windows. But i just made my mind to master myself with Linux, i have Ubuntu 10.04 Lynx desktop version for my computer (Client computer) and Ubuntu 10.04 Server version for my Web developing server. I'm completely loving Linux and feel so easy using the commands and using it. I have successed installing all the softwares that i need on my client computer except the Mic. I have gone through so many forum and tried so many things, but couldn't successed. I have just gone through your form and in it you mention to install Default Sound card and Pulse Audio Volume Control. What is it ..?? is it hardware which i have to install or Software to install from Applications >>> Ubuntu software center ..??? Can you please explain or some link to find some instructions to set up mic. Coz Mic is very important to me to use on Skype. I deeply appreciate any help or suggestions on this. Thanks again for your time in Reading my request....:popcorn:

---

### Post by bugfinder on 2010-08-22
an other updates guys i have in the alsamixer from the previous post and no result form it. its still not working .. i have attached the picture of my sound card. 

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: SigmaTel STAC9227                              F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: 0.00]                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;    Mic In    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;MM&#9474;              &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;     100    100<>97  100<>99    0<>0              0<>0      0        0        &#9474;
&#9474;  < Master >Headphon   PCM     Front   Front Mi Surround  Center    LFE   



any suggestions ???

---

### Post by lidex on 2010-08-22
> **bugfinder said:**
> an other updates guys i have in the alsamixer from the previous post and no result form it. its still not working .. i have attached the picture of my sound card. 

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; AlsaMixer v1.0.22 &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: SigmaTel STAC9227                              F2:  System information &#9474;
&#9474; View: F3:[Playback] F4: Capture  F5: All             F6:  Select sound card  &#9474;
&#9474; Item: Master [dB gain: 0.00]                         Esc: Exit               &#9474;
&#9474;                                                                              &#9474;
&#9474;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      >
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;              &#9474;  &#9474;     &#9474;  &#9474;     &#9474;  &#9474;      &#9474;
&#9474;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;    Mic In    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9474;
&#9474;     &#9474;OO&#9474;     &#9474;OO&#9474;              &#9474;MM&#9474;              &#9474;MM&#9474;     &#9474;MM&#9474;     &#9474;MM&#9474;      &#9474;
&#9474;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9474;
&#9474;     100    100<>97  100<>99    0<>0              0<>0      0        0        &#9474;
&#9474;  < Master >Headphon   PCM     Front   Front Mi Surround  Center    LFE   



any suggestions ???

Yes - see post #11

---

### Post by jimboat on 2010-08-27
I had the same problem after upgrading to 10.04. Solution for me turned out to be:

[LIST=1]
[*]Open PulseAudio Volume Control (obtain from software centre if not installed).
[*]Input devices tab.
[*]Select: Show all except monitors.
[*]Change the port to Microphone 1.
[*]Sliders left at 100%.
[/LIST]
(This was set to line in which you would think was correct, but for some reason wasn't with my headphone/microphone plugged into the sound card as normal.)

---

### Post by Behemoth0089 on 2010-08-27
> **tonymwangi said:**
> **Re: Microphone not working in Ubuntu 10.04**             
                                                                Before you mess  with all that and install new programs, make sure you check the  following (which was the problem I had on my Gateway MT3421).

1. Go to System -> Preferences -> Sound
2. Click on the Input tab
3. Make sure Mute is unchecked (it is checked by default, and this prevents the mic from working).

Before installing/making changed to your computer, better check this first. It worked for me

This works for me, but after a couple times I tried. Why? well, I unchecked the Mute but when I closed and re open the Sound, it was Muted again, so I changed the line from where the mic was trying to get the audio, and then it worked.
So make sure you got the right line selected before doing anything funny.

---

### Post by martysolutions on 2010-09-28
> **jimboat said:**
> I had the same problem after upgrading to 10.04. Solution for me turned out to be:

[LIST=1]
[*]Open PulseAudio Volume Control (obtain from software centre if not installed).
[*]Input devices tab.
[*]Select: Show all except monitors.
[*]Change the port to Microphone 1.
[*]Sliders left at 100%.
[/LIST]
(This was set to line in which you would think was correct, but for some reason wasn't with my headphone/microphone plugged into the sound card as normal.)
That worked out for me too, on Lenovo T61 14.1'. Instead Microphone 1, I choose Microphone 2.

---

### Post by riorikka on 2011-02-03
I have the same problem but nothing of the above worked for me. Any other ideas?? I am getting crazy with this. Please help!

---

### Post by dr.twinny on 2011-02-08
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Thanks alot. Also have a HP DV6. Seemed my internal mic was muted for some reason weird.

---

### Post by lamachine on 2011-03-04
To get work the micro on Toshiba satellite L650 I've added ubuntu audio repository and upgraded audio drivers.
 

 sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 
sudo apt-get update 
sudo apt-get install linux-alsa-driver-modules-$(uname -r) 

 Micro and skype work like a charm.

---

### Post by celestialamadeus on 2011-04-11
System : Lenovo Y530 Ideapad
OS: Ubuntu 10.04

Problem: Microphone (on Skype or Yahoo Messenger) not working (but speakers' output was normal)

How the problem was fixed :  Go to System --> Preferences --> Sound. Then Follow these steps:

1. Click on 'Hardware' Tab. 

2. Select profile in 'Settings for the selected device:' as Analog Stereo Duplex. 

3. Click on 'Input' Tab and make sure to uncheck 'Mute' box if it's checked and increase Input volume if it's 0%. 

4. Click on 'Output' to make sure the settings are ok and a device for sound output is chosen. 

It worked for me. Hope it works for you too! Cheers!

P.S. I am new to this forum and am not an expert. So pardon me if I was unable to explain the steps properly.

---

### Post by abhishek1912 on 2011-05-30
@lidex: Been following you on a lot of mic-related threads. Thanks!
The following worked for me:
Code:
options snd-hda-intel model=hp-dv5 enable_msi=1

This worked for me ofcourse except model=sony-vaio

Can you tell me what exactly did this do?

Thanks for all the help

---

### Post by lidex on 2011-05-31
Manufacturers utilize the same codec chips differently so not all of them wire the pins the same. Telling alsa the correct model allows it to route the audio for that specific configuration. The MSI(message signaled interrupt)option changes the device interrupt handling. For more detailed info look in your /usr/share/doc/alsa-base directory.

---

### Post by gothrog on 2012-06-27
Ok... so I did all of the stuff above and I "do" hear my recorded voice through "ubuntu-bug audio".

For some reason other applications are having an issue recording.  It can open the device to record, but when it tries to record it fails.

I have run it as root and it has not made a difference.

Having issues with trying to record in Audacity and a speech recognizer.

Are there other programs that can record and playback that are known to work?

I didn't hear any actual playback in pulseaudio, not sure if it is even supposed too.

If anyone has any ideas on what is wrong please let me know.

---

### Post by tarahmarie on 2012-06-28
[http://thecowgirlcoder.com/2012/06/28/how-to-get-the-microphone-working-in-skype-with-kubuntu-12-04-and-likely-with-previous-versions/](http://thecowgirlcoder.com/2012/06/28/how-to-get-the-microphone-working-in-skype-with-kubuntu-12-04-and-likely-with-previous-versions/)

---

### Post by sirio400516x on 2013-02-18
> **lidex said:**
> Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

That worked exactly as expected. I wrote
```
options snd-hda-intel enable_msi=1 
```
to the alsa-base.conf file and got my microphone working.

Many thanks!!

---


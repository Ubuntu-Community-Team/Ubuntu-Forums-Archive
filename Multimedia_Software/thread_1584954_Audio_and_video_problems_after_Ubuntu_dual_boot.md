---
title: "Audio and video problems after Ubuntu dual boot"
date: 2010-09-29
forum: Multimedia Software
---

### Post by rmcellig on 2010-09-29
I just installed Ubuntu 10.04 dual boot on my iMac running OS 10.6.4

iMac info:

Model Name:	iMac
Model Identifier:	iMac6,1
Processor Name:	Intel Core 2 Duo
Speed:	2.16 GHz
Number Of Processors:	1
Total Number Of Cores:	2
L2 Cache:	4 MB
Memory:	2 GB
Bus Speed:	667 MHz


Video is NVIDIA GeForce 7300 GT

Right away I noticed that I was unable to play videos properly. VLC player wouldn't even acknowledge that a video was being played as all. Movie player played a video but when I went to go full screen Movie player quit. Those are the video problems I noticed. I installed the Restricted Ubuntu extras, as well s some other things I forget at the moment. Is there something I can put in the terminal that will output what I have installed so that I can post it in this thread?

Audio is: Intel High Definition Audio

I found out that I am unable to record anything. I tried recording some sound from a radio I have hooked up to my Mac and all I get is white noise. If I choose Microphone in Sound Preferences, that works fine. It is the Lin In that doesn't work. Let me know if there is additional information you need that I can post to this thread.

---

### Post by peptobismal on 2010-09-29
Um, I am on ATI but I do know that there are proprietary drivers for both nVidia and ATI GPUs. Um, can you enable window effects? Check Hardware Drivers, too, and see if there's a proprietary driver to install. These normally are disabled for me after every new install or update.

---

### Post by rmcellig on 2010-09-29
Hi peptobismal

I have the nvidia  drivers installed. Compiz works fine. I only have Wobbly windows active for now.

---

### Post by rmcellig on 2010-09-30
Another thing I forgot to mention is that I even tried with the live Ubuntu CD and still could not record and audio via the Line in. The Mic option worked fine when I recorded from the built in iMac Mic but line in? No dice.

I really need to resolve this because although I can always record from my Mac using OS X, I really love Ubuntu so I would like to spend almost all of my computer time in this environment.

---

### Post by rmcellig on 2010-09-30
This is the info regarding the Audio card if this helps any. I hope so. :)

ubuntu@ubuntu:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A

---

### Post by lidex on 2010-09-30
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by rmcellig on 2010-09-30
Here you go:

[http://www.alsa-project.org/db/?f=9f89d6bf768f2be17c5d40a67869e07064e0f845](http://www.alsa-project.org/db/?f=9f89d6bf768f2be17c5d40a67869e07064e0f845)

---

### Post by rmcellig on 2010-09-30
I sure hope that this information will help me resolve my problems. It looks very detailed.

---

### Post by lidex on 2010-09-30
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=imac24 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by rmcellig on 2010-09-30
I tried that and still nothing. Attached are my settings and alsa base.conf file. Let me know if there is some kind of test I can do regarding the line in.

---

### Post by rmcellig on 2010-10-02
I just did a clean install of Ubuntu 10.10 and I am still having problems recording from Line in in the Sound Preferences. This is the number one thing I really need to get working. I only have two issues left. I am not able to use my internal isight camera in Ubuntu, and the recording from my radio that is hooked up to my computer. :(

---

### Post by lidex on 2010-10-02
Did you try toggling the input sources in alsamixer. Try setting the others to 'Line'

---

### Post by rmcellig on 2010-10-02
If possible can you post a screenshot of what the alsamixer settings should look like. Thanks!!

---

### Post by lidex on 2010-10-02
> **rmcellig said:**
> If possible can you post a screenshot of what the alsamixer settings should look like. Thanks!!

Actually I was looking at the screen you posted previously. In alsamixer/capture devices scroll right using -> key and toggle value with up/down keys. You'll need to experiment a little.

---

### Post by rmcellig on 2010-10-02
Thanks I will try that again. I'm in my Mac partition now. I really wished and hoped that everything would just work in the Ubuntu partition because I really like staying in Ubuntu, I guess like you, I am an Ubuntu addict and really enjoying it. It's just that when you expect things to work, things that should work like the isight camera and plain recording, I am left with a bitter taste.

---

### Post by lidex on 2010-10-03
> **rmcellig said:**
> Thanks I will try that again. I'm in my Mac partition now. I really wished and hoped that everything would just work in the Ubuntu partition because I really like staying in Ubuntu, I guess like you, I am an Ubuntu addict and really enjoying it. It's just that when you expect things to work, things that should work like the isight camera and plain recording, I am left with a bitter taste.
Yeah, unfortunately/fortunately with open source things don't always go that way because money moves the world and there is a financial reward in closed-source. So we putter along with the contributions in time and effort of unpaid volunteers who all wish that things would 'just work', but understand that **we** have to make it work. We are a community - join us.;)

---

### Post by rmcellig on 2010-10-03
Very good point! I never thought of it that way. So I should just keep pluggin along to see if I can solve the problem. Are there other sources I should explore to help me? Is there an Alsa forum. For example? 

I would like to be able to actually talk with someone who could guide me with the iSight and line in problem.

Maybe there is a line in test I could do or maybe there is a way to capture through a log file or something similar so that I could post it in a thread?

---

### Post by lidex on 2010-10-03
How many audio jacks do you have and have you tried others for input? Alsa could have them mixed up.

Try installing the latest alsa modules. First you'll need to add the repository:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
apt-get install linux-alsa-driver-modules-$(uname -r)
```
You'll need to reboot to see changes. It may reset your levels, etc, so recheck all your settings.

---

### Post by rmcellig on 2010-10-03
I will do that and ost back. When you say audio jacks, do you mean the ones on the iMac? I think there is only one In and one out jack.

---

### Post by rmcellig on 2010-10-10
Sorry I haven't had a chance to post back. I have been working in my Mac partition all week. 

On my iMac I have one mic jack and one line in jack. You suggested I plug something else directly into the line in jack and see if that works?

You also mentioned that Alsa may be mixing up the line in, in Ubuntu. I am really looking forward to solving my problem because I would like to spend most of my time in my Ubuntu partition. Hopefully this week I will have a chance to try out what you suggested!! :)

---

### Post by lidex on 2010-10-10
How about some updated info? 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by rmcellig on 2010-10-10
Here you go:

[http://www.alsa-project.org/db/?f=37dce9a3552ee3679cfaaafeebe9a3d5dcba5bc2](http://www.alsa-project.org/db/?f=37dce9a3552ee3679cfaaafeebe9a3d5dcba5bc2)

I'm back in my Ubuntu 10.10 partition now.

---

### Post by lidex on 2010-10-10
Check the Intel_Imac Wiki:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)
And have you looked at the Apple support forum:
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by rmcellig on 2010-10-10
Thanks! I never thought of going to the Apple support forum. I will post something there.

---

### Post by rmcellig on 2010-10-11
Here is a screenshot of my settings. What does Rec. mean?

Do my settings look OK?

Anything else I should look at?

I left a message on the Apple forum, and also checked out the Intel iMac wiki.

The last input source in the picture is actually selected.

---

### Post by rmcellig on 2010-10-11
I have more information that may help in solving my Line In problem.

My radio is an old Aiwa 945 circa 1980. It has line in and line out RCA jacks (red and white jacks for each). I am going to try and plug the radio directly into the line in input jack on he back of my iMac just to test. Which cable  from which jack from the radio goes into the input jack on the iMac? I have an RCA to pin adapter so that it will fit into the iMac sound in jack.

What tests would you recommend I try?

---

### Post by lidex on 2010-10-11
> **rmcellig said:**
> I have more information that may help in solving my Line In problem.

My radio is an old Aiwa 945 circa 1980. It has line in and line out RCA jacks (red and white jacks for each). I am going to try and plug the radio directly into the line in input jack on he back of my iMac just to test. Which cable  from which jack from the radio goes into the input jack on the iMac? I have an RCA to pin adapter so that it will fit into the iMac sound in jack.

What tests would you recommend I try?

You'll want the line out from the radio into the line input on the comp. Get some sound on the radio and open 'sound preferences'. Select the correct device in the 'hardware tab' and make sure you have selected a profile with analog-stereo-input or stereo-duplex. Look on the input tab to see input level.

---

### Post by rmcellig on 2010-10-12
Here is something interesting. On my PC (which does not work either regarding Line  in with Ubuntu), I booted up from the Fedora 13 live CD and the Line in worksgreat. I get movement on the audio bar in Sound  preferences. What is the difference between Fedora and Ubuntu?  

Where should I go from here? Startup my iMac from the  Fedora Live  CD and see what happens?

---

### Post by rmcellig on 2010-10-13
After trying Kubuntu  live CD, Fedora live CD, and booting from my Ubuntu partition on my iMac, I am convinced that there is no solution at all to the problems I am having recording from Line In. Using the same radio hooked up to an old Dell PC which I am selling, recording works fine. I can see the audio signal when I go to sound preferences and click on the Input tab. Works great.

For some reason  I beleive that Ubuntu just isn't compatible with the sound card in the iMac. This is too bad because I was really hoping that I could use Ubuntu dual boot on my Mac. Running Ubuntu in emulation works fine using VMware Fusion but dual boot really sucks. Unless I hear back from someone who actually is running Ubuntu dual boot on an imac and can record from the Line In, my hope of ever finding an answer is quickly slipping away and for me, that is pretty sad because I love using Linux and really wanted it to work for what I wanted to do. :(

---

### Post by rmcellig on 2010-10-13
You will notice from the screenshots that the sound card is different when running Ubuntu in emulation than it is when running Ubuntu dual boot. Could this be the problem? Is there a way to have the same sound card appear when running Ubuntu dualboot or is there another option?

---


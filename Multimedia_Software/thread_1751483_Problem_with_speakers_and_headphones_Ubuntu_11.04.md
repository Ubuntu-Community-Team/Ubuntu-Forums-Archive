---
title: "Problem with speakers and headphones Ubuntu 11.04"
date: 2011-05-06
forum: Multimedia Software
---

### Post by DrAuggin on 2011-05-06
I'm having problems with my sound, and it seems as if I'm not the only one. When using Ubuntu, (I have it dual-installed with Vista) and trying to listen to music on headphones, the internal speakers don't mute when I plug my headphones in. I am using a Compaq Presario CQ5112F desktop PC. When I looked at the sound card, it said Realtek High Definition Speakers, and the driver name is RTKVHDA.sys , but I don't know it any of that helps. I would really just like to know how to mute the speakers only when the headphones are plugged in. Thanks.

---

### Post by lidex on 2011-05-06
You're fired! Oops, sorry, I was channeling Donald Trump :lol:

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by biano on 2011-05-09
Hi,
I have the same problem with an HP Compaq dx2300.
Here you have the link for my audio configuration:
[http://www.alsa-project.org/db/?f=58b05a3fc8d9a899608714675a6781f753125daf](http://www.alsa-project.org/db/?f=58b05a3fc8d9a899608714675a6781f753125daf)
I'll apreciate any help.
Thank you!

---

### Post by lidex on 2011-05-09
@biano
You need to find the correct model switch for your pin configuration.Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
After the = you will add one of these model names (left column):
```
ALC882/883/885/888/889
======================
  3stack-dig	3-jack with SPDIF I/O
  6stack-dig	6-jack digital with SPDIF I/O
  arima		Arima W820Di1
  targa		Targa T8, MSI-1049 T8
  asus-a7j	ASUS A7J
  asus-a7m	ASUS A7M
  macpro	MacPro support
  mb5		Macbook 5,1
  macmini3	Macmini 3,1
  mba21		Macbook Air 2,1
  mbp3		Macbook Pro rev3
  imac24	iMac 24'' with jack detection
  imac91	iMac 9,1
  w2jc		ASUS W2JC
  3stack-2ch-dig	3-jack with SPDIF I/O (ALC883)
  alc883-6stack-dig	6-jack digital with SPDIF I/O (ALC883)
  3stack-6ch    3-jack 6-channel
  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
  6stack-dig-demo  6-jack digital for Intel demo board
  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
  acer-aspire	Acer Aspire 9810
  acer-aspire-4930g Acer Aspire 4930G
  acer-aspire-6530g Acer Aspire 6530G
  acer-aspire-7730g Acer Aspire 7730G
  acer-aspire-8930g Acer Aspire 8930G
  medion	Medion Laptops
  medion-md2	Medion MD2
  targa-dig	Targa/MSI
  targa-2ch-dig	Targa/MSI with 2-channel
  targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
  laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
  lenovo-101e	Lenovo 101E
  lenovo-nb0763	Lenovo NB0763
  lenovo-ms7195-dig Lenovo MS7195
  lenovo-sky	Lenovo Sky
  haier-w66	Haier W66
  3stack-hp	HP machines with 3stack (Lucknow, Samba boards)
  6stack-dell	Dell machines with 6stack (Inspiron 530)
  mitac		Mitac 8252D
  clevo-m540r	Clevo M540R (6ch + digital)
  clevo-m720	Clevo M720 laptop series
  fujitsu-pi2515 Fujitsu AMILO Pi2515
  fujitsu-xa3530 Fujitsu AMILO XA3530
  3stack-6ch-intel Intel DG33* boards
  intel-alc889a	Intel IbexPeak with ALC889A
  intel-x58	Intel DX58 with ALC889
  asus-p5q	ASUS P5Q-EM boards
  mb31		MacBook 3,1
  sony-vaio-tt  Sony VAIO TT
  auto		auto-config reading BIOS (default)

```
Your codec is ALC888. No space between the = and model name.
Reload alsa after each change and only one at a time please.
```
sudo alsa force-reload
```

EDIT: for others use this command to find your codec:
For intel HDA
```
head -n 1 /proc/asound/card*/codec#*

```
For AC'97:
```
head -1 /proc/asound/card0/codec97#0/ac97#0-0 
```
To find the model options for your codec:
```
zless /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz
```

---

### Post by JasonGriffee on 2011-05-13
I am also having this sound issue, on a ASUS k50IJ notebook computer. What course of action should I pursue?

---

### Post by thuci on 2011-05-13
I also have the same problem my laptop is TOSHIBA Satellite L655

---

### Post by lidex on 2011-05-13
@JasonGriffee
Use the procedure I posted above. For your machine:
```
options snd-hda-intel model=auto
```

@thuci
For yours:
```
options snd-hda-intel model=thinkpad
```

---

### Post by teutara on 2011-05-14
Hi there,

I did the exact same as you described, but no result. My rig is dell 4030. 
Thank you in advance..

---

### Post by lidex on 2011-05-14
> **teutara said:**
> Hi there,

I did the exact same as you described, but no result. My rig is dell 4030. 
Thank you in advance..

Another megathread?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Yellow Pasque on 2011-05-14
> Another megathread?
I love megathreads, especially when there's about 10 people without avatars/sigs and they don't provide any or useless information.

---

### Post by lidex on 2011-05-14
> **Temüjin said:**
> I love megathreads, especially when there's about 10 people without avatars/sigs and they don't provide any or useless information.

:lol:

---

### Post by JasonGriffee on 2011-05-14
> **lidex said:**
> 
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

It gave me this:
[http://pastebin.com/5fLz4vr5](http://pastebin.com/5fLz4vr5)

I still hear audio out of internal speakers when headphones are plugged in.

---

### Post by sent17inel on 2011-05-15
[http://www.alsa-project.org/db/?f=3fa114a06ebf37cac87d97efb39b2a6083743110](http://www.alsa-project.org/db/?f=3fa114a06ebf37cac87d97efb39b2a6083743110)

what do you got for me?

---

### Post by lidex on 2011-05-15
> **JasonGriffee said:**
> It gave me this:
[http://pastebin.com/5fLz4vr5](http://pastebin.com/5fLz4vr5)

I still hear audio out of internal speakers when headphones are plugged in.

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by JasonGriffee on 2011-05-15
Didn't work, still comes out when headphones are in.

---

### Post by sent17inel on 2011-05-15
> **JasonGriffee said:**
> Didn't work, still comes out when headphones are in.


I feel your pain jason.  :/

---

### Post by lidex on 2011-05-15
Let me address one thing I'm pretty sure of here, sent17inel:
Try changing this line in alsa-base.conf:
```
options snd-hda-intel model=thinkpad
```
to
```
options snd-hda-intel model=ideapad
```

---

### Post by sent17inel on 2011-05-15
> **lidex said:**
> Let me address one thing I'm pretty sure of here. sent17inel:
Try changing this line in alsa-base.conf:
```
options snd-hda-intel model=thinkpad
```
to
```
options snd-hda-intel model=ideapad
```


A little better. Going through the headphones and speakers now. Before it was only going through my speakers.

---

### Post by lidex on 2011-05-15
> **JasonGriffee said:**
> Didn't work, still comes out when headphones are in.

Try toggling this element in alsamixer:
```
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
```

There is a bug filed on this machine.
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/565685](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/565685)

---

### Post by JasonGriffee on 2011-05-15
> **lidex said:**
> Try toggling this element in alsamixer:
```
Simple mixer control 'Independent HP',0
  Capabilities: enum
  Items: 'OFF' 'ON'
  Item0: 'OFF'
```There is a bug filed on this machine.
[http://www.google.com/search?q=asus+k50ij&sitesearch=ubuntuforums.org](http://www.google.com/search?q=asus+k50ij&sitesearch=ubuntuforums.org)

I don't know how to do that.

---

### Post by sent17inel on 2011-05-15
Any luck figuring out mine? I know have sound coming out of both my headphones and laptop speakers.

---

### Post by lidex on 2011-05-15
Either of these...
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by lidex on 2011-05-15
> **sent17inel said:**
> Any luck figuring out mine? I know have sound coming out of both my headphones and laptop speakers.

Try switching/toggling the 'Connector' on output tab of 'Sound Preferences'.

Post an updated alsa-info please.

---

### Post by JasonGriffee on 2011-05-16
> **lidex said:**
> Either of these...
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

The reg. alsamixer's headphone setting was muted/ unchangeable. When I clicked to enable independent hp in gnome alsa, it gave error in terminal. something about not knowing what to do.

---

### Post by Qwerty_ls on 2011-05-17
I had the same problem and I managed to solve it using alsamixer.
I launched the alsamixer via shell, then I moved the cursor over the third column named "Headphone". Just over the column name, in the square I found "MM". I press the "m" button and the "MM" switched to "00". Now when I plug my headset the speakers are silenced. I attached the screenshot of the alsamixer.

I hope this can help someone.

---

### Post by ExOH on 2011-05-17
> **JasonGriffee said:**
> I am also having this sound issue, on a ASUS k50IJ notebook computer. What course of action should I pursue?


I have the same rig, just got it recently and am having the same problem. specifically with sony headphones. is yours a dual boot?

---

### Post by JasonGriffee on 2011-05-17
> **ExOH said:**
> I have the same rig, just got it recently and am having the same problem. specifically with sony headphones. is yours a dual boot?
Yes, i found unused space on my drive and stuck it there. I'm using standard headphone jack.

> **Qwerty_ls said:**
> I had the same problem and I managed to solve it using alsamixer.
I launched the alsamixer via shell, then I moved the cursor over the  third column named "Headphone". Just over the column name, in the square  I found "MM". I press the "m" button and the "MM" switched to "00". Now  when I plug my headset the speakers are silenced. I attached the  screenshot of the alsamixer.

I hope this can help someone.
Didn't work.

---

### Post by lidex on 2011-05-17
This was supposed to be addressed in 1.0.23 alsa
You saw this:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/565685](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/565685)

---

### Post by JasonGriffee on 2011-05-18
> **lidex said:**
> This was supposed to be addressed in 1.0.23 alsa
You saw this:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/565685](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/565685)

I just clicked and read it.

---

### Post by JasonGriffee on 2011-05-18
[QUOTE=Benjamin Kraus]
                 These instructions got the headphones  jacked working like I wanted: When I plug in my headphones the speakers  automatically mute, and when I unplug them the speakers come back on.
 1) Open gnome-volume-control
2) Click on the "Output" tab.
3) Change "Connector" to "Analog Headphones"
4) Open gnome-alsamixer
5) Turn the "Front" channel up to maximum volume.
6) Close gnome-alsamixer
7) Use gnome-volume-control to adjust volume/mute/unmute.
 If you want both headphones and speakers, open gnome-alsamixer and unmute the "Front" channel.
[/QUOTE]


I followed this and it worked.

---

### Post by Walkingcedar on 2011-05-18
Jason, thank you for your posting above. I followed it. Though I do not have a setting for "Analog Headphones", I used the "Analog Output" setting, instead, then installed alsamixer, and manipulated the settings from there. I am not sure this worked or why the gnome volume control (Ubuntu 11.04 Natty) didn't work by itself, without the alsamixer. The first time I hooked up the headset, I used the gnome controls, had it set on OUtput (as mentioned above), and it worked fine. Just for a moment, I changed it to "Analog Speakers". The sound went away. I tried to switch it back to "Analog Output"; the sound in the headset never returned, EVER. Your idea worked. Thank you so much.

---

### Post by ChrisKu on 2011-05-26
I am also having a problem with getting sound from my headphones after installing Ubuntu 11.04: No sound at all! I tried following the procedure at the beginniing of the thread without success. My information is located here: [FONT=monospace]

[http://www.alsa-project.org/db/?f=00a8b4893e22fb0793a491f76df6674197ee573d](http://www.alsa-project.org/db/?f=00a8b4893e22fb0793a491f76df6674197ee573d)

Would be grateful for a helping hint.

Thanks a lot, Chirs

Strangely enough when I boot my system from an Ubuntu 11.04 LiveCD all works fine
[/FONT]

---

### Post by pediatracancun on 2011-05-26
I have an Acer notebook Aspire 5253-B2820 and have the same problem. I run the proposed command and uploaded here: [http://www.alsa-project.org/db/?f=22250bbb81caee172fc92e98cafaca3ba12ec706](http://www.alsa-project.org/db/?f=22250bbb81caee172fc92e98cafaca3ba12ec706) 
Is there a form to fix this problem?
Best regards from Cancun

Juan Pedro Sanchez:KS

---

### Post by ChrisKu on 2011-05-27
Any ideas? My feeling is that I have worked through every sound problem solving guideline - without success. Everything seems to be ok except for the fact that there is no sound to be heard. Really frustrating....:(
 
Hopefully somedbody can help...
 
Chris

---

### Post by lidex on 2011-05-27
> **ChrisKu said:**
> I am also having a problem with getting sound from my headphones after installing Ubuntu 11.04: No sound at all! I tried following the procedure at the beginniing of the thread without success. My information is located here: [FONT=monospace]

[http://www.alsa-project.org/db/?f=00a8b4893e22fb0793a491f76df6674197ee573d](http://www.alsa-project.org/db/?f=00a8b4893e22fb0793a491f76df6674197ee573d)

Would be grateful for a helping hint.

Thanks a lot, Chirs

Strangely enough when I boot my system from an Ubuntu 11.04 LiveCD all works fine
[/FONT]

You have a model option in alsa-base.conf that does not belong there. Try changing it to auto. 
Using a Terminal="Applications-> Accessories-> Terminal"
Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Change this line
```
 options snd-hda-intel model=alc889a 
```
To look like this
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```

---

### Post by ChrisKu on 2011-05-28
Lidex, thank your for your great support! I followed your procedure, unmuted all Alsamixer channels and set them to max volume - except for the S/PDIF chnannels which I muted. The result was....no sound :(. Then I switched the channel Independent HP off and the sound worked when playing a file with  aplay.

Now the following problems remain: After rebooting the alsamixer settings are reset and I have to redo the changes in alsamixer to get sound. The same happend when I started Banshee the first time but on later occassions Banshee did not change the seetings..

Searching around in this forum I found another hint by Lidex:
> **lidex said:**
> The command to save alsamixer settings is:
```
sudo alsactl store 0
```If that doesn't work, open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```Scroll down to this line:
```
load-module module-device-restore
```Comment it out so it looks like this:
```
#load-module module-device-restore
```Save. Close. Logout/in.

For me the editing of the default.pa file solve the problem.

Thanks to lidex!

---

### Post by Calibwam on 2011-06-05
Hi. I had the usual problem developing where I have a small problem (microphone not working), escalating to a big problem (almost every sound thing disappears), following a lot of guides to fix most of the problems, and here I am.

Right now, I don't get any sound out of my internal speakers, though I have sound in my headphones, and through HDMI (I have two soundcards). [Here's the alsa info.]("http://www.alsa-project.org/db/?f=80342b05b05531deacd760850c20778744771c05")

I will be forever thankful if someone could help me! And maybe even get the microphone to work as well :)

---

### Post by zlovkvetinaci on 2011-06-24
Having similar problem on my laptop. :( I get sound only when I plug in speakers or headphones. It worked just fine on old 8.4.
My laptop is Prestigio... so I really dont know what model I should  use in that alsa-base thingy.
[http://www.alsa-project.org/db/?f=fca85e47ba7c582f589d26787dd84af3611da1e0](http://www.alsa-project.org/db/?f=fca85e47ba7c582f589d26787dd84af3611da1e0)

---

### Post by sabbir2world on 2011-06-27
Boss, It's a desktop issue

Boss, I can hear sound from my headphone. But while I speak to skype it doesn't respond. My voice doesn't pass from my microphone. Please gimme solution...:(:(

Here's my alsa details:

[http://www.alsa-project.org/db/?f=41438f5d77f0a5d48aff167a8e5849dee0aab1a6](http://www.alsa-project.org/db/?f=41438f5d77f0a5d48aff167a8e5849dee0aab1a6)

```
http://www.alsa-project.org/db/?f=41438f5d77f0a5d48aff167a8e5849dee0aab1a6
```

:guitar:

---

### Post by Yellow Pasque on 2011-06-27
> **sabbir2world said:**
> Boss, It's a desktop issue

Boss, I can hear sound from my headphone. But while I speak to skype it doesn't respond. My voice doesn't pass from my microphone. Please gimme solution...:(:(

Here's my alsa details:

[http://www.alsa-project.org/db/?f=41438f5d77f0a5d48aff167a8e5849dee0aab1a6](http://www.alsa-project.org/db/?f=41438f5d77f0a5d48aff167a8e5849dee0aab1a6)

```
http://www.alsa-project.org/db/?f=41438f5d77f0a5d48aff167a8e5849dee0aab1a6
```

:guitar:
Your microphones appear to be muted in the info. Play around with volumes in:
```
alsamixer
```

---

### Post by jhtao on 2011-07-05
I'm having a similar issue.  I am running ubuntu 11.04 off of an intel machine.  I get sound through speakers but not through headphones.  I've already checked that all the sound fields are cranked in alsamixer.  I've tried switching the output type to analog headphones, but to no avail.

Using the alsa info script, the following information is generated.
[http://www.alsa-project.org/db/?f=2455de2e4482b2da971938cb85f3b93331a7eb84]("http://www.alsa-project.org/db/?f=2455de2e4482b2da971938cb85f3b93331a7eb84")

If any one can help me.  I would greatly appreciate it.

---

### Post by Yellow Pasque on 2011-07-05
> **jhtao said:**
> I'm having a similar issue.  I am running ubuntu 11.04 off of an intel machine.  I get sound through speakers but not through headphones.  I've already checked that all the sound fields are cranked in alsamixer.  I've tried switching the output type to analog headphones, but to no avail.

Using the alsa info script, the following information is generated.
[http://www.alsa-project.org/db/?f=2455de2e4482b2da971938cb85f3b93331a7eb84]("http://www.alsa-project.org/db/?f=2455de2e4482b2da971938cb85f3b93331a7eb84")

If any one can help me.  I would greatly appreciate it.
See if this helps: [http://ubuntuforums.org/showthread.php?t=1794287](http://ubuntuforums.org/showthread.php?t=1794287)

---

### Post by jhtao on 2011-07-05
> **Temüjin said:**
> See if this helps: [http://ubuntuforums.org/showthread.php?t=1794287](http://ubuntuforums.org/showthread.php?t=1794287)

That worked wonderfully.  Thank you very much!

---

### Post by reaper_rr on 2011-07-05
I'd be very grateful if someone can help me solve this problem.

Here's the output:
[http://www.alsa-project.org/db/?f=8be868d2de2e9e59b3d97729033880c96c28d92a](http://www.alsa-project.org/db/?f=8be868d2de2e9e59b3d97729033880c96c28d92a)

---

### Post by Yellow Pasque on 2011-07-05
> **reaper_rr said:**
> I'd be very grateful if someone can help me solve this problem.

Here's the output:
[http://www.alsa-project.org/db/?f=8be868d2de2e9e59b3d97729033880c96c28d92a](http://www.alsa-project.org/db/?f=8be868d2de2e9e59b3d97729033880c96c28d92a)
What kind of system do you have?

---

### Post by lidex on 2011-07-06
> **Temüjin said:**
> What kind of system do you have?

Or at least motherboard info.
Your codec is:
```
Realtek ALC662
```
Your model selection in alsa-base.conf:
```
model=intel-alc889a
```
I'd ask why, but I'm afraid of the answer. Needless to say you'll need to remove that.

---

### Post by reaper_rr on 2011-07-06
> **lidex said:**
> Or at least motherboard info.
Your codec is:
```
Realtek ALC662
```
Your model selection in alsa-base.conf:
```
model=intel-alc889a
```
I'd ask why, but I'm afraid of the answer. Needless to say you'll need to remove that.

It won't work with intel-alc889a on my PC.
Here is my motherboard specification:
[http://tinyurl.com/mothrbrd](http://tinyurl.com/mothrbrd)

---

### Post by lidex on 2011-07-06
> **reaper_rr said:**
> It won't work with intel-alc889a on my PC.


Exactly, so why is it in there? Try changing intel-alc889a to ecs or 3stack-6ch

---

### Post by reaper_rr on 2011-07-06
> **lidex said:**
> Exactly, so why is it in there? Try changing intel-alc889a to ecs or 3stack-6ch

The headphone problem was solved when I put 'ecs' in the file, but the audio was very choppy.

---

### Post by lidex on 2011-07-06
Try resetting your pulse configuration. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 

```
**Logout/in.**

---

### Post by reaper_rr on 2011-07-06
> **lidex said:**
> Try resetting your pulse configuration. Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 

```
**Logout/in.**

I've tried resetting my pulse configuration and the sound is still choppy, when the model is set to 'ecs'.

On the other side, when the model is set to 'auto' or '3stack-6ch', the audio quality is excellent, but the speakers won't mute when I plug the headphones.

---

### Post by lidex on 2011-07-06
changing the model can cause new mixer options as well as profiles. make sure you go through all the adjustments for each

---

### Post by Yellow Pasque on 2011-07-08
I suggest trying this added on to the model=ecs line:
```
enable_msi=0
```

---

### Post by hero5902815 on 2011-07-14
Hi I have the same problem as well, i have a desktop hp compaq dx2300 microtower with a realtek ALC888 sound, here is the command u asked us to upload to help us, please this is the first time i ever used ubuntu/linux operating systems so i am barely getting by, so please don't leave out any details i might not be aware of :) 
```
http://www.alsa-project.org/db/?f=9e513877c48def4a606801a09df32093bc3c0564
```

EDITED: Ok never mind I kept trying out several model names from your list and 3stack-6ch-intel was the one that worked for me by lowering surround to = and raising front, master and pcm to max, unticked everything except headphone (those options werent't there with other model names) (really i was playing with it and accidentally did it! :D hope I helped others sharing my same problem and a similar pc or such :)

---

### Post by lidex on 2011-07-14
> **hero5902815 said:**
> Hi I have the same problem as well, i have a desktop hp compaq dx2300 microtower with a realtek ALC888 sound, here is the command u asked us to upload to help us, please this is the first time i ever used ubuntu/linux operating systems so i am barely getting by, so please don't leave out any details i might not be aware of :) 
```
http://www.alsa-project.org/db/?f=9e513877c48def4a606801a09df32093bc3c0564
```

EDITED: Ok never mind I kept trying out several model names from your list and 3stack-6ch-intel was the one that worked for me by lowering surround to = and raising front, master and pcm to max, unticked everything except headphone (those options werent't there with other model names) (really i was playing with it and accidentally did it! :D hope I helped others sharing my same problem and a similar pc or such :)

Nice work and thanks for sharing your fix!

---

### Post by Morderwurst on 2011-07-15
I'm not sure if this has been suggested or not but installing linux alsa driver modules from the PPA below resolved this problem for me on an ASUS 1215T

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa && sudo apt-get update && sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```Good luck, and reboot after install.

---

### Post by Waldr on 2011-07-16
> **Morderwurst said:**
> I'm not sure if this has been suggested or not but installing linux alsa driver modules from the PPA below resolved this problem for me on an ASUS 1215T

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa && sudo apt-get update && sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```Good luck, and reboot after install.

Thanks! This solved the problem on my Acer Aspire 5750. Before installing the modules above I couldn't get any sound when headphones were plugged in.

---

### Post by Detroit_Bad_Boy on 2011-07-20
I'm having a problem with my front mic/headphone jacks. I try to use X-Lite, but when I try to configure the audio it says that no drivers are installed.

Here's the link for my configuration. Any help would be greatly appreciated!!!!

[http://www.alsa-project.org/db/?f=11171dcd6fd7781b255af447452e8344b0f43bd1]("http://www.alsa-project.org/db/?f=11171dcd6fd7781b255af447452e8344b0f43bd1")

---

### Post by Number1luda on 2011-07-22
Hi, having this problem on my Asus P50IJ, can get sound on both headphones and speakers at the same time, or just the speakers.

Tryed a lot of stuff, actually been looking into this problem for weeks, but now im at work and bored with my ipod music and the fact that I cant watch any videos, and I need this fixed.

[Here is the info thing]("http://www.alsa-project.org/db/?f=9938aeff60fa7f28787315b055d040db2df719dd")

thanks in advance.

---

### Post by jfever311 on 2011-07-22
Okay, I just loaded ALSA and tried to find a tab or something to get some audio from my headphone jack, to no avail. How do you guys get the ALSA url that provides all this info to use to figure this out. Anyone have some tips for me??

---

### Post by lidex on 2011-07-22
> **Number1luda said:**
> Hi, having this problem on my Asus P50IJ, can get sound on both headphones and speakers at the same time, or just the speakers.

Tryed a lot of stuff, actually been looking into this problem for weeks, but now im at work and bored with my ipod music and the fact that I cant watch any videos, and I need this fixed.

[Here is the info thing]("http://www.alsa-project.org/db/?f=9938aeff60fa7f28787315b055d040db2df719dd")

thanks in advance.

You've made more than one edit to alsa-base.conf
When doing this, if the edit does not work, you need to remove it. Starting from a default config is the only way to debug.
What are these outputs:
```
cat /etc/modprobe.d/alsa-base.conf
```
```
ls /etc/modprobe.d/
```

---

### Post by jfever311 on 2011-07-23
Hey lidex, is the link or command that I need one of the ones in your sig line? Please help. I am a newb, but I have been trying hard to learn this stuff. Thanks in advance.

---

### Post by lidex on 2011-07-23
> **jfever311 said:**
> Hey lidex, is the link or command that I need one of the ones in your sig line? Please help. I am a newb, but I have been trying hard to learn this stuff. Thanks in advance.

See post #2

---

### Post by jfever311 on 2011-07-23
I swear I read this thread thoroughly too..... ;)

Anyway, I do appreciate your patience, lidex.

My info url is as follows:

[http://www.alsa-project.org/db/?f=93b6b45e3a906023573c3b90751c65c4c78c403d](http://www.alsa-project.org/db/?f=93b6b45e3a906023573c3b90751c65c4c78c403d)

---

### Post by lidex on 2011-07-23
> **jfever311 said:**
> I swear I read this thread thoroughly too..... ;)

Anyway, I do appreciate your patience, lidex.

My info url is as follows:

[http://www.alsa-project.org/db/?f=93b6b45e3a906023573c3b90751c65c4c78c403d](http://www.alsa-project.org/db/?f=93b6b45e3a906023573c3b90751c65c4c78c403d)

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by jfever311 on 2011-07-23
> **lidex said:**
> Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=ideapad" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**


I did that, with no change. What exactly did that command do?

---

### Post by lidex on 2011-07-24
> **jfever311 said:**
> I did that, with no change. What exactly did that command do?

Go into your 'Sound Preferences' and on the output tab, i believe, is a connector option. Try toggling that. Also check ```
alsamixer
``` from the terminal. Post your ```
amixer
``` output.

---

### Post by jfever311 on 2011-07-25
jason@jason-Compaq-Presario-CQ60-Notebook-PC:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 49 [66%] [-25.00dB] [on]
  Front Right: Playback 49 [66%] [-25.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 251 [98%] [0.80dB]
  Front Right: Playback 251 [98%] [0.80dB]
Simple mixer control 'Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 0 [0%] [-74.00dB] Playback [on]
  Front Right: 0 [0%] [-74.00dB] Playback [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 3 [100%] [0.00dB] [on]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [on]
  Front Right: 80 [100%] [6.00dB] Playback [on]

---

### Post by akira_sp on 2011-08-14
Hi. i have the same problem on my sony vaio ( model VPCEG18FG). I'm completely new to ubuntu too .Here's the link i obtained

[http://www.alsa-project.org/db/?f=42693d2ed5973bd56a49a41636b503cec65f5526](http://www.alsa-project.org/db/?f=42693d2ed5973bd56a49a41636b503cec65f5526)

any help/link is highly appreciated:)

---

### Post by hrafninn on 2011-08-15
Hello.

My headphone does not work (no sound), but internal speakers are fine (this was not a problem for me in 10.04). When I disconnect the headphone jack, I hear the sound from the internal speakers.

I have a Dell Precision M4300.  My alsa info is here:
[http://www.alsa-project.org/db/?f=2ec297cb6da3785b4d31a28cb883d35af6863165](http://www.alsa-project.org/db/?f=2ec297cb6da3785b4d31a28cb883d35af6863165)

The last line of my /etc/modprobe.d/alsa-base.conf has
options snd-hda-intel model=dell-m43

Maybe not the correct model (but again, it worked in 10.04)?

Any help appreciated.

---

### Post by Ahriman272 on 2011-08-15
This fixed my problem(the post below), i don't know how to delete this post.

---

### Post by Ahriman272 on 2011-08-15
> **Morderwurst said:**
> I'm not sure if this has been suggested or not but installing linux alsa driver modules from the PPA below resolved this problem for me on an ASUS 1215T

```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa && sudo apt-get update && sudo apt-get install linux-alsa-driver-modules-$(uname -r)

```Good luck, and reboot after install.


This worked for me also, thank you.

---

### Post by lidex on 2011-08-16
> **hrafninn said:**
> Hello.

My headphone does not work (no sound), but internal speakers are fine (this was not a problem for me in 10.04). When I disconnect the headphone jack, I hear the sound from the internal speakers.

I have a Dell Precision M4300.  My alsa info is here:
[http://www.alsa-project.org/db/?f=2ec297cb6da3785b4d31a28cb883d35af6863165](http://www.alsa-project.org/db/?f=2ec297cb6da3785b4d31a28cb883d35af6863165)

The last line of my /etc/modprobe.d/alsa-base.conf has
options snd-hda-intel model=dell-m43

Maybe not the correct model (but again, it worked in 10.04)?

Any help appreciated.

In your case alsa is picking up the m42 model. You probably have a backup file in /etc/modprobe.d causing that:
```
!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
[COLOR="Red"]snd-hda-intel: model=dell-m43[/COLOR]
snd-bt87x: index=-2
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
[COLOR="Red"]snd-hda-intel: model=dell-m42[/COLOR]
```

```
!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	[COLOR="Red"]model : dell-m42[/COLOR],(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N


```
I would suggest removing the backup file and also restoring alsa-base.conf to default - in other words, with no model selection. If a reboot doesn't show progress then add the correct model back and do not create any backups in that directory.

---

### Post by hrafninn on 2011-08-17
> **lidex said:**
> In your case alsa is picking up the m42 model. You probably have a backup file in /etc/modprobe.d causing that:

I would suggest removing the backup file and also restoring alsa-base.conf to default - in other words, with no model selection. If a reboot doesn't show progress then add the correct model back and do not create any backups in that directory.

You were right, lidex!  There was a backup file in /etc/modprobe.d stating the m42 model.  The problem is now fixed - thanks a lot.

---

### Post by jabdefiant on 2011-09-02
Hi All

Just got a new HP Pavillion G6, and the sound is acting really wierd.

Using Ubuntu 11.04 64 Bit.

I looked through the threads, but am still stuck.

I have run the script to post information on my card.
the link is as follows...
[http://www.alsa-project.org/db/?f=787a20cff6ce92dc9634cd6307d3501859e6bfcf]("http://www.alsa-project.org/db/?f=787a20cff6ce92dc9634cd6307d3501859e6bfcf")

I am wondering if anyone can help.
a) Internal mic is generates a lot of static on recordings
b) Headphone Jack does not work, but Speakers do.  Even when I plug in the headphones, the speakers remain on.

Any help would be appreciated.

jabdefiant.

---

### Post by lidex on 2011-09-02
> **jabdefiant said:**
> Hi All

Just got a new HP Pavillion G6, and the sound is acting really wierd.

Using Ubuntu 11.04 64 Bit.

I looked through the threads, but am still stuck.

I have run the script to post information on my card.
the link is as follows...
[http://www.alsa-project.org/db/?f=787a20cff6ce92dc9634cd6307d3501859e6bfcf]("http://www.alsa-project.org/db/?f=787a20cff6ce92dc9634cd6307d3501859e6bfcf")

I am wondering if anyone can help.
a) Internal mic is generates a lot of static on recordings
b) Headphone Jack does not work, but Speakers do.  Even when I plug in the headphones, the speakers remain on.

Any help would be appreciated.

jabdefiant.

This is a chipset with the hudson azalia controller. I am beginning to see issues with these chipsets and will try to figure out a solution but for now look for a bios update and follow the link in my sig to update your alsa install.

---

### Post by yashman on 2011-09-05
Hi Lidex, can you help me also? Audio from my main speakers is fine but when I plug in my headphones sound continues to play from the speakers and I hear nothing through my headphones.

Link to my information is: 
[http://www.alsa-project.org/db/?f=86a87a5f6ae2490896b61c9d275bb4fe0dc81d0e](http://www.alsa-project.org/db/?f=86a87a5f6ae2490896b61c9d275bb4fe0dc81d0e)

Thanks!

---

### Post by benzipperer on 2011-09-05
Hi, after a fresh install of 11.04 I can't hear audio out of the headphone jack on my Thinkpad X60s. This worked for me by default in 10.04.

I tried adding ```
options snd-hda-intel model=thinkpad
``` to alsa-base.conf but that didn't seem to help (neither did model=basic).

Here is my ALSA info: [http://www.alsa-project.org/db/?f=b293c62a22c0254d587858b84f2a160237455d3d](http://www.alsa-project.org/db/?f=b293c62a22c0254d587858b84f2a160237455d3d)

I can't seem to find any headphone options in either alsamixer or sound preferences. Any suggestions?

---

### Post by jabdefiant on 2011-09-10
> **lidex said:**
> This is a chipset with the hudson azalia controller. I am beginning to see issues with these chipsets and will try to figure out a solution but for now look for a bios update and follow the link in my sig to update your alsa install.
Thanks for looking into this for me lidex.  However, it's now started working.

I did a reinstall (for another reason....I was just testing and I did not setup the partitions as I wanted them long term).  So I am not sure if the reinstall did it, or something in the daily upgrades changed how the headphone works, but it's working now.

Thanks again.

jabdefiant

---

### Post by arabookworm on 2011-09-14
I am having a similar problem with my laptop. It's a toshiba satellite, and the alsa info is here: [http://www.alsa-project.org/db/?f=3a2b59133fa3f97a3c92ae541b16fe9afe56d9ba](http://www.alsa-project.org/db/?f=3a2b59133fa3f97a3c92ae541b16fe9afe56d9ba)

I'm also a complete noob, so please don't use big words lol.

---

### Post by hybrid00x on 2011-09-16
[LEFT]Hello. I seem to be having a similar problem with my Toshiba Satellite L755D. I've gone
all through this post and tried every suggestion within it, but I cannot figure out what is wrong.
 

 Here's my ALSA info: [http://www.alsa-project.org/db/?f=6d2512182a01a74e0a7c0dffdbd816df7a5ac221](http://www.alsa-project.org/db/?f=6d2512182a01a74e0a7c0dffdbd816df7a5ac221)
 

 Details: I get sound through both the speakers and headphones fine, but the computer speakers
fail to mute when my headphones are plugged in (they only level-off by about 50%). I've
attempted the solutions mentioned in post #4 (with both “thinkpad” and “ideapad” as the model),
post #30 (it may be worth noting that I don't seem to have the option “Connector” in the
“Output” tab of gnome-volume-control, nor do I have the “Front” channel in gnome-alsa-mixer),
and post #56 (short answer: didn't work). I don't think ALSA is even detecting my headphone
jack, as I don't seem to have an option for a “headphones” channel anywhere. Any help would be
greatly appreciated, and thank you in advance!
 

 (Also, it may be worth noting that I have dual-booted Windows 7 alongside Ubuntu 11.04. I don't
know if that would have something to do with it...)[/LEFT]

---

### Post by LiteDrive on 2011-09-17
I'm also having the exact same problem. Everything works fine, including my mic. Just not the headphones when plugged in. 

Here's my stuff:

```

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC271X

==> /proc/asound/card0/codec#3 <==
Codec: Intel CougarPoint HDMI
```

[URL="http://www.alsa-project.org/db/?f=62b703eff6b37e7d9680fccb267c7073e92206c3"]Alsa-Info
[/URL]

Thanks to anyone who can help. Let me know if you need more info.

---

### Post by Toz on 2011-09-17
> **hybrid00x said:**
> [LEFT]Hello. I seem to be having a similar problem with my Toshiba Satellite L755D. I've gone
all through this post and tried every suggestion within it, but I cannot figure out what is wrong.
 

 Here's my ALSA info: [http://www.alsa-project.org/db/?f=6d2512182a01a74e0a7c0dffdbd816df7a5ac221](http://www.alsa-project.org/db/?f=6d2512182a01a74e0a7c0dffdbd816df7a5ac221)
 

 Details: I get sound through both the speakers and headphones fine, but the computer speakers
fail to mute when my headphones are plugged in (they only level-off by about 50%). I've
attempted the solutions mentioned in post #4 (with both “thinkpad” and “ideapad” as the model),
post #30 (it may be worth noting that I don't seem to have the option “Connector” in the
“Output” tab of gnome-volume-control, nor do I have the “Front” channel in gnome-alsa-mixer),
and post #56 (short answer: didn't work). I don't think ALSA is even detecting my headphone
jack, as I don't seem to have an option for a “headphones” channel anywhere. Any help would be
greatly appreciated, and thank you in advance!
 

 (Also, it may be worth noting that I have dual-booted Windows 7 alongside Ubuntu 11.04. I don't
know if that would have something to do with it...)[/LEFT]

Try:
```
options snd-hda-intel model=dell-vostro
```.

---

### Post by ph34r_ on 2011-09-22
Also have that problem, sound goes from speakers and headphones simultaneously. Tried tips from this topic, didn't work.

[http://www.alsa-project.org/db/?f=dcf22f068fce65a4ff775df0d41e061e988fe53f](http://www.alsa-project.org/db/?f=dcf22f068fce65a4ff775df0d41e061e988fe53f)

---

### Post by Toz on 2011-09-22
> **ph34r_ said:**
> Also have that problem, sound goes from speakers and headphones simultaneously. Tried tips from this topic, didn't work.

[http://www.alsa-project.org/db/?f=dcf22f068fce65a4ff775df0d41e061e988fe53f](http://www.alsa-project.org/db/?f=dcf22f068fce65a4ff775df0d41e061e988fe53f)

You're currently using "model=6stack". Try the following instead:
- 6stack-dig
- 3stack 
- 3stack-dig   
- laptop     
- laptop-dig   
- auto  

If neither work, try the following two together:
```
options snd-hda-intel model=3stack
options snd-hda-intel enable_msi=1
```

---

### Post by hybrid00x on 2011-09-23
> **Toz said:**
> Try:
```
options snd-hda-intel model=dell-vostro
```.

No go, my friend. That just seemed to kill the headphone sound completely.
I was wondering if it could be that the software is having trouble identifying the headphone jack, as I cannot seem to find any real suggestion (aside from some suggested solutions providing output through my headphones) that the software is sensing the headphone jack. Also, I was wondering if the HDMI port/element of the card could have something to do with it, as I had a problem previously with JACK Audio Connection Kit where it had the HDMI element in the Interface option, and thus was failing to start. Now I don't know much about ALSA or anything, but I figured I might as well mention this because I figure it might be pertinent to how my software and hardware are interacting.

---

### Post by lidex on 2011-09-23
Try changing your model from whatever it is now to *ideapad*
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

---

### Post by sohussain on 2011-09-23
Speakers working normally here, plugged in headphones no sound from headphones or speakers.
[Alsa linky!]("http://www.alsa-project.org/db/?f=1723bf6d82fb8909fcb00d98af373cdc939d2e29")

Help would b greatly appreciated :D

---

### Post by lidex on 2011-09-23
> **sohussain said:**
> Speakers working normally here, plugged in headphones no sound from headphones or speakers.
[Alsa linky!]("http://www.alsa-project.org/db/?f=1723bf6d82fb8909fcb00d98af373cdc939d2e29")

Help would b greatly appreciated :D

You'll need to edit this file:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
and add a model switch, one at a time, reloading alsa for each edit. Format is:
```
options snd-hda-intel model=xxxx
```

Options for alc269:
```
ALC269
======
  basic         Basic preset
  quanta        Quanta FL1
  laptop-amic   Laptops with analog-mic input
  laptop-dmic   Laptops with digital-mic input
  fujitsu       FSC Amilo
  lifebook      Fujitsu Lifebook S6420
  auto          auto-config reading BIOS (default)
```

---

### Post by ph34r_ on 2011-09-25
> **Toz said:**
> You're currently using "model=6stack". Try the following instead:
- 6stack-dig
- 3stack 
- 3stack-dig   
- laptop     
- laptop-dig   
- auto  

If neither work, try the following two together:
```
options snd-hda-intel model=3stack
options snd-hda-intel enable_msi=1
```

Still doesn't work. Sound card is SupremeFX X-Fi. Sound goes from both headphones and speakers or neither of them if mode=laptop* selected and headphones are plugged in.

---

### Post by rukawa731 on 2011-09-25
Hi,

Installed linux today only and find out speakers are not working , though headphones are rocking .Please help.
Link: [http://pastebin.com/PMwWdaYe](http://pastebin.com/PMwWdaYe)

PC: Intel Core 2 Duo

Thanks,
rukawa731

---

### Post by hybrid00x on 2011-09-25
> **lidex said:**
> Try changing your model from whatever it is now to *ideapad*
To edit:
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Still nothing, my friend.
I noticed something odd in alsamixer. When I start it up, is it supposed to default to what's below?

---

### Post by lidex on 2011-09-27
> **rukawa731 said:**
> Hi,

Installed linux today only and find out speakers are not working , though headphones are rocking .Please help.
Link: [http://pastebin.com/PMwWdaYe](http://pastebin.com/PMwWdaYe)

PC: Intel Core 2 Duo

Thanks,
rukawa731

What is the make/model of this computer?

---

### Post by rukawa731 on 2011-09-27
> **lidex said:**
> What is the make/model of this computer?
Cpu Info:
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping    : 13
cpu MHz        : 2200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips    : 4399.82
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 6
model        : 15
model name    : Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz
stepping    : 13
cpu MHz        : 2200.000
cache size    : 2048 KB
physical id    : 0
siblings    : 2
core id        : 1
cpu cores    : 2
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 10
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dts
bogomips    : 4399.87
clflush size    : 64
cache_alignment    : 64
address sizes    : 36 bits physical, 48 bits virtual
power management:

---

### Post by lidex on 2011-09-27
Can you give the manufacturer and model number of the pc/laptop or if a home built unit the motherboard info? Processor info does not really help in this instance.

---

### Post by rukawa731 on 2011-09-27
HCL WE ezee**BEE  **E4500.

Thanks,

---

### Post by lidex on 2011-09-27
> **rukawa731 said:**
> HCL WE ezee**BEE  **E4500.

Thanks,

I see we're going to need to break this down to mobo level. Post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```

---

### Post by rukawa731 on 2011-09-28
> **lidex said:**
> I see we're going to need to break this down to mobo level. Post these outputs please:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
hehe..Thanks for understanding.I'm trying it first time :)

Logs:

rukawa@rukawa-desktop:~$ sudo dmidecode -t bios
[sudo] password for rukawa: 
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Intel Corp.
    Version: PRG3110H.86A.0065.2009.0421.1559
    Release Date: 04/21/2009
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 1024 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 KB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        LS-120 boot is supported
        ATAPI Zip drive boot is supported
        BIOS boot specification is supported
        Targeted content distribution is supported

Handle 0x0021, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

rukawa@rukawa-desktop:~$ sudo dmidecode -t baseboard
# dmidecode 2.9
SMBIOS 2.4 present.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
    Manufacturer: Intel Corporation
    Product Name: DG31PR
    Version: AAD97576-306
    Serial Number: BTPR94600H9X
    Asset Tag: To be filled by O.E.M.
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: To be filled by O.E.M.
    Chassis Handle: 0x0003
    Type: Motherboard
    Contained Object Handles: 0

Handle 0x001C, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Disabled
    Description:   Intel(R) Extreme Graphics 3 Controller

Handle 0x001D, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Disabled
    Description:  Intel(R) Azalia Audio Device

Handle 0x001E, DMI type 10, 6 bytes
On Board Device Information
    Type: Ethernet
    Status: Disabled
    Description:         Intel (R) 82562 Ethernet Device.

---

### Post by grusbueno on 2011-09-30
Hi!

I have an **Asus U30SD**, with a** VIA ID 8446** codec and** Ubuntu 11.04**.

This is my alsa-info page: [http://www.alsa-project.org/db/?f=eb1ee6e45eb8a22661b2940291fd65d9079fb796](http://www.alsa-project.org/db/?f=eb1ee6e45eb8a22661b2940291fd65d9079fb796)

The problem is that my laptop speakers doesnt mute when I plug in my headphones. But I can hear both at the same time, speakers and headphones.

lidex, can you help me please? :_

---

### Post by d4rk on 2011-10-01
Speakers on laptops works fine, but no sound from headphone jack. It does mute the laptop speakers when something is connected though.

Laptop: Lenovo R61i
System: 11.10 "Oneiric Ocelot"

[http://www.alsa-project.org/db/?f=91efda25e6354cc7de7055babfa68bdfbae19de6](http://www.alsa-project.org/db/?f=91efda25e6354cc7de7055babfa68bdfbae19de6)

Been playing around with different settings, to no avail though. Hoping for some help on this issue, thanks a lot in advance.

EDIT: Notice it says "lenovo-sky" for snd-hda-intel model, that is because I've been trying a bunch of different models here, and that was the last one I tried.

---

### Post by d4rk on 2011-10-03
I'm going to be bold enough to bump this thread. 

In addition here's the last lines of my current alsa-base.conf: 

```
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=thinkpad-t61p
```

Edit: Noticed this was pushed back to a new page with default forum settings, see the previous post for an elaboration of my issue.

---

### Post by bahamutgod on 2011-10-03
Hello there,

i recently got my laptop Acer 5750g, and I did install
ubuntu 11.04 on it, but when I connect my headphones there is no sound via headphones nor via speakers.

I've been searching now for a long time but looks like my model
is a bit "special" because I didn't find information about this concrete laptop or the ALC269VB artifact.

My information is [here]("http://www.alsa-project.org/db/?f=cb79282c5a29273bb5af2e25aa93d046d26f691a").

Thank you :)

---

### Post by nagy2011 on 2011-10-08
i have the the same problem 

[http://www.alsa-project.org/db/?f=7ca76a8670682d303523a2b0f3b0bdec5dbb5c4f](http://www.alsa-project.org/db/?f=7ca76a8670682d303523a2b0f3b0bdec5dbb5c4f)

---

### Post by rsn13 on 2011-10-10
I got this problem too, on an asus k50af. i tryed to modify that alsa config file but with no succes. can you please tell me what exactly should i add, and where can i find the original file because i can't remember what i already did.

---

### Post by lidex on 2011-10-11
> **rukawa731 said:**
> hehe..Thanks for understanding.I'm trying it first time :)


Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=3stack-6ch-intel" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by bahamutgod on 2011-10-12
Hello there again,

I have been looking for more info on my problem, posted some replies before.

For the Acer 5750g, having the ALC269VB, you can just suspend Ubuntu and when you come back from suspensions you have sound from headphones :)

You can see the description from the bug here, and suscribe and try to install the new alsa drivers to get this solved:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/697498")

Hope this helps some people!

---

### Post by rsn13 on 2011-10-17
bump? :oops:

---

### Post by d4rk on 2011-10-25
I'm going to bump this thread yet again, with a new log which should reflect new changes, if any. From my previous post: Speakers on laptop works fine, but no sound from headphone jack. It does mute the laptop speakers when something is connected though.

Laptop: Lenovo R61i
System: 11.10 "Oneiric Ocelot"

New log:
[http://www.alsa-project.org/db/?f=e0975d6e5b611b3ff4edb6433e37262a83220337](http://www.alsa-project.org/db/?f=e0975d6e5b611b3ff4edb6433e37262a83220337)

---

### Post by jfever311 on 2011-10-26
Never have gotten my headphones to work......

---

### Post by charyston on 2011-10-27
I added the line below my alsa-base.conf, rebooted, but nothing changed.

```
options snd-hda-intel model=auto
```ALSA information script:
[http://www.alsa-project.org/db/?f=d3ff0c1fa938c102d8d295a08be8971f7d05c0df](http://www.alsa-project.org/db/?f=d3ff0c1fa938c102d8d295a08be8971f7d05c0df)

All the best!

---

### Post by arash010 on 2011-10-27
Hi guys,
I have the same problem with my pc headphon and also speaker..This problem comes when i instal new window in my PC..i tried to modify this problem more time but no result well...anyone can tell me please what i should be do?

---

### Post by khanalbaBu on 2011-11-23
Thanks lidex,
That works !!!! :D

---

### Post by nsznaj on 2011-11-23
Hi I have the same problem.... It seems this is a general problem on Ubuntu 11.04.

Mine is Dell Inspiron 1545. Can't get through and about to install ubuntu again  !! 

I'd like to install 9.04 which worked perfectly and I regret the day I upgraded....Is there any recommendation against?

---

### Post by Pyre Vulpimorph on 2011-12-31
I'm running Kubuntu 11.10 64-bit and having the same issue. Laptop speakers do not mute when headphones are plugged in.

I'm using an HP Pavilion D7 laptop.

[http://www.alsa-project.org/db/?f=f57cf435c564d26528ca7c00bb8addfa3291559c](http://www.alsa-project.org/db/?f=f57cf435c564d26528ca7c00bb8addfa3291559c)
is my ALSA output


This is my motherboard info:
> # dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
        Manufacturer: Quanta
        Product Name: 3639
        Version: 33.22
        Serial Number: Base Board Serial Number
        Asset Tag:  
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Base Board Chassis Location
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

Handle 0x0007, DMI type 10, 6 bytes
On Board Device Information
        Type: Video
        Status: Enabled
        Description: 0
And this is my BIOS information:
> # dmidecode 2.9
SMBIOS 2.6 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Hewlett-Packard
        Version: F.08
        Release Date: 10/15/2009
        ROM Size: 2048 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                ESCD support is available
                Boot from CD is supported
                Selectable boot is supported
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                ACPI is supported
                USB legacy is supported
                AGP is supported
                Smart battery is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
        BIOS Revision: 15.8
        Firmware Revision: 51.34
I have installed the latest alsa drivers from the Ubuntu Audio Dev Team PPA, but that didn't fix anything.

I've also used alsamixer to manually configure my playback options, but  muting the onboard speakers mutes everything, even when "master" and  "front" are unmuted and at maximum.

---

### Post by lidex on 2011-12-31
> **Pyre Vulpimorph said:**
> I'm running Kubuntu 11.10 64-bit and having the same issue. Laptop speakers do not mute when headphones are plugged in.

I'm using an HP Pavilion D7 laptop.

[http://www.alsa-project.org/db/?f=f57cf435c564d26528ca7c00bb8addfa3291559c](http://www.alsa-project.org/db/?f=f57cf435c564d26528ca7c00bb8addfa3291559c)
is my ALSA output


This is my motherboard info:
And this is my BIOS information:
I have installed the latest alsa drivers from the Ubuntu Audio Dev Team PPA, but that didn't fix anything.

I've also used alsamixer to manually configure my playback options, but  muting the onboard speakers mutes everything, even when "master" and  "front" are unmuted and at maximum.

I have a Dv7 also. You would benefit from a bios update.
Meantime try this using a Terminal:
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by Pyre Vulpimorph on 2012-01-01
> **lidex said:**
> I have a Dv7 also. You would benefit from a bios update.
Meantime try this using a Terminal:
```
echo "options snd-hda-intel model=hp-dv5 enable_msi=1" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

**:popcorn: YES! **Thank you so much!

*kisses you in a totally non-romantic, non-sexual way*

Hmm, I looked on HP's support site for my laptop's model (Pavilion Dv7-3060us) and they only offer BIOS updates through a Windows utility. Would I really have to reinstall Win7 just to upgrade the BIOS, or is there another way? Is WINE safe?

---

### Post by Pianisimo on 2012-01-25
I don't know where to post for help here seemed good.
[http://www.alsa-project.org/db/?f=1a9ee914b5b7651f6f5ee8b844c6bc7f9417440a](http://www.alsa-project.org/db/?f=1a9ee914b5b7651f6f5ee8b844c6bc7f9417440a)
is my ALSA information, can anyone help my sound doesn't work.
Thanks in advance for reading :)

---

### Post by vale tudo on 2012-01-30
For those having trouble with Conexant CX20584,

using lidex's advice on page 1, try: model=laptop,dell-vostro position_fix=0,1

This is working for me at the moment

---

### Post by rsn13 on 2012-02-08
i have this very problem on my laptop, asus k50af running 10.10. if you need more info about my machine, please tell me what and where to get it from. thx a lot

---

### Post by armoftheland on 2012-02-19
THANK YOU LIDEX - i followed your very clear and thorough advice and fixed my Toshiba. Works! Painless easy fix. Love!

---

### Post by rsn13 on 2012-03-31
can someone help me with this? here's the alsa-project info [http://www.alsa-project.org/db/?f=5a7e0620cc20aaaec454672acd613c6331d06ea0](http://www.alsa-project.org/db/?f=5a7e0620cc20aaaec454672acd613c6331d06ea0)

---

### Post by Yellow Pasque on 2012-03-31
> **rsn13 said:**
> can someone help me with this? here's the alsa-project info [http://www.alsa-project.org/db/?f=5a7e0620cc20aaaec454672acd613c6331d06ea0](http://www.alsa-project.org/db/?f=5a7e0620cc20aaaec454672acd613c6331d06ea0)
Upgrading alsa module should fix it:
```
sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily
sudo apt-get update
sudo apt-get install alsa-hda-dkms
```
Reboot or reload alsa.

---

### Post by rsn13 on 2012-04-01
tnx alot, that fixed it :) you rock :D

---

### Post by tamashumi on 2012-04-14
Hi,

Speakers won't off after headphones plug in. Headphones remain silent.
Notebook Asus B23E, Ubuntu 12.04 beta2
[Alsa info link]("http://www.alsa-project.org/db/?f=97094eb8b8c3db63c9d6642561a63442b816dda7")

S.O.S. please :)

EDIT: I've found this among [change log]("http://ww.alsa-project.org/main/index.php/Changes_v1.0.24_v1.0.25"):
Add VT1802 check in via_speaker_automute function

...but not sure how this corresponds to alsa-base.conf

EDIT2: It has occurred that was a hardware problem.
I had bought notebook with custom CPU upgrade and jacks connector was misplaced.
After I reconnected headphones detection works just fine :)

---

### Post by zbigison on 2012-04-16
Hello,
My laptop uses Realtek ALC661 and I couldn't find what to put alsa-base.conf file.
Could you please help me? More details you can find here: [http://www.alsa-project.org/db/?f=90a3d410b729f47f474162a457fa678304d598a4]("http://www.alsa-project.org/db/?f=90a3d410b729f47f474162a457fa678304d598a4")
I use now Ubuntu 11.10 - does it change anything?

---

### Post by nitingupta on 2012-04-22
I am also having the headphone issue. Internal speakers dont mute when i plug-in headphone. And if headphones are not plugged in at boot time then no sounds in headphone..I have VAIO  laptop. My alsa info is  [http://www.alsa-project.org/db/?f=9f84464056496a48531aac22116fa8fb2708c8d5](http://www.alsa-project.org/db/?f=9f84464056496a48531aac22116fa8fb2708c8d5)
Any help will be appreciated.

@lidex can you help me out?

---

### Post by sushi80 on 2012-04-29
Hi All

I was running 11.10 and was working fine but since I've updated to 12.04 i'm having this problem 

here my alsa info
[http://www.alsa-project.org/db/?f=e17e53e138037a31528c2cdc18563484abed8681](http://www.alsa-project.org/db/?f=e17e53e138037a31528c2cdc18563484abed8681)

i tried to add different options to alsa-base.conf (snd-hda-intel model=...) but still not working

any suggestion??

---

### Post by sushi80 on 2012-04-29
> **sushi80 said:**
> Hi All

I was running 11.10 and was working fine but since I've updated to 12.04 i'm having this problem 

here my alsa info
[http://www.alsa-project.org/db/?f=e17e53e138037a31528c2cdc18563484abed8681](http://www.alsa-project.org/db/?f=e17e53e138037a31528c2cdc18563484abed8681)

i tried to add different options to alsa-base.conf (snd-hda-intel model=...) but still not working

any suggestion??

Fixed... for my Acer Aspire 5930g i used the option "auto" (snd-hda-intel model=auto)

---

### Post by ivawzh on 2012-05-03
I'm waiting for your save:popcorn:

[http://www.alsa-project.org/db/?f=05769b8c8a296a64b66926cd8c441433b4a08a6b](http://www.alsa-project.org/db/?f=05769b8c8a296a64b66926cd8c441433b4a08a6b)

---

### Post by tospo on 2012-06-08
I had fixed the same problem some time ago and my laptop just reverted to not switching off the internal speaker when headphones are plugged in. I found that I can run 
```
alsamixer
```
in a command terminal and there was a an "Auto mute mod" option that was set to "disabled". Simply switching that to "enabled" immediately solved the problem.

---


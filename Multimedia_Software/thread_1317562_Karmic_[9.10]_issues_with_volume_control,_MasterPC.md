---
title: "Karmic [9.10] issues with volume control, Master/PCM/LFE, and volume threshold"
date: 2009-11-06
forum: Multimedia Software
---

### Post by dkisl on 2009-11-06
Just upgraded to Ubuntu 9.10 (Karmic Koala) and am having sound issues like many others.

Symptoms:
Changing the system tray volume control doesn't affect the speaker volume at all, until I set it to 30% or below, at which point the speakers completely stop producing any sound
Using gnome-alsamixer, watched what happens when I lower volume: until the threshold, Master is dropping, then at that 30% point (when Master hits 0), PCM and LFE begin to drop.  At volume control 0, all three of them are at 0.
Checked ALSA drivers (up to date), deleted and reinstalled PulseAudio (no change at any point in the process)
Curiously, the minimum volume threshold is still there when I plug in headphones (through the headphone jack), but the volume control changes the sound output; gnome-alsamixer continues to do the exact same things as described above.

I will be happy to provide specs or run diagnostics if needed.  My soundcard is a Sigmatel STAC9200 and I'm running Karmic on a Dell Inspiron notebook.

Thanks.

---

### Post by Jixop on 2009-11-11
Same problem here. Same result in gnome-alsamixer.
Only for me, I would say the minimum threshold is more around 10%.

I'm on Dell 9400 laptop. Sound trough the speakers are always to loud. With headphones it's normal (with 10% treshold, but it isn't too loud at 15%). 

The problem would be solved for me if I could change the volume buttons to only control the PCM channel instead of Masterchannel. (In 9.04: Master also lowered LFE wich is my subwoofer and should always be full volume) I did change it in 9.04, but can't find the option in 9.10.

Thanks in advance.

---

### Post by LJComServ on 2009-11-13
I've got an identical problem.

Looks like the Master and PCM controls are flipped. Master controls the treble and the PCM controls the volume level.

I'm on a Inspiron E1705 and a Sigmatel STAC9200.

Thanks to all!

---

### Post by geopteryx on 2009-11-14
Hi!
I too have a DELL Inspiron 9400/E1705 with the STAC9200. I've solved this problem by making some changes in the file "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common". Try this:

```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

You will find those lines near the bottom of the file:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

So, add theses lines BEFORE:

```
[Element Master]
switch = mute
volume = ignore
```

and these lines AFTER:

```
[Element LFE]
switch = mute
volume = ignore
```

You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```

Save and quit. Then restart (restarting Pulseaudio isn't enough).

Using Fn + PageUp / PageDown or the media buttons now only modifies the "PCM" channel (have a look on alsamixer).

---

### Post by LJComServ on 2009-11-14
Thanks geopteryx!

That did it!

Got to love the Ubuntu community!

---

### Post by Jixop on 2009-11-15
Thanks! Solved it for me too. (also DELL Inspiron 9400/E1705 with the STAC9200)
Sound looks not as loud as in 9.04 though.

---

### Post by Jixop on 2009-11-15
> **Jixop said:**
> Thanks! Solved it for me too. (also DELL Inspiron 9400/E1705 with the STAC9200)
Sound looks not as loud as in 9.04 though.
Loudness issues solved: Some slider in the Sound preferences panel wasn't set correctly (anymore). 
(It was the volume of Exaile in the 'Applications' tab.)

---

### Post by Andre_44 on 2009-11-17
Worked perfectly for me too, is there a bug report for this?

---

### Post by cdthompso1 on 2009-11-21
Ditto for me on another Inspiron 9400.  Looks like this is very specific to the E1705 and 9400, which are essentially the same model.  Thanks for the tip.

---

### Post by SR_ELPIRATA on 2009-11-23
I wouldnt say this was a Dell only issue :P

I had many problems with this when I installed 9.10 and after some time doing this and that (thread was on launchpad) it never worked for me. Did the switch and merge thing and didnt fix it either. But worser than that, I had a noise that sounded at all times that was driving me crazy and since this is my HTPC... bad sound is a big issue.

So, after awhile and with no other kind of help available... back to 9.04 with perfect audio :P (well, I still have a tick every 10 secs when playing HD stuff, but other than that... perfect).

ELP

---

### Post by Seinfeld on 2009-11-23
Hi

I usually do not use pulseaudio. I always uninstall as it creates some problems with MediaPlayer.  But, the volume control on the system tray panel DISAPPEARS in Karmic. How can I get to control the volume??  
Any clue please?

Thanks

---

### Post by SR_ELPIRATA on 2009-11-24
You know, that was one of the questions I've always had since the inception of pulseaudio. This motherboard supposedly is using ALSA but I can control the sound also with the pulseaudio controls, so I wouldnt uninstall pulseaudio just because I use ALSA... in reality I dont really know what Im using, just that it works.

@Seinfeld: I'm not really sure how to help you, but if you still hear audio after removing pulseaudio... I think you can invoke the alsamixer. In my system I just open the terminal, type alsamixer and hit enter. You will see a window open with the mixer (it looks ugly), you can select which part of the mixer u want to control by moving the left/right keys and then adjust with up/down. When finish adjusting, just hit ESC to leave that window.

---

### Post by Seinfeld on 2009-11-25
Thanks SR_ELPIRATA

Same here, I do hear sound, however, we have to point all sound applications e.g. Skype, mplayer to pulseaudio. Well you are right, as long as it works, why worry.. Yes, it works but INTEL motherboard's native soundcard card (mine) does work better with alsa. The sound with Virtual Box is lower with pulseadio, also, the control preferences with alsa is much better. With pulseadio, the volume control cannot be add via Add-to-panel, the volume control appears in the "Notification Area" instead, so I cannot control keyboard shortcuts as nicely as ALSA e.g. PCM, Master, etc... 
Anyways, we just want to know why this is only in Karmic?? 
I tried and uninstalled ALSA completely, the sound still works which indicates "pulseadio is in control", however, strangely alsamixer command still works in the terminal and I still get the alsamixer controls and they do work and control the sound.... uhh.. weird...:)

---

### Post by SR_ELPIRATA on 2009-11-25
Precisely sound issues is what drove me back to 9.04 and that weird volume control applet didnt help matters either.

ELP

---

### Post by Dr. Falken on 2009-11-26
> **geopteryx said:**
> Hi!
I too have a DELL Inspiron 9400/E1705 with the STAC9200. I've solved this problem by making some changes in the file "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common". Try this:

```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

You will find those lines near the bottom of the file:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

So, add theses lines BEFORE:

```
[Element Master]
switch = mute
volume = ignore
```

and these lines AFTER:

```
[Element LFE]
switch = mute
volume = ignore
```

You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```

Save and quit. Then restart (restarting Pulseaudio isn't enough).

Using Fn + PageUp / PageDown or the media buttons now only modifies the "PCM" channel (have a look on alsamixer).
These solutions worked for me in a Dell Precision 690.

Also in other Precision 690, one of my team mates at work downgraded the ALSA modules to the Jaunty ones and also worked fine about this issue. I don't know the details how he did it.

---

### Post by mikesmithv on 2009-11-27
> **geopteryx said:**
> Hi!
I too have a DELL Inspiron 9400/E1705 with the STAC9200. I've solved this problem by making some changes in the file "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common". Try this:

```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

You will find those lines near the bottom of the file:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

So, add theses lines BEFORE:

```
[Element Master]
switch = mute
volume = ignore
```

and these lines AFTER:

```
[Element LFE]
switch = mute
volume = ignore
```

You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```

Save and quit. Then restart (restarting Pulseaudio isn't enough).

Using Fn + PageUp / PageDown or the media buttons now only modifies the "PCM" channel (have a look on alsamixer).

This fix also worked for me on my Dell E1705.  The volume is smooth now but it sounded "different".  I rebooted into Windows (Vista) and listened closely and discovered that in Windows the sound comes out the left and right speakers on the front of the laptop but in Ubuntu 9.10 with this fix it only comes out the "sub-woofer" on the bottom (nothing out of the left and right speakers).  So then I checked Ubuntu 9.04 (live CD) and the sound is out of the front speakers.  Do you think it might be possible to fix this by changing "volume = ignore" to something else?

---

### Post by patsy4078 on 2009-11-30
geopteryx's hack fixed my Dell XPS m1017. Thank you!

mikesmithv: Sounds like the trebble is too low. run alsamixer and increase your Master (trebble on a Dell) or decrease your LFE (bass) until your mid and low ranges sound right.

---

### Post by mikesmithv on 2009-12-02
patsy4078: You are correct about using alsamixer.

Master = "treble" which is the front left and right speakers
LFE = the "bass" speaker on the bottom
PCM = the real master which controls them both.

However, it did not work that way on my E1705 after doing geopteryx's hack.  Since my last post I did some more searching and finally fixed it by also editing /etc/pulse/default.pa as summarized here:

[http://ubuntuforums.org/showthread.php?t=1305889]("http://ubuntuforums.org/showthread.php?t=1305889")

Now 9.10 works great!

Mike

---

### Post by SR_ELPIRATA on 2009-12-02
Somebody should edit the thread subject to SOLVED status :) that way more people can come and get the fix :)

---

### Post by psrivats on 2010-01-15
> **geopteryx said:**
> Hi!
I too have a DELL Inspiron 9400/E1705 with the STAC9200. I've solved this problem by making some changes in the file "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common". Try this:

```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

You will find those lines near the bottom of the file:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

So, add theses lines BEFORE:

```
[Element Master]
switch = mute
volume = ignore
```

and these lines AFTER:

```
[Element LFE]
switch = mute
volume = ignore
```

You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```

Save and quit. Then restart (restarting Pulseaudio isn't enough).

Using Fn + PageUp / PageDown or the media buttons now only modifies the "PCM" channel (have a look on alsamixer).

Thank you for this!

Works on my thinkpad T60 running karmic... but in the opposite way. The hardware buttons change only the "master". The PCM stays fixed.

Can someone explain the difference between these two controls (Master and PCM)? Am I supposed to keep the PCM all the way up and say 40% on the Master? Or vice versa? Or should I set both to say 50% and adjust volume on my speakers to my preferred level? Are equivalent to the first two windows XP controls below?

[IMG]http://www.guidebookgallery.org/pics/gui/applications/multimedia/volume/winxppro-2-1.png[/IMG]

---

### Post by SR_ELPIRATA on 2010-01-17
Far as I know yes, PCM and Wave are the same thing. Depending on your configuration you might prefer to control the master or the PCM/Wave. For example, IIRC there was a time when the Master was also the front speakers and changing that volume only would not change the center/lfe/surrounds for me, so controlling the PCM in that case would be preferred.

---

### Post by erlendoos on 2010-01-20
What does LFE mean?

I use Ubuntu 9.10 on a dell inspiron 9400 and when i use the proposed configuration, the pc-speakers don't work, but the headphones do.
When I use the configuration below, the pc-speakers work, but the headphones produce little sound.


```
[Element Master]
switch = on
volume = ignore
override-map.1 = all
override-map.2 = all-left,all-right

[Element PCM]
switch = mute
volume = merge
```

---

### Post by psrivats on 2010-01-24
> **SR_ELPIRATA said:**
> Far as I know yes, PCM and Wave are the same thing. Depending on your configuration you might prefer to control the master or the PCM/Wave. For example, IIRC there was a time when the Master was also the front speakers and changing that volume only would not change the center/lfe/surrounds for me, so controlling the PCM in that case would be preferred.

Makes sense. Thanks! I am pretty happy with the sound setup on my thinkpad (I manually compiled and installed the lastest alsa). Audacity is the only program that is giving me trouble, will find a fix for that soon.

---

### Post by michelux on 2010-01-24
Works great for me. Thanks.

---

### Post by l-x-l on 2010-02-16
This thread saved me after a pulseaudio upgrade yesterday forced my LFE speakers to 100% all the time. Many thx.

---

### Post by Andre_44 on 2010-04-25
I have had to search for this thread 4 times in the past few months to find the fix again, it seems that upgrades are constantly overwriting the file.  Can we do anything to get this fixed upstream instead of constantly having to apply the fix ourselves?

---

### Post by lidex on 2010-04-25
There is another approach that may work. This is specific to the Dell Inspiron E1705/9400 model w/ STAC9200 codec.
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-m27  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

---

### Post by biomann on 2010-05-01
> **geopteryx said:**
> Hi!
I too have a DELL Inspiron 9400/E1705 with the STAC9200. I've solved this problem by making some changes in the file "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common". Try this:

```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

You will find those lines near the bottom of the file:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

So, add theses lines BEFORE:

```
[Element Master]
switch = mute
volume = ignore
```

and these lines AFTER:

```
[Element LFE]
switch = mute
volume = ignore
```

You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```

Save and quit. Then restart (restarting Pulseaudio isn't enough).

Using Fn + PageUp / PageDown or the media buttons now only modifies the "PCM" channel (have a look on alsamixer).

Hi,

This worked fine for Karmic, but it seems that it does not work with Lucid. The way lidex described doesnt work either :(

---

### Post by lidex on 2010-05-01
I guess OP got his working correctly.
*biomann*: Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by dclaw on 2010-05-06
I have been having the same issue since I installed lucid lynx 10.04. I can no longer choose which input/output the volume app is controlling... and see that it's changing the front first, then the master, but the master portion doesn't change anything volume wise.

Grrr....

I just edited the file and about to reboot. I'll post back if that resolves it.

-Dclaw

---

### Post by dclaw on 2010-05-06
Well... it's a little better.

Now, it gets to 70% and tops out instead of 25% in the volume manager app. The last 30% have no effect. The front output (which I'm not even using anyway) is at 100% now in alsamixer, but the PCM is now changed from 0->100 when I change volume in the app from 0->70%, then master goes from 74->100

Also, at 5% in the volume control applet, I don't get sound anymore, I get what I can only refer to as static.

Anyone have any other ideas?

-Dclaw

---

### Post by lidex on 2010-05-06
dclaw:
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Arless on 2010-05-29
> **geopteryx said:**
> Hi!
I too have a DELL Inspiron 9400/E1705 with the STAC9200. I've solved this problem by making some changes in the file "/usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common". Try this:

```
sudo gedit /usr/share/pulseaudio/alsa-mixer/paths/analog-output.conf.common
```

You will find those lines near the bottom of the file:

```
[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right
```

So, add theses lines BEFORE:

```
[Element Master]
switch = mute
volume = ignore
```

and these lines AFTER:

```
[Element LFE]
switch = mute
volume = ignore
```

You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```

Save and quit. Then restart (restarting Pulseaudio isn't enough).

Using Fn + PageUp / PageDown or the media buttons now only modifies the "PCM" channel (have a look on alsamixer).

Works perfect in Lucid Lynx !!, i always had pcm 100% and noise, now i can control individualy pcm center lfe etc.. with alsamixer, Thanks!

ECS gf8200a
Logitech Z5500

---

### Post by cometdog on 2010-06-06
> **geopteryx said:**
> Hi!
You should finally have:

```
[Element Master]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

[Element LFE]
switch = mute
volume = ignore
```



Something similar worked for me on Lucid.

I used

```

[Element Master Front]
switch = mute
volume = ignore

[Element PCM]
switch = mute
volume = merge
override-map.1 = all
override-map.2 = all-left,all-right

```

on an ASUS M4A785TD-V EVO

It has the AMD 785G+SB710 chipset.

Anyway, the above works fine for me using the analog outputs with the hardware set to Analog Surround 4.0 Output, which is how I'm using it.

---

### Post by pawhtiobo on 2010-06-22
THKX :)

It works in Thinkpad T41 :guitar:.

[[]]

---

### Post by iamgillespie on 2010-07-29
Thanks! This worked like a charm.:popcorn:

---

### Post by henjj on 2010-09-14
Worked for me too in Lucid with a Dell Inspiron 9400.  Thanks.

---

### Post by draxx31 on 2010-10-21
Hello, I have a desktop computer with Asrock P4i65G with Multimedia audio controller		: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02). 

I had the same problem on Ubuntu 9.10, 10.4 and 10.10 solved with your workaround. Thank you very much.

Does an official issue exist?

Could you explain how work the workaround?

---

### Post by kalross on 2011-01-10
Thank you so much.  Fixed my sound on Dell Precision M90.

Kal

---

### Post by Andre_44 on 2011-01-11
I am finally selling this laptop and building a new PC.. This issue plagued me for well over a year, every upgrade, every reinstall... I have applied this fixed many dozens of times, each time more annoying than the last... 

To those of you left with this problem, open an actual ticket on launchpad or something, this thread has been here forever and hasn't drawn any attention to the issue and its not going to get fixed unless someone does something about it.

---

### Post by Jetro on 2011-01-15
> **Andre_44 said:**
> I am finally selling this laptop and building a new PC.. This issue plagued me for well over a year, every upgrade, every reinstall... I have applied this fixed many dozens of times, each time more annoying than the last... 

To those of you left with this problem, open an actual ticket on launchpad or something, this thread has been here forever and hasn't drawn any attention to the issue and its not going to get fixed unless someone does something about it.
I've seen a bunch of similar threads/bug reports on Launchpad regarding this issue. Makes you wonder why they haven't fixed this when it has soon been **two years**.

---

### Post by cdthompso1 on 2012-11-18
I have been applying this change on my Inspiron 9400 and e1705 after every upgrade.  On 12.04.1 LTS now and I still apply this fix.

I guess that's what I get for using a five year old laptop.

---


---
title: "Webcam Mic not working properly in Ubuntu 11.10"
date: 2011-10-15
forum: Multimedia Software
---

### Post by zer0nes on 2011-10-15
I have a Logitech webcam with microphone built-in. 

The mic worked great in 11.04. However, after I upgraded to 11.10, it behaves very weird when I test with the sound recorder. It either 

- (i) doesn't record sound any all 
- or (ii) records but plays back the input very fast (like in a fast forwarding mode). To clarify (ii), I notice that the time lapse in the sound recorder changes very slowly (1s for each 4s in the real world). 

English is not my first language so please ask me to clarify if you don't understand my problem yet.

PS: as a consequence, I cannot use Skype.

---

### Post by mahroop on 2011-10-15
Same Problem here too

---

### Post by ddossett on 2011-10-16
Me too. It a fairly standard logitech webcam that was previously working fine on the same sound preferences settings. Both sound recorder and skype have the same 'fast talk' problem. I'm going to try fiddling with pulseaudio (uninstall reinstall, using alsamixer etc) to see if it goes away. I'll report back if successful.

---

### Post by zoso3325 on 2011-10-17
I have the same problem. also cheese displays me greenish

---

### Post by Sevenarth on 2011-10-17
Same problem... please correct >.>

---

### Post by paidjo on 2011-10-17
Mine too, built-in webcam on BenQ Joybook S32 doesn't work

---

### Post by crgutierrez on 2011-10-17
same problem
VERY SILLY
help pls:(

---

### Post by fermoncho on 2011-10-18
Nobody knows the solution. We're losted. Logitech C200 working perfectly in 10.10 and 11.04. But 11.10 ****

---

### Post by gindyo on 2011-10-18
same problem here
I can get it to work if I unplug and then plug the camera, but it doesn't work every time :(

---

### Post by francos3 on 2011-10-19
There is a workaround but it is not a pretty one ...

Basically you need to disconnect the camera, turn on Skype, reconnect the camera, open Skype options, hit the test video test button, and then the microphone works for as long as you keep the option windows open.  It is not a Skype bug, for some reason linux kernell 3.0 is messing up with the frecuency of the mike, hence it is also called the "chipmunk" bug!

It is a very ugly workaround but it enables you to make a skype phone call.  Obviously very frustating when someone calls you...

Going throgh different fourms I found out this issue is actually connected to the new 3.0 kernel for all logitech cameras.  Somebody mntnioned there is a fix/patch already out there but for some reason it has not been added to the UBUNTU repositories.  I am just an average Linux user and was not looking forward to rebuilt my kernel so I just use the workaround.

It would be great if somebody could fix this issue as it is going to be quite a spread one.  Apparently it affects all logitech cameras.

Thanks,

---

### Post by francos3 on 2011-10-21
Just updated to kernel 3.0.0-13 but still the same problem with the mike :-(

---

### Post by Docaltmed on 2011-10-21
Same problem! Dear lord, it's funny as heck, but really, really bad news for my sip and skype calls.

---

### Post by Docaltmed on 2011-10-21
Here's the launchpad bug, if anyone wants to join the fun:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843431?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843431?comments=all)

Looks like the only information they are looking for at this point is model/ID.

---

### Post by cococoen on 2011-10-23
Same here with the c270. The mentioned bug report ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843431](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843431)), contains a patch, but it means rebuilding the kernel. Anybody know how tot do that and willing to share that with the rest of us (step-by-step)?  
Thanks!

---

### Post by arkara on 2011-10-23
Hello. The problem is that the microphone is in the wrong sound rate by the pulse audio. As a user do the following:

```
gedit $HOME/.pulse/daemon.conf
```

and put the following line on the file:
```
default-sample-rate = 16000
```

save it, and then restart pulseaudio as a user with the following command

```
pulseaudio --kill && pulseaudio --start
```

This should solve the problem.

---

### Post by arkara on 2011-10-23
The problem that i have, is that the microphone randomly stops working and i have to restart pulseaudio.

---

### Post by Bobhuber on 2011-10-26
Don't upgrade the Kernel . Downgrade it to 2.6.38 (last Natty rev dated June 4 2011) Fixed my problems in 11.04 and 11.10 . Logitech Pro. Running Gnome 3 & Natty (dual boot) with no problems.

---

### Post by Querio on 2011-10-29
Thank you Arkara!  Works wonders.

---

### Post by francos3 on 2011-10-31
Thanks,Arkara same here.  It works great now ;-)

---

### Post by sarahlizz3 on 2011-11-01
Arkara, I cannot thank you enough!!!

Out of curiousity, is anyone having a problem with the video also?  Mine was working fine before this upgrade, after the sound went screwy (read: Alvin and the Chipmunks), which Arkara's fix fixed, and my video when in color is all weird.

It can take black and white photos/video fine, but if I turn back on the color it looks like this (attached). 
(this is a picture of a full color ad, just to demonstrate)

---

### Post by hemebond on 2011-11-02
> **sarahlizz3 said:**
> It can take black and white photos/video fine, but if I turn back on the color it looks like this (attached).I get that if I choose a high resolution.

---

### Post by sarahlizz3 on 2011-11-02
> **hemebond said:**
> I get that if I choose a high resolution.

I hadn't thought of that so I tried changing the resolution (and all other settings in Cheese) and same thing - still weird lines going across, saturation is all wrong, and parts of photo are black and white.

---

### Post by VinnyJ1701 on 2011-11-05
Arkara,

You saved me and many from a world of hassle.  Your solution worked.  Thank you.   I came so so close to using another distro.

Peace

---

### Post by johnnervo on 2011-11-06
Hey I had a similar problem with my logitech c210 on ubuntu 11.10.  I fixed it by installing qc-usb-source from synaptic package manager...it seems to work fine now. :)

---

### Post by crgutierrez on 2011-11-06
Great simple solution. Many Thanks

---

### Post by iamgeniusrnti on 2011-11-11
Hey,

I had the same problem on two different  computers (my Kubuntu on a 64 bit PC and my Ubuntu 10.10 running on my  Acer One), both with Pulse Audio.

I spent about a week tweaking on it and I fixed it. thru no help of  anyone whatsoever.  While everyone had bright ideas that seemed to work  for them, none worked for me.

Then a week later, I was poking around the skype forum and someone was  using pavucontrol to adjust his stereo output.  So I did the standard  sudo apt-get install pavucontrol.  Then I gave it a whirl and caught  something evil.

On my Acer One:  If you run pavucontrol and go to input devices, it sees  my microphone as a stereo input.  I noticed when I 'unlinked' the  left/right channels and turned the RIGHT channel all the way DOWN, and  the LEFT channel all the way up, the microphone instantly started  working.  Skype fixed.  

On my Kubuntu PC:  Whenever Skype was up and running, pavucontrol  detected Skype was trying to use the microphone jack for a source and  not my Logitech webcam mic.  So I clicked on the button and changed the  source over to webcam mic.  Problem was instantly fixed.

While the Ubuntu Linux Gods found this problem uninteresting, I hope  this posting will one day help out another of us little people.

---

### Post by mrady on 2011-11-27
mmm Arkara didn't seem to help me with my C510...

---

### Post by mrady on 2011-11-27
oh dear how simple to fix...found I had to select the mic from the webcam under Input in Sound Settings...for some reason it didn't do this automatically!


[LIST=1]
[*]Left-click on the speaker icon (by default at the right of the top desktop panel next to the network applet) and select **Sound Preferences** 
[*]In **Sound Preferences**, select the **Input** tab 
[/LIST]

---

### Post by mrady on 2011-11-27
Just plugged in new C510 and had mic problems too...took me ages to find this...oh dear how simple to fix...found I had to select the mic from the  webcam under Input in Sound Settings...for some reason it didn't do this  automatically!


[LIST=1]
[*]Left-click on the speaker icon (by default at the right of the top desktop panel next to the network applet) and select **Sound Preferences**
[*]In **Sound Preferences**, select the **Input** tab
[/LIST]

---

### Post by exanime on 2011-12-02
I had the same issue and some people are saying that it is a kernel problem; however, I noticed that the mic worked ok in Audacity although manual steps needed to be taken to choose the right mic.

That led me to believe that it was not a kernel issue in my case at least... 

I then proceeded to install pavucontrol and running it while attempting the test call with skype showed that skype (as well as other programs) were defaulting to the regular mic jack and therefore getting no signal since I didn't have anything plugged there. pavucontrol allowed me to change this skype selection to the usb mic and voila! everything works!

---

### Post by brick78 on 2011-12-02
My issues were the same as others - scrambled sound and strange video. These have been fixed by:
Audio - arkara's suggestion (audio)
Video - by an update within the last month

---

### Post by jorgebit on 2012-01-15
> **arkara said:**
> Hello. The problem is that the microphone is in the wrong sound rate by the pulse audio. As a user do the following:

```
gedit $HOME/.pulse/daemon.conf
```and put the following line on the file:
```
default-sample-rate = 16000
```save it, and then restart pulseaudio as a user with the following command

```
pulseaudio --kill && pulseaudio --start
```This should solve the problem.
Thank you Arkara! :KS:KS:KS:KS:KS
You solved my problem with microphone for camera Logitech C160.

---

### Post by ILGato on 2012-07-22
> **arkara said:**
> Hello. The problem is that the microphone is in the wrong sound rate by the pulse audio. As a user do the following:

```
gedit $HOME/.pulse/daemon.conf
```

and put the following line on the file:
```
default-sample-rate = 16000
```

save it, and then restart pulseaudio as a user with the following command

```
pulseaudio --kill && pulseaudio --start
```

This should solve the problem.


I signed up only to thank you!
Thank you very much! your advise solved the problem!
:guitar:

---

### Post by Deevad on 2012-09-29
> **arkara said:**
> Hello. The problem is that the microphone is in the wrong sound rate by the pulse audio. As a user do the following:

```
gedit $HOME/.pulse/daemon.conf
```and put the following line on the file:
```
default-sample-rate = 16000
```save it, and then restart pulseaudio as a user with the following command

```
pulseaudio --kill && pulseaudio --start
```This should solve the problem.

Worked for camera C110 Logitech , under 11.10 , and 10.04. ( couldn't test if solved on 12.04 )   You made my day sir ! Big thanks !

---


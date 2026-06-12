---
title: "Microphone problem in Skype on Ubuntu 11.10"
date: 2011-10-05
forum: Multimedia Software
---

### Post by kakesh on 2011-10-05
I have Ubuntu 11.10 beta 2 with all updates and after installing some updates mic stop working in Skype. It works, but the sound slutters. Before everything was fine. Mic works when I try to record something, but not in Skype. I use Microsoft USB Web camera Lifetime HD-6000. In sound settings webcam set to be default input device. If anyone know how to fix it let me know.

I'm new in Ubuntu so if you nee any additional info, please give me a hint on how to get it. :-) 

Thanks

---

### Post by Dadoo on 2011-10-06
Hello,

I am experiencing the same problem with the mention that I don't use an USB microphone. 

I've installed Ubuntu 11.10 since alpha 2, but I've got this problem only for one or two weeks. I'll wait to see if other people have the same problem when the non-beta version of Ubuntu 11.10 is released. If only those that have installed the beta or alpha versions experience this problem, probably I'll try to reinstall my system.

Anyway if someone figured a way to solve this problem, I'm interested to find out the solution.

Thanks

---

### Post by kakesh on 2011-10-06
Looks like after last update everything works fine.

---

### Post by slave2live on 2011-10-07
Same problem here. After Ubuntu upgrade, webcam and sound dead. Sound apparently only coming through in bursts. On test call I record the full time but only get playback of the first word.

The web cam did not work. In Cheese I get a very bad picture with lines. I attempted a fix I saw on youtube and does now get a webcam Imange but very bad and sad quality.

Please, If someone have advice, I will appreciate it. Alternative, I will have to downgrade two versions.

I run on an Acer Extensa 5620Z

---

### Post by Dadoo on 2011-10-08
> **Dadoo said:**
> Hello,

I am experiencing the same problem with the mention that I don't use an USB microphone. 

I've installed Ubuntu 11.10 since alpha 2, but I've got this problem only for one or two weeks. I'll wait to see if other people have the same problem when the non-beta version of Ubuntu 11.10 is released. If only those that have installed the beta or alpha versions experience this problem, probably I'll try to reinstall my system.

Anyway if someone figured a way to solve this problem, I'm interested to find out the solution.

Thanks

It seems to work after the upgrade I made this morning.

---

### Post by kjano on 2011-10-08
same problem here but I found a very strange solution. if you open the sound settings and move the input sound volume a bit skype will work perfectly. as soon as you shut the sound settings the micro quality in skype will go down again....:confused:

---

### Post by gahramanov on 2011-11-21
Just installed Ubuntu 11.10 few days ago. Having problem with the microphone. Not only on Skype. When tried to record on Sound Recorder, there was not any voice completely.

---

### Post by exanime on 2011-12-02
I had the same issue and some people are saying that it is a kernel problem; however, I noticed that the mic worked ok in Audacity although manual steps needed to be taken to choose the right mic.

That led me to believe that it was not a kernel issue... 

I then proceeded to install pavucontrol and running it while attempting the test call with skype showed that skype (as well as other programs) were defaulting to the regular mic jack and therefore getting no signal since I didn't have anything plugged there. pavucontrol allowed me to change this skype selection to the usb mic and voila! everything works!

---

### Post by aleoo on 2012-01-15
> **gahramanov said:**
> Just installed Ubuntu 11.10 few days ago. Having problem with the microphone. Not only on Skype. When tried to record on Sound Recorder, there was not any voice completely.

I have the same problem, with pavucontrol nothing changed: maybe I just need someone who suggests me 
the configuration or the settings I should choose to make it work.
I posted other info here: [http://ubuntuforums.org/showthread.php?t=1908893](http://ubuntuforums.org/showthread.php?t=1908893)

---

### Post by sardhwk on 2012-02-10
Same here. Internal and external microphone do not work with Skype 2.2. Installed upgrades of edubuntu 10.11 and PAV control but still no luck. Speakers and microphone works with audacity and sound recoder. Why not with skype? Please help. In the mean time I also lost my login sound . Not sure it is related. Please advice.

---

### Post by dabl on 2012-02-10
On pavucontrol, make sure you have (a) muted any unused channel, and (b) pressed the "Set as Fallback" button on the channel you wish to use.

[[IMG]http://img542.imageshack.us/img542/1235/pavucontrolinput.png[/IMG]](http://imageshack.us/photo/my-images/542/pavucontrolinput.png/)

I am using KDE 4.7.2, on Debian, and Skype is working when I use the mic in my webcam.

---

### Post by sardhwk on 2012-02-14
My Pavcontrol looks different. Config shows Internal audio, Profile   with 4 options: analog stero duplex, analog stereo output, analog stereo  input and Off. If I run testcall in skype and open PAVcontrol/recording  it shows skype input mono. The sound bar registers what looks like a  very low noise but the test shows the microphone did not work. Any  ideas?

---

### Post by Dale61 on 2012-02-23
I had a similar problem, but found that as the microphone is a mono device, it conflicts with itself in stereo mode.

Go in to your sound control and find the microphone setting screen.  You should see a slider for left and right channel. Slide BOTH fully to left, then lock one.  Slide the other to about 70%, then click apply (or enter), then restart Skype.

Make a test call, check your microphone and hopefully, problem solved.

---

### Post by daniroma on 2012-03-19
@Dale61: Your solution is good. Solve my problem.
I use XUBUNTU 11.10

---


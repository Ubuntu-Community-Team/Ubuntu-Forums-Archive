---
title: "Pulse Sound in Skype Keeps Dying"
date: 2009-04-27
forum: Multimedia Software
---

### Post by demarshall on 2009-04-27
I am running Jaunty Jackalope and using version 2.0.0.72 version of Skype with audio set to use Pulse. For some reason every so often I stop receiving sound from the other person in a voice call. When I shut down and restart Skype it starts working again. Is there some way to keep audio working properly so that I don't have to restart Skype continuously?

---

### Post by rabbit251 on 2009-04-27
I have the same problem. Also notable on my system is that after the moment when sound breaks, Skype freezes on a quit attempt and the processes (skype and skype.real) have to be ended manually. Hoping for a solution as well, though I have no hint of one unfortunately.

---

### Post by dbulante on 2009-04-28
I am having the same audio problem.

---

### Post by psyke83 on 2009-04-29
Within Skype's options, ensure that you set your microphone to the appropriate ALSA device, *not* the pulse device. See Appendix C of my PulseAudio guide for more information.

---

### Post by rabbit251 on 2009-04-29
@psyke83: My mic in Skype has been set to the ALSA device HDA Intel (hw:Intel,0) for some time now, even though it makes my input volume uncomfortably low. When I switch to the pulse input device, I suffer from [the compounding audio delay issue]("http://ubuntuforums.org/showthread.php?t=976850"). Those are the only two mic settings that Skype won't reject entirely.

---

### Post by demarshall on 2009-04-30
Even after following the advice in this forum, I'm still losing sound in Skype.  :-(

---

### Post by Arup on 2009-04-30
> **demarshall said:**
> Even after following the advice in this forum, I'm still losing sound in Skype.  :-(

In that case remove Skype and install Skype static-oss from repos.

---

### Post by stepanstas on 2009-05-01
Same issue.  I think this is because of 9.04.  The latest version of Skype if for 8.10 (which is understandable, 9.04 is new).

Here is some more detail on what happens.  In my case I can talk to the person for a few min.  Maybe 5 or so.  After that the sound coming out of Skype stops.  The person on the other line can hear me as if nothing happened but I cannot hear the person.

I am not sure what Skype static-oss is but I would prefer to stick to official skype software.  Once the sound stops the program freezes up if you try to close it.  If you don't try to close it, it keeps working for chat and stuff.  You can call people and they will hear you, but you cannot hear them.

At this point you must go to System>Admin>System Monitor and Kill (not end) Skype.  Relaunch and then talk for another few min before this happens again.

I doubt there will be a solution, but I think we should become aware of the problem so it can be fixed next update.

---

### Post by demarshall on 2009-05-02
Excellent sumation of the problem but sometimes I am able to hear the other person in a voice chat for up to a couple of hours.

I tried replacing Skype with Skype-oss but could not figure out what to set things to in Skype. I tried every possible setting but nothing worked. Perhaps I am missing files or need to have the sound set to oss somewhere.

---

### Post by Arup on 2009-05-02
Skype OSS is in the official repos as well and in your case, it will use the OSS drivers instead of PULSE to solve your issues. I have manually selected ALSA device with regular Skype and have no issues of CPU usage or drop outs.

---

### Post by rabbit251 on 2009-05-03
> I tried replacing Skype with Skype-oss but could not figure out what to set things to in Skype. I tried every possible setting but nothing worked. Perhaps I am missing files or need to have the sound set to oss somewhere.

Go to the System menu, Preferences and then Sound. Try changing all your devices to OSS, and then test the various Skype settings again. I think this would be a necessary step in getting skype-static-oss to work.

But you might also try plain skype-static. Sometimes that does it for people over skype proper or static-oss, and it kind of seems like a better bet to me in your situation since the problem was not in getting ALSA to sound for awhile, but rather in the frequent breakage.

Unfortunately, I'm not confident that the Skype version change will help you, demarshall. I certainly haven't solved the problem in my own Skype, where the only "workaround" has been to use Ekiga instead (which has been treating me pretty well, to tell the truth ;) ). Is there anyone who has dealt with this same issue and then gotten it fixed?

---

### Post by demarshall on 2009-05-07
I've tried installing Skype-static but Skype still stops getting or playing the incoming voice messages after a time.

Does anybody know what else to do?

---

### Post by patep34 on 2009-05-07
Ah! glad to know I'm not the only one. Just got my new Dell Mini 9 & was hoping to use it mainly for Skyping. Should I go back to 8.10???

---

### Post by evanrmurphy on 2009-05-08
> **patep34 said:**
> Ah! glad to know I'm not the only one. Just got my new Dell Mini 9 & was hoping to use it mainly for Skyping. Should I go back to 8.10???

If you are really planning to use it primarily for Skype, that might be wise. I think it depends on how much patience you can maintain for frequent restarts. I'd love to file a bug for this, but I don't think Skype issues are within Ubuntu's jurisdiction.

---

### Post by demarshall on 2009-05-08
There is an issue filed with Skype which I commented on.

[https://developer.skype.com/jira/browse/SCL-392](https://developer.skype.com/jira/browse/SCL-392)

I guess we'll just have to wait until their programmer(s) decide to work on it.  :-(

---

### Post by lorebett on 2009-05-08
I have the same problem, and skype, after a while, starts to eat CPU!

---

### Post by jsowoc on 2009-05-08
I have a working configuration of Skype on 64-bit Ubuntu 9.04.

I am using "skype-static-oss", installed "alsa-oss", and run Skype as "aoss skype".

The CPU useage is low, and the sound quality is decent.

---

### Post by evanrmurphy on 2009-05-09
> **jsowoc said:**
> I am using "skype-static-oss", installed "alsa-oss", and run Skype as "aoss skype".

Interesting, I didn't know about alsa-oss. So it's like an OSS compatibility layer for ALSA? Can you use it on a per-application without disrupting your overall audio setup?

---

### Post by sandy8925 on 2009-05-09
THere is a checkbox near the mike option. If you check it then Skype will automatically change your mic volume which is probably why it is low.

---

### Post by psyke83 on 2009-05-09
Note: aoss is obsoleted by padsp when using PulseAudio. See my guide for information on using OSS applications with PulseAudio.

---

### Post by evanrmurphy on 2009-05-09
> **psyke83 said:**
> Note: aoss is obsoleted by padsp when using PulseAudio. See my guide for information on using OSS applications with PulseAudio.

The section in your guide specifically dedicated to Skype does not fix the dying-sound issue we're having with skype and skype-static. Is there a chance that padsp can fix it for skype-static-oss?

> THere is a checkbox near the mike option. If you check it then Skype will automatically change your mic volume which is probably why it is low.Unfortunately, I don't think this addresses the problem of audio output spontaneously failing in Skype.

---

### Post by Caseyjp on 2009-05-09
Reporting the same issue here with official skype + ubuntu 9.04. Sound and video work just fine for several minutes, and then sound dies.  Outbound audio works, as well as video (both ways) but the inbound audio fails.  Skype must be killed via cmdline or top or sysmon in order to restart the cycle.

Oh and lets not use pulse for this?  If ubuntu has settled on pulse (and it most certainly has) then "use alsa or oss" isn't an optimal solution as most users (myself included) would prefer the system to just work as advertised.
If I want to futz with the guts, I'd install Arch or gentoo or slack.

The "lets change this and that and the other thing and then download something else and then hope that it resolves the problem" isn't optimal, desired, needed or otherwise helpful.

What is needed is a solution or an existing bug report to attach to if anyone has one.

This application worked GREAT under 8.10, but is fubar under 9.04 without jumping through hoops...and then sound still dies after a time and cpu spikes through the roof.

As skype didn't change, rather Ubuntu DID, and broke a damn important application on my system, I'm now back to dual booting an old xp partition to talk to my girlfriend who is currently really long distance.  Yeah, I know, my problem, but isn't the system supposed to improve from release to release rather than *** backwards?  It DID work.  Now it don't work worth a damn.

Just fyi.

---

### Post by psyke83 on 2009-05-09
Recently, I haven't used Skype for conversations longer than 10 minutes, so I can't test this issue.

I would agree with others who have suggested the folly of disabling PulseAudio for one buggy application.

Try the ALSA version of Skype with the appropriate settings for PulseAudio, *or* try the OSS version of Skype (in Medibuntu: skype-static-oss) with the padsp (not aoss) wrapper. See my guide for more details.

If neither of the above options resolve this issue, there are some more options for Jaunty users:

[LIST=1]
[*]Enable the "proposed" repository and upgrade to kernel 2.6.28-12-generic. It contains bugfixes for some ALSA kernel drivers (primarily intel-hda and intel8x0) that were problematic with PulseAudio.
[*]Upgrade to PulseAudio 0.9.15 via [Luke Yelavich's PPA]("https://launchpad.net/~themuso/+archive/ppa").
[/LIST]
I recommend all users upgrade to the proposed kernel, but I am a little more hesitant to recommend PA 0.9.15. At least on my system, it has a minor bug in which initialization fails upon first login. Manually restarting PulseAudio resolves the problem, though.

---

### Post by evanrmurphy on 2009-05-09
> **Caseyjp said:**
> [snip] Oh and lets not use pulse for this?  If ubuntu has settled on pulse (and it most certainly has) then "use alsa or oss" isn't an optimal solution as most users (myself included) would prefer the system to just work as advertised.
If I want to futz with the guts, I'd install Arch or gentoo or slack.

The "lets change this and that and the other thing and then download something else and then hope that it resolves the problem" isn't optimal, desired, needed or otherwise helpful.

What is needed is a solution or an existing bug report to attach to if anyone has one.

This application worked GREAT under 8.10, but is fubar under 9.04 without jumping through hoops...and then sound still dies after a time and cpu spikes through the roof.

As skype didn't change, rather Ubuntu DID, and broke a damn important application on my system, I'm now back to dual booting an old xp partition to talk to my girlfriend who is currently really long distance.  Yeah, I know, my problem, but isn't the system supposed to improve from release to release rather than *** backwards?  It DID work.  Now it don't work worth a damn. [snip]

I agree that discarding the PulseAudio sound server is undesirable. What using skype-static-oss together with the padsp wrapper supposedly allows you to do is use the OSS version of Skype, without affecting your overall audio configuration in the least.

Even though Skype broke on the Ubuntu upgrade, and that's really frustrating, I'm not sure it's totally fair to blame Ubuntu for it. The PulseAudio plugin for Skype is one of the weakest links in the chain here, and I'm not sure who was in charge of it. (Since Skype is proprietary and closed-source, I was inclined to think it was the Skype team, but I could be mistaken. Maybe someone else could shed light on this.)

Cheers to long distance! ;) Have you tried using Ekiga? Since issues with Skype started compounding, my girlfriend and I switched to talking over SIP. We've been largely satisfied with the results.

---

### Post by Caseyjp on 2009-05-09
> **evanrmurphy said:**
> 
Cheers to long distance! ;) Have you tried using Ekiga? Since issues with Skype started compounding, my girlfriend and I switched to talking over SIP. We've been largely satisfied with the results.

Going to try it, but my initial tests with ekiga produced shoddy video quality, while skype produces a much MUCH cleaner video image.  While me and the significant other aren't as fussed about video, it is really nice to sit and talk and see clearly.  Will give it a test again, but skype was optimal.  (Still is as dual boot is still an option, just not my favorite as its the ONLY thing that the XP partition is being used for.)

---

### Post by psyke83 on 2009-05-09
> **Caseyjp said:**
> Going to try it, but my initial tests with ekiga produced shoddy video quality, while skype produces a much MUCH cleaner video image.  While me and the significant other aren't as fussed about video, it is really nice to sit and talk and see clearly.  Will give it a test again, but skype was optimal.  (Still is as dual boot is still an option, just not my favorite as its the ONLY thing that the XP partition is being used for.)

Skype most likely has a high-bandwidth relay (or P2P) service for cases where the client cannot make direct connections to the destination caller.

Since Ekiga doesn't have such a fallback, you may have been unknowingly connected to a slow STUN server because the necessary ports for voice and video over IP were blocked (either by the operating system or your router). You may want to investigate this and re-test Ekiga.

---

### Post by ZoltAi on 2009-05-10
lucky you then ... I have problem as I'm experiencing huge delays during call ... using UBU 9.04 and skype 2.0.0.72 ... settings for sound devices in skype are set to pulse for in and out because any others won't work 

any suggestions ??  

thanks for help
ZoltAi

---

### Post by evanrmurphy on 2009-05-10
> **ZoltAi said:**
> lucky you then ... I have problem as I'm experiencing huge delays during call ... using UBU 9.04 and skype 2.0.0.72 ... settings for sound devices in skype are set to pulse for in and out because any others won't work

any suggestions ??  

thanks for help
ZoltAi

Hi ZoltAi, a lot of people have been experiencing this issue when "Sound In" is set to "pulse". (The compounding delay really is frustrating--I can't stand it.) You've said the other choices don't work, but maybe you can double check: I think most people have found that all fail except for one, whose name typically references their hardware. For me it's "HDA Intel (hw:Intel,0)", but there are three other "HDA Intel..." choices that don't work.

The one change usually eliminates the delay problem. Unfortunately, on my system it's exchanged for an uncomfortably low maximum mic volume (not everyone experiences this), and I still have the spontaneously failing output sound problem which is the main topic of this thread. Please follow up on how this works for you!

---

### Post by ZoltAi on 2009-05-10
thanks a lot evanmurphy ... it seems to solve my problem with delay and i did not notice any significant drop on capture volume ... I will test it for a while and if you guys not hear from me anymore it means it's sorted ... just for future readers below I specify what I have in my skype settings 

sound in: HDA Intel (hw: Intel,0)
sound out: pulse
ringing: pulse

UBUNTU 9.04 with Alsamixer 1.0.18 with skype 2.0.0.72

cheers and good luck

---

### Post by evanrmurphy on 2009-05-10
> **ZoltAi said:**
> thanks a lot evanmurphy ... [snip]

You're welcome!

---

### Post by Cenoforums on 2009-05-18
Glad to know that this issues is widespread in 9.04, for a while i thought it'd be a problem with the alsa driver for my soundcard.

I substituted regular skype with skype-static-oss from medibuntu. I tried running it without "padsp" and already on the sound configuration the only device I have available on all 3 entries is "/dev/dsp" and the sound works in the test call.

Does this solve the problem for anyone? Since I have /dev/dsp already listed, is padsp still needed?

---

### Post by demarshall on 2009-05-20
That solution (using the oss version) doesn't work for me. I can't get any sound using it so went back to the static version. The static version dies as much as the original version does. Is there any hope for this problem?

---

### Post by Cenoforums on 2009-05-20
Yesterday I tried the static oss version and it worked flawlessly in a 1h30m call. Didn't have to do anything, no padsp, no fiddling with the settings...

Now my problem that the sound structure is ruined. My wine apps stopped working, I had to change the driver to OSS, starting the apps with padsp didn't solve anything. Same thing for firefox. I cannot do anything with the audio as long as skype is running. I have no idea what the static-oss package installed.

---

### Post by 243kof on 2009-05-23
In my case, I seem to have worked around this problem by selecting the "hardware" option (hw:Nvidia,0 for me) for everything: Sound in, Sound out and ringing. Sound doesn't die anymore, plus no stattering. The downside is that sound is played from the left speaker output only.

---

### Post by neumeka on 2009-05-29
I tried selecting the hardware as the sound in, and it does fix the problem: skype does not seem to die anymore.  But now it seems like I can't use any other program that uses sound while I am using skype.  For example, if I have rythmbox playing a song and someone calls me, it will tell that person that there was a problem with my sound and the call will fail.  I have to stop playing the song and call them back.  In addition I am experienceing the same problem: sound from skype from only one ear.

---

### Post by 243kof on 2009-05-29
> **neumeka said:**
> I tried selecting the hardware as the sound in, and it does fix the problem: skype does not seem to die anymore.  But now it seems like I can't use any other program that uses sound while I am using skype.  For example, if I have rythmbox playing a song and someone calls me, it will tell that person that there was a problem with my sound and the call will fail.  I have to stop playing the song and call them back.  In addition I am experienceing the same problem: sound from skype from only one ear.

yes, i can confirm this. It's a little uncomfortable, but it will have to do until this bug gets fixed..

---

### Post by eraserB20 on 2009-05-31
For me adding 'options snd-hda-intel model=ref' to /etc/modprobe.d/alsa-base.conf' on a fresh install solved all my sound problems (DELL E520 / Sigmatel STAC 92xx) . You must change 'ref' for your hardware ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)). 

In Skype I set everything to 'pulse'.

---

### Post by demarshall on 2009-06-01
> **eraserB20 said:**
> For me adding 'options snd-hda-intel model=ref' to /etc/modprobe.d/alsa-base.conf' on a fresh install solved all my sound problems (DELL E520 / Sigmatel STAC 92xx) . You must change 'ref' for your hardware ([https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)). 

In Skype I set everything to 'pulse'.

Adding this line seems to have improved my Skype performance but I still lose audio. Each call seems to last longer though.

---

### Post by evanrmurphy on 2009-06-01
> **neumeka said:**
> I tried selecting the hardware as the sound in, and it does fix the problem: skype does not seem to die anymore.  But now it seems like I can't use any other program that uses sound while I am using skype.  For example, if I have rythmbox playing a song and someone calls me, it will tell that person that there was a problem with my sound and the call will fail.  I have to stop playing the song and call them back.  In addition I am experienceing the same problem: sound from skype from only one ear.

> **243kof said:**
> yes, i can confirm this. It's a little uncomfortable, but it will have to do until this bug gets fixed..

I experienced this issue for awhile, but unfortunately can't remember the fix. Here are a couple of threads about the same (or a similar) problem, though neither offers an obvious solution: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=863597](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=863597), [http://ubuntuforums.org/showthread.php?t=820910](http://ubuntuforums.org/showthread.php?t=820910).

---

### Post by PGScooter on 2009-06-03
Another success story for skype-static-oss on Jaunty 9.04. For anyone reading this that hasn't tried it, please do! I did the following commands:
```

sudo apt-get purge skype
sudo apt-get install skype-static-oss

```
The look of skype was EXACTLY the same, it had kept my login and my contacts and it worked without having to change anything!

Note that I have not yet tested it for a conversation more than 10 minutes.

---

### Post by xx58 on 2009-06-03
):P I download Ubuntu 9.04 and I had sound problems and many different problems. So. I tried hard and then I just downgrade back to Ubuntu 8.10 and everything works again. Now I will wait some 3 month and will try again Ubuntu 9.04, will wait upgrades and then I will see. Right now, best choice still Ubuntu 8.10 or 8.04. Good luck everybody with his choices.....

---

### Post by beefcurry on 2009-06-07
I've fixed the compound delay issue in skype thanks to this thread, but there still seems to be an issue with the random sound input drops. Any launchpad bug report for this?

---

### Post by mfarewell on 2009-07-15
There are numerous bugs mentioned but because the problem is spread between ubuntu, skype and medibuntu no one seems to be taking notice of it. It was definitely caused in upgrade to Jaunty, the only fully working solution is downgrading to 8.10, or switching operating system :(. For those of us who depend on Skype this is a very serious bug that damages the credibility of ubuntu linux.

I think this bug was probably created for another reason but seems the most active so everyone should post there [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203) . This skype forum also discusses it to [http://forum.skype.com/index.php?showtopic=306381](http://forum.skype.com/index.php?showtopic=306381) it is mentioned on Medibuntu launchpad a few times but no activity there e.g. [https://bugs.launchpad.net/medibuntu/+bug/395642](https://bugs.launchpad.net/medibuntu/+bug/395642).

---

### Post by igorzwx on 2009-07-15
Skype works well on my old boxes with Ubuntu 9.04.
No delay, no latency, no noise.
Fantastic performace.
It is very simple.
Remove Pulse and Alsa,
install OSS4 and skype-static-oss

---

### Post by Caseyjp on 2009-07-15
> **igorzwx said:**
> Skype works well on my old boxes with Ubuntu 9.04.
No delay, no latency, no noise.
Fantastic performace.
It is very simple.
Remove Pulse and Alsa,
install OSS4 and skype-static-oss

You're kidding.  Simple?  Sure if you want to bork your box for ubuntu going forward including upgrades, you go right ahead.  This is NOT a solution to the issues that are occurring that will be workable for the majority of folks who are having problems.

Ubuntu is supposed to "just work", and issues like this with a program that cannot be considered anywhere "niche" is unacceptable. 

The problem, as I see it at this point is that skype itself hasn't updated their application to work with the newer pulse audio solutions, and I'm thinking their support folks need to be the ones hammered on to resolve it.  

Ekiga is not a good solution for a lot of us as it will NOT connect to the people we wish to talk to as they are on skype.

So we hope these issues can get resolved.  The difference, once again between open source and closed source computing.  Open source...WE FIX. Closed source...we HOPE. sigh.

---

### Post by igorzwx on 2009-07-15
I am not kidding.
I have both Ekiga and Skype working perfectly on
my old boxes (of 2003 and 2001) with Ubuntu 9.04 and Ubuntu Lite Beta

[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

I have several Ubuntus in multiple boot.

2 Ekigas have not been tested yet.
My friends are on holidays.
Very few people have Ekiga installed.
Could you please help me to test them?

---

### Post by Caseyjp on 2009-07-15
> **igorzwx said:**
> I am not kidding.
I have both Ekiga and Skype working perfectly on
my old boxes (of 2003 and 2001) with Ubuntu 9.04 and Ubuntu Lite Beta

[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

I have several Ubuntus in multiple boot.

2 Ekigas have not been tested yet.
My friends are on holidays.
Very few people have Ekiga installed.
Could you please help me to test them?

OSS4 is not supported by Canonical or Ubuntu.  This isn't an acceptable solution to the issue. Sorry.  You may have the application working fine with that solution but as I said before, its NOT an acceptable solution to the issue(s) most of us are currently experiencing, simply as OSS4 is NOT a sound solution supported by this distro in any way shape or form. 

What needs to happen is skype releasing a new version of the application with proper pulse audio support, which it apparently is getting close to doing at this point via their support forums.  (One of their devs has started to respond to questions in the linux section there.)

---

### Post by igorzwx on 2009-07-15
If I understood you correctly, you believe that Skype is responsible for
all my troubles with Ubuntu 9.04.
I have been busy for months fixing Ubuntu 9.04 (screen, Audacity, etc.)
Thanks, now I know who is responsible!

---

### Post by jdkchem on 2009-07-21
> **Caseyjp said:**
> OSS4 is not supported by Canonical or Ubuntu.  This isn't an acceptable solution to the issue. Sorry.  You may have the application working fine with that solution but as I said before, its NOT an acceptable solution to the issue(s) most of us are currently experiencing, simply as OSS4 is NOT a sound solution supported by this distro in any way shape or form. 

What needs to happen is skype releasing a new version of the application with proper pulse audio support, which it apparently is getting close to doing at this point via their support forums.  (One of their devs has started to respond to questions in the linux section there.)

You're absolutely right.  Do you have links to the posts in the Skype forums?

---

### Post by igorzwx on 2009-07-21
To run Skype with pulse one may need a very powerful computer, I presume.
Has anybody tried Skype with Pulse on a quadro core?

---

### Post by jdkchem on 2009-07-21
> **igorzwx said:**
> To run Skype with pulse one may need a very powerful computer, I presume.
Has anybody tried Skype with Pulse on a quadro core?

Skype worked fine with pulseaudio in Hardy and Intrepid.  In Jaunty audio dies during calls.  Presume whatever you wish but that is hardly an indicator of needing a very powerful computer.

---

### Post by igorzwx on 2009-07-21
As I have already told here.
My Skype works well on my old boxes with Ubuntu 9.04 and OSS4.
Because OSS4 is very different from pulseaudio.
OSS4 can be used on old boxes and pulse not.
Nothing work with pulse on my old boxes 
(I mean audio aps, of course)

---

### Post by demarshall on 2009-07-22
igorzwx, perhaps you should give us some steps to follow to get OSS4 working on our computers. I am probably not the only one who is wary of uninstalling Pulse and Alsa in case we can't get OSS4 to work.

---

### Post by igorzwx on 2009-07-22
Hi all!

no secret here.
read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

This howtos are designed for Ubuntu 9.04

You can search my post in this forum too.

I am usually trying such things on my old box which I use for experiments.
You can install another Ubuntu 9.04 in dual boot and try there to see if it works
on your box.

---

### Post by jdkchem on 2009-07-23
> **igorzwx said:**
> Hi all!

no secret here.
read this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

This howtos are designed for Ubuntu 9.04

You can search my post in this forum too.

I am usually trying such things on my old box which I use for experiments.
You can install another Ubuntu 9.04 in dual boot and try there to see if it works
on your box.

Perhaps had you made this information available instead of calling people lazy you would not look like a jerk.

---

### Post by igorzwx on 2009-07-23
"Perhaps had you made this information available instead of calling people lazy you would not look like a jerk."

Sorry, I did not call anybody lazy, and I see no grounds for this interpretation.
Your post is #55 (page 6)
In my post #47 (page 5), 
you may find a link to my howto which explains how to install OSS4 on Ubuntu 9.04 and Ubuntu 8.04

It was not any bad intention in this post too, just information.

---

### Post by igorzwx on 2009-07-23
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
QUOTE:
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by jdkchem on 2009-07-24
> **igorzwx said:**
> "Perhaps had you made this information available instead of calling people lazy you would not look like a jerk."

Sorry, I did not call anybody lazy, and I see no grounds for this interpretation.
Your post is #55 (page 6)
In my post #47 (page 5), 
you may find a link to my howto which explains how to install OSS4 on Ubuntu 9.04 and Ubuntu 8.04

It was not any bad intention in this post too, just information.

No you did not call anyone lazy that was somebody on the Skype forum, my apologies.  You should have put the links in your first post.  Nothing is more irritating than the jokers whose only contribution is to say "mine works" or that everyone should use their solution.

OSS4 is a usable solution but not for everybody.  I looked at it and the disadvantages outweigh the advantages, for me.

---

### Post by igorzwx on 2009-07-24
"OSS4 is a usable solution but not for everybody.  I looked at it and the disadvantages outweigh the advantages, for me."

OSS4 is not a universal solution for all problems, of course.
I cannot use my iMic USB with OSS4, for example.
It is not a big problem for me, however.

---

### Post by jdkchem on 2009-07-24
Not the greatest fix but it seems to work for me.

You will need to add the ppa for Luke Yelavich [https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)

This will update pulse to 0.9.15.  I also included the proposed repo and updated the kernel to 2.6.28-14.

Skype now seems to be reliable however when I use pulse as the audio sources in skype the result is craptastic.  You will need to choose the appropriate hardware source.  You'll only get audio in one speaker and you cannot use any other audio apps.  I got close to 2 hours without losing the audio.

Another option is to use a usb headset.  This option provides audio in both channels and you can use other audio apps.  I did not use this option on a call so I cannot comment on it's reliability.  You'll want to plug in the headset after boot so that pulse does not se it.

As a solution it is not great but. . . .

---

### Post by martinbaselier on 2009-07-24
> 
OSS4 is a usable solution but not for everybody. I looked at it and the disadvantages outweigh the advantages, for me.

What disadvantages do you mean?
I'm wondering since I'm creating a howto and I could not really find any disadvantages.
But I definitely would like to know them, to create a full picture.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

---

### Post by jdkchem on 2009-08-04
> **igorzwx said:**
> "OSS4 is a usable solution but not for everybody.  I looked at it and the disadvantages outweigh the advantages, for me."

OSS4 is not a universal solution for all problems, of course.
I cannot use my iMic USB with OSS4, for example.
It is not a big problem for me, however.

I had no mic at all in OSS.  I did not even bother with the USB headset I have.  The jack worked fine.

---

### Post by jdkchem on 2009-08-04
> **martinbaselier said:**
> What disadvantages do you mean?
I'm wondering since I'm creating a howto and I could not really find any disadvantages.
But I definitely would like to know them, to create a full picture.


USB is pretty much unusable and for my laptop, Dell XPS M1530 I had no mic.

---

### Post by jdkchem on 2009-08-04
As an update to my "fix" I have not had Skype lose audio.  On the downside, and this is a failing of pulse, I had to adjust the mic volume in 3 separate places before it worked.  Additionally banshee and Skype, probably other apps as well, hijack the master volume control.  In banshee the master audio level will "reset" to previous levels if you change tracks.

Why do I have to use 2-3 separate sliders to adjust audio levels?  When I adjust the master volume that should stay set.  If I want to adjust the audio level of and app shouldn't that level be relative to the master level?  Shouldn't adjustment also be independent of the master volume?  That is supposed to be a "feature" of pulse!

The only positive is that now Skype does not drop the audio after 90+ minutes.

---

### Post by Arup on 2009-08-04
> **jdkchem said:**
> I had no mic at all in OSS.  I did not even bother with the USB headset I have.  The jack worked fine.

Actually its due to the mic issue I switched to OSS4 apart from the far superior sound. In ALSA, it would go low after every reboot and I would have to set it via alsamixer.

---

### Post by DrWilken on 2009-08-11
News from the Skype from Linux developer(s) -> [http://share.skype.com/sites/linux/](http://share.skype.com/sites/linux/)

"A quick status update for all of you out there longing for news:

I&#8217;ve been struggling with getting PulseAudio support to work on a range of different server versions &#8211; it wasn&#8217;t that simple. Suffice to say, different pulseaudio versions fail differently. We&#8217;re planning to support down to 0.9.10, but my suggestion is: if you want good sound &#8211; upgrade to 0.9.15 at least.
The video is now working, but there are a few corner cases we want to weed out before releasing.
UI work is finished for this release and no additional work is planned in this area so far."

FYI -> The release mentioned above ISN'T public yet, but it seems it's almost (tm) there... ;)

---

### Post by DrWilken on 2009-08-12
I just followed [this howto]("http://worldforum.pardus-linux.nl/index.php?topic=1763.0") to make Skype (only) not use PulseAudio and it works like a charm... :)

The only difference is that in the part where You have to comment out **load-module module-hal-detect** You have to do it like this:

Change this:
```
### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect tsched=0
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif
```

to this:
```
### Automatically load driver modules depending on the hardware available
#.ifexists module-hal-detect.so
#load-module module-hal-detect tsched=0
#.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
#.endif
```

(Comment out the whole section and not just the load-module module-hal-detect part)

Works for me... :)

Remember to select skypein as your input device and skypeout as your ringing and output device in Skype... :)

---

### Post by patep34 on 2009-08-25
> **Arup said:**
> In that case remove Skype and install Skype static-oss from repos.


I finally did this a few weeks ago & I'm happy to report that it solved all my Skype problems! I had a nice 2 hr conversation w/ friends in Hawaii a few days ago.

I don't use a mic so I haven't tested that. Sound seems to be ok in all other programs too.

Happy there's a solution,
Patep

---

### Post by lucho64 on 2010-02-11
I installed the last version of Skype on my Jaunty amd-64 system. Big mistake. No video or audio:mad:. Looking through the post in this and other threads, however, I identified pulse-audio as the culprit. Killed it and removed it with apt-get. Rebooted and now I have sound in skype ( both from my mike and from the outside )

---


---
title: "Pulse audio"
date: 2010-03-14
forum: Multimedia Software
---

### Post by poliltimmy on 2010-03-14
when will this asinine program be an option instead of the continuous pain where a pill can not reach!

---

### Post by RedSingularity on 2010-03-14
Whats the problem with it?

---

### Post by ndefontenay on 2010-03-14
Is that a request for help? Or just a rant. 
If you want to vent a bit, go to the communite cafe.

---

### Post by poliltimmy on 2010-03-15
Sorry guys! I guess it was a rant of sorts. I just am not looking forward to the headache of disabling pulse on about 20 of my friends and families computers. Some who have left Windows all together because I turned them on to Ubuntu.  Since it is becoming more ingrained with each release, and 10.04 just around the corner, I am wondering if this is the release that will leave your setting intact or is it back to working around it.  I already hide the "New Disto" button from them!

---

### Post by Grenage on 2010-03-15
Disabling it on 20 machines?  While every situation is different, I've only ever come across one machine (in about 50+) where pulseaudio was causing a problem.

What issues are you having?

---

### Post by gradinaruvasile on 2010-03-15
> **Grenage said:**
> Disabling it on 20 machines?  While every situation is different, I've only ever come across one machine (in about 50+) where pulseaudio was causing a problem.

What issues are you having?

Lol i had problems with it on every machine i installed it on... Some programs just dont work with it right.

Anyway i installed Debian on all 3 computers i use where PulseAudio is optional and i only needed it for bluetooth handsfree on my work laptop, i installed it and guess what - every program works well with the sound unlike Ubuntu where i had troubles with it. 

So its not PulseAudio per se that is causing issues, its the integration of it, forcing all alsa streams through the PA server. In Debian you have ALSA and PulseAudio - programs that can use PA use it, programs who know only ALSA use that. I created a pulse plugin in ALSA (2 lines in .asoundrc) so that i can redirect sound to the PA server if i want to.
Everyone is happy with this setup.

---

### Post by kostkon on 2010-03-15
And from my experience, in 90% of cases people tend to blame PulseAudio for their ALSA problems (driver problems, volume level problems etc.) because they don't actually know how the audio stack in Ubuntu works.

Every ALSA-based program that is well-written, i.e. it sends its sound to dmix instead of trying to access the hardware device directly, works fine with PulseAudio's ALSA plugin.

---

### Post by poliltimmy on 2010-03-15
Disabling it on 20 machines? While every situation is different, I've only ever come across one machine (in about 50+) where pulseaudio was causing a problem.

What issues are you having?
-------------------------------------------------------------------------------------
Besides high CPU usage, music and video snapping, crackling and popping like a popular cereal from Kellogg, unless you configure it to leave you alone, absolutely nothing.  
 
  I just do not like being a beta product guinea pig. Where is the 'freedom' in not having a choice upon installation. Or in it not leaving your sound server config files intact. Non tech end users want to be able to upgrade without this hassle.

  I guess I will learn a new distro starting next month, rather than go through the hassle. And I will apologetically explain to  my friends and family that Ubuntu has become the beta distro, so you can learn a new one or buy a Windows disk. Which do you think they will choose? 

 Feel free to move this to the rant section, you know the spot on this site where "go back to Windows' is the most popular answer. 

  I would love to see these 'mythical' computers that pulse automagicly "Just Works" on.

---

### Post by poliltimmy on 2010-03-15
> **kostkon said:**
> And from my experience, in 90% of cases people tend to blame PulseAudio for their ALSA problems (driver problems, volume level problems etc.) because they don't actually know how the audio stack in Ubuntu works.

Every ALSA-based program that is well-written, i.e. it sends its sound to dmix instead of trying to access the hardware device directly, works fine with PulseAudio's ALSA plugin.

Strange how disabling pulse and installing the latest ALSA fixed them all. Ubuntu is in denial!

---

### Post by Grenage on 2010-03-15
> **poliltimmy said:**
> I would love to see these 'mythical' computers that pulse automagicly "Just Works" on.

Those would be *most* Ubuntu installs.  This is definitely a rant; pulseaudio is far from beta, and almost all problems come from poorly-coded software (kostkon covered that).  The benefits of PA for the average user far outweigh the problems a handful of people experience.

As for the implementation of PA going againt freedom... what?  Ubuntu is a Distro aimed at those who want something simple to install and use, not those who want to answer 60 questions during the process.  It's not hard to remove.  Perhaps you might try LinuxFromScratch, I'm sure your family and friends would get on great with that.

---

### Post by poliltimmy on 2010-03-15
> **Grenage said:**
> Those would be *most* Ubuntu installs.  This is definitely a rant; pulseaudio is far from beta, and almost all problems come from poorly-coded software (kostkon covered that).  The benefits of PA for the average user far outweigh the problems a handful of people experience.

As for the implementation of PA going againt freedom... what?  Ubuntu is a Distro aimed at those who want something simple to install and use, not those who want to answer 60 questions during the process.  It's not hard to remove.  Perhaps you might try LinuxFromScratch, I'm sure your family and friends would get on great with that.

It would be just as simple to leave it out and add it to the repos. And I knew the the inevitable "go somewhere else" would pop up. We are talking one pop-up during installation. Such as a choice of standard install or custom. Harly 60 questions. Do you alway exaggerate.

---

### Post by Grenage on 2010-03-15
> Harly 60 questions. Do you alway exaggerate.

Well it seemed like I was in good company, what with working PA installs being 'mythical'.

> I knew the the inevitable "go somewhere else

I was being sarcastic; most of my friends and family would have a stroke installing LFS.

The problem that the devs likely have is that everyone has a preference; I don't like Empathy, you don't like PulseAudio, and Joe Bloggs over there doesn't like OpenOffice.  They just go with what will keep most people happy, and the rest can add/remove as they wish.

---

### Post by poliltimmy on 2010-03-15
> **Grenage said:**
> Well it seemed like I was in good company, what with working PA installs being 'mythical'.



I was being sarcastic; most of my friends and family would have a stroke installing LFS.

The problem that the devs likely have is that everyone has a preference; I don't like Empathy, you don't like PulseAudio, and Joe Bloggs over there doesn't like OpenOffice.  They just go with what will keep most people happy, and the rest can add/remove as they wish.

gradinaruvasile and I both agree that they are mythical. So I am not the only one.

Google search inquiry: Results 1 - 10 of about 88,300 for how to remove pulseaudio. (0.39 seconds)  And those links provide even more links. I guess that many hits for a problem means it is trivial. Just how many times does that question have to be asked before Ubuntu gets the message that we want it as repo not default? Hence the frustration. 

 It is disingenuous to say it can be simply removed.  That is simply not true it takes Ubuntu Desktop with it. 

# apt-get remove pulseaudio
Reading package lists… Done
Building dependency tree
Reading state information… Done
The following packages will be REMOVED:
pulseaudio ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1393kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
 Having that metapackage installed marks which distro you’re using, and upgrades use it for making individual package choices.

 Stop the FUD!

---

### Post by gradinaruvasile on 2010-03-15
The sound problems may come from poorly coded stuff, but this means many many programs are poorly coded - and PulseAudio cannot cope with those problems obviously.
These are facts.
Fact is that Ubuntu wants to be an easy to use distro, but it has a sound system that is WELL KNOWN to cause problems - regardless of poor code etc whatever.

And i have a simple question - why PulseAudio works well on Debian and doesnt wrecks other programs (poorly coded or not) sound?

I know what is the theory here: an easy to set up and easy to use sound system, where devices can be added/removed dynamically, the sound streams can be easily manipulated.

But in practice, only a handful of people REALLY NEED PULSEAUDIO - i do only on my laptop and its because i use a bluetooth handsfree - on my 2 desktops i use i have ABSOLUTELY NO USE FOR IT. And noone in my family who uses Linux does (i got rid of it because it caused sound disruption and everybody is happy with the sound and dont miss it a bit).

ALSA is a good and rugged sound system, building on years of experience - it really "just works". And it very well supports multiple streams or whatnot.

And Ubuntu is an expanding distro, many people try it to get a feel of Linux.
Why mess up one of the essential parts of the operating system willingly when there is a really good, tested and working alternative?

Just a quick suggestion:

Make it optional, like many other distros have it and make some mechanism to tell the user when he really needs it (such as connecting bluetooth sound devices). That will keep everybody happy.

And please dont say that "the others are to blame". Make your stuff to work as ALSA does. Period.
I as a user absolutely hate that i cannot play a simple game (actually all games i played had problems with PulseAudio) because someone decided to include a half-baked, bugfilled sound server in the OS base KNOWING that it will break stuff.

---

### Post by kostkon on 2010-03-15
> **poliltimmy said:**
> gradinaruvasile and I both agree that they are mythical. So I am not the only one.

Google search inquiry: Results 1 - 10 of about 88,300 for how to remove pulseaudio. (0.39 seconds)  And those links provide even more links. I guess that many hits for a problem means it is trivial. Just how many times does that question have to be asked before Ubuntu gets the message that we want it as repo not default? Hence the frustration.
Yes, because there is a lot of misinformation about PulseAUdio and as I have seen in the ubuntu IRC channels and on various forums, when you ask for help for your sound problems, the first thing they almost always recommend you (obviously they are the people that actually *don't* know how to help you) is to remove PulseAudio, for some reason, without even asking you for any additional information.

---

### Post by kostkon on 2010-03-15
> **gradinaruvasile said:**
> But in practice, only a handful of people REALLY NEED PULSEAUDIO - i do only on my laptop and its because i use a bluetooth handsfree - on my 2 desktops i use i have ABSOLUTELY NO USE FOR IT. And noone in my family who uses Linux does (i got rid of it because it caused sound disruption and everybody is happy with the sound and dont miss it a bit).
Only a handful?!!!! There are millions and millions of people using USB audio devices; headsets, speakers, pre-amps and so on!!!
> **gradinaruvasile said:**
> ALSA is a good and rugged sound system, building on years of experience - it really "just works". And it very well supports multiple streams or whatnot.
PulseAudio sits on top of ALSA, it's just a sound mixer, (Windows Vista and 7 and Mac OS X have also a software mixer) it doesn't replace ALSA. And yes, ALSA has its own primitive software mixer but it's... primitive... For example, you have to fiddle with conf files and so on if you want to use external audio devices etc etc. Do you actually want people to give
```
asoundconf "set-default-card
```
logout and re-login every time they want to use their USB headset? For me, this is absurd...

---

### Post by Grenage on 2010-03-15
I uninstalled pulseaudio here, just to check.  It didn't need or ask to remove ubuntu desktop.

> Google search inquiry: Results 1 - 10 of about 88,300 for how to remove pulseaudio

> Results 1 - 10 of about 42,700,000 for my dog dances.

Do you think 42 million people have dancing dogs?

---

### Post by poliltimmy on 2010-03-15
> **Grenage said:**
> I uninstalled pulseaudio here, just to check.  It didn't need or ask to remove ubuntu desktop.





Do you think 42 million people have dancing dogs?

Notice I posted the output in the terminal in my post? Is this just more FUD? And by the way you asked the wrong person about dancing dogs. I have a Pomeranian mix that I have in fact taught to dance. It's great at parties.  But I have yet to get a computer to play nice with pulse.

---

### Post by nerdy_kid on 2010-03-15
> **poliltimmy said:**
> gradinaruvasile and I both agree that they are mythical. So I am not the only one.

Google search inquiry: Results 1 - 10 of about 88,300 for how to remove pulseaudio. (0.39 seconds)  And those links provide even more links. I guess that many hits for a problem means it is trivial. Just how many times does that question have to be asked before Ubuntu gets the message that we want it as repo not default? Hence the frustration. 

 It is disingenuous to say it can be simply removed.  That is simply not true it takes Ubuntu Desktop with it. 

# apt-get remove pulseaudio
Reading package lists… Done
Building dependency tree
Reading state information… Done
The following packages will be REMOVED:
pulseaudio ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1393kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
 Having that metapackage installed marks which distro you’re using, and upgrades use it for making individual package choices.

 Stop the FUD!




```


sudo chmod -x /usr/bin/pulseaudio

```
done.

:D

---

### Post by Grenage on 2010-03-15
Are are my posts inciting Fear Uncertainty and Doubt?  You're the one proclaiming PA to be the AntiChrist of the Audio world.

Touchê on the dog, though.

---

### Post by poliltimmy on 2010-03-15
> **nerdy_kid said:**
> ```


sudo chmod -x /usr/bin/pulseaudio

```
done.

:D

what does that line actually do. I am a newbie. I've only been around since 6.06

---

### Post by poliltimmy on 2010-03-15
> **Grenage said:**
> Are are my posts inciting Fear Uncertainty and Doubt?  You're the one proclaiming PA to be the AntiChrist of the Audio world.

Touchê on the dog, though.

Well maybe not the Antichrist, but for me PA is audio hell. I'm hoping for a clean experience next month. Music is my main usage.

---

### Post by Grenage on 2010-03-15
It makes pulseaudo unexecutable :)

Music is not my main use, so that may be why I haven't run into the problems you have.  After all this, I'll probably end up having massive issues with it two weeks down the line.

---

### Post by poliltimmy on 2010-03-15
> **Grenage said:**
> It makes pulseaudo unexecutable :)

Music is not my main use, so that may be why I haven't run into the problems you have.  After all this, I'll probably end up having massive issues with it two weeks down the line.

Exactly! That is what I am wondering.  Will it all start again next month. And that is why I feel it should be in the repos. 





Is there a "undo" line for that code?

---

### Post by kostkon on 2010-03-15
> **Grenage said:**
> Music is not my main use, so that may be why I haven't run into the problems you have.  After all this, I'll probably end up having massive issues with it two weeks down the line.
????
Do you care to elaborate?

---

### Post by nerdy_kid on 2010-03-15
> **poliltimmy said:**
> Exactly! That is what I am wondering.  Will it all start again next month. And that is why I feel it should be in the repos. 





Is there a "undo" line for that code?

```

sudo chmod +x /usr/bin/pulseaudio

```

you actually need to do 
```

killall pulseaudio

```
after disabling it.  (the first command i gave)

---

### Post by Grenage on 2010-03-15
> **kostkon said:**
> ????
Do you care to elaborate?

How do you mean, sorry?

---

### Post by poliltimmy on 2010-03-15
> **nerdy_kid said:**
> ```

sudo chmod +x /usr/bin/pulseaudio

```

you actually need to do 
```

killall pulseaudio

```
after disabling it.  (the first command i gave)

If I run the first line and I end up screwed some how, not that I believe I will, how would I revert?

---

### Post by gradinaruvasile on 2010-03-15
> **kostkon said:**
> Only a handful?!!!! There are millions and millions of people using USB audio devices; headsets, speakers, pre-amps and so on!!!

PulseAudio sits on top of ALSA, it's just a sound mixer, (Windows Vista and 7 and Mac OS X have also a software mixer) it doesn't replace ALSA. And yes, ALSA has its own primitive software mixer but it's... primitive... For example, you have to fiddle with conf files and so on if you want to use external audio devices etc etc. Do you actually want people to give
```
asoundconf "set-default-card
```
logout and re-login every time they want to use their USB headset? For me, this is absurd...

I did say that there should be a program that detects such cases... And i think a graphical ALSA sound card manager isnt impossible to make, either.

My problem here is that from 8.04 onwards there is a default sound server in Ubuntu that is plainly buggy. People who make decisions like this should have a working solution when a stable version is released.

One real world example: A collegue installed Ubuntu 9.10 on his laptop. Then he had sound problems with virtually any sound using application - he works with Linux servers  for a living BTW. And no comprehensive way to solve them (audio just skipped or stopped in middle of movies, no flash sound etc etc). Finally he said that : "sound just sucks in Ubuntu. Period."
 
I really prefer less but working features and an optional piece of software in case i need it and some notification about it:

"Hey, you connected a USB card - do you want to install a program that manages it? Or make it default sound card under ALSA?" - I dont think the world would end if things would work this way...
Is it impossible to work on ALSA's mixer component to make it less primitive?

And the fact that Windows and Mac already has it should not mean that Ubuntu should have it before making it really stable IMO.

PS: Disabling PulseAudio will take away the volume control applet. I dont know that was intentional or a side effect of something but it isnt nice. At all.

---

### Post by Grenage on 2010-03-15
```
sudo chmod +x /usr/bin/pulseaudio
```

Re-enables it :)

---

### Post by poliltimmy on 2010-03-15
> **Grenage said:**
> ```
sudo chmod +x /usr/bin/pulseaudio
```

Re-enables it :)

Thanks. I do not like to anything a box if I can not back up and regroup.

---

### Post by Yellow Pasque on 2010-03-15
> I just am not looking forward to the headache of disabling pulse on about 20 of my friends and families computers.
This is what scripts are for ;)

I'm not a big fan of pulseaudio either, but the Ubuntu devs have chosen to use it in their GNOME flavor (and it might be coming to KDE). They're not going to change that anytime soon. Thankfully, you have choice:

- Remove Pulse (lots of guides for that)
- Use another distro (Debian/sidux, Arch Linux, etc.)
- Use Xubuntu. Heck, you can even install the GNOME stuff you want on top of that. In Synaptic, go to Settings -> Preferences and uncheck/disable 'Consider recommended packages as dependencies' to prevent pulseaudio stuff from installing (use the --no-install-recommends argument if using apt)

---

### Post by DJonsson2008 on 2010-03-15
all my audio stopped after an update from 9.10 to 10.04

that simple one line disable pulse audio 
command did the trick for me, 

sudo chmod -x /usr/bin/pulseaudio

i ran it 
rebooted and audio came back - thanks

---

### Post by DJonsson2008 on 2010-03-15
To recap...(make pulse audio unexecacutable in effect turning it off.

# Turn pulseaudio on
sudo chmod +x /usr/bin/pulseaudio
# reboot or execute pulseaudio

# Turn pulseaudio off
sudo chmod -x /usr/bin/pulseaudio
killall pulseaudio

I'm using an Maudio Delta 44 card and it seems 
to work much better with PulseAudio off.

---

### Post by poliltimmy on 2010-03-15
> **DJonsson2008 said:**
> all my audio stopped after an update from 9.10 to 10.04

that simple one line disable pulse audio 
command did the trick for me, 

sudo chmod -x /usr/bin/pulseaudio

i ran it 
rebooted and audio came back - thanks

That is what I was hoping for. Some thing simple as ALSA is all I need.

---

### Post by markbuntu on 2010-03-15
Don't blame pulseaudio just because it is so poorly implemented in Ubuntu, blame the ubuntu people. Pulseaudio works far better in Fedora and Mandriva and SUSE and a bunch of other distros because it actually gets integrated into the entire audio system and implemented as the default sound server. 

Ubuntu seems to have just tossed the pulseaudio daemon on top of the alsa stack and disregarded any need for critical libs and configurations and front ends to actually make it work as a default sound server and be controllable. 

Personally I like pulseaudio once I get it all dialed in. I really have doubts that I could deal with all my sound hardware devices (2 sound cards, usb headset, webcam mic, HDMI, bluetooth) without it. Plus it is very easy to set up to play over a network.

---

### Post by soltanis on 2010-03-16
ALSA makes me want to ram my face through a wall.

That's why I installed OSS4. Goodbye, sound problems.

---

### Post by DJonsson2008 on 2010-03-16
Oss, Alsa, Pulse Audio = Freedom of Choice

Pulse audio using 10.04 on one my installs using an onboard
sound card worked instantly with all audio programs. This includes Skype which in the past was a real monster to configure.
Perhaps that is what the majority of people are finding.

On another machine Pulse Audio seemed to take over during my upgrade from 9.10 to 10.04. A warning or option during upgrade would of saved me time and trouble.

---

### Post by pickarooney on 2010-03-16
> **Grenage said:**
> 
As for the implementation of PA going againt freedom... what?  Ubuntu is a Distro aimed at those who want something simple to install and use, not those who want to answer 60 questions during the process. 

If that is actaully its aim, it fails miserably. I have only once managed to upgrade a Ubuntu distro without having to completely reconfigure the audio, and in many cases the video on each of my machines, going all the way back to Dapper. I think the successful one was Intrepid to Jaunty on the desktop.

No distribution can succeed in being at once progressive, stable and user friendly - it's a complete contradiction. If you keep changing things (particularly changing things that work for things that don't work or haven't been tested) this is the antithesis of user-friendly. 

I like that Ubuntu is progressive and tries out new things with each iteration, but the downside is inevitably a rushed release with a silly, calendar-based deadline.

The obvious solution all round is to simply not perform distro upgrades just because they're there. I'm happy with Jaunty, for example, and have no intention of rushing out to install Lucid, a distro currently at Alpha, next month. That's just asking for trouble.

---

### Post by DJonsson2008 on 2010-03-16
I hear what you are saying and there is always room for
improvement. 

There is also the option of doing a fresh install, when the features of a major upgrade-update drives the need for upgrade/update. Some people only do fresh re-installs.
The tradeoffs, options and foibles of re-install/upgrade are though part of every OS I've dealt with Mac, Win and Linux.

Faster SSD drives will make fresh installs faster in the future, with of 20 machines under your umbrella its certainly easy to understand why you would want the option at the point of update, 

Have you logged this as a bug? and/or where is the next step to get this to the attention of the developers, because I do see similar warnings about overwriting some conf files during the install process it seems easy enough to place a similar option there such as "This machine is not using Pulse Audio, do you wish to make Pulse Audio your dominant Audio driver?"

---

### Post by Grenage on 2010-03-16
> **pickarooney said:**
> If that is actaully its aim, it fails miserably. I have only once managed to upgrade a Ubuntu distro without having to completely reconfigure the audio, and in many cases the video on each of my machines, going all the way back to Dapper. I think the successful one was Intrepid to Jaunty on the desktop.

Ill agree that you take a risk when upgrading.  While I've never had a botched machine during the process, I've had plenty of glitches.

---

### Post by poliltimmy on 2010-03-16
> **DJonsson2008 said:**
> I hear what you are saying and there is always room for
improvement. 

There is also the option of doing a fresh install, when the features of a major upgrade-update drives the need for upgrade/update. Some people only do fresh re-installs.
The tradeoffs, options and foibles of re-install/upgrade are though part of every OS I've dealt with Mac, Win and Linux.

Faster SSD drives will make fresh installs faster in the future, with of 20 machines under your umbrella its certainly easy to understand why you would want the option at the point of update, 

Have you logged this as a bug? and/or where is the next step to get this to the attention of the developers, because I do see similar warnings about overwriting some conf files during the install process it seems easy enough to place a similar option there such as "This machine is not using Pulse Audio, do you wish to make Pulse Audio your dominant Audio driver?"

Exactly! Everyone of us has most likely owned a windows computer. When you install a program in windows it asks questions, where you want it etc. Most of them ask about default or custom set up. People who do not know what they are doing select the default...next, next,next. correct? People are already used to questions during installs. What Ubuntu is saying is 'our users are not smart enough to answer one question during installation'. The simple fact we use Ubuntu should tell them they are wrong.

---


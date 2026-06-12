---
title: "Skype high cpu usage ubuntu 9.04 64-bit"
date: 2009-04-16
forum: Multimedia Software
---

### Post by nkef on 2009-04-16
I am experiencing high cpu usage with skype when i have voice conversation,
I am using Ubuntu 9.04 64 bit with latest updates.
The skype package i am using is 2.0.0.72-0medi.

My soundcard driver is snd_hda_intel and skype is configured to use pulseaudio.
The problem arises also when i am making the test call, skype reaches 195% cpu 
usage (my system has a quad core i7 920).

---

### Post by vlovich on 2009-04-16
it seems the upgrade to jaunty also broke the working config I had in hardy (I decided to take a risk & go with the package configuration rather than maintaining mine).  my recommendation would be to just switch to using raw alsa rather than pulse (which is what I'm doing), or try the OSS version of skype (supposedly the OSS-pulse wrapper causes less issues for skype).

---

### Post by benj1 on 2009-04-16
was the pun on the thread title intentional???:)


Skype high cpu usage ubuntu 9.04 64-bit
Sky high cpu usage ubuntu 9.04 64-bit

---

### Post by nkef on 2009-04-16
> **vlovich said:**
> it seems the upgrade to jaunty also broke the working config I had in hardy (I decided to take a risk & go with the package configuration rather than maintaining mine).  my recommendation would be to just switch to using raw alsa rather than pulse (which is what I'm doing), or try the OSS version of skype (supposedly the OSS-pulse wrapper causes less issues for skype).

I made a fresh install of jaunty with the beta 9.04 cd, situation did n't got any better.
Is there any way get more information?

The only think i can verify for the moment, is that skype executable takes 195% cpu time,
when i am doing a conversation.

---

### Post by vlovich on 2009-04-16
i've had issues where skype would start hogging the cpu even without a conversation (I think it was an issue with establishing a connection with pulse)

---

### Post by dof on 2009-04-18
I had the same problem on 32 bit. The problem was pulse or more accurate skype & pulse. I've changed the sound settings and it works fine, 3-5% cpu instead of 60% when in a call.

---

### Post by Bytesource on 2009-04-18
> **dof said:**
> I've changed the sound settings and it works fine, 3-5% cpu instead of 60% when in a call.

I have the same problem here with Skype on 32-bit Jaunty. Could you tell me what your sound settings look like now?

Thanks!

---

### Post by dof on 2009-04-19
> **Bytesource said:**
> I have the same problem here with Skype on 32-bit Jaunty. Could you tell me what your sound settings look like now?

Thanks!

These are my settings

---

### Post by Sophont on 2009-04-21
I had a maxed out CPU while running Skype. PA alone used > 20% of the (single) CPU (old laptop, installed Jaunty A4 and upgraded since then - mostly default settings, changed nothing about PA/sound).

The maxed CPU led to increasing delays between what I said and the other 5 in conference (used while gaming - the game runs on another machine).

I resolved the problem by installing the statically compiled version of Skype for OSS and start it with "padsp skype".
I did not remove or kill PA, nor did I change any other setting.

---

### Post by rileinc on 2009-04-22
I'm experiencing the same issue with Jaunty 64bit beta. Making a test sound and test call loads one of my cores to 100%.
I thought it was a bad upgrade so I did a complete install, and that didn't help at all.

I haven't tried the release candidate yet. I'll wait until the final release (in 2 days) and test it.

For me, Skype worked out of the box on Intrepid and Hardy. Seeing an old problem come back to haunt Ubuntu users is really disheartening.

---

### Post by qzio on 2009-04-23
I have this issue too. upgraded from working 8.10 to 9.04, x broke but was fixable, but this... i don't know where to even start searching :(

skype uses near 100% of cpu, and I'm not even in a call.

upgrades are evil!

---

### Post by Sophont on 2009-04-24
> **qzio said:**
> I have this issue too. upgraded from working 8.10 to 9.04, x broke but was fixable, but this... i don't know where to even start searching :(

skype uses near 100% of cpu, and I'm not even in a call.

upgrades are evil!

Did you try what I posted above?
Install OSS static compiled version of Skype and start with "padsp skype".

You'll find "skype-static-oss" in the Medibuntu repo:
[http://www.medibuntu.org/]("http://www.medibuntu.org/")

---

### Post by rileinc on 2009-04-25
> **Sophont said:**
> Did you try what I posted above?
Install OSS static compiled version of Skype and start with "padsp skype".That solves the CPU problem. *However*, the Medibuntu OSS build hogs my sound device. Whenever Skype is on call, no other software can capture or output sound.

---

### Post by nkef on 2009-04-25
> **rileinc said:**
> That solves the CPU problem. *However*, the Medibuntu OSS build hogs my sound device. Whenever Skype is on call, no other software can capture or output sound.

Dmix is disabled in ubuntu's Alsa configuration, so there no minixing in alsa. Pulseaudio server and oss skype build cannot use alsa concurrenlty.

---

### Post by Arup on 2009-04-26
> **dof said:**
> These are my settings

This solution worked out well for my install, I had the same CPU spike issues which was solved. I use the built in soundcard on my Intel motherboard. This is what my settings look like.

Thanks to you.

---

### Post by rileinc on 2009-04-26
> **Arup said:**
> This solution worked out well for my install, I had the same CPU spike issues which was solved. I use the built in soundcard on my Intel motherboard. This is what my settings look like.

Thanks to you.Could you also post a screenshot of your System Preferences -> Sound?
Thanks in advance.

---

### Post by Arup on 2009-04-26
> **rileinc said:**
> Could you also post a screenshot of your System Preferences -> Sound?
Thanks in advance.

Here you go, I haven't touched anything in sound preferences after fresh install, left all in default.

---

### Post by rileinc on 2009-04-26
> **Arup said:**
> Here you go, I haven't touched anything in sound preferences after fresh install, left all in default.Thanks for the quick reply! One more question: with your current setting, does Skype hog the sound device at all? e.g., When you're on a call, is your music or movie player able to produce sound?

---

### Post by ram130 on 2009-04-27
THis fixed my problem too..but  it hogs the sound card! Any other solution?? :confused:

---

### Post by Arup on 2009-04-27
> **rileinc said:**
> Thanks for the quick reply! One more question: with your current setting, does Skype hog the sound device at all? e.g., When you're on a call, is your music or movie player able to produce sound?

Well generally when I am on Skype I don't usually do anything but yes, it does hog the card.

---

### Post by nkef on 2009-04-28
I reported the issue at launchpad: Bug 362203
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/362203)

---

### Post by ram130 on 2009-04-29
Now i have problem with skype taking the sound card exclusively. What do i need 2 sound cards?? There must be a better solution than this, come on!... guys i run a internet radio so i am constantly listening it so having skype take over like its the boss not gonna work. Someone please fix this with a update soon, or ill be forced back to windows in a virtual machine with skype.:confused:

and u call this  a helpful forum:(


I have Ubuntu 9.04 32bit!!!!!!!!!!!

Amd 64 dual core 2.4GHZ and 2 GB of RAM. ...if tho thats not important.

update: If its pulse that is selected and i launch skype and leave it for 3-5min  it start to use 100% cpu on one core....some plz tell me its not my fault...

---

### Post by Arup on 2009-04-29
Don't use Pulse for audio, select your hardware by name, if its Intel make it so, if its audigy, then select that. I use Skype for audio and video and my CPUs' never go over 10% max.

---

### Post by ram130 on 2009-04-30
> **Arup said:**
> Don't use Pulse for audio, select your hardware by name, if its Intel make it so, if its audigy, then select that. I use Skype for audio and video and my CPUs' never go over 10% max.

U see  when you dont read, you wont understand. That solution works, but it hogs the sound card! Meaning i wont be able to play audio in firefox or my virtual machine or media player at the same time....So  the question is how do we work around this? 

a note: with pulse however  all audio can be played at the same time  without hogging the sound card. Its just the high cpu usage and skype crashing that sucks.

---

### Post by ram130 on 2009-05-03
ANy updates?

---

### Post by harvodan on 2009-05-03
I'd like some details on what is actually causing this bug. So far I don't have the slightest idea as to what the cause is. Some help on this would be great, right now I've reverted back to the old Ubuntu 8.10 because of this. This may seem a little extreme, but I'm a heavy skype user.

---

### Post by Arup on 2009-05-03
I used Skype with video for about an hour on my Jaunty today, peak CPU usage on my 8 cores was around 8%.

---

### Post by harvodan on 2009-05-03
Did you by any chance use pulseaudio for your skype sound devices?

---

### Post by jasidog on 2009-05-03
Just a me too post. On 32 bit jaunty.

---

### Post by khelben1979 on 2009-05-03
> **Arup said:**
> I used Skype with video for about an hour on my Jaunty today, peak CPU usage on my 8 cores was around 8%.

That also means if Skype were using 1 core only it would take 80% of the cpu. Phew!

Old versions of Skype together with a Windows XP system don't even come close to those power requirements on my old Pentium 4 processor which I have at home, from my own experience.

---

### Post by ashkool on 2009-05-05
A me too post. Ubuntu 9.04, 32 bit. Using pulse for soundin, ringing.

---

### Post by Arup on 2009-05-05
The problem is not Jaunty, according to Ubuntu devs, Skype in the repos is from Hardy and since Skype is closed source, there have been no updates to it yet. Time to hammer Skype devs at their forum I guess.

---

### Post by harvodan on 2009-05-06
I found a similar thing happening to me when recording audio with Audacity. I think this whole thing with Skype is a bug with PulseAudio, version 0.9.14, that happens when recording audio. On PulseAudio 0.9.10 under Intrepid, I have no such trouble whatsoever. This is the 32-bit version.

---

### Post by Domas on 2009-05-14
Hi all,

Well, I am using Pulse audio and had the same problem, on the call my CPU was always 100%. What I did is: unticked "Allow Skype to automatically adjust my mixer levels". After that all went just fine. On call Skype is using max 10% of CPU, sound is clear. Hope for somebody will work.

Ubuntu 9.04
Skype: skype-debian_2.0.0.72-1_i386.deb
Sound devices > Options:

Sound In: USB Audio (plughw:Audio,0)
Sound Out: pulse
Ringing: pulse

Regards,
Dom

Edit: still sometimes goes to 100% :(

---

### Post by ecoxmit on 2009-05-14
Domas, 

That didn't work for me.

---

### Post by ram130 on 2009-05-16
My problem is fixed. Here is what helped me fix my problem, I hope it will benefit those who are still in problems with Skype.

[http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/](http://www.econowics.com/news-from-the-net/170/skype-problem-with-audio-playback-ubuntu-810-intrepid-ibex/)

After I did the above, I then set my sound in to my Usb camera mic, sound out and  ringing to Default. After which I restarted.

  I am now happily on a Skype call while listening to music in Firefox or my fav media player and best of all no high cpu usage. Hope it helps.):P

---

### Post by darthmob on 2009-05-16
I have got the same problem with my 32bit jaunty.
setting the sound devices in skype to the hardware ones does not really solve it, as sound playback is only on the left side and multiple sound sources are not possible either.

I do not want to replace pulseaudio with something else as it works for all other programs. the way it is I'm using [ekiga]("http://www.gnomemeeting.org/") to call people (the downside is they need to install it, too).

---

### Post by darthmob on 2009-05-16
a friend of mine suggested it and I followed [this great guide]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/") to disable pulseaudio and enable alsa instead. now multiple sound sources work, skype does not hog the cpu and my sound is not muted anymore on startup.

PS: is it not possible to delete the own posts anymore?!

---

### Post by nrohluap on 2009-05-27
> **dof said:**
> These are my settings

I have had problems since upgrading to 9.04 with Skype eating 100% of one CPU core. Not consistent, but happens once or twice a day (probably same as vlovich's issue). Once it does so, it will not post or receive chat info and makes no sounds. I have to shut Skype down (usually with kill -9) and restart to get it back.

While it was running normally, I tried tinkering with the sound settings. I had been using "pulse" for both sound out and for ringing. I changed Sound Out to HDA Intel (hw:Intel,0) and sound worked OK - test sound played. I changed "ringing" to be the same HDA, and I only get sound out of the left channel (something that Linux Skype has done for me for a long time). When I switched Rining back to Pulse and hit "Make a test sound," it stuttered, then stopped ... and the CPU went to 100%. No more sound, no more chats.

If I leave the sound settings on HDA, Skype won't make sounds for chat etc. if any other app is using the soundcard. Can't start a call, either - "problem with audio playback" dialog. Have to restart pulse fairly often in this scenario - Skype refuses to make any sound or place/receive calls, but bouncing pulse will temporarily get it back.

Neither one is a good solution.

 - Paul
(jaunty x64, Thinkpad T61p)

---

### Post by rileinc on 2009-06-11
Not a solution, just giving up on pulseaudio altogether. Thanks to nkef @ #14, and darthmob @ #38 for pointing me to the right direction. 

First, follow the steps here to disable pulseaudio: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/) 
Second, follow the first post here [http://bbs.archlinux.org/viewtopic.php?id=19904](http://bbs.archlinux.org/viewtopic.php?id=19904) to set up dmix for alsa, and set Skype to launch with aoss.
Third, set Skype's sound out and ringing to 'asymed'. 

I tested this in VBox, and I only get sound on the left side. Skype worked without using 100% CPU or hogging the sound device. 

Does anyone get the same result?

---

### Post by viduliya on 2009-06-12
> **rileinc said:**
> Not a solution, just giving up on pulseaudio altogether. Thanks to nkef @ #14, and darthmob @ #38 for pointing me to the right direction. 

First, follow the steps here to disable pulseaudio: [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/) 
Second, follow the first post here [http://bbs.archlinux.org/viewtopic.php?id=19904](http://bbs.archlinux.org/viewtopic.php?id=19904) to set up dmix for alsa, and set Skype to launch with aoss.
Third, set Skype's sound out and ringing to 'asymed'. 

I tested this in VBox, and I only get sound on the left side. Skype worked without using 100% CPU or hogging the sound device. 

Does anyone get the same result?

Thank you very much for the information here.  Thank you ram130.  I followed the steps on your first link [http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/) on 3 machines using Janty.  Two with Intel cards and one with Nvidia card.  All of them have sound working perfectly for me without the pulsaudio pains.  My CPU usage is way down when I use Skype other software to play audio and a slew of other pulseaudio related problems are gone for now...  :D

---

### Post by nmaster on 2009-06-14
You should try this:[INDENT] 
[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[*]Reboot system and use the default sound setting in skype.
[/LIST]
 [/INDENT]I'm using skype from [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
You can call sudo dpkg -i -force-architecture <name of skype deb> to use the i386 package on x64.  I just did this, but I haven't had any problems yet.  I hope it works for the rest of you.


i kept a copy of 70pulseaudio just in case; i don't like deleting stuff if i don't know EXACTLY what it does.

---

### Post by PasQty on 2009-07-06
tra@lala:~$ *sudo vi /etc/pulse/daemon.conf*
of course it apply pulseaudio.
and try that setings more info about it i was put on: [http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9](http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9)

[I]high-priority = yes
nice-level = -11

realtime-scheduling = yes
realtime-priority = 5
resample-method = src-linear

default-fragments = 8
default-fragment-size-msec = 25[/I]

and in skype hardware audio set device instead "pulse'

---

### Post by ram130 on 2009-07-13
> **neal.m.master said:**
> You should try this:[INDENT] 
[LIST]
[*]killall pulseaudio
[*]sudo apt-get remove pulseaudio
[*]sudo apt-get install esound
[*]sudo rm /etc/X11/Xsession.d/70pulseaudio
[*]Reboot system and use the default sound setting in skype.
[/LIST]
 [/INDENT]I'm using skype from [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)
You can call sudo dpkg -i -force-architecture <name of skype deb> to use the i386 package on x64.  I just did this, but I haven't had any problems yet.  I hope it works for the rest of you.


i kept a copy of 70pulseaudio just in case; i don't like deleting stuff if i don't know EXACTLY what it does.

 That is  what i said too, but apparently no one wants to remove pulse. Its been a month or  more and  cpu is enjoying its holiday from work. :lolflag:

viduliya I hope all is well on your side of skype.

---

### Post by igorzwx on 2009-07-14
The blacklist ALSA modules, reboot, and install OSS4

---

### Post by igorzwx on 2009-07-14
Skype works well with OSS4
Fantastic perfomance
And Ekiga too.
Now I can call to my friends abroad.

The evil Pulse is the problem!

---

### Post by abhiroopb on 2009-07-20
I have found a solution:

in a terminal start skype by typing in "skype".

I get the following error:

```

ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

```

However, skype works without using 100% of my CPU.

My Sound settings are the default:

Autodetect
Autodetect
Autodetect
ALSA
Pulseaudio Mixer

My Skype sound settings:
HDA Intel (plughw:Intel,0)
pulse
pulse

What is interesting is if I start skype by launching it from the applications menu or by doing "ALT+F2" and launching it, it uses 100% cpu. But, launching from the terminal solves the problem.

This is a little annoying as I don't like to open the terminal to launch programs but this seems like an attractive solution!

---

### Post by nmaster on 2009-07-21
> **ram130 said:**
> That is  what i said too, but apparently no one wants to remove pulse.

sorry, didn't mean to repost your idea, i guess i wasn't reading very carefully.  i don't see why people wouldn't want to remove pulse tho.  i've had absolutely no problems with esound.

---

### Post by igorzwx on 2009-07-21
I do not know how many people want to remove Pulse.
But many have already changed to Mac or else.
It looks like a complete failure of Ubuntu,
if you google pulse.
The problem is, of course, the freadom of choice.
Freedom without choice means slavery.
Peaple feel this and run away.
I believe, it should be 3 versions of Ubuntu:

1. Ubuntulse
2. Ubuntalsa
3. Ubuntoss

and all will be happy

---

### Post by viduliya on 2009-07-22
> viduliya I hope all is well on your side of skype.  I have disabled pulseaudio according to the instructions from the link provided.  No problems since.  Evertying works wonderfully with alsa with pulse disabled.  If pulse gets fixed (ever? Or all the popular applications that has problems with pulse get fixed?) it is easy enough to change everything back to default setup.

---

### Post by igorzwx on 2009-07-22
Hi Vuduliya!

To be fair, I was not able to disable pulse,
and, therefore, changed to OSS4.

I am really intrigued to know how your sound work.
Can you record with Audacity? (it may start pulse)
And how your Skype works?
Do you have artefacts?

Best,
Igor

---

### Post by viduliya on 2009-07-23
> **igorzwx said:**
> Hi Vuduliya!

To be fair, I was not able to disable pulse,
and, therefore, changed to OSS4.

I am really intrigued to know how your sound work.
Can you record with Audacity? (it may start pulse)
And how your Skype works?
Do you have artefacts?

Best,
Igor

I can't comment on how Audacity works with this setup since I have not tried it.  Skype is used daily and there is no noticable sound quality problems or CPU usage problems since the disabling pulse.  It works like it did before when pulseaudio was not a part of the sandard ubuntu setup.  I will try Audacity and post a comment later.  I am running two laptops with intel sound hardware with this setup and so far, I have not noticed any sound related issues with this setup.

---

### Post by igorzwx on 2009-07-23
The problem with recording is artefacts.
When you record with pulse, you have a kind of irremovable noise.
On a Dell notebook you may even get 50Hz with odd overtones
(in US, 60Hz, perhaps).
Playback can be tested with special files.
You can easily create them with Audacity Nyquist,
10Hz + 19kHz, for example.

---

### Post by ram130 on 2009-07-23
> **igorzwx said:**
> I do not know how many people want to remove Pulse.
But many have already changed to Mac or else.
It looks like a complete failure of Ubuntu,
if you google pulse.
The problem is, of course, the freadom of choice.
Freedom without choice means slavery.
Peaple feel this and run away.
I believe, it should be 3 versions of Ubuntu:

1. Ubuntulse
2. Ubuntalsa
3. Ubuntoss

and all will be happy

Then Ubuntu will be more confusing to first timers, they would have to do some research to select the right version. I think Ubuntu sound mixers need a serious upgrade soon.

---

### Post by igorzwx on 2009-07-23
do you read post in the forum?

people try Ubuntu, then Kubuntu, the something very exotic.
and nothing helps.

It would not be difficult to provide a guide.
Ubuntoss - for ordinary users,
Ubuntulse and Ubuntalsa - for the advanced.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.[/B]

---

### Post by ram130 on 2009-08-03
> **igorzwx said:**
> do you read post in the forum?

people try Ubuntu, then Kubuntu, the something very exotic.
and nothing helps.

It would not be difficult to provide a guide.
Ubuntoss - for ordinary users,
Ubuntulse and Ubuntalsa - for the advanced.

True, but not everyone is willing to do that. First impression lasts.

---

### Post by merelin on 2009-08-08
Guys,

Try to change your /etc/pulse/daemon.conf:

high-priority = yes
nice-level = -11
realtime-scheduling = yes
realtime-priority = 5
default-fragment-size-msec = 5

That seems to have solved the issue.
I have pulseaudio on karmic amd64 and skype from the medibuntu repo.
Skype is set to pulse. Used to experience 100% cpu load.

---

### Post by soro2005 on 2009-08-10
@merelin: Looks relatively good here. Still get ~20% CPU usage, but that's much less than before. That is a very initial and preliminary result, will see how it plays out with more thorough testing. Jaunty, 64 bit, with pulseaudio, of course, and Skype 2.0.0.72

---

### Post by Arup on 2009-08-10
With ALSA or OSS4, my CPU max usage for all 8 cores was never over 4-6%, Skype is not multi threaded or multi core aware so it would select one of the eight cores. With OSS4, sound quality is excellent and there is no sound hogging issues.

---

### Post by axelsvag on 2009-08-15
Thank you Merelin your advice fixed at least my setup perfectly. I hope I wont run into trouble in another application now.

---

### Post by soro2005 on 2009-08-27
New Skype beta with Pulse Audio support at: [http://www.skype.com/intl/en/download/skype/linux/choose/](http://www.skype.com/intl/en/download/skype/linux/choose/)

---

### Post by abhiroopb on 2009-08-27
Thanks for that. But I still need to see what the benefit of pulse is before I bother going back to it! In any case I think I'll wait till I update to Karmic to bring back pulse.

---

### Post by H4F on 2010-08-31
I am experiencing the same issue. 
wish to see solution for that.

---


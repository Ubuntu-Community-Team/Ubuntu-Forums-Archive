---
title: "No &quot;line out&quot; (headphone output) in Ubuntu 11.10!?"
date: 2011-10-13
forum: Multimedia Software
---

### Post by Dingelfranz on 2011-10-13
Hey guys...
I've just updated to 11.10 from 10.04...
And now I don't have a "line out" option in Alsa-mixer!
When my headphones are plugged in, the internal speakers are playing as well... :( It kinda makes my headphones useless.

Is there anyway to get the "line out" option back???

-I'm on a Hp Pavillion dv7t series...


[http://www.alsa-project.org/db/?f=9f48d2148878e278262f9381abf99ea5044c245e](http://www.alsa-project.org/db/?f=9f48d2148878e278262f9381abf99ea5044c245e)

Hope you can help.

---

### Post by Minty :) on 2011-10-14
I have the same problem with hp dv6

---

### Post by jendie on 2011-10-14
I'm having a similar problem with the dv4 series. When the headphones are plugged in there is no sound at all...

---

### Post by kungfoofool on 2011-10-14
Try using alsamixer to change the volume for "Speaker." It was muted on my upgrade.

```

sudo apt-get install alsautils
alsamixer

```

---

### Post by Dingelfranz on 2011-10-15
Changing the volume won't bring back my "line out"... 
Tried changing all kinds of settings in alsamixer, but cant make it work. I'm seriously thinking about going back to 10.04.

---

### Post by mattybe on 2011-10-15
Ugh.  Same problem here, Lenovo R61i.  After updating, I didn't have any sounds.  Found the alsamixer and that "speaker" had been muted.  But my line out still doesn't work. There's no lineout option in alsamixer.  I've tried lots of options in alsa-base.conf (suggested here [http://ubuntuforums.org/showthread.php?t=1469949](http://ubuntuforums.org/showthread.php?t=1469949)) with no luck.

---

### Post by carsy on 2011-10-15
same system (Lenovo R61i) and symptoms here. Upgraded an Acer Aspire One at the same time...it's working fine.

In the process of trying everything possible, discovered some things that may be useful to someone who actually knows what they are doing.

alsamixer in the Acer has the "headphone" choice. Lenovo doesn't. Both the same version...R61i has onboard conexant soundcard, Acer Realtek.

This Lenovo R61i is 64 bit (don't know if that is generally true). Acer is 32 bit.

One of the recommended solutions ([http://dharmendralinuxdiary.blogspot.com/2011/10/ubuntu-1110-sound-problem.html](http://dharmendralinuxdiary.blogspot.com/2011/10/ubuntu-1110-sound-problem.html)) is to install or re-install linux-alsa-driver-modules-$(uname -r) from ppa:ubuntu-audio-dev/ppa. The latest version at that ppa is linux-alsa-driver-modules-2.6.38. Considering that the 11.10 upgrade included upgrading the Linux kernel to 3.0.0, that package doesn't exist at that ppa. I've sent a message to the ppa leader about this. I don't know whether or not this has anything to do with the issue.

Rather than taking more drastic measures, I'm gonna use the USB headphones that work great. It seems like this problem requires some small thing to be resolved. I have no idea what that is.

---

### Post by kvmapr on 2011-10-15
I have the same problem on my HP DV6-2150US. When I plug my head phones in, I get audio through the head phones, but it's also still coming through the laptop speakers. When I go to "Sound Settings" on the Sound control application, the Output tab list just one option for the "Connector" selection, Analog Speakers. In 11.04 that same setting offered both Analog Speakers and Analog Output (for head phone only output).

Does this need a bug report?

---

### Post by johnfriend on 2011-10-16
same problem for me also please solve this :)

---

### Post by Mad-Halfling on 2011-10-16
> **kvmapr said:**
> I have the same problem on my HP DV6-2150US. When I plug my head phones in, I get audio through the head phones, but it's also still coming through the laptop speakers. When I go to "Sound Settings" on the Sound control application, the Output tab list just one option for the "Connector" selection, Analog Speakers. In 11.04 that same setting offered both Analog Speakers and Analog Output (for head phone only output).

Does this need a bug report?

Yes, this is the exact problem I have on my DV8 - I could, manually, change the output destination, as you did, and though it wasn't as good as detecting the headphones being plugged in, it did the job.  This is an absolute killer for me, too, as there are times I need to use my headphones and not disturb people around me.
I did notice in /etc/modprobe.d/alsa-base.conf there was a line
options snd-hda-intel model=hp-dv8 enable_msi=1
that had been commented out, but restoring this doesn't seem to do anything.

---

### Post by Mad-Halfling on 2011-10-16
This is another temporary workaround, less pretty than the volume settings one, but at least it works until we can either get the output connector option working, or get the whole issue fixed.
In a terminal type
alsamixer
that will bring up the various volume setting options - if you have 
 Master      Speaker    PCM     Front 
available then you should be in business.  The Speaker and Front volumes affect the main laptop speakers and the headphone volumes, respectively.  If you use the right arrow key to go over to the Speaker column then the down arrow, you can take that volume down to 0 without changing the headphones volume.  You can also hit 0 to bring this down to zero and then 9 to take it virtually back up to full.  *Don't* use m to try to mute the column as this seems to mute the master, too - manually change the volume down to zero, just for that particular channel.

I've got some other things I'm trying, but that should enable you to control the different volumes until we can get a better solution.

---

### Post by mattybe on 2011-10-16
unfortunately, I don't have a "front" setting in alsamixer =/

---

### Post by Dingelfranz on 2011-10-16
Mad-Halfling: This "solution" works for me... 
Thanks man! 

But still, it would be nice to have my line-out option back...

Untill someone fixes this issue, "Mad-Halflings" work-around will have too do.

(Oh, I almost forgot!) -UBUNTU STILL KICKS ***!!!

---

### Post by Mad-Halfling on 2011-10-16
This is what my mixer looks like - you may find that it's called something different:-
[IMG]http://i472.photobucket.com/albums/rr89/mad-halfling/AlsaMixer.png[/IMG]
The master is the master volume, speaker is the hardware speakers, PCM is the software volume that affects both the speakers and the headphones, then front is the headphones.  Look for an entry that's got that 00 at the footer.  Worst case, plug your headphones in, stick some music on, put one headphone entry in your ear and listen the the speakers, then play with the various volumes and see what affects what.

If you're still having problems, post a screenshot of your alsamixer and maybe we can see something you may have missed, or run 
amixer
and post the output here

---

### Post by Mad-Halfling on 2011-10-16
As a general reply, rather than anything specific to Mattybe's problems - once you've got my previous workaround working, you can script it:-
amixer set Speaker 0%
amixer set Speaker 100%
turn the speakers off and on, respectively, whilst leaving the headphones as they were, on my system.  Obviously, if your channel is called something different you need to change the Speaker parameter to your channel name.  Create a couple of shell scripts that you can put on a menu or desktop icon and it's "Hello Uncle Bob"!  At least until we can get this sorted.
Scripting FTW =8) gotta love being able to take control of your system at a low level

---

### Post by carsy on 2011-10-16
headphones cut off laptop speakers, but no headphone sound

Lenovo R61i
[http://www.alsa-project.org/db/?f=374c392b7d917ff09ddef53f499f4e0da2089013](http://www.alsa-project.org/db/?f=374c392b7d917ff09ddef53f499f4e0da2089013)

screenshot of alsamixer attached

---

### Post by klinge01 on 2011-10-17
hey carsy

same problem here, same laptop as you and i guess your microphone dos not work too.

unfortunately i haven't found a solution yet, please let me know ...

---

### Post by carsy on 2011-10-17
It may be helpful to post the results of this command. It shows a lot of information about what's happening with your sound system. Answer yes when asked if the results should be uploaded. Paste the link in a message in this thread.

sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

My problem is with the headphones, not the microphone. I don't know whether or not the plug-in mike works.

Are you subscribed to this thread? That's the best way to stay on top of any replies.

---

### Post by nbb311069 on 2011-10-17
I'm on a Lenovo 3000 V200.
Just updated to 11.10 I didn't have the front connection listed thus no sound in my headphones no matter what I did.
Got the front-option by adding this line
options snd-hda-intel model=generic to the 
/etc/modprobe.d/alsa-base.conf

Unfortunately the auto-function cutting the sound to the speakers when connecting headphones is now gone - work-around is to choose front/headphones as the output in sound config.

It seems to be a problem with the driver for hda Intel cards - hope it gets fixed soon.

---

### Post by elachim on 2011-10-17
hello, i have same notebook, r61i, had the same problem, no sound from headphones output, and using [DKMS]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS") works for me as solution, it gave me "Analog Headphones" option in Output/Connector setting...
basicly it will "give you the latest ALSA driver ... for internal "HDA Intel" sound cards"
here is my [alsa-info]("http://www.alsa-project.org/db/?f=f2b9509cd912006fbc6ee8180fffaf36e803b590") report.
i am really glad i have the sound now but when i plug off the jack, internal speakers wont start automatically ...
i hope it will help you as well ;)

---

### Post by klinge01 on 2011-10-17
thanks elachim

it does not work perfect but it is definitely an improofment.

the automute function and the microphone still don't work and the headphones work only if i don't push the plug all the way in.

greetings, klinge

here is my alsa info report after the alsa upgrade : [http://www.alsa-project.org/db/?f=b2078a3f70b398d86f90e12c08a28a30b97da562](http://www.alsa-project.org/db/?f=b2078a3f70b398d86f90e12c08a28a30b97da562)

---

### Post by Mad-Halfling on 2011-10-17
If you don't mind, could the folks who have no sound coming from their headphones please move their discussion a new thread? I'm pretty sure that's a different issue you're experiencing and I think it will get rather confusing if we end up talking about 2 separate problems/solutions on the same thread.  If you _do_ start a new thread, pls post a link here so people know where to go and I'll have a look at it, too.

As an aside, for that problem, try running
amixer
and see if there are any channels set to 0 - that might help you find the culprit.

Cheers - MH

---

### Post by carsy on 2011-10-17
"If you don't mind, could the folks who have no sound coming from their headphones please move their discussion a new thread?"

Seriously? In a thread called "No "line out" (headphone output) in Ubuntu 11.10!?"? And with several related threads have been informally consolidated here.

That doesn't make sense. What is this thread about if it's not "no headphone output"?

I do mind starting another thread. Mad-Halfling, perhaps you could start another thread with a topic headline related to whatever you think is being discussed here.

---

### Post by elachim on 2011-10-17
> **carsy said:**
> "If you don't mind, could the folks who have no sound coming from their headphones please move their discussion a new thread?"

Seriously? In a thread called "No "line out" (headphone output) in Ubuntu 11.10!?"? And with several related threads have been informally consolidated here.

That doesn't make sense. What is this thread about if it's not "no headphone output"?

I do mind starting another thread. Mad-Halfling, perhaps you could start another thread with a topic headline related to whatever you think is being discussed here.

THANK YOU, you just wrote what came to my mind too...

---

### Post by Dingelfranz on 2011-10-17
> **Mad-Halfling said:**
> If you don't mind, could the folks who have no sound coming from their headphones please move their discussion a new thread? I'm pretty sure that's a different issue you're experiencing and I think it will get rather confusing if we end up talking about 2 separate problems/solutions on the same thread.  If you _do_ start a new thread, pls post a link here so people know where to go and I'll have a look at it, too.

As an aside, for that problem, try running
amixer
and see if there are any channels set to 0 - that might help you find the culprit.

Cheers - MH

I started this thread in search of a way to bring back the "line-out" option in Ubuntu 11.10... NOT to deal with volume or no sound issues...
However, learning about other 11.10 users sound problems, and their specific laptop/desktop model problems, will surely help to find a solution. So far my problem with the "line-out" disappearing, is also a problem for other Hp users...
So in the end, it all helps out.
Thanks again guys.
UBUNTU!!!:)

---

### Post by carsy on 2011-10-17
Updated to add clarity and specificity in response to kdavh post #28 (below)

Okay, I got this working by combining several suggestions in this thread. I hesitate to mark it solved, because it seems like there are several different issues.

Thanks to:
Elachim page 2 - reply #20
   Followed the directions in this post to install dkms. 
nbb311069 page 2 - reply #19
   Followed the directions in this post to add model=generic to alsa-base.conf

Details follow:
1. Clicked on the DKMS link in Elachim's post. It goes to a page [1] with directions for upgrading ALSA with DKMS. It would only confuse things to duplicate the directions given at those pages...I followed them exactly. The only thing I encountered that is not mentioned on those pages is that "sudo dpkg -i <file name>" reported the error that DKMS was not installed. That required sudo apt-get install dkms. Once dkms was installed, the deb file for alsa-hda-dkms for oneiric installed automatically.

I was concerned that the alsa-hda-dkms had only a i386 build, because my installation is on a 64 bit/x86-64 computer. The installation messages for alsa-hda-dkms indicated that the package supported 64 bit computers. No reason for concern with 64 bit computers.

[1] [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)  

2. Based on nbb311069's post...
sudo nano /etc/modprobe.d/alsa-base.conf
added 
options snd-hda-intel model=generic
in the section near the bottom where there are similar entries.

Save.

Restart.

Everything apparently works...headphone, internal speakers, Plugging in headphone cuts off internal speakers.

However the systray volume control didn't work. Up to now, I think that the process is the same for Ubuntu or Kubuntu. I'm running Kubuntu and I don't know how the volume control works in Ubuntu.

So...for Kubuntu:
The systray volume control (KMix) didn't work (it usually can be adjusted with the mouse wheel). Clicking the icon brings up a slider control...it also didn't work. Clicked the mixer button. On the following screen, PCM volume control works.

Back at the systray...right-clicking the KMix systray control icon displays a choice "Select Master Channel...". Clicked that and selected PCM. Now KMix adjusts volume for both headphone and internal speaker.

Thank you everyone. I worked on this for the better part of a day with no results. With your assistance, I'm back in business.

Caveat...This is only for the external _headphone_. I have no idea about the microphone jack.

---

### Post by kdavh on 2011-10-17
Same problem with 11.10 on my Lenovo 3000 v200.  I did not have this problem with 11.04.

---

### Post by kdavh on 2011-10-17
Thanks to nbb311069.  I used the:

options snd-hda-intel model=generic

line in the file:
 
/etc/modprobe.d/alsa-base.conf

I had tried so many others, like:

model=lenovo
model=test
model=laptop
...etc

But yours actually did it.
(Of course, there is still the problem of no auto-mute.)
**This also fixes the internal microphone*** Thanks for that

Carsy, thanks for starting such a coherent and useful thread.  Unfortunately, being a newbie, I can't quite follow your last post instructions where you claim to have fixed the issue.

---

### Post by Mad-Halfling on 2011-10-18
> **carsy said:**
> "If you don't mind, could the folks who have no sound coming from their headphones please move their discussion a new thread?"

Seriously? In a thread called "No "line out" (headphone output) in Ubuntu 11.10!?"? And with several related threads have been informally consolidated here.

That doesn't make sense. What is this thread about if it's not "no headphone output"?

I do mind starting another thread. Mad-Halfling, perhaps you could start another thread with a topic headline related to whatever you think is being discussed here.

> **elachim said:**
> THANK YOU, you just wrote what came to my mind too...

Err, excuse me - if you *read* the original post

> **Dingelfranz said:**
> Hey guys...
I've just updated to 11.10 from 10.04...
And now I don't have a "line out" option in Alsa-mixer!
When my headphones are plugged in, the internal speakers are playing as well... :( It kinda makes my headphones useless.

Is there anyway to get the "line out" option back???

-I'm on a Hp Pavillion dv7t series...


[http://www.alsa-project.org/db/?f=9f48d2148878e278262f9381abf99ea5044c245e](http://www.alsa-project.org/db/?f=9f48d2148878e278262f9381abf99ea5044c245e)

Hope you can help.

you will see that I am, in fact, correct (thanks to Dingelfranz for backing me up) and *you* are posting OT.

The original problem is diametrically opposed to that which you are experiencing (and the exact problem I am having) - when the headphones are plugged in we get sound in the headphones but the speakers don't mute.  The "No Line out" refers to the option begin missing in the output connector (see above!), rather than the lack of sound going to the line out channel.
PLEASE read the thread properly and make sure you are posting correctly, espcially before having a go at others.  Normally, if something's related I wouldn't have a problem with related posts, but as you are having *completely* the opposite problem to us - your speakers mute but you have no headphone sound, whereas we have headphone sound but the speakers don't mute - I thought, as I said, it wasn't appropriate for this thread and would just confuse both issues.  I also asked quite politely so you getting shirty with your reply was rather unjustified and doesn't exactly inspire me to help you further.  Remember, you are on here looking for help so it doens't pay to annoy people.  Any apologies will be graciously accepted =8)

---

### Post by mattybe on 2011-10-18
> **kdavh said:**
> (Of course, there is still the problem of no auto-mute.)

kdavh, try running alsamixer from console. There may be an automute toggle all the way on the right.

> **Mad-Halfling said:**
> The "No Line out" refers to the option begin missing in the output connector (see above!), rather than the lack of sound going to the line out channel.
These are all basic alsa-related issues and will probably have similar solutions.  Did you try dkms?

---

### Post by Mad-Halfling on 2011-10-18
> **mattybe said:**
> These are all basic alsa-related issues and will probably have similar solutions.  Did you try dkms?

That's already on my system.  As far as I've seen, when I've revisited this over the last couple years (IIRC, it first occured in the 9->10 upgrade) it's something specific to HP machines and is something weird to do with the way they mute the speakers - in the various forums I searched, this problem seems to be endemic and exclusive to their hardware (look at the posters here who say "I have an HP DV[X] laptop).  This is as much to do with a workaround now not working as it is to the original problem - we've lost an entry in the Connector dropdown list on the sound setting's output tab that we were using to switch over to the headphones, rather than the speakers and headphones.  Our sound output is working fine, it's just that the headphones plug/unplug event isn't being detected and the output channel changed, or the speakers muted - the other guys are having a far more fundamental problem in that they're not getting the output driven to their headphones channel, at all.  So, yes, whilst I agree with you that they're both alsa related, I think they are very differnt problems with alsa.  It's like saying that a wireless card not being able to connect to a wireless network and a wireless card not picking up the DHCP settings are the same because they're both problems with the card driver/network software.

---

### Post by elachim on 2011-10-18
> **Mad-Halfling said:**
> Err, excuse me - if you *read* the original post
...
Any apologies will be graciously accepted =8)

sorry but i rather found you very funny, also too sofisticated :D

---

### Post by Mad-Halfling on 2011-10-18
> **elachim said:**
> sorry but i rather found you very funny, also too sofisticated :D

Haha, thanks - I was trying to be polite and not go wraaaaaa - especially as I can see where confusion may have arisen from the thread title, if people didn't read the original post which clarifies the exact nature of the problem =8)

---

### Post by Ajidh on 2011-10-19
I have the same problem but i also don't have the front speaker volume... in my case when i connect the headphones the speaker volume goes to 00 and i fix the problem returning it to 100 but it goes down again when i disonnect and connect the headphones again... i can't put the image of my screenshot but the controls i have below are master, heaphones (wich is in 00 and i can't move), speaker, PCM, Mic, S/PDIF, S/PDIF D, Beep, F-Mic. 
That's the problem i have. i hope some of you have find the solution. Thanks!

---

### Post by carsy on 2011-10-21
Ajidh,

It would help to know more about what's going on.
What is your machine? Presumably (*)buntu...what flavor, what version? How about a screenshot of [terminal]alsamixer? Please don't just respond to these questions...more information will make it likely that someone can help.

Enter the following in terminal and post the URL it returns (you'll have to answer yes somewhere in the process).
sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Have you checked DKMS (see post #20 in this thread)?

modifying /etc/modprobe.d/alsa-base.conf with instructions and suggestions throughout this thread seems to work for some people.

---

### Post by crack.mech on 2011-10-21
Was Stuck with the problem : Speaker volume used to come to '0' whenever I plugged in the headphones. Either manually increase the speaker volume evrytime I inserted the H/Ps.. 

Or follow   Reply # 20:

> **elachim said:**
> hello, i have same notebook, r61i, had the same problem, no sound from headphones output, and using [DKMS]("https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS") works for me as solution....
i hope it will help you as well ;)


Worked like a charm...

Thanks!!

P.S: My Alsa report  (Asus F6A-X2): [http://www.alsa-project.org/db/?f=b7e6413f88b249d6e02372401793c08d9c17500d](http://www.alsa-project.org/db/?f=b7e6413f88b249d6e02372401793c08d9c17500d)

---

### Post by cccanovas73 on 2011-10-22
Hi, I have an hp-dv6 laptop with Oneiric Ocelot 11.10
After looking everywhere I fix the problem adding these two files to the alsa-base.conf file:

options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5

Now when I plug the headphones the speakers mute automatically!!

:KS

I hope it will help you!:guitar:

---

### Post by Dingelfranz on 2011-10-22
> **cccanovas73 said:**
> Hi, I have an hp-dv6 laptop with Oneiric Ocelot 11.10
After looking everywhere I fix the problem adding these two files to the alsa-base.conf file:

options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5

Now when I plug the headphones the speakers mute automatically!!

:KS

I hope it will help you!:guitar:

This sort of worked for me too...!
It makes my internal speakers mute all the time, but since I never use them, due to low quality, I am very happy with this solution! Finally I can play some loud music without annoying the neighbours... :lolflag:

Thanks a lot everyone! (cccanovas73 made my day/night)

May the "Ubuntu" in you stay strong!;)

---

### Post by cccanovas73 on 2011-10-22
Great!!!

Regards from Barcelona, Spain.   :)

---

### Post by fili on 2011-10-24
I also had no output on the headphones of my Lenovo Thinkpad R61i, this helped:

> /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=generic

There was no need to install the DKMS package

---

### Post by Mad-Halfling on 2011-10-25
> **cccanovas73 said:**
> Hi, I have an hp-dv6 laptop with Oneiric Ocelot 11.10
After looking everywhere I fix the problem adding these two files to the alsa-base.conf file:

options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5

Now when I plug the headphones the speakers mute automatically!!

:KS

I hope it will help you!:guitar:

I'm sure the solution to the solution to the problem is in these lines as it's something HP have done and searching for solutions reveals this roblem, pretty much, only occurring on HP machines.  Looking at that, as it worked for you, it seems like support is in there but the ALSA configuration isn't picking up the machine type, so it needs manually setting. I'd tried a couple of similar things on my DV8 but I don't think I tried setting the type to dv5 nor using it with the other line. However if this always mutes the internal speakers, this would be a problem for me.  I'll have more of a play around and post back my DV8 success. I've just remembered I did have this problem on my DV6 but I've subsequetly reloaded it with Fedora - I'll see if it works ok on that and if so what config entries there are, if ALSA is on there.

---

### Post by cccanovas73 on 2011-10-25
> **Mad-Halfling said:**
> I'm sure the solution to the solution to the problem is in these lines as it's something HP have done and searching for solutions reveals this roblem, pretty much, only occurring on HP machines.  Looking at that, as it worked for you, it seems like support is in there but the ALSA configuration isn't picking up the machine type, so it needs manually setting. I'd tried a couple of similar things on my DV8 but I don't think I tried setting the type to dv5 nor using it with the other line. However if this always mutes the internal speakers, this would be a problem for me.  I'll have more of a play around and post back my DV8 success. I've just remembered I did have this problem on my DV6 but I've subsequetly reloaded it with Fedora - I'll see if it works ok on that and if so what config entries there are, if ALSA is on there.


I can tell you that it works **adding the two lines**. (I tried before adding only the second one but it didn't worked.)
 When I say that it works it means that the speakers are** only muted  when you connect the headphones, not all the time**. There is no necessary to select headphones manually (In fact, I can't do it because there's no option to do that in the sound  oonfiguration menu whereas in Natty Narwhal I could select the output option). Sorry if I don't understand exactly what you say, my english is not so good as I'd like. Regards.

---

### Post by Mad-Halfling on 2011-10-26
We may have cause to rejoice as I think an update may have fixed this:-

Today, I was there with my headphones ohn and had run my speaker-mute script and then wanted to play something out loud, so I just ran my unmute script, but nothing happened, the sound was just coming out of my phones. Hoping beynd hope I unplugged them and the speakers sprang into life, plugging them back in ......... muted the speakers.  I haven't had time to do any further testing, but if you have this problem then run your updates and test things - it may well be working, now.

However, I'd make a note of this thread in case it breaks again, in future, or put the entries in the config and comment them out, so you have a reference

---

### Post by pandev92 on 2011-10-27
> **cccanovas73 said:**
> Hi, I have an hp-dv6 laptop with Oneiric Ocelot 11.10
After looking everywhere I fix the problem adding these two files to the alsa-base.conf file:

options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5

Now when I plug the headphones the speakers mute automatically!!

:KS

I hope it will help you!:guitar:

Thanks, it solved my problems :)

---

### Post by mrodden on 2011-10-29
Many thanks for that. Spent ages looking for solution but your fix was excellent!

---

### Post by Mad-Halfling on 2011-10-30
> **mrodden said:**
> Many thanks for that. Spent ages looking for solution but your fix was excellent!

Looks like this thread can be marked as solved then?

---

### Post by Mark.arted on 2011-10-30
I have the same problem on my Asus G50V, with the added treat that Alsamixer gui won't open. I just upgraded to Ocelot and it's like starting from scratch all over again.:evil:

---

### Post by trukker on 2011-11-03
Hi All,

I've got an MSI PR-200... added the lines above, there is sound out of the laptop line-out but with the sound-output set to speakers in sound settings...

So still some tweaking to go for this model of laptop.

---

### Post by psykotic25b on 2011-11-06
Ok, first of all let me thank carsy for getting me started on the path to fixing my audio/headphone problems.

Now, here's how I did it.  I went off of your post about installing dkms, and then adding the line to that configuration file, but, the only place that got me was working headphones and no external audio.  So the next thing I did was uninstall dkms, reinstall dkms, and then remove the model=generic line from the config file.  Now, my headphones and speakers work like they're newlyweds.  I don't even have to turn my speaker volume back up after I remove the headphones, it just automatically returns to the setting from before.

I use an Asus-U52F with Oneiric.

Thanks again guys!

---

### Post by sc4s2cg on 2011-11-09
[quote=carsy]Updated to add clarity and specificity in response to kdavh post #28 (below)

Okay, I got this working by combining several suggestions in this thread. I hesitate to mark it solved, because it seems like there are several different issues.

Thanks to:
Elachim page 2 - reply #20
Followed the directions in this post to install dkms.
nbb311069 page 2 - reply #19
Followed the directions in this post to add model=generic to alsa-base.conf

Details follow:
1. Clicked on the DKMS link in Elachim's post. It goes to a page [1] with directions for upgrading ALSA with DKMS. It would only confuse things to duplicate the directions given at those pages...I followed them exactly. The only thing I encountered that is not mentioned on those pages is that "sudo dpkg -i <file name>" reported the error that DKMS was not installed. That required sudo apt-get install dkms. Once dkms was installed, the deb file for alsa-hda-dkms for oneiric installed automatically.

I was concerned that the alsa-hda-dkms had only a i386 build, because my installation is on a 64 bit/x86-64 computer. The installation messages for alsa-hda-dkms indicated that the package supported 64 bit computers. No reason for concern with 64 bit computers.[/quote]

There doesn't seem to be a .deb file in the [ALSA download link]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages"). Apparently it was updated 2 hours ago.

Is there an alternative link for this download?

---

### Post by carsy on 2011-11-09
> There doesn't seem to be a .deb file in the ALSA download link. Apparently it was updated 2 hours ago.
Is there an alternative link for this download?

The recent builds failed. It shouldn't be long before a .deb is available at that site. Recommend against some other source...this is the one to use. Any other would be outdated at best.

---

### Post by sc4s2cg on 2011-11-11
The .deb was up today, so I went ahead and did what your post said, however I did have to change one thing.

Instead of "options snd-hda-intel model=generic", I had to use "options snd-hda-intel model=hp-dv5" for my dv7 laptop. Using generic I had barely audible sound through the headphones, even with volume at 120%, and no sound through the speakers.

Now the speakers turn off automatically after I plug in the headphones, and all is well. Thank you :)

Couple links I found:

- [HDA Intel Sound How to ]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
- [What to put after the "model=" edit]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/HD-Audio-Models.txt") HP dv series requires "hp-dv5"
- The [post]("http://ubuntuforums.org/showpost.php?p=7299632&postcount=60") that directed me to trying hp-dv5, after trying hp, hp-dv7, hp-dv4, hp-dv7-4000. And the [thread]("http://ubuntuforums.org/showthread.php?t=1192274") that directed me to the post.

---


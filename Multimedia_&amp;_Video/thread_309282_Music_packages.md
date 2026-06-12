---
title: "Music packages"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by luneo on 2006-11-29
I am building edgy packages... like realtime kernel... ardour2.... audacity... and some other... just take a look... [http://luneo.zendurl.com]("http://luneo.zendurl.com")

---

### Post by tronica on 2006-11-29
very nice, thank's i downloading now to try

---

### Post by jorg01 on 2006-11-29
luneo, cool! 

But how do I install? Im new to ubuntu...

cheers
jorgen

---

### Post by Hanj on 2006-11-29
@jorg01: If double-clicking the .deb file does not bring up the package installer, you can type 'sudo dpkg -i package_name' in a terminal to install it.

Has anyone tried Ardour 2? How stable is it?

---

### Post by damu on 2006-11-29
Thanks bunch Luneo. I didn't install the package on my desktop  yet, as I didn't recover from a kind of blue screen with WinXP (freeze + hall.dll missing...please reinstall, and finally screwed the grub...goes on and on...:rolleyes: ), but it's a major incentive to sort this out, and finally get a complete sound studio working with ubuntu. I guess the rt kernel is smp compatible ?



Thanks again

---

### Post by luneo on 2006-11-30
Yes it is.... by tomorrow we will have two versions of the kernel... one generic... one for p4... all based on the new 2.6.19 kernel... i will try to make one x86_64, but I´am new to cross-compiling... If someone could help me setup my cross-compiling system....

---

### Post by movibe on 2006-12-04
thz for ur big effort , luneo !!! :]

---

### Post by xyz on 2006-12-04
> **luneo said:**
> I am building edgy packages... like realtime kernel... ardour2.... audacity... and some other... just take a look... [http://luneo.zendurl.com]("http://luneo.zendurl.com")
I'd love to take a look at this but the site won't load.
I guess I'll give it another try later.
Thx in advance.

---

### Post by frolle on 2006-12-04
Seems like the site is down, i get an error message when i try.

---

### Post by falkenberg_cph on 2006-12-04
how is the ndiswrapper kernel comming on?
Sorry for sounding so demanding, how else could i have formulated it.

Thanks again
/Carsten

---

### Post by luneo on 2006-12-04
The site keeps getting down... I don't know why... I am making new kernels... and a repository... and I have compiled the ndiswrapper for the p4 kernel... I will wait a little to make 2.6.19 kernels... it seems to me that there is too much bugs... I compiled one kernel and it didn't want to compile nvidia... later on another compile... it was a fuzz with apm... I tried the config from the realtime kernel rpm... and it was the same thing... so I will wait... but it will come out...

---

### Post by luneo on 2006-12-04
now.. it's all up, including the how to... and there is a deb repo...
deb [http://luneo.zendurl.com/packages](http://luneo.zendurl.com/packages) 32bit/

---

### Post by handy on 2006-12-04
Thanks for all your hardwork Luneo! :KS

---

### Post by falkenberg_cph on 2006-12-05
And its down again. I have a webhotel you could use for mirror if the downtime continues. Just PM me?
/Carsten

---

### Post by CapnWhizBang on 2006-12-05
What is the benefit of using one of these kernels? How is it better than just following the UbuntuStudio instructions? (without [compiling  a vanilla kernel]("https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption")) Am I right that I would need the ndiswrapper kernel? (because I had to get ndiswrapper working to support my pcmcia wifi card) also, I can't find the HowTo mentioned above.... help!

---

### Post by damu on 2006-12-05
the answer you are looking for is in the 'how to' that u linked to :
> To get to the goal of true real-time, low-latency audio work under Linux, you will absolutely require Realtime-Preemption. Ingo Molnar, who currently works for Red Hat, wrote a patch that will apply to the the [WWW] official vanilla kernel sources. This patch gives you roughly 95% preemption, as compared to about 50% preemption without the patch

There will always be a latency with an emulated synth. But if it is low (< 10 ms), you won't notice the latency/time from pressing the key of your keyboard/synthetiser to hearing the sound produced by ZynaddsubFX (or any other emulated audio app). 
If the latency is higher (>50 ms), it will become really hard to play live, or mix accurately with automation.
The more you add stuff to your audio project the more you need an optimized kernel that can cope with loads of audio process at low latency.

Luneo has done it for us, and it is really really great! It simply means that with this rt kernel (which works with dual core proc...yes! :) ) installed in 3 clicks you have a fully functional audio workstation with Ubuntu. That was simply out of reach for anyone not confident enough to compile an rt kernel before.

---

### Post by luneo on 2006-12-05
I have compiled a linux-2.6.19-rt... it is fast... way more stable than the 2.6.18 rts ... there is just one problem... the nvidia kernel needs a patch to compile... and the ndiswrapper won't compile... and some others modules may not compile... I don't know if you guys want that kernel... :) I you guys  want and promise ;) that you won't rely on me to build the modules right away... I will try to put it on my site.. but this zendurl is allways offline...

---

### Post by damu on 2006-12-05
I don't need neither the nvdia or ndiswrapper for my desktop, but I definitely could do with this linux-2.6.19-rt. I seem to have loads of xruns with my config (with 2.6.18 rts). I don't know if it comes from the kernel or something else. I opened a thread about that... thanks bunch for your effort..u're a :KS !

---

### Post by luneo on 2006-12-06
great news from zendurl.com:


Our server's hard drive was corrupt causing the downtime. We are currently reconfiguring the server, plus we are adding an additional server. This way there will be less downtimes in the future and no such problems in the future.

Thank-you for understanding, and we plan to be back online by Sunday December 10th.

---

### Post by luneo on 2006-12-06
for now you'll can use that repo:
deb [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/

And a website... with instructions... it will no be the main site and repo... just for now... I am using the space of my project on codigolivre.org.br... when I get the zendurl thing back... the site is going down... and maybe I am going to mirror it on codigolivre but on a different subdomain...
The site address is: [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br)

---

### Post by luneo on 2006-12-06
By the end of today or by the morning of tomorrow...  I will upload the 2.6.19 kernels... I am compiling new ones... :) ... because entered the mingo site and I saw a new realese, rt6.... and I had the rt3 release... so I had to compile all over again... so just await a little more...

---

### Post by sgx on 2006-12-06
Hi, and thanx much for your packaging efforts, which have helped
greatly in my quest to utilize some excellent free vsti from
talented windoze coders

On my Suse box, I use qaconnect when qjackctl sometimes fails, but
I tried alien to make a .deb, and it failed...so when your more
important projects are finished, if you could try and package
qaconnect, I would be very grateful! Keep up the great work...
 
url for qaconnect tarball:

[http://public.planetmirror.com/pub/sf/q/qa/qalsatools/?fl=s](http://public.planetmirror.com/pub/sf/q/qa/qalsatools/?fl=s)

---

### Post by luneo on 2006-12-06
Ok 2.6.19 kernels are up.. with ndiswrapper... nvidia.. and all.. if you want to use my nvidia kernel.. you should use the alberto's repo... [http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html) ... and install it's glx...

---

### Post by luneo on 2006-12-06
man... you can use the aconnectgui or the kaconnect... i think they don't even make the qaconnect anymore... and there is a problem in the source code...

---

### Post by luneo on 2006-12-07
Ok... there is the qaconnect gui....:-D  ...
Just grab it, and install it...
Oh... if someone wants to compile it... you must change the line 27 on connector.h ....
Where it is: ConnectorWidget::ConnectorWidget(QWidget *parent, snd_seq_t *pseq);

It should be: ConnectorWidget(QWidget *parent, snd_seq_t *pseq);

That's all! If you don't want to change by hand grab the patch... and patch it....8)

---

### Post by luneo on 2006-12-07
...

---

### Post by luneo on 2006-12-08
I have been trying some new things with the rt kernel... amd with pam... although they say that the edgy pam is good for realtime... I did give a chance to the debian pam... that I know for sure that they are realtime good.... and I saw the change log... the realtime patch was only applied to the 0.79-4 version... and the ubuntu version is the 0.79-3... so... I installed the debian pam, and compiled a new kernel, the rt10, and voila... using ZynAddSubFx without xruns...(the only thing is that when I choose the drums pattern it just stop working.... then I have to close ZynAddSuxFx and open it again)... tried everything... just good... and my test soundcard is a SiS7012(onboard)... I think things are going to be great... se what we've got:
lucas@cyberwarrior:~$ ps -C jackd -cmL
  PID   LWP CLS PRI TTY          TIME CMD
 7716     - -     - ?        00:00:00 jackd
    -  7716 TS   16 -        00:00:00 -
    -  7717 TS   18 -        00:00:00 -
    -  7718 TS   24 -        00:00:00 -
    -  7719 FF  139 -        00:00:00 -
    -  7720 FF  129 -        00:00:00 -
and:
lucas@cyberwarrior:~$ chrt -p 7719
pid 7719's current scheduling policy: SCHED_FIFO
pid 7719's current scheduling priority: 99
lucas@cyberwarrior:~$ chrt -p 7720
pid 7720's current scheduling policy: SCHED_FIFO
pid 7720's current scheduling priority: 89
....
with 99 realtime priority... and jackd with 89 realtime priority, the max allowed in qjackctl...

---

### Post by damu on 2006-12-09
I tried the last kernel(2.6.19). 
Jack starts when t>5 ms and at 44khz and 48 khz (won't take 96 khs and it never has whatever may be the distro).

I usually test with just zynaddSubFx (with few layers of sound) and eventually jackrack , with a latency at 256 (12 ms) or 512 (23 ms). 

The good point is  that smp seems better handled  than on any other distros or previous config (don't ask me why). For the first time, with 7 layers of sound in Zynadd, both core of my X2 3800+  are in between 30 to 45%. Before it was more 60-70% one one core and 10-20 on the other. So that's a very good point. I guess that with jackdmp for parallel processing, one could now achieve very good results on larger audio projects.

The bad point is that I have as many xruns with this kernel than with the 2.6.18. I wonder if there is something wrong with my config. I seem to have to have more xruns with the rt kernel than with the stock kernel.
I followed the wiki for rt settings and created an audio group. When I go now to system/administration/users and groups/ manage groups, I can't see the audio group. I created many times, and every time , when I reopened the group I get the same result . But when I open etc/group, I can see the line :audio:x:29:damu,root, so I guess it's all right.

I didn't find how or where to set the rt priority to 99 and the jack rt priority to 89.

I tried to put the same lines than yours in terminal, but the 2 last ones gave me a 'command not found' :

> damu@ubuntu:~$ ps -C jackd -cmL
  PID   LWP CLS PRI TTY          TIME CMD
14101     - -     - ?        00:00:00 jackd
    - 14101 TS   19 -        00:00:00 -
    - 14102 TS   24 -        00:00:00 -
    - 14103 TS   24 -        00:00:00 -
    - 14104 FF   60 -        00:00:00 -
    - 14105 FF   50 -        00:00:00 -
damu@ubuntu:~$ chrt -p 7719
bash: chrt: command not found
damu@ubuntu:~$ chrt -p 7720
bash: chrt: command not found

Work in progress...

The big one missing for me on Edgy is Rosegarden 1.4.0. Having using it in STG and Feisty, I wouldn't feel to go back to the 1.2.4. 
I found some debs and rpms for 1.4.0 but always got some dependencies issues on Edgy or following the advices given on one thread , I could install it but Rosegarden wouldn't start (rosegarden: error while loading shared libraries: liblrdf.so.2: cannot open shared object file: No such file or directory).

Thanks again for your work Luneo. It feels like a big step forward for audio on Ubuntu.

---

### Post by MetalMusicAddict on 2006-12-09
luneo please contact me on IRC at #ubuntustudio on Freenode. My nick is _MMA_

---

### Post by rytmisk on 2006-12-09
Great work!

I actually made the 2.6.19-rt ork on my laptop - even learned something along the way... Why has never my wireless worked when I have tried other kernels - because I had to make a link to /lib/firmware and the original folder with the name of the new kenel... Pretty easy when you know it, but I always thought there was something wrong wih the kernels. Stupid me!

One thing though! Despite me being very(!) happy with your kernel - could you please help out on the actual release of ubuntustudio as well/instead? They need help and you are extremely capable!!

best regards!
Ketil

---

### Post by falkenberg_cph on 2006-12-10
Well, that settles it for me. I need your precompiled kernels.
I just had the patching and compiling going really well, and suddenly... my computer shut down ](*,)  - im afraid it overheated (it had been working pretty hard all day reinstalling Ubuntu, goodbye windows).

So, any news from zendurl? - when will you be back up again?

/Carsten

---

### Post by damu on 2006-12-11
I would like to install the rt10 kernel, but I can only see 2.6.19-rt6 and 2.6.18-rt7 on the devlinuxbr.codigolivre.org.br 32bit/ repositories. Is the rt10 on another repository?

---

### Post by falkenberg_cph on 2006-12-11
what am i doing wrong?
i added *deb [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/* to my /etc/apt/sources.list - i then ran *sudo apt-get update* - but no rt kernels shows up in synaptic? Why?

/Carsten

---

### Post by sgx on 2006-12-12
Thanx for getting qaconnect going! I got a 2.16.9 kernel, now to install it...

---

### Post by sgx on 2006-12-13
> **luneo said:**
> Ok... there is the qaconnect gui....:-D  ...
Just grab it, and install it...
Oh... if someone wants to compile it... you must change the line 27 on connector.h ....
Where it is: ConnectorWidget::ConnectorWidget(QWidget *parent, snd_seq_t *pseq);

It should be: ConnectorWidget(QWidget *parent, snd_seq_t *pseq);

That's all! If you don't want to change by hand grab the patch... and patch it....8)

Thanx very much...here is a link to qjackconnect, another similar app that works
when some others fail...If you can make a package for this, even more vsts will work!
thanx. Got your 2.6.19 kernel in my grub menu,  next, learning to configure   8')

[http://suse.osuosl.org/people/mana/](http://suse.osuosl.org/people/mana/)

---

### Post by falkenberg_cph on 2006-12-15
Sorry for bringing this up again. But im really having problems with [http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/).

Heres what i:

1. sudo gedit /etc/apt/sources.list
(i insert deb [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ in the end of the file, and save)

2. sudo apt-get update.
Apart from much more, i get these messages (translated from danish).

Ignoring [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Release.gpg
Ignoring [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Release
Ignoring [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Packages
Allready had [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Packages

3. search synaptec for "kernel-image"
No kernel-images containing rt show up.

Can anyone explain this, please :???: 
/Carsten

---

### Post by zettberlin on 2006-12-16
Thanks for providing these packages - this ist the first deb-binary for Ardour 2 right :-)

The p4 Kernel installs and starts very well yet the first test with ams does not yield very good results, if I play a complex 4-Oscillators/6polyphony patch with these jacksettings:

jackd -R -t1000 -u -dalsa -dhw:0 -r96000 -p32 -n2

I get hundreds of xruns whithin a minute plus several dropouts.

Using the testing-kernel from ubuntumusique in edgy with the same settings works better. about 10 xruns/h and no dropouts with the same patch/settings.

---

### Post by finferflu on 2006-12-16
> **falkenberg_cph said:**
> Sorry for bringing this up again. But im really having problems with [http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/).

Heres what i:

1. sudo gedit /etc/apt/sources.list
(i insert deb [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ in the end of the file, and save)

2. sudo apt-get update.
Apart from much more, i get these messages (translated from danish).

Ignoring [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Release.gpg
Ignoring [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Release
Ignoring [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Packages
Allready had [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) 32bit/ Packages

3. search synaptec for "kernel-image"
No kernel-images containing rt show up.

Can anyone explain this, please :???: 
/Carsten

I think he's right, this is what I get when I write *sudo aptitude install kernel-image* and double press TAB:

```
$ sudo aptitude install kernel-image
kernel-image                   kernel-image-2.4.27-2-k6
kernel-image-2.4               kernel-image-2.4.27-2-k7
kernel-image-2.4.27-2-386      kernel-image-2.4.27-2-k7-smp
kernel-image-2.4.27-2-586tsc   kernel-image-2.6
kernel-image-2.4.27-2-686      kernel-image-netboot
kernel-image-2.4.27-2-686-smp  kernel-image-netbootable

```

There's no kernel-image with *rt*...

Any hint? 

Thanks!

---

### Post by auricle on 2006-12-16
I have a problem. I have installed the 2.6.19-rt6-generic kernel, kernel headers, ndiswrapper and nvidia modules but when I boot into this kernel my pci wireless card is not detected or loaded and in kubuntu's System Settings it shows that I don't have any available network devices in Network Settings. 

I have a Netgear WG311T pci wireless card which is automatically detected and configured in the standard kubuntu installation. It is my only connection to the internet.

How can I get my wireless card working? 

Otherwise the RT kernel is working great! Thanks!

---

### Post by finferflu on 2006-12-16
How did you manage to install it?

---

### Post by auricle on 2006-12-16
I added the repositories as the instructions say on [http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/) and then installed the apropriate rt packages using adept.

---

### Post by auricle on 2006-12-17
* bump

What has happened to the Ubuntu Studio forum? Why has it merged with Multimedia & Video?

---

### Post by MetalMusicAddict on 2006-12-17
> **auricle said:**
> What has happened to the Ubuntu Studio forum? Why has it merged with Multimedia & Video?

I had it removed because most of the threads had nothing to do with our project. It was creating alot of confusion, like this thread.

We will open up our own forum in the coming weeks.

---

### Post by damu on 2006-12-17
MetalMusicAddict, can you explain this decision a bit more. I don't get it. It seems Ubuntu Studio is about an open source system based on Ubuntu which purpose is to deliver authoring tools for audio, video and graphics. The first thing needed (and probably one of the only thing missing in Ubuntu now) for audio is an rt-kernel, and this thread was about that. 
Most of the other threads were very much about audio tools for authoring and hardware issues. It had nothing to do with most of the threads that we find in the section multimedia & video, which don't relate to authoring tools.
So how the previous forum was creating confusion and how is this one more appropriate?

Thanks

---

### Post by MetalMusicAddict on 2006-12-17
damu, Look [HERE]("http://www.ubuntuforums.org/showthread.php?p=1897976#post1897976").

---

### Post by zettberlin on 2006-12-17
> **damu said:**
> 
So how the previous forum was creating confusion and how is this one more appropriate?


Good question, I´d like to know this also...

Plus: Why there was no announcement??

---

### Post by MetalMusicAddict on 2006-12-17
> **zettberlin said:**
> Good question, I´d like to know this also...

Plus: Why there was no announcement??

See the link I gave above. I dont wanna keep this thread off-topic.

---

### Post by finferflu on 2006-12-17
> **auricle said:**
> I added the repositories as the instructions say on [http://devlinuxbr.codigolivre.org.br/](http://devlinuxbr.codigolivre.org.br/) and then installed the apropriate rt packages using adept.

So you're on KDE as well, I've added the same repositories as the instructions say, but I can't find any rt package... what was your search criteria?

Thanks!

---

### Post by luneo on 2006-12-18
Ok... new kernel... 2.6.19.1-rt15, new ndiswrapper and nvidia  modules for the new kernel... now things should be working ok, hpet support activated, and some others things, the config is based on Ingo Molnar's, qaconnect is now a part of the repo, and new ardour 2 beta9... all built today!

---

### Post by luneo on 2006-12-18
and you should install... linux-image-2.6.19.1-rt15-generic and linux-headers-2.6.19.1-rt15-generic

---

### Post by MetalMusicAddict on 2006-12-18
luneo I would like it very much if you would contact me. Your work would benefit a much greater number of people if you would work with Ubuntu.

I sent a PM a week or so ago.

---

### Post by .t. on 2006-12-18
luneo:
I have noticed you have created packages for multimedia on Ubuntu. There is already a project with which I and others (for instance MetalMusicAddict above me) work to achieve this end, and we would love you to come and work with us. Why could this not be possible? Thanks, .t.

Please; come and join us on IRC in #ubuntustudio on irc.freenode.net

---

### Post by luneo on 2006-12-18
You guys should check the [http://devlinuxbr.codigolivre.org.br](http://devlinuxbr.codigolivre.org.br) for a Jack Control config... so you can achieve a low score of xruns...

---

### Post by finferflu on 2006-12-18
Thank you for your work, and for pointing out the correct names. I'm downloading right now. Thanks!! :D

---

### Post by luneo on 2006-12-18
The ardour2 package in the repo is newer than the svn20061128... but because of the name 2.0beta9, Synaptic (or apt-get) thinks that the beta9 is older... so you need to uninstall ardour2 and install it again, or you need to find ardour2 in synaptic and highlight it and then click on Packges, and Force Version and select 2.0beta9....

---

### Post by luneo on 2006-12-18
now there is also a madwifi package for the 2.6.19.1-rt15 kernel... so if you have problems with wireless, install madwifi, and ndiswrapper...

---

### Post by luneo on 2006-12-18
new update... new qjackconnect package in repo...

---

### Post by finferflu on 2006-12-18
Wow!! You're working very hard! Thanks for helping us so much!! :D

---

### Post by luneo on 2006-12-19
If there is an app request, just post it, and I`ll see what I can do...

---

### Post by finferflu on 2006-12-19
Well, actually I've got one, but it's not just about packaging, it's more integration with JACK. It's a guitar effect processor. Without JACK integration it's just useless for recording, which is a pity, being such a great app.

The project page is [http://www.jesusonic.com/](http://www.jesusonic.com/)

Also there is a very fun app, I haven't tried it yet, it's called [Ninjam]("http://www.ninjam.com"), which lets you jam in real time with other people through the internet. There is only the source code available...

Thanks a lot!

---

### Post by falkenberg_cph on 2006-12-19
Woohoo. i finally managed to make it work. :D :p :cool: 
Just wanna say thanks Luneo - and i further want to add:

You're good and productive. Dont be mad about the reference to this particular thread when they closed down the studio forum (sadly). You should definitely start collaborating with the ubuntu studio team.

Thanks Again
Carsten

---

### Post by EricS on 2006-12-30
EDIT: I put in the steps directly here instead of just linking (in case the link source would dissapear)

> **finferflu said:**
> Well, actually I've got one, but it's not just about packaging, it's more integration with JACK. It's a guitar effect processor. Without JACK integration it's just useless for recording, which is a pity, being such a great app.

The project page is [http://www.jesusonic.com/](http://www.jesusonic.com/)


The biggest problem is that Jesusonic is not opensource (source is not public). Even though the developers have said that they're planning jack support in jesusonic there haven't been any update in more than a year now. :/

But there is hope! :) You can create "virtual" alsa-channels that connects to jack and let jesusonic connect to these channels!

These are the steps to get jesusonic working with jack:

1. Edit the file ~/.asoundrc (/home/"yourusername"/.asoundrc) to include this: (create the file if it doesn't exist)

```
pcm.jesusplug {
	type plug
	slave { pcm "jack" }
}
        
pcm.jack {
	type jack
	playback_ports {
		0 alsa_pcm:playback_1
		1 alsa_pcm:playback_2
	}
	capture_ports {
		0 alsa_pcm:capture_1
		1 alsa_pcm:capture_2
	}
}
```

2. Install libasound2-plugins:
```
# sudo aptitude install libasound2-plugins
```
3. Start jack (perhaps with qjackctl)
4. Start jesusonic with:
```
# jesusonic -mode ALSA -in jesusplug -out jesusplug -high
```


( Explained here [http://www.cockos.com/forum/showthread.php?goto=lastpost&t=44](http://www.cockos.com/forum/showthread.php?goto=lastpost&t=44) )

---

### Post by A_POET on 2007-01-18
Hi I am trying to get the newest kernel to work, and i think that the newest nvidia stuff is newer than the driver that the kernel is asking for? it said something about that in the log output when it failed to start the x server..

can someone please help me :(


thanks


edit: I ended up figuring out what to do.... sorry (im noobish, but obviously learning...i guess :lol:)

thanks for all your hard work luneo--helping me do what i do best :)

---

### Post by packoman on 2007-01-24
Hi,
I stumbled across this thread looking for a way to finally get a fully working linux audio setup based on ubuntu.
I download your 2.6.19.1 rt-kernel and the ndiswrapper which I could get to run. 
I recently saw that you also have a 0.9.3beta package of the madwifi-driver. Wanted to download it, but your site has been down since then...
so the question is if and when it will be back-up again? I need the wireless lan internet connection so i can get all the packages i need. feel a little hung up at the moment.
besides that it's just great, that people like you put so much effort into this... thanks!
greetz,
           michael

---


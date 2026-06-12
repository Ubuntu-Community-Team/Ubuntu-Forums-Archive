---
title: "My only issue against Ubuntu"
date: 2008-09-29
forum: Multimedia Software
---

### Post by blakjesus on 2008-09-29
I apologize if this is the wrong place to post this. If it is please move it to the correct place.

I think Ubuntu is an awesome OS. I rarely use my XP partition because of it, but it does have one setback that really bothers me.

Anytime im browsing the internet while listening to music, (which is all of the time) if i come across a flash video or something that plays sound, i am forced to shutdown Rhythmbox and firefox and then start firefox back up and reload the webpage. :-k Then if i want to go back to listening music, i have to shutdown firefox and restart Rhythmbox. 

Why isn't Ubuntu designed to handle more than one audio source at a time? :confused: I mean if i want to quickly watch a video on the internet, i should be able to just pause my music and play the video but i am forced to do this long process.

---

### Post by littletinman on 2008-09-29
I've been having the same issue. It's a set back, but livable. I'd love to be able to fix this though.

---

### Post by Tadhg on 2008-09-29
That's is definitely not a feature of Ubuntu, it's a issue with your sound card setup. Not sure exactly the fix, but post in General help and you should be able to sort it out

---

### Post by blakjesus on 2008-09-29
This has happened on all 3 computers i have used Ubuntu on. And i haven't found any kind of fix for it.

---

### Post by Vince4Amy on 2008-09-29
I had some of the same problems only with different applications.

Give this a try:

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by binbash on 2008-09-29
Btw ubuntu is not OS, it is a distro.Linux is the OS.And you problem is not about ubuntu it is a sound card or alsa config issue.

---

### Post by adam_kimber on 2008-09-29
> **blakjesus said:**
> This has happened on all 3 computers i have used Ubuntu on. And i haven't found any kind of fix for it.

This happens on my machine too. Its a common problem. The problem arises when programs like Flash and Skype want to hog the soundcard so nothing else can use it. Makes for an annoying experience. The link above should help as Pulseaudio is supposed to mitigate all conflicts of soundcard use.

---

### Post by LaRoza on 2008-09-29
That is annoying. However, sound can be an issue anywhere. I have two sound devices, speakers and headphones, both work in Ubuntu. Neither do in Windows for some reason (well, reliably).

---

### Post by adam_kimber on 2008-09-29
> **binbash said:**
> Btw ubuntu is not OS, it is a distro.Linux is the OS.

If you want to get into semantics then the OS is [GNU/Linux]("http://www.gnu.org/gnu/gnu-linux-faq.html#why") of which Ubuntu is a [distribution]("http://distrowatch.com/"). :D

Sorry OP for derailing your thread. ](*,)

---

### Post by Circus-Killer on 2008-09-29
> **binbash said:**
> Btw ubuntu is not OS, it is a distro.Linux is the OS.And you problem is not about ubuntu it is a sound card or alsa config issue.

That issue has been thrown out soooo soooo many times (in part due to rms), and its clear that you quite good at repeating other people's words.

However, I do not think the intent of rms' points were to deface every thread that makes such an "error". In no way does you "correcting" the OP to not call Ubuntu an OS has helped the OP in absolutely no way. Please refrain from making that same correction for every single post that refers to Ubuntu to an OS. Apologies to OP and forum staff for going OT, just tryna avoid binbash from going OT in every thread that refers to Ubuntu as an OS.

---

### Post by Canis familiaris on 2008-09-29
Well it works for me. Seems like a PulseAudio Problem for you...

---

### Post by SupaSonic on 2008-09-29
I always have this with PulseAudio. The solution is removing it, and switching to ALSA. I never understood what was wrong with ALSA in the first place - sound works from everywhere simultaneously with it.

---

### Post by Vadi on 2008-09-29
There's a thread with PulseAudio fixes available. I don't have a link, but one guy made a pretty good post that fixed it for a lot of people, including me.

---

### Post by blakjesus on 2008-09-29
Thanks for your quick replies. I will try out what you have said and ill get back to you. :popcorn:

---

### Post by K.Mandla on 2008-09-29
I'm going to drop this in Multimedia and Video. You'll get a better quality of advice there.

Oops! :shock: Did I type that out loud?! :oops:

---

### Post by Vadi on 2008-09-29
Here is the magic post: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by eye208 on 2008-09-29
There are lots of guides about PulseAudio out there, but none of them really fixes sound issues for all applications. The only solution to address all of them is to remove PulseAudio.

The good news: It's done really quick, and it's easily reversible too in case you change your mind later. Here's the guide:

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

---

### Post by markbuntu on 2008-09-29
> **eye208 said:**
> There are lots of guides about PulseAudio out there, but none of them really fixes sound issues for all applications. The only solution to address all of them is to remove PulseAudio.

The good news: It's done really quick, and it's easily reversible too in case you change your mind later. Here's the guide:

[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)

You are not just wrong about that, you are spreading disinformation and you should stop. Pulseaudio can be setup for all your sound applications and you can also use it to get around the buggy volume control for usb headsets present in the alsamixer.

The guide here will not just help you to get your sound working but will get it working properly with pulseaudio. You might as well figure it out now since it will be in every current and future release of Ubuntu and many other distributions. You will find it to be an hour or so well spent.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by wolfen69 on 2008-09-29
```
sudo apt-get install libflashsupport
``` i'm surprised no one has mentioned this. it is a fairly common problem.

---

### Post by eye208 on 2008-09-29
> **markbuntu said:**
> You are not just wrong about that, you are spreading disinformation and you should stop. Pulseaudio can be setup for all your sound applications and you can also use it to get around the buggy volume control for usb headsets present in the alsamixer.

The guide here will not just help you to get your sound working but will get it working properly with pulseaudio. You might as well figure it out now since it will be in every current and future release of Ubuntu and many other distributions. You will find it to be an hour or so well spent.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Here's a quote from your guide:

> Things I have used and tested: audacious, rythmbox, xmms, ardour, hydrogen, rosegarden, vlc, mplayer, totem, miro, streamtuner, tunapie, firefox, opera, ZynAddSubFx, Amarok, Banshee, jackrack, soundrecorder.....
Things I do not use: audacity, xine, skype, wow, wine, second life....(but you can find a link to help with most of those here)
If stuff doesn't work, you don't use it. How convenient. These are the facts:[list][*]There is no fix for Audacity (other than suspending PulseAudio completely).[*]The proposed fixes for Flash and Skype don't work. People complain about crashes (Flash), 100% CPU load (Skype) and other issues such as stutter etc.[*]There is no fix for Second Life.[*]WineAsio depends on Jack. Routing it through PulseAudio would defeat the whole purpose of emulating ASIO in the first place.[/list]
I'm spreading disinformation? Well, go ahead and prove me wrong.

When it comes to PulseAudio issues, your bias simply makes you redefine the dimension of the problem until it matches your solution. Whenever your solution is insufficient for a specific case, you blame the application for not being written properly. What do you expect people to do? Stop using Skype and Flash? Lower their expectations until PulseAudio begins looking worthwhile?

As I pointed out several times, there is nothing in PulseAudio that ALSA and Jack cannot do. Most users would be far better off if Canonical had just included and enabled the full set of ALSA and Jack tools (e.g. loopback driver, virtual MIDI driver, Jack and A/52 plugins, aoss, NetJack, libsamplerate) by default instead of leaving them out or dropping them in favor of PulseAudio.

Regarding the future of PulseAudio, I think you are a bit too optimistic. PulseAudio will certainly not take over any of the audio/music production related distributions, and ALSA will remain the core audio layer of mainstream distros as well. I expect PulseAudio to be phased out just like OSS, aRts, and ESD, simply because it's redundant and doesn't bring anything new to the table (except hype). Applications will continue to work with plain ALSA because this is the component that is guaranteed to always be there, unlike PulseAudio which is optional.

---

### Post by markbuntu on 2008-09-29
Look, just because you got a little frustrated and angry when you got to Hardy and your sound didn't work does not give you a license to go on a crusade against Pulse Audio which is what you have been doing these past months.

You say that ALSA can do everything Pulse Audio can? OK then, write a guide, show us how easy it is.

I want ALSA to do this:

I want to be able to change my applications from one sound device to another or to my home newtwork and back on the fly.

I want to be able to use all my sound devices at the same time or individually or in any combination with point and click.

I want to control the volume of individual applications from one place.

I want all my running OSS and ALSA applications to play through jack or through my other sound card or usb headset as I choose on the fly.

4 simple things. Show me how to do this with ALSA.

Anyway, the FLash and Skype and Scond Life issues are very old issues that were fixed a long time ago. 

Audacity was written for the deprecated portaudio sound server and still thinks it is using it. The audacity devs have not worked on their kludgy OSS and ALSA plugins for 3 years or ever attempted to actually port it over to use the ALSA or OSS sound servers. It barely works with jack and has none of the jack functionality available in ardour.

You should really try to keep up.

---

### Post by eye208 on 2008-09-30
> **markbuntu said:**
> Look, just because you got a little frustrated and angry when you got to Hardy and your sound didn't work does not give you a license to go on a crusade against Pulse Audio which is what you have been doing these past months.
The crusade is against ALSA. The PulseAudio hype got so bad that there are actually people now believing that ALSA can handle only one application at a time. Of course once you live in that reality distortion field, you are much more willing to cope with the numerous issues. And that's what is really happening here. People put up with PulseAudio because they don't know much about ALSA since there is no hype surrounding it. This is made even worse by the fact that many PulseAudio issues appear to be ALSA issues when in fact they are not. People won't realize this until they remove PulseAudio and see their troubles disappear instantly.

The PulseAudio mess had already unfolded long before I even considered switching to Hardy. In fact if there had not been a quick fix like this, I would have switched distros instead of releases. I'll probably do so anyway when Debian switches to Live CDs with the upcoming release 5.0. Debian's libasound-plugins package is not crippled like Ubuntu's.

> You say that ALSA can do everything Pulse Audio can? OK then, write a guide, show us how easy it is.

I want ALSA to do this:

I want to be able to change my applications from one sound device to another or to my home newtwork and back on the fly.

I want to be able to use all my sound devices at the same time or individually or in any combination with point and click.

I want to control the volume of individual applications from one place.

I want all my running OSS and ALSA applications to play through jack or through my other sound card or usb headset as I choose on the fly.

4 simple things. Show me how to do this with ALSA.
Use the [Jack plugin for ALSA](http://alsa.opensrc.org/index.php/Jack_(plugin)). I have not seen any meaningful OSS-only application for a while, but for the sake of completeness there is aoss and oss2jack.

Once the application is connected to Jack, there's no limit to what you can do. You can run multiple instances of Jack, connect them to separate ALSA devices and link them using NetJack. You can route client streams through filter chains, between applications, across the network etc. Of course I'm not telling you anything new here. You just keep ignoring it because it makes the PulseAudio revolution look slightly pale.

> Anyway, the FLash and Skype and Scond Life issues are very old issues that were fixed a long time ago.
No, they are not. Neither is the Second Life issue.

> Audacity was written for the deprecated portaudio sound server and still thinks it is using it. The audacity devs have not worked on their kludgy OSS and ALSA plugins for 3 years or ever attempted to actually port it over to use the ALSA or OSS sound servers. It barely works with jack and has none of the jack functionality available in ardour.
See? That's what I mean. You blame application developers for not following the PulseAudio hype. This is typical evangelist attitude. Sorry, but those guys may just have something better to do than to embrace each and every "sound API of the day" coming along.

---

### Post by blakjesus on 2008-09-30
Ok. I have been able to fix the sound issue between my different applications. :) Except for flash. It just doesn't want to play nice. :confused:

---

### Post by markbuntu on 2008-09-30
> **eye208 said:**
> The crusade is against ALSA. The PulseAudio hype got so bad that there are actually people now believing that ALSA can handle only one application at a time. Of course once you live in that reality distortion field, you are much more willing to cope with the numerous issues. And that's what is really happening here. People put up with PulseAudio because they don't know much about ALSA since there is no hype surrounding it. This is made even worse by the fact that many PulseAudio issues appear to be ALSA issues when in fact they are not. People won't realize this until they remove PulseAudio and see their troubles disappear instantly.

Well, let me tell you a story about that. When I first installed Hardy I had all sorts of problems, not being able to login was first, a buggy video driver was second. By the time I got around to "fixing" my sound problems one of the first things I tried was get rid of pulseaudio. But then I bought a new sound card and I wanted to use them both. I looked high and low for information about using two sound cards in ALSA and the info I found was quite distressing. First, I could configure asound.rc and jack to use them both but they would drift as their clocks drifted. 

There were three solutions I found to that and one involved buying new expensive professional sound cards in pairs, another involved buying two identical consumer cards and physically wiring the clocks together and the third was installing PulseAudio. 

So, reluctantly I returned to PulseAudio and I figured it out. Because I am running 3 different versions of Hardy on my machine and had made many many changes to sound configurations trying to get things to work, I wrote myself a little guide and using that I could re-institute a working sound scheme in about 5 minutes no matter what I did. So, to help others to figure out this PulseAudio mess I posted it. 

Since then I have expanded my guide into a general troubleshooting guide and added links to everywhere I could find that offered people solutions to their sound problems, hardware and software, even to OSS4.


> 
The PulseAudio mess had already unfolded long before I even considered switching to Hardy. In fact if there had not been a quick fix like this, I would have switched distros instead of releases. I'll probably do so anyway when Debian switches to Live CDs with the upcoming release 5.0. Debian's libasound-plugins package is not crippled like Ubuntu's.


Use the [Jack plugin for ALSA](http://alsa.opensrc.org/index.php/Jack_(plugin)). I have not seen any meaningful OSS-only application for a while, but for the sake of completeness there is aoss and oss2jack.

Once the application is connected to Jack, there's no limit to what you can do. You can run multiple instances of Jack, connect them to separate ALSA devices and link them using NetJack. You can route client streams through filter chains, between applications, across the network etc. Of course I'm not telling you anything new here. You just keep ignoring it because it makes the PulseAudio revolution look slightly pale.

Much as I like jack, it is a resource hog and my machine would just bog down running multiple instances. Should I buy a new computer just so I can use netjack? Anyway, Jack is not part of ALSA. It is a connection kit that runs on top of the ALSA drivers, just like PulseAudio is a sound server that runs on top of the ALSA drivers. If you want to have a debate about jack vs pulseaudio that is a whole other thing but don't drag jack into this to defend yourself.

Jack was written because ALSA did not do what the jack devs wanted to do. It is geared toward one thing and one thing only, professional quality sound production which was pitiful in ALSA before jack came along. They also wrote ardour and in their view, if you are not using ardour and jack, you are not using jack because much of the reason jack was written, timing coherence and coordination between applications, will be entirely missing with an application like Audacity that just has a plugin. 

> 

No, they are not. Neither is the Second Life issue.


Did you ever bother to visit pulseaudio.org?

> 
See? That's what I mean. You blame application developers for not following the PulseAudio hype. This is typical evangelist attitude. Sorry, but those guys may just have something better to do than to embrace each and every "sound API of the day" coming along.

Even when I was trying to use Audacity without PulseAudio it would crash all the time, seize up my system, and block my other applications. I could never get Audacity to actually work with Hydrogen or Rosegarden so I switched to ardour which proved to be not only more usable, but professional quality like you find in a real recording studio.

Anyway, Audacity is the ONLY application I tried to use that has problems with pulseaudio. I can run pulseaudio and jack at the same time and have tested over 30 applications that use one or the other and they all work, every time, without a problem. Why can't I use Audacity?

Blaming that on pulseaudio is a stretch when so many other applications work fine. In fact, pulseaudio has revealed many poorly written alsa interfaces which, while they tend to work in alsa, do not actually conform to the alsa standards. Just good enough to work is not really very good as all these apps would break eventually at some update so Pulseaudio is actually doing everyone a favor by exposing all this bad code now and forcing the devs to conform to the alsa standards now.

I really never understood the dogged persistence of audacity users and I doubt I ever will and if that is the biggest reason for slagging Pulseaudio....lol.

---

### Post by matthewbpt on 2008-09-30
I managed to fix this issue by configuring pulseaudio properly, something with should be done automatically during installation (hint to developers!). Once pulseaudio is set up properly it works perfectly with as many audio sources as you want. This is what I did:

Opened up Synaptic Package Manager from 'System > Administration'
Click on 'Search' and type in pulseaudio and search.
Mark the following packages for installation from the results (by right clicking):

asoundconf-gtk
gstreamer0.10-pulseaudio (or whaterver version is currently in the repos)
libpulse0
libpulse-browse0
libpulsecore5
libpulse-mainloop-glib0
padevchooser
paman
paprefs
pavucontrol
pavumeter
pulseaudio
pulseaudio-esound-compat
pulseaudio-module-gconf
pulseaudio-module-x11
pulseaudio-module-zeroconf
pulseaudio-utils

You'll find you already have some of these installed, just install the ones you dont ahve installed.

Then after everything is installed, close Synaptic and go to 'System > Preferences > Default Sound Card' and choose your sound card from the list.

Then go to 'System > Preferences > Sound' and put Autodetect on everything and select your sound card device in the as the Default Mixer Track.

Now go to 'Applications > PulseAudio Device Chooser'

A new icon should appear on the system tray on the top right, looks like a headphone plug. If you click on it you can open the Manager and see the server running from your sound card, its very cool. And if you click on the icon and press Volume Control you can control the volume of each Audio application your running individually, thats also very cool.

If somehow this doesnt work then try going back to 'System > Preferences > Sound' and selecting sound playback in all to 'PulseAudio Sound Server' then try.

This should work, tell me how it works out for you.
Hope I helped!

It's a mystery to me why Ubuntu doesn't properly set all these options automatically on installation, the sound experience is really crippled without it. Once it's set up correctly the sound experience is much better than Windows IMHO.

-Matt

---

### Post by matthewbpt on 2008-09-30
Sorry for the double post, but in reply to the above posts, once PulseAudio is set up PROPERLY it is infinetely better than ALSA I think. I have pulseaudio running sound from two soundcards simultaneosly, and now finally have a perfect 5.1 surround setup, something I never managed with ALSA. PulseAudio is getting a bad reputation because Ubuntu developers seemed to have done a very poor job integrating into the system. Hopefully this will be addressed in Intrepid Ibex.

---

### Post by Crafty Kisses on 2008-09-30
This has happened to me from time to time, but I just restart Firefox and it works just fine.

---

### Post by doas777 on 2008-09-30
> **adam_kimber said:**
> If you want to get into semantics then the OS is [GNU/Linux]("http://www.gnu.org/gnu/gnu-linux-faq.html#why") of which Ubuntu is a [distribution]("http://distrowatch.com/"). :D

Sorry OP for derailing your thread. ](*,)

not to jump in, but I was always told that linux is a kernel. nothing more nothing less.

to me however ubuntu is a philosophy and a way of life.

---

### Post by eye208 on 2008-10-01
> **matthewbpt said:**
> once PulseAudio is set up PROPERLY it is infinetely better than ALSA I think.
And infinitely worse than Jack.

PulseAudio falls short in three aspects:[list=1][*]It is incompatible, i.e. it requires changes in applications that worked flawlessly before.[*]It makes things more complicated for the average user who has only one soundcard and just wants it to work the way it did in Windows.[*]It is not good enough to replace Jack.[/list]
Issue #1 will eventually be resolved, but the others remain. What I observe here is a small crowd of users with special needs (bundling two soundcards, streaming sound across networks etc.) imposing their will on the rest.

You are totally ignoring the fact that the vast majority of users does not benefit from PulseAudio in any way.

PulseAudio already existed in Ubuntu 7.10 but it didn't bother anyone then because it was an optional component not installed by default. And it will continue to be an optional component because it is unable to replace ALSA and Jack.

markbuntu and others criticize me for pointing out the optional nature of PulseAudio, yet they are unable to provide solutions for the problems at hand. Fact is, some applications don't work with PulseAudio, no matter how you configure it. The PulseAudio fanboys want you to believe that removing PulseAudio is not a solution. Sorry, but it is. They want you to believe that ALSA is somehow crippled or broken. Sorry, but it's not. They want you to believe that Jack is a "resource hog". Sorry, but that's utter nonsense.

---

### Post by markbuntu on 2008-10-01
Well, for those of use with more than one sound device Pulseaudio provides valuable services. 

Jack is not even part of alsa so stop bringing jack into this. It is a stand alone audio connection kit that works with many sound servers so don't be confusing jack with alsa. Jack and Pulseaudio works in a very complementary manner for me. I use them both all the time. In fact I am using them both right now.

ESD is also not part of alsa. It has an alsa plugin so all your alsa applications can play together. That is what you are using, the Enlightened Sound Demon with its alsa plugin.

So, it seems to me that what many people think of as ALSA is really a bunch of brilliantly written add ons sitting on the ALSA sound server and low level drivers and providing services that are either not satisfactory in ALSA or entirely missing.

Many people these days do not have just one sound card. They have a built in sound card, a usb webcam which is its own sound device, maybe a usb headset which is a whole other sound device, and maybe a usb sound card so they can get surround sound out of their old computer. Pulseaudio makes it very easy to manage all these new devices.

I like jack and I like pulseaudio too. If they got closer together they would be even more useful. I don't care what they use. If I needed to use portaudio and could compile it to run on my machine/distribution I would.

If I could just set jack to use defaults and change them somewhere else, on the fly, without having to restart jack. That is what I want and Pulseaudio is the closest thing to it. All they need to come up with is a way to connect their sinks with their sources and I will be completely satisfied with sound in ubuntu/linux.

So, if you want to get rid of Pulseaudio and go back to a "pure alsa" setup which is actually a bunch of other stuff, go ahead. Every time you upgrade your distro just sudo apt-get purge pulseaudio first thing. But when you upgrade to krappy koala or moaning mona and nothing works, you will be welcome to use my guide and the first thing it will ask is "Did you sudo apt-get purge pulseaudio you imbecile?" 

I promise, it will say that.

---

### Post by Yellow Pasque on 2008-10-01
**cough** OSS4 **cough** vmix
Well, that's what worked for me when I tried multiple sound sources. I once had foobar2000(through wine), a Youtube vid, and esd properly operating at the same time on my M-Audio Revo. Of course, this was just for fun and I'm not sure it works with all apps/sound cards. I usually don't use vmix at all since I find system sounds and multiple sound streams annoying.

> I expect PulseAudio to be phased out just like OSS..
Who said OSS was phased out (unless you're referring to OSS 3.x)? OSS4 development is alive and well. There are many of us who hope that one day, kernel developers drop their grudge against OSS (it was closed source at one time), work on improving it and make ALSA/P.A. go the way of the dodo.

---

### Post by markbuntu on 2008-10-01
Well Temujin, what I would really like for OSS4 would be just some good low level sound drivers in the kernel and a solid API. We need drivers man, drivers, drivers, drivers, and a quick and easy API so we can make full use of them.

I really do not care where the backend comes from and would switch to OSS4 in a heartbeat if I could use jack and pulseaudio with it. Drivers that show all the sound devices capabilities in a consistent manner and a sound mixer that does the same, that's all I want.

PA does good things and has its place, so does jack. Why fight them when you can join them and get all the good things without reinventing the wheel?

---

### Post by doas777 on 2008-10-01
> **markbuntu said:**
>  But when you upgrade to krappy koala or moaning mona and nothing works, you will be welcome to use my guide and the first thing it will ask is "Did you sudo apt-get purge pulseaudio you imbecile?" 

I promise, it will say that.


Markbuntu, Thats the best laugh I've had all day:D. Thank you.

---

### Post by bigdee973 on 2008-10-01
> **Tadhg said:**
> That's is definitely not a feature of Ubuntu, it's a issue with your sound card setup. Not sure exactly the fix, but post in General help and you should be able to sort it out

i dont think so i've had different pcs with different sound cards etc and i have experienced the same thing over and over again particularly with Dell computers and even ECS motherboard computers.

---

### Post by Yellow Pasque on 2008-10-01
> We need drivers man, drivers, drivers, drivers
How about ALSA start with an X-fi driver (and not the outdated one from Creative that requires kernel recompilation on Hardy)? I personally despise Creative and its products, but there are loads of people who just buy Creative's latest card because it has the best marketing. The OSS devs have done a good job keeping up with the (way too) many X-fi models and will add a PCI ID if you ask nicely.

> and a solid API
The OSS4 API is known for being well-documented and stable. ALSA is known for being poorly documented. The OSS devs have tried twice to make an ALSA compatibility layer (Cuckoo and SALSA), but could not do it properly because of ALSA's frequent changes and poor documentation.

> PA does good things and has its place, so does jack. Why fight them when you can join them and get all the good things without reinventing the wheel?

I personally don't need them, but the last time I checked, you can use JACK with OSS (again, an ALSA compatibility layer would help for ALSA-only apps). You can also use P.A. with OSS4.1 (see OSS's wiki), though this is not well-tested.

BTW, how many users truly want/need the features of P.A.? If it didn't come by default in Hardy to fix ALSA's mixing, how many users would install it? Also, if the developers of P.A. wanted to, they could make it fully compatible with OSS4. Note that the developer(s) of P.A. often admit that they're ALSA fans and won't exert any effort on this because, from their POV, OSS4 is a UNIX/BSD system that happens to work on Linux. Instead, they recommend switching to ALSA when someone submits an OSS-related ticket and churn out FUD like this in the guise of developer guides: [http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)

As an end-user and forum helper, I think OSS4 holds more promise to most end-users. What it needs are more devs and knowledgeable users. Personally, ALSA never worked properly for me (and many others), and it doesn't look like they're going to fix my (well-known) issues with it any time soon.

---

### Post by eye208 on 2008-10-02
> **markbuntu said:**
> Jack is not even part of alsa so stop bringing jack into this.
I never said it was part of ALSA. But it has been around for years and makes PulseAudio look lame even today. Why didn't the PulseAudio developers just extend Jack instead of adding yet another layer to the Linux audio mess? Is this another case of the not-invented-here syndrome?

> ESD is also not part of alsa.
I never said this either. The only reason I mentioned it at all is because PulseAudio was advertised as a "drop-in replacement" for ESD. Guess what, the only application on my system that actually needs ESD does not work with PulseAudio's ESD compatibility layer. Epic fail. And of course your guide doesn't offer a solution either, yet you claim that you can "make PulseAudio work with all apps". It's not true. And then you accuse me of "spreading disinformation". Why would I lie about these things? I'm not a zealot like you. I just want stuff to work.

Even worse, you claim that Jack is a "resource hog". That's hilarious given the fact that PulseAudio's bad performance has been criticized numerous times.

> So, if you want to get rid of Pulseaudio
I don't want to. I have to. I can't just say: "Oh well, Second Life voice chat stopped working on Linux, so please use text chat when I am around, dear Windows and Mac users. Oh, and Skype stopped working too, so please download Ekiga if you want to call me. Sorry, I can't open that YouTube clip right now because no other app can use sound while Flash is running ... Ahm yes, Linux is crap, but it's getting better all the time! And I have this cool rotating desktop cube that totally rocks ... 8-["

> Every time you upgrade your distro just sudo apt-get purge pulseaudio first thing. But when you upgrade to krappy koala or moaning mona and nothing works, you will be welcome to use my guide
Actually I consider your guide very helpful because its length is a pretty good indicator of the current crappiness of PulseAudio. As soon as the PulseAudio developers stop pointing fingers and start fixing bugs, your guide will shrink instead of grow.

And when it comes down to zero pages, I will embrace PulseAudio. Thank you very much.

---

### Post by markbuntu on 2008-10-02
> **eye208 said:**
> 

Actually I consider your guide very helpful because its length is a pretty good indicator of the current crappiness of PulseAudio. As soon as the PulseAudio developers stop pointing fingers and start fixing bugs, your guide will shrink instead of grow.

And when it comes down to zero pages, I will embrace PulseAudio. Thank you very much.

The vast majority of my guide is not about PulseAudio,it is about helping people find information, mostly about getting their sound card to work properly and getting all the packages missing from the standard install that are really necessary for being able to use and control your sound, There are as many missing AlSA packages as PulseAudio packages.

If there was another single place where this information was available and actually explained what all these things do and how they work, I would just send people there and my guide would be about 5 lines long.

---

### Post by markbuntu on 2008-10-02
> **Temüjin said:**
> How about ALSA start with an X-fi driver (and not the outdated one from Creative that requires kernel recompilation on Hardy)? I personally despise Creative and its products, but there are loads of people who just buy Creative's latest card because it has the best marketing. The OSS devs have done a good job keeping up with the (way too) many X-fi models and will add a PCI ID if you ask nicely.


I second that, Creative products have been nothing but a big pain for linux since the beginning. 14 years ago I gave up trying to get my SB16 to work with linux kernel 0.9 something. I read the posts, they are full of wining complainers, "well it works with my  windows...." like we need to hear that. Most of those people seem to forget they are getting something for free. They would complain about free beer.

> 
The OSS4 API is known for being well-documented and stable. ALSA is known for being poorly documented. The OSS devs have tried twice to make an ALSA compatibility layer (Cuckoo and SALSA), but could not do it properly because of ALSA's frequent changes and poor documentation.


Yes, this is well known. No one has a clue what those 50,000 plus api calls do. Somewhere down the line this house of cards will collapse of its own weight.

> 
I personally don't need them, but the last time I checked, you can use JACK with OSS (again, an ALSA compatibility layer would help for ALSA-only apps). You can also use P.A. with OSS4.1 (see OSS's wiki), though this is not well-tested.

BTW, how many users truly want/need the features of P.A.? If it didn't come by default in Hardy to fix ALSA's mixing, how many users would install it? Also, if the developers of P.A. wanted to, they could make it fully compatible with OSS4. Note that the developer(s) of P.A. often admit that they're ALSA fans and won't exert any effort on this because, from their POV, OSS4 is a UNIX/BSD system that happens to work on Linux. Instead, they recommend switching to ALSA when someone submits an OSS-related ticket and churn out FUD like this in the guise of developer guides: [http://0pointer.de/blog/projects/guide-to-sound-apis.html](http://0pointer.de/blog/projects/guide-to-sound-apis.html)


Well, I will just have to get on Lennarts case about that. There are a lot of complaints from PA users that the pa  module hal-detect is not seeing their digital devices and so they are not available in pa. Lennart answers with "well the alsa drivers are so screwed up it is impossible to do it blah blah blah  so hal-detect only sees the first device on each sound card because we can't tell what the other ones are blah blah blah... it is all alsa's fault." Well to me, that is not really an answer.So someone figured out how to manually add these devices in default.pa and Lennart says "Well that is not the proper way to do that." but never explains what is the proper way, lol.


> 
As an end-user and forum helper, I think OSS4 holds more promise to most end-users. What it needs are more devs and knowledgeable users. Personally, ALSA never worked properly for me (and many others), and it doesn't look like they're going to fix my (well-known) issues with it any time soon.

I will most likely be switching one of my installations to Intrepid some time after its release ( when ati gets it drivers fixed), and will also put OSS4 on it, give it a whirl and put up a guide if it seems to warrant one or put in on my existing guide but that is getting sort of out of control size wise.

I am not really that enamored of PA but it does make my life easier with all the audio devices I have and I just like to give the anti-pa crusaders a hard time, someone has to stand up to them. 

Lots of people are plugging their computers into their tvs and surround sound systems, why? because they find the plugs. This is the future. Starting next year tvs will come with ethernet connections built in. Better get ready.

If I could find some other something with a GUI that would give me the same functionality and ease of use as PA and maybe a few of the missing whirlygigs like digital output control and source to sink connectivity, I would drop PA like a hot potato. Like maybe with OSS4.something....

---

### Post by markbuntu on 2008-10-03
btw, I got skype working in PA, took about 2 hrs to install it, test it, find the answer and test it again. I have included instructions in my guide, a special SKYPE section.

---

### Post by TeoK on 2008-10-04
there's a simple solution here..

[http://ubuntuforums.org/showthread.php?t=762353&highlight=flash+audio](http://ubuntuforums.org/showthread.php?t=762353&highlight=flash+audio)

worked for me.

---

### Post by cariboo on 2008-10-04
I have exactly the opposite problem, If I record a tv program using my tv tuner, I have to mute the sound on line-in or else I have audio from it all the time and it gets kind of confusing try to listen to music while watching a flash video and hearing the television audio all at the same time. :)

BTW I'm running an out of the box installation of Intrepid beta. THe only thing I had to set up was the video drivers which was done on first startup.

Jim

---


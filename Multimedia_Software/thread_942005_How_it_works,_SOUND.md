---
title: "How it works, SOUND"
date: 2008-10-08
forum: Multimedia Software
---

### Post by markbuntu on 2008-10-08
Many people are completely baffled at the way sound is structured in Ubuntu and more particularly, in Hardy Heron 8.04, long time users as well as noobs. I will attempt an explanation as I see it, starting from the bottom up. I am trying to be as non-technical as I can while still getting the point across.

[]b]Hardware[/b]
At the bottom is the hardware, usually a sound chip on the motherboard. While only a few basic chips are generally used, OEMs have great latitude in configuring them. both physically and in the software/firmware that interfaces the chip to the operating system.  For example, some manufacturers decide to have two microphone jacks on their machines, one in front, one in back, others reconfigure the input and output ports. so maybe the line in becomes the side or lfe output for surround sound. Sometimes they do this within the same model of a computer. 
Needless to say, this has created widespread confusion among users and the driver writing community. 

Then there are sound cards, the most popular are the Creative Labs Soundblaster cards. These have alternately frustrated and infuriated linux users since linux fist started and the situation has not much improved until now. Recently Creative has completely given up on writing its own crappy linux drivers and released some information to the community. But still.... Other manufacturers include C-Media who OEMs cards to many resellers including Turtle Beach and SIIG among others. These cards are well supported as are the high end professional audio cards from Hammersmith and M-audio. This is by no means a complete list, just some examples.

Finally, there are the bazillion little usb things you can plug into you computer.  These are independent devices and many will change your sound configuration as the Sound Server finds them and adds them to its list, sometimes at the top making them the default, sometimes somewhere else. You need to check in your sound server to find them and set them up. Most of these should work out of the box because they are supposed to conform to usb standards but unfortunately some do not, especially older stuff and stuff that has gone through many revisions. 

If you just bought the latest greatest obscure thingamabob and it doesn't work, you need to realize that unless one of the other 15 people who bought it is a linux developer, or knows one, it probably be a little while before it is supported.

**dDrivers**
This brings us to the drivers, the software code in the kernel (the operating system) that provides low level services between the sound chip and the rest of the operating system which interfaces with software that is wanting to use these services. A driver is basically a translator, it translates commands and requests from the operating system to the sound chip and reports back the results. In order to do this, the driver must know the hardware intimately. it must know or be able to detect if the OEM has messed around with the firmware or hardware configuration which they do, continuously, even within models. If they have 10,000 cables on hand and the sound chip they were using runs out and they get ones that are configured entirely differently, they just reprogram the chip instead of tossing out all those cables. So the side speaker output on the new 7.1 surround chip becomes the headphone output which is what it was in the 5.1 configured chip they were using previously, which is the exact same Intel ICH8 chip on the exact same model of computer. Can you see the problem now?

This can become extremely difficult since OEMs are often very lax in publishing this information. So, for open source driver writers this is a big pain. They can write the driver to detect as many variations as they discover but in the end this often results in a guessing game. So, if you are having difficulty getting the driver for your particular sound chip configured, don't blame the driver writers, they are working as hard as they can, in the pitch black dark, with a flashlight, or maybe a candle. These days, it is the ALSA and OSS Teams that are the primary providers of sound drivers for Ubuntu/linux. You should thank these people as often as possible for taking on this almost impossible task.

** Sound Servers**
Sitting a level up from the drivers is Sound Server. The sound server provides kernel services to applications needing sound support. Not only does it provide driver services, but it also provides scheduling services and an interfacing scheme for other hardware and software the application calling it may desire. The sound server is what connects your application to your sound card or to a network, or not, depending on how you have it set up or misconfigured.

 ALSA and OSS, while providing drivers, also provide sound server services. For ALSA, many of the services are actually separate programs, like ESD, the Enlightened Sound Demon, which allows multiple applications to share sound services., or dmix, which is part of ALSA. These have been developed over the years in a haphazard sort of way to address percieved shortcomings in the ALSA sound server. OSS is an even older sound server that ALSA replaced but OSS is being revived, has been entirely rewritten and the current version, called OSS4 is slowly making inroads into the scheme again . Other sound servers like Portaudio, which Audacity was written for, and Coreaudio are mostly abandoned now. 

Pulseaudio is a fairly new entirely separate sound server that provide sound services using the ALSA drivers. It is a direct replacement for the ALSA sound server and all the ancillary parts, like ESD and dmix, that the ALSA sound server has accreted over the years. Pulseaudio also seeks to provide functions that were previously difficult to achieve in the ALSA sound server scheme, like network broadcasting and syncing multiple sound cards and controlling the individual volumes of applications at the sound server and a bunch of other stuff. There is also some rumors that Pulseaudio is now experimentally working with OSS4.1.

Jackd, Many people consider jackd, often just called jack, as a sound server but this belies its nature. Jack is not a sound server, jack is an audio connection kit. Jack was designed around one purpose, to provide services that applications for professionals in the music industry need from an operating system like real time priority kernel/cpu access and low level driver access to reduce latency and interruptions in time sensitive activities like live recording and performance. Jack's connection kit allows all the jack written applications to connect together and be operated together, from a keyboard, from a midi device, remotely or locally. Jack is a boon to musicians. Since jack utilizes so much low level control, it needs to be in charge of the resources it is using and will conflict with sound servers seeking to also use them. There are ways around this. The ALSA OSS and Pulseaudio sound servers have modules to interface with jack which allows them, and the applications using them, to work with jack.

Phonon is the new sound server and application API for KDE. It can work with Pulseaudio and the ALSA drivers. It currently uses the xine backend though gstreamer support is coming.

**Interfaces**
Unlike sound drivers, sound servers need a public face so users can interact with them and tell them of their desires. First, there is the all important System/Preferences/Sound. This is where you tell the system where to send the sound. You can direct the sound to a sound server, making the sound server the boss, or you can direct it to the hardware driver, making the sound server the servant. If you direct the sound to the hardware or to autodetect which is almost the same thing, the first application to get there will often shut out all the others. If you choose a sound server, the sound server will make that decision and you can have some control over that. ALSA will try to use ESD or dmix to share the sound and Pulseaudio will just do it itself. You can also make one sound server use another, like making Pulseaudio the default sound card for ALSA which will redirect all the ALSA applications to Pulseaudio. The applications don't care and don't know., this is beyond them, or should be.

For ALSA, interfaces include a pile of sound mixers you can get from the repos. The most basic is the alsamixer which is run from the terminal. There is also the alsamixer-gui and the gnome-alsamixer. Personally, I prefer the gnome-alsamixer.  In the sound mixer you will find a bunch of sliders and switches to control your sound card with. The layout and availability of switches is entirely determined by your sound card driver, which, if it is the wrong one or poorly written, can create all sorts of surprises. There is also the Volume Control, which is the little speaker icon in your top panel. The volume control may give you more options than the sound mixer, or less, it depends.... Also in the Volume Control you can choose the device you want to control with it. The other most used interface with ALSA is the asoundrc file which must be edited by hand though there is also the gui application asoundconf-gtk which lets you choose your default sound card so you can avoid hand editing for that at least.

Pulseaudio does not delve deeply into the sound drivers so the ALSA sound mixer is still used with Pulseaudio. While Pulseaudio can control the master volume, channel volumes, and the volume of applications, and inputs it has no direct control over all the inputs and outputs of the sound mixer. If these are muted, or not turned up or on, Pulseaudio can make no use of them.
Nevertheless, the Pulseaudio interfaces offer you a lot of control. In the Pulseaudio Volume Control (pavucontrol) you can view all your input and output devices and make any one the default device. You can also control the volume of any application and the device it uses without effecting the application's operation.  In Pulse Audio Preferences (paprefs) you can control network access to your sound devices, set up a multicast RTP server. You can also create  virtual devices that are treated exactly like the hardware devices. Much of this is really handy if you wish to direct your applications elsewhere than your sound card.

** Helpers/Backends**
Due to the many different formats that sound comes in these days and the many different sound servers etc used in the past, we end up with a myriad of filters, plugins, and wrappers so our applications can still work. To understand how these things work, you need to understand a little about how your user application goes about its business.  As an example let's use Amarok. When you want to play an mp3 Amarok looks at the file and says to itself, OK, I need some help here, let me look at my list of helpers...hey, I got this xine engine here to help me, he's got an mp3 plugin which will filter this mp3 file into something I can use. Hey xine can I use your mp3 plugin? xine says OK, here, use it, so then Amaok calls xine again and says hey, send this to the Pulseaudio sound server. So xine calls Pulseaudio and says hey, I got a stream from Amarok, can you play it? and pulseaudio says, sure, bring it on. So Amarok takes the file and runs it through the xine engine which converts it to pcm and sends the pcm stream to Pulseaudio who puts it in the Playback box and assigns it to the default Output Device which is an alsa driver that drives the sound device. If that device is your speakers or headphone, and the pcm is turned up in the alsa volume control you will be able to hear it. So it goes something like this Amarok-xine-pulseaudio-alsa driver-sound card-speakers.

Gstreamer also provides backend helper services to applications like xine does. Gstreamer and xine also provide video services, they are multimedia helper or filter applications with their own set of plugins and filters for the various sound servers and media formats. This is a more modular approach to things and is very appealing to application writers, they only need to write an interface with gstreamer or xine  and not worry about all the details. Gstreamer and xine also have their own default configurations which you can change.

There are also filters like the LADSPA plugin set that can change the audio itself, adding effects like delay or distortion or upmixing 2 channel sound to 5.1 surround sound output. I don't know much about that myself except for using them with jack but they can be used directly with the Pulseaudio and ALSA and OSS sound servers apparently.

Application developers also create their own plugins. Plugins for gstreamer and xine and alsa and oss and pulseaudio and jack are some common application plugins. Sound servers also come with plugins so they can appear compatible with applications that are looking for other sound servers or were written for other sound schemes or to plug in to or from services offered by other programs. Pulseaudio has plugin modules ALSA and OSS, another plugin for jack, one for libao. Pulseaudio calls them modules. ALSA has many of its plugins wrapped up in libasound2 and libasound2-plugins.  Plugins are very useful items. It is not a bad thing to have as many as you can get. They give you flexibility and widen your choices.

There are also wrappers. Wrappers are used when an application, which is expecting a certain scheme, needs to be used in a system using a different one. Many application developers provide plugins for this, but some do not, or the plugins they do provide for one sound server do not work correctly but another one does. To solve this dilemma, we can use wrappers.  The largest use of wrappers in sound is to get OSS applications or their OSS plugin to work with ALSA and Pulseaudio. These wrappers are called respectively, aoss and padsp. To invoke a wrapper, we simply open the applications with the wrapper command in front of it like this: 
```

padsp wine

```
And configure the application to use its oss plugin.

** Conclusion**
Well that is the basics of how the sound scheme around here seems to work as far as I can tell. Hopefully you are not so confused about it anymore.
But what do I do with all that? It is long on information but lacking in specifics. Well, the reason I decided to make this a separate thread is that my more specific guide linked below is getting very large but some sort of more general overview was definitely needed.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)


This is a first draft, subject to revision, constructive criticism welcome.:guitar:
Edit 01/27/09 Added preliminary Phonon info

---

### Post by Neobuntu on 2008-11-14
Oh Spit! That's complex as heck. You did a great job explaining it. Thank you very much!

My feeble brain interprets this as inserting "sound layers" (my thinking); for better level(s) of control and depending on what you need to do.

1. Driver must work with various sound chips AND designs even on the same sound chips. The driver part of ALSA (Thank you) handles this and has plugins for older OSS only programs(games etc..).

2. The next layer is about doing more than one sound (program) at once and dealing with their timing.

3. The "layer" (my word) after that could include networking the sound elsewhere; so that a "front-end" media CONTROLLING computer (MythTV etc) can get the media from where ever, and then optionally send the sound to a **different computer or media set top device** sound hardware.

4. Then you could also insert a layer for direct sound, as used by recording artist that require direct control for timing and such. This still allowing typical sound use.

Did I get it right? Seriously? Am I off or is that good? How would you change this simpler explanation?

I understand better now. I still just want sound to work and in these differing situations. I fear my running Kubuntu may (or may not) add complexities to setting this all up.

I'm going back at it (Pulse set up; without studdering and no OSS game sound, even with "padsp") again. Dive...dive!

Oh and intrepid (me now) should just work. Hardy should REALLY just work. I understand why it doesn't. I just hope a set of simple instructions, will be forthcoming and make it all work. 

There's too much clutter when Googling and Ubuntu forum searching for solutions! We need a better, central and wise way.

---

### Post by Neobuntu on 2008-11-14
Opps

---

### Post by markbuntu on 2008-11-14
Well, my 10,000 page guide has grown into a sort of clearing house for sound in Ubuntu. This thread is just a minor offshoot for people looking for an explanation. Actually, you are very close with your understanding but I see it as three basic layers, the low level sound drivers, the sound server (pulseaudio,jack) that is as a sort of traffic cop between the applications and the drivers and then the helpers like xine and gstreamer which act as interpreters for the various encoding schemes.

Pulseaudio is a low latency sound server that also provides networking services for applications along with connection services to low level drivers. jack is not really a full blown sound server but is especially designed for low latency access to the drivers for jack aware applications and their time critical needs in live recording and performing environments. 

Since jack and pulseaudio can be connected together, it is the best of both worlds. Low latency time critical funtionality for jack apps and a full blown sound server with network services for all applications.

As far as I can tell, Intrepid has made some progress but still, much of the needed functionality has been left out. It still takes some work to get everything dialed in.

Anyway, thanks for the post.

mark

---

### Post by refractal on 2008-12-25
markbuntu, 

this is a really beautifully written explanation of how sound works in linux. you made allusions to a 10,000 page guide... have you written more broadly in this manner about how linux functions? do you know of others who have? i would really love to find a comprehensive discussion of linux architecture at approximately this level of technical detail. do you have any suggestions? thank you again, and take good care!

---

### Post by ussndmac on 2009-01-04
Do the terms daemon and server refer to the same thing?

Can these words be used interchangeably when referring to the ALSA server or the Pulseaudio server?

---

### Post by markbuntu on 2009-01-05
What a daemon does is just sort of hang around until some application calls for a service it provides. Then it starts up the service and connects the application. There are usually a few daemons hanging around the system, daemons for I/O services, networking, and other services like sound.

As you can see, the Pulseaudio daemon does not constitute the whole sound server which includes the guis and ancillary programs and modules that the daemon cals on to perform the requested tasks. 

So no, strictly speaking the daemon is not the sound server and it would be a mistake and sow confusion to use these terms interchangably.

---

### Post by markbuntu on 2009-01-05
> **refractal said:**
> markbuntu, 

this is a really beautifully written explanation of how sound works in linux. you made allusions to a 10,000 page guide... have you written more broadly in this manner about how linux functions? do you know of others who have? i would really love to find a comprehensive discussion of linux architecture at approximately this level of technical detail. do you have any suggestions? thank you again, and take good care!

Thank you, 

The 10,000 page guide is here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

It does not really go into structural details, it is mostly a troubleshooting and setup guide. 

If you want more technical explanations you pretty much have to do some heavy digging in the wikis and the sites maintained by the orgs who provide the apps. 

While some are very good about explaining what their stuff does I could not find any good overview of the whole system which is why I wrote the OP. 

I am sure there is a better explanation than mine somewhere out there. There has to be. I have only been using linux since last April though I did play with it for a while but stopped about 10 years ago.

---

### Post by ussndmac on 2009-01-06
> **markbuntu said:**
> What a daemon does is just sort of hang around until some application calls for a service it provides. Then it starts up the service and connects the application. There are usually a few daemons hanging around the system, daemons for I/O services, networking, and other services like sound.

As you can see, the Pulseaudio daemon does not constitute the whole sound server which includes the guis and ancillary programs and modules that the daemon cals on to perform the requested tasks. 

So no, strictly speaking the daemon is not the sound server and it would be a mistake and sow confusion to use these terms interchangably.

So how would you describe a sound server?

So if Pulse is a daemon, what is ALSA? Are they redundant?

Is Jack a daemon or server? Are Pulse, ALSA, and/or Jack redundant?

Mac

---

### Post by markbuntu on 2009-01-06
Alsa is actually two parts, low level drivers and a sound server layer. 

The sound server is what provides connection services between the low level hardware drivers and the application. Since hardware drivers have moved or are moving into the kernel it is no longer desireable or appropriate to include higher level sound server functions so a separation is necessary. 

What many consider as the alsa sound server is a bunch of applications grafted onto the alsa api over the years which makes the whole scheme become somewhat messy and incoherent and makes appication development more difficult. Pulseaudio is a attempt to bring some order and sanity to this by replacing all these disaprate functions with a single coherent sound server and a simple api written from the ground up.

Jack is not a sound server since it is not intended to provide sound services to all applications. Jack runs as a daemon.

ALSA still provides the low level drivers and pulseaudio provides functionality that was difficult to impossible with the alsa sound server. Jack serves the professional audio production community so no, they are not redundant, they are complementary.

---

### Post by chkneater on 2009-01-29
Hi, your FAQ was really well written.  I followed it step by step even tho my audio playback was fine.  I was missing on lib tho.  Anyways I need help getting Audacity to record for me again.  Ever since switching to 8.1 I have not been able to record at all.  I've tried every possible setting in the sound menu and tried both front an back inputs.  Any help would be apprectiated

---

### Post by ((( ~ ))) on 2012-02-02
Hi,

Is the info posted in the original post still relevant and current? If not, could someone please direct me to a more recent (perhaps more detailed) guide?

...or explain the differences between this guide and the current situation of audio in Ubuntu? ;-)

---


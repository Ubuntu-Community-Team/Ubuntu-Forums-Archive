---
title: "This sound application is so confusing"
date: 2006-03-09
forum: Multimedia &amp; Video
---

### Post by Sidney_the_n00b on 2006-03-09
Well, I've been working on installing ubuntu for a few days, I've sort of got the hang of it. I've been trying to install OSS sound (to get doom 3's sound to work.) It stated that I need to install four packets to install OSS. The packets are

Kernal-source
GCC
binutils
make

I've install the last three (I found them on the install CD I had), but I can't find the first anywhere.

I tried installing OSS again, and it still says that I need all four packets.

Anyone have any idea? Thanks for the help

-The n00b

---

### Post by mpvano on 2006-03-10
Don't go any farther! You are following bogus instructions.

You should NOT need to build and install OSS drivers. The correct versions are already built and installed in breezy.

In addition, virtually all OSS programs work just fine with the OSS emulation support that is part of the ALSA drivers.

However, If you REALLY think you know what you are doing and feel that you MUST break and remove all the audio support in your present ubuntu system (Since that's what you plan to do), then ignore this warning and proceed.

The make program is part of the "build-essential" package and you will need to install that.

Note also that you cannot build kernel modules (like the OSS modules) with the GCC version that is installed when you use the gcc package. You MUST download GCC 3.4 from the ubuntu repositories and know how to switch back and forth between compilers as needed.

The generic build and install instructions supplied with source tar bundles like alsa are for people building and installing the software into their own kernel builds - NOT for users of distributions like Fedoray, SUSE and Ubuntu.

Again, I strongly advise you NOT to proceed with what you are doing. It will break your system and you will probably not be able to fix it without a complete re-installation.

Mario

---

### Post by Sidney_the_n00b on 2006-03-10
Thanks for the help Mario, I've already screwed up, but reinstalling isn't to big a deal (soooo much faster than installing windows). I hope I can find some way to get it to work. :)

---

### Post by mpvano on 2006-03-11
Sorry I was so negative....

The difference between using OSS and ALSA in Ubuntu is all in the startup of the system. Unfortunately that's fairly complicated to explain, but basically BOTH sets of drivers are built and present in the modules libraries. In the standard system, the alsa drivers are loaded in response to the installed hardware during the bootup process.

To use the OSS modules you need to prevent the alsa modules from loading, and force your selection of OSS modules to load with the correct parameters.

I'm not aware of any scripting support for doing that, so I think you'll need to come up with your own way to do that.

If you're just experimenting, you may be able to manually unload all the alsa modules (the ones starting with "snd") and then use the correct manual modprobe commands to load your desired drivers. Once you have this working, you need to write init scripts to do that and install them.

The question remains, however - Why exactly are you trying to do this? As I said, 99.9% of all OSS applications run unmodified under ALSA's built in OSS support.

If your sound is not working the way you think it should, it's more probable that you have misunderstood how it's configured. In particular, OSS (and ALSA) programs rarely work properly under the kde or gnome window managers unless you disable the "sound daemons" installed by those managers to allow them to make UI sounds while other applications play sound. These are called the ESOUND system under gnome, and ARTS under KDE. Unfortunately these "sound daemons" rarely work properly and break nearly all OSS applications.

There's a control panel in your "system:Preferences" menus to switch them off. If you also disable the UI sound generation in gnome/kde and are careful not to run any applications that reload ESOUND or ARTS, then OSS and alsa applications work fine. If you don't do this, they hang up mysteriously, or work sometimes but not other times because the sound daemon program has opened the sound device and locked it, preventing other access.

This, or other problems with the loading of the built in OSS emulation, or it's mixer settings are almost certainly your problem.

By the way, most modern releases use the 2.6 series kernels, which generally incorporates the ALSA drivers and their OSS emulation instead of the obsolete and no longer maintained OSS drivers. Ubuntu is not unique in that respect. Any application today that requires you to use OSS drivers is probably too obsolete to work for other reasons.

hope this information helps - if not, please tell us all what kind of machine you have, what kind of sound card, and what problem you are tryig to fix. I'm sure someone here can point you to a solution.

You might also take a look at the Ubuntu wiki - it has a great deal of information about solving hardware configuration problems. Whatever problem you are trying to solve has probably already been faced by someone before.

Mario

---

### Post by mpvano on 2006-03-11
Here's some more info for you.

I did some poking around in the ubuntu documentation directory and found the details of how to switch drivers (if you really must).

Almost all debian and ubuntu packages install SOME sort of documentation into /usr/share/doc/ in a folder with the same name as the package.

Take a look at /usr/share/doc/linux-sound-base/README.Debian for instructions on switching back and forth between supported ALSA and OSS drivers.

Basically, all you need to do is blacklist the specific ALSA drivers for your card and the OSS sound system will be used instead.

hope this helps (once you get things back together),

Mario

---

### Post by Sidney_the_n00b on 2006-03-12
Thanks for all your help Mario, It makes sense that the sound is messed up, 'cause I've been running it in gnome, but I'm pretty sure I know how to disable gnome and just run it from the command prompt.

---

### Post by McQuaid on 2006-03-15
As the other poster said, don't install oss.  In the rarest of circumstances could a need arise for native oss support, and doom3 shouldn't be one of them.

Sound, initially can be confusing on linux.  I'm no expert, but I'll give you the basics.  Way back when, there was basically one way to have sound on linux, OSS. Think of it like a unified driver set for all sound cards. Even with the name (OPEN sound system) the company making them started making a closed pay for version that supported more cards.  Not sure if alsa was already in development but people embraced it being gpl and it's now become the defacto standard for sound. And I've never directly compared, but it strived too exceed oss, oss having some limitations.

You never mentioned if you actually have sound in other apps, but I'll assume you do and that your alsa is probably working fine.

What's probably giving you issue is not a sound driver problem (oss vs alsa), but what's called a sound daemon.  This is something that's running in the background and intercepts all sound calls and plays them through it's sound server.  There are basically two main ones, esd and arts.  Esd is what gnome uses and I'll assume thats what you are using.  Esd is so you can have all your system sounds and theoretically, have all your apps have sound.  This can help with some older/onboard sound cards do not have whats called hardware mixing.  Hardware mixing has the ability to allow more than one app to have access to the soundcard.  For cards that don't, you 'mix' all the sounds together in software (via esd) so you can have multiple sounds.

But sound daemons can be a pain in the arse.  When you use esd you have to make sure esd is supported by your apps.  All the popular ones are: mplayer,xmms, bmp, any gstreamer app, but some aren't and doom3 is one of them.

So first thing is, shut down esd.  Now you won't have system sounds doing this, but ignore that for now.
Go to System-->Preferences-->Sound

Then uncheck enable sound server startup.  It shound stop it there but logout/login of gnome to make sure.

Just to mention.  All previous id games used oss and wouldn't play nice with mixing so ET, q3 would (potentially, not all cards)lock out your sound card to any other apps.  Doom3 is the first id game with native alsa support which is a good thing.

Now, launch doom3.  Sound? Great. No?  Ok, we'll try some other things.  Now even though with alsa you don't actually have oss installed, alsa has oss emulation.  This is for older applications that do not have native alsa support.  So try launching doom3 using oss emulation.
doom3 +set s_driver oss

Sound? Cool, you can stop there and enjoy but personally I'd prefer any app that has alsa support to use it so it doesn't hog my card.  Alsa has something similar to a sound daemon called dmix.  Basically it will mix sounds for you.  Sometimes it works great, sometimes not.  It can have issues with rate conversion.  A lot of onboard soundcards only handle one native rate 48000hz.  But lots of music,games etc is at 44100hz.  If the card can't natively support it, it gets upsampled in software and sometimes with varying results.  First off, make sure your updated with doom3 as they addressed the rate issues.  

I don't know if you've ever poked around in the preferences of any of your sound apps but for example in xmms, if you have it set up with alsa and choose properties it usually defaults to 'default'.  'Default' will attempt to use dmix automatically and allow alsa aware apps to share your card.  But again, because of rate issues etc, this can cause problems.  So most apps will allow you to select hw:0 for alsa instead of default.  I'd recommend you first try default then hw:0.

Hopefully some of these suggestions will give you sound in doom3.

On a side note I read here before:
[http://zerowing.idsoftware.com/linux/doom/]("http://zerowing.idsoftware.com/linux/doom/")

That idsoftware recommends that if alsa fails ditch it and go with oss.  I was kind of surprised to see that.  

> OSS is not an outdated and deprecated sound API. It turns out to be much easier to setup and operate than Alsa for a lot of people.

Interesting to see that from them, even though they hold a minority opinion.  I actually went to the oss site as a result and noticed that it's free for personal use although you have to update every 4 months.

I'm curious if anyone here actually went through the hassle and installed oss.  I'm only curious because my card only supports 48000 natively, and while 44100 do not sound too bad, there is skipping with 8000hz samples which I've been using with voip.  I'm curious if oss handles sample rate conversion better.  I'll probably start another thread on that though.

---


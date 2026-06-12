---
title: "Dssi-Vst"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by damu on 2006-07-21
Hi,

I just installed on my Ubuntu most of the softwares that I already use for audio prod (with a dedicated distro for audio prod). Quite impressed that it just works too with my RME Hammerfall. :) I didn't patch the kernel as I don't feel experimented enough to do this.

But I would really like to be able to use my VSTs. I installed all the DSSI stuff that I could find in synaptic, and googled to find a .deb of dssi-vst. I found only one. Unfortunatelly, when I tried to install it , there was a dependancy issue with a lib. I have the version .100 and the deb needs the version 0.80...I read somewhere that it would create a mess to downgrade this lib so I gave up. Read the "how to" on the dssi page...looks a bit like chinese to me :-k  ...could anyone help me on this one? 

Thanks,

---

### Post by metasymbol on 2006-07-24
You need a current build of dssi-vst which fullfill every single depency of the libaries. I don't know why there is no newer build, because it is no problem to distribute dssi-vst as binary - because of the lesser gpl. (dssi-vst need the propritary c headers from the steinberg vst-sdk).

maybe you should write a nice mail to your deb-build maintainer ;)

---

### Post by Cybolic on 2006-07-28
I've attached a checkinstall build of dssi-vst 0.4 here:

[http://www.ubuntuforums.org/showpost.php?p=1310545&postcount=13](http://www.ubuntuforums.org/showpost.php?p=1310545&postcount=13)

---

### Post by drycellbattery on 2006-08-01
Does dssi-vst only work with vsti instruments? I'm guessing it does as dssi is an instrument plugin api. What about for using vst effects?

---

### Post by Sheik Yerbouti on 2006-08-01
It only works for vsti instruments but it's not a big deal because there are ton of LADSPA effect plugins and some are quite good.

---

### Post by drycellbattery on 2006-08-01
The vst effects I'm fond of are the fish fillets, and there's some delays and distortions I like. So far I tried some delays, distortion, and gverb. The delays only produced some crackle and I couldn't get any decent sound from them :( . I was using amsynth hooked up to a jack-rack. I'll start another thread on this soon.

---

### Post by dburgan on 2007-02-08
> **Sheik Yerbouti said:**
> It only works for vsti instruments but it's not a big deal because there are ton of LADSPA effect plugins and some are quite good.

Sorry, but the best LADSPA plugins don't hold a candle to the quality of the algorithms available in the VST world, and that's just a fact.

I know that VST is hobbled by the proprietary nature of Steinberg's license, but the reality is that pro audio on Linux will not ever happen until these high end VST plugins become available to mere mortals under Linux.  Whether that means they are ported from VST to DSSI or whatever doesn't really matter to me.  But pretending that LADSPA can stand up to stuff like the Voxengo plugins, or the Waves Native plugins, or DSSI to any of the excellent soft synths from companies like GMedia, Arturia, Native Instruments, etc. ... well, this is why Linux has not caught on in pro audio circles yet.

OSX has a big following because these companies support it.  Until these companies support Linux or until the Linux world figures out how to reliably run these plugins in an emulation layer, Linux pro audio will remain a backwater.  Which sucks, because I desperately want to get rid of Windoze from my computer, but there it is.

---

### Post by eric71 on 2007-02-09
Using the DSSI-VST package linked above, I'm able to use both VSTi and VST effects in Rosegarden.  Works pretty well, but for some reason the interface of the VST will only load once.  After I close it and want to open it again, it won't. Otherwise, everything I've tried works well. The native (non Windows) interface is usually enough, but to get to presets, etc. it is nice to have the full graphical interface.  Don't know if it is a wine problem, or what.

---

### Post by joshsherman on 2007-05-12
> **eric71 said:**
> but for some reason the interface of the VST will only load once

If you click "Editor" under the plugin slot, it should bring up what's called the "native editor" which is the originally intended VST interface.  Also, you can the VST slot, and from the window with all the mapped settings, you can click "Editor >>" and pull up the same thing.

I will also mention that I've noticed it can have considerable lag when pulling up the native editor, it's either just my system, or it's a wine thing.

Hope that helps.

-j

---

### Post by GinoCyber on 2008-01-11
The above link works for intel32 but is there one that will install on an AMD64?

---


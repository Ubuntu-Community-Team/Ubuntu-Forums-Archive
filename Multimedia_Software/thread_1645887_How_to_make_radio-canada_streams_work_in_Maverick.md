---
title: "How to make radio-canada streams work in Maverick?"
date: 2010-12-15
forum: Multimedia Software
---

### Post by geoffm on 2010-12-15
This is an eternal problem with [radio-canada streaming content]("http://www.radio-canada.ca/emissions/infoman/saison11/blogue.asp"), and it seems every new version of ubuntu we have to go through different processes to get it to work.

In some previous versions, following the [guidelines provided by radio-canada]("http://www.radio-canada.ca/apropos/aide/pdf/Linuxconsolevideo.pdf") worked, but they are quite outdated now and some of the packages they refered to do not even exist anymore. I make regular reports of their website, but users complaining only end up by, if they answer at all, "it works on our computers so it should work on yours" or "why don't you use windows".

Basically, their guides consist of removing the totem totem plugin, installing flash-plugin-nonfree and the mplayer plugin.
I read somewhere the mplayer plugin is now gecko-mediaplayer, which I installed, but the videos still don't work.

Anyone has a solution?

---

### Post by qamelian on 2010-12-15
I haven't done anything other than install the flash plugin from the repos and it works fine on my laptop. Right now, I'm listening to Espace Musique. 

What exactly happens when you try to play a stream from this site?

---

### Post by geoffm on 2010-12-15
The advertisement plays and then the video screen stays black. I'm surprised that yours worked out of the box, it never happened to me. Can you tell me which video plugin you are using (totem? mplayer? vlc?) and which flash plugin, and if you might have something else installed that makes it work?
I think I have tried them all, though...

---

### Post by qamelian on 2010-12-15
Totem plugin and flashplayer as installed from the flashplayer-installer package in the Ubuntu repos. Any other codecs that may be installed are only as a result of Totem telling me that one was missing and installing it for me. I never use the medibuntu repo, nor do I install ubuntu-restricted-extras. This way I end up with only the stuff I actually need. Less excess baggage = easier troubleshooting, in the rare case where I run into trouble. :)

---

### Post by gdiloren on 2011-01-09
> **qamelian said:**
> I haven't done anything other than install the flash plugin from the repos and it works fine on my laptop. Right now, I'm listening to Espace Musique. 

What exactly happens when you try to play a stream from this site?
No, no! Problem is with live video streaming, working with Windows but not with Linux. RAI-TV just upgraded and we can watch the News on Linux. Some News on French France-1 and 2 and 3 are also unavailable to linux OS. If you try RDI on Google on R-C web site, well their live streaming is unaccessible with Ubuntu. I emailed them 4-8  weeks ago but so far no progress or change, no word!!!:confused:

---

### Post by gdiloren on 2011-01-09
CBC/Radio-Canada is not Linux Friendly. That's the whole Truth !!!     :(

---


---
title: "Ubuntu studio OS?"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by joshier on 2006-08-13
Hey

I think this is a brilliant idea.

When will this ever be configured for a standard OS instillation disk?.. like, kubuntu and so on?

---

### Post by dolson on 2006-08-13
Answer: Never. Although this has been answered many times, people still ask, so I'll say it again.

Ubuntu Studio is a wiki only, and any work I do on packaging goes directly back into Ubuntu proper.

That said, talks are under way between several parties for a multimedia-oriented derivative of Ubuntu. This is independant of the Ubuntu Studio wiki.

---

### Post by pneaveill on 2006-08-14
How do we get in touch with them?  I would like to know what they have devised as far as VST and other techie toys. So far, all I have found is crap on linux. If there is something out there that really works as OS, then please let me know.

---

### Post by dolson on 2006-08-14
You should try windows if all you are after are windows libraries and programs.

Otherwise, be patient, compile software that doesn't exist in your OS yet, or help out by learning how to package software and contribute it to Ubuntu.

---

### Post by pneaveill on 2006-08-14
> **dolson said:**
> You should try windows if all you are after are windows libraries and programs.

Otherwise, be patient, compile software that doesn't exist in your OS yet, or help out by learning how to package software and contribute it to Ubuntu.
Was not intending to be rude previously. Just frustrated and nursing a migraine.  M$: been there, done that, not going back.

What I want to do is to run the VST (and other toys). However, if there is something in linux, I would gladly be made aware.

---

### Post by edev on 2006-08-14
> So far, all I have found is crap on linux. If there is something out there that really works as OS, then please let me know.

I run a professionnal studio with 2 Ubuntu Dapper boxes. I've done recording, mixing and mastering with musicians that only knew about Pro Tools... They are totaly amazed by the quality of the softwares/pluggins that's in the boxes. If you have only found crap, you haven't search very much...

Eric,

---

### Post by 23meg on 2006-08-14
> **pneaveill said:**
> So far, all I have found is crap on linux. If there is something out there that really works as OS, then please let me know.

[http://www.ferventsoftware.com/](http://www.ferventsoftware.com/)
[http://www.musix.org.ar/](http://www.musix.org.ar/)
[http://dynebolic.org/](http://dynebolic.org/)
[http://www.linux-sound.org](http://www.linux-sound.org)

---

### Post by dolson on 2006-08-15
FST is one that I hear a lot about. The entire point of it is to run VST files. Same with the dssi-vst application. And others... Indeed, you can find this info anywhere on Google.

Keep in mind what I said. If you want Windows software, you best run it in Windows*. VST files are Windows programs, and so all Linux solutions are based off of Wine, and we all know how crappy Wine is. So don't expect miracles...

* - this is not me being a dick, this is me being serious. I don't run Windows, but I also don't download or buy Windows software. If I did, however, I would run it under Windows because regardless of what anyone says, Windows has been improving in terms of stability lately, and you aren't going to find a better platform for running software designed specifically with that platform in mind. Seriously. Wine is a great first step towards companies never having to even think about Linux users, and Linux users relying on Windows applications instead of Linux applications... But it is currently not very good, especially, I would say, WRT audio applications.

---

### Post by floogy on 2006-08-15
Try LADSPA or LASH instead, or enable your VST plugins by wine.

EDIT: I thought, [LASH ]("http://savannah.nongnu.org/projects/lash")is a replacement for [LADSPA]("http://en.wikipedia.org/wiki/LADSPA"), but it isn't it's a replacement/renaming of [LADCCA]("http://savannah.nongnu.org/projects/ladcca/"), but it's also part of an pro studio like LADSPA is. Maybe I meant [LV2]("http://lv2plug.in/") instead.

[1][LADCCA/LASH Mini Howto]("http://tapas.affenbande.org/?page_id=31")
[2] [LADCCA at agnula.org]("http://www.agnula.org/packages/ladcca/")

---

### Post by pneaveill on 2006-08-15
Appreciate the help with all this. What probably happened is that I setup a series of things incorrectly and got impatient with myself.

These migraines/ mini sizures mess with my thinking and all that. ANyway, not just looking at running the VSTs, but more importantly wanting a small studio that is running from my computer. This is all I am really asking for. Sorry for any miscommunications.

---

### Post by dolson on 2006-08-17
Just a word about LV2... This is news to me. I thought that the Linux world was migrating towards DSSI as the new replacement for LADSPA.

And I really really hope Debian (and thereby Ubuntu as well) update from LADCCA to LASH. I really wish that people would stop renaming applications too.

I have a lot of wishes.

---

### Post by pneaveill on 2006-08-18
> **pneaveill said:**
> Appreciate the help with all this. What probably happened is that I setup a series of things incorrectly and got impatient with myself.

These migraines/ mini sizures mess with my thinking and all that. ANyway, not just looking at running the VSTs, but more importantly wanting a small studio that is running from my computer. This is all I am really asking for. Sorry for any miscommunications.
Update: not sure how to explain this but physically removed the card and replaced it with another one. COmputer found it right away and couple of reboots and such later, I am enjoying a CD.

Is it supposed to be that easy?

---

### Post by metasymbol on 2006-08-19
> **dolson said:**
> I thought that the Linux world was migrating towards DSSI as the new replacement for LADSPA.


LADSPA is the name for FX plugins (similar to VSTfx)
DSSI is the name for instrument plugins (similar to VSTi)

But the aceptance of DSSI for the developers is not very high, so only 6 DSSI instruments available, but hundreds of VST plugins.

---

### Post by dolson on 2006-08-19
No kidding. DSSI is for Linux, and VST is for Windows. Of course it's going to be lopsided. Acceptance of DSSI amongst Linux developers (ie: the people to whom this matters) is pretty near 100%.

---

### Post by floogy on 2006-08-19
Don't forget to mention since when both, VSTi and DSSI, were invented...

---

### Post by dolson on 2006-09-11
As an update to this thread:

LASH is in both Debian and Ubuntu Edgy. Yay!

FST is in Debian. Not sure if it'll install in Edgy. I will install Edgy later today after work and see if it will. I'd rather not compile it myself, just because of the SDK garbage that Steinberg makes us go through.

Anyhow, yeah. Thought someone might like to know.

---

### Post by pneaveill on 2006-09-11
> **dolson said:**
> As an update to this thread:

LASH is in both Debian and Ubuntu Edgy. Yay!

FST is in Debian. Not sure if it'll install in Edgy. I will install Edgy later today after work and see if it will. I'd rather not compile it myself, just because of the SDK garbage that Steinberg makes us go through.

Anyhow, yeah. Thought someone might like to know.

Appreciate the work on this. Please keep us informed what we need to do.
Paul

---


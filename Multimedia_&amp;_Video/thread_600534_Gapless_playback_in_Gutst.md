---
title: "Gapless playback in Gutst"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by ivanhelguera on 2007-11-02
Hello,
I badly need gapless playback. in Amarok or another application that offers reasonable library options. I understand it's been made available with the new version of the gstreamer engine. Amarok uses xine. 
I can't get it to work. Amarok offers crossfading, but 400 ms is the minimum value. No crossfading gives gaps. I have LAME created mp3. 
Of course, foobar or winamp under wine would be a solution. 
BTW, what about flac/cue support?
IH

---

### Post by VCSkier on 2007-11-02
I've been asking these same 2 questions for almost 2 years...  progress is being made, but its really slow.  For a while there was a subforum on hydrogenaudio.org for linux users, but it was cut off pretty quick for lack of activity (see my signature).

I got in touch briefly of the developer of [soundKonverter]("http://www.kde-apps.org/content/show.php?content=29024") and he says that he wants to implement the ability to split flac images based on cue sheets, and then transcode them, but that "it will take some time."  K3B can rip cd's to this format, but at this point, there's not much you can do with them.

Once these two features come into line, I think we will find many more audio enthusiast windows users (namely those on hydrogenaudio.org) ditching microsoft altogether and becoming linux users.  *then* the development of these audio tools will pick up, because there will be more interest...

So stay vocal!  Keep asking questions, and when possible, pursue developers to work on these things.  Don't give up, the functionality we want will come eventually.

---

### Post by ivanhelguera on 2007-11-04
The good news is that foobar 2000 works quite well under wine. This solves most problems. 
It's quite sad, though, that the audio apps lack those options. This shows that the open source world still has a long way to go in terms of satisfying more refined needs of the users. Gapless playback etc. is just an example, something I happened to care aboout, but I imagine the situation may well be similar in other domains.

---

### Post by Eddy5 on 2007-11-12
I'm sure RhythmBox does gapless. Well it did with an MP£ mix album I have. Well chuffed. I think I had to enable cross fading and set the overlap to zero. Can't check at the moment as I'm at work. Also not tested with FLACs or Oggs, but I'm sure it would work with those too.

---

### Post by WebDrake on 2007-11-13
If it's for CDs, KsCD will do the job, although it has a rotten habit of skipping occasionally during digital playback, which I've never been able to resolve; advice welcome.  Typical that when one problem is solved, another appears....

---

### Post by mcduck on 2007-11-13
MPD supports gapless playback as well. And has _excellent_ library, way faster with large music collection than any other player I've used on any platform.

I'm pretty sure that there are many other apps supporting this, but it's been a while since I've used anything else than MPD so I can't remember which ones supported it and which ones didn't.

---

### Post by WebDrake on 2007-11-13
Can you recommend a client for MPD?

---

### Post by mcduck on 2007-11-13
> **WebDrake said:**
> Can you recommend a client for MPD?

I really like Sonata. You can get the latest version from here: [http://www.getdeb.net/app.php?name=Sonata]("http://www.getdeb.net/app.php?name=Sonata")

And of course ncmpc if you want a client that you can use from command line and control fully with a keyboard.

---

### Post by logos34 on 2007-11-13
You might consider Audacious with crossfader-plugin...there's a gapless tab/option you can enable independently of crossfade.  Amarok and Audacious are my two favs--the latter is a great all-round lightweight player.  I have some .alac (apple lossless) problem files--not live music but symphonies--and there's a pop between tracks/movements on playback in Amarok (xine) and audacious and every other player.  VLC is the only player other than audacious that plays it back perfectly.  The problem disappears when I convert .alac to flac with dBpoweramp or foobar.

---

### Post by WebDrake on 2007-11-15
> **logos34 said:**
> You might consider Audacious with crossfader-plugin...there's a gapless tab/option you can enable independently of crossfade.  Amarok and Audacious are my two favs--the latter is a great all-round lightweight player.  I have some .alac (apple lossless) problem files--not live music but symphonies--and there's a pop between tracks/movements on playback in Amarok (xine) and audacious and every other player.  VLC is the only player other than audacious that plays it back perfectly.  The problem disappears when I convert .alac to flac with dBpoweramp or foobar.

I've tried it but couldn't find the crossfading tab/plugin: I installed audacious-crossfade or whatever the package is, but nothing related to it showed up in the Preferences.

Could you advise?  I must say I did like the look of it as a player.

---

### Post by logos34 on 2007-11-15
> **WebDrake said:**
> I've tried it but couldn't find the crossfading tab/plugin: I installed audacious-crossfade or whatever the package is, but nothing related to it showed up in the Preferences.

Could you advise?  I must say I did like the look of it as a player.

Preferences>audio>current outputplugin>select 'crossfade plugin

Output plugin preferences>audio output=Alsa

>Gap killer tab>enable


you're basically just piping the sound through the crossfade plugin filter and back out through Alsa

---

### Post by logos34 on 2007-11-15
you can make audacious[ look even better]("http://www.gnome-look.org/content/show.php/Almond+%28VUmeter+skin+added%29?content=41102&PHPSESSID=f66d43e8e089e86f75358dee86f469af") with these skins:

almond 
vortigo
kore 
digiblue
etc, etc
and good 'ol ultrafina2000 (still my fav if only because of the crisp bright helvetica font LED text)

at least those are my favs

---

### Post by WebDrake on 2007-11-16
> **logos34 said:**
> Preferences>audio>current outputplugin>select 'crossfade plugin

Output plugin preferences>audio output=Alsa

>Gap killer tab>enable


you're basically just piping the sound through the crossfade plugin filter and back out through Alsa

Oh, fantastic!  Finally, gapless playback!  Thank you very much.

As far as the gap killer goes, how does that work .... ?  I'm sure I have CDs where there are deliberate long gaps, and I *wouldn't* want to kill those.  I just want there to be no gaps where there *shouldn't* be ....

(Solve one problem, create another .... :-) )

---

### Post by WebDrake on 2007-11-16
> **WebDrake said:**
> As far as the gap killer goes, how does that work .... ?  I'm sure I have CDs where there are deliberate long gaps, and I *wouldn't* want to kill those.  I just want there to be no gaps where there *shouldn't* be ....

Hmm, seems on my system at least that there is no need for the gap killer if the crossfading details are set right (i.e. to 0).

---

### Post by logos34 on 2007-11-16
yeah, if you hover your cursor over it, and you get this pop-up:

> None (gapless/off): Gapless mode. Keeps the device open, but does not do any fading.

so I guess for true gapless you may want to set the crossfade to 'None (gapless/off)' and untick the 'enable' box in the Gap killer tab...the latter seems to just mask any pops or discontinuities in the transition between tracks so you don't notice them.

You'll have to experiment with different settings, but that plugin is the best I've seen yet. (that said there may be something better out there for another media player I'm unaware of).

---


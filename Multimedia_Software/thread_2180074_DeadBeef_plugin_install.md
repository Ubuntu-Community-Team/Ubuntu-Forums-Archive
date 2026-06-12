---
title: "DeadBeef plugin install?"
date: 2013-10-11
forum: Multimedia Software
---

### Post by Rob Sayer on 2013-10-11
I've installed deadbeef because it has direct to soundcard capability (Ie. hopefully avoid resampling).

However, it doesn't have file tree based playlist support without a plugin.  This is essential to me.

Tried make/install the fp plugin.  Copied all to /usr/lib/deadbeef/.  No joy ... it does not appear on the plugin list.

I generally stick to canonical ppa software, so I'm a bit weak with this stuff.  And, as usual, all the docs I've found on installing deadbeef plugins are pretty much written assuming you already know how to to it.

Can anyone point me towards a more understandable guide?

I am getting tired of dealing with the lack of control of linux audio resampling and am *this close* to using the windows version of vlc under wine or vbox.

---

### Post by tgalati4 on 2013-10-11
Perhaps describe your resampling problem in more detail so that we understand what you are trying to achieve.  For a file tree and minimal processing, install *moc* and play with *mocp*.

---

### Post by Rob Sayer on 2013-10-11
Well, from what I can see, I can get pulseaudio to default to 44.1k but not ALSA, and pulse will just output to alsa, which defaults to 48Khz..

The vast majority of my audio files are 44.1KHz.  I do not want these resampled.

Video file audio streams are almost always 48KHz.  If those were resampled to 44.1 and the audio files left alone I'd actually be happy.  I don't care that much about the audio quality of video files, but for music, yes.

Frankly, alsa configuration *stinks*.

I don't have any idea what moc and mocp are, but I'll look them up.

Thanks for the response.

---

### Post by Yellow Pasque on 2013-10-11
What kind of sound card do you have? If you output directly to the sound device (e.g. hw:0,1), then you should get what you want (you may need to add your user to audio group in /etc/group). Of course, you can only get one sound stream at a time that way unless your card has a hardware mixer. A good test:
```
speaker-test -c 2 -r 44100 hw:0,0
```
^Modify hw:0,0 appropriately..

---

### Post by tgalati4 on 2013-10-11
Most sound cards will auto adjust otherwise you would hear pitch differences between 44.1 and 48kHz.  If the music sounds OK, then I wouldn't worry about it.  Music will only get resampled if you have a music server and you set up a transcription service that translates on-the-fly.  Otherwise music files get sent directly to the hardware as PCM (straight digital stream) after being decoded (mp3, ogg, etc).

Install *audacity* and use the tone generator and record 5 seconds of a 1000 kHz test tone at different rates 44.1, 48, 96, 192 kHz.  Then play each one back.  They should all sound the same.  If they don't then you have a rate problem, otherwise you don't and I wouldn't worry about it.

I'm not convinced (yet) this is a real problem.

---

### Post by Rob Sayer on 2013-10-12
Lots of good responses here.  Thanks.  I use audacity but haven't tried that trick.

Actually, last night I was playing with deadbeef's output directly to sound card options.  There's one option that does so with no software processing.

Sorry if I'm not explaining this well, but I'm sitting in a cafe right now on a different machine that I haven't installed deadbeef on.

Plus deadbeef  has an option to output to alsa w/o sample rate conversion, and to reset alsa at program exit.

I'm pretty convinced so far it sound better that way.  Haven't a/b'ed it with really good recordings yet but I'm optimistic.  I'm dead set against resampling audio.  It's why serious audio geeks running windows use ASIO/wasapi drivers.

Now I'll try some of the above suggestions, and hopefully get that dang deadbeef file tree plugin to work.

---

### Post by Rob Sayer on 2013-10-12
Haven't tried any of the above suggestions yet, but I'm now trying to install the file tree plugin.  With no success.  Tried the tar/makefile approach.  No good.  I may have been doing something wrong.

Tried d/ling the version with the .so file zipped, copied it to /usr/lib/deadbeef/.  No good either.

When I go into edit/preferences/plugins, there is no file tree plugin in the list.

This is extremely frustrating.  There is apparently zero developer support ... no forum, contact, docs ... though there IS a link for donations.  If it didn't sound as good as it does I wouldn't waste a minute on it.

Are there any users here experienced with this?

---

### Post by Yellow Pasque on 2013-10-12
When deadbeef changes its plugin API, the plugin needs updated, but deadbeef devs don't update third-party plugins. You either have to prod the original author to do it or do it yourself (or find someone sympathetic and knowledgeable enough to do it for you). It's something that happens with all media players...

I personally use Audacious and send audio directly to my soundcard device (I run Debian sid with no pulesaudio and I'm lucky enough to have a sound card with a hardware mixer). I don't hear a difference with deadbeef, but I consider myself a pseudo-audophile at best.

---

### Post by shantiq on 2013-10-12
Rob Deadbeef is a great player but the sound is nowhere near crystalline    treat yourself and install [xmms]("http://ubuntuforums.org/showthread.php?t=1525072") if you like great sound     or Audacious with crystallizer plugin    but xmms even better thn that

---

### Post by Rob Sayer on 2013-10-12
Thanks for the response.

I realize that 3rd party plugins aren't supported by the program devs.  That's why I wouldn't use foorbar2000 in windows ... most features you'd want in foobar are 3rd party.

The way I organize my music library, I absolutely have to have a file tree browser.  So audacious is out most of the time.  But it is extremely fast loading, so I use it as default for individual files.

---

### Post by shantiq on 2013-10-12
ok so maybe try [moc]("http://ubuntuforums.org/showthread.php?t=2033852&highlight=moc+shantiq") as suggested earlier by [[COLOR=#000000]tgalati4[/COLOR]]("http://ubuntuforums.org/member.php?u=241895")[COLOR=#000000]   great sound and all the library tricks you wish for

**PS **[SIZE=1]and you may know this but foobar works perfectly under Wine

see foobar on 13.04


[/SIZE][/COLOR][ATTACH=CONFIG]246891[/ATTACH]

---

### Post by Yellow Pasque on 2013-10-12
I also like clementine with gstreamer-delta plugin (similar to Audacious crystallizer). [https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/](https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/)

---

### Post by shantiq on 2013-10-13
> **Temüjin said:**
> I also like clementine with gstreamer-delta plugin (similar to Audacious crystallizer). [https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/](https://decatf.wordpress.com/2010/11/04/gstreamer-delta-audio-sharpening-plugin/)



yea great tip too[[COLOR=#000000]Temüjin[/COLOR]]("http://ubuntuforums.org/member.php?u=327594")[COLOR=#000000] clementine is a corker too especially if library is what one is after; streets ahead of the competition all the **info on bands song lyrics** and similar groups displayed; i shall try the plugin beacause in vanilla form the sound is not great, slightly muffled it seems to my bat-ears :::]]] ;    but definitely a hugely brilliant player!


ok tried it!   and yes just like crystallizer on Audacious  slight echoey silkey sound   very nice   [i personally still favour crystal-bell of Xmms]

[/COLOR]> sudo add-apt-repository ppa:decatf/testy
[COLOR=#000000]sudo apt-get update && sudo apt-get install delta[/COLOR][COLOR=#000000]


then run

[/COLOR]```
[COLOR=#333333][FONT=Ubuntu Mono] gconftool --type string --set /system/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]gstreamer/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]0.10/default/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]musicaudiosink "delta gain=100 ! autoaudiosink"[/FONT][/COLOR]
```

> [COLOR=#333333][FONT=Ubuntu Mono]Gstreamer delta: Audio sharpening plugin[/FONT][/COLOR][COLOR=#000000]
[/COLOR][COLOR=#333333][FONT=Ubuntu Mono]- Valid gain values [0 200]. Default 100[/FONT][/COLOR]

PS in clementine go to tools/preferences and pick GSettings audio sink   [i think]



[ATTACH=CONFIG]246899[/ATTACH][ATTACH=CONFIG]246901[/ATTACH][ATTACH=CONFIG]246900[/ATTACH]


**ps2   **ran same track through clementine xmms and moc [question for [[COLOR=#000000]Temüjin[/COLOR]]("http://ubuntuforums.org/member.php?u=327594")[COLOR=#000000] :surely delta is also acting on moc since it uses Gstreamer too right?[/COLOR]]and the difference is striking [my computer is linked to my very average stereo]
WAY clearer on moc than on clementine still muffled even with plugin   xmms is by far the cleanest and pure sound
&#8203;[[IMG]http://img96.imageshack.us/img96/4558/xt2f.th.png[/IMG]]("http://img96.imageshack.us/img96/4558/xt2f.png")

---

### Post by Rob Sayer on 2013-10-13
Thanks, but I'm afraid the last thing I want to do is install a crystallizer or any other DSP plugin.  For a decent explanation of why you don't want any of that stuff check out the wiki at benchmarkmedia.com.

What I've found with this sort of thing is that dsp and different output modules in clementine et al. do affect the sound.  When it's right the sources in the stereo sound field are stable.  I'm not an soundstaging nut but instruments or voices shouldn't seem to move.

I'm not exactly a hifi purist but I've been into this stuff since the 70s, and if there's anything I've learned it's that if you're listening to how your playback system sounds, rather than just listening to the dang tune, *there's something wrong*.  I'm amazed how many serious audiophiles don't get this.

I haven't dicked around with asound.conf yet (I may never) since my last post here. But I've edited /usr/share/alsa/alsa.conf and changed defaults.pcm.dmix.rate from 48000 to 44100.  As I mentioned before, I don't really care if the audio on video files gets resampled.  But for music, yes.

I *think* that worked, but I haven't had time to listen to it much.  But clementine ... which has great playlist features and I'd really prefer to get that working better ... seems to sound right that way.  As good as deadbeef.  But I'll have to do more testing.  Of course, that may be all wrong and I may have been kidding myself during that quick listen.

Overall, though, linux audio seems to be a poorly standardized bucket of worms.  It's the one area where I think windows is better.

---

### Post by Yellow Pasque on 2013-10-13
> changed defaults.pcm.dmix.rate from 48000 to 44100
AFAIK, if you have pulseaudio running or you're outputting directly to hw:x,y device, then you're not using dmix.

>  For a decent explanation of why you don't want any of that stuff...
Yeah, I've read those types of things, and I'd say it's dependent on the hardware you have and your ears. Sometimes, the only way to get a crappy laptop audio setup to sound good is using EQ. A lot of DSP plugins I've tried did nothing (at best) or just created clipping, but the "noise sharpening / delta" plugin always makes things sound better.

---

### Post by Rob Sayer on 2013-10-15
I agree sometimes you need EQ, but it's more because of bad recordings.  Which unfortunately is most of them.

From what I can tell clementine is working as well as deadbeef with clementine set to alsa output and alsa set to default to 44.1K sample rate.

The problem with comparing these things is level matching ... it's far too little understood that to compare 2 things you have to match levels to less than 0.3dB.  If you don't, they'll sound different, even though you may not be able to tell the volume isn't the same.  This was tested in the 1970s and has been experimentally confirmed a number of times.

You'd *think* it'd be straightforward to do that.  But 100% volume on one player is often noticeably louder than another.

It'd be a lot easier if they all had an option to bypass their software volume control.  But most of them don't.

---

### Post by syntaxerror74 on 2013-10-27
> **Rob Sayer said:**
> 
Frankly, alsa configuration *stinks*.


Yes, but only on console. The problem is that most people do not know that there is also a GUI tool to tweak ALSA parameters. That's why I recommend you to look for **QasMixer**. I wouldn't want to mess with console GUI anymore, unless I need to (some capture settings, e. g. 'What U Hear' on a Creative card will still require that)

---


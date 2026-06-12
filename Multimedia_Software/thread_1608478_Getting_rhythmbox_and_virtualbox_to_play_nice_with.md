---
title: "Getting rhythmbox and virtualbox to play nice with jack - help"
date: 2010-10-29
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-10-29
More audio craziness...

Ideally, I would be able to have Jack (for supercollider) coexisting happily with other apps that use the audio system, specifically --


[LIST]
[*]Rhythmbox (yes, there are other players but this one interfaces cleanly with my iPod)
[*]Oracle virtualbox (which I use for NaturallySpeaking)
[/LIST]

The typical recommendation around the web is to configure ALSA to pipe its audio through Jack, which I tried according to [http://alsa.opensrc.org/index.php/Jack_%28plugin%29]("http://alsa.opensrc.org/index.php/Jack_%28plugin%29"). With that .asoundrc, I could choose ALSA as the driver for VLC and it output okay. But I'm not sure how to tell rhythm box to use ALSA instead of pulse audio. Worse, when I changed my virtual machine's configuration for ALSA (instead of the default pulse audio), the audio connection died -- the alsa ports disappeared from qjackctl's Connections window, and NaturallySpeaking didn't pick up any audio. This is fairly serious because I depend on dictation software to deal with an RSI (dictating English, not code of course) and I'd rather not have to stop Jack just to dictate something.

Rhythm box and virtual box both work perfectly with pulse audio connecting directly to the hardware. In the past, I've gotten pulse audio to route through Jack but it's dicey -- xruns are common and sometimes the audio gets choppy.

What next? I suppose getting the ALSA configuration right is the best thing, but early tests were not exactly encouraging.

Thanks in advance --
James

(edit) PS I'm using virtualbox for DNS because wine failed me. Completely :)  Plus wine's jack option for audio IO did not work with NS at all. NS works really well in virtualbox so I'm keeping that one.

---

### Post by cchhrriiss121212 on 2010-10-29
Virtualisation and audio work do not mix well. Also, I would not recommend using jack all the time, which is what is implied in your post, it is best for audio production only.

If you are not using pulse you could try disabling or removing it. Sorry I can't offer any more help, but your setup seems to be more complicated than is necessary.

---

### Post by Yellow Pasque on 2010-10-29
> **dewdrop_world said:**
> But I'm not sure how to tell rhythm box to use ALSA instead of pulse audio.
```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink alsasink
```

---

### Post by dewdrop_world on 2010-10-29
> **cchhrriiss121212 said:**
> Virtualisation and audio work do not mix well. Also, I would not recommend using jack all the time, which is what is implied in your post, it is best for audio production only.

Let me clarify some use cases:

- Suppose I'm working in SuperCollider, and I notice some odd behavior or I need to ask a question that will take more than a short paragraph or two to describe (which is about as much as I can comfortably type by hand). In the current situation, I have to stop SC audio, stop Jack server, boot up the virtual machine, dictate my message, send it, shut down the virtual machine, restart Jack and reload what I was working on in SC.

By comparison, on my Mac, I could launch MacSpeech Dictate and it would cooperate with all other audio apps.

- Or, I'm going through my e-mail and I want to answer a supercollider question that requires me to test a solution using audio. The current workflow is to shut down the dictation virtual machine, do the test, then reboot to continue dictating.

The question is if there is any way to streamline these workflows. You have to admit, it's not convenient the way it is (though the virtual machine is an improvement over rebooting the entire box into Windows 7).

To some degree, I'm complaining and that's partly a waste of time. But, I'm a recent Linux convert from the Mac, and I can't escape the conclusion that audio handling in Linux is a ghastly mess. I'm dumping Apple because I don't like what they're doing with the app store, but seriously... CoreAudio is one of the things they did very, very right. This whole business in Linux about some apps working together, but they can't be used with other apps so you have to quit the first bunch of apps to use the second, is new to me and frankly, it's a very weak point.

If the developers could standardize on something that would combine the best features of Jack and pulse audio, and app developers would adopt that new standard, it would improve Linux's usability dramatically.

I know that will never happen -- but neither can I sit here and say that the audio situation in Linux is exactly good. Pro audio apps have a server suited to their needs, and entertainment apps have a different server optimized for that, and everybody wins **except the users**.

> **cchhrriiss121212 said:**
> If you are not using pulse you could try disabling or removing it. Sorry I can't offer any more help, but your setup seems to be more complicated than is necessary.

Some searching in the virtual box forums reveals that Oracle basically deprecated alsa support in favor of pulse audio. I don't have a choice about that. It's not an option for me to stop using dictation software.

> **Temüjin said:**
> ```
gconftool-2 --type string --set /system/gstreamer/0.10/default/audiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/chataudiosink alsasink
gconftool-2 --type string --set /system/gstreamer/0.10/default/musicaudiosink alsasink
```

Thanks for this -- I had read about gstreamer conf some time ago but forgot.

James

---

### Post by dewdrop_world on 2010-10-30
I suppose another choice is to use different audio hardware for Jack, and then a hardware mixer to bring the onboard and outboard audio together into the speakers. But I'd still consider that a hardware workaround to a software limitation.

James

---

### Post by cchhrriiss121212 on 2010-10-30
> I can't escape the conclusion that audio handling in Linux is a ghastly mess
That is not the way I would put it, but I agree with your sentiment. Pulse has been problematic for some time now, but it is improving at a slow rate.

With that in mind I think your best option is to get pulse running through jack. When trying it before what steps did you take to set it up? Did you see the pulse-jack sink package in [this PPA]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/+index?start=300&batch=75")?

There are numerous tweaks you can use to get xruns down while using a low latency, like installing a [low latency kernel]("https://launchpad.net/%7Eabogani/+archive/ppa") and disabling things like compiz.

---

### Post by dewdrop_world on 2010-10-31
> **cchhrriiss121212 said:**
> That is not the way I would put it, but I agree with your sentiment. Pulse has been problematic for some time now, but it is improving at a slow rate.

I might have been too harsh -- but software improves in response to user criticism, and it's an area where some criticism is warranted.

And I should also say, it's not ideal in Windows either. When I boot into the win7 partition, the dictation software can share the audio hardware with apps that are using the normal Microsoft MME driver, but if something else has grabbed the hardware with ASIO, it chokes -- say I want to use SuperCollider with a latency less than 230 ms (!) :)

I'm actually not having problems with pulse when running it by itself. I'm dictating in virtual box now while Stravinsky is playing in rhythm box, no issues.

> With that in mind I think your best option is to get pulse running through jack. When trying it before what steps did you take to set it up?

[http://ubuntuforums.org/showthread.php?t=1581522](http://ubuntuforums.org/showthread.php?t=1581522)

> Did you see the pulse-jack sink package in [this PPA]("https://launchpad.net/%7Efalk-t-j/+archive/lucid/+index?start=300&batch=75")?

Didn't see that one. I had installed pulseaudio-module-jack (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) from the software center. Any difference?

>  There are numerous tweaks you can use to get xruns down while using a low latency, like installing a [low latency kernel]("https://launchpad.net/%7Eabogani/+archive/ppa") and disabling things like compiz.

Haven't gone for a low latency kernel yet; maybe it's time.

As far as I could find online, the way to disable compiz is to go to appearance > visual effects and set "none." I did that a long time ago (I hate the flashy stuff) but I'm not totally convinced this has really got rid of it. Anything else I need to do?

Thanks!
James

---

### Post by cchhrriiss121212 on 2010-10-31
> Didn't see that one. I had installed pulseaudio-module-jack  (1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14) from the software  center. Any difference?
I'm not sure whether it will be different for you, but that PPA is by FalkTX who has developed his own OS, KXStudio, that has pulse+jack working out of the box. The consensus in [this thread]("http://ubuntuforums.org/showthread.php?t=1589400") seems to indicate it works well.

> As far as I could find online, the way to disable compiz is to go to  appearance > visual effects and set "none." I did that a long time  ago (I hate the flashy stuff) but I'm not totally convinced this has  really got rid of it. Anything else I need to do?
That means it is disabled, but if you don't need compiz any more you can also remove it completely using software center.

> Haven't gone for a low latency kernel yet; maybe it's time.

It is not necessary for everyone, but a low latency kernel plus jack in realtime mode will give you reliable output and latency of <10ms.

---

### Post by dewdrop_world on 2010-11-10
Been a few days... anyway, thanks for the ideas. I've been busy working (that is, actually *getting stuff done* with Ubuntu!). I'll come back to this when I have time, but it won't be right away.

James

---

### Post by zenon222 on 2010-11-18
WOW!
Upgrading to Lucid broke PulseAudio and Rhythmbox completely, now in less than 5 minutes I'm up and running again!

THANK YOU

---


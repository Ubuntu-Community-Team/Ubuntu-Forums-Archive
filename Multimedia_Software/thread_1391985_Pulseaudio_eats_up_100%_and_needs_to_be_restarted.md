---
title: "Pulseaudio eats up 100% and needs to be restarted"
date: 2010-01-27
forum: Multimedia Software
---

### Post by defaria on 2010-01-27
I'm on 9.10 and I use huludesktop often to watch my Hulu queue. Every once in a while (and more so lately) the video freeze and the sound stutters. I then find that pulseaudio is taking 100% of a CPU (I have a quad core AMD 64bit machine). Killing pulseaudio causes huludesktop to continue without sound and a new pulseaudio starts up. I have to kill huludesktop and resume playback and then everything's OK, until it happens again.

Is anybody else experiencing this? Is there a fix?

I've searched around for one but none seem to describe my situation exactly nor do any of the workarounds seem to work.

---

### Post by bowens44 on 2010-01-27
I was seeing pulseaudio with 100% cpu usage. I removed linux-backports-modules-alsa-2.6.31-16-generic and the problem went away.

---

### Post by sports.car.guy on 2010-01-28
I hate to say this to you and there are people who will disagree, PulseAudio is a buggy hunk of code that should fade out of Linux and stay a part of the Windows world. Both are programmed with a similar mentality. Lets make it robust and not keep code lean. Programmers are loosing this concept and the PulseAudio developers really have.

They have crammed too much into it for starters. They keep throwing bad on top of worse. The code for PulseAudio should be frozen and completely audited and rewritten from the ground up. It has way too many latency issues which cause problems with audio syncing, chirping out of your speakers, all fun things like that.

It is a multi OS environment, another downfall in it's case. It is not like a GPU where the calls to the hardware are consistent and you can have cross coding. How Windows handles sound is far different then Unix and Unix-like environments.

Now the companies and community groups that handle the different distributions aren't helping either. They are counting on PulseAudio to become the default and only sound service for Linux, this is regardless of the community outcry. The ones who embraced it, pushed it into their end product far too early and are relying way too heavily on it to make the experience more Windows like with sound setup.

THIS IS NOT WINDOWS! IT IS LINUX! They need to grasp this along with new users coming into the Linux community. Creating a layer to allow for easy configuration of Alsa or transitioning to JACK instead of PulseAudio is the way to go.

Because of all of the short comings of PulseAudio and what you are experiencing I would suggest tossing it. If on Ubuntu with Gnome you can switch to GStreamer or use Alsa with the Esound pluging for it, or I think there is a PulseAudio one for piping through Alsa as well.

---

### Post by defaria on 2010-01-29
That's nice however I was not looking for you soapbox speech. I was looking for a solution! Please take your rant somewhere else where it's more appropriate and perhaps more helpful.

Thanks.

Regarding linux-backports-modules-alsa-2.6.31-16-generic - I don't have it installed.

---

### Post by sports.car.guy on 2010-01-29
> **defaria said:**
> That's nice however I was not looking for you soapbox speech. I was looking for a solution! Please take your rant somewhere else where it's more appropriate and perhaps more helpful.

Thanks.

Regarding linux-backports-modules-alsa-2.6.31-16-generic - I don't have it installed.

I gave you a solution of removing PulseAudio you schmuck, and using GStreamer or Alsa!

That is truly the only way to solve your problems. If you even searched the threads here that is what everyone tells people to do. If you expanded the search to google you would find the same there.

OMG removal is a solution that would take um, like all of 10 minutes including installing GStreamer or additional Alsa components that aren't installed on your system!

You could even use the jack sound server as well.

I gave you the reasons why you are dealing with what you are, then the way to solve it! Truly solve it that is! It is not my problem you would rather waste more of your life then you already have with this trying to fix something that is beyond broke, instead of getting rid of it for something that works.

Ignorant or an idiot savant, the verdict is out!

Oh and another thing. If PulseAudio wasn't filled with the problems that it is, like you are experiencing, why wouldn't Kubuntu have it as part of their Ubuntu variant. Simple, the PulseAudio developer refers all bugs, inquires on problems to the didtrubutions and won't take responsibility for his crappy code! He claims his code is perfect like you think you are, and claims no one but him knows how to properly implement it because he has not had one problem it seems millions are experiencing. The Kubuntu team have better things to do then deal with PulseAudio and the BS it brings such as idiots like you who don't want to actually take some advice on truly fixing it.

---


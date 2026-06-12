---
title: "Kaffeine insists on internal sound hw"
date: 2009-05-07
forum: Multimedia Software
---

### Post by umuro on 2009-05-07
On Kubuntu 9.04

I have been using external USB audio hardware.

I have no problem with Amarok or Firefox.

Used system settings multimedia to set the priorities of audio hardware. Wrote a little .asoundconf to fix firefox.

But...

On Kaffeine, it insists on using auto for the sound backend (saying alsa is busy) and sound never goes to external usb!!!

So I am very confused here. Amarok behaving as expected and Kaffeine not. Bot are KDE applications... So what is the difference? :confused:

---

### Post by inobe on 2009-05-07
try xine' it makes an excellent kde backend.

i really never used kaffeine, not once........

using linux for years

---

### Post by umuro on 2009-05-08
That's where my confusion is. Kaffeine is using XINE.

---

### Post by xc3RnbFO8P on 2009-05-08
> On Kaffeine, it insists on using auto for the sound backend (saying alsa is busy) and sound never goes to external usb!!!
In Settings> Xine Engine> Audio, did you try to change it to Alsa?

---

### Post by umuro on 2009-05-08
> **Ringi said:**
> In Settings> Xine Engine> Audio, did you try to change it to Alsa?

It replies "Alsa is busy". Hmmm, if Alsa is busy then how amarok and firefox are able to work at the same time?

---

### Post by HavocXphere on 2009-05-08
Had similar issues in Kubuntu 8.10.

Some random pointers with absolutely no guarantees:

Some people blacklist the internal device so that only the external is available.

Setting default ALSA output device:
asoundconf list
asoundconf set-default-device [device_name_from_listing]

And finally make sure that the order of the devices in the system settings->sound is right.

EDIT: "sudo alsa force-reload" can also fix temporary issues...but it lacks elegance.
EDIT2: The force command kills all apps that are connected to the sound server.

---

### Post by umuro on 2009-05-08
Ok. I guess I found the reason. But not the solution.

I have in .asoundrc
```

pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:1,0"
}
capture.pcm {
type plug
slave.pcm "hw:1,0"
}
}

```

So when every I start audio in Firefox, sorry for XINE. It can no longer use alsa.

Is there a better .asoundconf so that Firefox and XINE could use external USB audio at the same time?

---

### Post by umuro on 2009-05-09
I had to write .asoundconf myself because "asoundconf set-default-device [device_name_from_listing]" does not work with Logitech Z Cinema which I happen to use.

---

### Post by markbuntu on 2009-05-09
The only way that I have found to change the global xine default in Jaunty is through xine-ui so get that and then run it and make yourself "master of the known universe" and change the audio default. 

I have also found pulseaudio very helpful for managing multiple sound devices in KDE4.2/Kubuntu Jaunty. You can read this about that. I have just edited it to include Jaunty.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

Please let me know how this works out for you.

---

### Post by umuro on 2009-05-10
xine was already working see below.

Like asoundconf, pulse audio does not work for Z Cinema. The reason is this usb audio hardware has a foreign character in its name (the stuff you get with aplay -l is Z Cin?ma). As pulseaudio uses names, it was the only hardware I could not use. Otherwise pulseaudio was nice :(

And I am not expecting soon that anybody corrects this non-ascii characters problem in usb device names.

So I am stuck with alsa configuration which enable me to access it sayin hw:1,0 

This problem only and only applies to Logitech Z Cin?ma. No other usb hardware.

And I became aware that I am able to set xine without any problems.

But I have to exit any applications or tray bar applications that uses audio now. Because only one application at a time can use it. I open firefox, xine dies. I open xine, firefox dies. My twitter client goes ping and my firefox and xine dies. etc. etc.

So now my problem is this. The asoundconf above sets it as the default device. That's working!

But only one application at a time can use it!

THE CORRECT PROBLEM IS HOW TO WRITE AN ALSA CONF THAT CAN ALOW ONE HARDWARE TO BE USED BY MULTIPLE APPLICATIONS.

 I know that in alsa there is a way to mixin all applications to the same hw. But how to specify it?

Current .asoundconf is

```
pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:1,0"
}
capture.pcm {
type plug
slave.pcm "hw:1,0"
}
}
```

---

### Post by Chronon on 2009-05-10
umuro, I am having similar problems, except I use an Nvidia card, so maybe I will look into using PulseAudio, even though it seems it's not intended for use with Kubuntu at this time.

---

### Post by umuro on 2009-05-10
> **Chronon said:**
> umuro, I am having similar problems, except I use an Nvidia card, so maybe I will look into using PulseAudio, even though it seems it's not intended for use with Kubuntu at this time.

I tried Pulse audio. I was fantastic. I were able to redirect sound anywhere on the fly. Every sound device. Even over the network. 

But... Except... "Logitech Z Cin?ma"

Pulse audio was never able to select Z Cin?ma because of its weird name. So far I could not find a way of overcoming this name with a foreign character problem with pulse audio, too. Like asoundconf, pulseaudio uses their names to target the devices. This is good because your usb hardware could be on a different slot the next day. But they are only working with ascii names!

Would it be possible to configure pulse audio to use a virtual alsa device so that I can workaround this name problem?

---

### Post by umuro on 2009-05-10
So far potential solutions seem like
a) Writing an advanced alsa configuration that allows sound overlaying. That requires digging into low levels of alsa which are not required by anybody nowadays.
b) Going beyond what is possible in visual configuration tools for pulseaudio. So that I can address the device without referring to its name but hardware slot.

If I do any of those then I'll become ultimate audio configuration guru :(

---


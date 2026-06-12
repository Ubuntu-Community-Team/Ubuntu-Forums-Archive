---
title: "Bluetooth headphone Motorola S9"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by heart_reaver on 2007-12-13
Hi All,

What would be simple way to configure blue tooth headphone Motorola S9. 

I am not even able to pair them up in Gusty.

---

### Post by CypherSystem on 2008-03-14
Im in the Same Boat.

The S9's Rule, but I cant get Gutsy to Work With Them  .:(

---

### Post by CypherSystem on 2008-03-14
"obex://[00:0d:fd:1a:bb:c9]" is not a valid location.

This is the Error

---

### Post by CypherSystem on 2008-03-14
[http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/#comment-4096](http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/#comment-4096)


This allowed me to connect, Now I just need to figure out how to re route the Sound.

---

### Post by fudje on 2008-04-18
Depends what you want to do with the headset.

Not sure if this will work with Older versions of the distro, but for Hardy I managed to get stereo support for gstreamer apps with the a2dpsink gstreamer plugin, by doing something similar to:

> gconftool-2 --set /system/gstreamer/0.10/default/musicaudiosink --type string "sbcenc ! a2dpsink device=[S9 BTAddr]"

Where [S9 BTAddr] is the bluetooth device address of the S9 Headphones.  You can also substitute in audiosink and chataudiosink to cover more apps (although you probably want to use a SCO setup instead of A2DP for chat, which currently requires some hacking of ~/.asoundrc -- also, unfortunately, you don't seem to be able to mix input, which is only supported by SCO, with A2DP output
, so you can have either quality stereo output or two-way single-channel low-bitrate voice).
Currently as far as I know there is no useful UI way to do this.
I'm considering putting the grunt work in to support SCO and A2DP devices with a pulseaudio plugin, which should simplify things greatly for the average user, but haven't started anything yet (I first need to do some investigation of how the gstreamer and alsa plugins work).

Hope this was helpful to someone :)

You might want to trylooking at [http://wiki.bluez.org/wiki/HOWTO/AudioDevices](http://wiki.bluez.org/wiki/HOWTO/AudioDevices)

---

### Post by shaunbarlow on 2008-04-29
> **fudje said:**
> 
Currently as far as I know there is no useful UI way to do this.
I'm considering putting the grunt work in to support SCO and A2DP devices with a pulseaudio plugin, which should simplify things greatly for the average user, 

I'm just sussing out how easy it's going to be to get bluetooth audio working in hardy (I'm planning on doing a clean install when I find the time and backup storage space). I've been using it in Gutsy mostly successfully and from the mumblings I've read here and there Pulseaudio is supposed to make it really intuitive to get things happening. 
By the sounds of this post it's still a bit of a long handed process, sooo fudje: I support your effort into producing a good a2dp plugin for pulse. 
I'm not a programmer, but if there is layman work to be done I'd be glad to help out.
Cheers all!

---


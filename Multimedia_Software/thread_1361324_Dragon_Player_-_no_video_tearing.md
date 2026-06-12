---
title: "Dragon Player - no video tearing?"
date: 2009-12-21
forum: Multimedia Software
---

### Post by Roasted on 2009-12-21
For years I've been plagued with video tearing on VLC, no matter what I did, nothing worked. I tried every fix in the book. Nothing. Worked. Ever.

I recently switched to Kubuntu, loving every minute of it. I have a high def live concert file here and I fired it up and blam - dragon player opened. Uh, what? No, I want VLC. I want VLC because, well, no reason... I'm just used to VLC.

But as Dragon Player was playing, I quickly noticed the high paced strobe lights and guitar solos and drum swings and, wow, no video tearing? Really?

Fired up VLC = blam. Video tearing.

What is the story with Dragon Player? Has it been KDE's default for a long time now? I've never heard of it, but then again I only recently came to KDE land. Is it available on Gnome as well? Is it a KDE application? The lack of K-something in the name made me curious.

---

### Post by Yellow Pasque on 2009-12-21
It is a replacement for Codeine(KDE3)

> Is it available on Gnome as well? Is it a KDE application?
Well, it uses Qt libraries and Phonon/xine, but that doesn't mean you can't use it in GNOME.

---

### Post by Roasted on 2009-12-21
I see it locks out the DSP, or whatever that is where it locks out system sounds outside of the program itself.

Is there a way to adjust that?

---

### Post by Yellow Pasque on 2009-12-21
Set xine to use Pulseaudio if you're running that.

---

### Post by Roasted on 2009-12-21
> **Temüjin said:**
> Set xine to use Pulseaudio if you're running that.

So I need to set xine to use pulseaudio... but where do I access xine? I'm kind of drawing a blank as to where I would do that. Do I do that within Dragon Player since it's just a frontend for xine, or do I need to do it in "xine" itself?

Sorry if it's a dumb question. I was just drawing a blank.

---

### Post by Yellow Pasque on 2009-12-22
You can use the xine-ui program/package to generate a config file and alter settings, or you can find a generic xine configuration file (~/.xine/config) file and text-edit that to your liking.

> Sorry if it's a dumb question. I was just drawing a blank.
Not at all. xine configuration can be confusing since "xine" is a standalone media player and libxine is used by Phonon.

---

### Post by lovinglinux on 2009-12-22
I still have tearing with Dragon Player, but my problem is not persistent. It happens when the nvidia driver fails to load with Direct Rendering enabled, due to permission issues. See [workaround here](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2). I'm using that workaround since Jaunty and it works like a charm. Nevertheless, sometimes nvidia still loads with direct rendering disabled.Then I need to reboot to fix it.

---

### Post by Roasted on 2009-12-22
> **lovinglinux said:**
> I still have tearing with Dragon Player, but my problem is not persistent. It happens when the nvidia driver fails to load with Direct Rendering enabled, due to permission issues. See [workaround here](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2). I'm using that workaround since Jaunty and it works like a charm. Nevertheless, sometimes nvidia still loads with direct rendering disabled.Then I need to reboot to fix it.

I don't understand entirely. Nvidia just randomly boots up with different settings that can dictate when/how bad your video tearing is? 

I mean, in my instance when I have the latest driver and I have video tearing in VLC, but not Dragon, that tells me something is wrong with VLC. 

No?

---

### Post by lovinglinux on 2009-12-22
> **Roasted said:**
> I don't understand entirely. Nvidia just randomly boots up with different settings that can dictate when/how bad your video tearing is?

In my case, yes. I usually check with this command:

```
glxinfo | grep -i direct
```

If the resulted output says "Direct Rendering: No", then I get tearing, no matter which player I use. If it says YES, then I'm good.

> **Roasted said:**
> I mean, in my instance when I have the latest driver and I have video tearing in VLC, but not Dragon, that tells me something is wrong with VLC. 

No?

Perhaps you don't have Direct Rendering at all, but Dragon player settings are different from VLC and other players. For instance, it could be using a different output driver (i.e. xv, x11, vdpau, gl etc).

---

### Post by Roasted on 2009-12-22
> **lovinglinux said:**
> 



Perhaps you don't have Direct Rendering at all, but Dragon player settings are different from VLC and other players. For instance, it could be using a different output driver (i.e. xv, x11, vdpau, gl etc).

But it still begs this question - in VLC I tried every single mode of output. I tried all settings possible. Each one wasn't better than the last. I'm really confused on how they could be different.

Another thing is I have a high def concert video file that's just over 2 gigs in size. When I fire it up in dragon player, bam, perfect aspect ratio. When I fire it up in VLC, it's scrunched on the very far left. Why? I have no idea. No matter what video or ratio settings I change, it still stays scrunched on the left, leaving the center/right completely black. Yet Dragon works fine...

Come on, VLC...

---

### Post by nerdy_kid on 2009-12-22
maybe -- (my thread) [http://ubuntuforums.org/showthread.php?t=1348168](http://ubuntuforums.org/showthread.php?t=1348168)

tells how to fix desktop wide page tearing and is what i do -- have NVIDIA Geforce 8600M and NO PAGE TEARING YAY!!!!

---

### Post by Roasted on 2009-12-24
Well, my initial idea failed. I still have video tearing in dragon player too. While it doesn't seem that bad in dragon player as it did in VLC, it's still there.

I have no tearing on my 19 inch monitor, 1440x900. But when I move dragon player to my main monitor, 24 inch 1920x1080, I have tearing.

Maybe, just maybe, us *buntu users don't have to deal with this. Sigh.

---


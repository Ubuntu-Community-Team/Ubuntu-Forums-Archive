---
title: "Problem with Totem"
date: 2018-05-01
forum: Multimedia Software
---

### Post by jeo7 on 2018-05-01
I just installed Ubuntu 18.04 on my AMD 64 computer with Radeon R7 graphics. A kind person on ASK UBUNTU pointed me to a webpage where I managed to download a video driver(s) for my system. The driver I installed fixed one issue I was having (video hash when waking up from suspend), but one very irritating issue remains.

When I play, say, an mp4 with Totem (videos) I get a psychedelic mixture of colors where I can make out movement, but I cannot see any features. This does not happen and never happened on other video players. Ordinarily, I'd just let it go and use another video player, but I really like Totem and I really would like to solve this problem because I don't know what is says about the health of my system.

Has this happened to anyone else? Any ideas on how to fix this problem with Totem? 

Thanks in advance.

---

### Post by jeo7 on 2018-05-01
I ran Totem from a terminal and this is the message I got:

```

/Videos$ totem B.mp4
mesa: for the -simplifycfg-sink-common option: may only occur zero or one times!

(totem:4559): Gtk-WARNING **: 22:02:56.144: Drawing a gadget with negative dimensions. Did you forget to allocate a size? (node slider owner GtkScale)

```

---

### Post by mc4man on 2018-05-02
try 
```
sudo apt purge gstreamer1.0-vaapi
```

---

### Post by jeo7 on 2018-05-02
Thank you! That has brought back people looking like people. However, now I have another problem ... video playback sometimes is choppy. In places, it seems to hesitate every 5 seconds or so. It's only the video that does this. Sound is fine.

Anybody know how to fix hesitating video in Totem?

---

### Post by jeo7 on 2018-05-03
Yesterday and today I tried the following to solve the hesitating playback of videos problem:

1. Uninstalled GStreamer codecs in case there might have been a conflict of codecs
2. Uninstalled and reinstalled ubuntu-restricted-extras
3. Uninstalled and reinstalled Totem

None  of these has solved my problem. Now things get really, really weird.  When I installed Ubuntu, I created 2 accounts because I like to keep my  working account separate from my administrator account (because I go  overboard on security). For obvious reasons, I've been doing all this  from the administrator account. Today I logged into the  non-administrator account and attempted to play that video that has  given me such problems ... and it played without the hesitations and  getting stuck that I see from my administrator account. How could this  be? Why would Totem behave differently in a different account? And how  can I solve this problem with the administrator account?

---

### Post by monkeybrain20122 on 2018-05-03
One of the first things I do after installing Ubuntu is to remove totem. It is garbage, there are much better video players around : mpv or vlc.

---

### Post by jeo7 on 2018-05-04
> **monkeybrain20122 said:**
> One of the first things I do after installing Ubuntu is to remove totem. It is garbage, there are much better video players around : mpv or vlc.

I actually like Totem. I guess I just got used to it in prior releases.

I think that I have hit on something that might point the finger to the root of the problem. The problem exists in Gnome and Gnome derivatives such as the Ubuntu desktop. In addition to Gnome, I have KDE and Cinnamon installed. I noticed this evening that the problem does not exist in KDE.

I have to retract partially what I posted earlier. In the non-administrator account, the problem sometimes exists, sometimes doesn't. So it's more dependent on the desktop environment than on the account type.

---

### Post by jeo7 on 2018-05-04
Ok, after much researching and experimenting, I have significantly narrowed down the problem. Here are the facts: It is not a video driver problem. It depends strongly on the desktop environment because it is seen only in Gnome (and Gnome derivatives). The problem is not seen using Totem in KDE nor in Cinnamon.

But it is even narrower than that. In fact, the problem exists only with Gnome on Xorg. Gnome on Wayland does not have this problem. Unfortunately, Ubuntu chose to make Gnome on Xorg the default in 18.04.

So why does Totem hesitate, jerk, and halt in Gnome on Xorg but not on other desktop environments or even on Gnome on Wayland? I think this is either a bug or points to a larger problem putting Gnome on Xorg.

---

### Post by monkeybrain20122 on 2018-05-05
> **jeo7 said:**
> Ok, after much researching and experimenting, I have significantly narrowed down the problem. Here are the facts: It is not a video driver problem. It depends strongly on the desktop environment because it is seen only in Gnome (and Gnome derivatives). The problem is not seen using Totem in KDE nor in Cinnamon.

But it is even narrower than that. In fact, the problem exists only with Gnome on Xorg. Gnome on Wayland does not have this problem. Unfortunately, Ubuntu chose to make Gnome on Xorg the default in 18.04.

So why does Totem hesitate, jerk, and halt in Gnome on Xorg but not on other desktop environments or even on Gnome on Wayland? I think this is either a bug or points to a larger problem putting Gnome on Xorg.

But gnome on  wayland (or anything on wayland for that matter) have even bigger problems. It is a good idea not to default to wayland.

---

### Post by ooops2 on 2018-06-30
> **jeo7 said:**
> 
 Now things get really, really weird.  When I installed Ubuntu, I created 2 accounts because I like to keep my  working account separate from my administrator account (because I go  overboard on security). For obvious reasons, I've been doing all this  from the administrator account. Today I logged into the  non-administrator account and attempted to play that video that has  given me such problems ... and it played without the hesitations and  getting stuck that I see from my administrator account. How could this  be? Why would Totem behave differently in a different account? And how  can I solve this problem with the administrator account?

For me the source of choppy play was the amdgpu1-fan setting of the system-monitor applet. Apparently, the kernel-driver blocks the GPU for some time. After disabling that videos play without stutter.

---

### Post by ariel on 2018-08-07
Removing gstreamer1.0-vaapi solved this problem in my case as well. AMD GPU / RX560 here. Wondering though... removing acceleration will is manageable for x264 but may render HEVC playback unusable. Hopefully there is a bug open somewhere for this.

---


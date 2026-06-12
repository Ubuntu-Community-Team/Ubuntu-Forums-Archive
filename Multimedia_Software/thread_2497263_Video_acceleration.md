---
title: "Video acceleration"
date: 2024-04-28
forum: Multimedia Software
---

### Post by Shishimaru on 2024-04-28
Good day everyone.

I have an Nvidia laptop and an external monitor connected via DP. On Kubuntu 24.04, I installed the proprietary drivers (535) and I see that I get no video acceleration at all in any browser or video player.

A simple video file runs at 0.4% of my CPU on Windows, while on Ubuntu I am at 115%. A 360 video online instead it takes around 50%. It's a lot.

I have tried to see some guides on the internet, but some are outdated, some are for Intel only.

Am I missing something?

edit: KDE neon seems to go perfectly both with Haruna and VLC (but live USB version with Wayland with open source drivers). Same goes with Clear Linux (Gnome and Live, which is the best performance hands down).

Maybe there's something wrong with the proprietary drivers?

---

### Post by Autodave on 2024-04-28
You need to give us the make and model of your laptop.  It sounds like you probably have 2 GPUs and your laptop is only using the low powered one.

---

### Post by Shishimaru on 2024-04-29
> **Autodave said:**
> You need to give us the make and model of your laptop.  It sounds like you probably have 2 GPUs and your laptop is only using the low powered one.

Hi!

It's MSI Vector GP68 HX13V. And yes, it has two GPUs. When connected to an external monitor, the Intel one cannot be selected (it's the same as in Windows): [https://imgur.com/a/jcOjFTj](https://imgur.com/a/jcOjFTj)
[IMG]https://imgur.com/a/jcOjFTj[/IMG]

---

### Post by Shishimaru on 2024-04-30
EDIT: for Ubuntu users, they can start from [this link]("https://ubuntuhandbook.org/index.php/2024/01/firefox-vaapi-nvidia/?unapproved=3756819&moderation-hash=afd2b3ca871ae728931ebdfafe6d8827") and see if it works. Unfortunately it requires to use a PPA since Ubuntu uses a very old version of nvidia vaapi driver for who knows what reason. If you installed the driver, do a sudo apt update and then dist-upgrade. Otherwise, proceed to update and install the driver.
Note that:
- laptop users should switch to "Nvidia Performance" in the NVidia settings and restart the OS in order to fully use the Nvidia card
- the "export LIBVA driver name=nvidia" will go along with the line above
- unfortunately for me it didn't 100% work with Nvidia, but it worked with the Intel and in this case you can omit both the line above (so in Nvidia settings leave to Nvidia On-Demand)
In the end vaapi gets correctly used with mpv and Haruna, but not the browsers. At least for Edge and Chrome, they seem to use the Vaapi instead of the ffmped decoder. I don't know why the nvtop command says that the drivers are not set in "compute". Maybe they are using accelerated video instead. The intel_gpu_top command says that a very small % of video is elaborated, while it stays 0 if vaapi is not enabled.
Hopefully someone here has any suggestion.

---

### Post by Yellow Pasque on 2024-05-02
If you're using an Intel/Nvidia hybrid GPU laptop, then you want to use the Intel GPU for web browsing and video play (so stay in ondemand mode). Save the Nvidia GPU for games, CAD, CUDA, etc.

> In the end vaapi gets correctly used with mpv and Haruna, but not the browsers.
Probably because Ubuntu distributes Firefox and Chromium as snaps (for some reason).

---


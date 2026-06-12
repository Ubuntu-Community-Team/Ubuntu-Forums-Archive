---
title: "How to get 2560x1080 resolution on Toshiba Qosmio X775 (LG IPS Monitor 29EA93 29&quot;)"
date: 2013-11-11
forum: Multimedia Software
---

### Post by nelsoneci on 2013-11-11
(Ubuntu 12.04 precise LTS)

Hi.

I have a Toshiba Qosmio X775. The video card is a NVIDIA GeForce GTX 560M with Optimus (It also has an Intel video card).
I also have a 29" ultawide monitor ( [http://www.lg.com/uk/monitors/lg-29EA93](http://www.lg.com/uk/monitors/lg-29EA93) ).

The laptop has two video outputs and I have two external monitors. One of them works fine at 1920x1080, plugged to the VGA connector.

The issue I have is that the big monitor (connected to the HDMI connector) works with resolution 1920x1080 while it should be working at [FONT=Arial]2560 x1080.
I checked the same setup (and HDMI cable) works at the desired resolution using Windows 7.

I tried installing the restricted NVIDIA driver but it did not work, so I would prefer to use the open source drivers if it is possible (less pain). I don't care if I have to use the intel or the nouveau driver.

I tried reading instructions on the internet and I could not find a way to solve the issue.
I have read I need to instruct the software driver to use a higher frequency so that it can attain the desired resolution.

Can you help debug the issue? Thanks!

[/FONT]Xorg.0.log : [http://pastebin.com/hpNQxuWS](http://pastebin.com/hpNQxuWS)
[FONT=Arial]
[/FONT]lspci : [http://pastebin.com/YH6wyXDv](http://pastebin.com/YH6wyXDv)

---

### Post by nelsoneci on 2013-11-12
I researched and it seems I had to install bumblebee for things to work.
I decided to save the pain and installed 13.10 instead of the 12.04 LTS I wanted (I prefer not to use ppa repositories).
Things worked out of the box. I'll wait for the next LTS.

---


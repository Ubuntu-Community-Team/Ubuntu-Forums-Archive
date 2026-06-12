---
title: "Microphone Built in Audio is not working - Del G3 3590 with Ubuntu 23.04"
date: 2023-04-24
forum: Multimedia Software
---

### Post by jeyanxm on 2023-04-24
[COLOR=#232629][FONT=-apple-system]
Built-in Microphone is not working in laptop Dell G3 3590 with Ubuntu 22.04, Ubuntu 22.10, and Ubuntu 23.04.[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system][COLOR=var(--black-200)  !important][FONT=inherit][COLOR=var(--black-500)  !important][FONT=inherit][FONT=inherit]
[/FONT][/FONT][/FONT][/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][FONT=var(--theme-post-body-font-family)][FONT=inherit][TABLE="width: 50%"]
[TR]
[TH="class: s-table"]Output Device[/TH]
[TH="class: s-table"]Results[/TH]
[/TR]
[TR]
[TD]Speakers Built-in Audio[/TD]
[TD]Working[/TD]
[/TR]
[TR]
[TD]Headset - ***[/TD]
[TD]Working[/TD]
[/TR]
[TR]
[TD]Handsfree - ***[/TD]
[TD]Working[/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=inherit][TABLE="width: 50%"]
[TR]
[TH="class: s-table"]Input Device[/TH]
[TH="class: s-table"]Results[/TH]
[/TR]
[TR]
[TD]Handsfree - ***[/TD]
[TD]Working[/TD]
[/TR]
[TR]
[TD]Microphone - Built-in Audio[/TD]
[TD]Not Working ( some constant noise while playback the recording )[/TD]
[/TR]
[TR]
[TD]Headset Microphone - Built-in Audio[/TD]
[TD]Not Working[/TD]
[/TR]
[/TABLE]
[/FONT]
[FONT=inherit]inxi -Fxz[/FONT]
System:
  Kernel: 6.2.0-20-generic arch: x86_64 bits: 64 compiler: N/A Desktop: GNOME
    v: 44.0 Distro: Ubuntu 23.04 (Lunar Lobster)
Machine:
  Type: Laptop System: Dell product: G3 3590 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 0DKM3T v: A00 serial: <superuser required> UEFI: Dell
    v: 1.4.3 date: 07/01/2019

Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Dell driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  Device-2: NVIDIA TU116 High Definition Audio vendor: Dell
    driver: snd_hda_intel v: kernel bus-ID: 01:00.1
  Sound API: ALSA v: k6.2.0-20-generic running: yes
  Sound Server-1: PulseAudio v: 16.1 running: no
  Sound Server-2: PipeWire v: 0.3.65 running: yes
[FONT=inherit]AlsaMixer & Settings->Sound [[IMG]https://i.stack.imgur.com/TOEB4.png[/IMG]Sound" style="margin: 0px; padding: 0px; border: 0px; font-style: inherit; font-variant: inherit; font-weight: inherit; font-stretch: inherit; line-height: inherit; font-family: inherit; font-optical-sizing: inherit; font-kerning: inherit; font-feature-settings: inherit; font-variation-settings: inherit; vertical-align: bottom; box-sizing: inherit; max-width: 100%;">]("https://i.stack.imgur.com/TOEB4.png")[/FONT]
[FONT=inherit]Online Microphone Testing [https://webcammictest.com/check-mic.html](https://webcammictest.com/check-mic.html) [[IMG]https://i.stack.imgur.com/qGPBm.png[/IMG]]("https://i.stack.imgur.com/qGPBm.png")[/FONT]
[/FONT]

[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]Update[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]adding these two lines solved the issue in my case[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]edit /etc/modprobe.d/alsa-base.conf to add[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]blacklist snd-hda-intel blacklist snd-soc-skl[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system][https://github.com/thesofproject/linux/issues/1877#issuecomment-596600017](https://github.com/thesofproject/linux/issues/1877#issuecomment-596600017)[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]
[/FONT][/COLOR]

---


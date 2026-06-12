---
title: "How to install avideumx external filters ?"
date: 2012-01-25
forum: Multimedia Software
---

### Post by flemur13013 on 2012-01-25
I've been trying to install an external filter to avidemux without much luck, including groping thru the avidemux wiki/docs and avisynth docs, and haven't been able to find some very basic information.

Before I forget, please don't recommend the [avisynth wiki page]("http://ubuntuforums.org/avisynth.org/mediawiki/External_filters") because it doesn't address this question.

Questions:
 - Are the filter files always DLLs? 
 - Are these windows DLLs, and do they work as filters in Linux?
 - If the Linux filters are NOT .dll files, what are they (extention)?
 - If anyone has added external filters to either windows or linux version, how did you do it and what kind of file was it? 

I have two versions of avidemux:

- Linux version 2.5.2: w/option to tell it where the external filters are. 

- Windows version 2.5.6 working fine under wine: NO option to tell where external filters are.

I downloaded the [Hdragc-1.8.7.zip]("http://strony.aster.pl/paviko/hdragc.htm") filter for a test. The zip files contains AGC.dll, a license.txt file and a hdragc-help.htm file which doesn't tell how to install the filter. The DL page also doesn't tell how to install it or whether it's for windows or linux or both.

But I gather that the file "AGC.dll" is the filter! 

Here's what I've tried:

1- Linux: extract AGC.dll somewhere and tell Linux version where it is. 
It doesn't show up. 

2- Windows/wine: since I can't tell it where the filter is, I put AGC.dll in the ~/.wine/drive_c/Programs/Avidemux/plugins/videoFilter directory with other video filters (dlls) 
It doesn't show up.

???? 

Thanks!

---

### Post by flemur13013 on 2012-01-31
- bump -

---

### Post by xubunt on 2012-03-08
What is your wine version?
Does Avidemux run under wine without any errors?

---

### Post by flemur13013 on 2012-03-09
$ wine --version = wine-1.4-rc6

I get the below errors from any sound app w/wine, but they all work fine including avidemux:

```
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
ALSA lib pcm_pulse.c:1008:(_snd_pcm_pulse_open) Unknown field handle_underrun
err:winediag:AUDDRV_GetAudioEndpoint PulseAudio "default" -22 without handle_underrun. Audio may hang. Please upgrade to alsa_plugins >= 1.0.24
```

---

### Post by xubunt on 2012-03-31
$ wine --version = wine-1.4

I get the below errors - Avidemux does not start and crashes:

err:seh:setup_exception_record stack overflow 832 bytes in thread 0009 eip 7bc3f2c8 esp 01280ff0 stack 0x1280000-0x1281000-0x1480000

---


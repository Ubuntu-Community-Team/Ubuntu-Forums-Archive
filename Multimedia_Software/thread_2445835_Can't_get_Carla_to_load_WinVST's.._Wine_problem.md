---
title: "Can't get Carla to load WinVST's.. Wine problem?"
date: 2020-06-20
forum: Multimedia Software
---

### Post by sixstring.psycho on 2020-06-20
Hello,
First I am fairly new to this forum and hope I am posting in the correct section.
I am running Ubuntu 18.04 with the latest KxStudio repo and Using Carla  version 2.1.1. Not the Carla-Git When I scan for Windows VSTs nothing comes up. I was able  to load 32-bit VSTs in the past but now it will not show any Win VSTs  after I Refresh. Maybe something I did or a conflict with another  program? But I have been searching through this forum and googling it  for 2 days now and cannot seam to resolve the problem. I am sure I have  all of the correct bridges?

> [INDENT]carla-bridge-linux32: audio plugin host (linux32 bridge)
carla-bridge-linux64: audio plugin host (linux64 bridge)
carla-bridge-win32: carla win32 bridge
carla-bridge-win64: carla win64 bridge
carla-bridge-wine32: carla win32 bridge (wine DLL)
carla-bridge-wine64: carla win64 bridge (wine DLL)

[/INDENT]
Under *Search for new...* the *Windows 32bit and Windows 64bit* is checked along with *VST3*.
 Under 'Available tools' '*carla-discovery-native  carala-discovery-posix32 carla-discovery-win32 carla-disocvery-win64  and python3-rdflib (LADSPA-RDF support)*' are all (green) check marked. And I am able to scan and discover the [I]Internal, LADSPA, LV2, and VST2 plugins but not VST3 
[/I]
Here are the messages in the *Logs* of Carla:
[I]> ======= Starting engine =======
======= Engine started ========
Carla engine started, details:
  Driver name:  JACK
  Sample rate:  44100
  Process mode: Single client
Gtk-Message: 22:32:48.893: GtkDialog mapped without a transient parent. This is discouraged.
error: failed to expand CURIE *`foaf:Person'*
wine: '/home/thomas/.wine' is a 64-bit installation, it cannot be used with a 32-bit wineserver.[/I]

So to me it has something to do with wine obviously. But seriously I do  not have much knowledge of wine. Is anyone else getting this  error/problem with Kxstudio winvst's? Or does anyone have any idea of what went wrong?

If any other information is needed just let me know.

Any help is appreciated

**SOLVED**

> I posted this same problem in linuxmusicians forum and found a solution with a bit of help. And as I suspected, it had to do with wine.
I renamed .wine to .wine.bak and ran the wineprefix command and started over. but first I read this: [https://linuxconfig.org/configuring-win ... troduction]("https://linuxconfig.org/configuring-wine-with-winetricks#h1-introduction")  to get a little understanding of what I was doing. I don't know what  messed it all up in the first place, but after going through the steps in the link I  started Carla up and Refreshed! BAM! There they were! I got WinVST back  again!

                                                                                                                                                                                   [                                  Top             ]("https://linuxmusicians.com/viewtopic.php?f=47&t=21656&p=120460#top")

---


---
title: "Fade to Black, DVD playback and, WriteAudio: buffer underrun"
date: 2009-06-07
forum: Mythbuntu
---

### Post by Al_Vampyre on 2009-06-07
I'm really happy with my Mythbuntu setup apart from these three little niggles, still on Intrepid but just about to update to Jaunty in the next couple of days so I have time to tinker with my system if anyone can help.

Fade to Black - Just noticed this one (or rather the other half did!!) at some point in the last couple of days one of the updates seems to cause live TV to fade to black after a few minutes (almost like a screensaver)unfortunately the only way to get it back is to Ctrl-Alt-Backspace. Doesn't seem to happen whilst watching recorded/video just liveTV.

DVD Playback - Using the internal player I get jerky video (audio is fine) usually only happens when there is movement on the screen (or panning) makes watching somebody walk down the street look like a 1920's B&W movie...movement will stop briefly then a flurry of movemnet as the system re-syncs. Is there anyway of curing this that isn't going to affect the WAF too much?

WriteAudio: Buffer Underruns - This one had me puzzled for a while because I couldn't understand it. It was only when I started to 'tail' my Mythfrontend log on the laptop whilst watching TV that I saw what was happening. Happens on liveTV and on recordings and most of the time is pretty much unnoticeable until certain things are going on onscreen. It gets very noticeable and very annoying when display changes from a 'normal' broadcast picture to anything that is animated or CGI. E.g. Yesterday I was watching D-Day to Berlin on the History channel (UK DVB-T), everything was fine until the program cut from footage of the Normandy landings to a graphic of a map of Europe with lines on it showing the advances of different units, the sound break up really became annoying, it then switched back to footage and everything went back to normal. It also happens at the end of programs, switching from normal footage to the credits etc.  The mythtv-frontend log shows WriteAudio:Bufferunderrun, CPU usage stays within normals limits as I was monitoring 'top' at the same time. Switching on the 'Aggresive Souncard Buffering' option in the Frontend setup makes the problem worse.

Combined BE/FE on an Opteron 165 with 4Gb RAM on an Asrock 939N68PV-GLAN (NVIDIA® GeForce 7050 / nForce 630A MCP Chipsets)running 0.21+fixes on Intrepid and any help or advice would be greatly appreciated.

---

### Post by Al_Vampyre on 2009-06-10
OK, quick update (and shameless bump!) I have sorted the fade to black issue by playing around with the screensaver settings (should have thought of that myself to be honest)

By searching about I gather that I may be able to sort the dvd playback by using Xine as the default player in Mythbuntu - is there any reason not to? Specifically anything that will affect the WAF??

Does anyone have any idea about the WriteAudio: Buffer Underruns? Any settings I can play with?

---


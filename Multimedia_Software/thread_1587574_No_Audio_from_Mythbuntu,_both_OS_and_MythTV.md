---
title: "No Audio from Mythbuntu, both OS and MythTV"
date: 2010-10-03
forum: Multimedia Software
---

### Post by aperifanos on 2010-10-03
[COLOR=black][FONT=Arial]**Hi,**[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]**I’m new to Linux. I’m having issues getting sound to come out of my mythbuntu box.**[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]**[[COLOR=#800080]http://ubuntuforums.org/showthread.php?t=1577126[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1577126") (original thread)**[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]**My hardware is a follows**[/FONT][/COLOR]
 
[COLOR=black][FONT=Arial]**CPU Intel duo core i5**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**Motherboar GA-G41MT-D3 (onboard video and sound disabled)**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**TV Tuner DIVCO Fusion HDTV Dual Digital 4**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**Video 512MB Gygabyte NVIDIA**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**Sound Card Creative**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**RAM 2GB**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**HD Western Digital 4TB**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**DVDR LG**[/FONT][/COLOR]
[COLOR=black][FONT=Arial]**Case Cooler master**[/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]Originally I wanted to use on board sound. The computer shop where I bought the components from assured me that the onboard sound (Realtek) on the motherboard is compatible with Linux and would work out of the box.[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]I installed Mythbuntu 10.04, the system was working including TV tuner card, except I couldn’t get any audio, either from Myth TV, or the normal operating system. I spent many hours, trying to get it to work with no success. [/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]On the weekend, I took it back to the computer shop for assistance. He spent 2 hours on it without any success either. From the desktop, when I attempted to launch - Applications - Multimedia - Mixer. I got the following error message "GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem"[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]The computer shop gave me an second hand creative sound card, he said that these sound cards are guaranteed to work with Linux. He also told me that I would need to re-install Mythbuntu with the sound card installed in order for it to detect and install the correct drivers.[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]I noticed that there was a new version of Mythbuntu, v 10.10, so I downloaded and installed the latest version. It looks like the operating system detected the creative sound card, when I go to the desktop, Applications - Multimedia – Mixer – I now have sound controls, where I can adjust the volume and unmute etc..[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]From MythTV front-end / setup / general, I changed the setting to ALSA default and tested, however I still have the same issue, no sound. I then tried ALSA analogue, digital, Jack and every other possible option, without any success. [/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]I thought I needed to isolate the issue, so I decided to see if I could get audio from the operating system[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]I then closed down MythTV, and went back to the operating system. From the terminal window, I tried to launch alsamixer by typing in “alsamixer” in the terminal window, however I got this error message “antonios@Mythbuntu:~$ alsamixercannot load mixer controls: Invalid argument”[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]I downloaded all updates via update manager. Launched Firefox, and attempted to listen to audio via firefox / you tube. After installing the relevant Adobe flash plug-in, the you tube video played successfully, however I still cannot get any audio.. Very frustrating….[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]The speakers definitely work, as I use them on my Windows 7 laptop[/FONT][/FONT][/COLOR]
 
[COLOR=black][FONT=Calibri][FONT=Calibri]I’m not sure what else to try, is anyone able to assist me? Surely it’s a setting right? [/FONT][/FONT][/COLOR]

---


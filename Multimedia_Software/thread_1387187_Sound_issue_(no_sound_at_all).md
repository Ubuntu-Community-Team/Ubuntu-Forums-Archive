---
title: "Sound issue (no sound at all)"
date: 2010-01-21
forum: Multimedia Software
---

### Post by sirspartan on 2010-01-21
Hi I just recently installed ubuntu  (two days ago).  Everything is working as expected, except the sound.  For one reason or another I cant get any sound at all.  So I searched around a little on my computer and noticed that sound devices were not enabled for this computer.  So I turned it on and still got nothing.  Then I went through the comprehensive guide to fix sound and still nothing.  Although Alsa did not have my exact audio sound card (HDA ATI and Intel) it did have the generic one, so I tried that.  Nothing.  I was wondering if anyone knows a solution to get my sound cards to work.  Im posting them up here.  A in depth description of what to do would be appreciated because im a newb to this OS


0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2400000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2310000 irq 19

by the way my computer is a 64 bit if that matters

---

### Post by mörgæs on 2010-01-21
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by garvinrick4 on 2010-01-22
This has worked for me on three installs. Make sure your backports are checked in Software Sources. Then make sure you reboot when done, just takes a minute.                           [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][SIZE=4]**Part A: Common instructions (Hardy, Intrepid, Jaunty & Karmic)**[/SIZE]
*All users must must follow the steps in this section to guarantee a fully working PulseAudio configuration.*

1. Backup (and then delete) your previous configuration files: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ rm -r ~/.pulse ~/.asound* [/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo rm /etc/asound.conf[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#ff0000]**Warning:**[/COLOR][COLOR=#ff0000] As always, use caution when removing files on your system. Any typos can potentially cause data loss.[/COLOR]
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Don't worry if some of these files did not exist on your system.[/COLOR]


2. Ensure you have the necessary PulseAudio libraries and configuration utilities installed:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000] [FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio[/SIZE][/FONT][/COLOR] [[COLOR=#444444][FONT=Verdana, Arial, Tahoma][SIZE=2]_3_[/SIZE][/FONT][/COLOR]]("https://bugs.launchpad.net/bugs/192888")[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]. Ensure the evil "libflashsupport" library is [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]**not**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2] installed: [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks![/COLOR]

4. (Karmic users - please skip this step, it's not necessary). Open System/Preferences/Sound. In the Devices section, ensure that all "Sound playback" options are set to Autodetect. Set the "Sound capture" item to "ALSA", or the appropriate hardware definition. Close the application when you're finished.
[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] Choosing PulseAudio for sound capture may result in crashes, so you are advised to choose the "direct" ALSA device instead.[/COLOR]

5. Open the PulseAudio Volume Control application ("pavucontrol", or you can launch "Applications/Sound & Video/PulseAudio Device Chooser" and select Volume Control from this applet's menu). In the Output Devices section you will see a listing of the playback devices available on your system. Right-click on the entry that you desire to be made the default playback device on your system and enable the "Default" checkmark. Similarly, navigate to Input Devices, then right-click on the device you wish to set as your default input device (microphone), and ensure the "Default" setting is checked. Close the application when you're finished.

[COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] If you are greeted with the error "Connection failed: Connection refused", manually launch PulseAudio before opening the PulseAudio Volume Control application:[/COLOR][/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ pulseaudio & pavucontrol[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]6. Ensure that your sound card's PCM mixer is not muted or set to 0% volume (this appears to be a common bug in Intrepid and Jaunty):[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Code:[/SIZE][/FONT][/COLOR]
 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]$ alsamixer [COLOR=#0000ff]-Dhw[/COLOR][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][COLOR=#0000ff]**Note:**[/COLOR][COLOR=#0000ff] When the PulseAudio ALSA plugins are active, you must explicitly specify your hardware device in alsamixer (marked in blue above), otherwise it will open the PulseAudio mixer.[/COLOR]

7. Continue to **Part B** if you are running Hardy Heron (8.04), or **Part C** if you are running Intrepid Ibex (8.10). If you are running Karmic Koala (9.10) or Jaunty Jackalope (9.04), you're finished - log out and back in for changes to take effect![/SIZE][/FONT][/COLOR]

---


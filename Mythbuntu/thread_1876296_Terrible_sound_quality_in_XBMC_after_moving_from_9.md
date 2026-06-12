---
title: "Terrible sound quality in XBMC after moving from 9.10 to 11.10?"
date: 2011-11-06
forum: Mythbuntu
---

### Post by minneyar on 2011-11-06
In a nutshell, I've got a Mythbuntu box that's been running 9.10 for a few years, so I decided to give 11.10.  I installed it on a second hard drive so I could switch between 9.10 and 11.10, but they're otherwise running on the exact same hardware.  My problem is that when playing movies in XBMC in 11.10, the sound quality is *awful*.  It's possible to make out the original sounds, but they're very garbled and scratchy.  I can boot back into 9.10 and everything sounds fine.  Any ideas what might be going on?

Just for reference, the box has a 2.5 GHz Core 2 Duo CPU, 2 GB of RAM, and I'm using the 64-bit version of Mythbuntu in both cases.  The motherboard has an integrated GeForce 7100 video chipset (not super awesome, but good enough), and I'm displaying audio & video over HDMI connected to an HDTV.  I I've got a Hauppauge 350 encoder card (which was a huge pain to get set up in 11.10, by the way...), but I don't think that's relevant, as I still get bad sound quality if I'm playing .mkv files or videos on Youtube.

In both OS's, I'm using the latest XBMC pulled and compiled from the official git repository.  Also, like I mentioned earlier, I didn't upgrade to 11.10, I did a fresh install of it on a new hard drive so that I could dual boot between it and 9.10 until everything is working.  As far as I can tell, their configurations are identical, so I really don't know why things sound great in 9.10 but not in 11.10.

---

### Post by donb21 on 2011-11-06
[FONT=Verdana][SIZE=2]First, th[/SIZE][/FONT][FONT=Verdana][SIZE=2]e disclaimer; I'm a novice in audio, but I do have a couple of things to try.  It sounds a little like it's not using what we think it's using.  Try some of these

Note - These steps are from a procedure on setting up hdmi:
[http://ubuntuforums.org/showthread.php?t=1842439](http://ubuntuforums.org/showthread.php?t=1842439)

 [/SIZE][/FONT][FONT=Verdana][SIZE=3][FONT=Calibri]4. Identify the audio hardware with "aplay -l"[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ aplay -l[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]**** List of PLAYBACK Hardware Devices ****[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 0/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0][/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]I'm interested in the HDMI audio hardware, so the devices to consider are card 1, device 3, 7, 8, or 9.[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]5. Make sure the HDMI cable is connected from the PC to the TV (mine is plugged into HDMI input #4.).  Now we'll test for which HDMI ports gives us sound. From the list above, we'll test card 0 with device 3 (just doing 0,3 to see what it does), then card 1 with each device: (replace the "plughw:x,y with whatever is in your list)[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Left.wav[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Left.wav[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Left.wav[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,8 /usr/share/sounds/alsa/Front_Left.wav[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]
[/SIZE][/FONT] [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Left.wav[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]Note – Before you do these tests, make sure the channel is not muted in the mixer:[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]don@zedo:~$ alsamixer[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=3]

[/SIZE][/FONT]  [FONT=Verdana][SIZE=3][FONT=Calibri]…then press F6 to display the Nvidia channels.  Each “S/PDIF” channel should be “00”, not “MM”.  Press “M” to switch it.  Also check the master volume while you’re there.[/FONT][/SIZE][/FONT]

---

### Post by nickrout on 2011-11-07
This is not an xbmc forum, I suggest you ask on the official xbmc forum.

---


---
title: "Setting up HDMI audio on the GT220 (MythBuntu 11.04)"
date: 2011-09-11
forum: Mythbuntu
---

### Post by donb21 on 2011-09-11
[SIZE=3][FONT=Calibri]The MythDora developers have decided to get out of the MythTv installation business (their effort were highly appreciated), so I&#8217;m switching-over to MythBuntu.  It took a while to get this combination working in MythDora (earlier version) and I&#8217;m using some of the same methods here.  This is how we did it (I had a lot of help from other forum users):[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]This is a link to the MythDora write-up on the same subject:[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri][http://mythdora.com/?q=node/5528](http://mythdora.com/?q=node/5528)[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]This is an excellent write-up on the nVidia HDMI audio.  [/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri][http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240]("http://wiki.xbmc.org/?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210%2C_GT220%2C_or_GT240")[/FONT]



[/SIZE]      [SIZE=3][FONT=Calibri]This write-up assumes you have the video board installed and the HDMI video is working (but not the audio).[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]**1. **Verify the minimum version of alsa is installed:[/FONT]

[/SIZE][SIZE=3][FONT=Calibri] don@zedo:~$ cat /proc/asound/version[/FONT]
[/SIZE][SIZE=3][FONT=Calibri]Advanced Linux Sound Architecture Driver Version 1.0.24.[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]Compiled on Aug 25 2011 for kernel 2.6.38-11-generic-pae (SMP).[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]don@zedo:~$[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Or, you can run alsa-info.sh to get the full report:[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]don@zedo:~$ sudo /home/don/alsa-info.sh[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]alsa-info.sh generates a long list of information; this is the part with the version:[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]!!ALSA Version[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]!!------------[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Driver version:     1.0.24[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]Library version:    1.0.24.1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]Utilities version:  1.0.24.2[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]As I recall, "alsa-driver-**1.0.23**.tar.bz2" was the first version that included audio encoding on the Nvidia GT220 card.  This version looks good, on to the next step.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Note - From the xbmc.org; the following command would load the drivers if they were not the current revision.  When I ran it, the installer reported the latest available versions were already installed. [/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]don@zedo:~$ sudo [/FONT][FONT=Calibri]apt-get install alsa-base alsa-utils linux-alsa-driver-modules-$(uname -r)[/FONT]


[/SIZE]         [SIZE=3][FONT=Calibri]**2. **Add the driver to /etc/modprobe.d/alsa-base.conf (in MythDora, it was dist-alsa.conf)[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- open alsa-base.conf with an editor[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- add this line to the end of the file[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]options snd-hda-intel enable_msi=0[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Note - Refer to the xbmc.org HOW-TO for details on forming the final command, including the probe_mask , but do this first.  The site also has a list of video boards and associated &#8220;options &#8230;&#8221; lines.  [/FONT][FONT=Calibri]This is the line for &#8220;[/FONT][FONT=Calibri]Any GT210/GT220/GT240&#8221; (mine was by Zotac).[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Note - We removed the "probe_mask" portion of the command in order to see all the audio hardware.  As I recall, using the mask was kinda optional, so we ended up leaving it off altogether.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]**3.** Reboot the box to make the driver take effect.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]**4.** Identify the audio hardware with "aplay -l"[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -l[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]**** List of PLAYBACK Hardware Devices ****[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 0/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0][/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevices: 1/1[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]  Subdevice #0: subdevice #0[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]I'm interested in the HDMI audio hardware, so the devices to consider are card 1, device 3, 7, 8, or 9.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]**5.** Make sure the HDMI cable is connected from the PC to the TV (mine is plugged into HDMI input #4.).  Now we'll test for which HDMI ports gives us sound. From the list above, we'll test card 0 with device 3 (just doing 0,3 to see what it does), then card 1 with each device: (replace the "plughw:x,y with whatever is in your list)[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:0,3 /usr/share/sounds/alsa/Front_Left.wav[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Left.wav[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Left.wav[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,8 /usr/share/sounds/alsa/Front_Left.wav[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Left.wav[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Note &#8211; Before you do these tests, make sure the channel is not muted in the mixer:[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]don@zedo:~$ alsamixer[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]&#8230;then press F6 to display the Nvidia channels.  Each &#8220;S/PDIF&#8221; channel should be &#8220;00&#8221;, not &#8220;MM&#8221;.  Press &#8220;M&#8221; to switch it.  Also check the master volume while you&#8217;re there.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]**6. **Mine had sound on card 1, device 7. As soon as it worked, other devices seemed to start working. I selected 1,7 to use on MythTv.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]Note - I tried this test prior to adding the option line to &#8220;/etc/modprobe.d/alsa-base.conf&#8221; and received an error (don't recall what it was).  It was solved when we added the driver option line.  When you do the test, it should look like this: (plays for a few seconds then returns to a prompt)[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]don@zedo:~$ aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Left.wav[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]Playing WAVE '/usr/share/sounds/alsa/Front_Left.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]don@zedo:~$[/FONT]


[/SIZE]         [SIZE=3][FONT=Calibri]**7.** Add the audio selection to the MythTv setup.  From the first MythBuntu menu, select:[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Utilities / Setup > Setup > General > Hit &#8220;Next&#8221; until you access the &#8220;Audio System&#8221; Menu[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press up-arrow to access &#8220;Scan for audio devices&#8221; and press enter. (give it a second to run)[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;Audio output device&#8221;[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press right-arrow to scroll through audio selections.[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- I selected &#8220;ALSA:plughw:CARD=NVIDIA,DEV=7&#8221;[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;Next&#8221;[/FONT][/SIZE][SIZE=3][FONT=Calibri].  Continue to press &#8220;Next&#8221; to finish the set-up.[/FONT]
[/SIZE][SIZE=3][FONT=Calibri]- Exit the setup menus and try to play a recording.  Be careful, the mixer may be at 100% volume.[/FONT]

[/SIZE]      [SIZE=3][FONT=Calibri]**8. **I also found that I had to set the mixer control to &#8220;Software&#8221; in order to use the volume control buttons on my remote control.  These are the settings I used.  From the first MythBuntu menu, select:[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Utilities / Setup > Setup > General > Hit &#8220;Next&#8221; until you access the &#8220;Audio Mixer&#8221; menu.[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press up-arrow to access &#8220;Use internal volume controls&#8221;.  Press &#8220;right-arrow&#8221; to check the box.[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;Mixer device&#8221; and select &#8220;Software&#8221;[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;Mixer controls&#8221; and &#8220;Master&#8221;[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;Master mixer volume&#8221; and set it to &#8220;25%&#8221;.  Your mileage may vary; In MythDora, this was set to 100%, I had to turn this down on this setup [/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;PCM mixer volume&#8221; and set it to &#8220;2%&#8221;.  Note - I&#8217;m not sure how this setting affects the volume.[/FONT]
[/SIZE]   [SIZE=3][FONT=Calibri]- Press down-arrow to access &#8220;Next&#8221;.  Continue to press &#8220;Next&#8221; to finish the set-up.[/FONT]
[/SIZE]

---


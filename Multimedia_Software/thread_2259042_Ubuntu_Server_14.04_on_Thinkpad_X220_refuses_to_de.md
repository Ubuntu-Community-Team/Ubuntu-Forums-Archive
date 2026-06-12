---
title: "Ubuntu Server 14.04 on Thinkpad X220 refuses to deliver bits to the DAC/AMP over USB"
date: 2015-01-01
forum: Multimedia Software
---

### Post by mark183 on 2015-01-01
Hi forum,



trying to turn an old Lenovo Thinkpad into a headless music server/player. Desired set-up:



LMS > SqeezeLite > ALSA > (USB) > DAC/AMP (NAD C390DD)



Linux Distribution: Ubuntu 14.04.1 LTS
     Kernel release:    3.13.0-43-generic
ALSA Version:

     Driver version:     k3.13.0-43-generic

     Library version:    1.0.27.2

     Utilities version:  1.0.27.2



Soundcards recognised by ALSA:

[FONT=Andale Mono]0 [PCH              ]: HDA-Intel - HDA Intel PCH[/FONT]

[FONT=Andale Mono]                       HDA Intel PCH at 0xf2520000 irq 43[/FONT]

[FONT=Andale Mono] 1 [Audio            ]: USB-Audio - NAD USB Audio[/FONT]

[FONT=Andale Mono]                       NAD Electronics NAD USB Audio at usb-0000:00:1a.0-1.1.4, full speed[/FONT]

[FONT=Andale Mono]29 [ThinkPadEC      ]: ThinkPad EC - ThinkPad Console Audio Control[/FONT]

[FONT=Andale Mono]                       ThinkPad Console Audio Control at EC reg 0x30, fw unknown[/FONT]



Pulseaudio is not installed on the box:

```


[FONT=Andale Mono]mark@x220:~$ killall pulseaudio[/FONT]

[FONT=Andale Mono]pulseaudio: no process found[/FONT]

[FONT=Andale Mono]mark@x220:~$[/FONT]


```

 



aplay -l returns:

```


[FONT=Andale Mono]mark@x220:~$ [COLOR=#9B288E]**aplay -l**[/COLOR][/FONT]

[FONT=Andale Mono]aplay: device_list:268: no soundcards found...[/FONT]

[FONT=Andale Mono]mark@x220:~$[/FONT]


```

 


And:

```


[FONT=Andale Mono]mark@x220:~$ **[COLOR=#9B288E]alsamixer -c 1[/COLOR]**[/FONT]

[FONT=Andale Mono]invalid card index: 1[/FONT]

[FONT=Andale Mono]try `alsamixer --help' for more information[/FONT]

[FONT=Andale Mono]mark@x220:~$[/FONT]

[FONT=Andale Mono]mark@x220:~$ [COLOR=#9B288E]**speaker-test -D plughw:1,0 -c 2**[/COLOR][/FONT]

[FONT=Andale Mono]speaker-test 1.0.27.2[/FONT]

[FONT=Andale Mono]Playback device is plughw:1,0[/FONT]

[FONT=Andale Mono]Stream parameters are 48000Hz, S16_LE, 2 channels[/FONT]

[FONT=Andale Mono]Using 16 octaves of pink noise[/FONT]

[FONT=Andale Mono]ALSA lib pcm_hw.c:1667:(_snd_pcm_hw_open) Invalid value for card[/FONT]

[FONT=Andale Mono]Playback open error: -2,No such file or directory[/FONT]

[FONT=Andale Mono]mark@x220:~$[/FONT]


``` 





Step 3 of the Sound Troubleshooting Procedure: result from the diagnostics can be found here:

[http://www.alsa-project.org/db/?f=a2960d326e019c20d5b70c6b9944fbb66a79d231](http://www.alsa-project.org/db/?f=a2960d326e019c20d5b70c6b9944fbb66a79d231)



Any hint where and how I should continue?



Thanks & BR

Mark

---


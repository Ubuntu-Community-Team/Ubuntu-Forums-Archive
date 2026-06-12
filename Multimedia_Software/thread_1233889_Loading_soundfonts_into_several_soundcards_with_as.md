---
title: "Loading soundfonts into several soundcards with asfxload"
date: 2009-08-07
forum: Multimedia Software
---

### Post by Laurent COLLET on 2009-08-07
Hi,
I have 3 Creative soundcards (2 x Audigy 1, 1 x Audigy 2 ZS) installed and running under Ubuntu 9.04.  I need to load into these 3 cards their respective 3 soundfonts. Using  asfxload, I have been able to load one soundfont into one the cards ; in order to load the 3 soundfonts, I understand that the parameter -D must be entered :
       **-D,** **--hwdep=***name* (asfxload only)
              Specify the hwdep name to be used.  As default,  asfxload  seeks
              until any Emux compatible hwdep device is found.

My question is : How can I know the hwdep values of my 3 soundcards ?
Thanks for your help

---

### Post by Laurent COLLET on 2009-08-08
The solution was :
1/ list the devices with amidi :
  	 	 	 	 	 	  [FONT=Nimbus Sans L, sans-serif][SIZE=2]**amidi -l **[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]Dir Device    Name [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:0,0    Audigy MPU-401 (UART) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:0,1    Audigy MPU-401 #2 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:0,2    Emu10k1 Synth MIDI (16 subdevices) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:0,3    Emu10k1 Synth MIDI (16 subdevices) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:1,0    Audigy MPU-401 (UART) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:1,1    Audigy MPU-401 #2 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:1,2    Emu10k1 Synth MIDI (16 subdevices) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:1,3    Emu10k1 Synth MIDI (16 subdevices) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:2,0    Audigy MPU-401 (UART) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:2,1    Audigy MPU-401 #2 [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:2,2    Emu10k1 Synth MIDI (16 subdevices) [/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=2]IO  hw:2,3    Emu10k1 Synth MIDI (16 subdevices)[/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]Column 2 contains the hwdep parameters needed by asfxload.[/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]
[/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=2]2/the soundfonts are loaded with asfxload, as follows :[/SIZE][/FONT]


   	 	 	 	 	 	  [FONT=Nimbus Sans L, sans-serif][SIZE=2]laurent@PCORGUE:~$ asfxload  -Dhw:0,2 /home/laurent/Orgue/ACO3_0.sf2 [/SIZE][/FONT]
 [FONT=Nimbus Sans L, sans-serif][SIZE=2]laurent@PCORGUE:~$ asfxload  -Dhw:1,2 /home/laurent/Orgue/ACO3_0.sf2 [/SIZE][/FONT]
 [FONT=Nimbus Sans L, sans-serif][SIZE=2]laurent@PCORGUE:~$ asfxload  -Dhw:2,2 /home/laurent/Orgue/ACO3_0.sf2[/SIZE][/FONT]

---

### Post by ggoodesa on 2010-01-15
Hi Laurent,

Thanks for posting this. Have you tried the more recent jOrgan Creative Extension for Linux yet? I'm attempting to use it with the ACO and have only been succesful with loading one sf2 into a card, not two...

GrahamG

---


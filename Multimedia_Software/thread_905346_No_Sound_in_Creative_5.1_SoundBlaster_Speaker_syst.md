---
title: "No Sound in Creative 5.1 SoundBlaster Speaker system"
date: 2008-08-30
forum: Multimedia Software
---

### Post by srivboopathi on 2008-08-30
[SIZE="4"]**Hi i am new to ubuntu Linux. I have installed ubuntu8.04 in my 32 bit PC. I am having the following problem with my 5.1 speaker system. Appreciate your help in solving these problem.**[/SIZE]

[COLOR="Red"][SIZE="4"]1. No sound in my 5.1 sound blaster speakers. :( [/SIZE][/COLOR]
[COLOR="Blue"][SIZE="2"]Action performed:
The PC had two ordinary stereo speakers while installing ubuntu in my machine. The sound in those 2 speakers were good. Recently i removed those ordinary speakers and added a new "5.1 speaker system" and a "Sound Card" to my PC. The details about speaker and sound card are as provided below...
Speaker = Inspire M5300
SoundCard = Sound Blaster® 5.1
Problem:
The 5.1 speaker system does not function properly, out of 5 speakers and a sub woofer only 2 Front Speakers and sub woofer is producing sound. there is no sound in remaining three speakers( 1 middle and 2 Rear speakers. :( )

I noticed a strange behavior that even the front two speakers doesn't produce sound when i play different media files in different players. This gets solved when i change the audio playback setting to "ALSA output" or "Auto detect" setting under "Administration > Sound" menu. (currently i switch b/w "ALSA output" and "Auto detect" whenever i get no sound in front 2 speakers)
[/SIZE]
[/COLOR]

[COLOR="Blue"]
[SIZE="4"]PC Configuration:[/SIZE]
INTEL dual core processor,
INTEL 945 Mother board,
250 GB hard disk,
CREATIVE SOUND BLASTER 5.1 SOUND CARD INSTALLED,
Other Operating System Installed: WINDOWS XP Professional.[/COLOR]

---

### Post by nightwolf2k5 on 2008-08-30
Hi,
Well i have a similar problem with my 6.1 Creative Inspire speakers. I tried a lot of things, but could not get the other speakers to work.
I came across this link: 
[http://georgia.ubuntuforums.com/showthread.php?t=39920](http://georgia.ubuntuforums.com/showthread.php?t=39920)

Though it worked for him, it didn't work for me. So you might want to try your luck following this.

---

### Post by srivboopathi on 2009-04-02
> **nightwolf2k5 said:**
> Hi,
Well i have a similar problem with my 6.1 Creative Inspire speakers. I tried a lot of things, but could not get the other speakers to work.
I came across this link: 
[http://georgia.ubuntuforums.com/showthread.php?t=39920](http://georgia.ubuntuforums.com/showthread.php?t=39920)

Though it worked for him, it didn't work for me. So you might want to try your luck following this.
hi friend, i tried this link but it dint work for me :(

---

### Post by Einstein86 on 2010-06-11
hello sir, ihave just the same problem with my 5.1 system. i recovered that link's not valid, in fact he misspelled something from it. i change it in valid ;) 

[http://georgia.ubuntuforums.org/showthread.php?t=39920](http://georgia.ubuntuforums.org/showthread.php?t=39920) :)

it's same just domen suppose to be .org

good luck in searching

---

### Post by lidex on 2010-06-13
> **srivboopathi said:**
> [SIZE="4"]**Hi i am new to ubuntu Linux. I have installed ubuntu8.04 in my 32 bit PC. I am having the following problem with my 5.1 speaker system. Appreciate your help in solving these problem.**[/SIZE]

[COLOR="Red"][SIZE="4"]1. No sound in my 5.1 sound blaster speakers. :( [/SIZE][/COLOR]
[COLOR="Blue"][SIZE="2"]Action performed:
The PC had two ordinary stereo speakers while installing ubuntu in my machine. The sound in those 2 speakers were good. Recently i removed those ordinary speakers and added a new "5.1 speaker system" and a "Sound Card" to my PC. The details about speaker and sound card are as provided below...
Speaker = Inspire M5300
SoundCard = Sound Blaster® 5.1
Problem:
The 5.1 speaker system does not function properly, out of 5 speakers and a sub woofer only 2 Front Speakers and sub woofer is producing sound. there is no sound in remaining three speakers( 1 middle and 2 Rear speakers. :( )

I noticed a strange behavior that even the front two speakers doesn't produce sound when i play different media files in different players. This gets solved when i change the audio playback setting to "ALSA output" or "Auto detect" setting under "Administration > Sound" menu. (currently i switch b/w "ALSA output" and "Auto detect" whenever i get no sound in front 2 speakers)
[/SIZE]
[/COLOR]

[COLOR="Blue"]
[SIZE="4"]PC Configuration:[/SIZE]
INTEL dual core processor,
INTEL 945 Mother board,
250 GB hard disk,
CREATIVE SOUND BLASTER 5.1 SOUND CARD INSTALLED,
Other Operating System Installed: WINDOWS XP Professional.[/COLOR]

Why are you running those commands as root? That can actually cause problems due to permissions. Use a terminal in user-mode for this next bit.
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---


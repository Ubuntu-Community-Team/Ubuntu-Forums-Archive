---
title: "How to use Line-In for Surround Speakers"
date: 2010-03-27
forum: Multimedia Software
---

### Post by sosaited on 2010-03-27
I have Asus P5GL-MX board with Intel HD Audio (AD1986a). It supports 5.1 surround sound, but it has only 1 stereo output jack, and the line-In and Microphone jacks are used for Read/Centre speakers. 

In Windows, the SoundMax panel automatically pops up whenever I plug in anything, asking what I plugged in what jack, and changing the output profile for that. For the moment I have 4.1 speakers, so I use the green Line-out jack for Front speakers, and Blue Line-In Jack for Rear speakers.

I have been trying to find a way to make this work in Ubuntu Karmic for almost 20 days now, but none of the threads seemed to provide an answer. I have done all the usual tweaking/settings, but I still don't see Surround or 4.1 option in the Sound preferences panel.

Can someone please give any tips how this can be done.

---

### Post by lyall on 2010-03-27
SurroundSound in Community Documentation
[https://help.ubuntu.com/community/SurroundSound]("https://help.ubuntu.com/community/SurroundSound")

also install Gnome Alsa Mixer (alsamixergui) it is in Synaptic Package Manuager.  It shows you all the sound settings.

good luck and have fun learning

---

### Post by sosaited on 2010-03-27
As I mentioned before, I have tried everything I found on the forums etc, including the editing of daemon file and alsa gui mixer.

In the GUI mixer, I already have options for LFE, Centre and Surround (Although I only set 4 speakers, so Centre is not needed), and they are all turned to full, I still only get sound from front two speakers.

The problem most likely is that I have to set in some configuration that Line-in Jack is to be used to output the Rear Speakers.

---

### Post by kpsg25690 on 2010-05-03
I have the same problem and I've been trying to find out a working solution but can't..

---

### Post by mr_hide3 on 2010-06-02
same problem here , i have tried EVVVerything there is to try ,
looked through every forum and irc channel there's to look in . only way that worked for some is the famous  modifying of /etc/modprobe.d/alsa-base
added : options snd-hda-intel model=3stack




  enabled4 channel configuration in deamon.conf at pulse

and still no use:confused:


the sound preference don't even have an option for surround , so i  figured then the problem is more in the driver itself not in alsa or pulse configuration 
so ,upgraded the kernel , tried out older drivers , newer drivers and nothing

the alsamix is showing sliders for surround speakers , but of course , only the analogue output (i.e. the green jack) that is working

maybe it some sort of a codec missing or a bridge? idk

i found in this link [http://manpages.ubuntu.com/manpages/lucid/man4/snd_hda.4freebsd.html](http://manpages.ubuntu.com/manpages/lucid/man4/snd_hda.4freebsd.html)
a solution for the problem but for freebsd :mad:

anyone have any solution or like to share what they tried and maybe together we would work sth out?

*hopes the original poster of this thread worked something out and would come here to share it*

---

### Post by mr_hide3 on 2010-06-02
i found this :
[http://www.opensound.com/forum/viewtopic.php?f=3&t=3549](http://www.opensound.com/forum/viewtopic.php?f=3&t=3549)
might help
but they are talking about OSS . should i remove alsa and pulse audio and use oss? i'm kinda noob so any help would be really appreciated

---

### Post by mr_hide3 on 2010-06-04
pump
any help of any sort would be greatly appreciated even with the slightest information about the subject
i mean i'm loving ubuntu but i don't wanna lose my sound system over it 
i can't live or work with only 2 speakers working:(

---

### Post by mr_hide3 on 2010-06-08
update : i found this page on the alsaproject >> [http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0](http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0)
although my card ( ad1986 ) isn't listed under  intel8x0  but (ad1985) is. 

i tried what they said , and the outcome was that there was absolutely no sound output , and under sound preferences > hardware tap , there was no sound card listed . it just disappeared


is it something i did wrong? is it that my card is not supported ? then if it's not supported , how come that when i installed the alsa driver package with all cards it worked again???
c'mon people , somebody help =/

---

### Post by mr_hide3 on 2010-06-10
ok , someone please explain this ( i found in alsa-configuration.txt here >>[http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt) )
> AC97 Quirk Option
2039	=================
2040	
2041	The ac97_quirk option is used to enable/override the workaround for
2042	specific devices on drivers for on-board AC'97 controllers like
2043	snd-intel8x0.  Some hardware have swapped output pins between Master
2044	and Headphone, or Surround (thanks to confusion of AC'97
2045	specifications from version to version :-)
2046	
2047	The driver provides the auto-detection of known problematic devices,
2048	but some might be unknown or wrongly detected.  In such a case, pass
2049	the proper value with this option.
2050	
2051	The following strings are accepted:
2052	    - default	Don't override the default setting
2053	    - none	Disable the quirk
2054	    - hp_only	Bind Master and Headphone controls as a single control
2055	    - swap_hp	Swap headphone and master controls
2056	    - swap_surround  Swap master and surround controls
2057	    - ad_sharing  For AD1985, turn on OMS bit and use headphone
2058	    - alc_jack	For ALC65x, turn on the jack sense mode
2059	    - inv_eapd	Inverted EAPD implementation
2060	    - mute_led	Bind EAPD bit for turning on/off mute LED
2061	
2062	For backward compatibility, the corresponding integer value -1, 0,
2063	... are  accepted, too.
2064	
2065	For example, if "Master" volume control has no effect on your device
2066	but only "Headphone" does, pass ac97_quirk=hp_only module option


i'm no tech guy so i don't know where to put these options , or what i'm supposed to do . please help

---

### Post by mr_hide3 on 2010-06-18
pump 
(any input would be helpful)

---


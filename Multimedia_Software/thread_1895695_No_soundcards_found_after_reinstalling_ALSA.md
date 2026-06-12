---
title: "No soundcards found after reinstalling ALSA"
date: 2011-12-15
forum: Multimedia Software
---

### Post by Esix on 2011-12-15
So, I've been with this problem for a week now, and I can't solve it. So I ask politely for your help.

So two weeks ago I wanted to use my headphones to listen to some music. I plugged it in and there was no sound from the headphones, only from the main speakers. I couldn't solve this with the controls so I googled and the best possible solution was to reinstall ALSA. 

After I did this I only got two controls left:
[[IMG]http://img16.imageshack.us/img16/5695/soundcarddamn.png[/IMG]]("http://imageshack.us/photo/my-images/16/soundcarddamn.png/")

Now I only can check for the masters of capture and playback, the other two are GONE. 

So I searched something about getting my sound back. 
aplay -l gets me: ```
aplay: device_list:240: no soundcards found...
```So what did I do:
Reinstalling ALSA again (and again) --> nothing
Installing linux soundcard driver from Lenovo --> nothing
Reinstalling ALSA/sound packages by synaptic package manager --> nothing
Installing extra ALSA software --> nothing
The sticky of Sound troublshooting --> nothing
  
Has anyone some other proposes what I should do, because I'm getting annoyed by this. 

my soundcard is:
```
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
```

alsa info about my laptop:
[http://www.alsa-project.org/db/?f=9cb2a5f60f097aab22f32f8f0313339a3fd3c5f1](http://www.alsa-project.org/db/?f=9cb2a5f60f097aab22f32f8f0313339a3fd3c5f1)

Thanks in advance,
EsixX

---

### Post by Esix on 2011-12-15
by the way 
aplay -l still gives: 
aplay: device_list:240: no soundcards found...

---

### Post by Esix on 2011-12-15
bump

---

### Post by bluexrider on 2011-12-15
have you looked here

```
sudo lshw -C sound
```

---

### Post by Esix on 2011-12-15
Yes, I did:
```

 sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f2800000-f2803fff

```

this is my ALSA info: [http://www.alsa-project.org/db/?f=9cb2a5f60f097aab22f32f8f0313339a3fd3c5f1](http://www.alsa-project.org/db/?f=9cb2a5f60f097aab22f32f8f0313339a3fd3c5f1)

---

### Post by bluexrider on 2011-12-15
> **Esix said:**
> So, I've been with this problem for a week now, and I can't solve it. So I ask politely for your help.

So two weeks ago I wanted to use my headphones to listen to some music. I plugged it in and there was no sound from the headphones, only from the main speakers. I couldn't solve this with the controls so I googled and the best possible solution was to reinstall ALSA. 

After I did this I only got two controls left:


Now I only can check for the masters of capture and playback, the other two are GONE. 

So I searched something about getting my sound back. 
aplay -l gets me: ```
aplay: device_list:240: no soundcards found...
```So what did I do:
Reinstalling ALSA again (and again) --> nothing
Installing linux soundcard driver from Lenovo --> nothing
Reinstalling ALSA/sound packages by synaptic package manager --> nothing
Installing extra ALSA software --> nothing
The sticky of Sound troublshooting --> nothing
  
Has anyone some other proposes what I should do, because I'm getting annoyed by this. 

my soundcard is:
```
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
```alsa info about my laptop:
[http://www.alsa-project.org/db/?f=9cb2a5f60f097aab22f32f8f0313339a3fd3c5f1](http://www.alsa-project.org/db/?f=9cb2a5f60f097aab22f32f8f0313339a3fd3c5f1)

Thanks in advance,
EsixX

When you said you tried to install ALSA again and again. this would result in nothing without removing the package first.

I can see the result. There is NO driver installed. 

just to be clear. 

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```then reinstall
```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

```
lspci -v
```


see if this helps

---

### Post by bluexrider on 2011-12-15
There is a tutorial here:  

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

its older but good info

 				 				**Sound troubleshooting** 			
 			 			 		   		 		 		These two manuals give good advice for solving sound problems:

[Sound Troubleshooting Guide]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit")
(by Lkjoel and Wildmanne39)


[Sound Troubleshooting Procedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")
(by Mark Rijckenberg)

---


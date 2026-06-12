---
title: "snd-cmipci how to load this driver"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by Frogster on 2008-01-10
Evening everyone. I am hoping that someone can advise in newbie how to install this driver cmipc   . As the instructions at: [http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci#Setting_up_modprobe_and_kmod_support](http://www.alsa-project.org/main/index.php/Matrix:Module-cmipci#Setting_up_modprobe_and_kmod_support)  don't seem to work for me. Its probably me mis reading them.

:)

---

### Post by balaknair on 2008-01-10
Hi Frogster

I'm assuming you know for sure that the snd-cmpci what is what you need.
(just to be sure type 
aplay -l
in a terminal- this will give you the sound hardware you use- it should match C-Media CMI8x38 PCI)
I assume you've got ALSA installed already(they come with your Ubuntu CD), so you could skip this next step
You can install the ALSA codecs from the Ubuntu repositories by typing in a terminal
sudo apt-get install linux-sound-base alsa-base alsa-utils

Next in the terminal type
modprobe snd-cmipci ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
 
Reboot your system.

That's about it. The module snd-cmpci has been installed and loaded into the kernel
The additional stuff that comes after this is probably not required in your case.
Should you still have problems after this please post here or send me a PM with the details(I'm no expert but I'll do what I can to help ASAP).
Lotsa luck

---

### Post by Frogster on 2008-01-10
aplay -l  returns the following

keith@keith-Ubuntu:~$ aplay -l
aplay: device_list:204: no soundcards found...

However, the soundcard is this one  [http://www.cmedia.com.tw/?q=en/PCI/CMI8738](http://www.cmedia.com.tw/?q=en/PCI/CMI8738).

I have tried working through LordRaiden's Comprehensive_Sound_Problems_Solutions_Guide and just don't seem to be getting anywhere.  I got as far as being told to post here!

Thank you for your advice

Keith

---

### Post by Yellow Pasque on 2008-01-10
If ALSA does not work, try OSSv4. Follow the link in my sig.

---

### Post by Frogster on 2008-01-10
Thank you Temujin,

Its good to know that there is another option. I will give it a try. 

I have to say that if I cant get sound working soon in Ubuntu I will have to re load windows or try another distro.

Once again thank you

---

### Post by balaknair on 2008-01-10
hi frogster
Could you also post the output of lspci -v
I think you could try purging ALSA completely and reinstalling it with apt-get.
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils

I had this problem with my sound card being detected but that was after I'd tinkered with the settings a lot. but from a search of the c-media link you posted(and the c-media forums) it seems the CMI8738 card and its brethren have some serious issues with Linux(esp ALSA)

I'm assuming you installed Ubuntu from a Live CD, did you get any sound then when running the Live CD?
Or did the sound issues start after installing and perhaps updating?
If you're not sure, maybe you could just pop in the live cd and boot from it to see if there's any sound- as before aplay -l and lspci -v ouitputs should help. If you're getting sound in the Live CD, it could be a change(maybe on updating) to the kernel that caused the issue. In that case it might be possible to fix it by just reverting to the older generic kernel. Details on how to do that are beyond me though( I just reinstalled Gutsy from scratch- not the best method, I know).
Anyway, wishing you luck. Be sure to post an update when you're done, I'll check this thread tomorrow(or later today- it's nearly three in the morning here)

---

### Post by Frogster on 2008-01-15
Thank you balaknair for your help. Sound is still not working even after many kernal purges.  I am now giving up on ever getting sound out of Ubuntu.:confused:

---


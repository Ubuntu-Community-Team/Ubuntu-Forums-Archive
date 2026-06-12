---
title: "Sound coming out from Laptop Speakers + Headphones :(   Hardy Heron"
date: 2008-05-03
forum: Multimedia Software
---

### Post by zentropy on 2008-05-03
when I plug in headphones, the sound continues to come out of the built in speakers as well as the headphones. Is there anyway to get the sound to only come out of the headphones? Ive tried for SO long cant get it to work.


lspci -v|grep Audio =
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
Subsystem: Uniwill Computer Corp Unknown device 9077
Flags: medium devsel, IRQ 10
I/O ports at 18e0 [size=32]


&#9474; &#9474;/proc/asound/cards: &#9618; &#9474;
&#9474; &#9474;=================== &#9618; &#9474;
&#9474; &#9474; 0 [pcsp ]: PC-Speaker - pcsp &#9618; &#9474;
&#9474; &#9474; Internal PC-Speaker at port 0x61 &#9618; &#9474;
&#9474; &#9474; 1 [Intel ]: HDA-Intel - HDA Intel &#9618; &#9474;
&#9474; &#9474; HDA Intel at 0xb0000000 irq 21



I tried this:

sudo apt-get install module-assistant alsa-source

and opened it:
sudo module-assistant

tried everything, no luck

.....the sound continues to come out of the built in speakers as well as the headphones


in windows xp this problem is solved by installing these windows drivers:

[http://www.uniwill.com/UserDownload/P53In/P53In.php](http://www.uniwill.com/UserDownload/P53In/P53In.php)

The latop is sold via alienware, novatech (mine) and many more


Please, any advice will do 

Thanks in advance :D

---

### Post by Zorael on 2008-05-03
This seems to be a common problem with Intel HDA cards, in recent kernels.

The very first thing you need to do if you're not getting *any* sound is to open up **alsamixer** in a terminal and make sure everything is unmuted. Of course, this doesn't apply if you're getting scrambled sound.

Failing that, likely you need to specify a "model" at the very end of **/etc/modprobe.d/alsa-base**.

Open it up in a text editor with superuser permissions, such as by running '**gksu gedit /etc/modprobe.d/alsa-base**' in a run box (Alt+F2). Then you add a line to the bottom of that file saying something like the following.
```
options snd-hda-intel model=*<model>*
```
I have an Acer 9815 laptop so I made it 'model=acer' and after that it worked. You need to figure out which model you're to use, though.

Enter this command to find out which chipset your card has.
```
$ aplay -l
```
It'll say something like:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: **ALC883** Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #
```
...where the ALC883 part is what you want to find out. Obviously, yours might say something different. Then see the relevant chipset section over at [http://ubuntuforums.org/showthread.php?p=4869458#post4869458](http://ubuntuforums.org/showthread.php?p=4869458#post4869458) for models available to your chipset. Try adding one, then do the following in a terminal to see if it worked.

edit: PulseAudio, which is the default sound server/manager in Ubuntu Hardy and onwards, makes it hard to unload the sound driver so we can restart it with the new model parameters. The following might work, else you'll just have to do a complete reboot. Close all applications using sound.
```
$ pulseaudio -k
$ sudo service alsa-utils stop
$ sudo rmmod snd_hda_intel
$ sudo modprobe snd_hda_intel
$ sudo service alsa-utils start
$ pulseaudio -D
```
All in one line for your copy/paste pleasure:
**pulseaudio -k; sudo service alsa-utils stop; sudo rmmod snd_hda_intel; sudo modprobe snd_hda_intel; sudo service alsa-utils start; pulseaudio -D**

Start playing something, connect/disconnect headphones, etc. If it didn't, change it to something else from that list, and do the above command again.

---

### Post by zentropy on 2008-05-03
Nice, thanks for the speedy reply

however its still not working :(  

you helped allot tho :) doing tons of searching across forums. ill post if i find a fix or how i fixed it.

here is my aplay -l 

# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


tried 
options snd-hda-intel model=ALC882
options snd-hda-intel model=uniwill
options snd-hda-intel model=acer
options snd-hda-intel model=ALC882/885
and some others

some other stuff:

# cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC885

---

### Post by zentropy on 2008-05-03
bah

after another 3 hours of searching and trying stuff no luck -_-

is there any way i can completely disable the speakers on my laptop? 

Since the sound comes out from headphones and speakers at same time that could solve the problem :)

i found this (no clue if it helps):

&#9474; &#9474;/proc/asound/cards: &#9618; &#9474;
&#9474; &#9474;=================== &#9618; &#9474;
&#9474; &#9474; 0 [pcsp ]: PC-Speaker - pcsp &#9618; &#9474;
&#9474; &#9474; Internal PC-Speaker at port 0x61 &#9618; &#9474;
&#9474; &#9474; 1 [Intel ]: HDA-Intel - HDA Intel &#9618; &#9474;
&#9474; &#9474; HDA Intel at 0xb0000000 irq 21



This is the VERY last thing i have to get working in ubuntu :) already havent booted windows since 8.04 release. all my games etc work through cedega/wine. Just need this working so i can listen to music in the library etc.

Thanks in advance

---

### Post by Zorael on 2008-05-03
```
3stack-dig           (3-jack with SPDIF I/O)
6stack-dig           (6-jack digital with SPDIF I/O)
arima                (Arima W820Di1)
macpro               (MacPro support)
```

Tried any of those? Those are the ones listed under ALC882. :>

---

### Post by zentropy on 2008-05-03
yeh, unfortunately none of those work :(

---

### Post by zentropy on 2008-05-03
OMG ITS WORKING! the laptop speakers are completely off and only headphones work which is AWESOME. laptop speakers suck anyway.

now i gotta find out what fixed it lol so i can post here if anyone else has the same problem :D


ok i think the fix was a combination of these two:

adding "options snd-hda-intel model=3stack-dig" in # gksu gedit /etc/modprobe.d/alsa-base
AND

i added this [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf)
to   sudo ./alsaconf.sh    then save
then chmod it and ran it. 
it did something
then restart and it worked :D


THANKS SOOO MUCH Zorael :D

---

### Post by Zorael on 2008-05-03
*<ignore>*

---

### Post by Zorael on 2008-05-03
Awesome, cheers. :>

---

### Post by genfly on 2008-05-03
This fixed my sound issue too
Thank you

---

### Post by chriskin on 2008-06-10
> **zentropy said:**
> OMG ITS WORKING! the laptop speakers are completely off and only headphones work which is AWESOME. laptop speakers suck anyway.

now i gotta find out what fixed it lol so i can post here if anyone else has the same problem :D


ok i think the fix was a combination of these two:

adding "options snd-hda-intel model=3stack-dig" in # gksu gedit /etc/modprobe.d/alsa-base
AND

i added this [http://www.schugy.de/forenlinks/alsaconf](http://www.schugy.de/forenlinks/alsaconf)
to   sudo ./alsaconf.sh    then save
then chmod it and ran it. 
it did something
then restart and it worked :D


THANKS SOOO MUCH Zorael :D

i did this and now i have sound only through my headphones :S
speakers are dead :S

is there any way i can make both work, each when it is needed?

---

### Post by genfly on 2008-06-17
RE: is there any way i can make both work, each when it is needed?

let me know if you find a way cause id like both to work too, each when needed.

---

### Post by Michael080808 on 2008-08-09
*bump*
Same, just got a new Vaio (vgn-nr498e) and I have everything working except for this (also can't wait for pyroom to become distributible...) pretty new to linux and I'm excited to get all this working properly (no weird configs like no speakers just headphones). I'd like this to be my long term relationship with linux ;-)

---

### Post by discord on 2008-09-23
having the same problem. Tried all the alsa-base modprobe options. I also tried running the alsaconf.sh script. no luck. I have a Sony VGN-N320E. Anybody know how to get rid of this issue for this laptop?

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by discord on 2008-10-01
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

Here are a few more threads about hda sound chips:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

url above on top listed the assamd sony module which worked for me after reboot...

---

### Post by p0inte on 2008-11-05
I'm using a Sony VAIO VGN-FW139E and i'm experiencing the same problem - sounds comes out of both the laptop speakers and the headphones(while they're plugged). I tried the suggestions above (forcing the snd-intel-hda model, downloading and running that ALSA Configuration script, which was supposed to work) and i'm still having the issue. 

Forcing the model didn't make a difference.

The configuration script did something, said that my card is configured and ready for playback. Alas, playback was still out of both "holes".

Any other ideas? I'm still very new to using Ubuntu (and Linux in general).

*edit* i would also like to mention that after reading the other threads, i couldn't solve my problem, yet again. I HAVE the audio switch named "Headphones", which works too - when unticked i get no sound in the headphones as expected, but no matter the option and if headphones are plugged or not, the speakers keep playing as well.

---

### Post by tamagotono on 2008-11-28
> **p0inte said:**
> I'm using a Sony VAIO VGN-FW139E and i'm experiencing the same problem - sounds comes out of both the laptop speakers and the headphones(while they're plugged). I tried the suggestions above (forcing the snd-intel-hda model, downloading and running that ALSA Configuration script, which was supposed to work) and i'm still having the issue. 

Forcing the model didn't make a difference.

The configuration script did something, said that my card is configured and ready for playback. Alas, playback was still out of both "holes".

Any other ideas? I'm still very new to using Ubuntu (and Linux in general).

*edit* i would also like to mention that after reading the other threads, i couldn't solve my problem, yet again. I HAVE the audio switch named "Headphones", which works too - when unticked i get no sound in the headphones as expected, but no matter the option and if headphones are plugged or not, the speakers keep playing as well.

I too am using a Sony VGN-FW139E and have just found the fix for the headphone jack problems.

you just need to edit the alsa-base file and add "options snd-hda-intel model=sony-assamd" to the end of the file.

In a console type
```
sudo nano /etc/modprobe.d/alsa-base
```

then page-down to the bottom of the file and add 
```
options snd-hda-intel model=sony-assamd
```

use CTRL+X to exit and make sure to save it.  Then restart your computer and your headphones will work the way you expect them to.

I found this information at [http://ubuntuforums.org/showthread.php?t=806620&page=3]("http://ubuntuforums.org/showthread.php?t=806620&page=3")

If anyone is interested I am keeping a google notebook of all the notes I have found to getting my laptop working.  I have made it public so anyone can see it.  I would recommend making copies of any information you find helpful because who knows what I will change in the future.. :)

[http://www.google.com/notebook/public/14361927605303813452/BDQrTDAoQ1oSjwtIj]("http://www.google.com/notebook/public/14361927605303813452/BDQrTDAoQ1oSjwtIj")

Hope this helps.

---

### Post by xsilvergs on 2009-03-13
Hi,

I have a laptop sold by Novatech, it's a L55110 but I have no idea who makes the internals.

My problem is that the speakers do not mute when I insert the headphone jack, what should I put at the end of options snd-hda-intel model= for the model? Is this what I need to do?

Thanks for any help.

---

### Post by Plastic Dinosaur on 2009-04-25
Ok...mine was just working, I take the headphones out for a second to show my dad something, and they decide to quit working!!! auuugghghghg!!!!

Here's my audio info.

card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Someone for the love of god, please help me. :O :(

---

### Post by Plastic Dinosaur on 2009-04-25
please

---

### Post by MCMalkemus on 2009-04-27
Simple solution for my problem: I heard sound coming from the speakers and the headphones with a cheap set of headphone/mic with two jacks from logitech. When I later used the Sennheiser headset without a mic, no sound was heard from the speakers.

---


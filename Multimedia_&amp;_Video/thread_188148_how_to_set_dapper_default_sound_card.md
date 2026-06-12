---
title: "how to set dapper default sound card"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by bags on 2006-06-03
hy! :mrgreen: 
I have 2 sound cards:
1. onboard nvidia card
2. terratec dmx fire 24/96

I would like to use both the sound cards but I'm not able to set the terratec as the default one... I tried system->preferences->sound but my default card changes every time i restart!

can you help me? this is my /etc/modprobe.d/alsa-base file:

> # autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }

# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-intel8x0m index=-2
options snd-atiixp-modem index=-2
options snd-via82xx-modem index=-2


thanks, :mrgreen: 
matteo

(sorry for the [double post]("http://www.ubuntuforums.org/showthread.php?t=187808") but I don't know how to delete it)

---

### Post by neymac on 2006-06-05
The same hapens with my Dapper.

And some programs play one sound card (the default one) and some programs play the other sound card (not the default).

I change the default sound card like Bags did and when I come back to Pref=>Sounds the old one returns like the default.

---

### Post by bags on 2006-06-05
i think this is more than a little bug ;)

---

### Post by neymac on 2006-06-05
The site [https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=default+sound+card&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=&orderby=-priority%2C-severity](https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=default+sound+card&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=&orderby=-priority%2C-severity)
shows this like unconfirmed bug.
Bug number= 45786
"default sound card is randomly set on boot, settting default sound card through gnome-sound-properties did not work correctly, changing volume through hotkeys (on logitech multimedia keyboard) is bind with card0, not with default card"

---

### Post by jwmislan on 2006-06-24
Did you try
options snd-(onboard nvidia card) index=-2 

to keep the nvidia sound from grabbing index 0

---

### Post by bags on 2006-06-24
I tried it but it's still not working... ](*,) 
every time I log in my default sound card changes randomly :-k

---

### Post by wangdang on 2006-06-27
same here...and in dosbox my sound always play thru my secondary soundcard, as does flash in firefox....but mp3s come out right

---

### Post by ogami1972 on 2006-06-29
same here- sets my midi controller to default sound card- no fixes yet but i am working on it...
and done!

i followed the instructions on this thread

[http://ubuntuforums.org/showthread.php?t=114551](http://ubuntuforums.org/showthread.php?t=114551)

this is what i added to the end of my /etc/modprobe.d/alsa-base 

#hard set for sound cards
options snd-usb-audio index=1
options snd_ICE1712 index=0
options snd-ICH6 index=2

then i 
$sudo update-modules

and rebooted- voila!

did this work for you?

---

### Post by cocteau on 2006-07-11
Hi

   Hardsetting the sound cards didn't work for me, but 'un'-setting my internal one worked like a charm.

   I added this line to /etc/modprobe.d/alsa-base

options snd-via8233 index=-2

   and didn't mention my usb sound card. Last part, to get it working was thanks to you.

> then i 
$sudo update-modules

and rebooted- voila!

---

### Post by Ambimom on 2006-08-12
Add my name to those who find the sound card default changing each time I boot....it drove me nuts until I read this.

The only effect I notice is that I cannot use Audacity whenever it boots to the usb; but when it boots to intel ich5, which is my actual default, Audacity works just fine.

I never know which card it will boot to....I sure hope someone fixes this bug...

---

### Post by alipi on 2006-08-17
**Original:**

I have two sound cards and this seems to work for me so far:

Locate the module names of your sound cards with:
 
less /proc/asound/modules

mine was:

0 snd_emu10k1
1 snd_ice1712

In /etc/modprobe.d/alsa-base replace:

install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1

with:

install sound-slot-0 modprobe snd_ice1712
install sound-slot-1 modprobe snd_emu10k1

or the other way depending on which card you want as the default (sound-slot-0) 

I've rebooted several times and I have always gotten the right card as default, but it may be pure luck ;)

**Update:**

Seems like it was pure luck :-({|=

---

### Post by Ambimom on 2006-08-17
Thanks for the tip.  I've done as you suggest.  I'll let you know if this fixes the problem!  It seems like common sense so fingers crossed!

---

### Post by Ambimom on 2006-08-18
Seems to be working!  Thanks so much.  It was driving me nuts.  I even checked the bug reports and found a couple of other people who were experiencing this.  I appreciate your help!

---

### Post by Ambimom on 2006-08-18
Spoke too soon....unfortunately, on the fourth boot, I was back to the wrong sound card AGAIN!  I'm at my wit's end unless I am doing something wrong.

---

### Post by alipi on 2006-08-19
Yes it's back at random for me too :( 

I hope someone comes with a solution for this one.

---

### Post by Ambimom on 2006-08-19
I filed a bug report [https://launchpad.net/distros/ubuntu/+bug/56482](https://launchpad.net/distros/ubuntu/+bug/56482).  Perhaps you can add your data here too.  It's not serious just very, very annoying.  ](*,)

---

### Post by alipi on 2006-08-25
I also added 

options snd_ice1712 index=0
options snd_emu10k1 index=1

at the end of 

/etc/modprobe.d/alsa-base 

it has been correct 10+ boots, but it could be luck again.

---

### Post by Ambimom on 2006-08-25
Fingers crossed, I did the same thing two days ago (added my sound card sequence to the end of  /etc/modprobe.d/alsa-base) and it's been okay ever since too!

The Comprehensive Sound Problems Solution Guide (which I've read a thousand times already) does offer this solution.  Yet,  I am so unfamiliar with terminal commands and conventions that I misinterpreted the instructions.  

A few days ago, I re-read them and realized my mistake.  I re-did it and I've been booting to the correct card ever since!  [I hope from now on.....]

---

### Post by sonicste on 2007-08-24
The better way is this:
see all the soundcards in the system with: sudo asoundconf list
Select your favourite one: sudo asoundconf set-default-card "favouriteoundcard"

Regards
Stefano

---

### Post by Essence on 2007-12-28
I had similar problems were it would put other cards as my default sound card. I'm running 7.1

What confused me was that the config file seemed appropriate with... (/etc/modprobe.d/alsa-base)
```
options cx88-alsa index=-2
```
This did not fix it... what the problem was is that I have TWO of these cards on my computer, and it seems the above would only force one of them not to be 0.

Finally fixed the problem with
```
 options cx88-alsa index=-2,-2
```

---


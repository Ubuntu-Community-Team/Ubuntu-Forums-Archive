---
title: "Surround sound"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by snobby500 on 2007-04-10
Hi

sorry, I am new to ubuntu. I currently have ubuntu edgy and am trying to get surround sound working. From what ive read so far I get the impression that it is very difficult unless you get a sound blaster? I have intergrated 5.1 surround sound and it works gr8 on xp but its not workin on linux. when i go to the volume control it says that the device I am using is the VIA 8237 (alsa mixer) if that matters. Could this simply be a driver problem? I can get sound from the left and right front speakers, but not the center and only the back ones if I duplicate the front sound in the back.

any help would be appreciated.

---

### Post by smoothone on 2007-04-10
Same problem here! Wish I could get surround sound working when I play a DVD. I have the same VIA 8237 (alsa mixer). Any help would be appreciated!:confused:

---

### Post by benton on 2007-04-10
I had the same problem the first time I used Ubuntu. Double-click your speaker icon to fire up the ALSA mixer application, then check speaker settings and add the relevant speaker volume controls.  Find the one that controls your rear speakers. That's what I did and it worked wonders.

Cheers,

-Benton

---

### Post by snobby500 on 2007-04-11
I checked every box, and then put the volume on, then turned it off and went to the next one, on every checkbox :) and i can get my rear speakers working, but only if they copy the front ones. But no matter what i do i cant get my centre working :( I think/hope fiesty will help me :)

thx 4 the help tho

---

### Post by DannyW on 2007-04-11
Same problem here.

VIA 8237 (Alsa)
Only front R+L work by default.
Had to enable 'Dublicate front' to enable the rear R+L, but still no center speaker or bass speaker.

And the volume control is a little messed up with dublicate front enabled:
Master - controls front R+L
Surround - controls rear R+L
PCM - controls both front and rear.

I would assume master should control all sounds.

Onboard sound 'Realtek ALC850' on motherboard 'Asus A8v Deluxe'.

Any help greatly appreciated.

Thanks,
Danny

---

### Post by smoothone on 2007-04-11
Is anyone able to play a DVD with surround in Ubuntu? If so what player do you use and how is it configured? Thanks

---

### Post by kidford on 2007-04-18
I had this problem until ten minutes ago.
I found a working solution!!
From ArsGeek ([http://www.arsgeek.com/?p=971)]("http://www.arsgeek.com/?p=971")

I had no .asoundrc in my home directory, so I created one with the following:

> pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}

Then, using the command
> speaker-test -c6 -twav
I verified that it works!

---

### Post by Rice_slayer on 2007-04-22
sorry to bring up a few day old post, but in my .asoundrc it says the following
> # ALSA library configuration file

# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/riceslayer/.asoundrc.asoundconf>


And when i change it to what he has above, i get no sound whatsoever. I'm using the CA0106 for my SoundBlaster Live! 24 bit PCi card. Any help on 5.1 for it?

---

### Post by snobby500 on 2007-07-06
if anyonme is still reading this, i can get all my speakers working inc sub but i dont think its true surround sound (where they function individually), i did this by unplugging the center speaker wire from the pc to the sub, and then duplicating sound in rear speakers on the sound option in ubuntu, i also enabled surround sound and put up the volume, but i think this might just be my speakers that can make 4.1 surround sound to 5.1, i thought id mention it for anyone out there, you never know, might come in handy :)

sorry i dont know anythin about above post :(

---

### Post by mchaggis211 on 2007-07-07
all that the asound configuration u posted does is copy the sound from the stereo speakers an outputs tehm to the others.

I am having the same problem i have a Asus a8n-sli motherboard with built in Realtek ac97 souround card

my speakers work great in xp

---


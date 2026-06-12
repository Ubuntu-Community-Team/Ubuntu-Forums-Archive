---
title: "New to ubuntu stodio - sound card problem"
date: 2008-09-14
forum: Multimedia Software
---

### Post by igetupigetdown85 on 2008-09-14
hello all!
first of, i'm new to ubuntu studio and linux in general.
i'm using ego-sys (ESI) "Waveterminal 192x" soundcard which suppose to work with ALSA (it appears on their list of soundcards).

i have installed ubuntu-studio but it doesn't recognize my sound card.
although ubuntu studio comes with the ALSA driver (i guess??!),
when i go: SYSTEM -> preferences -> SOUND,
i can see the ALSA driver, but in DEVICE i can only see the on-board intel sound device (INTEL ICH5). couldn't find the WAVETERMINAL.
i've disabled the on-board AUDIO in BIOS and now the DEVICE line is empty!
how can i make ubuntu recognize my WAVETERMINAL 192x sound-card?

many thanks,

eyal

---

### Post by markbuntu on 2008-09-14
I had some problems with various pci cards and when Ubuntu would not see them I would try another slot and then they would work. I know it sounds sort of silly, but you should try that first.

---

### Post by Yellow Pasque on 2008-09-14
Is it an ESI Juli@ or a different card?
OSS4 has support for that card. [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by igetupigetdown85 on 2008-09-14
it's not a Juli@...
it's a waveterminal 192x.

---

### Post by Stochastic on 2008-09-14
do you see it in the output of ```
lspci
```

---

### Post by igetupigetdown85 on 2008-09-15
yes, but it calls it "VIA" for some reason..

02:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

---

### Post by Stochastic on 2008-09-15
I think the reply in your other thread (the second one you created here: [http://ubuntuforums.org/showthread.php?t=919890](http://ubuntuforums.org/showthread.php?t=919890)) nailed it on the head then as Linux sees it as a general envy24 chip.

---

### Post by igetupigetdown85 on 2008-09-16
ok,
i nearly give up using ubuntu.
if someone could please explain me what should i do in order to get my sound card working, in a simple way, i'd be very thankful.
do i need to download something? a driver?
do i need only to copy/paste those lines into the terminal?? 
sorry, but i'm very new to this system and can't understand most of the things you guys are talking about.
again- many thanks.

---

### Post by igetupigetdown85 on 2008-09-16
help?????????

---

### Post by markbuntu on 2008-09-16
Did you actually try anything anyone suggested. A little feedback about what you are doing would help here.

Anyway, there is some links from here that may help you out:

[http://alsa.opensrc.org/index.php/Main_Page](http://alsa.opensrc.org/index.php/Main_Page)

---

### Post by igetupigetdown85 on 2008-09-16
hi,
you're right.
sorry for being impatient, i'm just trying to make it work over and over again for the last few days.
sure i did try everything people here suggested.
i also tried this guide: Comprehensive Sound Problem Solutions Guide.
nothing worked.

the alsa wiki site helped me understand a few things.
so, i guess i don't need to install the alsa driver,
it obviously comes with ubuntu studio. am i right?

i think the problem is that ubuntu won't identify my sound card as a sound device.
though it apears when i enter lspci - but not in it's real name.. don't know why.
i tried also - sudo modprobe snd-ice1724 - to load the right driver but it just didn't do a thing.
any idea?

---

### Post by Yellow Pasque on 2008-09-17
Your card doesn't appear to be supported under ALSA: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-ESI](http://www.alsa-project.org/main/index.php/Matrix:Vendor-ESI)

---

### Post by igetupigetdown85 on 2008-09-17
yse it is...
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ego_Sys](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ego_Sys)

---

### Post by Yellow Pasque on 2008-09-17
> **igetupigetdown85 said:**
> yse it is...
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ego_Sys](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Ego_Sys)
Ah, ALSA has it listed under two different names (horrible ALSA documentation, as usual). Anyway, your model is tagged with "possible" meaning "Possible to support, but no driver has been written yet".

---

### Post by igetupigetdown85 on 2008-09-17
oh.. ok.
i hope it will work in the end.
i can't wait throwing XP away and start recording with linux.
do you have an idea what else do i need to do?
thanks.

---

### Post by igetupigetdown85 on 2008-09-19
Hi,
thank you very much for trying to help.
i'm going back to windows xp after more than a week i tried to make linux "accept" my sound card.
i'll stay tuned to see if alsa has made a driver for my waveterminal 192x.
maybe someone will find it helpful, so i'm posting the thread for the same problem i made in the 64studio forums: [http://64studio.com/node/732](http://64studio.com/node/732)

thanks again for everything and good luck!
i hope i'll be able to use ubuntu studio soon.

eyal

---


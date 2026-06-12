---
title: "Behringer Mixers &amp; USB/Firewire Audio Devices in Ubuntu Studio"
date: 2007-05-16
forum: Multimedia Production
---

### Post by [wakingeden] on 2007-05-16
The reason why I'm starting this thread is to see if we can come to a working solution for mixing and recording audio with Behringer Mixers & USB/Firewire Audio Devices in Ubuntu Studio (Mainly the FCA-202, UCA-200, UCA-202 USB Audio Devices).

Behringer is best known for it's quality to price ratio in the audio market, it is not the best and most certainly not the most supported. If you are reading this thread, you should know about Behringer's faults and weakness as well as its strong points. This thread is not here to compare or discuss those points, we assume you know them and have made your choice accordingly.

[SIZE="3"]References[/SIZE]:

[SIZE="2"]Main Site:[/SIZE]

[www.behringer.com/]("http://www.behringer.com/")

[SIZE="2"]USB/Firewire/MIDI Audio Devices:[/SIZE]

Behringer UCA-200
*There is no reference page for this device on the manufacturers site* 

[Behringer UCA-202]("http://www.behringer.com/UCA202/index.cfm?lang=eng")

[Behringer FCA-202]("http://www.behringer.com/FCA202/index.cfm?lang=eng")
[SIZE="3"]
*This is an initial post and will worked on as time permits, if you have any questions or comments I would like to ask if you would PM me instead of posting. It will help keep this thread clean and filled with only useful information.* [/SIZE]

---

### Post by kayosiii on 2007-05-24
I know that currently the firewire based device is not supported (which is a pity)... Can't help you with the others.

---

### Post by dj.mimo on 2007-06-04
i'm using the uca202 with my laptop as additional audio i/o. works fine with both in and out, sounds definitly beter as the onboard sound. there seems to be no input gain control in alsa mixer. no problem for me since i use external level control. the output is ok, no distortion even at highest volume. small problem with mains hum (only on ac adaptor), but this can be solved with a di-box.

---

### Post by holotone on 2007-07-13
Any tips on getting the UCA200 up and running in Feisty?

---

### Post by holotone on 2007-07-13
> **holotone said:**
> Any tips on getting the UCA200 up and running in Feisty?

Nevermind - Plug 'n' Play, even. Just had to select the USB device from within Audacity's settings, and I'm good to go!

---

### Post by mrroland on 2007-07-15
Hi all, great inititative!

I received a UCA202 yesterday, i like it.
I tested it on windows (sorry i have to use this word:oops:) and it works fine.
But with latest kubuntu the device is recognized and shown in alsa mixer, but i can't hear any sound.
Moving the two available sliders doesn't help.

Does anybody has some sugestions for me?


I want to use the device to record with Rosegarden, but alsa shows me no inputs. 
Does this mean the inputs are not recognized, or that i simply can't change anything with the mixer?

Any comments from users are welcome.

---

### Post by barkeff on 2007-09-27
Hi there,
I recently purchased a dell inspiron 1420 laptop w/ ubuntu and installed the ubuntu studio packages on.I was pretty dissapointed with the integrated Intel HDA audio..........and I get no audio at all with it using the linux-rt kernel.Concerning the UCA-202....Is this little bugger decent for multitracking with Audour?That more or less all I wanna do.You can't beat $30 over at Musician's Friend!Might be able to afford a decent set of monitors for my desktop if I buy this thing.Thanks!Ubuntu Studio is pretty much what made Ubuntu my primary OS......:guitar:

---

### Post by happydan on 2007-11-06
has anyone managed to get firewire interfaces working? i have the FCA202 and ubuntu sorta detects it, but doesnt seem to have a working driver.

would be, you know... cool if anyone can give me a hint as im new to the linux thing,

---


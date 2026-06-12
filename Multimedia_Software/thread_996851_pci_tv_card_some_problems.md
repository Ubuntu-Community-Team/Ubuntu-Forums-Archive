---
title: "pci tv card some problems"
date: 2008-11-29
forum: Multimedia Software
---

### Post by techno-mole on 2008-11-29
hello.

I have a kworld plus tv hybrid pci tv card (model dvb-t 210 se) and ive been trying to get it to work on ubuntu (have also tried on kubutu 8.10, but thought id go back to gnome again)

i did try the following applications for watching freeview (free to air digital tv)

mythtv - tried it and failed to get it set up
me-tv - got it working but had some issues
currently using kaffeine, which for the most part has been the best of the lot  (in my opinion) but i have a small issue, that being the reception ? at least it might be that.

the problem is that when i try to watch any channel i get this on the picture (see attached screen shot) now i have been told that this is most likely interference, this happens regardless of the channel im watching.

the card is using the arial on the roof of my house and runs through a booster (compatible with digital signals) now i also have windows xp (dual booting) and i have installed the drivers etc for the card (the stuff that came with it) and the card works fine, but the reception is also fine, i get nothing like in the screenshot, and i also get a full signal on pretty much every channel.

now if the problem in the screenshot is interference why does it only occur when im logged into my liux system ? and also kaffeine only ever gets a 50% signal on any channel, never the full 100% like i would get on my windows system, this is why im having some trouble accepting that its a problem with interference and not something else.

i have messed about with the de-interlacing settings in kaffeine and with it on the reception is terrible, and with it off its not much better.
I have also noticed that although i have an x2 athalon cpu @ 2.6ghz kaffeine never uses more than 18% on the cpu usage (eg - if i run top in a terminal kaffeine never uses more than 18%)

i have tried while running kaffeine pressing ctrl and i (this brings up the de-interlacing settings) and setting it to the max, but the cpu usage doesnt go above 18% even then.

i have wondered whether the info i have for my local transmitter is okay, as i had to find it myself because it didnt come up in any of the lists in kaffeine and me-tv, i did a scan using w_scan for the frequencies etc, but this hasnt made a difference to the quality.

does anyone have any suggestions as to why i get this apparent interference, but only on the ubuntu system ? surely the recption shouldnt change because of the operating system ?

cheers in advanced for any help, also if any more info is needed let me know and ill provide it.

my systems specs are as follows.

cpu amd athalon x2 5200 + @2.6gh (dual core)
nvidia 8600gt pci express graphics card (using the 177.80 driver)
2 gig of ddr 2 ram @ 800mhz
sound blaster audigy sound card
500 gb sata hard drive (this is the one with ubuntu on)
80 gb sata hard drive (with xp on for playing games)
19inch widescreen flat screen monitor.

the tv card is as mentioned a kworld pci card, it does dvb-t, fm radio, it also has a remote and a composite out put, for connecting a games system of other bit of kit, it uses a philips semiconductor chip, if i do lspci in a terminal it comes up as - 01:05.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
 
although this particular card is not on the list of supported cards on linuxtv.org, the chips it uses are, at least thats the impression i got.

cheers again

---


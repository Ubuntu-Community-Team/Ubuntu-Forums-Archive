---
title: "i know what is causing the firefox flash crash!!"
date: 2009-01-08
forum: Multimedia Software
---

### Post by cb34 on 2009-01-08
i found out what it is..

after installing debian etch, which had the same problem, and now on debianLenny which took me 4 installs to get it right(im fairly new to the linux world and did everything from the cli from memory;))

again, with a new install of not ubuntu, but straight debian, same thing happens, no flash plugin=no crashing super stable,
flash installed=lockup/crash.. or in full screen mode flash locks the whole machine/xserver. very reproducible.

so anywayz...

i know what it is, and i think for the people that the
firefoxrc dsp= fix,
or the export XLIB_SKIP_ARGB_VISUALS=1 fix,
or the default 24bit fix didn't work,
or all the different settings in xorg you can fiddle with..

you need to look at your sound card, or onboard sound built onto the motherboard.

i played with a million settings, reinstalled operating systems, i'd say now about 8 times,just to fix the flash issue. can you imagine, i nuked intrepid, and reinstalled it 3 times just for flash, and now just recently spent DAYZ to figure out how to install debian properly just for this issue, and when it still crashed in my new debian etch and lenny install(tried both), i almost cried im tellin ya............
i tried tons of different settings in xorg, and dont have compiz or anything special installed.. nothing worked, i've been at this for MONTHS now... MONTHS of hrs and hrs of work just on this problem.. im so sick of it.

when i disabled my onboard sound in the bios, the problem is completely gone. i opened 15 flash vids(ya, was choppy n slow..hehe because so many open but), no crashing at all, and i do full screen on and off, back forward, and let it run for hrs while i went and cleaned the snow.

i thought still it might be something like alsa or oss and not the hardware itself(dont have pulse installed on my debian box..for now), since the operating system i figured is not detecting any sound hardware present so doesn't load up the proper things, and no crashing.. but maybe with a different sound card plugged in, the problem will still be there. ??

so i then(very luckily) found an old creative sound blaster card i had laying around from like 10 years ago, set it up and now everything works.. i dont know about sound quality difference from old card and onboard sound.. but for now, this is it folks. and i could not get flash working with anything i did, every version of flash, every version of firefox, from repo or manual install.. etc etc etc........... for months!
i work from home and spend dayz at a time on this.. so sickening.. as im sure many of you feel the same way.

so.. look into your sound card/hardware.

i have a ABIT AA8 motherboard with the uguru clock(3rd eye), which comes with Realtek ALC880 onboard sound.

i was seriously getting ill already from troubleshooting this problem, and that's no exaggeration.

be well everybody. im finally watching flash with no worries, and to think the only thing that did it was to use a garbage 2$ oldazz sound card.

p.s. i have not even once thought of switching to win. HAHA
ok.. maybe once for about 0.06 seconds. then i installed debian. :D

---

### Post by cb34 on 2009-01-08
oh maaan! this is a dream come true.. just wanted to also mention...

i could never get 5.1 surround sound working with hardy, intrepid, debian etch/lenny.. following psyke's pulseaudio threads and reading forever and trying everything i could.. would never work in 5.1..

but now not going crazy setting all kinds of settings, just popping in an old creative SB Live card, and disabling the onboard sound from the bios, my 5.1 sound is working! :D:D

in preferences/sound i had some new option appear for the SB card, and BAM.. 5.1 sound! that's all there was too it.
no installing drivers or anything.. i think i got real lucky here. :D

peace.

---

### Post by wolfen69 on 2009-01-08
good to hear you got it sorted.

---

### Post by wolfen69 on 2009-01-08
.

---

### Post by cb34 on 2009-01-11
thanks man. :)

this was a huge problem for me.

have not had any crashes due to firefox/flash since. :D

---

### Post by pristoid on 2009-02-02
Woow thanks a lot cb34. I'v been despeerate to make my intrepid box running multimedia presentation using firefox and of course with flash and sound (duh) so I guest i had to search the market for that old soundblaster card. Thanks once again. But I think it was a serious problem and had to clear up cause most of us using on board sound card now on. :p

---

### Post by Chandler258 on 2009-02-26
Could it be that some DMA or IRQ adresses are coliding?

---

### Post by cor2y on 2009-03-06
Thanks cb34 i'll have to swap in a standalone soundcard and see if that works.
I too have been banging my head ever since 8.04 trying to figure out why firefox would crash with an unhelpful "Segmentation fault" even in safe mode when going to sites with flash, and the frustrating part it is never all the time but at random moments thank goodness for the firefox crash handler that allows you to recover tabs when it crashes (doesn't work all the time though) .
I too have the Realtek ALC880 chipset for onboard audio although my board is MSI.

---


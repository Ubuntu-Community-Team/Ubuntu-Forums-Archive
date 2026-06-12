---
title: "trying to get creative audigy se working with kubuntu; total noob"
date: 2009-01-18
forum: Multimedia Software
---

### Post by elijah_bravo on 2009-01-18
not been working with kubuntu long and i dont really understand a lot of stuff so if you can help please act like your talking to a 4 year old ;) just bought a creative labs audigy se cuz i think the onboard soundcard stopped working. it works great in XP but not in kubuntu.i disabled the onboard soundcard and i found the thread "Comprehensive Sound Problems Solution Guide" and followed it to step 6 of the alsa driver compilation. the module assistant fails and , looking at the log file, it looks good until the end where it says:
 /usr/src/modules/alsa-driver/acore/info.c:90: error: implicit              &#9618;
                   &#9474; declaration of function ‘PAGE_ALIGN’                                       &#9618;
                   &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1           &#9618;
                   &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                  &#9618;
                   &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                &#9618;
                   &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'       &#9618;
                   &#9474; make[2]: *** [compile] Error 2                                             &#9618;
                   &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9618;
                   &#9474; make[1]: *** [build-stamp] Error 2                                         &#9618;
                   &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                  &#9646;
                   &#9474; make: *** [kdist_image] Error 2 
i could post the entire log if needed. please help!! it is much appreciated!!!

p.s. when i used "lspci -v" in konsole my soundcard showed as a Creative Labs SB Audigy LS, but in the list on alsa's site it only shows a soundblaster ls, not audigy ls,:confused: plus the box of the soundcard i bought says soundblaster audigy se....dont know if that helps or anything...

---

### Post by elijah_bravo on 2009-01-18
bump, please help....anyone??

---


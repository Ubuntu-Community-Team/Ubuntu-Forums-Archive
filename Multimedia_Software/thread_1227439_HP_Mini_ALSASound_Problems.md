---
title: "HP Mini ALSA/Sound Problems"
date: 2009-07-30
forum: Multimedia Software
---

### Post by Elycian on 2009-07-30
Ubuntu family, I recently purchased an HP Mini 110-1000 hearing ubuntu works well with it. And it does it works great!

Except for the sound. Originally from my first install sound only worked with the headphone jack. I tried looking at the forums and other resources for fixes but none seemed to work. On one of the suggestions it recommended installing ALSA drivers from source. So I downloaded both versions 1.0.18 and 1.0.19 with the Driver, Utils, and Lib package. The Driver and Lib package compile nicely, but when I try to compile the Utils package for either version I get this error while using the make command in the terminal:

```
Making all in include
make[1]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/include'
make  all-am
make[2]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/include'
make[2]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/include'
make[1]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/include'
Making all in alsactl
make[1]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsactl'
Making all in init
make[2]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsactl/init'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsactl/init'
make[2]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsactl'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT alsactl.o -MD -MP -MF ".deps/alsactl.Tpo" -c -o alsactl.o alsactl.c; \
	then mv -f ".deps/alsactl.Tpo" ".deps/alsactl.Po"; else rm -f ".deps/alsactl.Tpo"; exit 1; fi
alsactl.c: In function &#8216;main&#8217;:
alsactl.c:166: warning: assignment from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT state.o -MD -MP -MF ".deps/state.Tpo" -c -o state.o state.c; \
	then mv -f ".deps/state.Tpo" ".deps/state.Po"; else rm -f ".deps/state.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT utils.o -MD -MP -MF ".deps/utils.Tpo" -c -o utils.o utils.c; \
	then mv -f ".deps/utils.Tpo" ".deps/utils.Po"; else rm -f ".deps/utils.Tpo"; exit 1; fi
utils.c: In function &#8216;initfailed&#8217;:
utils.c:92: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
utils.c:93: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
utils.c:94: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
utils.c:95: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
if gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -MT init_parse.o -MD -MP -MF ".deps/init_parse.Tpo" -c -o init_parse.o init_parse.c; \
	then mv -f ".deps/init_parse.Tpo" ".deps/init_parse.Po"; else rm -f ".deps/init_parse.Tpo"; exit 1; fi
gcc  -g -O2   -o alsactl  alsactl.o state.o utils.o init_parse.o  -lasound -lm -ldl -lpthread
xmlto man alsactl_init.xml
Note: Writing alsactl_init.7
make[2]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsactl'
make[1]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsaconf'
Making all in po
make[2]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsaconf/po'
35 translated messages, 1 untranslated message.
34 translated messages, 1 fuzzy translation, 1 untranslated message.
make[2]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsaconf/po'
make[2]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsaconf'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsaconf'
make[1]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsaconf'
Making all in alsamixer
make[1]: Entering directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsamixer'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include    -DCURSESINC="<ncurses.h>" -g -O2 -MT alsamixer.o -MD -MP -MF ".deps/alsamixer.Tpo" -c -o alsamixer.o alsamixer.c; \
	then mv -f ".deps/alsamixer.Tpo" ".deps/alsamixer.Po"; else rm -f ".deps/alsamixer.Tpo"; exit 1; fi
alsamixer.c:122:19: error: ncurses.h: No such file or directory
alsamixer.c:180: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
alsamixer.c: In function &#8216;mixer_init_draw_contexts&#8217;:
alsamixer.c:343: error: &#8216;COLOR_WHITE&#8217; undeclared (first use in this function)
alsamixer.c:343: error: (Each undeclared identifier is reported only once
alsamixer.c:343: error: for each function it appears in.)
alsamixer.c:343: error: &#8216;A_BOLD&#8217; undeclared (first use in this function)
alsamixer.c:343: error: &#8216;COLOR_BLACK&#8217; undeclared (first use in this function)
alsamixer.c:343: error: &#8216;A_NORMAL&#8217; undeclared (first use in this function)
alsamixer.c:344: error: &#8216;COLOR_YELLOW&#8217; undeclared (first use in this function)
alsamixer.c:345: error: &#8216;COLOR_CYAN&#8217; undeclared (first use in this function)
alsamixer.c:348: error: &#8216;COLOR_GREEN&#8217; undeclared (first use in this function)
alsamixer.c:349: error: &#8216;COLOR_RED&#8217; undeclared (first use in this function)
alsamixer.c:351: error: &#8216;A_DIM&#8217; undeclared (first use in this function)
alsamixer.c:352: error: &#8216;COLOR_BLUE&#8217; undeclared (first use in this function)
alsamixer.c:352: error: &#8216;A_REVERSE&#8217; undeclared (first use in this function)
alsamixer.c:355: error: &#8216;ACS_CKBOARD&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_clear&#8217;:
alsamixer.c:394: error: &#8216;mixer_window&#8217; undeclared (first use in this function)
alsamixer.c:394: error: &#8216;TRUE&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_abort&#8217;:
alsamixer.c:409: error: &#8216;mixer_window&#8217; undeclared (first use in this function)
alsamixer.c:411: error: &#8216;TRUE&#8217; undeclared (first use in this function)
alsamixer.c:413: error: &#8216;FALSE&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_cbar_get_pos&#8217;:
alsamixer.c:463: error: &#8216;FALSE&#8217; undeclared (first use in this function)
alsamixer.c:481: error: &#8216;TRUE&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;draw_volume_bar&#8217;:
alsamixer.c:825: error: &#8216;ACS_LTEE&#8217; undeclared (first use in this function)
alsamixer.c:826: error: &#8216;ACS_RTEE&#8217; undeclared (first use in this function)
alsamixer.c:828: error: &#8216;ACS_LLCORNER&#8217; undeclared (first use in this function)
alsamixer.c:829: error: &#8216;ACS_HLINE&#8217; undeclared (first use in this function)
alsamixer.c:831: error: &#8216;ACS_LRCORNER&#8217; undeclared (first use in this function)
alsamixer.c:837: error: &#8216;ACS_VLINE&#8217; undeclared (first use in this function)
alsamixer.c:855: error: &#8216;ACS_ULCORNER&#8217; undeclared (first use in this function)
alsamixer.c:858: error: &#8216;ACS_URCORNER&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;draw_playback_switch&#8217;:
alsamixer.c:866: error: &#8216;ACS_LLCORNER&#8217; undeclared (first use in this function)
alsamixer.c:867: error: &#8216;ACS_HLINE&#8217; undeclared (first use in this function)
alsamixer.c:869: error: &#8216;ACS_LRCORNER&#8217; undeclared (first use in this function)
alsamixer.c:871: error: &#8216;ACS_VLINE&#8217; undeclared (first use in this function)
alsamixer.c:874: error: &#8216;ACS_ULCORNER&#8217; undeclared (first use in this function)
alsamixer.c:877: error: &#8216;ACS_URCORNER&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_draw_frame&#8217;:
alsamixer.c:1209: error: &#8216;ACS_VLINE&#8217; undeclared (first use in this function)
alsamixer.c:1214: error: &#8216;ACS_HLINE&#8217; undeclared (first use in this function)
alsamixer.c:1220: error: &#8216;ACS_ULCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1221: error: &#8216;ACS_URCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1222: error: &#8216;ACS_LLCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1224: error: &#8216;ACS_LRCORNER&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_show_text&#8217;:
alsamixer.c:1418: error: &#8216;ACS_LRCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1419: error: &#8216;ACS_LLCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1420: error: &#8216;ACS_ULCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1421: error: &#8216;ACS_URCORNER&#8217; undeclared (first use in this function)
alsamixer.c:1426: error: &#8216;ACS_VLINE&#8217; undeclared (first use in this function)
alsamixer.c:1428: error: &#8216;ACS_HLINE&#8217; undeclared (first use in this function)
alsamixer.c:1445: error: &#8216;ACS_CKBOARD&#8217; undeclared (first use in this function)
alsamixer.c:1446: error: &#8216;ACS_BLOCK&#8217; undeclared (first use in this function)
alsamixer.c:1447: error: &#8216;ACS_BOARD&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;recalc_screen_size&#8217;:
alsamixer.c:1650: error: &#8216;mixer_window&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_init_window&#8217;:
alsamixer.c:1854: error: &#8216;mixer_window&#8217; undeclared (first use in this function)
alsamixer.c:1867: error: &#8216;TRUE&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_resize&#8217;:
alsamixer.c:1886: error: &#8216;mixer_window&#8217; undeclared (first use in this function)
alsamixer.c:1886: error: &#8216;FALSE&#8217; undeclared (first use in this function)
alsamixer.c: In function &#8216;mixer_iteration&#8217;:
alsamixer.c:2010: error: case label does not reduce to an integer constant
alsamixer.c:2026: error: case label does not reduce to an integer constant
alsamixer.c:2031: error: case label does not reduce to an integer constant
alsamixer.c:2035: error: case label does not reduce to an integer constant
alsamixer.c:2037: error: &#8216;FALSE&#8217; undeclared (first use in this function)
alsamixer.c:2045: error: case label does not reduce to an integer constant
alsamixer.c:2055: error: case label does not reduce to an integer constant
alsamixer.c:2077: error: &#8216;TRUE&#8217; undeclared (first use in this function)
alsamixer.c:2088: error: &#8216;KEY_BTAB&#8217; undeclared (first use in this function)
alsamixer.c:2091: error: &#8216;KEY_A1&#8217; undeclared (first use in this function)
alsamixer.c:2095: error: &#8216;KEY_A3&#8217; undeclared (first use in this function)
alsamixer.c:2099: error: &#8216;KEY_C1&#8217; undeclared (first use in this function)
alsamixer.c:2103: error: &#8216;KEY_C3&#8217; undeclared (first use in this function)
alsamixer.c:2107: error: &#8216;KEY_RIGHT&#8217; undeclared (first use in this function)
alsamixer.c:2111: error: &#8216;KEY_LEFT&#8217; undeclared (first use in this function)
alsamixer.c:2115: error: &#8216;KEY_UP&#8217; undeclared (first use in this function)
alsamixer.c:2120: error: &#8216;KEY_DOWN&#8217; undeclared (first use in this function)
alsamixer.c:2125: error: &#8216;KEY_PPAGE&#8217; undeclared (first use in this function)
alsamixer.c:2130: error: &#8216;KEY_NPAGE&#8217; undeclared (first use in this function)
alsamixer.c:2134: error: &#8216;KEY_BEG&#8217; undeclared (first use in this function)
alsamixer.c:2135: error: &#8216;KEY_HOME&#8217; undeclared (first use in this function)
alsamixer.c:2138: error: &#8216;KEY_LL&#8217; undeclared (first use in this function)
alsamixer.c:2139: error: &#8216;KEY_END&#8217; undeclared (first use in this function)
alsamixer.c:2246: error: &#8216;KEY_IC&#8217; undeclared (first use in this function)
alsamixer.c:2251: error: &#8216;KEY_DC&#8217; undeclared (first use in this function)
make[1]: *** [alsamixer.o] Error 1
make[1]: Leaving directory `/home/elycian/Desktop/alsa-utils-1.0.19/alsamixer'
make: *** [all-recursive] Error 1
elycian@titan:~/Desktop/alsa-utils-1.0.19$ 

```

Why am I getting these errors? After trying to install new ALSA drivers I no longer can get sound from the headphone jack either. Can anyone tell me how I can fix my sound in general or maybe revert my changes back to the original ubuntu ALSA drivers from install without having to actually reinstall everything??

Thanks

---


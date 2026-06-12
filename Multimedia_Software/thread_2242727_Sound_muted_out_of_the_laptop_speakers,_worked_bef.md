---
title: "Sound muted out of the laptop speakers, worked before, stopped to work. Xubuntu 14.04"
date: 2014-09-03
forum: Multimedia Software
---

### Post by christoph5 on 2014-09-03
No sound, pavucontrol shows that the sound-bar is moving and playing even its not coming any sounds from my laptops speaker:

[IMG]http://0o2471.net/l/59901[/IMG]


[COLOR=#ff0000]aplay[/COLOR] gives:
```
Usage: aplay [OPTION]... [FILE]...

-h, --help              help
    --version           print current version
-l, --list-devices      list all soundcards and digital audio devices
-L, --list-pcms         list device names
-D, --device=NAME       select PCM by name
-q, --quiet             quiet mode
-t, --file-type TYPE    file type (voc, wav, raw or au)
-c, --channels=#        channels
-f, --format=FORMAT     sample format (case insensitive)
-r, --rate=#            sample rate
-d, --duration=#        interrupt after # seconds
-M, --mmap              mmap stream
-N, --nonblock          nonblocking mode
-F, --period-time=#     distance between interrupts is # microseconds
-B, --buffer-time=#     buffer duration is # microseconds
    --period-size=#     distance between interrupts is # frames
    --buffer-size=#     buffer duration is # frames
-A, --avail-min=#       min available space for wakeup is # microseconds
-R, --start-delay=#     delay for automatic PCM start is # microseconds 
                        (relative to buffer size if <= 0)
-T, --stop-delay=#      delay for automatic PCM stop is # microseconds from xrun
-v, --verbose           show PCM structure and setup (accumulative)
-V, --vumeter=TYPE      enable VU meter (TYPE: mono or stereo)
-I, --separate-channels one file for each channel
-i, --interactive       allow interactive operation from stdin
-m, --chmap=ch1,ch2,..  Give the channel map to override or follow
    --disable-resample  disable automatic rate resample
    --disable-channels  disable automatic channel conversions
    --disable-format    disable automatic format conversions
    --disable-softvol   disable software volume control (softvol)
    --test-position     test ring buffer position
    --test-coef=#       test coefficient for ring buffer position (default 8)
                        expression for validation is: coef * (buffer_size / 2)
    --test-nowait       do not wait for ring buffer - eats whole CPU
    --max-file-time=#   start another output file when the old file has recorded
                        for this many seconds
    --process-id-file   write the process ID here
    --use-strftime      apply the strftime facility to the output file name
    --dump-hw-params    dump hw_params of the device
    --fatal-errors      treat all errors as fatal
De gjenkjente lydmønsterformatene er: S8 U8 S16_LE S16_BE U16_LE U16_BE S24_LE S24_BE U24_LE U24_BE S32_LE S32_BE U32_LE U32_BE FLOAT_LE FLOAT_BE FLOAT64_LE FLOAT64_BE IEC958_SUBFRAME_LE IEC958_SUBFRAME_BE MU_LAW A_LAW IMA_ADPCM MPEG GSM SPECIAL S24_3LE S24_3BE U24_3LE U24_3BE S20_3LE S20_3BE U20_3LE U20_3BE S18_3LE S18_3BE U18_3LE U18_3BE G723_24 G723_24_1B G723_40 G723_40_1B DSD_U8 DSD_U16_LE
Noen av disse kan være utilgjengelige ved bruk av valgte maskinvarekomponenter
The available format shortcuts are:
-f cd (16 bit minst viktige byte først, 44100, stereo)
-f cdr (16 bit viktigste byte først, 44100, stereo)
-f dat (16 bit minst viktige byte først, 48000, stereo)  


```, 

[COLOR=#ff0000]lspci[/COLOR]shows soundcard:  ```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
```


I Didn't find any solution around the web, even ive ben looking for like 2 weeks now, what can I do?

---

### Post by vaiden2 on 2014-09-05
Hey there, I am new to linux and I had the same problem in Ubuntu, Mint, and Xubuntu (I'm new, so trying things out) and the thing that worked for me was doing this: in terminal open alsamixer and find <Auto-Mute> and switch it to 'Disabled' and close, no need to force reload, the sound started working for me right away. Hope this helps, because I've spent 2 days trying different fixes and workarounds with no results.

---

### Post by christoph5 on 2014-09-05
i have already tried that too before and it is on disabled, i have tried like every solution ive found on google searches also

---


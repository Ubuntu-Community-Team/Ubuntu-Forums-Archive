---
title: "Getting front audio jacks to work"
date: 2011-01-04
forum: Multimedia Software
---

### Post by ashfame on 2011-01-04
I run Ubuntu 10.10 on my Intel DG965RY. My front audio ports don't work  in Ubuntu, the rear one does. I never got it working earlier when I had  Ubuntu 10.04 but this time I am going to try it again.  My codec is **SigmaTel STAC9227**

  My ALSA information is **[here]("http://www.alsa-project.org/db/?f=95f8cb94c3bd2f013bdf3099c17700b383979eeb")**. 



  **Handy details:**
  !!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel
 I know something that I will have to change the model of my module to  make the front audio jack works but I couldn't find a model related  line in my ALSA configuration file - /etc/modprobe.d/alsa-base.conf (I  was able to get to that point in Ubuntu 10.04, may be something has  changed).
  

How can I proceed from here?

---

### Post by ashfame on 2011-01-04
```
Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8, ICH9, ICH10,
            PCH, SCH),
        ATI SB450, SB600, R600, RS600, RS690, RS780, RV610, RV620,
            RV630, RV635, RV670, RV770,
        VIA VT8251/VT8237A,
        SIS966, ULI M5461

    [Multiple options for each card instance]
    model    - force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = use LPIB, 2 = POSBUF)
    probe_mask  - Bitmask to probe codecs (default = -1, meaning all slots)
              When the bit 8 (0x100) is set, the lower 8 bits are used
          as the "fixed" codec slots; i.e. the driver probes the
          slots regardless what hardware reports back
    probe_only    - Only probing and no codec initialization (default=off);
          Useful to check the initial codec status for debugging
    bdl_pos_adj    - Specifies the DMA IRQ timing delay in samples.
        Passing -1 will make the driver to choose the appropriate
        value based on the controller chip.
    patch    - Specifies the early "patch" files to modify the HD-audio
            setup before initializing the codecs.  This option is
        available only when CONFIG_SND_HDA_PATCH_LOADER=y is set.
        See HD-Audio.txt for details.
    beep_mode    - Selects the beep registration mode (0=off, 1=on, 2=
        dynamic registration via mute switch on/off); the default
        value is set via CONFIG_SND_HDA_INPUT_BEEP_MODE kconfig.
    
    [Single (global) options]
    single_cmd  - Use single immediate commands to communicate with
        codecs (for debugging only)
    enable_msi    - Enable Message Signaled Interrupt (MSI) (default = off)
    power_save    - Automatic power-saving timeout (in second, 0 =
        disable)
    power_save_controller - Reset HD-audio controller in power-saving mode
        (default = on)

    This module supports multiple cards and autoprobe.
    
    See Documentation/sound/alsa/HD-Audio.txt for more details about
    HD-audio driver.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.  The list of available models
    is found in HD-Audio-Models.txt

    The model name "genric" is treated as a special case.  When this
    model is given, the driver uses the generic codec parser without
    "codec-patch".  It's sometimes good for testing and debugging.

    If the default configuration doesn't work and one of the above
    matches with your device, report it together with alsa-info.sh
    output (with --no-upload option) to kernel bugzilla or alsa-devel
    ML (see the section "Links and Addresses").

    power_save and power_save_controller options are for power-saving
    mode.  See powersave.txt for details.

    Note 2: If you get click noises on output, try the module option
        position_fix=1 or 2.  position_fix=1 will use the SD_LPIB
        register value without FIFO size correction as the current
        DMA pointer.  position_fix=2 will make the driver to use
        the position buffer instead of reading SD_LPIB register.
        (Usually SD_LPIB register is more accurate than the
        position buffer.)

    NB: If you get many "azx_get_response timeout" messages at
    loading, it's likely a problem of interrupts (e.g. ACPI irq
    routing).  Try to boot with options like "pci=noacpi".  Also, you
    can try "single_cmd=1" module option.  This will switch the
    communication method between HDA controller and codecs to the
    single immediate commands instead of CORB/RIRB.  Basically, the
    single command mode is provided only for BIOS, and you won't get
    unsolicited events, too.  But, at least, this works independently
    from the irq.  Remember this is a last resort, and should be
    avoided as much as possible...
    
    MORE NOTES ON "azx_get_response timeout" PROBLEMS:
    On some hardwares, you may need to add a proper probe_mask option
    to avoid the "azx_get_response timeout" problem above, instead.
    This occurs when the access to non-existing or non-working codec slot
    (likely a modem one) causes a stall of the communication via HD-audio
    bus.  You can see which codec slots are probed by enabling
    CONFIG_SND_DEBUG_VERBOSE, or simply from the file name of the codec
    proc files.  Then limit the slots to probe by probe_mask option.
    For example, probe_mask=1 means to probe only the first slot, and
    probe_mask=4 means only the third slot.

    The power-management is supported.

```

Possible models for my codec

```

STAC9227/9228/9229/927x
=======================
  ref        Reference board
  ref-no-jd    Reference board without HP/Mic jack detection
  3stack    D965 3stack
  5stack    D965 5stack + SPDIF
  5stack-no-fp    D965 5stack without front panel
  dell-3stack    Dell Dimension E520
  dell-bios    Fixes with Dell BIOS setup
  volknob    Fixes with volume-knob widget 0x24
  auto        BIOS setup (default)
```

Unfortunately, I have no idea how to use that information.

---

### Post by dasan on 2011-01-04
take konsole
give command  
alsamixer 

just see the configurations and remove any muted one.

---

### Post by ashfame on 2011-01-04
Hi dason,

I did and got this
[[IMG]http://img25.imageshack.us/img25/9233/003jq.th.png[/IMG]]("http://img25.imageshack.us/i/003jq.png/")

I am not sure if anything is muted. I tried lifting up those bars but to no gain.

---

### Post by lidex on 2011-01-04
Those channels with MM at the bottom are muted. To enable you use the arrow keys to navigate then hit the <M> key to unmute.

---

### Post by ashfame on 2011-01-04
Thanks! I unmuted them, change their values but still no sound

---

### Post by lidex on 2011-01-04
> **ashfame said:**
> Thanks! I unmuted them, change their values but still no sound

Front panel jacks are hit-or-miss, usually miss. Try going into your bios and toggling the front panel audio state. I forget the exact wording but mine has an option to use HD vs regular.

---

### Post by ashfame on 2011-01-04
> **lidex said:**
> Front panel jacks are hit-or-miss, usually miss. Try going into your bios and toggling the front panel audio state. I forget the exact wording but mine has an option to use HD vs regular.

Do I need to look for something like that when they used to work on windows fine?

**Edit:** I don't have any options in BIOS for front panel jacks, just the whole sound option to enable/disable.

---

### Post by ashfame on 2011-01-04
I tried every model listed for my codec but still couldn't get it to work.
```
options snd-hda-intel model=ref
options snd-hda-intel model=ref-no-jd
options snd-hda-intel model=3stack
options snd-hda-intel model=5stack
options snd-hda-intel model=5stack-no-fp
options snd-hda-intel model=dell-3stack
options snd-hda-intel model=dell-bios
options snd-hda-intel model=volknob
options snd-hda-intel model=auto
```

I tried them one by one by putting it at the end of  config file
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
After every change I force-reload alsa
```
sudo alsa force-reload
```


Does that confirm it as a bug?

---

### Post by ashfame on 2011-01-05
Anything else that I can try?

---

### Post by ashfame on 2011-01-07
Anyone else? I seriously need to fix it.
No movies no sound, moreover tomorrow is my birthday... lol

---

### Post by lidex on 2011-01-07
No, sorry. You have no rear jacks?

---

### Post by ashfame on 2011-01-07
I do, I use ear plugs to listen and its inconvenient to stay close to the desk to keep the plug plugg'ed in ear. What do you suggest I do? File a bug perhaps?

If its really fixable, then I can get more help there else its indeed a bug.

---

### Post by ashfame on 2011-01-08
Still looking for help!

---

### Post by ashfame on 2011-01-19
Bump!

---

### Post by ashfame on 2011-01-19
Bump!

---

### Post by Anubis on 2011-01-26
I feel your pain.

---

### Post by ptrinder64 on 2011-01-26
Is it just the front headphone jack you're trying to get working? If so, mine doesn't work as soon as you plug the headphone/speakers in, but if I go to 'Applications > Sound & Video > GNOME ALSA Mixer' (you may need to install it, but I'm guessing not) and put the speaker volume down to zero then my headphones/speakers work fine.

---

### Post by oukourj on 2011-03-24
Up, same problem here !
I tried unmuting everything in the alsamixer, but nothing works.

Note that I run Windows too on this machine and front ports work perfectly...

(EDIT: I'm on Maverick 64 too)

---


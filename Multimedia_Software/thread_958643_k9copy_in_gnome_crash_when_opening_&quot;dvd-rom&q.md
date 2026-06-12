---
title: "k9copy in gnome crash when opening &quot;dvd-rom&quot;s"
date: 2008-10-25
forum: Multimedia Software
---

### Post by shmi85 on 2008-10-25
Hi all --

Whenever I try and open a so-called "dvd-rom" (a disc that has extras/features when you run it in your cd-rom instead of your dvd player/tv) with k9copy, it crashes in two different ways. Sometimes it freezes and crashes and other times I get a "error in block 123456789" and then it crashes.

When I used dvd95, I get an "error reading dvd structure!" message.

I never have any problems playing the dvds (Totem, vlc, whatever) and I never have any problems opening other dvds in k9copy, it's just trying to open these specific "dvd-rom" discs inside of any copying software.

Has anyone else encountered this problem? Does anyone know of any work-arounds?

Thanks!

~Elisa

---

### Post by shmi85 on 2008-10-26
and here is the output when i run it from the terminal:

```

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1792 ***
*** for pgcit->pgci_srp[i].pgc_start_byte + PGC_SIZE <= pgcit->last_byte+1 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xd68e

*** libdvdread: CHECK_VALUE failed in ifo_read.c:766 ***
*** for pgc->nr_of_programs <= pgc->nr_of_cells ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:784 ***
*** for pgc->program_map_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:785 ***
*** for pgc->cell_playback_offset != 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:786 ***
*** for pgc->cell_position_offset != 0 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

libdvdread: Ignored UDF provided size of file.
libdvdread: Ignored UDF provided size of file.
*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

*** Zero check failed in ifo_read.c:765
    for pgc->zero_1 = 0xffff

*** libdvdread: CHECK_VALUE failed in ifo_read.c:780 ***
*** for pgc->program_map_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:781 ***
*** for pgc->cell_playback_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:782 ***
*** for pgc->cell_position_offset == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:608 ***
*** for PGC_COMMAND_TBL_SIZE + total * COMMAND_DATA_SIZE <= cmd_tbl->last_byte + 1U ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:609 ***
*** for total <= 255 ***

libdvdread: Invalid title IFO (VTS_05_0.IFO).
KCrash: Application 'k9copy' crashing...
KCrash cannot reach kdeinit, launching directly.
```

---

### Post by xc3RnbFO8P on 2008-10-26
Did install Medibuntu
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
and
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by shmi85 on 2008-10-26
yes, of course. I don't have any problems playing dvds, ripping non-interactual dvds; playing or using any other multimedia. I just have this very specific problem with ripping interactual dvds that I can't seem to figure out.

Thanks though!

---


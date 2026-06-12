---
title: "Can't burn successfully with nautilus-cd-burner (cdrecord error)"
date: 2006-08-05
forum: Multimedia &amp; Video
---

### Post by DamianABBA on 2006-08-05
I'm having problems burning cds using nautilus, when the progress bar is around 40% it suddenly goes to 100% and says the cd was burned successfully, but it's not. I tried enabling burnproof but the problem persists.

this is the output I get:

```

$ nautilus-cd-burner --source-iso=/home/damian/Desktop/Documents/rhinoceros.iso

(nautilus-cd-burner:5348): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(nautilus-cd-burner:5348): Gdk-WARNING **: locale not supported by C library

launching command: cdrecord fs=16m dev=/dev/hda -dao driveropts=burnfree -v -dat a -nopad /home/damian/Desktop/Documents/rhinoceros.iso
cdrecord stderr: cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord stderr: cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord stderr: cdrecord: If you have unexpected problems, please try Linux-2.4  or Solaris.
cdrecord stderr: scsidev: '/dev/hda'
cdrecord stderr: devname: '/dev/hda'
cdrecord stderr: scsibus: -2 target: -2 lun: -2
cdrecord stderr: Warning: Open by 'devname' is unintentional and not supported.
cdrecord stderr: Linux sg driver version: 3.5.27
cdrecord stderr: cdrecord: Warning: using inofficial version of libscg (debian-0 .8debian2 '@(#)scsitransp.c     1.91 04/06/17 Copyright 1988,1995,2000-2004 J. S chilling').
cdrecord stderr: SCSI buffer size: 64512
cdrecord stdout: Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 199 5-2004 Joerg Schilling
cdrecord stdout: NOTE: this version of cdrecord is an inofficial (modified) rele ase of cdrecord
cdrecord stdout:       and thus may have bugs that are not present in the origin al version.
cdrecord stdout:       Please send bug reports and support requests to <cdrtools @packages.debian.org>.
cdrecord stdout:       The original author should not be bothered with problems of this version.
cdrecord stdout:
cdrecord stdout: TOC Type: 1 = CD-ROM
cdrecord stdout: Using libscg version 'debian-0.8debian2'.
cdrecord stdout: Driveropts: 'burnfree'
cdrecord stdout: atapi: 1
cdrecord stdout: Device type    : Removable CD-ROM
cdrecord stdout: Version        : 0
cdrecord stdout: Response Format: 1
cdrecord stdout: Vendor_info    : 'SONY    '
cdrecord stdout: Identifikation : 'CD-RW  CRX230E5 '
cdrecord stdout: Revision       : '5.0K'
cdrecord stdout: Device seems to be: Generic mmc CD-RW.
cdrecord stdout: Current: 0x0009
cdrecord stdout: Profile: 0x000A
cdrecord stdout: Profile: 0x0009 (current)
cdrecord stdout: Profile: 0x0008
cdrecord stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
cdrecord stdout: Driver flags   : MMC-2 SWABAUDIO BURNFREE
cdrecord stdout: Supported modes: TAO PACKET SAO SAO/R96P RAW/R16 RAW/R96R
cdrecord stdout: Drive buf size : 1575840 = 1538 KB
cdrecord stdout: FIFO size      : 16777216 = 16384 KB
cdrecord stdout: Track 01: data   520 MB
cdrecord stdout: Total size:      598 MB (59:15.37) = 266653 sectors
cdrecord stdout: Lout start:      598 MB (59:17/28) = 266653 sectors
cdrecord stdout: Current Secsize: 2048
cdrecord stdout: ATIP info from disk:
cdrecord stdout:   Indicated writing power: 4
cdrecord stdout:   Is not unrestricted
cdrecord stdout:   Is not erasable
cdrecord stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
cdrecord stdout:   ATIP start of lead in:  -12508 (97:15/17)
cdrecord stdout:   ATIP start of lead out: 359845 (79:59/70)
cdrecord stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
cdrecord stdout: Manuf. index: 22
cdrecord stdout: Manufacturer: Ritek Co.
cdrecord stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 9 3192
cdrecord stdout: Starting to write CD/DVD at speed 40 in real SAO mode for singl e session.
cdrecord stdout: Last chance to quit, starting real write    0 seconds. Operatio n starts.
cdrecord stdout: Waiting for reader process to fill input buffer ... input buffe r ready.
cdrecord stdout: BURN-Free is ON.
cdrecord stdout: Performing OPC...
cdrecord stdout: Sending CUE sheet...
cdrecord stdout: Writing pregap for track 1 at 266653
cdrecord stdout: Starting new track at sector: 266803
cdrecord stdout: Track 01:    1 of  520 MB written (fifo  98%) [buf  92%]   1.3x 
cdrecord stdout: Track 01:    2 of  520 MB written (fifo 100%) [buf  97%]  35.1x 
cdrecord stdout: Track 01:    3 of  520 MB written (fifo  99%) [buf  97%]  34.0x 
cdrecord stdout: Track 01:    4 of  520 MB written (fifo 100%) [buf  97%]  32.9x 
cdrecord stdout: Track 01:    5 of  520 MB written (fifo 100%) [buf  97%]  33.9x 
cdrecord stdout: Track 01:    6 of  520 MB written (fifo 100%) [buf  97%]  32.9x 
cdrecord stdout: Track 01:    7 of  520 MB written (fifo  99%) [buf  97%]  33.8x 
cdrecord stdout: Track 01:    8 of  520 MB written (fifo  98%) [buf  33%]  10.5x 
cdrecord stdout: Track 01:    9 of  520 MB written (fifo  99%) [buf  97%]   1.4x 
cdrecord stdout: Track 01:   10 of  520 MB written (fifo  99%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:   11 of  520 MB written (fifo 100%) [buf  96%]  42.0x 
cdrecord stdout: Track 01:   12 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:   13 of  520 MB written (fifo 100%) [buf  96%]  42.0x 
cdrecord stdout: Track 01:   14 of  520 MB written (fifo 100%) [buf  96%]  40.7x 
cdrecord stdout: Track 01:   15 of  520 MB written (fifo 100%) [buf  97%]  42.1x 
cdrecord stdout: Track 01:   16 of  520 MB written (fifo  99%) [buf  97%]  40.6x 
cdrecord stdout: Track 01:   17 of  520 MB written (fifo 100%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:   18 of  520 MB written (fifo  99%) [buf  97%]  40.6x 
cdrecord stdout: Track 01:   19 of  520 MB written (fifo  99%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:   20 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:   21 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:   22 of  520 MB written (fifo 100%) [buf  96%]  40.4x 
cdrecord stdout: Track 01:   23 of  520 MB written (fifo  99%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:   24 of  520 MB written (fifo 100%) [buf  97%]  40.3x 
cdrecord stdout: Track 01:   25 of  520 MB written (fifo  99%) [buf  96%]  41.5x 
cdrecord stdout: Track 01:   26 of  520 MB written (fifo  99%) [buf  96%]  40.2x 
cdrecord stdout: Track 01:   27 of  520 MB written (fifo 100%) [buf  97%]  41.5x 
cdrecord stdout: Track 01:   28 of  520 MB written (fifo 100%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:   29 of  520 MB written (fifo  99%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:   30 of  520 MB written (fifo 100%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:   31 of  520 MB written (fifo  99%) [buf  97%]  41.3x 
cdrecord stdout: Track 01:   32 of  520 MB written (fifo 100%) [buf  97%]  40.0x 
cdrecord stdout: Track 01:   33 of  520 MB written (fifo  99%) [buf  97%]  41.2x 
cdrecord stdout: Track 01:   34 of  520 MB written (fifo  99%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:   35 of  520 MB written (fifo  99%) [buf  97%]  41.1x 
cdrecord stdout: Track 01:   36 of  520 MB written (fifo  99%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:   37 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:   38 of  520 MB written (fifo 100%) [buf  96%]  42.2x 
cdrecord stdout: Track 01:   39 of  520 MB written (fifo 100%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:   40 of  520 MB written (fifo 100%) [buf  96%]  42.2x 
cdrecord stdout: Track 01:   41 of  520 MB written (fifo 100%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:   42 of  520 MB written (fifo 100%) [buf  96%]  42.0x 
cdrecord stdout: Track 01:   43 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:   44 of  520 MB written (fifo 100%) [buf  97%]  42.1x 
cdrecord stdout: Track 01:   45 of  520 MB written (fifo 100%) [buf  97%]  40.7x 
cdrecord stdout: Track 01:   46 of  520 MB written (fifo  99%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:   47 of  520 MB written (fifo 100%) [buf  97%]  40.6x 
cdrecord stdout: Track 01:   48 of  520 MB written (fifo 100%) [buf  96%]  41.8x 
cdrecord stdout: Track 01:   49 of  520 MB written (fifo  99%) [buf  97%]  40.7x 
cdrecord stdout: Track 01:   50 of  520 MB written (fifo  99%) [buf  97%]  41.8x 
cdrecord stdout: Track 01:   51 of  520 MB written (fifo 100%) [buf  96%]  40.4x 
cdrecord stdout: Track 01:   52 of  520 MB written (fifo 100%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:   53 of  520 MB written (fifo  99%) [buf  96%]  40.3x 
cdrecord stdout: Track 01:   54 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:   55 of  520 MB written (fifo  99%) [buf  97%]  40.3x 
cdrecord stdout: Track 01:   56 of  520 MB written (fifo  99%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:   57 of  520 MB written (fifo  99%) [buf  96%]  40.2x 
cdrecord stdout: Track 01:   58 of  520 MB written (fifo  99%) [buf  97%]  41.5x 
cdrecord stdout: Track 01:   59 of  520 MB written (fifo  99%) [buf  96%]  40.1x 
cdrecord stdout: Track 01:   60 of  520 MB written (fifo  99%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:   61 of  520 MB written (fifo 100%) [buf  97%]  40.0x 
cdrecord stdout: Track 01:   62 of  520 MB written (fifo 100%) [buf  97%]  41.3x 
cdrecord stdout: Track 01:   63 of  520 MB written (fifo  99%) [buf  96%]  40.0x 
cdrecord stdout: Track 01:   64 of  520 MB written (fifo 100%) [buf  97%]  41.2x 
cdrecord stdout: Track 01:   65 of  520 MB written (fifo  99%) [buf  96%]  42.3x 
cdrecord stdout: Track 01:   66 of  520 MB written (fifo 100%) [buf  96%]  41.1x 
cdrecord stdout: Track 01:   67 of  520 MB written (fifo 100%) [buf  97%]  42.5x 
cdrecord stdout: Track 01:   68 of  520 MB written (fifo  99%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:   69 of  520 MB written (fifo  99%) [buf  97%]  42.2x 
cdrecord stdout: Track 01:   70 of  520 MB written (fifo  99%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:   71 of  520 MB written (fifo  99%) [buf  97%]  42.2x 
cdrecord stdout: Track 01:   72 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:   73 of  520 MB written (fifo 100%) [buf  97%]  42.0x 
cdrecord stdout: Track 01:   74 of  520 MB written (fifo  99%) [buf  96%]  40.8x 
cdrecord stdout: Track 01:   75 of  520 MB written (fifo 100%) [buf  96%]  42.0x 
cdrecord stdout: Track 01:   76 of  520 MB written (fifo  99%) [buf  96%]  40.8x 
cdrecord stdout: Track 01:   77 of  520 MB written (fifo 100%) [buf  97%]  42.1x 
cdrecord stdout: Track 01:   78 of  520 MB written (fifo 100%) [buf  97%]  40.6x 
cdrecord stdout: Track 01:   79 of  520 MB written (fifo 100%) [buf  97%]  42.0x 
cdrecord stdout: Track 01:   80 of  520 MB written (fifo 100%) [buf  96%]  40.4x 
cdrecord stdout: Track 01:   81 of  520 MB written (fifo  99%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:   82 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:   83 of  520 MB written (fifo  99%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:   84 of  520 MB written (fifo 100%) [buf  97%]  40.4x 
cdrecord stdout: Track 01:   85 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:   86 of  520 MB written (fifo 100%) [buf  97%]  40.3x 
cdrecord stdout: Track 01:   87 of  520 MB written (fifo  99%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:   88 of  520 MB written (fifo  99%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:   89 of  520 MB written (fifo  99%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:   90 of  520 MB written (fifo  99%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:   91 of  520 MB written (fifo 100%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:   92 of  520 MB written (fifo  99%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:   93 of  520 MB written (fifo  99%) [buf  97%]  41.3x 
cdrecord stdout: Track 01:   94 of  520 MB written (fifo  99%) [buf  97%]  40.1x 
cdrecord stdout: Track 01:   95 of  520 MB written (fifo 100%) [buf  97%]  41.1x 
cdrecord stdout: Track 01:   96 of  520 MB written (fifo  99%) [buf  96%]  42.4x 
cdrecord stdout: Track 01:   97 of  520 MB written (fifo 100%) [buf  97%]  41.1x 
cdrecord stdout: Track 01:   98 of  520 MB written (fifo  99%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:   99 of  520 MB written (fifo 100%) [buf  96%]  40.9x 
cdrecord stdout: Track 01:  100 of  520 MB written (fifo  99%) [buf  96%]  42.3x 
cdrecord stdout: Track 01:  101 of  520 MB written (fifo  99%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:  102 of  520 MB written (fifo  99%) [buf  97%]  42.3x 
cdrecord stdout: Track 01:  103 of  520 MB written (fifo 100%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:  104 of  520 MB written (fifo  99%) [buf  96%]  42.1x 
cdrecord stdout: Track 01:  105 of  520 MB written (fifo 100%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  106 of  520 MB written (fifo  99%) [buf  96%]  41.7x 
cdrecord stdout: Track 01:  107 of  520 MB written (fifo 100%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  108 of  520 MB written (fifo  99%) [buf  96%]  41.9x 
cdrecord stdout: Track 01:  109 of  520 MB written (fifo 100%) [buf  97%]  40.7x 
cdrecord stdout: Track 01:  110 of  520 MB written (fifo 100%) [buf  97%]  42.0x 
cdrecord stdout: Track 01:  111 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  112 of  520 MB written (fifo 100%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:  113 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  114 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:  115 of  520 MB written (fifo  99%) [buf  97%]  40.4x 
cdrecord stdout: Track 01:  116 of  520 MB written (fifo 100%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:  117 of  520 MB written (fifo  99%) [buf  96%]  40.3x 
cdrecord stdout: Track 01:  118 of  520 MB written (fifo 100%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:  119 of  520 MB written (fifo  99%) [buf  97%]  40.3x 
cdrecord stdout: Track 01:  120 of  520 MB written (fifo 100%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:  121 of  520 MB written (fifo  99%) [buf  97%]  40.3x 
cdrecord stdout: Track 01:  122 of  520 MB written (fifo  99%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:  123 of  520 MB written (fifo  99%) [buf  97%]  40.1x 
cdrecord stdout: Track 01:  124 of  520 MB written (fifo 100%) [buf  97%]  41.2x 
cdrecord stdout: Track 01:  125 of  520 MB written (fifo  99%) [buf  96%]  40.0x 
cdrecord stdout: Track 01:  126 of  520 MB written (fifo 100%) [buf  96%]  41.1x 
cdrecord stdout: Track 01:  127 of  520 MB written (fifo  99%) [buf  97%]  42.6x 
cdrecord stdout: Track 01:  128 of  520 MB written (fifo 100%) [buf  96%]  41.0x 
cdrecord stdout: Track 01:  129 of  520 MB written (fifo 100%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:  130 of  520 MB written (fifo  99%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:  131 of  520 MB written (fifo  99%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:  132 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  133 of  520 MB written (fifo  99%) [buf  97%]  42.3x 
cdrecord stdout: Track 01:  134 of  520 MB written (fifo 100%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:  135 of  520 MB written (fifo 100%) [buf  97%]  42.1x 
cdrecord stdout: Track 01:  136 of  520 MB written (fifo  99%) [buf  96%]  40.8x 
cdrecord stdout: Track 01:  137 of  520 MB written (fifo  99%) [buf  97%]  42.1x 
cdrecord stdout: Track 01:  138 of  520 MB written (fifo  99%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:  139 of  520 MB written (fifo  99%) [buf  97%]  41.8x 
cdrecord stdout: Track 01:  140 of  520 MB written (fifo 100%) [buf  97%]  40.6x 
cdrecord stdout: Track 01:  141 of  520 MB written (fifo  99%) [buf  97%]  42.0x 
cdrecord stdout: Track 01:  142 of  520 MB written (fifo 100%) [buf  97%]  40.6x 
cdrecord stdout: Track 01:  143 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:  144 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  145 of  520 MB written (fifo 100%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:  146 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  147 of  520 MB written (fifo  99%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:  148 of  520 MB written (fifo  99%) [buf  97%]  40.3x 
cdrecord stdout: Track 01:  149 of  520 MB written (fifo  99%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:  150 of  520 MB written (fifo 100%) [buf  97%]  40.1x 
cdrecord stdout: Track 01:  151 of  520 MB written (fifo 100%) [buf  97%]  41.5x 
cdrecord stdout: Track 01:  152 of  520 MB written (fifo  98%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:  153 of  520 MB written (fifo  99%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:  154 of  520 MB written (fifo  99%) [buf  97%]  40.1x 
cdrecord stdout: Track 01:  155 of  520 MB written (fifo  99%) [buf  97%]  41.3x 
cdrecord stdout: Track 01:  156 of  520 MB written (fifo  99%) [buf  97%]  40.0x 
cdrecord stdout: Track 01:  157 of  520 MB written (fifo  99%) [buf  97%]  41.1x 
cdrecord stdout: Track 01:  158 of  520 MB written (fifo 100%) [buf  97%]  42.5x 
cdrecord stdout: Track 01:  159 of  520 MB written (fifo  99%) [buf  97%]  41.1x 
cdrecord stdout: Track 01:  160 of  520 MB written (fifo  99%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:  161 of  520 MB written (fifo  99%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:  162 of  520 MB written (fifo  99%) [buf  96%]  42.1x 
cdrecord stdout: Track 01:  163 of  520 MB written (fifo  99%) [buf  97%]  41.0x 
cdrecord stdout: Track 01:  164 of  520 MB written (fifo  99%) [buf  97%]  42.2x 
cdrecord stdout: Track 01:  165 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  166 of  520 MB written (fifo  99%) [buf  97%]  42.2x 
cdrecord stdout: Track 01:  167 of  520 MB written (fifo 100%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:  168 of  520 MB written (fifo  99%) [buf  97%]  42.0x 
cdrecord stdout: Track 01:  169 of  520 MB written (fifo  99%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:  170 of  520 MB written (fifo 100%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:  171 of  520 MB written (fifo  99%) [buf  96%]  40.4x 
cdrecord stdout: Track 01:  172 of  520 MB written (fifo 100%) [buf  96%]  42.0x 
cdrecord stdout: Track 01:  173 of  520 MB written (fifo  99%) [buf  97%]  40.7x 
cdrecord stdout: Track 01:  174 of  520 MB written (fifo  99%) [buf  97%]  41.8x 
cdrecord stdout: Track 01:  175 of  520 MB written (fifo  99%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  176 of  520 MB written (fifo 100%) [buf  96%]  41.5x 
cdrecord stdout: Track 01:  177 of  520 MB written (fifo  99%) [buf  97%]  40.5x
cdrecord stdout: Track 01:  178 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:  179 of  520 MB written (fifo  99%) [buf  96%]  40.3x 
cdrecord stdout: Track 01:  180 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:  181 of  520 MB written (fifo  99%) [buf  96%]  40.1x 
cdrecord stdout: Track 01:  182 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:  183 of  520 MB written (fifo  99%) [buf  97%]  40.1x 
cdrecord stdout: Track 01:  184 of  520 MB written (fifo  99%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:  185 of  520 MB written (fifo  99%) [buf  97%]  40.2x 
cdrecord stdout: Track 01:  186 of  520 MB written (fifo  99%) [buf  97%]  41.4x 
cdrecord stdout: Track 01:  187 of  520 MB written (fifo  99%) [buf  97%]  39.9x 
cdrecord stdout: Track 01:  188 of  520 MB written (fifo 100%) [buf  97%]  41.2x 
cdrecord stdout: Track 01:  189 of  520 MB written (fifo  99%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:  190 of  520 MB written (fifo  99%) [buf  96%]  41.0x 
cdrecord stdout: Track 01:  191 of  520 MB written (fifo 100%) [buf  97%]  42.4x 
cdrecord stdout: Track 01:  192 of  520 MB written (fifo 100%) [buf  97%]  41.1x 
cdrecord stdout: Track 01:  193 of  520 MB written (fifo 100%) [buf  97%]  42.2x 
cdrecord stdout: Track 01:  194 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  195 of  520 MB written (fifo 100%) [buf  97%]  42.1x 
cdrecord stdout: Track 01:  196 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  197 of  520 MB written (fifo  99%) [buf  96%]  42.1x 
cdrecord stdout: Track 01:  198 of  520 MB written (fifo  99%) [buf  97%]  40.9x 
cdrecord stdout: Track 01:  199 of  520 MB written (fifo 100%) [buf  97%]  42.0x 
cdrecord stdout: Track 01:  200 of  520 MB written (fifo 100%) [buf  97%]  40.8x 
cdrecord stdout: Track 01:  201 of  520 MB written (fifo 100%) [buf  96%]  41.9x 
cdrecord stdout: Track 01:  202 of  520 MB written (fifo  99%) [buf  97%]  40.7x 
cdrecord stdout: Track 01:  203 of  520 MB written (fifo 100%) [buf  97%]  41.9x 
cdrecord stdout: Track 01:  204 of  520 MB written (fifo  98%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  205 of  520 MB written (fifo  99%) [buf  97%]  41.8x 
cdrecord stdout: Track 01:  206 of  520 MB written (fifo 100%) [buf  97%]  40.5x 
cdrecord stdout: Track 01:  207 of  520 MB written (fifo 100%) [buf  97%]  41.7x 
cdrecord stdout: Track 01:  208 of  520 MB written (fifo  99%) [buf  97%]  40.4x 
cdrecord stdout: Track 01:  209 of  520 MB written (fifo  99%) [buf  97%]  41.6x 
cdrecord stdout: Track 01:  210 of  520 MB written (fifo  99%) [buf  97%]  40.4x 
cdrecord stdout: Track 01:  211 of  520 MB written (fifo  99%) [buf  97%]  41.5x 
cdrecord stdout: Track 01:  212 of  520 MB written (fifo  99%) [buf  96%]  40.3x 
cdrecord stderr: cdrecord: Success. write_g1: scsi sendcmd: no error
cdrecord stderr: CDB:  2A 00 00 05 BC 35 00 00 1F 00
cdrecord stderr: status: 0x2 (CHECK CONDITION)
cdrecord stderr: Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
cdrecord stderr: Sense Key: 0x3 Medium Error, Segment 0
cdrecord stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
cdrecord stderr: Sense flags: Blk 0 (not valid)
cdrecord stderr: resid: 63488
cdrecord stderr: cmd finished after 9.698s timeout 200s
cdrecord stderr: cdrecord: A write error occured.
cdrecord stderr: cdrecord: Please properly read the error message above.
cdrecord stdout: Track 01:  213 of  520 MB written (fifo  99%) [buf  97%]  41.5x .
cdrecord stdout: write track data: error after 223350784 bytes
cdrecord stdout: Writing  time:   86.052s
cdrecord stdout: Average write speed  44.0x.
cdrecord stdout: Min drive buffer fill was 33%
cdrecord stdout: Fixating...
cdrecord stdout: Fixating time:    0.002s
process stdout: HUP
cdrecord stderr: cdrecord: fifo had 3773 puts and 3519 gets.

```

---

### Post by DamianABBA on 2006-08-06
Should I post this on other forum?

---

### Post by DamianABBA on 2006-08-26
I still need help with this. :(

---


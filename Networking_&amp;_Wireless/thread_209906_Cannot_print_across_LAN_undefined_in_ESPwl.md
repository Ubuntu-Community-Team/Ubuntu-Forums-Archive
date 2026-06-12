---
title: "Cannot print across LAN: /undefined in ESPwl"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by raboof on 2006-07-05
I'm having trouble setting up print sharing.  Two computers form the LAN (alpha and krusty) and each has a printer.  The printers both work locally and both computers can see the other's printer.  I can sucessfully print on alpha's printer from krusty but not vice versa.  I can send a test page from alpha to krusty but ghostscript dies and nothing prints.

alpha - Gentoo - Cups 1.1.23-r8
krusty - Ubuntu 6.06 - Cups 1.2.0-0ubuntu5 - ESP Ghostscript 8.15.2.dfsg.0ubuntu1-0ubuntu1

Here is the debug output from /var/log/cups/error_log on krusty.

I [05/Jul/2006:14:23:09 -0600] Job 22 queued on "LaserJet-4L" by "sheldon".
D [05/Jul/2006:14:23:09 -0600] Job 22 hold_until = 0
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[0]="LaserJet-4L"
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[1]="22"
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[2]="sheldon"
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[3]="Test Page"
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[4]="1"
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[5]="job-uuid=urn:uuid:e5662f2f-03f2-3a38-5fdc-029937f452b5"
D [05/Jul/2006:14:23:09 -0600] [Job 22] argv[6]="/var/spool/cups/d00022-001"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[9]="SERVER_ADMIN=root@krusty"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[10]="SOFTWARE=CUPS/1.2.0"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[11]="TMPDIR=/var/spool/cups/tmp"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[12]="TZ=America/Regina"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[13]="USER=root"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[16]="IPP_PORT=631"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[17]="CHARSET=us-ascii"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[18]="LANG=en"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[19]="PPD=/etc/cups/ppd/LaserJet-4L.ppd"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[20]="RIP_MAX_CACHE=8m"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[21]="CONTENT_TYPE=application/postscript"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[22]="DEVICE_URI=hp:/par/LaserJet_4L?device=/dev/parport0"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[23]="PRINTER=LaserJet-4L"
D [05/Jul/2006:14:23:09 -0600] [Job 22] envp[24]="FINAL_CONTENT_TYPE=printer/LaserJet-4L"
D [05/Jul/2006:14:23:09 -0600] [Job 22] Page = 595x842; 0,0 to 595,842
D [05/Jul/2006:14:23:09 -0600] [Job 22] slow_collate=0, slow_duplex=0, slow_order=0
D [05/Jul/2006:14:23:09 -0600] [Job 22] Before copy_comments - %!PS-Adobe-3.0 EPSF-3.0
D [05/Jul/2006:14:23:09 -0600] [Job 22] %!PS-Adobe-3.0 EPSF-3.0
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%BoundingBox: 0 0 612 792
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%Pages: 0
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%Creator: Sun Microsystems, Inc.
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%Title: none
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%CreationDate: none
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%LanguageLevel: 2
D [05/Jul/2006:14:23:09 -0600] [Job 22] %%EndComments
D [05/Jul/2006:14:23:09 -0600] [Job 22] Before copy_prolog - %%BeginProlog
D [05/Jul/2006:14:23:09 -0600] [Job 22] Before copy_setup - %%BeginSetup
D [05/Jul/2006:14:23:09 -0600] [Job 22] Before page loop - %%Page: 1 1
D [05/Jul/2006:14:23:09 -0600] [Job 22] Copying page 1...
D [05/Jul/2006:14:23:09 -0600] [Job 22] pagew = 595.0, pagel = 842.0
D [05/Jul/2006:14:23:09 -0600] [Job 22] bboxw = 595, bboxl = 842
D [05/Jul/2006:14:23:09 -0600] [Job 22] PageLeft = 0.0, PageRight = 595.0
D [05/Jul/2006:14:23:09 -0600] [Job 22] PageTop = 842.0, PageBottom = 0.0
D [05/Jul/2006:14:23:09 -0600] [Job 22] PageWidth = 595.0, PageLength = 842.0
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Setting locale failed.
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Please check that your locale settings:
D [05/Jul/2006:14:23:09 -0600] [Job 22] LANGUAGE = (unset),
D [05/Jul/2006:14:23:09 -0600] [Job 22] LC_ALL = (unset),
D [05/Jul/2006:14:23:09 -0600] [Job 22] LANG = "en"
D [05/Jul/2006:14:23:09 -0600] [Job 22] are supported and installed on your system.
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Falling back to the standard locale ("C").
D [05/Jul/2006:14:23:09 -0600] [Job 22] invalid ModelQueryResult: msg=modelqueryresult
D [05/Jul/2006:14:23:09 -0600] [Job 22] result-code=48
D [05/Jul/2006:14:23:09 -0600] [Job 22] prnt/hpijs/hplip_api.c 396
D [05/Jul/2006:14:23:09 -0600] [Job 22] foomatic-rip version $Revision: 3.43.2.15 $ running...
D [05/Jul/2006:14:23:09 -0600] [Job 22] Parsing PPD file ...
D [05/Jul/2006:14:23:09 -0600] [Job 22] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option ColorSpace
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option PageSize
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option PageRegion
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option ImageableArea
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option PaperDimension
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option InputSlot
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option Manualfeed
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option Resolution
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option Economode
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option Copies
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option HalftoningAlgorithm
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option REt
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option TonerDensity
D [05/Jul/2006:14:23:09 -0600] [Job 22] Added option Font
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] Parameter Summary
D [05/Jul/2006:14:23:09 -0600] [Job 22] -----------------
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] Spooler: cups
D [05/Jul/2006:14:23:09 -0600] [Job 22] Printer: LaserJet-4L
D [05/Jul/2006:14:23:09 -0600] [Job 22] PPD file: /etc/cups/ppd/LaserJet-4L.ppd
D [05/Jul/2006:14:23:09 -0600] [Job 22] Printer model: HP LaserJet 4L Foomatic/ljet4 (recommended)
D [05/Jul/2006:14:23:09 -0600] [Job 22] Job title: Test Page
D [05/Jul/2006:14:23:09 -0600] [Job 22] File(s) to be printed:
D [05/Jul/2006:14:23:09 -0600] [Job 22] <STDIN>
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [05/Jul/2006:14:23:09 -0600] [Job 22] Pondering option 'job-uuid=urn:uuid:e5662f2f-03f2-3a38-5fdc-029937f452b5 '
D [05/Jul/2006:14:23:09 -0600] [Job 22] Unknown option job-uuid=urn:uuid:e5662f2f-03f2-3a38-5fdc-029937f452b5.
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] ================================================
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] File: <STDIN>
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] ================================================
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] Reading PostScript input ...
D [05/Jul/2006:14:23:09 -0600] [Job 22] --> This document is DSC-conforming!
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] -----------
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginProlog
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%EndProlog
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] -----------
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginSetup
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *PageRegion A4
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: PageRegion=A4 --> Option will be set by PostScript interpreter
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *InputSlot Default
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: InputSlot=Default --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %% FoomaticRIPOptionSetting: InputSlot=Default
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: InputSlot=Default --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *Manualfeed Off
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Manualfeed=Off --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %% FoomaticRIPOptionSetting: Manualfeed=Off
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Manualfeed=Off --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *Economode Off
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Economode=Off --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %% FoomaticRIPOptionSetting: Economode=Off
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Economode=Off --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *Copies 1
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Copies=1 --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %% FoomaticRIPOptionSetting: Copies=1
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Copies=1 --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *REt Medium
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: REt=Medium --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %% FoomaticRIPOptionSetting: REt=Medium
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: REt=Medium --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *TonerDensity 3
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: TonerDensity=3 --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %% FoomaticRIPOptionSetting: TonerDensity=3
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: TonerDensity=3 --> Setting option
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginFeature: *Resolution 300x300dpi
D [05/Jul/2006:14:23:09 -0600] [Job 22] Option: Resolution=300x300dpi --> Option will be set by PostScript inter preter
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%EndSetup
D [05/Jul/2006:14:23:09 -0600] [Job 22] Inserting PostScript code for CUPS' page accounting
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] -----------
D [05/Jul/2006:14:23:09 -0600] [Job 22] New page:  1 1
D [05/Jul/2006:14:23:09 -0600] [Job 22] Inserting option code into "PageSetup" section.
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%BeginPageSetup
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found: %%EndPageSetup
D [05/Jul/2006:14:23:09 -0600] [Job 22] End of page header
D [05/Jul/2006:14:23:09 -0600] [Job 22] Stopping search for page header options
D [05/Jul/2006:14:23:09 -0600] [Job 22] Found:
D [05/Jul/2006:14:23:09 -0600] [Job 22] 272.61532 887.70906 l  286.04014 909.21911 l  300.83795 929.43245 l
D [05/Jul/2006:14:23:09 -0600] [Job 22] --> Output goes directly to the renderer now.
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] Starting renderer
D [05/Jul/2006:14:23:09 -0600] [Job 22] JCL: %-12345X@PJL
D [05/Jul/2006:14:23:09 -0600] [Job 22] @PJL SET MANUALFEED=OFF
D [05/Jul/2006:14:23:09 -0600] [Job 22] @PJL SET ECONOMODE=OFF
D [05/Jul/2006:14:23:09 -0600] [Job 22] @PJL SET COPIES=1
D [05/Jul/2006:14:23:09 -0600] [Job 22] @PJL SET RET=MEDIUM
D [05/Jul/2006:14:23:09 -0600] [Job 22] @PJL SET DENSITY=3
D [05/Jul/2006:14:23:09 -0600] [Job 22] <job data>
D [05/Jul/2006:14:23:09 -0600] [Job 22] %-12345X@PJL RESET
D [05/Jul/2006:14:23:09 -0600] [Job 22]
D [05/Jul/2006:14:23:09 -0600] [Job 22] renderer PID kid4=17707
D [05/Jul/2006:14:23:09 -0600] [Job 22] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dNOPAUSE -sDEVICE=ljet4  -sOutputFile=- - | perl -p -0033 -e " s/^&l\d+[aA]/$&/; "
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Setting locale failed.
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Please check that your locale settings:
D [05/Jul/2006:14:23:09 -0600] [Job 22] LANGUAGE = (unset),
D [05/Jul/2006:14:23:09 -0600] [Job 22] LC_ALL = (unset),
D [05/Jul/2006:14:23:09 -0600] [Job 22] LANG = "en"
D [05/Jul/2006:14:23:09 -0600] [Job 22] are supported and installed on your system.
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Falling back to the standard locale ("C").
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Setting locale failed.
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Please check that your locale settings:
D [05/Jul/2006:14:23:09 -0600] [Job 22] LANGUAGE = (unset),
D [05/Jul/2006:14:23:09 -0600] [Job 22] LC_ALL = (unset),
D [05/Jul/2006:14:23:09 -0600] [Job 22] LANG = "en"
D [05/Jul/2006:14:23:09 -0600] [Job 22] are supported and installed on your system.
D [05/Jul/2006:14:23:09 -0600] [Job 22] perl: warning: Falling back to the standard locale ("C").
D [05/Jul/2006:14:23:09 -0600] [Job 22] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dNOPAUSE' '-sDEVICE =ljet4' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [05/Jul/2006:14:23:09 -0600] [Job 22] ESP Ghostscript 815.02 (2006-04-19)
D [05/Jul/2006:14:23:09 -0600] [Job 22] Copyright (C) 2004 artofcode LLC, Benicia, CA.  All rights reserved.
D [05/Jul/2006:14:23:09 -0600] [Job 22] This software comes with NO WARRANTY: see the file PUBLIC for details.
D [05/Jul/2006:14:23:10 -0600] [Job 22] Wrote 1 pages...
D [05/Jul/2006:14:23:10 -0600] [Job 22]
D [05/Jul/2006:14:23:10 -0600] [Job 22] Closing renderer
E [05/Jul/2006:14:23:10 -0600] [Job 22] /undefined in ESPwl
D [05/Jul/2006:14:23:10 -0600] [Job 22] Operand stack:
D [05/Jul/2006:14:23:10 -0600] [Job 22]
D [05/Jul/2006:14:23:10 -0600] [Job 22] Execution stack:
D [05/Jul/2006:14:23:10 -0600] [Job 22] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostrin gval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1    3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   1   3   %oparray_pop   .runexec2   --nostrin gval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
D [05/Jul/2006:14:23:10 -0600] [Job 22] Dictionary stack:
D [05/Jul/2006:14:23:10 -0600] [Job 22] --dict:1121/1686(ro)(G)--   --dict:0/20(G)--   --dict:82/200(L)--
D [05/Jul/2006:14:23:10 -0600] [Job 22] Current allocation mode is local
D [05/Jul/2006:14:23:10 -0600] [Job 22] Last OS error: 2
D [05/Jul/2006:14:23:10 -0600] [Job 22] ESP Ghostscript 815.02: Unrecoverable error, exit code 1
D [05/Jul/2006:14:23:10 -0600] [Job 22] tail process done writing data to STDOUT
D [05/Jul/2006:14:23:10 -0600] [Job 22] KID4 finished
D [05/Jul/2006:14:23:10 -0600] [Job 22] KID3 exited with status 0
D [05/Jul/2006:14:23:10 -0600] [Job 22] KID4 exited with status 0
D [05/Jul/2006:14:23:10 -0600] [Job 22] Renderer exit stat: 0
D [05/Jul/2006:14:23:10 -0600] [Job 22] KID3 finished
D [05/Jul/2006:14:23:10 -0600] [Job 22] Renderer process finished
D [05/Jul/2006:14:23:10 -0600] [Job 22]
D [05/Jul/2006:14:23:10 -0600] [Job 22] Closing foomatic-rip.
D [05/Jul/2006:14:23:39 -0600] [Job 22] File 0 is complete.

---


---
title: "smb failed trying to print"
date: 2011-04-16
forum: Networking &amp; Wireless
---

### Post by ranger_cole on 2011-04-16
Using Ubuntu 10.10 and trying to print to a found and verified windows 7 connected samsung ml2010 printer.  I get the following error when I try to print:
/usr/lib/cups/backend/smb failed.

Here is the error log:

D [16/Apr/2011:12:58:30 -0500] [Job 21] The following messages were recorded from 12:58:29 to 12:58:30
D [16/Apr/2011:12:58:30 -0500] [Job 21] Adding start banner page "none".
D [16/Apr/2011:12:58:30 -0500] [Job 21] Adding end banner page "none".
D [16/Apr/2011:12:58:30 -0500] [Job 21] File of type application/postscript queued by "maclite".
D [16/Apr/2011:12:58:30 -0500] [Job 21] hold_until=0
D [16/Apr/2011:12:58:30 -0500] [Job 21] Queued on "Samsung-ML-2010" by "maclite".
D [16/Apr/2011:12:58:30 -0500] [Job 21] job-sheets=none,none
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[0]="Samsung-ML-2010"
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[1]="21"
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[2]="maclite"
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[3]="Test Page"
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[4]="1"
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[5]="PageSize=Letter job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e job-originating-host-name=localhost"
D [16/Apr/2011:12:58:30 -0500] [Job 21] argv[6]="/var/spool/cups/d00021-001"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[8]="HOME=/var/spool/cups/tmp"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[10]="SERVER_ADMIN=root@ubuntu"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[11]="SOFTWARE=CUPS/1.4.4"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[13]="USER=root"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[16]="IPP_PORT=631"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[17]="CHARSET=utf-8"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[18]="LANG=en_US.UTF-8"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[19]="PPD=/etc/cups/ppd/Samsung-ML-2010.ppd"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[20]="RIP_MAX_CACHE=auto"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[21]="CONTENT_TYPE=application/postscript"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[22]="DEVICE_URI=smb://jaypugh-PC/SAMSUNG"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[23]="PRINTER_INFO=Samsung ML-2010"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[24]="PRINTER_LOCATION="
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[25]="PRINTER=Samsung-ML-2010"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[26]="CUPS_FILETYPE=document"
D [16/Apr/2011:12:58:30 -0500] [Job 21] envp[27]="FINAL_CONTENT_TYPE=printer/Samsung-ML-2010"
D [16/Apr/2011:12:58:30 -0500] [Job 21] Started filter /usr/lib/cups/filter/pstopdf (PID 2765)
D [16/Apr/2011:12:58:30 -0500] [Job 21] Started filter /usr/lib/cups/filter/pdftopdf (PID 2766)
D [16/Apr/2011:12:58:30 -0500] [Job 21] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2767)
D [16/Apr/2011:12:58:30 -0500] [Job 21] Started backend /usr/lib/cups/backend/smb (PID 2768)
D [16/Apr/2011:12:58:30 -0500] [Job 21] pstopdf 6 args: 21 maclite Test Page 1 PageSize=Letter job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e job-originating-host-name=localhost /var/spool/cups/d00021-001
D [16/Apr/2011:12:58:30 -0500] [Job 21] /usr/lib/cups/backend/smb: Permission denied
D [16/Apr/2011:12:58:30 -0500] [Job 21] PPD: /etc/cups/ppd/Samsung-ML-2010.ppd
D [16/Apr/2011:12:58:30 -0500] [Job 21] Getting input from file 
D [16/Apr/2011:12:58:30 -0500] [Job 21] foomatic-rip version 4.0.5.223 running...
D [16/Apr/2011:12:58:30 -0500] [Job 21] Parsing PPD file ...
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Manualfeed
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Resolution
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Economode
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option MediaType
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option RET
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Copies
D [16/Apr/2011:12:58:30 -0500] [Job 21] Resolution: 600x600
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PageSize
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option ImageableArea
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PaperDimension
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option HalftoningAlgorithm
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Density
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option JamRecovery
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option AllowReprint
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Altitude
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PageTimeout
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PowerSaving
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PowerSaveTime
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PageSizeJCL
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option PageSizePS
D [16/Apr/2011:12:58:30 -0500] [Job 21] Added option Font
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] Parameter Summary
D [16/Apr/2011:12:58:30 -0500] [Job 21] -----------------
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] Spooler: cups
D [16/Apr/2011:12:58:30 -0500] [Job 21] Printer: Samsung-ML-2010
D [16/Apr/2011:12:58:30 -0500] [Job 21] Shell: /bin/bash
D [16/Apr/2011:12:58:30 -0500] [Job 21] PPD file: /etc/cups/ppd/Samsung-ML-2010.ppd
D [16/Apr/2011:12:58:30 -0500] [Job 21] ATTR file: 
D [16/Apr/2011:12:58:30 -0500] [Job 21] Printer model: Samsung ML-2010 Foomatic/gdi
D [16/Apr/2011:12:58:30 -0500] [Job 21] Job title: Test Page
D [16/Apr/2011:12:58:30 -0500] [Job 21] File(s) to be printed:
D [16/Apr/2011:12:58:30 -0500] [Job 21] <STDIN>
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [16/Apr/2011:12:58:30 -0500] [Job 21] Printing system options:
D [16/Apr/2011:12:58:30 -0500] [Job 21] Pondering option 'job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e'
D [16/Apr/2011:12:58:30 -0500] [Job 21] Unknown option job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e.
D [16/Apr/2011:12:58:30 -0500] [Job 21] Pondering option 'job-originating-host-name=localhost'
D [16/Apr/2011:12:58:30 -0500] [Job 21] Unknown option job-originating-host-name=localhost.
D [16/Apr/2011:12:58:30 -0500] [Job 21] Options from the PPD file:
D [16/Apr/2011:12:58:30 -0500] [Job 21] Pondering option 'PageSize=Letter'
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] ================================================
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] File: <STDIN>
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] ================================================
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] Page size: Letter
D [16/Apr/2011:12:58:30 -0500] [Job 21] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [16/Apr/2011:12:58:30 -0500] [Job 21] Relative margins: 18, 36, 18, 36
D [16/Apr/2011:12:58:30 -0500] [Job 21] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [16/Apr/2011:12:58:30 -0500] [Job 21] PostScript to be injected: 
D [16/Apr/2011:12:58:30 -0500] [Job 21] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [16/Apr/2011:12:58:30 -0500] [Job 21] Filetype: PDF
D [16/Apr/2011:12:58:30 -0500] [Job 21] Storing temporary files in /var/spool/cups/tmp
D [16/Apr/2011:12:58:30 -0500] [Job 21] File contains 1 pages
D [16/Apr/2011:12:58:30 -0500] [Job 21] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=gdi -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r600x600 -sOutputFile=- -f    /var/spool/cups/tmp/foomatic-IV6RlV | perl -p -e 's/PJL PAGE LETTER/PJL PAGE LETTER/; s/PJL PAGE (\S*) AUTO/PJL PAGE $1 AUTO/; s/PJL SET TONERSAVE = OFF/PJL SET TONERSAVE = OFF\r\n\@PJL SET ECONOMODE = OFF/; s/PJL SET PAPERTYPE = NORMAL/PJL SET PAPERTYPE = NORMAL/; s/PJL SET DENSITY = 1/PJL SET DENSITY = 3/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET RET = OFF\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET JAMRECOVERY = ON\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET REPRINT = ON\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET ALTITUDE = OFF\r\n$1/; s/PJL COPIES = 1/PJL COPIES = 1/; s/(\@PJL ENTER LANGUAGE)/\@PJL DEFAULT TIMEOUT = 15\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL DEFAULT POWERSAVE = ON\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL DEFAULT POWERSAVETIME = 5\r\n$1/; '
D [16/Apr/2011:12:58:30 -0500] [Job 21] Starting process "kid3" (generation 1)
D [16/Apr/2011:12:58:30 -0500] [Job 21] Starting process "kid4" (generation 2)
D [16/Apr/2011:12:58:30 -0500] [Job 21] Starting process "renderer" (generation 2)
D [16/Apr/2011:12:58:30 -0500] [Job 21] JCL: %-12345X@PJL
D [16/Apr/2011:12:58:30 -0500] [Job 21] <job data> 
D [16/Apr/2011:12:58:30 -0500] [Job 21] 
D [16/Apr/2011:12:58:30 -0500] [Job 21] renderer exited with status 141
D [16/Apr/2011:12:58:30 -0500] [Job 21] A filter used in addition to the renderer itself may have failed.Kid3 exit status: 1
D [16/Apr/2011:12:58:30 -0500] [Job 21] Backend returned status 22 (unknown)
D [16/Apr/2011:12:58:30 -0500] [Job 21] End of messages
D [16/Apr/2011:12:58:30 -0500] [Job 21] printer-state=3(idle)
D [16/Apr/2011:12:58:30 -0500] [Job 21] printer-state-message="/usr/lib/cups/backend/smb failed"
D [16/Apr/2011:12:58:30 -0500] [Job 21] printer-state-reasons=none
D [16/Apr/2011:13:03:41 -0500] [Job 21] The following messages were recorded from 13:03:40 to 13:03:41
D [16/Apr/2011:13:03:41 -0500] [Job 21] Job submission timed out.
D [16/Apr/2011:13:03:41 -0500] [Job 21] job-sheets=none,none
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[0]="Samsung-ML-2010"
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[1]="21"
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[2]="maclite"
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[3]="Test Page"
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[4]="1"
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[5]="PageSize=Letter job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e job-originating-host-name=localhost"
D [16/Apr/2011:13:03:41 -0500] [Job 21] argv[6]="/var/spool/cups/d00021-001"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[8]="HOME=/var/spool/cups/tmp"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[10]="SERVER_ADMIN=root@ubuntu"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[11]="SOFTWARE=CUPS/1.4.4"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[13]="USER=root"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[16]="IPP_PORT=631"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[17]="CHARSET=utf-8"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[18]="LANG=en_US.UTF-8"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[19]="PPD=/etc/cups/ppd/Samsung-ML-2010.ppd"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[20]="RIP_MAX_CACHE=auto"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[21]="CONTENT_TYPE=application/postscript"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[22]="DEVICE_URI=smb://jaypugh-PC/SAMSUNG"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[23]="PRINTER_INFO=Samsung ML-2010"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[24]="PRINTER_LOCATION="
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[25]="PRINTER=Samsung-ML-2010"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[26]="CUPS_FILETYPE=document"
D [16/Apr/2011:13:03:41 -0500] [Job 21] envp[27]="FINAL_CONTENT_TYPE=printer/Samsung-ML-2010"
D [16/Apr/2011:13:03:41 -0500] [Job 21] Started filter /usr/lib/cups/filter/pstopdf (PID 2841)
D [16/Apr/2011:13:03:41 -0500] [Job 21] Started filter /usr/lib/cups/filter/pdftopdf (PID 2842)
D [16/Apr/2011:13:03:41 -0500] [Job 21] Started filter /usr/lib/cups/filter/foomatic-rip (PID 2843)
D [16/Apr/2011:13:03:41 -0500] [Job 21] Started backend /usr/lib/cups/backend/smb (PID 2844)
D [16/Apr/2011:13:03:41 -0500] [Job 21] pstopdf 6 args: 21 maclite Test Page 1 PageSize=Letter job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e job-originating-host-name=localhost /var/spool/cups/d00021-001
D [16/Apr/2011:13:03:41 -0500] [Job 21] Getting input from file 
D [16/Apr/2011:13:03:41 -0500] [Job 21] /usr/lib/cups/backend/smb: Permission denied
D [16/Apr/2011:13:03:41 -0500] [Job 21] PPD: /etc/cups/ppd/Samsung-ML-2010.ppd
D [16/Apr/2011:13:03:41 -0500] [Job 21] foomatic-rip version 4.0.5.223 running...
D [16/Apr/2011:13:03:41 -0500] [Job 21] Parsing PPD file ...
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Manualfeed
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Resolution
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Economode
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option MediaType
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option RET
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Copies
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PageSize
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option ImageableArea
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PaperDimension
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option HalftoningAlgorithm
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Density
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option JamRecovery
D [16/Apr/2011:13:03:41 -0500] [Job 21] Resolution: 600x600
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option AllowReprint
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Altitude
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PageTimeout
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PowerSaving
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PowerSaveTime
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PageSizeJCL
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option PageSizePS
D [16/Apr/2011:13:03:41 -0500] [Job 21] Added option Font
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] Parameter Summary
D [16/Apr/2011:13:03:41 -0500] [Job 21] -----------------
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] Spooler: cups
D [16/Apr/2011:13:03:41 -0500] [Job 21] Printer: Samsung-ML-2010
D [16/Apr/2011:13:03:41 -0500] [Job 21] Shell: /bin/bash
D [16/Apr/2011:13:03:41 -0500] [Job 21] PPD file: /etc/cups/ppd/Samsung-ML-2010.ppd
D [16/Apr/2011:13:03:41 -0500] [Job 21] ATTR file: 
D [16/Apr/2011:13:03:41 -0500] [Job 21] Printer model: Samsung ML-2010 Foomatic/gdi
D [16/Apr/2011:13:03:41 -0500] [Job 21] Job title: Test Page
D [16/Apr/2011:13:03:41 -0500] [Job 21] File(s) to be printed:
D [16/Apr/2011:13:03:41 -0500] [Job 21] <STDIN>
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] Ghostscript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [16/Apr/2011:13:03:41 -0500] [Job 21] Printing system options:
D [16/Apr/2011:13:03:41 -0500] [Job 21] Pondering option 'job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e'
D [16/Apr/2011:13:03:41 -0500] [Job 21] Unknown option job-uuid=urn:uuid:60507006-f9cb-3c1d-7c00-78538556938e.
D [16/Apr/2011:13:03:41 -0500] [Job 21] Pondering option 'job-originating-host-name=localhost'
D [16/Apr/2011:13:03:41 -0500] [Job 21] Unknown option job-originating-host-name=localhost.
D [16/Apr/2011:13:03:41 -0500] [Job 21] Options from the PPD file:
D [16/Apr/2011:13:03:41 -0500] [Job 21] Pondering option 'PageSize=Letter'
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] ================================================
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] File: <STDIN>
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] ================================================
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] Page size: Letter
D [16/Apr/2011:13:03:41 -0500] [Job 21] Width: 612, height: 792, absolute margins: 18, 36, 594, 756
D [16/Apr/2011:13:03:41 -0500] [Job 21] Relative margins: 18, 36, 18, 36
D [16/Apr/2011:13:03:41 -0500] [Job 21] PPD options: -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792
D [16/Apr/2011:13:03:41 -0500] [Job 21] PostScript to be injected: 
D [16/Apr/2011:13:03:41 -0500] [Job 21] Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r600 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -sOutputFile=-  -c .setpdfwrite -f -
D [16/Apr/2011:13:03:41 -0500] [Job 21] Filetype: PDF
D [16/Apr/2011:13:03:41 -0500] [Job 21] Storing temporary files in /var/spool/cups/tmp
D [16/Apr/2011:13:03:41 -0500] [Job 21] File contains 1 pages
D [16/Apr/2011:13:03:41 -0500] [Job 21] Starting renderer with command: gs -dFirstPage=1  -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=gdi -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -r600x600 -sOutputFile=- -f    /var/spool/cups/tmp/foomatic-FeMK8I | perl -p -e 's/PJL PAGE LETTER/PJL PAGE LETTER/; s/PJL PAGE (\S*) AUTO/PJL PAGE $1 AUTO/; s/PJL SET TONERSAVE = OFF/PJL SET TONERSAVE = OFF\r\n\@PJL SET ECONOMODE = OFF/; s/PJL SET PAPERTYPE = NORMAL/PJL SET PAPERTYPE = NORMAL/; s/PJL SET DENSITY = 1/PJL SET DENSITY = 3/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET RET = OFF\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET JAMRECOVERY = ON\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET REPRINT = ON\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL SET ALTITUDE = OFF\r\n$1/; s/PJL COPIES = 1/PJL COPIES = 1/; s/(\@PJL ENTER LANGUAGE)/\@PJL DEFAULT TIMEOUT = 15\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL DEFAULT POWERSAVE = ON\r\n$1/; s/(\@PJL ENTER LANGUAGE)/\@PJL DEFAULT POWERSAVETIME = 5\r\n$1/; '
D [16/Apr/2011:13:03:41 -0500] [Job 21] Starting process "kid3" (generation 1)
D [16/Apr/2011:13:03:41 -0500] [Job 21] Starting process "kid4" (generation 2)
D [16/Apr/2011:13:03:41 -0500] [Job 21] Starting process "renderer" (generation 2)
D [16/Apr/2011:13:03:41 -0500] [Job 21] JCL: %-12345X@PJL
D [16/Apr/2011:13:03:41 -0500] [Job 21] <job data> 
D [16/Apr/2011:13:03:41 -0500] [Job 21] 
D [16/Apr/2011:13:03:41 -0500] [Job 21] renderer exited with status 141
D [16/Apr/2011:13:03:41 -0500] [Job 21] A filter used in addition to the renderer itself may have failed.Kid3 exit status: 1
D [16/Apr/2011:13:03:41 -0500] [Job 21] Backend returned status 22 (unknown)
D [16/Apr/2011:13:03:41 -0500] [Job 21] End of messages
D [16/Apr/2011:13:03:41 -0500] [Job 21] printer-state=3(idle)
D [16/Apr/2011:13:03:41 -0500] [Job 21] printer-state-message="/usr/lib/cups/backend/smb failed"
D [16/Apr/2011:13:03:41 -0500] [Job 21] printer-state-reasons=none

Also cups pdf printer is installed.

---


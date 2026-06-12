---
title: "Printer sharing not working between 2 Linux computers"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by philbastian on 2010-02-05
My desktop computer, which is hooked up to the printer, is running Karmic and my netbook is running Mint 8. I turned on printer sharing on my Ubuntu computer and lo and behold, there was the printer on the list of printers on my netbook. Naturally I was impressed, and started singing the praises of Linux.

Unfortunately, however, when I tried to print something, it got stuck in the queue with the status "Processing." This went on for several minutes before I cancelled it. That was with OpenOffice. I have since tried with other applications (both Firefox and gedit), and often when I select the printer, the program will go grey (i.e. stop responding), but the print dialog will stay in normal color, but stop responding. 

The printer is an HP psc2210 with the normal Linux driver. I wish I had more information to give--I tried running gedit in terminal to see if it returned an error message, but it didn't--it just crashed.

Thanks in advance,
Phil

---

### Post by chili555 on 2010-02-05
When you go to System -> Administration -> Printing and right-click the printer and select Properties, what does it show for the make and model? If you click Change and go through the selection process for drivers, does it identify a recommended driver? Is that the one selected? Please see attached.

---

### Post by philbastian on 2010-02-05
Make and model is: HP PSC 2200 Series hpijs, 3.9.8

The actual printer is a 2210, so that makes sense to me. I went through the change process, and it said there were proprietary drivers available, but then when it got to the page where I could download them, it didn't show any.

I should also point out that the printer works perfectly on the desktop computer (i.e. the one it's connected to by USB). It also works perfectly if I connect it to the netbook by USB. It's just the networking that doesn't work.

---

### Post by chili555 on 2010-02-05
> The actual printer is a 2210Did the 2210 driver not work as expected? Which protocol are you using? I have had perfect results with ipp.

Please see attached.

---

### Post by philbastian on 2010-02-05
Hmmmm.. Not entirely sure what protocol it is. I just selected "Shared" in the properties dialog. Again, the printer shows up on the netbook printing menu--it just doesn't work.

---

### Post by chili555 on 2010-02-05
On the netbook, select System -> Administration -> Printing (or it's near equivalent in Mint's windowing system). Do you see something like this?

If you right click it and select Properties, you should see something like my previous attachment from post #2. See the protocol in the device URI is ipp.

What is yours *on the netbook*?

---

### Post by philbastian on 2010-02-05
Hi,
Thanks for your patience. Mint has the same printing configuration as Ubuntu. I tried clicking properties, but it greys out and then I have to kill the process. I did manage to run a troubleshooting tool, but it wasn't much help. It did, however, return the following:

```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Is local server publishing?):
{'local_server_exporting_printers': False}
Page 3 (Choose printer):
{'cups_dest': <cups.Dest PSC-2200-Series>,
 'cups_instance': None,
 'cups_queue': 'PSC-2200-Series',
 'cups_queue_listed': True}
Page 4 (Check printer sanity):
{'cups_device_uri_scheme': u'file',
 'cups_printer_dict': {'device-uri': u'file:///dev/null',
                       'printer-info': u'Hewlett-Packard PSC 2200 Series',
                       'printer-is-shared': False,
                       'printer-location': u'philb-desktop',
                       'printer-make-and-model': u'HP PSC 2200 Series hpijs, 3.9.8 on 192.168.0.101',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 2199580,
                       'printer-uri-supported': u'ipp://localhost:631/printers/PSC-2200-Series'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.1',
                                 'device-uri': u'file:///dev/null',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/rss+xml',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-command',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-ppd',
                                                               u'application/vnd.cups-raster',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-alias',
                                                               u'image/x-bitmap',
                                                               u'image/x-icon',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'generated-natural-language-supported': [u'en_US'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-col-supported': [u'media-color',
                                                         u'media-key',
                                                         u'media-size',
                                                         u'media-type'],
                                 'member-names': [u'PSC-2200-Series@192.168.0.101',
                                                  u'PSC-2200-Series@192.168.0.102'],
                                 'member-uris': [u'ipp://192.168.0.101:631/printers/PSC-2200-Series',
                                                 u'ipp://192.168.0.102:631/printers/PSC-2200-Series'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en_US',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'page-ranges-supported': True,
                                 'pdl-override-supported': [u'not-attempted'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'retry-current-job'],
                                 'printer-info': u'Hewlett-Packard PSC 2200 Series',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': False,
                                 'printer-location': u'philb-desktop',
                                 'printer-make-and-model': u'HP PSC 2200 Series hpijs, 3.9.8 on 192.168.0.101',
                                 'printer-more-info': u'http://localhost:631/printers/PSC-2200-Series',
                                 'printer-name': u'PSC-2200-Series',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1265425210,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 2199580,
                                 'printer-up-time': 1265425369,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/PSC-2200-Series'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': False,
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Error log checkpoint):
{'cups_server_settings': {'BrowseLocalProtocols': '',
                          'BrowseRemoteProtocols': 'CUPS',
                          'DefaultAuthType': 'Basic',
                          'MaxLogSize': '0',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '1',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 73534L,
 'error_log_debug_logging_set': True}
Page 7 (Print test page):
{'test_page_attempted': '05/Feb/2010:22:07:03 +0000',
 'test_page_job_id': [5],
 'test_page_job_status': [(True,
                           5,
                           'PSC-2200-Series@192.168.0.102',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-count': 1,
                            'document-format': u'application/vnd.cups-banner',
                            'job-actual-printer-uri': u'ipp://192.168.0.102:631/printers/PSC-2200-Series',
                            'job-hold-until': u'no-hold',
                            'job-id': 5,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/5',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'philb',
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'connecting-to-device'],
                            'job-printer-up-time': 1265425656,
                            'job-printer-uri': u'ipp://philb-netbook:0/printers/PSC-2200-Series',
                            'job-priority': 50,
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/5',
                            'job-uuid': u'urn:uuid:bf263f44-e30a-36c9-6544-5aa8491a51a1',
                            'printer-uri': u'ipp://localhost/printers/PSC-2200-Series',
                            'time-at-completed': None,
                            'time-at-creation': 1265425623,
                            'time-at-processing': 1265425623})],
 'test_page_successful': False}
Page 8 (Error log fetch):
{'error_log': ['D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Dirty files',
               'D [05/Feb/2010:22:06:59 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Feb/2010:22:06:59 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:06:59 -0500] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [05/Feb/2010:22:06:59 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Feb/2010:22:06:59 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Dirty files',
               'D [05/Feb/2010:22:06:59 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Feb/2010:22:06:59 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:06:59 -0500] cupsdReadClient: 12 1.1 Get-Jobs 1',
               'D [05/Feb/2010:22:06:59 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Feb/2010:22:06:59 -0500] [Job 1] Loading attributes...',
               'D [05/Feb/2010:22:06:59 -0500] [Job 2] Loading attributes...',
               'D [05/Feb/2010:22:06:59 -0500] [Job 4] Loading attributes...',
               'D [05/Feb/2010:22:06:59 -0500] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Dirty files',
               'D [05/Feb/2010:22:06:59 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Feb/2010:22:06:59 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:06:59 -0500] cupsdReadClient: 12 1.1 Create-Printer-Subscription 1',
               'D [05/Feb/2010:22:06:59 -0500] Create-Printer-Subscription /',
               'D [05/Feb/2010:22:06:59 -0500] cupsdCreateSubscription(con=0x1694f38(12), uri="/")',
               'D [05/Feb/2010:22:06:59 -0500] pullmethod="ippget"',
               'D [05/Feb/2010:22:06:59 -0500] notify-lease-duration=86400',
               'D [05/Feb/2010:22:06:59 -0500] notify-time-interval=0',
               'D [05/Feb/2010:22:06:59 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [05/Feb/2010:22:06:59 -0500] Added subscription 11 for server',
               'D [05/Feb/2010:22:06:59 -0500] cupsdMarkDirty(-----S)',
               'D [05/Feb/2010:22:06:59 -0500] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [05/Feb/2010:22:06:59 -0500] cupsdSetBusyState: Dirty files',
               'D [05/Feb/2010:22:07:00 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:00 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Feb/2010:22:07:00 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:00 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [05/Feb/2010:22:07:00 -0500] Get-Notifications /',
               'D [05/Feb/2010:22:07:00 -0500] cupsdIsAuthorized: requesting-user-name="philb"',
               'D [05/Feb/2010:22:07:00 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2010:22:07:00 -0500] cupsdSetBusyState: Dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAcceptClient: 14 from localhost (Domain)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 14 POST /printers/PSC-2200-Series HTTP/1.1',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Active clients and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 14 1.1 Print-Job 1',
               'D [05/Feb/2010:22:07:03 -0500] Print-Job ipp://localhost/printers/PSC-2200-Series',
               'D [05/Feb/2010:22:07:03 -0500] [Job ???] Auto-typing file...',
               'I [05/Feb/2010:22:07:03 -0500] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(----J-)',
               'D [05/Feb/2010:22:07:03 -0500] add_job: requesting-user-name="philb"',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(-----S)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(----J-)',
               'I [05/Feb/2010:22:07:03 -0500] [Job 5] File of type application/vnd.cups-banner queued by "philb".',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] hold_until=0',
               'I [05/Feb/2010:22:07:03 -0500] [Job 5] Queued on "PSC-2200-Series" by "philb".',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(----J-)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(----J-)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] Sending job to queue tagged as raw...',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] No job-sheets attribute.',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[0]="PSC-2200-Series@192.168.0.102"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[1]="5"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[2]="philb"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[3]="Test Page"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[4]="1"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[5]="job-originating-user-name=philb job-priority=50 job-uuid=urn:uuid:bf263f44-e30a-36c9-6544-5aa8491a51a1 job-originating-host-name=localhost job-id=5 job-state=5 job-media-sheets-completed=0 job-k-octets=1"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] argv[6]="/var/spool/cups/d00005-001"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[10]="SERVER_ADMIN=root@philb-netbook"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[11]="SOFTWARE=CUPS/1.4.1"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[13]="TZ=America/New_York"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[14]="USER=root"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[16]="CUPS_ENCRYPTION=IfRequested"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[17]="IPP_PORT=631"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[18]="CHARSET=utf-8"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[19]="LANG=en_US.UTF-8"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[20]="PPD=/etc/cups/ppd/PSC-2200-Series@192.168.0.102.ppd"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[21]="RIP_MAX_CACHE=254520k"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[22]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[23]="DEVICE_URI=file:///dev/null"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[24]="PRINTER_INFO=Hewlett-Packard PSC 2200 Series"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[25]="PRINTER_LOCATION=philb-desktop"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[26]="PRINTER=PSC-2200-Series@192.168.0.102"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[27]="CUPS_FILETYPE=document"',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] envp[28]="CLASS=PSC-2200-Series"',
               'I [05/Feb/2010:22:07:03 -0500] [Job 5] Started backend /usr/lib/cups/backend/ipp (PID 2634)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(-----S)',
               'D [05/Feb/2010:22:07:03 -0500] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/PSC-2200-Series) from localhost',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] 1 files to send in job...',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] STATE: +connecting-to-device',
               'D [05/Feb/2010:22:07:03 -0500] [Job 5] Connecting to 192.168.0.102:631',
               'I [05/Feb/2010:22:07:03 -0500] [Job 5] Connecting to printer...',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(-----S)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdMarkDirty(-----S)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 16 1.1 Get-Notifications 1',
               'D [05/Feb/2010:22:07:03 -0500] Get-Notifications /',
               'D [05/Feb/2010:22:07:03 -0500] cupsdIsAuthorized: requesting-user-name="philb"',
               'D [05/Feb/2010:22:07:03 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 16 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 16 1.1 Get-Job-Attributes 1',
               'D [05/Feb/2010:22:07:03 -0500] Get-Job-Attributes ipp://localhost/jobs/5',
               'D [05/Feb/2010:22:07:03 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/5) from localhost',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 17 1.1 Get-Notifications 1',
               'D [05/Feb/2010:22:07:03 -0500] Get-Notifications /',
               'D [05/Feb/2010:22:07:03 -0500] cupsdIsAuthorized: requesting-user-name="philb"',
               'D [05/Feb/2010:22:07:03 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [05/Feb/2010:22:07:03 -0500] cupsdCloseClient: 17',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 12 1.1 Get-Notifications 1',
               'D [05/Feb/2010:22:07:03 -0500] Get-Notifications /',
               'D [05/Feb/2010:22:07:03 -0500] cupsdIsAuthorized: requesting-user-name="philb"',
               'D [05/Feb/2010:22:07:03 -0500] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAcceptClient: 17 from localhost (Domain)',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 17 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 17 1.1 Get-Printer-Attributes 1',
               'D [05/Feb/2010:22:07:03 -0500] Get-Printer-Attributes ipp://philb-netbook:0/printers/PSC-2200-Series',
               'D [05/Feb/2010:22:07:03 -0500] Returning IPP successful-ok for Get-Printer-Attributes (ipp://philb-netbook:0/printers/PSC-2200-Series) from localhost',
               'D [05/Feb/2010:22:07:03 -0500] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 17 WAITING Closing on EOF',
               'D [05/Feb/2010:22:07:03 -0500] cupsdCloseClient: 17',
               'D [05/Feb/2010:22:07:03 -0500] cupsdReadClient: 16 WAITING Closing on EOF',
               'D [05/Feb/2010:22:07:03 -0500] cupsdCloseClient: 16',
               'D [05/Feb/2010:22:07:11 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [05/Feb/2010:22:07:11 -0500] cupsdNetIFUpdate: "wlan0" = 192.168.0.103:0',
               'D [05/Feb/2010:22:07:11 -0500] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [05/Feb/2010:22:07:11 -0500] cupsdNetIFUpdate: "wlan0" = fe80::225:d3ff:fec6:bff0%wlan0:0',
               'I [05/Feb/2010:22:07:21 -0500] Saving printers.conf...',
               'I [05/Feb/2010:22:07:21 -0500] Generating printcap /var/run/cups/printcap...',
               'I [05/Feb/2010:22:07:21 -0500] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [05/Feb/2010:22:07:21 -0500] Saving subscriptions.conf...',
               'D [05/Feb/2010:22:07:21 -0500] cupsdSetBusyState: Printing jobs',
               'D [05/Feb/2010:22:07:36 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:36 -0500] cupsdSetBusyState: Active clients and printing jobs',
               'D [05/Feb/2010:22:07:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:36 -0500] cupsdReadClient: 12 1.1 Get-Job-Attributes 1',
               'D [05/Feb/2010:22:07:36 -0500] Get-Job-Attributes ipp://localhost/jobs/5',
               'D [05/Feb/2010:22:07:36 -0500] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/5) from localhost',
               'D [05/Feb/2010:22:07:36 -0500] cupsdSetBusyState: Printing jobs',
               'D [05/Feb/2010:22:07:36 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Feb/2010:22:07:36 -0500] cupsdSetBusyState: Active clients and printing jobs',
               'D [05/Feb/2010:22:07:36 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Feb/2010:22:07:36 -0500] cupsdReadClient: 12 1.1 Cancel-Subscription 1',
               'D [05/Feb/2010:22:07:36 -0500] Cancel-Subscription /',
               'D [05/Feb/2010:22:07:36 -0500] cupsdIsAuthorized: requesting-user-name="philb"',
               'D [05/Feb/2010:22:07:36 -0500] cupsdMarkDirty(-----S)',
               'D [05/Feb/2010:22:07:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:36 -0500] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [05/Feb/2010:22:07:36 -0500] cupsdSetBusyState: Printing jobs and dirty files',
               'D [05/Feb/2010:22:07:36 -0500] cupsdAcceptClient: 16 from localhost (Domain)',
               'D [05/Feb/2010:22:07:36 -0500] cupsdReadClient: 16 GET /admin/log/error_log HTTP/1.1',
               'D [05/Feb/2010:22:07:36 -0500] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [05/Feb/2010:22:07:36 -0500] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 9 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
```

Thanks,
Phil

---

### Post by chili555 on 2010-02-06
Two other things to check. On the desktop, that is, the computer with the printer attached, go to System -> Administration -> Printing. Select Server -> Settings. Make sure that Publish.. and Allow Printing from the Internet are both checked. Don't worry, the open and closed ports on your router will actually only allow printing from your LAN. Just to be obsessive, after these changes are made, if any, restart cups:```
sudo /etc/init.d/cups restart
```

Next, on the netbook, open a browser and go to [http://127.0.0.1:631/printers/printer](http://127.0.0.1:631/printers/printer) and tell us what the listings are for Driver and Connection. My working perfectly connection on this machine reads: ipp://192.168.1.117:631/printers/ML-2010

If everything looks good, restart cups on this machine, too, and try a printing job.

---

### Post by philbastian on 2010-02-06
On both the desktop and the netbook, I get the following:

```
Description:	{printer_info}
Location:	{printer_location}
Driver:	{printer_make_and_model} (grayscale)
Connection:	{device_uri}
Defaults:	job-sheets={job_sheets_default} media=unknown 
```

I figured *that* must be the problem when I saw it on the netbook, but then it was the same for the working connection on the desktop.

---

### Post by chili555 on 2010-02-06
I think, on the desktop, I'd go through System -> Administration -> Printing and select Properties and try to change the device and driver. I am going to my desktop to give you a screenshot to show you my suggested setup.

---

### Post by chili555 on 2010-02-06
Here are the two things I suggest you check and redo, if necessary. In Printer Properties, I suggest running through both the device URI and driver setups to fine tune them. Click Change and look at all the settings.

In Basic Server Settings, be sure the appropriate boxes are checked.

---

### Post by philbastian on 2010-02-07
The basic settings are all exactly the same as you show. I have tried the two drivers that match the "official" model of the printer--PSC2210. Neither works. Only the 2200 drivers work.

---

### Post by rrc21 on 2010-05-25
I'm trying to do the same thing between 2 desktop computers running Lucid, and I've marked the printer as shared on the computer that it's connected to, but am not seeing anything on the other computer. Not sure exactly what else that I'm supposed to do...

My setup is:
Desktop PC1 connected wirelessly to router and connected via usb to the Samsung printer (CUPS and everything working here).
Desktop PC2 connected via ethernet cable to the router - trying to print with this one.

That's basically it.

I've tried marking everything on the shared printer as allowed, remote administration and all.
Evidently, I don't think that PC2 can see the printer connected to PC1, even though the printer is marked as shared. do I need to publish a LAN address and direct PC2 to the printer? If so,  how?

Thanks

---

### Post by chili555 on 2010-05-25
Does desktop PC1 have an IP address by DHCP; that is, ever changing? It's hard to find if it changes. I think samba will help: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Of course, you can set a static IP address and ditch Network Manager on PC1. Then PC2 can set up printing with the ipp protocal and use the URI: ipp://192.168.static.youset:631/printers/Samsungwhatever.

---

### Post by rrc21 on 2010-05-26
Thanks chili555,

I followed your advice and gave it a static IP - works perfectly!

Thanks again for your help :)

---


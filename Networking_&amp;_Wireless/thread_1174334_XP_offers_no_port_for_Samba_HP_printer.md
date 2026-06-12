---
title: "XP offers no port for Samba HP printer"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by rexsty on 2009-05-30
Below is the message received in Samba when Print Test Page fails. Host is Hardy 8.04 linked via router to XP SP3 box. "Printers and Faxes" in XP shows networked printer but no port connection?  Help? Thanks

Page 1 (Choose printer):
{'cups_dest': <cups.Dest object at 0xa36ecc0>,
 'cups_instance': None,
 'cups_queue': 'LaserJet_4_Plus',
 'cups_queue_listed': True}
Page 2 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri':
u'smb://WORKGROUP/REXSTY/LaserJet_4_Plus',
                       'printer-info': u'LaserJet_4_Plus',
                       'printer-is-shared': True,
                       'printer-location': u'rexsty-newlaptop',
                       'printer-make-and-model': u'HP LaserJet 4 Plus
Foomatic/ljet4',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143380,
                       'printer-uri-supported':
u'ipp://localhost:631/printers/LaserJet_4_Plus'},
 'is_cups_class': False}
Page 3 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}
Page 4 (Print test page):
{'test_page_attempted': True,
 'test_page_completions': [(3862, u'Job completed.')],
 'test_page_job_id': [3862],
 'test_page_job_status': [(3862, 'LaserJet_4_Plus', 'Test Page')],
 'test_page_successful': False}
Page 5 (Printer state reasons):
{'printer-state-message': '', 'printer-state-reasons': 'none'}

---

### Post by rexsty on 2009-06-01
I now see that while the folder /var/lib/samba/printers does contain two folders X386 (or something like that) and WIN40, both of those folders are empty. They were created somewhere during the Samba set up process.

---


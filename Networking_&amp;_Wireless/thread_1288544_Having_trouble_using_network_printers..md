---
title: "Having trouble using network printers."
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by deathrunner1 on 2009-10-11
Hello I am new to Ubuntu and Linux.  I have networked my Ubuntu 9.04 machine with my Windows Vista Machine physically.  I tried to find the network printer to no avail.  Then I clicked on the troubleshoot button and...:

I selected not listed as the printer.

Then I selected Network Printer.

I then entered the IP address of the computer with the two printers I am trying to locate and use.

Next I chose not listed as the printer.

Then the system gave me a Diagnostic Output File.

here it is....
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.1.102', 'remote_server_name': ''}
Page 5 (Check network server sanity):
{'remote_server_connect_ipp': True,
 'remote_server_cups': True,
 'remote_server_name_resolves': ['192.168.1.102',
                                 '192.168.1.102',
                                 '192.168.1.102'],
 'remote_server_try_connect': '192.168.1.102'}
Page 6 (Choose network printer):
{'remote_cups_dests_available': [], 'remote_cups_queue_listed': False}
Page 7 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}
--------------------------------------------------------------------------

I would like to be pointed in the write directed so I will be able to utilize my networked printers on my new Ubuntu System.

Thanks in advance,

Lynn

---

### Post by ST3ALTHPSYCH0 on 2009-10-19
Is the printer connected to the vista machine? In order to access my widows shares from my Ubuntu box I had to turn off password sharing (it wouldn't accept my UN password for some reason) and uninstall Windows Live assistant from the programs list.

---

### Post by deathrunner1 on 2009-11-05
Thanks for the input I know its been along time since I've been busy studying for school... I posted a new thread.  If you could let me know how to turn off password sharing then I would be most grateful.

Lynn J

---


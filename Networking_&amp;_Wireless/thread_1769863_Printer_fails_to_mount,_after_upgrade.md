---
title: "Printer fails to mount, after upgrade"
date: 2011-05-28
forum: Networking &amp; Wireless
---

### Post by eino1953 on 2011-05-28
I have no problems accessing files, with the windows shares. The only problem is getting my printer to mount.
Here is the trouble shoot log, if that helps solve the the problem. I didn't fine the problem till, I tried to print something.

> Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': True}
Page 4 (Remote address):
{'remote_server_ip_address': '192.168.1.101', 'remote_server_name': 'house1'}
Page 5 (Check network server sanity):
{'remote_server_connect_ipp': False,
 'remote_server_name_resolves': ['192.168.1.101',
                                 '192.168.1.101',
                                 '192.168.1.101'],
 'remote_server_smb': True,
 'remote_server_smb_shares': [<smbc.Dirent object "IPC$" (IPC share) at 0x9f5df20>,
                              <smbc.Dirent object "print$" (File share) at 0x9d39d70>,
                              <smbc.Dirent object "SharedDocs" (File share) at 0x9f5df38>,
                              <smbc.Dirent object "Dad's Music" (File share) at 0x9f5df50>,
                              <smbc.Dirent object "EPSON" (Printer share) at 0x9f5df80>,
                              <smbc.Dirent object "Dad's" (File share) at 0x9f5dfb0>,
                              <smbc.Dirent object "Camera pics" (File share) at 0x9f5df98>],
 'remote_server_try_connect': 'house1'}
Page 6 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by eino1953 on 2011-05-28
I removed the printer, and tried a reinstall. This is the message I get. CUPS server error    
There was an error during the CUPS operation: 'client-error-not-possible'.

Anyone have an Idea? Please help

---

### Post by eino1953 on 2011-05-29
If I'm in the wrong forum, Plesae let me know.

---


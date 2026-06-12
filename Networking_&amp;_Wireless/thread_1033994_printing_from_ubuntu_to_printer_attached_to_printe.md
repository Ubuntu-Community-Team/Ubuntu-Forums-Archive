---
title: "printing from ubuntu to printer attached to printer will not work"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by will.hillary on 2009-01-07
How do

I just installed 8.10.  Nice version.

I have been trying to set up my computer to network with my computer running windows xp.  I have managed to get the network working (though I am guessing I have some problems in my smb.conf file), but cannot get the printer (a dell 1110 attached to xp box) to print.  

I ran the troubleshooter

(please note the following xxxx refers to the user of the xp box)

The error is as follows:
I [07/Jan/2009:19:01:56 -0800] Saving subscriptions.conf...
E [07/Jan/2009:19:01:57 -0800] Print-Job: Unauthorized
I [07/Jan/2009:19:01:57 -0800] [Job 37] Adding start banner page "none".
I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...
I [07/Jan/2009:19:01:57 -0800] [Job 37] Adding end banner page "none".
I [07/Jan/2009:19:01:57 -0800] [Job 37] File of type application/postscript queued by "root".
I [07/Jan/2009:19:01:57 -0800] [Job 37] Queued on "1110" by "root".
I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...
I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/pstopdf (PID 7439)
I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/pdftopdf (PID 7440)
I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/pdftosplixraster (PID 7441)
I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/rastertoqpdl (PID 7442)
I [07/Jan/2009:19:01:57 -0800] [Job 37] Started backend /usr/lib/cups/backend/smb (PID 7444)
I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...
E [07/Jan/2009:19:01:57 -0800] [Job 37] Session setup failed: NT_STATUS_LOGON_FAILURE
I [07/Jan/2009:19:01:57 -0800] Saving printers.conf...
E [07/Jan/2009:19:01:57 -0800] [Job 37] Session setup failed: NT_STATUS_LOGON_FAILURE
I [07/Jan/2009:19:01:57 -0800] Saving printers.conf...
I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...
E [07/Jan/2009:19:01:57 -0800] [Job 37] Session setup failed: NT_STATUS_LOGON_FAILURE
I [07/Jan/2009:19:01:57 -0800] Saving printers.conf...
I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...
E [07/Jan/2009:19:01:57 -0800] [Job 37] Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)
E [07/Jan/2009:19:01:57 -0800] [Job 37] Unable to connect to CIFS host, will retry in 60 seconds...
I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...
I [07/Jan/2009:19:02:00 -0800] Saving subscriptions.conf...

The troubleshooter is also nice enough to put together a diagnostic output

Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest 1110 (default)>,
 'cups_instance': None,
 'cups_queue': '1110',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'smb',
 'cups_printer_dict': {'device-uri': u'smb://WORKGROUP/xxxx/DellLase.2',
                       'printer-info': u'1110',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Dell 1110, 2.0.0',
                       'printer-state': 3,
                       'printer-state-message': u'Unable to connect to CIFS host, will retry in 60 seconds...',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 4337748,
                       'printer-uri-supported': u'ipp://localhost:631/printers/1110'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'nmblookup_output': ('querying NIKKI on 192.168.0.255\n192.168.0.102 NIKKI<00>\n',
                      ''),
 'remote_server_name': '192.168.0.102'}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Altitude': u'LOW',
                                            u'ColorModel': u'Gray',
                                            u'Duplex': u'None',
                                            u'EconoMode': u'0',
                                            u'InputSlot': u'Auto',
                                            u'JamRecovery': u'False',
                                            u'MediaType': u'OFF',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PowerSave': u'5',
                                            u'Resolution': u'600dpi',
                                            u'TonerDensity': u'3'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Check network server sanity):
{'remote_server_name_resolves': ['192.168.0.102',
                                 '192.168.0.102',
                                 '192.168.0.102'],
 'remote_server_try_connect': '192.168.0.102'}
Page 7 (Printer state reasons):
{'printer-state-message': u'Unable to connect to CIFS host, will retry in 60 seconds...',
 'printer-state-reasons': [u'none']}
Page 8 (Error log checkpoint):
{'cups_server_settings': {'AccessLog': '/var/log/cups/access_log',
                          'AutoPurgeJobs': 'No',
                          'BrowseInterval': '30',
                          'BrowsePort': '631',
                          'BrowseProtocols': 'CUPS',
                          'BrowseShortNames': 'Yes',
                          'BrowseTimeout': '300',
                          'Classification': 'none',
                          'DataDir': '/usr/share/cups',
                          'DefaultCharset': 'UTF-8',
                          'DefaultLanguage': 'en',
                          'DocumentRoot': '/usr/share/cups/doc-root',
                          'ErrorLog': '/var/log/cups/error_log',
                          'FilterLimit': '0',
                          'Group': 'lpadmin',
                          'HideImplicitMembers': 'Yes',
                          'HostnameLookups': 'On',
                          'ImplicitAnyClasses': 'Off',
                          'ImplicitClasses': 'On',
                          'KeepAlive': 'On',
                          'KeepAliveTimeout': '60',
                          'MaxClients': '100',
                          'MaxJobs': '0',
                          'MaxJobsPerPrinter': '0',
                          'MaxJobsPerUser': '0',
                          'MaxLogSize': '1m',
                          'MaxRequestSize': '0m',
                          'PageLog': '/var/log/cups/page_log',
                          'PreserveJobFiles': 'Off',
                          'PreserveJobHistory': 'On',
                          'Printcap': '/etc/printcap',
                          'PrintcapFormat': 'BSD',
                          'RIPCache': '8m',
                          'RemoteRoot': 'remroot',
                          'RequestRoot': '/var/spool/cups',
                          'ServerBin': '/usr/lib/cups',
                          'ServerCertificate': '/etc/cups/ssl/server.crt',
                          'ServerKey': '/etc/cups/ssl/server.key',
                          'ServerName': 'WORKGROUP',
                          'ServerRoot': '/etc/cups',
                          'SystemGroup': 'lpadmin',
                          'TempDir': '/var/spool/cups/tmp',
                          'Timeout': '300',
                          'User': 'lp',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0',
                          'defaultauthtype': 'Basic'},
 'error_log_checkpoint': 65720L}
Page 9 (Print test page):
{'test_page_attempted': True,
 'test_page_job_id': [37],
 'test_page_job_status': [(True,
                           37,
                           '1110',
                           'Test Page',
                           'Processing',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-ca',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 37,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/37',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'root',
                            'job-printer-state-message': u'Unable to connect to CIFS host, will retry in 60 seconds...',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1231383720,
                            'job-printer-uri': u'ipp://WORKGROUP:631/printers/1110',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 5,
                            'job-state-reasons': u'job-printing',
                            'job-uri': u'ipp://localhost:631/jobs/37',
                            'job-uuid': u'urn:uuid:73254268-a7d3-336b-5a8d-67c9140be500',
                            'printer-uri': u'ipp://localhost/printers/1110',
                            'time-at-completed': None,
                            'time-at-creation': 1231383717,
                            'time-at-processing': 1231383717})],
 'test_page_successful': False}
Page 10 (Error log fetch):
{'error_log': ['I [07/Jan/2009:19:01:56 -0800] Saving subscriptions.conf...',
               'E [07/Jan/2009:19:01:57 -0800] Print-Job: Unauthorized',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Adding start banner page "none".',
               'I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Adding end banner page "none".',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] File of type application/postscript queued by "root".',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Queued on "1110" by "root".',
               'I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/pstopdf (PID 7439)',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/pdftopdf (PID 7440)',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/pdftosplixraster (PID 7441)',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Started filter /usr/lib/cups/filter/rastertoqpdl (PID 7442)',
               'I [07/Jan/2009:19:01:57 -0800] [Job 37] Started backend /usr/lib/cups/backend/smb (PID 7444)',
               'I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...',
               'E [07/Jan/2009:19:01:57 -0800] [Job 37] Session setup failed: NT_STATUS_LOGON_FAILURE',
               'I [07/Jan/2009:19:01:57 -0800] Saving printers.conf...',
               'E [07/Jan/2009:19:01:57 -0800] [Job 37] Session setup failed: NT_STATUS_LOGON_FAILURE',
               'I [07/Jan/2009:19:01:57 -0800] Saving printers.conf...',
               'I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...',
               'E [07/Jan/2009:19:01:57 -0800] [Job 37] Session setup failed: NT_STATUS_LOGON_FAILURE',
               'I [07/Jan/2009:19:01:57 -0800] Saving printers.conf...',
               'I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...',
               'E [07/Jan/2009:19:01:57 -0800] [Job 37] Tree connect failed (NT_STATUS_BAD_NETWORK_NAME)',
               'E [07/Jan/2009:19:01:57 -0800] [Job 37] Unable to connect to CIFS host, will retry in 60 seconds...',
               'I [07/Jan/2009:19:01:57 -0800] Saving subscriptions.conf...',
               'I [07/Jan/2009:19:02:00 -0800] Saving subscriptions.conf...']}


I have also attached my smb.conf file because I am willing to bet that is where my problems are coming from (please note, the xxxx is now referring to my user id):

[global]
    ; General server settings
    netbios name = Intrepid
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes
    load printers = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = yes
    guest ok = yes
    browseable = yes
write list = @wheel, xxxx
admin users = @wheel, xxxx
create mask = 0644
directory mask = 0755
    printer admin = root, @ntadmins, @smbprintadm

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/xxxxx/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = xxxx
    force group = xxxx
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home/xxxx
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =



any help would be greatly appreciated!

---

### Post by akelsall on 2009-01-09
Will, if I may make a suggestion, rather than post pages and pages of output, please get in the habit of attaching info like this. People prefer that the problem be described in the body of the thread, with support info (like what you posted) simply attached to the thread. 

Andy

---

### Post by superprash2003 on 2009-01-09
when connecting to the network printer in xp.. enter the full address location of the printer.. like \\x.x.x.x\printername .. where x.x.x.x is the ip of the pc which is connected to the printer.. and printername is the name of the printer which is to be shared..

---


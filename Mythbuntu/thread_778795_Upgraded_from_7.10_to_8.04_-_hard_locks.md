---
title: "Upgraded from 7.10 to 8.04 - hard locks"
date: 2008-05-02
forum: Mythbuntu
---

### Post by Nikas on 2008-05-02
Hello.

I just upgraded my server to 8.04 and now I'm experiencing hard locks now and then. Where do i start? I had no problems what so ever with 7.10.

I checked my messages-log and found this:
May  2 15:22:56 mythtv dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
May  2 15:22:56 mythtv dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1
May  2 15:22:56 mythtv dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
May  2 15:22:56 mythtv dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_renewal_time = -1
May  2 15:22:56 mythtv dhcdbd: dhco_input_option: Value -1 cannot be converted to type L
May  2 15:22:56 mythtv dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_rebinding_time = -1
May  2 15:22:57 mythtv dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
May  2 15:22:57 mythtv dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
May  2 15:22:57 mythtv dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
May  2 15:22:57 mythtv dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
May  2 15:22:57 mythtv dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu

but that was there before the hard lock.

:(

Nikas

---

### Post by superm1 on 2008-05-02
Those messages would have nothing to do with hard locks.

Look at the other logs for some more info.  (/var/log/dmesg /var/log/message)

---

### Post by Nikas on 2008-05-02
> **superm1 said:**
> Those messages would have nothing to do with hard locks.

Look at the other logs for some more info.  (/var/log/dmesg /var/log/message)

Nothing strange there. :(
Did just complete 2 runs of memtest86 with no errors.

My drives did go from hd* to sd* after upgrade but i'm using UUID's  in fstab.

I can see this in dmesg:
"[   25.620363] ata4.00: configured for UDMA/100
[   25.620454] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDP72502 GM2O PQ: 0 ANSI: 5
[   25.620777] scsi 3:0:0:0: Direct-Access     ATA      HDS722525VLAT80  V36O PQ: 0 ANSI: 5

I'm interested in why the disks changed name from hd to sd.

Edit2:
Hard lock again.
I did had "top" running in putty and tail -f on messages and dmesg.

 7199 mythtv    20   0  414m  51m 9764 S 59.3  5.1   0:31.83 mythbackend <- 59% cpu before lock up.
10252 mythtv    37  17 98440  47m  12m R 16.6  4.7   1:40.54 mythcommflag
10263 mythtv    37  17 98532  47m  12m R 15.6  4.7   1:07.37 mythcommflag

Noting strange in messages or dmesg.

Edit3:

I have the feeling that the problem occur when i have much disk activity.. hm.
Need to have them back as hda and hdc with the old IDE-drivers but that does not seem to work.
When i try that everything gets painfully slow.

---

### Post by Nikas on 2008-05-02
Ok. So, watching TV and recording. Working fine for 1h. Tried to start two commflagjobs and bam, hard lock.
This did NOT happen with 7.10.

Edit: Yes. It's when running one or more commflag-jobs that makes the computer freeze. I will disable commflagging until i find a solution.

Changed to temporary use the kernel from 7.10 (.22) Works great.
I'm quite sure it has something to do with libata.

---


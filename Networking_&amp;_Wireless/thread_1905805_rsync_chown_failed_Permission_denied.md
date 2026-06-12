---
title: "rsync: chown failed: Permission denied"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by woodyg on 2012-01-07
I have a working Samba connection from my main computer to a remote backup computer. I'd like to make backups of the main one and have them stored on the remote one and I have tried using LuckyBackup (in super user mode) for this. I keep getting some errors though, and I don't really know what the problem is. It says that **rsync: chown "SomeFile" failed: Permission denied**. The output looks like this:


<OUTPUT>
[COLOR=#ff00ff]Removing old snapshots and logfiles of task: [/COLOR][COLOR=#ff00ff]testing[/COLOR]
=====================================

  Removed all older snapshots data
  Removing /root/.luckyBackup/snaps/default-testing-20120107202042.changes.log
  Removing /root/.luckyBackup/logs/default-testing-20120107202042.log
 =====================================
[COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]testing[/COLOR][COLOR=#ff00ff], starting[/COLOR]
Source : [COLOR=#0000ff]/home/m-xubuntu/Maj/testfolder/[/COLOR]
Destination : [COLOR=#0000ff]/media/remote_lubuntu/remote_test_folder/[/COLOR] 
 building file list ... 
  0 files...
 4 files to consider
 ./
   [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: chown "/media/remote_lubuntu/remote_test_folder/." failed: Permission denied (13) rsync: chown "/media/remote_lubuntu/remote_test_folder/file1.pdf" failed: Permission denied (13) rsync: chown "/media/remote_lubuntu/remote_test_folder/file2.XLS" failed: Permission denied (13) rsync: chown "/media/remote_lubuntu/remote_test_folder/file3" failed: Permission denied (13) [/COLOR]
 deleting .luckybackup-snaphots/
  Number of files: 4
 Number of files transferred: 0
 Total file size: 2.02M bytes
 Total transferred file size: 0 bytes
 Literal data: 0 bytes
 Matched data: 0 bytes
 File list size: 131
 File list generation time: 0.001 seconds
 File list transfer time: 0.000 seconds
 Total bytes sent: 150
 Total bytes received: 24
  sent 150 bytes  received 24 bytes  348.00 bytes/sec
 total size is 2.02M  speedup is 11592.99
   [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8] [/COLOR]
 [COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]testing[/COLOR][COLOR=#ff00ff], finished[/COLOR] =====================================

 .
 [COLOR=#008000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
 trying to send an email
        . . .
 The specified command is probably not installed
  command:   
 exit code: 0
 output:    No such file or directory
</OUTPUT>


The files on the local machine are owned by m-xubuntu, m-xubuntu is the user that is connected to the remote machine and the resulting backup files on the remote computer are owned by 1002 (which is the uid for the user m-xubuntu on the remote machine). 

What am I doing wrong? :confused:

---

### Post by woodyg on 2012-01-09
If I don't run in super user mode, then I get these errors instead:

<OUTPUT>
 [COLOR=#ff00ff]Removing old snapshots and logfiles of task: [/COLOR][COLOR=#ff00ff]testing[/COLOR]
=====================================

  failed to remove all older snapshots data
  Removing /home/m-xubuntu/.luckyBackup/snaps/default-testing-20120108190939.changes.log
  Removing /home/m-xubuntu/.luckyBackup/logs/default-testing-20120108190939.log
 =====================================
[COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]testing[/COLOR][COLOR=#ff00ff], starting[/COLOR]
Source : [COLOR=#0000ff]/home/m-xubuntu/Maj/testfolder/[/COLOR]
Destination : [COLOR=#0000ff]/media/remote_lubuntu/remote_test_folder/[/COLOR] 
 sending incremental file list
 ./
 file1.pdf
        32.77K   1%    0.00kB/s    0:00:00  
  [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: failed to set times on "/media/remote_lubuntu/remote_test_folder/.": Operation not permitted (1) [/COLOR]
         1.96M 100%   91.92MB/s    0:00:00 (xfer#1, to-check=2/4)
 file2.XLS
        32.77K  59%    1.49MB/s    0:00:00  
       55.30K 100%    2.51MB/s    0:00:00 (xfer#2, to-check=1/4)
 file3
1.33K 100%   61.71kB/s    0:00:00  
        1.33K 100%   61.71kB/s    0:00:00 (xfer#3, to-check=0/4)
   [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: mkstemp "/media/remote_lubuntu/remote_test_folder/.file1.pdf.dRsVyV" failed: Permission denied (13) rsync: mkstemp "/media/remote_lubuntu/remote_test_folder/.file2.XLS.suQw9F" failed: Permission denied (13) rsync: mkstemp "/media/remote_lubuntu/remote_test_folder/.file3.CNvcKq" failed: Permission denied (13) [/COLOR]
  Number of files: 4
 Number of files transferred: 3
 Total file size: 2.02M bytes
 Total transferred file size: 2.02M bytes
 Literal data: 2.02M bytes
 Matched data: 0 bytes
 File list size: 126
 File list generation time: 0.001 seconds
 File list transfer time: 0.000 seconds
 Total bytes sent: 2.02M
 Total bytes received: 72
  sent 2.02M bytes  received 72 bytes  4.04M bytes/sec
 total size is 2.02M  speedup is 1.00
   [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.8] [/COLOR]
 [COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]testing[/COLOR][COLOR=#ff00ff], finished[/COLOR] =====================================

</OUTPUT>

:(

---

### Post by woodyg on 2012-01-09
What does something like this even mean?

[COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: mkstemp "/media/remote_lubuntu/remote_test_folder/.file1.pdf.dRsVyV" failed: Permission denied (13)

[/COLOR] The actual file that is to be backed up is called file1.pdf, so** what is ".file1.pdf.dRsVvV"**?

---


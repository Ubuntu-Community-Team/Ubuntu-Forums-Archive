---
title: "Samba Error Log"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by vandorjw on 2010-07-29
Does anyone else have the message "**Unable to mount location - Failed to retrieve share list from server**"?

If you do, could you please check your logs and see if you also have these errors?

I haven't read the trouble shoot guide like it suggested yet because I figured its good to post here first to try and get a solution, and because its almost 1000 pages! :( If I find the solution to this before someone is able to answer I'll post it. 

Also, is this a bug that needs to be filed or has already been filed?

Cheers - CC7

> 
[COLOR="Red"]******@athlonServer:~$ cat /var/log/samba/log.[/COLOR]
log.127.0.0.1             log.__ffff_192.168.0.101  log.nmbd.1.gz
log.192.168.0.101         log.__ffff_192.168.0.120  log.smbd
log.192.168.0.120         log.******-pc              log.smbd.1.gz
log.__ffff_127.0.0.1      log.nmbd                  log.******-pc
[COLOR="Red"]*******@athlonServer:~$ cat /var/log/samba/log.*****-pc[/COLOR] 
[2010/07/24 17:59:50,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/24 17:59:50,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/24 18:31:50,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/24 18:31:50,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/25 09:58:55,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/25 09:58:55,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/25 10:30:55,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/25 10:30:55,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/25 11:02:55,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/25 11:02:55,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/25 12:07:25,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/25 12:07:25,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/25 12:39:49,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2010/07/25 12:39:49,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.
[2010/07/25 13:03:26,  0] lib/sharesec.c:268(delete_share_security)
  delete_share_security: Failed to delete entry for share Music: NT_STATUS_NOT_FOUND
[2010/07/25 13:03:26,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2010/07/25 13:03:27,  1] smbd/service.c:1063(make_connection_snum)
  ********-pc (192.168.0.120) connect to service music initially as user nobody (uid=65534, gid=65534) (pid 9644)
[2010/07/25 13:03:27,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied
[2010/07/25 13:13:00,  1] smbd/service.c:1240(close_cnum)
[COLOR="Red"][2010/07/25 13:13:00,  0] lib/substitute.c:560(alloc_sub_basic)
  alloc_sub_basic: NULL source string!  This should not happen
  *****-pc (192.168.0.120) closed connection to service (null)[/COLOR]
[2010/07/25 13:13:00,  0] lib/substitute.c:560(alloc_sub_basic)
  alloc_sub_basic: NULL source string!  This should not happen
[2010/07/25 13:13:00,  0] lib/fault.c:46(fault_report)
  ===============================================================
[COLOR="Red"][2010/07/25 13:13:00,  0] lib/fault.c:47(fault_report)
  INTERNAL ERROR: Signal 11 in pid 9644 (3.4.7)[/COLOR]
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2010/07/25 13:13:00,  0] lib/fault.c:49(fault_report)
  
  From: [http://www.samba.org/samba/docs/Samba3-HOWTO.pdf](http://www.samba.org/samba/docs/Samba3-HOWTO.pdf)
[2010/07/25 13:13:00,  0] lib/fault.c:50(fault_report)
  ===============================================================
[2010/07/25 13:13:00,  0] lib/util.c:1480(smb_panic)
  PANIC (pid 9644): internal error
[2010/07/25 13:13:01,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 23 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7f8cd89a57aa]
   #1 smbd(smb_panic+0x1f) [0x7f8cd89a586f]
   #2 smbd(+0x309e7d) [0x7f8cd8994e7d]
   #3 /lib/libpthread.so.0(+0xf8f0) [0x7f8cd6dd98f0]
   #4 /lib/libc.so.6(+0x83022) [0x7f8cd5196022]
   #5 smbd(rep_strlcpy+0x2e) [0x7f8cd897f1fe]
   #6 smbd(connections_fetch_entry+0x74) [0x7f8cd89b2b04]
   #7 smbd(yield_connection+0x36) [0x7f8cd875c996]
   #8 smbd(close_cnum+0xa7) [0x7f8cd87c6ea7]
   #9 smbd(conn_close_all+0x44) [0x7f8cd87639e4]
   #10 smbd(+0x5a9c5d) [0x7f8cd8c34c5d]
   #11 smbd(+0x5a9e2e) [0x7f8cd8c34e2e]
   #12 smbd(remove_deferred_open_smb_message+0) [0x7f8cd87c3590]
   #13 smbd(tevent_common_check_signal+0x1da) [0x7f8cd89b6eca]
   #14 smbd(run_events+0x34) [0x7f8cd89b52a4]
   #15 smbd(smbd_process+0x618) [0x7f8cd87c54a8]
   #16 smbd(+0x5aa26b) [0x7f8cd8c3526b]
   #17 smbd(run_events+0x132) [0x7f8cd89b53a2]
   #18 smbd(+0x32a611) [0x7f8cd89b5611]
   #19 smbd(_tevent_loop_once+0x90) [0x7f8cd89b59f0]
   #20 smbd(main+0xa5b) [0x7f8cd8c35d3b]
   #21 /lib/libc.so.6(__libc_start_main+0xfd) [0x7f8cd5131c4d]
   #22 smbd(+0xc0a49) [0x7f8cd874ba49]
[2010/07/25 13:13:02,  0] lib/util.c:1485(smb_panic)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 9644]
[2010/07/25 13:13:02,  0] lib/util.c:1493(smb_panic)
  smb_panic(): action returned status 0
[2010/07/25 13:13:02,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd


---

### Post by marc.verwerft on 2010-07-30
> ********-pc (192.168.0.120) connect to service music initially as user nobody (uid=65534, gid=65534) (pid 9644)
[2010/07/25 13:03:27,  0] param/loadparm.c:8569(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/music failed. Permission denied

Does the file exist and  can 'nobody' read it?

---


---
title: "samba update in the last few weeks broke smb shares"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by Sharft 6 on 2011-02-28
I recently installed a whole lot of updates and now samba won't start.

```

philip@philip-mythbuntu:~$ sudo start smbd
smbd start/running, process 17017
philip@philip-mythbuntu:~$ sudo status smbd
smbd stop/waiting

```

OS: mythtbuntu 10.04 x64

I tried completely removing all samba thing and reinstalling them but it didn't help.

I'm just using the default smb.conf for testing but the same thing happens with my old smb.conf aswell

here's what syslog says:
```

Mar  1 18:23:27 philip-mythbuntu init: smbd main process (26973) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (26978) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (26983) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (26988) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (26993) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (26998) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (27003) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (27008) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (27013) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (27018) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd main process ended, respawning
Mar  1 18:23:27 philip-mythbuntu init: smbd main process (27023) killed by ABRT signal
Mar  1 18:23:27 philip-mythbuntu init: smbd respawning too fast, stopped

```

here's what log.smbd says
```

[2011/03/01 18:23:27,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/03/01 18:23:27,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2011/03/01 18:23:27,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2011/03/01 18:23:27,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2011/03/01 18:23:27,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2011/03/01 18:23:27,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2011/03/01 18:23:27,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2011/03/01 18:23:27,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x1a) [0x7f6bf9a4c8ea]
   #1 smbd(+0x5a9e10) [0x7f6bf9cdbe10]
   #2 smbd(+0x5a9fe1) [0x7f6bf9cdbfe1]
   #3 smbd(main+0x90d) [0x7f6bf9cdcd3d]
   #4 /lib/libc.so.6(__libc_start_main+0xfd) [0x7f6bf61d9c4d]
   #5 smbd(+0xc0a49) [0x7f6bf97f2a49]
[2011/03/01 18:23:27,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd

```

---

### Post by Sharft 6 on 2011-03-01
oh never mind. I just did another update and it's working.

---


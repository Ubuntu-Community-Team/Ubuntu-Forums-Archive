---
title: "SFTP connection time out"
date: 2010-07-07
forum: Networking &amp; Wireless
---

### Post by ravindika on 2010-07-07
Hi,

I'm using Filezilla to connect to a remote server with site 2 site VPN.  Even when i'm sending a small file with SFTP, the connection time outs  and reconnects. Its happening again and again. Even SCP connection is  also the same. BUT SSH CONNECTION IS WORKING FINE.

_Filezilla log_

ravindika@ravindika:~$ tail -f filezilla.log 
2010-07-07 10:35:12 2690 2 Response: fzSftp started
2010-07-07 10:35:12 2690 2 Command: open "root@XXX.XXX.XXX.XXX" 22
2010-07-07 10:35:19 2690 2 Command: Trust new Hostkey: Once
2010-07-07 10:35:21 2690 2 Command: Pass: *******
2010-07-07 10:35:25 2690 2 Status: Connected to XXX.XXX.XXX.XXX
2010-07-07 10:35:28 2690 2 Status: Retrieving directory listing...
2010-07-07 10:35:28 2690 2 Command: pwd
2010-07-07 10:35:28 2690 2 Response: Current directory is: "/root"
2010-07-07 10:35:28 2690 2 Command: ls
2010-07-07 10:35:30 2690 2 Status: Listing directory /root
2010-07-07 10:35:38 2690 2 Status: Calculating timezone offset of  server...
2010-07-07 10:35:38 2690 2 Command: mtime ".Xauthority"
2010-07-07 10:35:41 2690 2 Response: 1278479139
2010-07-07 10:35:41 2690 2 Status: Timezone offsets: Server: -3780  seconds. Local: 19800 seconds. Difference: 23580 seconds.
2010-07-07 10:35:41 2690 2 Status: Directory listing successful
2010-07-07 10:36:12 2690 0 Status: Connecting to XXX.XXX.XXX.XXX...
2010-07-07 10:36:12 2690 0 Response: fzSftp started
2010-07-07 10:36:12 2690 0 Command: open "root@XXX.XXX.XXX.XXX" 22
2010-07-07 10:36:17 2690 0 Command: Trust new Hostkey: Once
2010-07-07 10:36:19 2690 0 Command: Pass: *******
2010-07-07 10:36:22 2690 0 Status: Connected to XXX.XXX.XXX.XXX
2010-07-07 10:36:26 2690 0 Status: Starting upload of  /home/user/filename
2010-07-07 10:36:26 2690 0 Command: cd "/root"
2010-07-07 10:36:31 2690 0 Response: New directory is: "/root"
2010-07-07 10:36:31 2690 0 Command: put "/home/user/filename" "filename"
2010-07-07 10:36:36 2690 0 Status: local:/home/user/filename =>  remote:/root/filename
2010-07-07 10:36:57 2690 0 Error: Connection timed out
2010-07-07 10:36:57 2690 0 Status: Connecting to XXX.XXX.XXX.XXX...
2010-07-07 10:36:57 2690 0 Response: fzSftp started
2010-07-07 10:36:57 2690 0 Command: open "root@XXX.XXX.XXX" 22
2010-07-07 10:37:02 2690 0 Command: Trust new Hostkey: Once
2010-07-07 10:37:04 2690 0 Command: Pass: *******
2010-07-07 10:37:08 2690 0 Status: Connected to XXX.XXX.XXX.XXX
2010-07-07 10:37:11 2690 0 Status: Starting upload of  /home/ruser/filename
2010-07-07 10:37:11 2690 0 Command: cd "/root"

_SCP Log_

debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
[email]root@XXX.XXX.XXX.XXX[/email]'s password: 
debug3: packet_send2: adding 64 (len 56 padlen 8 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug3: Wrote 144 bytes for a total of 1271
debug1: Authentication succeeded (password).
debug2: fd 4 setting O_NONBLOCK
debug2: fd 5 setting O_NONBLOCK
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug3: Wrote 64 bytes for a total of 1335
debug2: callback start
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug3: Ignored env ORBIT_SOCKETDIR
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env TERM
debug3: Ignored env SHELL
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env WINDOWID
debug3: Ignored env GNOME_KEYRING_CONTROL
debug3: Ignored env GTK_MODULES
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env DEFAULTS_PATH
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env XDG_CONFIG_DIRS
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env PATH
debug3: Ignored env QT_IM_MODULE
debug3: Ignored env PWD
debug3: Ignored env XMODIFIERS
debug3: Ignored env GDM_KEYBOARD_LAYOUT
debug1: Sending env LANG = en_US.utf8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env MANDATORY_PATH
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env SPEECHD_PORT
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env DISPLAY
debug3: Ignored env GTK_IM_MODULE
debug3: Ignored env LESSCLOSE
debug3: Ignored env XAUTHORITY
debug3: Ignored env COLORTERM
debug3: Ignored env _
debug1: Sending command: scp -v -t /tmp/
debug2: channel 0: request exec confirm 1
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug3: Wrote 128 bytes for a total of 1463
debug2: channel 0: rcvd adjust 131072
debug2: channel_input_status_confirm: type 99 id 0
debug2: exec request accepted on channel 0
Sending file modes: C0600 4656 filename
debug3: Wrote 64 bytes for a total of 1527
debug2: channel 0: rcvd ext data 34
Sink: C0600 4656 filename
debug2: channel 0: written 34 to efd 6 filename                                                                                                                               100% 4656     4.6KB/s   00:00    
debug3: Wrote 4704 bytes for a total of 6231
debug3: Wrote 48 bytes for a total of 6279

(After this, SCP connection hangup)

Pls note that this issue is happening only with ubuntu 9.10 and ubuntu 10.04. I can SFTP files using Windows XP.

Pls help to solve this issue.

Thanks & Regards.

---

### Post by vcrpcant on 2010-09-05
I'd like to know the answer to this question also:)

---

### Post by marsanyi on 2013-04-28
I had a similar problem.  Solution for me was to notice that, when ssh'ing in manually from a terminal, I received warnings about non-matching certificates for both the machine (name.local) and the IP address (dynamic, since it's wifi).  Clearing out the entries using ssh-keygen (see [http://askubuntu.com/questions/20865/is-it-possible-to-remove-a-particular-host-key-from-sshs-known-hosts-file](http://askubuntu.com/questions/20865/is-it-possible-to-remove-a-particular-host-key-from-sshs-known-hosts-file)) for both the name and the IP address made SFTP to that machine start working.

---


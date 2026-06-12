---
title: "vncserver problem: gdm exits"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by gene02 on 2009-01-07
I used to have a working vncserver setup for resumable sessions, having followed the tutorial [here]("http://ubuntuforums.org/showthread.php?t=122402").  Recently, I updated from Feisty to Gutsy and it still worked at first, but after various config file edits, individual package installations and removals, and other assorted tinkering, it stopped working.  I tried to re-follow the tutorials in various threads here, but I just can't bring it back.  What I see is that gdm launches, but then quits.  From my vnc client, a blank window opens up with a message that the connection was terminated.

 Here is an excerpt of the 1127 lines of debug info gdm writes into syslog:

```
Jan  7 14:57:10 howler xinetd[2847]: warning: can't get client address: Transport endpoint is not connected
Jan  7 14:57:10 howler gdm[2825]: DEBUG: decode_packet: GIOCondition 1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: XDMCP: Received opcode QUERY from client ::ffff:127.0.0.1 : 33250 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 127.0.0.1  
Jan  7 14:57:10 howler gdm[2825]: DEBUG: XDMCP: Sending WILLING to ::ffff:127.0.0.1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_peek_local_address_list: Could not get address from hostname! 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: decode_packet: GIOCondition 1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: XDMCP: Received opcode REQUEST from client ::ffff:127.0.0.1 : 33250 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_xdmcp_handle_request: Got REQUEST from ::ffff:127.0.0.1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_xdmcp_host_allow: client->hostname is 127.0.0.1  
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_xdmcp_handle_request: xdmcp_pending=0, MaxPending=4, xdmcp_sessions=0, MaxSessions=16, ManufacturerID= 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_xdmcp_display_dispose_check (127.0.0.1:1) 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: security/AllowRemoteAutoLogin=false 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_auth_secure_display: Setting up access for 127.0.0.1:1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_auth_secure_display: Setting up access 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: debug/Enable=false 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_auth_secure_display: Setting up access for 127.0.0.1:1 - 1 entries 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_xdmcp_display_alloc: display=127.0.0.1:1, session id=1215608634, xdmcp_pending=1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: XDMCP: Sending ACCEPT to ::ffff:127.0.0.1 with SessionID=1215608634 
[.... snip ...]
Jan  7 14:57:10 howler gdmlogin[2856]: DEBUG:   Got response: 'OK /usr/lib/gdmprefetch @/etc/gdm/gdmprefetchlist' 
Jan  7 14:57:10 howler gdmlogin[2856]: DEBUG: Sending command: 'GET_CONFIG greeter/SetPosition 127.0.0.1:1' 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Handling user message: 'GET_CONFIG greeter/SetPosition 127.0.0.1:1' 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Handling GET_CONFIG: greeter/SetPosition for display 127.0.0.1:1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Looking up per display value for greeter/SetPosition 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: greeter/SetPosition 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: greeter/SetPosition 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Requesting group=greeter key=SetPosition locale=(null) 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Looking up key: greeter/SetPosition 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: greeter/SetPosition 
Jan  7 14:57:10 howler gdmlogin[2856]: DEBUG:   Got response: 'OK false' 
Jan  7 14:57:10 howler gdmlogin[2856]: DEBUG: Sending command: 'CLOSE' 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Handling user message: 'CLOSE' 
Jan  7 14:57:10 howler gdm[2848]: DEBUG: term_quit: Final cleanup 
Jan  7 14:57:10 howler gdm[2848]: DEBUG: gdm_slave_quick_exit: Will kill everything from the display 
Jan  7 14:57:10 howler gdm[2848]: DEBUG: gdm_slave_quick_exit: Killed everything from the display 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: mainloop_sig_callback: Got signal 17 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_cleanup_children: child 2848 returned 65 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Looking up per display value for greeter/SystemMenu=true 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: greeter/SystemMenu=true 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: greeter/SystemMenu=true 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Requesting group=greeter key=SystemMenu locale=(null) 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: Attempting to parse key string: greeter/SystemMenu=true 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_child_action: In remanage 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_display_unmanage: Stopping 127.0.0.1:1 (slave pid: 0) 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_display_dispose: Disposing 127.0.0.1:1 
Jan  7 14:57:10 howler gdm[2825]: DEBUG: gdm_display_unmanage: Display stopped 

```

Does anyone have any suggestions?

---


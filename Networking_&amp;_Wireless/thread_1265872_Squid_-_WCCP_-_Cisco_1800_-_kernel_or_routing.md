---
title: "Squid - WCCP - Cisco 1800 - kernel or routing?"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by MauroD on 2009-09-14
Hello,

I need some help to resolve this configuration problem

It is out of my knowledges but I really want to see it working.

here some log of what I have done:

#####################
root@proxy:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:fe:0d:f5:77
          inet addr:192.168.1.253  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:feff:fe0d:f577/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:797528 (778.8 KB)  TX bytes:638881 (623.9 KB)
          Interrupt:16

gre1      Link encap:UNSPEC  HWaddr C0-A8-01-FD-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP  MTU:1476  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          
root@proxy:~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 3128

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination



Extract from Cisco configuration:

###
...
no ip source-route
ip wccp check services all
ip wccp check acl outbound
ip wccp web-cache group-list 10 password 7 xxxxxxxxxxx
...
interface Vlan1
 ip address 192.168.1.254 255.255.255.0
 ip access-group 102 in
 ip wccp web-cache redirect in
...
access-list 10 remark Web Cache
access-list 10 permit 192.168.1.253
...
end
### 

#####################

#####################
SQUID.CONF -WCCP extract only-

# WCCPv1 AND WCCPv2 CONFIGURATION OPTIONS
# -----------------------------------------------------------------------------
wccp2_router 192.168.1.254
wccp_version 4
wccp2_forwarding_method 1
wccp2_return_method 1
wccp2_assignment_method 2
wccp2_service standard 0 password=xxxxxxxx 
#####################

#####################
LOGS:

CISCO:
TCLAUCK#
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: allocate orig mask info (28 bytes                             )
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032                             7
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: no srvc grp mask data, exit
2d06h: WCCP-EVNT:GRE adjacency added for 192.168.1.253
*Sep  9 06:59:50: %WCCP-5-SERVICEFOUND: Service web-cache acquired on WCCP clien                             t 192.168.1.253
2d06h: WCCP-PKT:S00: Received valid Here_I_Am packet from 192.168.1.253 w/rcv_id                              00000327
2d06h: WCCP-EVNT:wccp_change_router_view: S00
2d06h: WCCP-EVNT:wccp_change_router_view: deallocate rtr_view (24 bytes)
2d06h: WCCP-EVNT:wccp_change_router_view: allocate mask rtr_view (60 bytes)
2d06h: WCCP-EVNT:wccp_change_router_view: copy orig info (28 bytes)
2d06h: WCCP-EVNT:S00: Assignment wait timer started
2d06h: WCCP-EVNT:S00: Built new router view: 1 routers, 1 usable WCCP clients, c                             hange # 00000026
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032                             8
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: no srvc grp mask data, exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 00000329
2d06h: WCCP-EVNT:wccp_set_wc_mask_assignments: enter
2d06h: WCCP-EVNT:wccp_set_wc_mask_assignments: allocate current assign info (1052 bytes)
2d06h: WCCP-EVNT:wccp_set_wc_mask_assignments: set current info (1052 bytes)
2d06h: WCCP-EVNT:wccp_set_wc_mask_assignments: exit
2d06h: WCCP-EVNT:S00: verifying mask-value adjacency map (64)
2d06h: WCCP-EVNT:wccp_change_router_view: S00
2d06h: WCCP-EVNT:wccp_change_router_view: reuse rtr_view (44 of 60 bytes)
2d06h: WCCP-EVNT:wccp_change_router_view: copy blank current info
2d06h: WCCP-EVNT:S00: Assignment wait timer stopped
2d06h: WCCP-EVNT:S00: Built new router view: 1 routers, 1 usable WCCP clients, change # 00000026
2d06h: WCCP-EVNT:S00: Redirect_Assignment packet from 192.168.1.253, cache info updated
2d06h: WCCP-PKT:S00: Received valid Redirect_Assignment packet from 192.168.1.253 w/rcv_id 00000329
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032A
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032B
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032C
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032D
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032E
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 0000032F
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 00000330
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 00000331
2d06h: WCCP-EVNT:wccp_update_assignment_status: enter
2d06h: WCCP-EVNT:wccp_update_assignment_status: exit
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: enter
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: reuse orig mask info (28 bytes)
2d06h: WCCP-EVNT:wccp_copy_wc_assignment_data: exit
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: enter
2d06h: WCCP-EVNT:wccp_validate_wc_assignments: exit
2d06h: WCCP-PKT:S00: Sending I_See_You packet to 192.168.1.253 w/ rcv_id 00000332
2d06h: WCCP-PKT:S00: Sending Removal_Query packet to 192.168.1.253w/ rcv_id 00000333
2d06h: WCCP-EVNT:wccp_change_router_view: S00
2d06h: WCCP-EVNT:wccp_change_router_view: reuse rtr_view (40 of 44 bytes)
2d06h: WCCP-EVNT:wccp_change_router_view: copy blank current info
2d06h: WCCP-EVNT:S00: Assignment wait timer started
2d06h: WCCP-EVNT:S00: Built new router view: 0 routers, 1 usable WCCP clients, change # 00000027
2d06h: WCCP-EVNT:S00: Router 203.397.178.304 removed.
2d06h: WCCP-EVNT:wccp_free_wc_assignment_memory: enter
2d06h: WCCP-EVNT:wccp_free_wc_assignment_memory: deallocate orig info (28 bytes)
2d06h: WCCP-EVNT:wccp_free_wc_assignment_memory: deallocate current info (1052 bytes)
2d06h: WCCP-EVNT:wccp_free_wc_assignment_memory: exit
2d06h: WCCP-EVNT:S00: Cleared assignment key 192.168.1.253, wc id: 192.168.1.253, wc addr: 192.168.1.253
2d06h: WCCP-EVNT:wccp_free_mask_assignment_memory: enter
2d06h: WCCP-EVNT:wccp_free_mask_assignment_memory: exit
*Sep  9 07:02:00: %WCCP-1-SERVICELOST: Service web-cache lost on WCCP client 192.168.1.253
2d06h: WCCP-EVNT:GRE adjacency removed for 192.168.1.253
2d06h: WCCP-EVNT:wccp_change_router_view: S00
2d06h: WCCP-EVNT:wccp_change_router_view: deallocate rtr_view (40 bytes)
2d06h: WCCP-EVNT:wccp_change_router_view: allocate hash rtr_view (1564 bytes)
2d06h: WCCP-EVNT:wccp_change_router_view: rtr_view_size set to 24 bytes
2d06h: WCCP-EVNT:S00: Assignment wait timer started
2d06h: WCCP-EVNT:S00: Built new router view: 0 routers, 0 usable WCCP clients, change # 00000028
2d06h: WCCP-EVNT:S00: Assignment wait timer expired
2d06h: WCCP-EVNT:S00: Cleared hash assignment key 0.0.0.0

SQUID cache.log:
2009/09/09 18:58:30| Finished rebuilding storage from disk.
2009/09/09 18:58:30|      8450 Entries scanned
2009/09/09 18:58:30|         0 Invalid entries.
2009/09/09 18:58:30|         0 With invalid flags.
2009/09/09 18:58:30|      8450 Objects loaded.
2009/09/09 18:58:30|         0 Objects expired.
2009/09/09 18:58:30|         0 Objects cancelled.
2009/09/09 18:58:30|         0 Duplicate URLs purged.
2009/09/09 18:58:30|         0 Swapfile clashes avoided.
2009/09/09 18:58:30|   Took 0.3 seconds (26065.1 objects/sec).
2009/09/09 18:58:30| Beginning Validation Procedure
2009/09/09 18:58:30|   Completed Validation Procedure
2009/09/09 18:58:30|   Validated 8450 Entries
2009/09/09 18:58:30|   store_swap_size = 84368k
2009/09/09 18:58:31| storeLateRelease: released 0 objects
2009/09/09 18:58:31| Sending HereIam packet size 148
2009/09/09 18:58:31| Incoming WCCPv2 I_SEE_YOU length 128.
2009/09/09 18:58:31| Incoming WCCP2_I_SEE_YOU Received ID old=0 new=807.
2009/09/09 18:58:41| Sending HereIam packet size 148
2009/09/09 18:58:41| Incoming WCCPv2 I_SEE_YOU length 164.
2009/09/09 18:58:41| Incoming WCCP2_I_SEE_YOU Received ID old=807 new=808.
2009/09/09 18:58:51| Sending HereIam packet size 148
2009/09/09 18:58:51| Incoming WCCPv2 I_SEE_YOU length 164.
2009/09/09 18:58:51| Incoming WCCP2_I_SEE_YOU Received ID old=808 new=809.
2009/09/09 18:58:56| Running wccp2AssignBuckets
2009/09/09 18:59:01| Sending HereIam packet size 148
2009/09/09 18:59:01| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 18:59:01| Incoming WCCP2_I_SEE_YOU Received ID old=809 new=810.
2009/09/09 18:59:11| Sending HereIam packet size 148
2009/09/09 18:59:11| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 18:59:11| Incoming WCCP2_I_SEE_YOU Received ID old=810 new=811.
2009/09/09 18:59:21| Sending HereIam packet size 148
2009/09/09 18:59:21| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 18:59:21| Incoming WCCP2_I_SEE_YOU Received ID old=811 new=812.
2009/09/09 18:59:31| Sending HereIam packet size 148
2009/09/09 18:59:31| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 18:59:31| Incoming WCCP2_I_SEE_YOU Received ID old=812 new=813.
2009/09/09 18:59:41| Sending HereIam packet size 148
2009/09/09 18:59:41| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 18:59:41| Incoming WCCP2_I_SEE_YOU Received ID old=813 new=814.
2009/09/09 18:59:51| Sending HereIam packet size 148
2009/09/09 18:59:51| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 18:59:51| Incoming WCCP2_I_SEE_YOU Received ID old=814 new=815.
2009/09/09 19:00:01| Sending HereIam packet size 148
2009/09/09 19:00:01| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 19:00:01| Incoming WCCP2_I_SEE_YOU Received ID old=815 new=816.
2009/09/09 19:00:11| Sending HereIam packet size 148
2009/09/09 19:00:11| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 19:00:11| Incoming WCCP2_I_SEE_YOU Received ID old=816 new=817.
2009/09/09 19:00:21| Sending HereIam packet size 148
2009/09/09 19:00:21| Incoming WCCPv2 I_SEE_YOU length 1196.
2009/09/09 19:00:21| Incoming WCCP2_I_SEE_YOU Received ID old=817 new=818.
2009/09/09 19:00:30| Preparing for shutdown after 0 requests
2009/09/09 19:00:30| Waiting 30 seconds for active connections to finish
2009/09/09 19:00:30| FD 13 Closing HTTP connection
2009/09/09 19:00:30| FD 15 Closing WCCP socket
2009/09/09 19:00:30| Shutting down...
2009/09/09 19:00:30| FD 14 Closing ICP connection
2009/09/09 19:00:30| Closing unlinkd pipe on FD 11
2009/09/09 19:00:30| storeDirWriteCleanLogs: Starting...
2009/09/09 19:00:30|   Finished.  Wrote 8450 entries.
2009/09/09 19:00:30|   Took 0.0 seconds (2204539.5 entries/sec).
CPU Usage: 0.100 seconds = 0.060 user + 0.040 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Memory usage for squid via mallinfo():
        total space in arena:    2904 KB
        Ordinary blocks:         2800 KB      8 blks
        Small blocks:               0 KB      0 blks
        Holding blocks:           240 KB      1 blks
        Free Small blocks:          0 KB
        Free Ordinary blocks:     103 KB
        Total in use:            3040 KB 97%
        Total free:               103 KB 3%
2009/09/09 19:00:30| Squid Cache (Version 2.6.STABLE18): Exiting normally.
#####################




I have a doubt about this on the Squid box
root@proxy:~# lsmod  | grep wccp
root@proxy:~# lsmod  | grep gre
ip_gre                 14752  0

Is it matter of kernel?


Thanks So much for your help

---


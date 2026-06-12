---
title: "product: 82566DM-2 Gigabit Network Connection up down up down after upgrade 9.04"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by jinhumanus on 2009-08-23
Hi

I upgraded to ubuntu 9.04 and every once and while my network connection stops. for 30 seconds or so.

I am on Dell Optiplex 755

gig ethernet

driver: e1000e
version: 0.3.3.3-k6
firmware-version: 1.4-0
bus-info: 0000:00:19.0


NIC statistics:
     rx_packets: 110897
     tx_packets: 71750
     rx_bytes: 100861052
     tx_bytes: 7705106
     rx_broadcast: 18453
     tx_broadcast: 141
     rx_multicast: 159
     tx_multicast: 150
     rx_errors: 0
     tx_errors: 0
     tx_dropped: 0
     multicast: 159
     collisions: 0
     rx_length_errors: 0
     rx_over_errors: 0
     rx_crc_errors: 0
     rx_frame_errors: 0
     rx_no_buffer_count: 0
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
     tx_window_errors: 0
     tx_abort_late_coll: 0
     tx_deferred_ok: 0
     tx_single_coll_ok: 0
     tx_multi_coll_ok: 0
     tx_timeout_count: 0
     tx_restart_queue: 0
     rx_long_length_errors: 0
     rx_short_length_errors: 0
     rx_align_errors: 0
     tx_tcp_seg_good: 2
     tx_tcp_seg_failed: 0
     rx_flow_control_xon: 0
     rx_flow_control_xoff: 0
     tx_flow_control_xon: 0
     tx_flow_control_xoff: 0
     rx_long_byte_count: 100861052
     rx_csum_offload_good: 92071
     rx_csum_offload_errors: 0
     rx_header_split: 0
     alloc_rx_buff_failed: 0
     tx_smbus: 0
     rx_smbus: 0
     dropped_smbus: 0
     rx_dma_failed: 0
     tx_dma_failed: 0

The test result is PASS
The test extra info:
Register test  (offline)     0
Eeprom test    (offline)     0
Interrupt test (offline)     0
Loopback test  (offline)     0
Link test   (on/offline)     0

*-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1e:4f:f9:a9:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.4-0 ip=10.1.100.35 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:99:4d:49:7d:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---


---
title: "debug bad ethernet packets"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by fransfrans on 2013-04-15
Hi there, I am trying to debug some custom made hardware which sends out 10Gbit ethernet packets.
My PC (running ubuntu 12.04) has in ixgbe network card.
ethtool -S eth1 gives an increasing number of rx_errors, but all other values stay the same.

I already added these lines to my ixgbe driver:
```
fctrl |= (IXGBE_FCTRL_SBP | /* Receive bad packets */
              IXGBE_FCTRL_BAM | /* RX All Bcast Pkts */
              IXGBE_FCTRL_PMCF); /* RX All MAC Ctrl Pkts */ 
```

in order to let it receive bad packets.
now I would like to see the content of these malformed packets. Wireshark and tcpdump don't show them. Is there a way do dump the content of these (probably malformed) raw ethernet packets?

Thanks for your help

---

### Post by fransfrans on 2013-04-16
For your information, the output of ethtool -S after a few hours:
```

Every 1.0s: ethtool -S eth1                                                                                                                                                          Tue Apr 16 08:23:27 2013

NIC statistics:
     rx_packets: 0
     tx_packets: 53
     rx_bytes: 0
     tx_bytes: 9774
     rx_pkts_nic: 34
     tx_pkts_nic: 533
     rx_bytes_nic: 7664
     tx_bytes_nic: 128593
     lsc_int: 836
     tx_busy: 0
     non_eop_descs: 0
     rx_errors: 4141831567
     tx_errors: 0
     rx_dropped: 0
     tx_dropped: 0
     multicast: 34
     broadcast: 0
     rx_no_buffer_count: 0
     collisions: 0
     rx_over_errors: 0
     rx_crc_errors: 11547
     rx_frame_errors: 0
     hw_rsc_aggregated: 0
     hw_rsc_flushed: 0
     fdir_match: 0
     fdir_miss: 34
     fdir_overflow: 0
     rx_fifo_errors: 0
     rx_missed_errors: 0
     tx_aborted_errors: 0
     tx_carrier_errors: 0
     tx_fifo_errors: 0
     tx_heartbeat_errors: 0
     tx_timeout_count: 0
     tx_restart_queue: 0
     rx_long_length_errors: 0
     rx_short_length_errors: 0
     tx_flow_control_xon: 2
     rx_flow_control_xon: 0
     tx_flow_control_xoff: 3
     rx_flow_control_xoff: 0
     rx_csum_offload_errors: 0
     alloc_rx_page_failed: 0
     alloc_rx_buff_failed: 0
     rx_no_dma_resources: 0
     os2bmc_rx_by_bmc: 0
     os2bmc_tx_by_bmc: 0
     os2bmc_tx_by_host: 0
     os2bmc_rx_by_host: 0
     fcoe_bad_fccrc: 0
     rx_fcoe_dropped: 0
     rx_fcoe_packets: 0
     rx_fcoe_dwords: 0
     fcoe_noddp: 0
     fcoe_noddp_ext_buff: 0
     tx_fcoe_packets: 0
     tx_fcoe_dwords: 0
     tx_queue_0_packets: 1
     tx_queue_0_bytes: 206
     tx_queue_1_packets: 26

```

All numbers stay more or less constant, only rx_errors increases with the number of packets I send. Is there a way to figure out what causes this error?
If there is no crc error (apart from a few that has been caused by other reasons) what can possibly be the reason of discarding those packets?
Thanks!

---


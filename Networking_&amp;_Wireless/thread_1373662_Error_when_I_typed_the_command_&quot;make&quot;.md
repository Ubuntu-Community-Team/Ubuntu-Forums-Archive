---
title: "Error when I typed the command &quot;make&quot;"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by zach_kirov on 2010-01-06
Hi I followed the instruction in [http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG](http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG)
When I do until the "make" step, I get an error like this. I have tried to use 'make SHELL=/bin/bash' and I got the same error too. May I know what is the problem please?

-------------------------------------------------------------------------------------------
ubuntugod@ubuntu:~/ipwraw-ng$ sudo make

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

make -C /lib/modules/2.6.31-16-generic/build M=/home/ubuntugod/ipwraw-ng modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'

WARNING: $SHELL not set to bash.
If you experience build errors, try
'make SHELL=/bin/bash'.

  CC [M]  /home/ubuntugod/ipwraw-ng/ipwraw.o
/home/ubuntugod/ipwraw-ng/ipwraw.c:43:27: error: net/ieee80211.h: No such file or directory
In file included from /home/ubuntugod/ipwraw-ng/ipwraw.h:51,
                 from /home/ubuntugod/ipwraw-ng/ipwraw.c:48:
/home/ubuntugod/ipwraw-ng/iwlwifi_hw.h:525: error: array type has incomplete element type
/home/ubuntugod/ipwraw-ng/iwlwifi_hw.h:847: error: array type has incomplete element type
In file included from /home/ubuntugod/ipwraw-ng/ipwraw.c:48:
/home/ubuntugod/ipwraw-ng/ipwraw.h:531: error: field ‘frame’ has incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.h:532: error: ‘IEEE80211_FRAME_LEN’ undeclared here (not in a function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘frame_get_hdrlen’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: ‘IEEE80211_3ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: (Each undeclared identifier is reported only once
/home/ubuntugod/ipwraw-ng/ipwraw.c:52: error: for each function it appears in.)
/home/ubuntugod/ipwraw-ng/ipwraw.c:53: error: implicit declaration of function ‘WLAN_FC_GET_STYPE’
/home/ubuntugod/ipwraw-ng/ipwraw.c:55: error: implicit declaration of function ‘WLAN_FC_GET_TYPE’
/home/ubuntugod/ipwraw-ng/ipwraw.c:56: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_FROMDS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:57: error: ‘IEEE80211_FCTL_TODS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:58: error: ‘IEEE80211_4ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:59: error: ‘IEEE80211_STYPE_QOS_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:62: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:64: error: ‘IEEE80211_STYPE_CTS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:65: error: ‘IEEE80211_STYPE_ACK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:66: error: ‘IEEE80211_1ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:69: error: ‘IEEE80211_2ADDR_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_channel_a_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1709: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_channel_bg_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1714: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘store_channel’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1878: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:1884: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘store_band’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:1926: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:1927: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_get_channel_info’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:3284: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:3294: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘reg_get_chnl_grp_index’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:3489: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_init_channel_map’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:4111: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4112: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_post_alive_work’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:4248: error: ‘IEEE80211_OFDM_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4249: error: ‘IEEE80211_OFDM_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4250: error: ‘IEEE80211_CCK_DEFAULT_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:4251: error: ‘IEEE80211_CCK_BASIC_RATES_MASK’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_queue_tx_free_tfd’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:5974: error: implicit declaration of function ‘ieee80211_get_hdrlen’
/home/ubuntugod/ipwraw-ng/ipwraw.c:5974: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘raw_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6396: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6406: error: ‘ETH_P_80211_RAW’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6416: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c:6416: warning: its scope is only this definition or declaration, which is probably not what you want
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_data_packet’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6441: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6456: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘is_duplicate_packet’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6458: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6459: error: implicit declaration of function ‘WLAN_GET_SEQ_SEQ’
/home/ubuntugod/ipwraw-ng/ipwraw.c:6460: error: implicit declaration of function ‘WLAN_GET_SEQ_FRAG’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_tx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6504: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6509: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6509: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6514: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6514: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6522: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6526: error: ‘IEEE80211_RADIOTAP_HDRLEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6540: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6563: warning: ‘struct ieee80211_rx_stats’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_promiscuous_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6618: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6623: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6623: error: ‘IEEE80211_FTYPE_CTL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6628: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6628: error: ‘IEEE80211_FTYPE_DATA’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6646: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_handle_reply_rx’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: error: variable ‘stats’ has initializer but incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: error: unknown field ‘rssi’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6853: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: error: unknown field ‘signal’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6854: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: error: unknown field ‘noise’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6855: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: error: unknown field ‘mac_time’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6856: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: error: unknown field ‘rate’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6857: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: error: unknown field ‘received_channel’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6858: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: error: unknown field ‘len’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6859: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6860: error: unknown field ‘freq’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6863: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: error: unknown field ‘tsf’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6864: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: error: unknown field ‘beacon_time’ specified in initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: warning: excess elements in struct initializer
/home/ubuntugod/ipwraw-ng/ipwraw.c:6865: warning: (near initialization for ‘stats’)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: error: storage size of ‘stats’ isn’t known
/home/ubuntugod/ipwraw-ng/ipwraw.c:6881: error: ‘IEEE80211_STATMASK_RSSI’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6885: error: ‘IEEE80211_STATMASK_SIGNAL’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6887: error: ‘IEEE80211_STATMASK_NOISE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6889: error: ‘IEEE80211_STATMASK_RATE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:6852: warning: unused variable ‘stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7256: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_rate’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7263: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7264: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7286: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7295: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7302: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7303: error: ‘IEEE80211_STYPE_AUTH’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7304: error: ‘IEEE80211_STYPE_DEAUTH’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7305: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7306: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: At top level:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7333: warning: ‘struct ieee80211_hdr_4addr’ declared inside parameter list
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_build_tx_cmd_basic’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7340: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7340: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7341: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7344: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7345: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7354: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7354: error: ‘IEEE80211_FCTL_MOREFRAGS’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7359: error: ‘IEEE80211_FCS_LEN’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7366: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7366: error: ‘IEEE80211_FCTL_PROTECTED’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7382: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7383: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7384: error: ‘IEEE80211_STYPE_ASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7385: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7386: error: ‘IEEE80211_STYPE_REASSOC_REQ’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘tx_skb’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7420: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7422: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7423: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7427: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7430: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7435: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7439: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7491: warning: passing argument 3 of ‘ipw_build_tx_cmd_basic’ from incompatible pointer type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7330: note: expected ‘struct ieee80211_hdr_4addr *’ but argument is of type ‘struct ieee80211_hdr_4addr *’
/home/ubuntugod/ipwraw-ng/ipwraw.c:7493: warning: passing argument 3 of ‘ipw_build_tx_cmd_rate’ from incompatible pointer type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7253: note: expected ‘struct ieee80211_hdr_4addr *’ but argument is of type ‘struct ieee80211_hdr_4addr *’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_net_hard_start_xmit’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:7562: error: invalid application of ‘sizeof’ to incomplete type ‘struct ieee80211_hdr_1addr’
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_FTYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FTYPE_MGMT’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_FCTL_STYPE’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7581: error: ‘IEEE80211_STYPE_PROBE_RESP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:7582: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7583: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c:7586: error: dereferencing pointer to incomplete type
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_prom_alloc’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8374: error: ‘ARPHRD_IEEE80211_RADIOTAP’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8375: error: ‘struct net_device’ has no member named ‘open’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8376: error: ‘struct net_device’ has no member named ‘stop’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8377: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8378: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_wx_set_freq’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8517: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8523: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c: In function ‘ipw_pci_probe’:
/home/ubuntugod/ipwraw-ng/ipwraw.c:8870: error: ‘IEEE80211_52GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8872: error: ‘IEEE80211_24GHZ_BAND’ undeclared (first use in this function)
/home/ubuntugod/ipwraw-ng/ipwraw.c:8897: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8898: error: ‘struct net_device’ has no member named ‘open’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8899: error: ‘struct net_device’ has no member named ‘stop’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8900: error: ‘struct net_device’ has no member named ‘get_stats’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8901: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/ubuntugod/ipwraw-ng/ipwraw.c:8902: error: ‘ARPHRD_IEEE80211’ undeclared (first use in this function)
make[2]: *** [/home/ubuntugod/ipwraw-ng/ipwraw.o] Error 1
make[1]: *** [_module_/home/ubuntugod/ipwraw-ng] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2
-------------------------------------------------------------------------------------------

---

### Post by zach_kirov on 2010-01-06
anyone can help me?

---

### Post by changingstate on 2010-01-06
You're using an older driver for your card. As you're using kernel 2.6.31, I suggest using the iwl3945 module that's included with the stock kernel, rather than trying to roll the old module, as it should come with injection built in.

See : [http://www.aircrack-ng.org/doku.php?id=iwl3945](http://www.aircrack-ng.org/doku.php?id=iwl3945)

---

### Post by zach_kirov on 2010-01-06
[COLOR=black]Thanks for the info. Sorry i am new to ubuntu, can you explain more to me? Do you mean that I should install the  iwl3945 before install the [FONT=courier new]ipwraw-ng? Or I can use [/FONT]iwl3945 to set my adapter to monitor mode without  [FONT=courier new]ipwraw-ng?[/FONT][/COLOR]

---

### Post by changingstate on 2010-01-06
The info on the aircrack site says iwl3945 will allow monitor mode by itself, no need for any of the ipraw stuff. :)

If I have it right, you should just need to modprobe iwl3945 ( if needed ), having downloaded and installed iw ( [http://wireless.kernel.org/download/iw/](http://wireless.kernel.org/download/iw/) ) and aircrack itself ( See link on [http://www.aircrack-ng.org/doku.php](http://www.aircrack-ng.org/doku.php) ), then you're ready to go. 

The tutorials on the aircrack site are great, too, I highly recommend reading them if you're new to playing with this fun piece of software, ok? :D

---

### Post by zach_kirov on 2010-01-06
i see. on the page you gave, [http://www.aircrack-ng.org/doku.php?id=iwl3945](http://www.aircrack-ng.org/doku.php?id=iwl3945)
point number 4, Download [the fragmentation patch]("http://patches.aircrack-ng.org/mac80211_2.6.28-rc4-wl_frag+ack_v2.patch"), and apply it to the compat-wireless package. This is needed to make attacks -5 and -7 work.

May I know how to apply patch? what's the syntax?

btw the patch link is not working too

---

### Post by zach_kirov on 2010-01-06
i downloaded the iwl3945 and untar it. when i type "make" it gives me the following error:

---------------------------------------------------------------------------
ubuntugod@ubuntu:~$ cd compat-wireless*
ubuntugod@ubuntu:~/compat-wireless-2.6.31-rc7$ make
./scripts/gen-compat-autoconf.sh config.mk > include/linux/compat_autoconf.h
make -C /lib/modules/2.6.31-16-generic/build M=/home/ubuntugod/compat-wireless-2.6.31-rc7 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  LD      /home/ubuntugod/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/built-in.o
make[3]: *** No rule to make target `/home/ubuntugod/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.c', needed by `/home/ubuntugod/compat-wireless-2.6.31-rc7/drivers/misc/eeprom/max6875.o'.  Stop.
make[2]: *** [/home/ubuntugod/compat-wireless-2.6.31-rc7/drivers/misc/eeprom] Error 2
make[1]: *** [_module_/home/ubuntugod/compat-wireless-2.6.31-rc7] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [modules] Error 2
---------------------------------------------------------------------------

---

### Post by changingstate on 2010-01-06
Aaah, ok. Good to know you're reading :)

Right, lets return to your original post. You'll notice you posted :

make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'

2.6.31 is the version of the linux kernel you're running. The kernel basically manages talk between the hardware and your programs, all modern OSes have one. ( You can check this with the uname -r command in terminal in future, should you need to ).

Now check out the page you referred to : 

Starting with 2.6.24, the driver is included in the kernel. **Injection requires 2.6.25 or later.** The compat-wireless-old package must be installed and patched to get injection support on 2.6.25 and 2.6.26. For 2.6.27 and newer, no special patch is needed, follow the common instructions for [mac80211]("http://www.aircrack-ng.org/doku.php?id=mac80211").  

2.6.31 is a higher number than 2.6.27, thus the kernel is a newer version, so make a beeline for the mac80211 page. :D

---

### Post by zach_kirov on 2010-01-06
yeah I just realised that and then I proceed to "make". However, I get the error instead. Do you know what's the problem? I have tried "sudo make" and the result is the same.

---

### Post by changingstate on 2010-01-06
You're trying to build compat-wireless in the last build log you posted. You don't need it, so just ignore it. iw is what's needed next. 0.9.14 is in the repositories ( just checked ), so you might like to try grabbing that along with the suprisingly up to date version of aircrack ( sudo apt-get install iw aircrack-ng ).

---

### Post by zach_kirov on 2010-01-06
i see. i proceeded to install iw and get the following error when i type "make"

--------------------------------------------------------
ubuntugod@ubuntu:~$ tar -xjf iw-0.9.14*
ubuntugod@ubuntu:~$ cd iw-0.9.14*
ubuntugod@ubuntu:~/iw-0.9.14$ make
Makefile:33: *** Cannot find development files for any supported version of libnl.  Stop.
ubuntugod@ubuntu:~/iw-0.9.14$ ls
COPYING  genl.c  info.c       iw.8  iw.h      mesh.c   nl80211.h  README    reg.c   station.c  util.c
event.c  ibss.c  interface.c  iw.c  Makefile  mpath.c  phy.c      reason.c  scan.c  status.c   version.sh
--------------------------------------------------------

but when i typed "sudo apt-get install iw aircrack-ng" , i get the following instead:

ubuntugod@ubuntu:~$ sudo apt-get install iw aircrack-ng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  aircrack-ng iw
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,596kB of archives.
After this operation, 2,937kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe iw 0.9.14-1 [30.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe aircrack-ng 1:1.0-1 [1,566kB]
Fetched 1,596kB in 6s (249kB/s)                                                                            
Selecting previously deselected package iw.
(Reading database ... 119562 files and directories currently installed.)
Unpacking iw (from .../archives/iw_0.9.14-1_i386.deb) ...
Selecting previously deselected package aircrack-ng.
Unpacking aircrack-ng (from .../aircrack-ng_1%3a1.0-1_i386.deb) ...
Processing triggers for man-db ...
Setting up iw (0.9.14-1) ...
Setting up aircrack-ng (1:1.0-1) ...


does it means that i already successfully installed them?
[FONT=courier new] [/FONT]

---

### Post by changingstate on 2010-01-06
Edit : It means you've just installed them now :) Just test it works by following a tutorial.

---

### Post by zach_kirov on 2010-01-06
i see. ok, thank you. I tried to set my adapter to monitor mode but it doesn't seem to be successful.

------------------------------------------------------------------------------------------------------------------------------

ubuntugod@ubuntu:~$ sudo airmon-ng start wlan0


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
897    NetworkManager
913    avahi-daemon
916    avahi-daemon
1084    wpa_supplicant
1264    dhclient


Interface    Chipset        Driver

wlan0        Intel 3945ABG    iwl3945 - [phy0]
                (monitor mode enabled on mon0)

ubuntugod@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11abg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
------------------------------------------------------------------------------------------------------------------------------

---

### Post by changingstate on 2010-01-06
Look at that :

wlan0        Intel 3945ABG    iwl3945 - [phy0]
                (monitor mode enabled on mon0)

Looks like you're good to go.

---

### Post by zach_kirov on 2010-01-06
yea, although it said monitor mode enabled, but when I typed iwconfig it still shows managed mode and wlan0 instead of monitor mode and wifi0.
According to this page [http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG](http://maxi-pedia.com/how+to+crack+WEP+with+intel+PRO+wireless+3945ABG) , there is a picture - [http://maxi-pedia.com/web_files/images/How_to_crack_WEP_with_Intel_Wireless_PRO.png](http://maxi-pedia.com/web_files/images/How_to_crack_WEP_with_Intel_Wireless_PRO.png) and it shows that cracking WEP in managed mode is not possible. after changed to monitor mode, the wlan0 should be changed to wifi0.

I think I know the reason now. Because the driver is different. According to this page, [http://www.aircrack-ng.org/doku.php?id=iwl3945#intel_pro_wireless_3945abg_mac80211_driver](http://www.aircrack-ng.org/doku.php?id=iwl3945#intel_pro_wireless_3945abg_mac80211_driver) , it will create an interface called mon0 and use that to monitor. So I can start to monitor already.


But I have a question: How to set back to managed mode?

---

### Post by changingstate on 2010-01-06
Ignore the maxipedia article, it's out of date. Try looking at : [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack) 

Remember your device is using mon0 rather than ath0 when monitoring.

Edit, Yep, to return to managed mode, just issue airmon-ng stop mon0

---

### Post by zach_kirov on 2010-01-06
I see I see. That's great. Now I get the idea. Alright, thank you very much!!

---


---
title: "Re: Wireless Access Point"
date: 2012-07-31
forum: Networking &amp; Wireless
---

### Post by ctownstud00 on 2012-07-31
I know [this thread]("http://ubuntuforums.org/showthread.php?t=1488953") is a little old, but I'm having issues getting things to work. I have followed the steps in this thread and have had limited success using the user-provided script (thanks)! My only exception is that I read DHCP3-server has some issues, and so I turned to DNSMasq instead. It appears to be providing proper DHCP IPs, but, perhaps my routing tables aren't right? I'm not sure..

My issue is that I am unable to access the Internet with my iPhone when connecting to my Netbook's soft AP "hotspot."

I am using a Netbook running Ubuntu 10.04, with an internal WiFi card acting as the soft AP and a USB WiFi card connecting to "Internet" WiFi networks. I want to essentially repeat this through the internal card.

My iPhone will connect to my "hotspot," but it will take a long time to try loading things, eventually returning "Not connected to the Internet" errors.

Here are my configuration files:

hostapd.conf
```
##### hostapd configuration file ##############################################
# Empty lines and lines starting with # are ignored

# AP netdevice name (without 'ap' postfix, i.e., wlan0 uses wlan0ap for
# management frames); ath0 for madwifi
interface=wlan0

# In case of madwifi and nl80211 driver interfaces, an additional configuration
# parameter, bridge, must be used to notify hostapd if the interface is
# included in a bridge. This parameter is not used with Host AP driver.
#bridge=br0

# Driver interface type (hostap/wired/madwifi/prism54/test/none/nl80211/bsd);
# default: hostap). nl80211 is used with all Linux mac80211 drivers.
# Use driver=none if building hostapd as a standalone RADIUS server that does
# not control any wireless/wired driver.
driver=nl80211

# hostapd event logger configuration
#
# Two output method: syslog and stdout (only usable if not forking to
# background).
#
# Module bitfield (ORed bitfield of modules that will be logged; -1 = all
# modules):
# bit 0 (1) = IEEE 802.11
# bit 1 (2) = IEEE 802.1X
# bit 2 (4) = RADIUS
# bit 3 (8) = WPA
# bit 4 (16) = driver interface
# bit 5 (32) = IAPP
# bit 6 (64) = MLME
#
# Levels (minimum value for logged events):
#  0 = verbose debugging
#  1 = debugging
#  2 = informational messages
#  3 = notification
#  4 = warning
#
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2

# Dump file for state information (on SIGUSR1)
dump_file=/tmp/hostapd.dump

# Interface for separate control program. If this is specified, hostapd
# will create this directory and a UNIX domain socket for listening to requests
# from external programs (CLI/GUI, etc.) for status information and
# configuration. The socket file will be named based on the interface name, so
# multiple hostapd processes/interfaces can be run at the same time if more
# than one interface is used.
# /var/run/hostapd is the recommended directory for sockets and by default,
# hostapd_cli will use it when trying to connect with hostapd.
ctrl_interface=/var/run/hostapd

# Access control for the control interface can be configured by setting the
# directory to allow only members of a group to use sockets. This way, it is
# possible to run hostapd as root (since it needs to change network
# configuration and open raw sockets) and still allow GUI/CLI components to be
# run as non-root users. However, since the control interface can be used to
# change the network configuration, this access needs to be protected in many
# cases. By default, hostapd is configured to use gid 0 (root). If you
# want to allow non-root users to use the contron interface, add a new group
# and change this value to match with that group. Add users that should have
# control interface access to this group.
#
# This variable can be a group name or gid.
#ctrl_interface_group=wheel
ctrl_interface_group=0


##### IEEE 802.11 related configuration #######################################

# SSID to be used in IEEE 802.11 management frames
ssid=K8JSM-Hot

# Country code (ISO/IEC 3166-1). Used to set regulatory domain.
# Set as needed to indicate country in which device is operating.
# This can limit available channels and transmit power.
country_code=US

# Enable IEEE 802.11d. This advertises the country_code and the set of allowed
# channels and transmit power levels based on the regulatory limits. The
# country_code setting must be configured with the correct country for
# IEEE 802.11d functions.
# (default: 0 = disabled)
#ieee80211d=1

# Operation mode (a = IEEE 802.11a, b = IEEE 802.11b, g = IEEE 802.11g,
# Default: IEEE 802.11b
hw_mode=g

# Channel number (IEEE 802.11)
# (default: 0, i.e., not set)
# Please note that some drivers (e.g., madwifi) do not use this value from
# hostapd and the channel will need to be configuration separately with
# iwconfig.
channel=3

# Beacon interval in kus (1.024 ms) (default: 100; range 15..65535)
beacon_int=100

# DTIM (delivery trafic information message) period (range 1..255):
# number of beacons between DTIMs (1 = every beacon includes DTIM element)
# (default: 2)
dtim_period=2

# Maximum number of stations allowed in station table. New stations will be
# rejected after the station table is full. IEEE 802.11 has a limit of 2007
# different association IDs, so this number should not be larger than that.
# (default: 2007)
max_num_sta=50

# RTS/CTS threshold; 2347 = disabled (default); range 0..2347
# If this field is not included in hostapd.conf, hostapd will not control
# RTS threshold and 'iwconfig wlan# rts <val>' can be used to set it.
rts_threshold=2347

# Fragmentation threshold; 2346 = disabled (default); range 256..2346
# If this field is not included in hostapd.conf, hostapd will not control
# fragmentation threshold and 'iwconfig wlan# frag <val>' can be used to set
# it.
fragm_threshold=2346

# Rate configuration
# Default is to enable all rates supported by the hardware. This configuration
# item allows this list be filtered so that only the listed rates will be left
# in the list. If the list is empty, all rates are used. This list can have
# entries that are not in the list of rates the hardware supports (such entries
# are ignored). The entries in this list are in 100 kbps, i.e., 11 Mbps = 110.
# If this item is present, at least one rate have to be matching with the rates
# hardware supports.
# default: use the most common supported rate setting for the selected
# hw_mode (i.e., this line can be removed from configuration file in most
# cases)
#supported_rates=10 20 55 110 60 90 120 180 240 360 480 540

# Basic rate set configuration
# List of rates (in 100 kbps) that are included in the basic rate set.
# If this item is not included, usually reasonable default set is used.
#basic_rates=10 20
#basic_rates=10 20 55 110
#basic_rates=60 120 240

# Short Preamble
# This parameter can be used to enable optional use of short preamble for
# frames sent at 2 Mbps, 5.5 Mbps, and 11 Mbps to improve network performance.
# This applies only to IEEE 802.11b-compatible networks and this should only be
# enabled if the local hardware supports use of short preamble. If any of the
# associated STAs do not support short preamble, use of short preamble will be
# disabled (and enabled when such STAs disassociate) dynamically.
# 0 = do not allow use of short preamble (default)
# 1 = allow use of short preamble
#preamble=1

# Station MAC address -based authentication
# Please note that this kind of access control requires a driver that uses
# hostapd to take care of management frame processing and as such, this can be
# used with driver=hostap or driver=nl80211, but not with driver=madwifi.
# 0 = accept unless in deny list
# 1 = deny unless in accept list
# 2 = use external RADIUS server (accept/deny lists are searched first)
macaddr_acl=0

# Accept/deny lists are read from separate files (containing list of
# MAC addresses, one per line). Use absolute path name to make sure that the
# files can be read on SIGHUP configuration reloads.
#accept_mac_file=/etc/hostapd/hostapd.accept
#deny_mac_file=/etc/hostapd/hostapd.deny

# IEEE 802.11 specifies two authentication algorithms. hostapd can be
# configured to allow both of these or only one. Open system authentication
# should be used with IEEE 802.1X.
# Bit fields of allowed authentication algorithms:
# bit 0 = Open System Authentication
# bit 1 = Shared Key Authentication (requires WEP)
auth_algs=1

# Send empty SSID in beacons and ignore probe request frames that do not
# specify full SSID, i.e., require stations to know SSID.
# default: disabled (0)
# 1 = send empty (length=0) SSID in beacon and ignore probe request for
#     broadcast SSID
# 2 = clear SSID (ASCII 0), but keep the original length (this may be required
#     with some clients that do not support empty SSID) and ignore probe
#     requests for broadcast SSID
ignore_broadcast_ssid=0

# TX queue parameters (EDCF / bursting)
# default for all these fields: not set, use hardware defaults
# tx_queue_<queue name>_<param>
# queues: data0, data1, data2, data3, after_beacon, beacon
#        (data0 is the highest priority queue)
# parameters:
#   aifs: AIFS (default 2)
#   cwmin: cwMin (1, 3, 7, 15, 31, 63, 127, 255, 511, 1023)
#   cwmax: cwMax (1, 3, 7, 15, 31, 63, 127, 255, 511, 1023); cwMax >= cwMin
#   burst: maximum length (in milliseconds with precision of up to 0.1 ms) for
#          bursting
#
# Default WMM parameters (IEEE 802.11 draft; 11-03-0504-03-000e):
# These parameters are used by the access point when transmitting frames
# to the clients.
#
# Low priority / AC_BK = background
#tx_queue_data3_aifs=7
#tx_queue_data3_cwmin=15
#tx_queue_data3_cwmax=1023
#tx_queue_data3_burst=0
# Note: for IEEE 802.11b mode: cWmin=31 cWmax=1023 burst=0
#
# Normal priority / AC_BE = best effort
#tx_queue_data2_aifs=3
#tx_queue_data2_cwmin=15
#tx_queue_data2_cwmax=63
#tx_queue_data2_burst=0
# Note: for IEEE 802.11b mode: cWmin=31 cWmax=127 burst=0
#
# High priority / AC_VI = video
#tx_queue_data1_aifs=1
#tx_queue_data1_cwmin=7
#tx_queue_data1_cwmax=15
#tx_queue_data1_burst=3.0
# Note: for IEEE 802.11b mode: cWmin=15 cWmax=31 burst=6.0
#
# Highest priority / AC_VO = voice
#tx_queue_data0_aifs=1
#tx_queue_data0_cwmin=3
#tx_queue_data0_cwmax=7
#tx_queue_data0_burst=1.5
# Note: for IEEE 802.11b mode: cWmin=7 cWmax=15 burst=3.3
#
# Special queues; normally not user configurable
#
#tx_queue_after_beacon_aifs=2
#tx_queue_after_beacon_cwmin=15
#tx_queue_after_beacon_cwmax=1023
#tx_queue_after_beacon_burst=0
#
#tx_queue_beacon_aifs=2
#tx_queue_beacon_cwmin=3
#tx_queue_beacon_cwmax=7
#tx_queue_beacon_burst=1.5

# 802.1D Tag (= UP) to AC mappings
# WMM specifies following mapping of data frames to different ACs. This mapping
# can be configured using Linux QoS/tc and sch_pktpri.o module.
# 802.1D Tag    802.1D Designation    Access Category    WMM Designation
# 1        BK            AC_BK        Background
# 2        -            AC_BK        Background
# 0        BE            AC_BE        Best Effort
# 3        EE            AC_BE        Best Effort
# 4        CL            AC_VI        Video
# 5        VI            AC_VI        Video
# 6        VO            AC_VO        Voice
# 7        NC            AC_VO        Voice
# Data frames with no priority information: AC_BE
# Management frames: AC_VO
# PS-Poll frames: AC_BE

# Default WMM parameters (IEEE 802.11 draft; 11-03-0504-03-000e):
# for 802.11a or 802.11g networks
# These parameters are sent to WMM clients when they associate.
# The parameters will be used by WMM clients for frames transmitted to the
# access point.
#
# note - txop_limit is in units of 32microseconds
# note - acm is admission control mandatory flag. 0 = admission control not
# required, 1 = mandatory
# note - here cwMin and cmMax are in exponent form. the actual cw value used
# will be (2^n)-1 where n is the value given here
#
wme_enabled=1
#
# Low priority / AC_BK = background
wme_ac_bk_cwmin=4
wme_ac_bk_cwmax=10
wme_ac_bk_aifs=7
wme_ac_bk_txop_limit=0
wme_ac_bk_acm=0
# Note: for IEEE 802.11b mode: cWmin=5 cWmax=10
#
# Normal priority / AC_BE = best effort
wme_ac_be_aifs=3
wme_ac_be_cwmin=4
wme_ac_be_cwmax=10
wme_ac_be_txop_limit=0
wme_ac_be_acm=0
# Note: for IEEE 802.11b mode: cWmin=5 cWmax=7
#
# High priority / AC_VI = video
wme_ac_vi_aifs=2
wme_ac_vi_cwmin=3
wme_ac_vi_cwmax=4
wme_ac_vi_txop_limit=94
wme_ac_vi_acm=0
# Note: for IEEE 802.11b mode: cWmin=4 cWmax=5 txop_limit=188
#
# Highest priority / AC_VO = voice
wme_ac_vo_aifs=2
wme_ac_vo_cwmin=2
wme_ac_vo_cwmax=3
wme_ac_vo_txop_limit=47
wme_ac_vo_acm=0
# Note: for IEEE 802.11b mode: cWmin=3 cWmax=4 burst=102

# Static WEP key configuration
#
# The key number to use when transmitting.
# It must be between 0 and 3, and the corresponding key must be set.
# default: not set
#wep_default_key=0
# The WEP keys to use.
# A key may be a quoted string or unquoted hexadecimal digits.
# The key length should be 5, 13, or 16 characters, or 10, 26, or 32
# digits, depending on whether 40-bit (64-bit), 104-bit (128-bit), or
# 128-bit (152-bit) WEP is used.
# Only the default key must be supplied; the others are optional.
# default: not set
#wep_key0=123456789a
#wep_key1="vwxyz"
#wep_key2=0102030405060708090a0b0c0d
#wep_key3=".2.4.6.8.0.23"

# Station inactivity limit
#
# If a station does not send anything in ap_max_inactivity seconds, an
# empty data frame is sent to it in order to verify whether it is
# still in range. If this frame is not ACKed, the station will be
# disassociated and then deauthenticated. This feature is used to
# clear station table of old entries when the STAs move out of the
# range.
#
# The station can associate again with the AP if it is still in range;
# this inactivity poll is just used as a nicer way of verifying
# inactivity; i.e., client will not report broken connection because
# disassociation frame is not sent immediately without first polling
# the STA with a data frame.
# default: 300 (i.e., 5 minutes)
#ap_max_inactivity=300

# Enable/disable internal bridge for packets between associated stations.
#
# When IEEE 802.11 is used in managed mode, packets are usually send through
# the AP even if they are from a wireless station to another wireless station.
# This functionality requires that the AP has a bridge functionality that sends
# frames back to the same interface if their destination is another associated
# station. In addition, broadcast/multicast frames from wireless stations will
# be sent both to the host system net stack (e.g., to eventually wired network)
# and back to the wireless interface.
#
# The internal bridge is implemented within the wireless kernel module and it
# bypasses kernel filtering (netfilter/iptables/ebtables). If direct
# communication between the stations needs to be prevented, the internal
# bridge can be disabled by setting bridge_packets=0.
#
# Note: If this variable is not included in hostapd.conf, hostapd does not
# change the configuration and iwpriv can be used to set the value with
# 'iwpriv wlan# param 10 0' command. If the variable is in hostapd.conf,
# hostapd will override possible iwpriv configuration whenever configuration
# file is reloaded.
#
# default: do not control from hostapd (80211.o defaults to 1=enabled)
#bridge_packets=1

# Maximum allowed Listen Interval (how many Beacon periods STAs are allowed to
# remain asleep). Default: 65535 (no limit apart from field size)
#max_listen_interval=100

##### IEEE 802.11n related configuration ######################################

# ieee80211n: Whether IEEE 802.11n (HT) is enabled
# 0 = disabled (default)
# 1 = enabled
#ieee80211n=1

# ht_capab: HT capabilities (list of flags)
# LDPC coding capability: [LDPC] = supported
# Supported channel width set: [HT40-] = both 20 MHz and 40 MHz with secondary
#    channel below the primary channel; [HT40+] = both 20 MHz and 40 MHz
#    with secondary channel below the primary channel
#    (20 MHz only if neither is set)
#    Note: There are limits on which channels can be used with HT40- and
#    HT40+. Following table shows the channels that may be available for
#    HT40- and HT40+ use per IEEE 802.11n Annex J:
#    freq        HT40-        HT40+
#    2.4 GHz        5-13        1-7 (1-9 in Europe/Japan)
#    5 GHz        40,48,56,64    36,44,52,60
#    (depending on the location, not all of these channels may be available
#    for use)
# Spatial Multiplexing (SM) Power Save: [SMPS-STATIC] or [SMPS-DYNAMIC]
#    (SMPS disabled if neither is set)
# HT-greenfield: [GF] (disabled if not set)
# Short GI for 20 MHz: [SHORT-GI-20] (disabled if not set)
# Short GI for 40 MHz: [SHORT-GI-40] (disabled if not set)
# Tx STBC: [TX-STBC] (disabled if not set)
# Rx STBC: [RX-STBC1] (one spatial stream), [RX-STBC12] (one or two spatial
#    streams), or [RX-STBC123] (one, two, or three spatial streams); Rx STBC
#    disabled if none of these set
# HT-delayed Block Ack: [DELAYED-BA] (disabled if not set)
# Maximum A-MSDU length: [MAX-AMSDU-7935] for 7935 octets (3839 octets if not
#    set)
# DSSS/CCK Mode in 40 MHz: [DSSS_CCK-40] = allowed (not allowed if not set)
# PSMP support: [PSMP] (disabled if not set)
# L-SIG TXOP protection support: [LSIG-TXOP-PROT] (disabled if not set)
#ht_capab=[HT40-][SHORT-GI-20][SHORT-GI-40]

##### IEEE 802.1X-2004 related configuration ##################################

# Require IEEE 802.1X authorization
#ieee8021x=1

# IEEE 802.1X/EAPOL version
# hostapd is implemented based on IEEE Std 802.1X-2004 which defines EAPOL
# version 2. However, there are many client implementations that do not handle
# the new version number correctly (they seem to drop the frames completely).
# In order to make hostapd interoperate with these clients, the version number
# can be set to the older version (1) with this configuration value.
#eapol_version=2

# Optional displayable message sent with EAP Request-Identity. The first \0
# in this string will be converted to ASCII-0 (nul). This can be used to
# separate network info (comma separated list of attribute=value pairs); see,
# e.g., RFC 4284.
#eap_message=hello
#eap_message=hello\0networkid=netw,nasid=foo,portid=0,NAIRealms=example.com

# WEP rekeying (disabled if key lengths are not set or are set to 0)
# Key lengths for default/broadcast and individual/unicast keys:
# 5 = 40-bit WEP (also known as 64-bit WEP with 40 secret bits)
# 13 = 104-bit WEP (also known as 128-bit WEP with 104 secret bits)
#wep_key_len_broadcast=5
#wep_key_len_unicast=5
# Rekeying period in seconds. 0 = do not rekey (i.e., set keys only once)
#wep_rekey_period=300

# EAPOL-Key index workaround (set bit7) for WinXP Supplicant (needed only if
# only broadcast keys are used)
eapol_key_index_workaround=0

# EAP reauthentication period in seconds (default: 3600 seconds; 0 = disable
# reauthentication).
#eap_reauth_period=3600

# Use PAE group address (01:80:c2:00:00:03) instead of individual target
# address when sending EAPOL frames with driver=wired. This is the most common
# mechanism used in wired authentication, but it also requires that the port
# is only used by one station.
#use_pae_group_addr=1

##### Integrated EAP server ###################################################

# Optionally, hostapd can be configured to use an integrated EAP server
# to process EAP authentication locally without need for an external RADIUS
# server. This functionality can be used both as a local authentication server
# for IEEE 802.1X/EAPOL and as a RADIUS server for other devices.

# Use integrated EAP server instead of external RADIUS authentication
# server. This is also needed if hostapd is configured to act as a RADIUS
# authentication server.
eap_server=0

# Path for EAP server user database
#eap_user_file=/etc/hostapd/hostapd.eap_user

# CA certificate (PEM or DER file) for EAP-TLS/PEAP/TTLS
#ca_cert=/etc/hostapd/hostapd.ca.pem

# Server certificate (PEM or DER file) for EAP-TLS/PEAP/TTLS
#server_cert=/etc/hostapd/hostapd.server.pem

# Private key matching with the server certificate for EAP-TLS/PEAP/TTLS
# This may point to the same file as server_cert if both certificate and key
# are included in a single file. PKCS#12 (PFX) file (.p12/.pfx) can also be
# used by commenting out server_cert and specifying the PFX file as the
# private_key.
#private_key=/etc/hostapd/hostapd.server.prv

# Passphrase for private key
#private_key_passwd=secret passphrase

# Enable CRL verification.
# Note: hostapd does not yet support CRL downloading based on CDP. Thus, a
# valid CRL signed by the CA is required to be included in the ca_cert file.
# This can be done by using PEM format for CA certificate and CRL and
# concatenating these into one file. Whenever CRL changes, hostapd needs to be
# restarted to take the new CRL into use.
# 0 = do not verify CRLs (default)
# 1 = check the CRL of the user certificate
# 2 = check all CRLs in the certificate path
#check_crl=1

# dh_file: File path to DH/DSA parameters file (in PEM format)
# This is an optional configuration file for setting parameters for an
# ephemeral DH key exchange. In most cases, the default RSA authentication does
# not use this configuration. However, it is possible setup RSA to use
# ephemeral DH key exchange. In addition, ciphers with DSA keys always use
# ephemeral DH keys. This can be used to achieve forward secrecy. If the file
# is in DSA parameters format, it will be automatically converted into DH
# params. This parameter is required if anonymous EAP-FAST is used.
# You can generate DH parameters file with OpenSSL, e.g.,
# "openssl dhparam -out /etc/hostapd/hostapd.dh.pem 1024"
#dh_file=/etc/hostapd/hostapd.dh.pem

# Configuration data for EAP-SIM database/authentication gateway interface.
# This is a text string in implementation specific format. The example
# implementation in eap_sim_db.c uses this as the UNIX domain socket name for
# the HLR/AuC gateway (e.g., hlr_auc_gw). In this case, the path uses "unix:"
# prefix.
#eap_sim_db=unix:/tmp/hlr_auc_gw.sock

# Encryption key for EAP-FAST PAC-Opaque values. This key must be a secret,
# random value. It is configured as a 16-octet value in hex format. It can be
# generated, e.g., with the following command:
# od -tx1 -v -N16 /dev/random | colrm 1 8 | tr -d ' '
#pac_opaque_encr_key=000102030405060708090a0b0c0d0e0f

# EAP-FAST authority identity (A-ID)
# A-ID indicates the identity of the authority that issues PACs. The A-ID
# should be unique across all issuing servers. In theory, this is a variable
# length field, but due to some existing implementations required A-ID to be
# 16 octets in length, it is strongly recommended to use that length for the
# field to provided interoperability with deployed peer implementation. This
# field is configured in hex format.
#eap_fast_a_id=101112131415161718191a1b1c1d1e1f

# EAP-FAST authority identifier information (A-ID-Info)
# This is a user-friendly name for the A-ID. For example, the enterprise name
# and server name in a human-readable format. This field is encoded as UTF-8.
#eap_fast_a_id_info=test server

# Enable/disable different EAP-FAST provisioning modes:
#0 = provisioning disabled
#1 = only anonymous provisioning allowed
#2 = only authenticated provisioning allowed
#3 = both provisioning modes allowed (default)
#eap_fast_prov=3

# EAP-FAST PAC-Key lifetime in seconds (hard limit)
#pac_key_lifetime=604800

# EAP-FAST PAC-Key refresh time in seconds (soft limit on remaining hard
# limit). The server will generate a new PAC-Key when this number of seconds
# (or fewer) of the lifetime remains.
#pac_key_refresh_time=86400

# EAP-SIM and EAP-AKA protected success/failure indication using AT_RESULT_IND
# (default: 0 = disabled).
#eap_sim_aka_result_ind=1

# Trusted Network Connect (TNC)
# If enabled, TNC validation will be required before the peer is allowed to
# connect. Note: This is only used with EAP-TTLS and EAP-FAST. If any other
# EAP method is enabled, the peer will be allowed to connect without TNC.
#tnc=1


##### IEEE 802.11f - Inter-Access Point Protocol (IAPP) #######################

# Interface to be used for IAPP broadcast packets
#iapp_interface=eth0


##### RADIUS client configuration #############################################
# for IEEE 802.1X with external Authentication Server, IEEE 802.11
# authentication with external ACL for MAC addresses, and accounting

# The own IP address of the access point (used as NAS-IP-Address)
own_ip_addr=127.0.0.1

# Optional NAS-Identifier string for RADIUS messages. When used, this should be
# a unique to the NAS within the scope of the RADIUS server. For example, a
# fully qualified domain name can be used here.
# When using IEEE 802.11r, nas_identifier must be set and must be between 1 and
# 48 octets long.
#nas_identifier=ap.example.com

# RADIUS authentication server
#auth_server_addr=127.0.0.1
#auth_server_port=1812
#auth_server_shared_secret=secret

# RADIUS accounting server
#acct_server_addr=127.0.0.1
#acct_server_port=1813
#acct_server_shared_secret=secret

# Secondary RADIUS servers; to be used if primary one does not reply to
# RADIUS packets. These are optional and there can be more than one secondary
# server listed.
#auth_server_addr=127.0.0.2
#auth_server_port=1812
#auth_server_shared_secret=secret2
#
#acct_server_addr=127.0.0.2
#acct_server_port=1813
#acct_server_shared_secret=secret2

# Retry interval for trying to return to the primary RADIUS server (in
# seconds). RADIUS client code will automatically try to use the next server
# when the current server is not replying to requests. If this interval is set,
# primary server will be retried after configured amount of time even if the
# currently used secondary server is still working.
#radius_retry_primary_interval=600


# Interim accounting update interval
# If this is set (larger than 0) and acct_server is configured, hostapd will
# send interim accounting updates every N seconds. Note: if set, this overrides
# possible Acct-Interim-Interval attribute in Access-Accept message. Thus, this
# value should not be configured in hostapd.conf, if RADIUS server is used to
# control the interim interval.
# This value should not be less 600 (10 minutes) and must not be less than
# 60 (1 minute).
#radius_acct_interim_interval=600

# Dynamic VLAN mode; allow RADIUS authentication server to decide which VLAN
# is used for the stations. This information is parsed from following RADIUS
# attributes based on RFC 3580 and RFC 2868: Tunnel-Type (value 13 = VLAN),
# Tunnel-Medium-Type (value 6 = IEEE 802), Tunnel-Private-Group-ID (value
# VLANID as a string). vlan_file option below must be configured if dynamic
# VLANs are used. Optionally, the local MAC ACL list (accept_mac_file) can be
# used to set static client MAC address to VLAN ID mapping.
# 0 = disabled (default)
# 1 = option; use default interface if RADIUS server does not include VLAN ID
# 2 = required; reject authentication if RADIUS server does not include VLAN ID
#dynamic_vlan=0

# VLAN interface list for dynamic VLAN mode is read from a separate text file.
# This list is used to map VLAN ID from the RADIUS server to a network
# interface. Each station is bound to one interface in the same way as with
# multiple BSSIDs or SSIDs. Each line in this text file is defining a new
# interface and the line must include VLAN ID and interface name separated by
# white space (space or tab).
#vlan_file=/etc/hostapd/hostapd.vlan

# Interface where 802.1q tagged packets should appear when a RADIUS server is
# used to determine which VLAN a station is on.  hostapd creates a bridge for
# each VLAN.  Then hostapd adds a VLAN interface (associated with the interface
# indicated by 'vlan_tagged_interface') and the appropriate wireless interface
# to the bridge.
#vlan_tagged_interface=eth0


##### RADIUS authentication server configuration ##############################

# hostapd can be used as a RADIUS authentication server for other hosts. This
# requires that the integrated EAP server is also enabled and both
# authentication services are sharing the same configuration.

# File name of the RADIUS clients configuration for the RADIUS server. If this
# commented out, RADIUS server is disabled.
#radius_server_clients=/etc/hostapd/hostapd.radius_clients

# The UDP port number for the RADIUS authentication server
#radius_server_auth_port=1812

# Use IPv6 with RADIUS server (IPv4 will also be supported using IPv6 API)
#radius_server_ipv6=1


##### WPA/IEEE 802.11i configuration ##########################################

# Enable WPA. Setting this variable configures the AP to require WPA (either
# WPA-PSK or WPA-RADIUS/EAP based on other configuration). For WPA-PSK, either
# wpa_psk or wpa_passphrase must be set and wpa_key_mgmt must include WPA-PSK.
# For WPA-RADIUS/EAP, ieee8021x must be set (but without dynamic WEP keys),
# RADIUS authentication server must be configured, and WPA-EAP must be included
# in wpa_key_mgmt.
# This field is a bit field that can be used to enable WPA (IEEE 802.11i/D3.0)
# and/or WPA2 (full IEEE 802.11i/RSN):
# bit0 = WPA
# bit1 = IEEE 802.11i/RSN (WPA2) (dot11RSNAEnabled)
#wpa=0

# WPA pre-shared keys for WPA-PSK. This can be either entered as a 256-bit
# secret in hex format (64 hex digits), wpa_psk, or as an ASCII passphrase
# (8..63 characters) that will be converted to PSK. This conversion uses SSID
# so the PSK changes when ASCII passphrase is used and the SSID is changed.
# wpa_psk (dot11RSNAConfigPSKValue)
# wpa_passphrase (dot11RSNAConfigPSKPassPhrase)
#wpa_psk=0123456789abcdef0123456789abcdef0123456789abcdef0123456789abcdef
#wpa_passphrase=

# Optionally, WPA PSKs can be read from a separate text file (containing list
# of (PSK,MAC address) pairs. This allows more than one PSK to be configured.
# Use absolute path name to make sure that the files can be read on SIGHUP
# configuration reloads.
#wpa_psk_file=/etc/hostapd/hostapd.wpa_psk

# Set of accepted key management algorithms (WPA-PSK, WPA-EAP, or both). The
# entries are separated with a space. WPA-PSK-SHA256 and WPA-EAP-SHA256 can be
# added to enable SHA256-based stronger algorithms.
# (dot11RSNAConfigAuthenticationSuitesTable)
wpa_key_mgmt=WPA-PSK

# Set of accepted cipher suites (encryption algorithms) for pairwise keys
# (unicast packets). This is a space separated list of algorithms:
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# Group cipher suite (encryption algorithm for broadcast and multicast frames)
# is automatically selected based on this configuration. If only CCMP is
# allowed as the pairwise cipher, group cipher will also be CCMP. Otherwise,
# TKIP will be used as the group cipher.
# (dot11RSNAConfigPairwiseCiphersTable)
# Pairwise cipher for WPA (v1) (default: TKIP)
wpa_pairwise=TKIP CCMP
# Pairwise cipher for RSN/WPA2 (default: use wpa_pairwise value)
rsn_pairwise=CCMP

# Time interval for rekeying GTK (broadcast/multicast encryption keys) in
# seconds. (dot11RSNAConfigGroupRekeyTime)
#wpa_group_rekey=600

# Rekey GTK when any STA that possesses the current GTK is leaving the BSS.
# (dot11RSNAConfigGroupRekeyStrict)
#wpa_strict_rekey=1

# Time interval for rekeying GMK (master key used internally to generate GTKs
# (in seconds).
#wpa_gmk_rekey=86400

# Maximum lifetime for PTK in seconds. This can be used to enforce rekeying of
# PTK to mitigate some attacks against TKIP deficiencies.
#wpa_ptk_rekey=600

# Enable IEEE 802.11i/RSN/WPA2 pre-authentication. This is used to speed up
# roaming be pre-authenticating IEEE 802.1X/EAP part of the full RSN
# authentication and key handshake before actually associating with a new AP.
# (dot11RSNAPreauthenticationEnabled)
#rsn_preauth=1
#
# Space separated list of interfaces from which pre-authentication frames are
# accepted (e.g., 'eth0' or 'eth0 wlan0wds0'. This list should include all
# interface that are used for connections to other APs. This could include
# wired interfaces and WDS links. The normal wireless data interface towards
# associated stations (e.g., wlan0) should not be added, since
# pre-authentication is only used with APs other than the currently associated
# one.
#rsn_preauth_interfaces=eth0

# peerkey: Whether PeerKey negotiation for direct links (IEEE 802.11e) is
# allowed. This is only used with RSN/WPA2.
# 0 = disabled (default)
# 1 = enabled
#peerkey=1

# ieee80211w: Whether management frame protection (MFP) is enabled
# 0 = disabled (default)
# 1 = optional
# 2 = required
#ieee80211w=0

# Association SA Query maximum timeout (in TU = 1.024 ms; for MFP)
# (maximum time to wait for a SA Query response)
# dot11AssociationSAQueryMaximumTimeout, 1...4294967295
#assoc_sa_query_max_timeout=1000

# Association SA Query retry timeout (in TU = 1.024 ms; for MFP)
# (time between two subsequent SA Query requests)
# dot11AssociationSAQueryRetryTimeout, 1...4294967295
#assoc_sa_query_retry_timeout=201


# okc: Opportunistic Key Caching (aka Proactive Key Caching)
# Allow PMK cache to be shared opportunistically among configured interfaces
# and BSSes (i.e., all configurations within a single hostapd process).
# 0 = disabled (default)
# 1 = enabled
#okc=1


##### IEEE 802.11r configuration ##############################################

# Mobility Domain identifier (dot11FTMobilityDomainID, MDID)
# MDID is used to indicate a group of APs (within an ESS, i.e., sharing the
# same SSID) between which a STA can use Fast BSS Transition.
# 2-octet identifier as a hex string.
#mobility_domain=a1b2

# PMK-R0 Key Holder identifier (dot11FTR0KeyHolderID)
# 1 to 48 octet identifier.
# This is configured with nas_identifier (see RADIUS client section above).

# Default lifetime of the PMK-RO in minutes; range 1..65535
# (dot11FTR0KeyLifetime)
#r0_key_lifetime=10000

# PMK-R1 Key Holder identifier (dot11FTR1KeyHolderID)
# 6-octet identifier as a hex string.
#r1_key_holder=000102030405

# Reassociation deadline in time units (TUs / 1.024 ms; range 1000..65535)
# (dot11FTReassociationDeadline)
#reassociation_deadline=1000

# List of R0KHs in the same Mobility Domain
# format: <MAC address> <NAS Identifier> <128-bit key as hex string>
# This list is used to map R0KH-ID (NAS Identifier) to a destination MAC
# address when requesting PMK-R1 key from the R0KH that the STA used during the
# Initial Mobility Domain Association.
#r0kh=02:01:02:03:04:05 r0kh-1.example.com 000102030405060708090a0b0c0d0e0f
#r0kh=02:01:02:03:04:06 r0kh-2.example.com 00112233445566778899aabbccddeeff
# And so on.. One line per R0KH.

# List of R1KHs in the same Mobility Domain
# format: <MAC address> <R0KH-ID> <128-bit key as hex string>
# This list is used to map R1KH-ID to a destination MAC address when sending
# PMK-R1 key from the R0KH. This is also the list of authorized R1KHs in the MD
# that can request PMK-R1 keys.
#r1kh=02:01:02:03:04:05 02:11:22:33:44:55 000102030405060708090a0b0c0d0e0f
#r1kh=02:01:02:03:04:06 02:11:22:33:44:66 00112233445566778899aabbccddeeff
# And so on.. One line per R1KH.

# Whether PMK-R1 push is enabled at R0KH
# 0 = do not push PMK-R1 to all configured R1KHs (default)
# 1 = push PMK-R1 to all configured R1KHs whenever a new PMK-R0 is derived
#pmk_r1_push=1

##### Passive scanning ########################################################
# Scan different channels every N seconds. 0 = disable passive scanning.
#passive_scan_interval=60

# Listen N usecs on each channel when doing passive scanning.
# This value plus the time needed for changing channels should be less than
# 32 milliseconds (i.e. 32000 usec) to avoid interruptions to normal
# operations. Time needed for channel changing varies based on the used wlan
# hardware.
# default: disabled (0)
#passive_scan_listen=10000

# Passive scanning mode:
# 0 = scan all supported modes (802.11a/b/g/Turbo) (default)
# 1 = scan only the mode that is currently used for normal operations
#passive_scan_mode=1

# Maximum number of entries kept in AP table (either for passive scanning or
# for detecting Overlapping Legacy BSS Condition). The oldest entry will be
# removed when adding a new entry that would make the list grow over this
# limit. Note! Wi-Fi certification for IEEE 802.11g requires that OLBC is
# enabled, so this field should not be set to 0 when using IEEE 802.11g.
# default: 255
#ap_table_max_size=255

# Number of seconds of no frames received after which entries may be deleted
# from the AP table. Since passive scanning is not usually performed frequently
# this should not be set to very small value. In addition, there is no
# guarantee that every scan cycle will receive beacon frames from the
# neighboring APs.
# default: 60
#ap_table_expiration_time=3600


##### Wi-Fi Protected Setup (WPS) #############################################

# WPS state
# 0 = WPS disabled (default)
# 1 = WPS enabled, not configured
# 2 = WPS enabled, configured
#wps_state=2

# AP can be configured into a locked state where new WPS Registrar are not
# accepted, but previously authorized Registrars (including the internal one)
# can continue to add new Enrollees.
#ap_setup_locked=1

# Universally Unique IDentifier (UUID; see RFC 4122) of the device
# This value is used as the UUID for the internal WPS Registrar. If the AP
# is also using UPnP, this value should be set to the device's UPnP UUID.
# If not configured, UUID will be generated based on the local MAC address.
#uuid=12345678-9abc-def0-1234-56789abcdef0

# Note: If wpa_psk_file is set, WPS is used to generate random, per-device PSKs
# that will be appended to the wpa_psk_file. If wpa_psk_file is not set, the
# default PSK (wpa_psk/wpa_passphrase) will be delivered to Enrollees. Use of
# per-device PSKs is recommended as the more secure option (i.e., make sure to
# set wpa_psk_file when using WPS with WPA-PSK).

# When an Enrollee requests access to the network with PIN method, the Enrollee
# PIN will need to be entered for the Registrar. PIN request notifications are
# sent to hostapd ctrl_iface monitor. In addition, they can be written to a
# text file that could be used, e.g., to populate the AP administration UI with
# pending PIN requests. If the following variable is set, the PIN requests will
# be written to the configured file.
#wps_pin_requests=/var/run/hostapd_wps_pin_requests

# Device Name
# User-friendly description of device; up to 32 octets encoded in UTF-8
#device_name=Wireless AP

# Manufacturer
# The manufacturer of the device (up to 64 ASCII characters)
#manufacturer=Company

# Model Name
# Model of the device (up to 32 ASCII characters)
#model_name=WAP

# Model Number
# Additional device description (up to 32 ASCII characters)
#model_number=123

# Serial Number
# Serial number of the device (up to 32 characters)
#serial_number=12345

# Primary Device Type
# Used format: <categ>-<OUI>-<subcateg>
# categ = Category as an integer value
# OUI = OUI and type octet as a 4-octet hex-encoded value; 0050F204 for
#       default WPS OUI
# subcateg = OUI-specific Sub Category as an integer value
# Examples:
#   1-0050F204-1 (Computer / PC)
#   1-0050F204-2 (Computer / Server)
#   5-0050F204-1 (Storage / NAS)
#   6-0050F204-1 (Network Infrastructure / AP)
#device_type=6-0050F204-1

# OS Version
# 4-octet operating system version number (hex string)
#os_version=01020300

# Config Methods
# List of the supported configuration methods
#config_methods=label display push_button keypad

# Access point PIN for initial configuration and adding Registrars
# If not set, hostapd will not allow external WPS Registrars to control the
# access point.
#ap_pin=12345670

# Skip building of automatic WPS credential
# This can be used to allow the automatically generated Credential attribute to
# be replaced with pre-configured Credential(s).
#skip_cred_build=1

# Additional Credential attribute(s)
# This option can be used to add pre-configured Credential attributes into M8
# message when acting as a Registrar. If skip_cred_build=1, this data will also
# be able to override the Credential attribute that would have otherwise been
# automatically generated based on network configuration. This configuration
# option points to an external file that much contain the WPS Credential
# attribute(s) as binary data.
#extra_cred=hostapd.cred

# Credential processing
#   0 = process received credentials internally (default)
#   1 = do not process received credentials; just pass them over ctrl_iface to
#    external program(s)
#   2 = process received credentials internally and pass them over ctrl_iface
#    to external program(s)
# Note: With wps_cred_processing=1, skip_cred_build should be set to 1 and
# extra_cred be used to provide the Credential data for Enrollees.
#
# wps_cred_processing=1 will disabled automatic updates of hostapd.conf file
# both for Credential processing and for marking AP Setup Locked based on
# validation failures of AP PIN. An external program is responsible on updating
# the configuration appropriately in this case.
#wps_cred_processing=0

# AP Settings Attributes for M7
# By default, hostapd generates the AP Settings Attributes for M7 based on the
# current configuration. It is possible to override this by providing a file
# with pre-configured attributes. This is similar to extra_cred file format,
# but the AP Settings attributes are not encapsulated in a Credential
# attribute.
#ap_settings=hostapd.ap_settings

# WPS UPnP interface
# If set, support for external Registrars is enabled.
#upnp_iface=br0

# Friendly Name (required for UPnP)
# Short description for end use. Should be less than 64 characters.
#friendly_name=WPS Access Point

# Manufacturer URL (optional for UPnP)
#manufacturer_url=http://www.example.com/

# Model Description (recommended for UPnP)
# Long description for end user. Should be less than 128 characters.
#model_description=Wireless Access Point

# Model URL (optional for UPnP)
#model_url=http://www.example.com/model/

# Universal Product Code (optional for UPnP)
# 12-digit, all-numeric code that identifies the consumer package.
#upc=123456789012

##### Multiple BSSID support ##################################################
#
# Above configuration is using the default interface (wlan#, or multi-SSID VLAN
# interfaces). Other BSSIDs can be added by using separator 'bss' with
# default interface name to be allocated for the data packets of the new BSS.
#
# hostapd will generate BSSID mask based on the BSSIDs that are
# configured. hostapd will verify that dev_addr & MASK == dev_addr. If this is
# not the case, the MAC address of the radio must be changed before starting
# hostapd (ifconfig wlan0 hw ether <MAC addr>).
#
# BSSIDs are assigned in order to each BSS, unless an explicit BSSID is
# specified using the 'bssid' parameter.
# If an explicit BSSID is specified, it must be chosen such that it:
# - results in a valid MASK that covers it and the dev_addr
# - is not the same as the MAC address of the radio
# - is not the same as any other explicitly specified BSSID
#
# Please note that hostapd uses some of the values configured for the first BSS
# as the defaults for the following BSSes. However, it is recommended that all
# BSSes include explicit configuration of all relevant configuration items.
#
#bss=wlan0_0
#ssid=test2
# most of the above items can be used here (apart from radio interface specific
# items, like channel)

#bss=wlan0_1
#bssid=00:13:10:95:fe:0b
# ...
```dnsmasq.conf
```
# Configuration file for dnsmasq.
#
# Format is one option per line, legal options are the same
# as the long options legal on the command line. See
# "/usr/sbin/dnsmasq --help" or "man 8 dnsmasq" for details.

# The following two options make you a better netizen, since they
# tell dnsmasq to filter out queries which the public DNS cannot
# answer, and which load the servers (especially the root servers)
# uneccessarily. If you have a dial-on-demand link they also stop
# these requests from bringing up the link uneccessarily.

# Never forward plain names (without a dot or domain part)
#domain-needed
# Never forward addresses in the non-routed address spaces.
#bogus-priv


# Uncomment this to filter useless windows-originated DNS requests
# which can trigger dial-on-demand links needlessly.
# Note that (amongst other things) this blocks all SRV requests,
# so don't use it if you use eg Kerberos, SIP, XMMP or Google-talk.
# This option only affects forwarding, SRV records originating for
# dnsmasq (via srv-host= lines) are not suppressed by it.
#filterwin2k

# Change this line if you want dns to get its upstream servers from
# somewhere other that /etc/resolv.conf
#resolv-file=

# By  default,  dnsmasq  will  send queries to any of the upstream
# servers it knows about and tries to favour servers to are  known
# to  be  up.  Uncommenting this forces dnsmasq to try each query
# with  each  server  strictly  in  the  order  they   appear   in
# /etc/resolv.conf
#strict-order

# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
#no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
#no-poll

# Add other name servers here, with domain specs if they are for
# non-public domains.
#server=/localnet/192.168.0.1

# Example of routing PTR queries to nameservers: this will send all 
# address->name queries for 192.168.3/24 to nameserver 10.1.2.3
#server=/3.168.192.in-addr.arpa/10.1.2.3

# Add local-only domains here, queries in these domains are answered
# from /etc/hosts or DHCP only.
#local=/localnet/

# Add domains which you want to force to an IP address here.
# The example below send any host in doubleclick.net to a local
# webserver.
#address=/doubleclick.net/127.0.0.1

# --address (and --server) work with IPv6 addresses too.
#address=/www.thekelleys.org.uk/fe80::20d:60ff:fe36:f83

# You can control how dnsmasq talks to a server: this forces 
# queries to 10.1.2.3 to be routed via eth1
# --server=10.1.2.3@eth1

# and this sets the source (ie local) address used to talk to
# 10.1.2.3 to 192.168.1.1 port 55 (there must be a interface with that
# IP on the machine, obviously).
# --server=10.1.2.3@192.168.1.1#55

# If you want dnsmasq to change uid and gid to something other
# than the default, edit the following lines.
#user=
#group=

# If you want dnsmasq to listen for DHCP and DNS requests only on
# specified interfaces (and the loopback) give the name of the
# interface (eg eth0) here.
# Repeat the line for more than one interface.
#interface=
# Or you can specify which interface _not_ to listen on
#except-interface=
# Or which to listen on by address (remember to include 127.0.0.1 if
# you use this.)
#listen-address=
# If you want dnsmasq to provide only DNS service on an interface,
# configure it as shown above, and then use the following line to
# disable DHCP on it.
#no-dhcp-interface=

# On systems which support it, dnsmasq binds the wildcard address,
# even when it is listening on only some interfaces. It then discards
# requests that it shouldn't reply to. This has the advantage of
# working even when interfaces come and go and change address. If you
# want dnsmasq to really bind only the interfaces it is listening on,
# uncomment this option. About the only time you may need this is when
# running another nameserver on the same machine.
#bind-interfaces

# If you don't want dnsmasq to read /etc/hosts, uncomment the
# following line.
#no-hosts
# or if you want it to read another file, as well as /etc/hosts, use
# this.
#addn-hosts=/etc/banner_add_hosts

# Set this (and domain: see below) if you want to have a domain
# automatically added to simple names in a hosts-file.
#expand-hosts

# Set the domain for dnsmasq. this is optional, but if it is set, it
# does the following things.
# 1) Allows DHCP hosts to have fully qualified domain names, as long
#     as the domain part matches this setting.
# 2) Sets the "domain" DHCP option thereby potentially setting the
#    domain of all systems configured by DHCP
# 3) Provides the domain part for "expand-hosts"
#domain=thekelleys.org.uk

# Set a different domain for a particular subnet
#domain=wireless.thekelleys.org.uk,192.168.2.0/24

# Same idea, but range rather then subnet
#domain=reserved.thekelleys.org.uk,192.68.3.100,192.168.3.200

# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
#dhcp-range=192.168.0.50,192.168.0.150,12h

# This is an example of a DHCP range where the netmask is given. This
# is needed for networks we reach the dnsmasq DHCP server via a relay
# agent. If you don't know what a DHCP relay agent is, you probably
# don't need to worry about this.
#dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h

# This is an example of a DHCP range with a network-id, so that
# some DHCP options may be set only for this network.
#dhcp-range=red,192.168.0.50,192.168.0.150

# Supply parameters for specified hosts using DHCP. There are lots
# of valid alternatives, so we will give examples of each. Note that
# IP addresses DO NOT have to be in the range given above, they just
# need to be on the same network. The order of the parameters in these
# do not matter, it's permissble to give name,adddress and MAC in any order

# Always allocate the host with ethernet address 11:22:33:44:55:66
# The IP address 192.168.0.60
#dhcp-host=11:22:33:44:55:66,192.168.0.60

# Always set the name of the host with hardware address
# 11:22:33:44:55:66 to be "fred"
#dhcp-host=11:22:33:44:55:66,fred

# Always give the host with ethernet address 11:22:33:44:55:66
# the name fred and IP address 192.168.0.60 and lease time 45 minutes
#dhcp-host=11:22:33:44:55:66,fred,192.168.0.60,45m

# Give a host with ethernet address 11:22:33:44:55:66 or
# 12:34:56:78:90:12 the IP address 192.168.0.60. Dnsmasq will assume
# that these two ethernet interfaces will never be in use at the same
# time, and give the IP address to the second, even if it is already
# in use by the first. Useful for laptops with wired and wireless
# addresses.
#dhcp-host=11:22:33:44:55:66,12:34:56:78:90:12,192.168.0.60

# Give the machine which says its name is "bert" IP address
# 192.168.0.70 and an infinite lease
#dhcp-host=bert,192.168.0.70,infinite

# Always give the host with client identifier 01:02:02:04
# the IP address 192.168.0.60
#dhcp-host=id:01:02:02:04,192.168.0.60

# Always give the host with client identifier "marjorie"
# the IP address 192.168.0.60
#dhcp-host=id:marjorie,192.168.0.60

# Enable the address given for "judge" in /etc/hosts
# to be given to a machine presenting the name "judge" when
# it asks for a DHCP lease.
#dhcp-host=judge

# Never offer DHCP service to a machine whose ethernet
# address is 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,ignore

# Ignore any client-id presented by the machine with ethernet
# address 11:22:33:44:55:66. This is useful to prevent a machine
# being treated differently when running under different OS's or
# between PXE boot and OS boot.
#dhcp-host=11:22:33:44:55:66,id:*

# Send extra options which are tagged as "red" to
# the machine with ethernet address 11:22:33:44:55:66
#dhcp-host=11:22:33:44:55:66,net:red

# Send extra options which are tagged as "red" to
# any machine with ethernet address starting 11:22:33:
#dhcp-host=11:22:33:*:*:*,net:red

# Ignore any clients which are specified in dhcp-host lines
# or /etc/ethers. Equivalent to ISC "deny unkown-clients".
# This relies on the special "known" tag which is set when 
# a host is matched.
#dhcp-ignore=#known

# Send extra options which are tagged as "red" to any machine whose
# DHCP vendorclass string includes the substring "Linux"
#dhcp-vendorclass=red,Linux

# Send extra options which are tagged as "red" to any machine one
# of whose DHCP userclass strings includes the substring "accounts"
#dhcp-userclass=red,accounts

# Send extra options which are tagged as "red" to any machine whose
# MAC address matches the pattern.
#dhcp-mac=red,00:60:8C:*:*:*

# If this line is uncommented, dnsmasq will read /etc/ethers and act
# on the ethernet-address/IP pairs found there just as if they had
# been given as --dhcp-host options. Useful if you keep
# MAC-address/host mappings there for other purposes.
#read-ethers

# Send options to hosts which ask for a DHCP lease.
# See RFC 2132 for details of available options.
# Common options can be given to dnsmasq by name: 
# run "dnsmasq --help dhcp" to get a list.
# Note that all the common settings, such as netmask and
# broadcast address, DNS server and default route, are given
# sane defaults by dnsmasq. You very likely will not need 
# any dhcp-options. If you use Windows clients and Samba, there
# are some options which are recommended, they are detailed at the
# end of this section.

# Override the default route supplied by dnsmasq, which assumes the
# router is the same machine as the one running dnsmasq.
#dhcp-option=3,1.2.3.4

# Do the same thing, but using the option name
#dhcp-option=option:router,1.2.3.4

# Override the default route supplied by dnsmasq and send no default
# route at all. Note that this only works for the options sent by
# default (1, 3, 6, 12, 28) the same line will send a zero-length option 
# for all other option numbers.
#dhcp-option=3

# Set the NTP time server addresses to 192.168.0.4 and 10.10.0.5
#dhcp-option=option:ntp-server,192.168.0.4,10.10.0.5

# Set the NTP time server address to be the same machine as
# is running dnsmasq
#dhcp-option=42,0.0.0.0

# Set the NIS domain name to "welly"
#dhcp-option=40,welly

# Set the default time-to-live to 50
#dhcp-option=23,50

# Set the "all subnets are local" flag
#dhcp-option=27,1

# Send the etherboot magic flag and then etherboot options (a string).
#dhcp-option=128,e4:45:74:68:00:00
#dhcp-option=129,NIC=eepro100

# Specify an option which will only be sent to the "red" network
# (see dhcp-range for the declaration of the "red" network)
# Note that the net: part must precede the option: part.
#dhcp-option = net:red, option:ntp-server, 192.168.1.1

# The following DHCP options set up dnsmasq in the same way as is specified
# for the ISC dhcpcd in
# http://www.samba.org/samba/ftp/docs/textdocs/DHCP-Server-Configuration.txt
# adapted for a typical dnsmasq installation where the host running
# dnsmasq is also the host running samba.
# you may want to uncomment some or all of them if you use 
# Windows clients and Samba.
#dhcp-option=19,0           # option ip-forwarding off
#dhcp-option=44,0.0.0.0     # set netbios-over-TCP/IP nameserver(s) aka WINS server(s)
#dhcp-option=45,0.0.0.0     # netbios datagram distribution server
#dhcp-option=46,8           # netbios node type

# Send RFC-3397 DNS domain search DHCP option. WARNING: Your DHCP client
# probably doesn't support this......
#dhcp-option=option:domain-search,eng.apple.com,marketing.apple.com

# Send RFC-3442 classless static routes (note the netmask encoding)
#dhcp-option=121,192.168.1.0/24,1.2.3.4,10.0.0.0/8,5.6.7.8

# Send vendor-class specific options encapsulated in DHCP option 43. 
# The meaning of the options is defined by the vendor-class so
# options are sent only when the client supplied vendor class
# matches the class given here. (A substring match is OK, so "MSFT" 
# matches "MSFT" and "MSFT 5.0"). This example sets the
# mtftp address to 0.0.0.0 for PXEClients.
#dhcp-option=vendor:PXEClient,1,0.0.0.0

# Send microsoft-specific option to tell windows to release the DHCP lease
# when it shuts down. Note the "i" flag, to tell dnsmasq to send the
# value as a four-byte integer - that's what microsoft wants. See
# http://technet2.microsoft.com/WindowsServer/en/library/a70f1bb7-d2d4-49f0-96d6-4b7414ecfaae1033.mspx?mfr=true
#dhcp-option=vendor:MSFT,2,1i

# Send the Encapsulated-vendor-class ID needed by some configurations of
# Etherboot to allow is to recognise the DHCP server.
#dhcp-option=vendor:Etherboot,60,"Etherboot"

# Send options to PXELinux. Note that we need to send the options even
# though they don't appear in the parameter request list, so we need
# to use dhcp-option-force here. 
# See http://syslinux.zytor.com/pxe.php#special for details.
# Magic number - needed before anything else is recognised
#dhcp-option-force=208,f1:00:74:7e
# Configuration file name
#dhcp-option-force=209,configs/common
# Path prefix
#dhcp-option-force=210,/tftpboot/pxelinux/files/
# Reboot time. (Note 'i' to send 32-bit value)
#dhcp-option-force=211,30i

# Set the boot filename for netboot/PXE. You will only need 
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
#dhcp-boot=pxelinux.0

# Boot for Etherboot gPXE. The idea is to send two different
# filenames, the first loads gPXE, and the second tells gPXE what to
# load. The dhcp-match sets the gpxe tag for requests from gPXE.
#dhcp-match=gpxe,175 # gPXE sends a 175 option.
#dhcp-boot=net:#gpxe,undionly.kpxe
#dhcp-boot=mybootimage
 
# Encapsulated options for Etherboot gPXE. All the options are
# encapsulated within option 175
#dhcp-option=encap:175, 1, 5b         # priority code
#dhcp-option=encap:175, 176, 1b       # no-proxydhcp 
#dhcp-option=encap:175, 177, string   # bus-id 
#dhcp-option=encap:175, 189, 1b       # BIOS drive code
#dhcp-option=encap:175, 190, user     # iSCSI username
#dhcp-option=encap:175, 191, pass     # iSCSI password

# Test for the architecture of a netboot client. PXE clients are
# supposed to send their architecture as option 93. (See RFC 4578)
#dhcp-match=peecees, option:client-arch, 0 #x86-32
#dhcp-match=itanics, option:client-arch, 2 #IA64
#dhcp-match=hammers, option:client-arch, 6 #x86-64
#dhcp-match=mactels, option:client-arch, 7 #EFI x86-64 

# Do real PXE, rather than just booting a single file, this is an
# alternative to dhcp-boot.
#pxe-prompt="What system shall I netboot?"
# or with timeout before first available action is taken:
#pxe-prompt="Press F8 for menu.", 60

# Available boot services. for PXE.
#pxe-service=x86PC, "Boot from local disk"

# Loads <tftp-root>/pxelinux.0 from dnsmasq TFTP server.
#pxe-service=x86PC, "Install Linux", pxelinux 

# Loads <tftp-root>/pxelinux.0 from TFTP server at 1.2.3.4.
# Beware this fails on old PXE ROMS.
#pxe-service=x86PC, "Install Linux", pxelinux, 1.2.3.4 

# Use bootserver on network, found my multicast or broadcast.
#pxe-service=x86PC, "Install windows from RIS server", 1

# Use bootserver at a known IP address.
#pxe-service=x86PC, "Install windows from RIS server", 1, 1.2.3.4

# If you have multicast-FTP available,
# information for that can be passed in a similar way using options 1
# to 5. See page 19 of
# http://download.intel.com/design/archives/wfm/downloads/pxespec.pdf  

  
# Enable dnsmasq's built-in TFTP server
#enable-tftp

# Set the root directory for files availble via FTP.
#tftp-root=/var/ftpd

# Make the TFTP server more secure: with this set, only files owned by
# the user dnsmasq is running as will be send over the net.
#tftp-secure

# This option stops dnsmasq from negotiating a larger blocksize for TFTP 
# transfers. It will slow things down, but may rescue some broken TFTP
# clients.
#tftp-no-blocksize

# Set the boot file name only when the "red" tag is set.
#dhcp-boot=net:red,pxelinux.red-net

# An example of dhcp-boot with an external TFTP server: the name and IP
# address of the server are given after the filename.
# Can fail with old PXE ROMS. Overridden by --pxe-service.
#dhcp-boot=/var/ftpd/pxelinux.0,boothost,192.168.0.3

# Set the limit on DHCP leases, the default is 150
#dhcp-lease-max=150

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slighest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# http://www.isc.org/index.pl?/sw/dhcp/authoritative.php
#dhcp-authoritative

# Run an executable when a DHCP lease is created or destroyed.
# The arguments sent to the script are "add" or "del", 
# then the MAC address, the IP address and finally the hostname
# if there is one. 
#dhcp-script=/bin/echo

# Set the cachesize here.
#cache-size=150

# If you want to disable negative caching, uncomment this.
#no-negcache

# Normally responses which come form /etc/hosts and the DHCP lease
# file have Time-To-Live set as zero, which conventionally means
# do not cache further. If you are happy to trade lower load on the
# server for potentially stale date, you can set a time-to-live (in
# seconds) here.
#local-ttl=

# If you want dnsmasq to detect attempts by Verisign to send queries
# to unregistered .com and .net hosts to its sitefinder service and
# have dnsmasq instead return the correct NXDOMAIN response, uncomment
# this line. You can add similar lines to do the same for other
# registries which have implemented wildcard A records.
#bogus-nxdomain=64.94.110.11

# If you want to fix up DNS results from upstream servers, use the
# alias option. This only works for IPv4.
# This alias makes a result of 1.2.3.4 appear as 5.6.7.8
#alias=1.2.3.4,5.6.7.8
# and this maps 1.2.3.x to 5.6.7.x
#alias=1.2.3.0,5.6.7.0,255.255.255.0
# and this maps 192.168.0.10->192.168.0.40 to 10.0.0.10->10.0.0.40
#alias=192.168.0.10-192.168.0.40,10.0.0.0,255.255.255.0

# Change these lines if you want dnsmasq to serve MX records.

# Return an MX record named "maildomain.com" with target
# servermachine.com and preference 50
#mx-host=maildomain.com,servermachine.com,50

# Set the default target for MX records created using the localmx option.
#mx-target=servermachine.com

# Return an MX record pointing to the mx-target for all local
# machines.
#localmx

# Return an MX record pointing to itself for all local machines.
#selfmx

# Change the following lines if you want dnsmasq to serve SRV
# records.  These are useful if you want to serve ldap requests for
# Active Directory and other windows-originated DNS requests.
# See RFC 2782.
# You may add multiple srv-host lines.
# The fields are <name>,<target>,<port>,<priority>,<weight>
# If the domain part if missing from the name (so that is just has the
# service and protocol sections) then the domain given by the domain=
# config option is used. (Note that expand-hosts does not need to be
# set for this to work.)

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389

# A SRV record sending LDAP for the example.com domain to
# ldapserver.example.com port 289 (using domain=)
#domain=example.com
#srv-host=_ldap._tcp,ldapserver.example.com,389

# Two SRV records for LDAP, each with different priorities
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,1
#srv-host=_ldap._tcp.example.com,ldapserver.example.com,389,2

# A SRV record indicating that there is no LDAP server for the domain
# example.com
#srv-host=_ldap._tcp.example.com

# The following line shows how to make dnsmasq serve an arbitrary PTR
# record. This is useful for DNS-SD. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for PTR records.)
#ptr-record=_http._tcp.dns-sd-services,"New Employee Page._http._tcp.dns-sd-services"

# Change the following lines to enable dnsmasq to serve TXT records.
# These are used for things like SPF and zeroconf. (Note that the
# domain-name expansion done for SRV records _does_not
# occur for TXT records.)

#Example SPF.
#txt-record=example.com,"v=spf1 a -all"

#Example zeroconf
#txt-record=_http._tcp.example.com,name=value,paper=A4

# Provide an alias for a "local" DNS name. Note that this _only_ works
# for targets which are names from DHCP or /etc/hosts. Give host
# "bert" another name, bertrand
#cname=bertand,bert

# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
#log-queries

# Log lots of extra information about DHCP transactions.
#log-dhcp

# Include a another lot of configuration options.
#conf-file=/etc/dnsmasq.more.conf
#conf-dir=/etc/dnsmasq.d

interface=wlan0
dhcp-range=net:wlan0,192.168.8.10,192.168.8.50,255.255.255.0,1440m
dhcp-option=wlan0,3,192.168.8.1
dhcp-option=wlan0,6,208.67.222.222,208.67.220.220
```ap_ctl
```
#!/bin/bash

# broadcasting interface
BROADCAST="wlan0"

# receiving interface broadcast is connected to
RECEIVE="ra0"

if [[ $1 == "-0" || $1 == "--start" ]]
 then
 ## start hostapd
 echo "Starting hostapd"
 echo "    You can view the log at /var/log/hostapd.log"

 # launch hostapd daemon
 hostapd -d /etc/hostapd/hostapd.conf > /var/log/hostapd.log &

 ## start dhcp server
 echo "Starting dnsmasq"

 # set IP address
 ifconfig $BROADCAST 192.168.8.2
 sleep 2

 # launch dhcpd3 daemon
 # echo "INTERFACES=$BROADCAST" > /etc/default/dhcp
 # dhcpd3 $BROADCAST &
 dnsmasq

elif [[ $1 == "-1" || $1 == "--stop" ]]
 then
 # send signal 2 to hostapd and dhcpd3/dnsmasq
 killall -2 hostapd dnsmasq

elif [[ $1 == "-2" || $1 == "--ics" ]]
 then
 # create iptables rules
 iptables -A FORWARD -i $RECEIVE -o $BROADCAST -s 192.168.8.2/24 -m conntrack --ctstate NEW -j ACCEPT
 iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
 iptables -A POSTROUTING -t nat -j MASQUERADE

 # set kernel variable(s)
 echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

 # edit kernel configuration
 cp /etc/sysctl.conf /etc/sysctl.conf.ap_ctl
 echo "net.ipv4.conf.default.forwarding=1" >> /etc/sysctl.conf
 echo "net.ipv4.conf.all.forwarding=1" >> /etc/sysctl.conf

 # restart networking
 /etc/init.d/networking restart

elif [[ $1 == "-3" || $1 == "--noics" ]]
 then
 # remove iptables rules
 iptables -D FORWARD 1
 iptables -D FORWARD 1

 # set kernel variable(s)
 echo 0 > /proc/sys/net/ipv4/conf/all/forwarding

 # revert kernel configuration
 mv -i /etc/sysctl.conf.ap_ctl /etc/sysctl.conf

 # restart networking
 /etc/init.d/networking restart

else
 echo $0
 echo "A tool to manage hostapd and dhcpd3/dnsmasq"
 echo "Usage:"
 echo "    -0 --start    Start hostapd and dhcpd3"
 echo "    -1 --stop    Stop hostapd and dhcpd3/dnsmasq with signal 2"
 echo "    -2 --ics    Activate internet connection sharing"
 echo "            between specified interfaces"
 echo "    -3 --noics    Undo internet connection sharing settings"
fi

exit 0
```rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ap_ctl --start
ap_ctl --ics
exit 0
```I'm really stumped, because, everything seems to be working OK on the Netbook, as far as running the script(s) and setting up the "hotspot," but I just can't get the Internet to be accessible via the iPhone (which is the only testing device I have, unfortunately). Help would be greatly appreciated!!

---

### Post by wildmanne39 on 2012-07-31
*Thread moved to **Networking & Wireless**.*

---

### Post by ctownstud00 on 2012-07-31
> **wildmanne39 said:**
> *Thread moved to **Networking & Wireless**.*

Thank you.

---

### Post by ctownstud00 on 2012-08-01
I updated my USB wireless driver and now I am having some new issues.

When I boot Ubuntu, it used to be that the internal wireless card would not show up in Network Manager, and, respectively, it wouldn't try to connect to other wireless APs. Now, when I boot, it is showing up in Network Manager, and trying to connect to the "nearest" or "best" or whatever random wireless AP that I'm near. Also, I am having trouble connecting with my iPhone, and one time, it did connect, but assigned a funky IP that I didn't think was in my DHCP range.

What changed was the names of the wireless connections, when I installed the new driver. The USB wireless card was called "wlan0," and now, it's called "ra0." The internal wireless card (the one that is now acting differently) was called "wlan1_rename," and now, it's called "wlan1." I changed the names in the respective configuration files of hostapd, dnsmasq, and ap_ctl, but it's not even letting me connect to the hotspot now! Someone freakin' help me!!

---

### Post by ctownstud00 on 2012-08-01
Now, it seems like the DNSMasq is assigning proper IPs again, but I still have no Internet connectivity. I also tried changing the DNS to 192.168.8.1, similar to what I see when I connect to a normal router, but that didn't work, either. I really need some guidance here!

---

### Post by ctownstud00 on 2012-08-02
Trouble was in hostapd.conf. I had to change the Broadcast IP to 192.168.8.1. Solved. Please close!

---


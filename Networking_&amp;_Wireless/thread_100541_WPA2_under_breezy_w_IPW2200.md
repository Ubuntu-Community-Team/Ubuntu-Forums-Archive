---
title: "WPA2 under breezy w/ IPW2200"
date: 2005-12-07
forum: Networking &amp; Wireless
---

### Post by robfindlay on 2005-12-07
Is WPA2 even supported?   

All the guides i'm finding are for WPA. 


Tkns...


EDIT: I shouldn't have to install the "ieee80211" under breezy?  I thought they were a part of the IPW2200 drivers.....

---

### Post by Lambert on 2005-12-07
Used with wpa supplicant it should support wpa2

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

### Post by robfindlay on 2005-12-07
[QUOTE=Lambert]Used with wpa supplicant it should support wpa2

[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)[/QUOTE]


Even with an ipw2200 ??    I can't for the life of me get it to work....

I'll post my .conf file when i get home in a bit.

---

### Post by Lambert on 2005-12-07
Maybe look here for help but note it looks like it's written for hoary so you may not need to compile anything, just the confi part.

[http://doc.gwos.org/index.php/Ipw2200_wpa](http://doc.gwos.org/index.php/Ipw2200_wpa)

---

### Post by robfindlay on 2005-12-08
[QUOTE=Lambert]Maybe look here for help but note it looks like it's written for hoary so you may not need to compile anything, just the confi part.

[http://doc.gwos.org/index.php/Ipw2200_wpa](http://doc.gwos.org/index.php/Ipw2200_wpa)[/QUOTE]

Man i am at my wits end with this.  


my linksys (WRT54G) is setup: 

sec mode: WPA2 Personal 
WPA algorithims: TKIP+AES
WPA Shared Key: satan6900
group key renewal: 36000

My conf file:
 ##### Example wpa_supplicant configuration file ###############################
# Empty lines and lines starting with # are ignored

# NOTE! This file may contain password information and should probably be made
# readable only by root user on multiuser systems.

# Whether to allow wpa_supplicant to update (overwrite) configuration
#
# This option can be used to allow wpa_supplicant to overwrite configuration
# file whenever configuration is changed (e.g., new network block is added with
# wpa_cli or wpa_gui, or a password is changed). This is required for
# wpa_cli/wpa_gui to be able to store the configuration changes permanently.
# Please note that overwriting configuration file will remove the comments from
# it.
#update_config=1

# global configuration (shared by all network blocks)
#
# Interface for separate control program. If this is specified, wpa_supplicant
# will create this directory and a UNIX domain socket for listening to requests
# from external programs (CLI/GUI, etc.) for status information and
# configuration. The socket file will be named based on the interface name, so
# multiple wpa_supplicant processes can be run at the same time if more than
# one interface is used.
# /var/run/wpa_supplicant is the recommended directory for sockets and by
# default, wpa_cli will use it when trying to connect with wpa_supplicant.
#ctrl_interface=/var/run/wpa_supplicant

# Access control for the control interface can be configured by setting the
# directory to allow only members of a group to use sockets. This way, it is
# possible to run wpa_supplicant as root (since it needs to change network
# configuration and open raw sockets) and still allow GUI/CLI components to be
# run as non-root users. However, since the control interface can be used to
# change the network configuration, this access needs to be protected in many
# cases. By default, wpa_supplicant is configured to use gid 0 (root). If you
# want to allow non-root users to use the control interface, add a new group
# and change this value to match with that group. Add users that should have
# control interface access to this group. If this variable is commented out or
# not included in the configuration file, group will not be changed from the
# value it got by default when the directory or socket was created.
#
# This variable can be a group name or gid.
#ctrl_interface_group=wheel
ctrl_interface_group=0

# IEEE 802.1X/EAPOL version
# wpa_supplicant was implemented based on IEEE 802-1X-REV-d8 which defines
# EAPOL version 2. However, there are many APs that do not handle the new
# version number correctly (they seem to drop the frames completely). In order
# to make wpa_supplicant interoperate with these APs, the version number is set
# to 1 by default. This configuration value can be used to set it to the new
# version (2).
#eapol_version=1

# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode; do not try to associate with
#    APs (i.e., external program needs to control association). This mode must
#    also be used when using wired Ethernet drivers.
# 2: like 0, but associate with APs using security policy and SSID (but not
#    BSSID); this can be used, e.g., with ndiswrapper and NDIS drivers to
#    enable operation with hidden SSIDs and optimized roaming; in this mode,
#    the network blocks in the configuration file are tried one by one until
#    the driver reports successful association; each network block should have
#    explicit security policy (i.e., only one option in the lists) for
#    key_mgmt, pairwise, group, proto variables
#ap_scan=1

# EAP fast re-authentication
# By default, fast re-authentication is enabled for all EAP methods that
# support it. This variable can be used to disable fast re-authentication.
# Normally, there is no need to disable this.
fast_reauth=1

# OpenSSL Engine support
# These options can be used to load OpenSSL engines.
# The two engines that are supported currently are shown below:
# They are both from the opensc project ([http://www.opensc.org/](http://www.opensc.org/))
# By default no engines are loaded.
# make the opensc engine available
opensc_engine_path=/usr/lib/opensc/engine_opensc.so
# make the pkcs11 engine available
pkcs11_engine_path=/usr/lib/opensc/engine_pkcs11.so
# configure the path to the pkcs11 module required by the pkcs11 engine
pkcs11_module_path=/usr/lib/pkcs11/opensc-pkcs11.so

# Driver interface parameters
# This field can be used to configure arbitrary driver interace parameters. The
# format is specific to the selected driver interface. This field is not used
# in most cases.
#driver_param="field=value"

# Maximum lifetime for PMKSA in seconds; default 43200
#dot11RSNAConfigPMKLifetime=43200
# Threshold for reauthentication (percentage of PMK lifetime); default 70
#dot11RSNAConfigPMKReauthThreshold=70
# Timeout for security association negotiation in seconds; default 60
#dot11RSNAConfigSATimeout=60

# network block
#
# Each network (usually AP's sharing the same SSID) is configured as a separate
# block in this configuration file. The network blocks are in preference order
# (the first match is used).
#
# network block fields:
#
# disabled:
#	0 = this network can be used (default)
#	1 = this network block is disabled (can be enabled through ctrl_iface,
#	    e.g., with wpa_cli or wpa_gui)
#
# ssid: SSID (mandatory); either as an ASCII string with double quotation or
#	as hex string; network name
#
# scan_ssid:
#	0 = do not scan this SSID with specific Probe Request frames (default)
#	1 = scan with SSID-specific Probe Request frames (this can be used to
#	    find APs that do not accept broadcast SSID or use multiple SSIDs;
#	    this will add latency to scanning, so enable this only when needed)
#
# bssid: BSSID (optional); if set, this network block is used only when
#	associating with the AP using the configured BSSID
#
# priority: priority group (integer)
# By default, all networks will get same priority group (0). If some of the
# networks are more desirable, this field can be used to change the order in
# which wpa_supplicant goes through the networks when selecting a BSS. The
# priority groups will be iterated in decreasing priority (i.e., the larger the
# priority value, the sooner the network is matched against the scan results).
# Within each priority group, networks will be selected based on security
# policy, signal strength, etc.
# Please note that AP scanning with scan_ssid=1 and ap_scan=2 mode are not
# using this priority to select the order for scanning. Instead, they try the
# networks in the order that used in the configuration file.
#
# mode: IEEE 802.11 operation mode
# 0 = infrastructure (Managed) mode, i.e., associate with an AP (default)
# 1 = IBSS (ad-hoc, peer-to-peer)
# Note: IBSS can only be used with key_mgmt NONE (plaintext and static WEP)
# and key_mgmt=WPA-NONE (fixed group key TKIP/CCMP). In addition, ap_scan has
# to be set to 2 for IBSS. WPA-None requires following network block options:
# proto=WPA, key_mgmt=WPA-NONE, pairwise=NONE, group=TKIP (or CCMP, but not
# both), and psk must also be set.
#
# proto: list of accepted protocols
# WPA = WPA/IEEE 802.11i/D3.0
# RSN = WPA2/IEEE 802.11i (also WPA2 can be used as an alias for RSN)
# If not set, this defaults to: WPA RSN
#
# key_mgmt: list of accepted authenticated key management protocols
# WPA-PSK = WPA pre-shared key (this requires 'psk' field)
# WPA-EAP = WPA using EAP authentication (this can use an external
#	program, e.g., Xsupplicant, for IEEE 802.1X EAP Authentication
# IEEE8021X = IEEE 802.1X using EAP authentication and (optionally) dynamically
#	generated WEP keys
# NONE = WPA is not used; plaintext or static WEP could be used
# If not set, this defaults to: WPA-PSK WPA-EAP
#
# auth_alg: list of allowed IEEE 802.11 authentication algorithms
# OPEN = Open System authentication (required for WPA/WPA2)
# SHARED = Shared Key authentication (requires static WEP keys)
# LEAP = LEAP/Network EAP (only used with LEAP)
# If not set, automatic selection is used (Open System with LEAP enabled if
# LEAP is allowed as one of the EAP methods).
#
# pairwise: list of accepted pairwise (unicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# NONE = Use only Group Keys (deprecated, should not be included if APs support
#	pairwise keys)
# If not set, this defaults to: CCMP TKIP
#
# group: list of accepted group (broadcast/multicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# WEP104 = WEP (Wired Equivalent Privacy) with 104-bit key
# WEP40 = WEP (Wired Equivalent Privacy) with 40-bit key [IEEE 802.11]
# If not set, this defaults to: CCMP TKIP WEP104 WEP40
#
# psk: WPA preshared key; 256-bit pre-shared key
# The key used in WPA-PSK mode can be entered either as 64 hex-digits, i.e.,
# 32 bytes or as an ASCII passphrase (in which case, the real PSK will be
# generated using the passphrase and SSID). ASCII passphrase must be between
# 8 and 63 characters (inclusive).
# This field is not needed, if WPA-EAP is used.
# Note: Separate tool, wpa_passphrase, can be used to generate 256-bit keys
# from ASCII passphrase. This process uses lot of CPU and wpa_supplicant
# startup and reconfiguration time can be optimized by generating the PSK only
# only when the passphrase or SSID has actually changed.
#
# eapol_flags: IEEE 802.1X/EAPOL options (bit field)
# Dynamic WEP key required for non-WPA mode
# bit0 (1): require dynamically generated unicast WEP key
# bit1 (2): require dynamically generated broadcast WEP key
# 	(3 = require both keys; default)
# Note: When using wired authentication, eapol_flags must be set to 0 for the
# authentication to be completed successfully.
#
# proactive_key_caching:
# Enable/disable opportunistic PMKSA caching for WPA2.
# 0 = disabled (default)
# 1 = enabled
#
# Following fields are only used with internal EAP implementation.
# eap: space-separated list of accepted EAP methods
#	MD5 = EAP-MD5 (unsecure and does not generate keying material ->
#			cannot be used with WPA; to be used as a Phase 2 method
#			with EAP-PEAP or EAP-TTLS)
#       MSCHAPV2 = EAP-MSCHAPv2 (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       OTP = EAP-OTP (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       GTC = EAP-GTC (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#	TLS = EAP-TLS (client and server certificate)
#	PEAP = EAP-PEAP (with tunnelled EAP authentication)
#	TTLS = EAP-TTLS (with tunnelled EAP or PAP/CHAP/MSCHAP/MSCHAPV2
#			 authentication)
#	If not set, all compiled in methods are allowed.
#
# identity: Identity string for EAP
# anonymous_identity: Anonymous identity string for EAP (to be used as the
#	unencrypted identity with EAP types that support different tunnelled
#	identity, e.g., EAP-TTLS)
# password: Password string for EAP
# ca_cert: File path to CA certificate file (PEM/DER). This file can have one
#	or more trusted CA certificates. If ca_cert is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured when using EAP-TLS/TTLS/PEAP.
# client_cert: File path to client certificate file (PEM/DER)
# private_key: File path to client private key file (PEM/DER/PFX)
#	When PKCS#12/PFX file (.p12/.pfx) is used, client_cert should be
#	commented out. Both the private key and certificate will be read from
#	the PKCS#12 file in this case.
#	Windows certificate store can be used by leaving client_cert out and
#	configuring private_key in one of the following formats:
#	cert://substring_to_match
#	hash://certificate_thumbprint_in_hex
#	for example: private_key="hash://63093aa9c47f56ae88334c7b65a4"
# private_key_passwd: Password for private key file (if left out, this will be
#	asked through control interface)
# dh_file: File path to DH/DSA parameters file (in PEM format)
#	This is an optional configuration file for setting parameters for an
#	ephemeral DH key exchange. In most cases, the default RSA
#	authentication does not use this configuration. However, it is possible
#	setup RSA to use ephemeral DH key exchange. In addition, ciphers with
#	DSA keys always use ephemeral DH keys. This can be used to achieve
#	forward secrecy. If the file is in DSA parameters format, it will be
#	automatically converted into DH params.
# subject_match: Substring to be matched against the subject of the
#	authentication server certificate. If this string is set, the server
#	sertificate is only accepted if it contains this string in the subject.
#	The subject string is in following format:
#	/C=US/ST=CA/L=San Francisco/CN=Test AS/emailAddress=as@example.com
# altsubject_match: Substring to be matched against the alternative subject
#	name of the authentication server certificate. If this string is set,
#	the server sertificate is only accepted if it contains this string in
#	an alternative subject name extension.
#	altSubjectName string is in following format: TYPE:VALUE
#	Example: DNS:server.example.com
#	Following types are supported: EMAIL, DNS, URI
# phase1: Phase1 (outer authentication, i.e., TLS tunnel) parameters
#	(string with field-value pairs, e.g., "peapver=0" or
#	"peapver=1 peaplabel=1")
#	'peapver' can be used to force which PEAP version (0 or 1) is used.
#	'peaplabel=1' can be used to force new label, "client PEAP encryption",
#	to be used during key derivation when PEAPv1 or newer. Most existing
#	PEAPv1 implementation seem to be using the old label, "client EAP
#	encryption", and wpa_supplicant is now using that as the default value.
#	Some servers, e.g., Radiator, may require peaplabel=1 configuration to
#	interoperate with PEAPv1; see eap_testing.txt for more details.
#	'peap_outer_success=0' can be used to terminate PEAP authentication on
#	tunneled EAP-Success. This is required with some RADIUS servers that
#	implement draft-josefsson-pppext-eap-tls-eap-05.txt (e.g.,
#	Lucent NavisRadius v4.4.0 with PEAP in "IETF Draft 5" mode)
#	include_tls_length=1 can be used to force wpa_supplicant to include
#	TLS Message Length field in all TLS messages even if they are not
#	fragmented.
#	sim_min_num_chal=3 can be used to configure EAP-SIM to require three
#	challenges (by default, it accepts 2 or 3)
# phase2: Phase2 (inner authentication with TLS tunnel) parameters
#	(string with field-value pairs, e.g., "auth=MSCHAPV2" for EAP-PEAP or
#	"autheap=MSCHAPV2 autheap=MD5" for EAP-TTLS)
# Following certificate/private key fields are used in inner Phase2
# authentication when using EAP-TTLS or EAP-PEAP.
# ca_cert2: File path to CA certificate file. This file can have one or more
#	trusted CA certificates. If ca_cert2 is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured.
# client_cert2: File path to client certificate file
# private_key2: File path to client private key file
# private_key2_passwd: Password for private key file
# dh_file2: File path to DH/DSA parameters file (in PEM format)
# subject_match2: Substring to be matched against the subject of the
#	authentication server certificate.
# altsubject_match2: Substring to be matched against the alternative subject
#	name of the authentication server certificate.
#
# EAP-PSK variables:
# eappsk: 16-byte (128-bit, 32 hex digits) pre-shared key in hex format
# nai: user NAI
#
# EAP-FAST variables:
# pac_file: File path for the PAC entries. wpa_supplicant will need to be able
#	to create this file and write updates to it when PAC is being
#	provisioned or refreshed.
# phase1: fast_provisioning=1 option enables in-line provisioning of EAP-FAST
#	credentials (PAC)
#
# wpa_supplicant supports number of "EAP workarounds" to work around
# interoperability issues with incorrectly behaving authentication servers.
# These are enabled by default because some of the issues are present in large
# number of authentication servers. Strict EAP conformance mode can be
# configured by disabling workarounds with eap_workaround=0.

# Example blocks:

ctrl_interface=/var/run/wpa_supplicant

ap_scan=2

network={
	ssid="mothera"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=TKIP
	psk="satan6900"
}


When i execute the following command: sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd

I get the following: 
Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface_group=0
fast_reauth=1
opensc_engine_path='/usr/lib/opensc/engine_opensc.so'
pkcs11_engine_path='/usr/lib/opensc/engine_pkcs11.so'
pkcs11_module_path='/usr/lib/pkcs11/opensc-pkcs11.so'
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 330 - start of a new network block
ssid - hexdump_ascii(len=7):
     6d 6f 74 68 65 72 61                              mothera
scan_ssid=1 (0x1)
proto: 0x2
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 337: removed CCMP from group cipher list since it was not allowed for pairwise c ipher
Priority group 0
   id=0 ssid='mothera'
Daemonize..

 
And then nothing.  The Gnome network monitoring applet never looses the little red diamond and ps aux doesn't show the wpa supplicant running. 

I even followed the rest of the instructions on that link and created a startup script which gives me the same result. 


Help anyone?   If i can't get this working, at work, i'll have to to go back to winblows..... 


HELP!


Rob



EDIT: I shouldn't have to install the "ieee80211" under breezy? I thought they were a part of the IPW2200 drivers.....

---

### Post by jafenske on 2005-12-08
I think you may have to install the ieee80211... to make this work.  

Look at this

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by robfindlay on 2005-12-08
[QUOTE=jafenske]I think you may have to install the ieee80211... to make this work.  

Look at this

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)[/QUOTE]


Got the ieee installed and no joy.  I boot onto the desktop and my network monitor has that nifty yellow explaination point and red diamond.  So i go to a terminal and execute: 

sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D

And get: 

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface_group=0
eapol_version=1
fast_reauth=1
ctrl_interface='/var/run/wpa_supplicant'
ap_scan=2
Line: 330 - start of a new network block
ssid - hexdump_ascii(len=15):
     6d 6f 74 6f 5f 67 75 65 73 74 5f 77 70 61 32      moto_guest_wpa2
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=13): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='moto_guest_wpa2'
Daemonize..


wpa_supplicant is running but i whev i try to bring up the interface it never properly initiallizes. 


And then this command:  sudo wpa_supplicant -i eth1 -c/etc/wpa_supplicant.conf -D ipw

Gives me this: 
ioctl[SIOCSIWPMKSA]: Operation not supported
Trying to associate with SSID 'moto_guest_wpa2'
WPA: Failed to parse WPA IE from association info
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'moto_guest_wpa2'
WPA: Failed to parse WPA IE from association info
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with SSID 'moto_guest_wpa2'
WPA: Failed to parse WPA IE from association info
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys


Here is my current wpa_supplicant.conf 

##### Example wpa_supplicant configuration file ###############################
# Empty lines and lines starting with # are ignored

# NOTE! This file may contain password information and should probably be made
# readable only by root user on multiuser systems.

# Whether to allow wpa_supplicant to update (overwrite) configuration
#
# This option can be used to allow wpa_supplicant to overwrite configuration
# file whenever configuration is changed (e.g., new network block is added with
# wpa_cli or wpa_gui, or a password is changed). This is required for
# wpa_cli/wpa_gui to be able to store the configuration changes permanently.
# Please note that overwriting configuration file will remove the comments from
# it.
#update_config=1

# global configuration (shared by all network blocks)
#
# Interface for separate control program. If this is specified, wpa_supplicant
# will create this directory and a UNIX domain socket for listening to requests
# from external programs (CLI/GUI, etc.) for status information and
# configuration. The socket file will be named based on the interface name, so
# multiple wpa_supplicant processes can be run at the same time if more than
# one interface is used.
# /var/run/wpa_supplicant is the recommended directory for sockets and by
# default, wpa_cli will use it when trying to connect with wpa_supplicant.
#ctrl_interface=/var/run/wpa_supplicant

# Access control for the control interface can be configured by setting the
# directory to allow only members of a group to use sockets. This way, it is
# possible to run wpa_supplicant as root (since it needs to change network
# configuration and open raw sockets) and still allow GUI/CLI components to be
# run as non-root users. However, since the control interface can be used to
# change the network configuration, this access needs to be protected in many
# cases. By default, wpa_supplicant is configured to use gid 0 (root). If you
# want to allow non-root users to use the control interface, add a new group
# and change this value to match with that group. Add users that should have
# control interface access to this group. If this variable is commented out or
# not included in the configuration file, group will not be changed from the
# value it got by default when the directory or socket was created.
#
# This variable can be a group name or gid.
#ctrl_interface_group=wheel
ctrl_interface_group=0

# IEEE 802.1X/EAPOL version
# wpa_supplicant was implemented based on IEEE 802-1X-REV-d8 which defines
# EAPOL version 2. However, there are many APs that do not handle the new
# version number correctly (they seem to drop the frames completely). In order
# to make wpa_supplicant interoperate with these APs, the version number is set
# to 1 by default. This configuration value can be used to set it to the new
# version (2).
eapol_version=1

# AP scanning/selection
# By default, wpa_supplicant requests driver to perform AP scanning and then
# uses the scan results to select a suitable AP. Another alternative is to
# allow the driver to take care of AP scanning and selection and use
# wpa_supplicant just to process EAPOL frames based on IEEE 802.11 association
# information from the driver.
# 1: wpa_supplicant initiates scanning and AP selection
# 0: driver takes care of scanning, AP selection, and IEEE 802.11 association
#    parameters (e.g., WPA IE generation); this mode can also be used with
#    non-WPA drivers when using IEEE 802.1X mode; do not try to associate with
#    APs (i.e., external program needs to control association). This mode must
#    also be used when using wired Ethernet drivers.
# 2: like 0, but associate with APs using security policy and SSID (but not
#    BSSID); this can be used, e.g., with ndiswrapper and NDIS drivers to
#    enable operation with hidden SSIDs and optimized roaming; in this mode,
#    the network blocks in the configuration file are tried one by one until
#    the driver reports successful association; each network block should have
#    explicit security policy (i.e., only one option in the lists) for
#    key_mgmt, pairwise, group, proto variables
#ap_scan=1

# EAP fast re-authentication
# By default, fast re-authentication is enabled for all EAP methods that
# support it. This variable can be used to disable fast re-authentication.
# Normally, there is no need to disable this.
fast_reauth=1

# OpenSSL Engine support
# These options can be used to load OpenSSL engines.
# The two engines that are supported currently are shown below:
# They are both from the opensc project ([http://www.opensc.org/](http://www.opensc.org/))
# By default no engines are loaded.
# make the opensc engine available
#opensc_engine_path=/usr/lib/opensc/engine_opensc.so
# make the pkcs11 engine available
#pkcs11_engine_path=/usr/lib/opensc/engine_pkcs11.so
# configure the path to the pkcs11 module required by the pkcs11 engine
#pkcs11_module_path=/usr/lib/pkcs11/opensc-pkcs11.so

# Driver interface parameters
# This field can be used to configure arbitrary driver interace parameters. The
# format is specific to the selected driver interface. This field is not used
# in most cases.
#driver_param="field=value"

# Maximum lifetime for PMKSA in seconds; default 43200
#dot11RSNAConfigPMKLifetime=43200
# Threshold for reauthentication (percentage of PMK lifetime); default 70
#dot11RSNAConfigPMKReauthThreshold=70
# Timeout for security association negotiation in seconds; default 60
#dot11RSNAConfigSATimeout=60

# network block
#
# Each network (usually AP's sharing the same SSID) is configured as a separate
# block in this configuration file. The network blocks are in preference order
# (the first match is used).
#
# network block fields:
#
# disabled:
#	0 = this network can be used (default)
#	1 = this network block is disabled (can be enabled through ctrl_iface,
#	    e.g., with wpa_cli or wpa_gui)
#
# ssid: SSID (mandatory); either as an ASCII string with double quotation or
#	as hex string; network name
#
# scan_ssid:
#	0 = do not scan this SSID with specific Probe Request frames (default)
#	1 = scan with SSID-specific Probe Request frames (this can be used to
#	    find APs that do not accept broadcast SSID or use multiple SSIDs;
#	    this will add latency to scanning, so enable this only when needed)
#
# bssid: BSSID (optional); if set, this network block is used only when
#	associating with the AP using the configured BSSID
#
# priority: priority group (integer)
# By default, all networks will get same priority group (0). If some of the
# networks are more desirable, this field can be used to change the order in
# which wpa_supplicant goes through the networks when selecting a BSS. The
# priority groups will be iterated in decreasing priority (i.e., the larger the
# priority value, the sooner the network is matched against the scan results).
# Within each priority group, networks will be selected based on security
# policy, signal strength, etc.
# Please note that AP scanning with scan_ssid=1 and ap_scan=2 mode are not
# using this priority to select the order for scanning. Instead, they try the
# networks in the order that used in the configuration file.
#
# mode: IEEE 802.11 operation mode
# 0 = infrastructure (Managed) mode, i.e., associate with an AP (default)
# 1 = IBSS (ad-hoc, peer-to-peer)
# Note: IBSS can only be used with key_mgmt NONE (plaintext and static WEP)
# and key_mgmt=WPA-NONE (fixed group key TKIP/CCMP). In addition, ap_scan has
# to be set to 2 for IBSS. WPA-None requires following network block options:
# proto=WPA, key_mgmt=WPA-NONE, pairwise=NONE, group=TKIP (or CCMP, but not
# both), and psk must also be set.
#
# proto: list of accepted protocols
# WPA = WPA/IEEE 802.11i/D3.0
# RSN = WPA2/IEEE 802.11i (also WPA2 can be used as an alias for RSN)
# If not set, this defaults to: WPA RSN
#
# key_mgmt: list of accepted authenticated key management protocols
# WPA-PSK = WPA pre-shared key (this requires 'psk' field)
# WPA-EAP = WPA using EAP authentication (this can use an external
#	program, e.g., Xsupplicant, for IEEE 802.1X EAP Authentication
# IEEE8021X = IEEE 802.1X using EAP authentication and (optionally) dynamically
#	generated WEP keys
# NONE = WPA is not used; plaintext or static WEP could be used
# If not set, this defaults to: WPA-PSK WPA-EAP
#
# auth_alg: list of allowed IEEE 802.11 authentication algorithms
# OPEN = Open System authentication (required for WPA/WPA2)
# SHARED = Shared Key authentication (requires static WEP keys)
# LEAP = LEAP/Network EAP (only used with LEAP)
# If not set, automatic selection is used (Open System with LEAP enabled if
# LEAP is allowed as one of the EAP methods).
#
# pairwise: list of accepted pairwise (unicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# NONE = Use only Group Keys (deprecated, should not be included if APs support
#	pairwise keys)
# If not set, this defaults to: CCMP TKIP
#
# group: list of accepted group (broadcast/multicast) ciphers for WPA
# CCMP = AES in Counter mode with CBC-MAC [RFC 3610, IEEE 802.11i/D7.0]
# TKIP = Temporal Key Integrity Protocol [IEEE 802.11i/D7.0]
# WEP104 = WEP (Wired Equivalent Privacy) with 104-bit key
# WEP40 = WEP (Wired Equivalent Privacy) with 40-bit key [IEEE 802.11]
# If not set, this defaults to: CCMP TKIP WEP104 WEP40
#
# psk: WPA preshared key; 256-bit pre-shared key
# The key used in WPA-PSK mode can be entered either as 64 hex-digits, i.e.,
# 32 bytes or as an ASCII passphrase (in which case, the real PSK will be
# generated using the passphrase and SSID). ASCII passphrase must be between
# 8 and 63 characters (inclusive).
# This field is not needed, if WPA-EAP is used.
# Note: Separate tool, wpa_passphrase, can be used to generate 256-bit keys
# from ASCII passphrase. This process uses lot of CPU and wpa_supplicant
# startup and reconfiguration time can be optimized by generating the PSK only
# only when the passphrase or SSID has actually changed.
#
# eapol_flags: IEEE 802.1X/EAPOL options (bit field)
# Dynamic WEP key required for non-WPA mode
# bit0 (1): require dynamically generated unicast WEP key
# bit1 (2): require dynamically generated broadcast WEP key
# 	(3 = require both keys; default)
# Note: When using wired authentication, eapol_flags must be set to 0 for the
# authentication to be completed successfully.
#
# proactive_key_caching:
# Enable/disable opportunistic PMKSA caching for WPA2.
# 0 = disabled (default)
# 1 = enabled
#
# Following fields are only used with internal EAP implementation.
# eap: space-separated list of accepted EAP methods
#	MD5 = EAP-MD5 (unsecure and does not generate keying material ->
#			cannot be used with WPA; to be used as a Phase 2 method
#			with EAP-PEAP or EAP-TTLS)
#       MSCHAPV2 = EAP-MSCHAPv2 (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       OTP = EAP-OTP (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#       GTC = EAP-GTC (cannot be used separately with WPA; to be used
#		as a Phase 2 method with EAP-PEAP or EAP-TTLS)
#	TLS = EAP-TLS (client and server certificate)
#	PEAP = EAP-PEAP (with tunnelled EAP authentication)
#	TTLS = EAP-TTLS (with tunnelled EAP or PAP/CHAP/MSCHAP/MSCHAPV2
#			 authentication)
#	If not set, all compiled in methods are allowed.
#
# identity: Identity string for EAP
# anonymous_identity: Anonymous identity string for EAP (to be used as the
#	unencrypted identity with EAP types that support different tunnelled
#	identity, e.g., EAP-TTLS)
# password: Password string for EAP
# ca_cert: File path to CA certificate file (PEM/DER). This file can have one
#	or more trusted CA certificates. If ca_cert is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured when using EAP-TLS/TTLS/PEAP.
# client_cert: File path to client certificate file (PEM/DER)
# private_key: File path to client private key file (PEM/DER/PFX)
#	When PKCS#12/PFX file (.p12/.pfx) is used, client_cert should be
#	commented out. Both the private key and certificate will be read from
#	the PKCS#12 file in this case.
#	Windows certificate store can be used by leaving client_cert out and
#	configuring private_key in one of the following formats:
#	cert://substring_to_match
#	hash://certificate_thumbprint_in_hex
#	for example: private_key="hash://63093aa9c47f56ae88334c7b65a4"
# private_key_passwd: Password for private key file (if left out, this will be
#	asked through control interface)
# dh_file: File path to DH/DSA parameters file (in PEM format)
#	This is an optional configuration file for setting parameters for an
#	ephemeral DH key exchange. In most cases, the default RSA
#	authentication does not use this configuration. However, it is possible
#	setup RSA to use ephemeral DH key exchange. In addition, ciphers with
#	DSA keys always use ephemeral DH keys. This can be used to achieve
#	forward secrecy. If the file is in DSA parameters format, it will be
#	automatically converted into DH params.
# subject_match: Substring to be matched against the subject of the
#	authentication server certificate. If this string is set, the server
#	sertificate is only accepted if it contains this string in the subject.
#	The subject string is in following format:
#	/C=US/ST=CA/L=San Francisco/CN=Test AS/emailAddress=as@example.com
# altsubject_match: Substring to be matched against the alternative subject
#	name of the authentication server certificate. If this string is set,
#	the server sertificate is only accepted if it contains this string in
#	an alternative subject name extension.
#	altSubjectName string is in following format: TYPE:VALUE
#	Example: DNS:server.example.com
#	Following types are supported: EMAIL, DNS, URI
# phase1: Phase1 (outer authentication, i.e., TLS tunnel) parameters
#	(string with field-value pairs, e.g., "peapver=0" or
#	"peapver=1 peaplabel=1")
#	'peapver' can be used to force which PEAP version (0 or 1) is used.
#	'peaplabel=1' can be used to force new label, "client PEAP encryption",
#	to be used during key derivation when PEAPv1 or newer. Most existing
#	PEAPv1 implementation seem to be using the old label, "client EAP
#	encryption", and wpa_supplicant is now using that as the default value.
#	Some servers, e.g., Radiator, may require peaplabel=1 configuration to
#	interoperate with PEAPv1; see eap_testing.txt for more details.
#	'peap_outer_success=0' can be used to terminate PEAP authentication on
#	tunneled EAP-Success. This is required with some RADIUS servers that
#	implement draft-josefsson-pppext-eap-tls-eap-05.txt (e.g.,
#	Lucent NavisRadius v4.4.0 with PEAP in "IETF Draft 5" mode)
#	include_tls_length=1 can be used to force wpa_supplicant to include
#	TLS Message Length field in all TLS messages even if they are not
#	fragmented.
#	sim_min_num_chal=3 can be used to configure EAP-SIM to require three
#	challenges (by default, it accepts 2 or 3)
# phase2: Phase2 (inner authentication with TLS tunnel) parameters
#	(string with field-value pairs, e.g., "auth=MSCHAPV2" for EAP-PEAP or
#	"autheap=MSCHAPV2 autheap=MD5" for EAP-TTLS)
# Following certificate/private key fields are used in inner Phase2
# authentication when using EAP-TTLS or EAP-PEAP.
# ca_cert2: File path to CA certificate file. This file can have one or more
#	trusted CA certificates. If ca_cert2 is not included, server
#	certificate will not be verified. This is insecure and the CA file
#	should always be configured.
# client_cert2: File path to client certificate file
# private_key2: File path to client private key file
# private_key2_passwd: Password for private key file
# dh_file2: File path to DH/DSA parameters file (in PEM format)
# subject_match2: Substring to be matched against the subject of the
#	authentication server certificate.
# altsubject_match2: Substring to be matched against the alternative subject
#	name of the authentication server certificate.
#
# EAP-PSK variables:
# eappsk: 16-byte (128-bit, 32 hex digits) pre-shared key in hex format
# nai: user NAI
#
# EAP-FAST variables:
# pac_file: File path for the PAC entries. wpa_supplicant will need to be able
#	to create this file and write updates to it when PAC is being
#	provisioned or refreshed.
# phase1: fast_provisioning=1 option enables in-line provisioning of EAP-FAST
#	credentials (PAC)
#
# wpa_supplicant supports number of "EAP workarounds" to work around
# interoperability issues with incorrectly behaving authentication servers.
# These are enabled by default because some of the issues are present in large
# number of authentication servers. Strict EAP conformance mode can be
# configured by disabling workarounds with eap_workaround=0.

# Example blocks:

ctrl_interface=/var/run/wpa_supplicant

ap_scan=2

network={
	ssid="xxxxx"
	#scan_ssid=1
	#proto=RSN
	key_mgmt=WPA-PSK
	#pairwise=TKIP
	psk="xxxx"
}



And my current: /etc/default/wpasupplicant

# /etc/default/wpasupplicant

# WARNING! Make sure you have a configuration file!

ENABLED=1

# Useful flags:
#  -D <driver>		Wireless drive, typically optional.
#  -i <ifname>		Interface
#  -c <config file>	Configuration file
#  -d 			Debugging (-dd for more)
#  -w			Wait for interface to come up

# See the manual page wpa_supplicant(1) for more options and information.

# OPTIONS="-D ipw -i eth1 -c /etc/wpa_supplicant.conf -w"

# EXAMPLES:

# OPTIONS="-i wlan0 -D hostap -c /etc/wpa_supplicant.conf"
# OPTIONS="-i ath0 -D madwifi -c /etc/wpa_supplicant.conf"




For the life of me i cannot get this to work. 




Rob

---

### Post by jafenske on 2005-12-08
Try uncommenting out this line;

# OPTIONS="-D ipw -i eth1 -c /etc/wpa_supplicant.conf -w"

I think they say you san take out the -w if you are having problems,  I need to double check this though...

---

### Post by robfindlay on 2005-12-08
[QUOTE=jafenske]Try uncommenting out this line;

# OPTIONS="-D ipw -i eth1 -c /etc/wpa_supplicant.conf -w"

I think they say you san take out the -w if you are having problems,  I need to double check this though...[/QUOTE]

Nope, no joy.  Same errors.

is there some special way i should be initializing the interface?  Should i stop gnome from trying to bring up the interface before running wpa_supplicant? 


Anyone else with DELL 6000's w/ IPW2200 gotten this to work? 


Rob

---

### Post by robfindlay on 2005-12-08
BUMP.

Anyone.....help? .....anyone?

---

### Post by routerstu on 2005-12-09
did you look at this for an example?  i am going to try it now


[http://number9.hellooperator.net/articles/2005/11/21/fun-with-wpa_supplicant](http://number9.hellooperator.net/articles/2005/11/21/fun-with-wpa_supplicant)

---

### Post by routerstu on 2005-12-09
im stuck. it looks like it is working but i dont get an ip.  im using linksys v5 router with wpa2.  i am only using "wpa personal" and "aes" on the linksys router.  ill post relevant stuff below.

-------------------------------------------------------------------------jason@UbuntuLap:/var/log$ cat /etc/wpa_supplicant.conf
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
        ssid="seattle1"
        # 'RSN' == 'WPA2'
        proto=RSN WPA
        # that's 'pre-shared key'
        key_mgmt=WPA-PSK
        # lists ciphers to try. CCMP is AES
        # pairwise is for client -> AP, group is for broadcasts
        pairwise=CCMP TKIP
        group=CCMP TKIP
        # this can be made faster.see wpa_passphrase(1)
        psk="DAA37E331931Dxxxxxxxxxxxxxxxxxxxx3A4BF11D3CC2E622F0A70592B5DFA59"
}

#network={
#        ssid=""
#        key_mgmt=NONE
#}

-----------------------------------------------------------------------


jason@UbuntuLap:/var/log$
jason@UbuntuLap:/var/log$ sudo wpa_cli
wpa_cli v0.4.5
Copyright (c) 2004-2005, Jouni Malinen <jkmaline@cc.hut.fi> and contributors

This program is free software. You can distribute it and/or modify it
under the terms of the GNU General Public License version 2.

Alternatively, this software may be distributed under the terms of the
BSD license. See README and COPYING for more details.


Selected interface 'eth1'

Interactive mode

> status
bssid=00:14:bf:ad:e9:56
ssid=seattle1
pairwise_cipher=CCMP
group_cipher=CCMP
key_mgmt=WPA2-PSK
wpa_state=COMPLETED
Supplicant PAE state=AUTHENTICATED
suppPortStatus=Authorized
EAP state=SUCCESS
>

---------------------------------------------------------------------------


to me it looks like its happy but i dont have connectivity with dhcp or static ip.

any ideas?

---

### Post by routerstu on 2005-12-09
ok, it seems there are LOTS of issues with ipw2200 and using wpa.  the forums is full of these issues with various levels of success and methods of reaching them.  here is another:

[http://www.unpluggable.com/blog/](http://www.unpluggable.com/blog/)



im not sure what to do, im kind of a newb but getting through the wpa-supplicant could have been done, but resintalling drivers and changing all that other stuff is a but intimidating.  maybe someone will write something for us poor people with ipw2200's


:)

---

### Post by Jeff250 on 2006-01-11
If you're using Breezy, you don't need to update IEEE or IPW drivers.

Here's an excerpt from my working /etc/wpa_supplicant.conf file:

ctrl_interface=/var/run/wpa_supplicant
ap_scan=2

network={
  ssid="Jeff's Place"
  proto=wpa2
  key_mgmt=WPA-PSK
  pairwise=TKIP
  group=TKIP
  psk=Code you generated by inputting your ssid and password into wpa_passphrase
}

Now as far as command line arguments are concerned, I use in my /etc/default/wpasupplicant file:
OPTIONS="-i eth1 -c /etc/wpa_supplicant.conf -w -D ipw"
Also, don't forget to set ENABLED=1.

Wpa supplicant won't get an IP for you by itself.  You have to do that seperately (or automatically on boot-up, etc.).  If you set ENABLED=1, then all you have to do is type in "sudo ifup eth1" to activate your network (this will automatically start wpa_supplicant and get an IP, if possible).  Good luck.

---


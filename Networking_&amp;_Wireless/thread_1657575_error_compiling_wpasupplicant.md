---
title: "error compiling wpasupplicant"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by ruben_linux on 2011-01-01
I read the README, and i undertant that i have to make a .config archive with my options. Includes all features and driver interfaces that are
included in the wpa_supplicant package.

well it is:
***************************----------************************
CONFIG_IEEE8021X_EAPOL=y
CONFIG_EAP_MD5=y
CONFIG_EAP_MSCHAPV2=y
CONFIG_EAP_TLS=y
CONFIG_EAP_PEAP=y
CONFIG_EAP_TTLS=y
CONFIG_EAP_GTC=y
CONFIG_EAP_OTP=y
CONFIG_EAP_SIM=y
CONFIG_EAP_AKA=y
CONFIG_EAP_PSK=y
CONFIG_EAP_SAKE=y
CONFIG_EAP_GPSK=y
CONFIG_EAP_PAX=y
CONFIG_EAP_LEAP=y
CONFIG_EAP_IKEV2=y

#Following option can be used to include GSM SIM/USIM interface for GSM/UMTS
#authentication algorithm (for EAP-SIM/EAP-AKA). This requires pcsc-lite
#([http://www.linuxnet.com/](http://www.linuxnet.com/)) for smart card access.

CONFIG_PCSC=y

#Following options can be added to .config to select which driver
#interfaces are included. Hermes driver interface needs to be downloaded
#from Agere (see above).


CONFIG_DRIVER_HOSTAP=y
CONFIG_DRIVER_HERMES=y
CONFIG_DRIVER_MADWIFI=y
CONFIG_DRIVER_ATMEL=y
CONFIG_DRIVER_WEXT=y
CONFIG_DRIVER_RALINK=y
CONFIG_DRIVER_NDISWRAPPER=y
CONFIG_DRIVER_BROADCOM=y
CONFIG_DRIVER_IPW=y
CONFIG_DRIVER_BSD=y
CONFIG_DRIVER_NDIS=y
***************************----------************************
When i try compile:

ruben@CoYoTe:~/Descargas/wpa_supplicant-0.7.3/wpa_supplicant$ sudo make
  CC  config.c
  CC  notify.c
  CC  bss.c
  CC  eap_register.c
  CC  ../src/utils/common.c
  CC  ../src/utils/wpa_debug.c
  CC  ../src/utils/wpabuf.c
  CC  ../src/utils/os_unix.c
  CC  ../src/utils/eloop.c
  CC  config_file.c
  CC  ../src/rsn_supp/wpa.c
  CC  ../src/rsn_supp/preauth.c
  CC  ../src/rsn_supp/pmksa_cache.c
  CC  ../src/rsn_supp/peerkey.c
  CC  ../src/rsn_supp/wpa_ie.c
  CC  ../src/common/wpa_common.c
  CC  ../src/eap_peer/eap_tls.c
  CC  ../src/eap_peer/eap_peap.c
  CC  ../src/eap_common/eap_peap_common.c
  CC  ../src/eap_peer/eap_ttls.c
  CC  ../src/eap_peer/eap_md5.c
  CC  ../src/eap_peer/eap_mschapv2.c
  CC  ../src/eap_peer/mschapv2.c
  CC  ../src/eap_peer/eap_gtc.c
  CC  ../src/eap_peer/eap_otp.c
  CC  ../src/eap_peer/eap_sim.c
  CC  ../src/eap_peer/eap_leap.c
  CC  ../src/eap_peer/eap_psk.c
  CC  ../src/eap_common/eap_psk_common.c
  CC  ../src/eap_peer/eap_aka.c
  CC  ../src/eap_common/eap_sim_common.c
  CC  ../src/eap_peer/eap_pax.c
  CC  ../src/eap_common/eap_pax_common.c
  CC  ../src/eap_peer/eap_sake.c
  CC  ../src/eap_common/eap_sake_common.c
  CC  ../src/eap_peer/eap_gpsk.c
  CC  ../src/eap_common/eap_gpsk_common.c
  CC  ../src/eap_peer/eap_ikev2.c
  CC  ../src/eap_peer/ikev2.c
  CC  ../src/eap_common/eap_ikev2_common.c
  CC  ../src/eap_common/ikev2_common.c
  CC  ../src/eapol_supp/eapol_supp_sm.c
  CC  ../src/eap_peer/eap.c
  CC  ../src/eap_peer/eap_methods.c
../src/utils/pcsc_funcs.c:20:22: warning: winscard.h: No existe el archivo o directorio
../src/utils/pcsc_funcs.c:93: error: expected specifier-qualifier-list before ‘SCARDCONTEXT’
../src/utils/pcsc_funcs.c: In function ‘scard_pin_needed’:
../src/utils/pcsc_funcs.c:303: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:310: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c: In function ‘scard_init’:
../src/utils/pcsc_funcs.c:456: warning: implicit declaration of function ‘SCardEstablishContext’
../src/utils/pcsc_funcs.c:456: error: ‘SCARD_SCOPE_SYSTEM’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:456: error: (Each undeclared identifier is reported only once
../src/utils/pcsc_funcs.c:456: error: for each function it appears in.)
../src/utils/pcsc_funcs.c:457: error: ‘struct scard_data’ has no member named ‘ctx’
../src/utils/pcsc_funcs.c:458: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:464: warning: implicit declaration of function ‘SCardListReaders’
../src/utils/pcsc_funcs.c:464: error: ‘struct scard_data’ has no member named ‘ctx’
../src/utils/pcsc_funcs.c:480: error: ‘struct scard_data’ has no member named ‘ctx’
../src/utils/pcsc_funcs.c:501: warning: implicit declaration of function ‘SCardConnect’
../src/utils/pcsc_funcs.c:501: error: ‘struct scard_data’ has no member named ‘ctx’
../src/utils/pcsc_funcs.c:501: error: ‘SCARD_SHARE_SHARED’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:502: error: ‘SCARD_PROTOCOL_T0’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:502: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:502: error: ‘struct scard_data’ has no member named ‘protocol’
../src/utils/pcsc_funcs.c:504: error: ‘SCARD_E_NO_SMARTCARD’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:515: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:515: error: ‘struct scard_data’ has no member named ‘protocol’
../src/utils/pcsc_funcs.c:516: error: ‘struct scard_data’ has no member named ‘protocol’
../src/utils/pcsc_funcs.c:518: warning: implicit declaration of function ‘SCardBeginTransaction’
../src/utils/pcsc_funcs.c:518: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:528: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:537: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:540: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:544: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:572: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:590: error: ‘struct scard_data’ has no member named ‘pin1_required’
../src/utils/pcsc_funcs.c:594: warning: implicit declaration of function ‘SCardEndTransaction’
../src/utils/pcsc_funcs.c:594: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:594: error: ‘SCARD_LEAVE_CARD’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:604: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c: In function ‘scard_set_pin’:
../src/utils/pcsc_funcs.c:623: error: ‘struct scard_data’ has no member named ‘pin1_required’
../src/utils/pcsc_funcs.c: In function ‘scard_deinit’:
../src/utils/pcsc_funcs.c:654: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:655: warning: implicit declaration of function ‘SCardDisconnect’
../src/utils/pcsc_funcs.c:655: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:655: error: ‘SCARD_UNPOWER_CARD’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:656: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:662: error: ‘struct scard_data’ has no member named ‘ctx’
../src/utils/pcsc_funcs.c:663: warning: implicit declaration of function ‘SCardReleaseContext’
../src/utils/pcsc_funcs.c:663: error: ‘struct scard_data’ has no member named ‘ctx’
../src/utils/pcsc_funcs.c: In function ‘scard_transmit’:
../src/utils/pcsc_funcs.c:684: warning: implicit declaration of function ‘SCardTransmit’
../src/utils/pcsc_funcs.c:684: error: ‘struct scard_data’ has no member named ‘card’
../src/utils/pcsc_funcs.c:685: error: ‘struct scard_data’ has no member named ‘protocol’
../src/utils/pcsc_funcs.c:685: error: ‘SCARD_PROTOCOL_T1’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:686: error: ‘SCARD_PCI_T1’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:686: error: ‘SCARD_PCI_T0’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:690: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c: In function ‘_scard_select_file’:
../src/utils/pcsc_funcs.c:736: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c: In function ‘scard_select_file’:
../src/utils/pcsc_funcs.c:786: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c: In function ‘scard_get_record_len’:
../src/utils/pcsc_funcs.c:798: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:806: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c: In function ‘scard_read_record’:
../src/utils/pcsc_funcs.c:834: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:845: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c: In function ‘scard_read_file’:
../src/utils/pcsc_funcs.c:886: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:889: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c: In function ‘scard_verify_pin’:
../src/utils/pcsc_funcs.c:928: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:935: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c: In function ‘scard_get_imsi’:
../src/utils/pcsc_funcs.c:978: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c: In function ‘scard_gsm_auth’:
../src/utils/pcsc_funcs.c:1055: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:1068: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
../src/utils/pcsc_funcs.c:1071: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:1073: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:1087: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c: In function ‘scard_umts_auth’:
../src/utils/pcsc_funcs.c:1154: error: ‘struct scard_data’ has no member named ‘sim_type’
../src/utils/pcsc_funcs.c:1169: error: ‘SCARD_S_SUCCESS’ undeclared (first use in this function)
make: *** [../src/utils/pcsc_funcs.o] Error 1

can we help me, i dont understant this error. Currently i have install wpasupplicant 0.6.10-2.

---

### Post by chili555 on 2011-01-01
It may be that you do not have installed or have installed a version that is too old of a dependency. I suggest you look at the README to be certain that all the items required are installed. Often, the -dev package is also required, although it may not be evident by reading the README. From the error:> ../src/utils/[COLOR="Red"]pcsc[/COLOR]_funcs.c:20:22: warning: winscard.h: No existe el archivo o directorioI'd suggest looking in System > Administration > Synaptic and make sure you have the latest versions of libpcsclite and libpcsclite-dev installed. Then do:```
sudo make clean
sudo make
```And proceed as outlined in the README.

---

### Post by ruben_linux on 2011-01-01
i had no install libpcsclite-dev.

i will try compile and then post.
:KS

---


---
title: "Cisco AnyConnect with Ubuntu 12.10"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by wurstsalat on 2013-01-12
I've installed Cisco AnyConnect on my Ubuntu 12.10. While connecting I revceive following error: 
```
anyconnect cannot confirm it is connected to your secure gateway
```

I've googled for nearly 5 hours and tried everything concerning the Certificate-Isuess everywhere discribed
([http://askubuntu.com/questions/129477/server-certificate-problem-with-cisco-anyconnect-vpn-client](http://askubuntu.com/questions/129477/server-certificate-problem-with-cisco-anyconnect-vpn-client) , [http://blog.bstpierre.org/fixing-certificate-errors-with-cisco-anyconnect](http://blog.bstpierre.org/fixing-certificate-errors-with-cisco-anyconnect) , etc). 

After a look into syslog I think it is not a certificate issue:
```
Jan 12 17:05:35 x5 acvpnui[16263]: An SSL VPN connection to vpn.*****.de has been requested by the user.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 796 No profile available for host vpn.*****.de.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getHostInitSettings File: ProfileMgr.cpp Line: 876 Profile () not found. Using default settings.
Jan 12 17:05:35 x5 acvpnagent[1053]: Function: ResolveHostname File: Utility/HostLocator.cpp Line: 560 Resolved vpn.*****.de to **.**.**.**
Jan 12 17:05:35 x5 acvpnagent[1053]: Writing to hosts file:  **.**.**.**#011vpn.*****.de 
Jan 12 17:05:35 x5 acvpnui[16263]: Message type information sent to the user: Contacting vpn.*****.de.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: loadProfiles File: ProfileMgr.cpp Line: 110 No profile is available.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 796 No profile available for host vpn.*****.de.
Jan 12 17:05:35 x5 acvpnui[16263]: Using default preferences. Some settings (e.g. certificate matching) may not function as expected if a local profile is expected to be used. Verify that the selected host is in the server list section of the profile and that the profile is configured on the secure gateway.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getProfileNameFromHost File: ProfileMgr.cpp Line: 796 No profile available for host vpn.*****.de.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getHostInitSettings File: ProfileMgr.cpp Line: 876 Profile () not found. Using default settings.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: enumerateCert File: Certificates/FileCertStore.cpp Line: 214 Invoked Function: enumerateCert Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND Could not acquire any X509 certificate in the /home/es/.cisco/certificates/client/ directory.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: Enumerate File: Certificates/FileCertStore.cpp Line: 118 Invoked Function: Enumerate Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: enumerateCert File: Certificates/FileCertStore.cpp Line: 157 Invoked Function: enumerateCert Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND The /opt/.cisco/certificates/client/ directory was not found.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: Enumerate File: Certificates/FileCertStore.cpp Line: 118 Invoked Function: Enumerate Return Code: -31391730 (0xFE21000E) Description: CERTSTORE_ERROR_CERT_NOT_FOUND 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getCertList File: ApiCert.cpp Line: 259 Number of certificates found: 0
Jan 12 17:05:35 x5 acvpnui[16263]: Function: ResolveHostname File: Utility/HostLocator.cpp Line: 560 Resolved vpn.*****.de to **.**.**.**
Jan 12 17:05:35 x5 acvpnui[16263]: Initiating VPN connection to the secure gateway https://vpn.*****.de
Jan 12 17:05:35 x5 acvpnui[16263]: Function: getUserName File: CTransportCurlStatic.cpp Line: 1972 PasswordEntry username is es
Jan 12 17:05:35 x5 acvpnui[16263]: Function: STLoadLibrary File: Utility/Win/HModuleMgr.cpp Line: 149 Invoked Function: dlopen Return Code: 0 (0x00000000) Description: /usr/lib/i386-linux-gnu/libnssutil3.so: version `NSSUTIL_3.14' not found (required by /usr/lib/firefox/libnss3.so) 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: loadLibs File: Certificates/NSSCertUtils.cpp Line: 1378 Invoked Function: CHModuleMgr::STLoadLibrary Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: CNSSCertUtils File: Certificates/NSSCertUtils.cpp Line: 282 Invoked Function: CNSSCertUtils::loadLibs Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: CNSSCertStore File: Certificates/NSSCertStore.cpp Line: 55 Invoked Function: CNSSCertUtils Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: addNSSStore File: Certificates/CollectiveCertStore.cpp Line: 1058 Invoked Function: CNSSCertStore::CNSSCertStore Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: OpenStores File: Certificates/CollectiveCertStore.cpp Line: 248 Invoked Function: CCollectiveCertStore::addNSSStore Return Code: -33554425 (0xFE000007) Description: GLOBAL_ERROR_NOT_INITIALIZED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: Verify File: Certificates/FileCertificate.cpp Line: 395 Invoked Function: X509_verify_cert Return Code: 20 (0x00000014) Description: unknown unable to get local issuer certificate
Jan 12 17:05:35 x5 acvpnui[16263]: Function: VerifyServerCertificate File: Certificates/FileCertStore.cpp Line: 790 Invoked Function: CFileCertificate::Verify Return Code: -31326191 (0xFE220011) Description: CERTIFICATE_ERROR_VERIFY_CHAIN_POLICY_FAILED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: Verify File: Certificates/FileCertificate.cpp Line: 395 Invoked Function: X509_verify_cert Return Code: 20 (0x00000014) Description: unknown unable to get local issuer certificate
Jan 12 17:05:35 x5 acvpnui[16263]: Function: VerifyServerCertificate File: Certificates/FileCertStore.cpp Line: 790 Invoked Function: CFileCertificate::Verify Return Code: -31326191 (0xFE220011) Description: CERTIFICATE_ERROR_VERIFY_CHAIN_POLICY_FAILED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: VerifyServerCertificate File: Certificates/CertHelper.cpp Line: 174 Invoked Function: CCertStore::VerifyServerCertificate Return Code: -31326191 (0xFE220011) Description: CERTIFICATE_ERROR_VERIFY_CHAIN_POLICY_FAILED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: sendRequest File: ConnectIfc.cpp Line: 3057 Invoked Function: CTransport::SendRequest Return Code: -29949919 (0xFE370021) Description: CTRANSPORT_ERROR_PEER_CERT_REJECTED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: connect File: ConnectIfc.cpp Line: 452 Invoked Function: ConnectIfc::sendRequest Return Code: -29949919 (0xFE370021) Description: CTRANSPORT_ERROR_PEER_CERT_REJECTED 
Jan 12 17:05:35 x5 acvpnui[16263]: Function: TranslateStatusCode File: ConnectIfc.cpp Line: 2881 Invoked Function: TranslateStatusCode Return Code: -29949919 (0xFE370021) Description: CTRANSPORT_ERROR_PEER_CERT_REJECTED AnyConnect cannot confirm it is connected to your secure gateway.  The local network may not be trustworthy.  Please try another network.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: doConnectIfcConnect File: ConnectMgr.cpp Line: 1862 Invoked Function: ConnectIfc::connect Return Code: -29949919 (0xFE370021) Description: CTRANSPORT_ERROR_PEER_CERT_REJECTED 
Jan 12 17:05:35 x5 acvpnui[16263]: Message type warning sent to the user: Connection attempt has failed.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: processIfcData File: ConnectMgr.cpp Line: 2310 Content type (unknown) received. Response type (undefined) from vpn.*****.de: 
Jan 12 17:05:35 x5 acvpnui[16263]: Message type error sent to the user: AnyConnect cannot confirm it is connected to your secure gateway.  The local network may not be trustworthy.  Please try another network.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: connect File: ConnectMgr.cpp Line: 1917 ConnectMgr::processIfcData failed
Jan 12 17:05:35 x5 acvpnui[16263]: Function: initiateConnect File: ConnectMgr.cpp Line: 987 Connection failed.
Jan 12 17:05:35 x5 acvpnui[16263]: VPN state: Disconnected Network state: Network Accessible Network control state: Network Access: Available Network type: Undefined
Jan 12 17:05:35 x5 acvpnui[16263]: Function: setConnectRequestComplete File: ConnectMgr.cpp Line: 8424 Connect request complete. Proceeding to cleanup.
Jan 12 17:05:35 x5 acvpnui[16263]: Function: run File: ConnectMgr.cpp Line: 568 Invoked Function: ConnectMgr::initiateConnect Return Code: -29556727 (0xFE3D0009) Description: CONNECTMGR_ERROR_UNEXPECTED 
```


Has anybody an idea what I can do to fix this?
thx in advance.

---

### Post by galfly on 2013-03-12
Hi,

AnyConnect gives this error when vpn client can not successfully validate the gateway's certificate. You might be a victim of a man-in-the-middle attack, and the certificate might be tempered with; or the secure headend does not have a properly provisioned certificate to begin with. If all certificates are valid, then the secure gateway has "strict mode" on, which will prompt this error for all remote connections.

---


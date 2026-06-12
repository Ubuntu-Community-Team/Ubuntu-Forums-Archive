---
title: "knetwork manager cannot find network"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by pretobomba on 2009-01-22
So, im running on intrepid, with Kubuntu (kernel 2.6.27-9-generic), and when trying to connect to a wireless network using knetworkmanager, it just doesn't connect, it loads for a while and returns to normal (not connected). Also knetworkmanager doesn't show my home network, which is odd because the wireless router is right at the side of my computer. I tried to run both networkmanager and knetworkmanager as root, but it doesn't make any difference.Output when i run knetworkmanager:

Error: "/tmp/kde-pretobomba" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-pretobomba" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-pretobomba" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-pretobomba" is owned by uid 1000 instead of uid 0.    
kbuildsycoca running...                                                
Error: "/var/tmp/kdecache-pretobomba" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-pretobomba" is owned by uid 1000 instead of uid 0.         
Error: "/var/tmp/kdecache-pretobomba" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-pretobomba" is owned by uid 1000 instead of uid 0.
NMSettings::NMSettings                                                      
restore setting: ConnectionSetting_51qe6L3aG54QKbC7_connection              
restore setting: ConnectionSetting_51qe6L3aG54QKbC7_ipv4                    
restore setting: ConnectionSetting_51qe6L3aG54QKbC7_802-11-wireless         
restore setting: ConnectionSetting_51qe6L3aG54QKbC7_802-11-wireless-security
WirelessSecurity::fromMap                                                   
restore setting: ConnectionSetting_51qe6L3aG54QKbC7_802-1x                  
IEEE8021x::fromMap                                                          
restore setting: ConnectionSetting_AxZkHLtV1FwumM1u_connection              
restore setting: ConnectionSetting_AxZkHLtV1FwumM1u_ipv4                    
restore setting: ConnectionSetting_AxZkHLtV1FwumM1u_802-11-wireless         
restore setting: ConnectionSetting_AxZkHLtV1FwumM1u_802-11-wireless-security
WirelessSecurity::fromMap                                                   
restore setting: ConnectionSetting_AxZkHLtV1FwumM1u_802-1x                  
IEEE8021x::fromMap                                                          
restore setting: ConnectionSetting_lOiaOH5exvz9dwMK_connection              
restore setting: ConnectionSetting_lOiaOH5exvz9dwMK_ipv4                    
restore setting: ConnectionSetting_lOiaOH5exvz9dwMK_802-11-wireless         
restore setting: ConnectionSetting_lOiaOH5exvz9dwMK_802-11-wireless-security                                                   
(...)                                        
Connection::GetSettings, obj: /org/freedesktop/NetworkManagerSettings/Connection/1                                                                              
(...)                                               
  Processing Setting '802-11-wireless'                                          
  Attach setting '802-11-wireless'                                              
    (...)
  Processing Setting '802-1x'
  Setting '802-1x' is empty, discarding
(...)
  Processing Setting '802-1x'
IEEE8021x::toSecretsMap
  Setting '802-1x' is empty, discarding


Any ideas?

---


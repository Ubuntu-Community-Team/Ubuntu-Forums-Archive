---
title: "Intel 3945 wireless card does not work in kernel 2.6.31"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by jirik_cs on 2009-09-09
There is a problem with Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) in Karmic Koala (Kubuntu) which uses the new Linux Kernel 2.6.31-x.

I can not connect to open wifi network, here is the output from bash. The settings is "autoconnect to network vosecek". Connection failed ...

Some other users have similar problems. What is going on?

```
karmic@karmic-laptop:~$ knetworkmanager 
NMSettings::NMSettings                  
restore setting: ConnectionSetting_aDJvmL5v61LRulKa_connection
restore setting: ConnectionSetting_aDJvmL5v61LRulKa_ipv4      
restore setting: ConnectionSetting_aDJvmL5v61LRulKa_802-11-wireless
restore setting: ConnectionSetting_aDJvmL5v61LRulKa_802-11-wireless-security
WirelessSecurity::fromMap                                                   
restore setting: ConnectionSetting_aDJvmL5v61LRulKa_802-1x                  
IEEE8021x::fromMap                                                          
Connection::GetSettings, obj: /org/freedesktop/NetworkManagerSettings/Connection/0
  Processing Setting 'connection'                                                 
  Attach setting 'connection'                                                     
    autoconnect: <bool>true</bool>                                                
    id: <string>vosecek</string>                                                  
    type: <string>802-11-wireless</string>                                        
    uuid: <string>aDJvmL5v61LRulKa</string>                                       
  Processing Setting 'ipv4'                                                       
  Attach setting 'ipv4'                                                           
    ignore-auto-dns: <bool>false</bool>                                           
    ignore-auto-routes: <bool>false</bool>                                        
    method: <string>auto</string>                                                 
  Processing Setting '802-11-wireless'                                            
  Attach setting '802-11-wireless'                                                
    mode: <string>infrastructure</string>                                         
    ssid: <list>  <byte>118</byte>  <byte>111</byte>  <byte>115</byte>  <byte>101</byte>  <byte>99</byte>  <byte>101</byte>  <byte>107</byte> </list> 
  Processing Setting '802-11-wireless-security'                                                                                                       
WirelessSecurity::getEnabled false (null)                                                                                                             
  Setting '802-11-wireless-security' is not enabled, discarding                                                                                       
  Processing Setting '802-1x'                                                                                                                         
  Setting '802-1x' is empty, discarding                                                                                                               
karmic@karmic-laptop:~$ Connection::GetSettings, obj: /org/freedesktop/NetworkManagerSettings/Connection/0                                            
  Processing Setting 'connection'
  Attach setting 'connection'
    autoconnect: <bool>true</bool>
    id: <string>vosecek</string>
    type: <string>802-11-wireless</string>
    uuid: <string>aDJvmL5v61LRulKa</string>
  Processing Setting 'ipv4'
  Attach setting 'ipv4'
    ignore-auto-dns: <bool>false</bool>
    ignore-auto-routes: <bool>false</bool>
    method: <string>auto</string>
  Processing Setting '802-11-wireless'
  Attach setting '802-11-wireless'
    mode: <string>infrastructure</string>
    ssid: <list>  <byte>118</byte>  <byte>111</byte>  <byte>115</byte>  <byte>101</byte>  <byte>99</byte>  <byte>101</byte>  <byte>107</byte> </list>
  Processing Setting '802-11-wireless-security'
WirelessSecurity::getEnabled false (null)
  Setting '802-11-wireless-security' is not enabled, discarding
  Processing Setting '802-1x'
  Setting '802-1x' is empty, discarding
```

---


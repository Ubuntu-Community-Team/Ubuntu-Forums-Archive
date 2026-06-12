---
title: "How make opnevpn connections?"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by dimas09 on 2010-07-26
Hello!
I've install openvpn sudo apt-get install openvpn
after that I take my configs from windows
[EMAIL="demi@demi-desktop:%7E/vpn.server.com"]demi@demi-desktop:~/vpn.server.com[/EMAIL]$ openvpn --config vpn.server.com.ovpn
and I got next log:
```

Mon Jul 26 16:33:41 2010 OpenVPN 2.1_rc19 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 13 2009
Mon Jul 26 16:33:41 2010 WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Mon Jul 26 16:33:41 2010 NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables                     
Mon Jul 26 16:33:41 2010 WARNING: file 'ibonusdev1.vpn.inprimex.com.key' is group or others accessible                                              
Mon Jul 26 16:33:41 2010 /usr/bin/openssl-vulnkey -q -b 2048 -m <modulus omitted>                                                                   
Mon Jul 26 16:33:41 2010 LZO compression initialized                                                                                                
Mon Jul 26 16:33:41 2010 Control Channel MTU parms [ L:1558 D:138 EF:38 EB:0 ET:0 EL:0 ]                                                            
Mon Jul 26 16:33:41 2010 Data Channel MTU parms [ L:1558 D:1450 EF:58 EB:135 ET:0 EL:0 AF:3/1 ]                                                     
Mon Jul 26 16:33:41 2010 Local Options hash (VER=V4): '22188c5b'                                                                                    
Mon Jul 26 16:33:41 2010 Expected Remote Options hash (VER=V4): 'a8f55717'                                                                          
Mon Jul 26 16:33:41 2010 UDPv4 link local: [undef]                                                                                                  
Mon Jul 26 16:33:41 2010 UDPv4 link remote: 77.120.98.86:1194                                                                                       
Mon Jul 26 16:33:41 2010 VERIFY OK: depth=1, /C=UA/ST=Kyiv/L=Kyiv/O=inprimex.com/emailAddress=admin@inprimex.com                                    
Mon Jul 26 16:33:41 2010 VERIFY OK: depth=0, /C=UA/ST=Kyiv/L=Kyiv/O=inprimex.com/OU=Office/CN=vpn.inprimex.com/emailAddress=admin@inprimex.com      
Mon Jul 26 16:33:41 2010 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key                                                    
Mon Jul 26 16:33:41 2010 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication                                            
Mon Jul 26 16:33:41 2010 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key                                                    
Mon Jul 26 16:33:41 2010 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication                                            
Mon Jul 26 16:33:41 2010 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA                                                
Mon Jul 26 16:33:41 2010 [vpn.inprimex.com] Peer Connection Initiated with 77.120.98.86:1194                                                        
Mon Jul 26 16:33:42 2010 Note: Cannot ioctl TUNSETIFF tun: Operation not permitted (errno=1)                                                        
Mon Jul 26 16:33:42 2010 Note: Attempting fallback to kernel 2.2 TUN/TAP interface                                                                  
Mon Jul 26 16:33:42 2010 Cannot allocate TUN/TAP dev dynamically                                                                                    
Mon Jul 26 16:33:42 2010 Exiting                                            

```What I need to do?

---


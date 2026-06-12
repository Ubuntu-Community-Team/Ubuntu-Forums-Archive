---
title: "Mgetty issue! not able to connect modem says busy!"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by prinsh on 2011-08-10
Hi friends i have been trying to get my modem back working for last a week now....i don't know where m going working..
Below is the log for connection!!

08/10 14:37:51 yS0  mgetty: interim release 1.1.36-Jun15                        
08/10 14:37:51 yS0  check for lockfiles                                         
08/10 14:37:51 yS0   checklock: no active process has lock, will remove         
08/10 14:37:51 yS0  locking the line                                            
08/10 14:37:51 yS0   makelock(ttyS0) called                                     
08/10 14:37:51 yS0   do_makelock: lock='/var/lock/LCK..ttyS0'                   
08/10 14:37:51 yS0   lock made                                                  
08/10 14:37:51 yS0   tio_get_rs232_lines: status: RTS CTS DSR DTR DCD RI        
08/10 14:37:51 yS0  WARNING: DCD line still active, check modem settings (AT&Dx)
08/10 14:37:51 yS0  lowering DTR to reset Modem                                 
08/10 14:37:52 yS0   tss: set speed to 115200 (10002)                   
08/10 14:37:52 yS0   tio_set_flow_control( HARD )                       
08/10 14:37:52 yS0   waiting for line to clear (VTIME=1), read:         
08/10 14:37:52 yS0  send: \dATQ0V1H0[0d]                                
08/10 14:37:53 yS0  waiting for ``OK''                                  
08/10 14:37:53 yS0   got:                                               
08/10 14:38:13 yS0  timeout in chat script, waiting for `OK'            
08/10 14:38:13 yS0  init chat timed out, trying force-init-chat         
08/10 14:38:13 yS0  send: \d[10][03]\d\d\d+++\d\d\d[0d]\dATQ0V1H0[0d]   
08/10 14:38:18 yS0  waiting for ``OK''                                  
08/10 14:38:18 yS0   got: [0d]ATQ0V1H0[0d]                              
08/10 14:38:18 yS0    CND: ATQ0V1H0[0d][0a]OK ** found **               
08/10 14:38:18 yS0   force-init succeeded, retrying init-chat           
08/10 14:38:18 yS0   waiting for line to clear (VTIME=3), read: [0d][0a] 
08/10 14:38:18 yS0  send: \dATQ0V1H0[0d]                                
08/10 14:38:19 yS0  waiting for ``OK''                                  
08/10 14:38:19 yS0   got: ATQ0V1H0[0d]                                  
08/10 14:38:19 yS0    CND: OKATQ0V1H0[0d][0a]OK ** found **             
08/10 14:38:19 yS0  send: ATS0=0Q0&D3&C1[0d]                            
08/10 14:38:19 yS0  waiting for ``OK''                                  
08/10 14:38:19 yS0   got: [0d]                                          
08/10 14:38:19 yS0    CND: OK[0a]ATS0=0Q0&D3&C1[0d]                     
08/10 14:38:19 yS0    CND: ATS0=0Q0&D3&C1[0d][0a]OK ** found **         
08/10 14:38:19 yS0   waiting for line to clear (VTIME=3), read: [0d][0a]
08/10 14:38:19 yS0   removing lock file ...


Friends i have modified my mgetty.conf file for my use and m using a different file as a chat script...


'' ATZ
OK ATM0
OK ATDT251862
CONNECT ""
ogin: ppp
sword: ppp123

this is the chat script for making the connection..



and below is the mgetty.conf file

#server properties
#Wed Jan 27 16:47:02 GMT 2010
portowner=root
debug=7
device=/dev/ttyS0
port=ttyS0
serverargs="-detach asyncmap 0 modem crtscts login lock proxyarp"
clientip=10.101.156.72
netmask=255.255.255.0
baud=115200
mode=data-only
portmode=0666
dns2=10.101.156.221
dns1=10.101.156.220
rings=3
optionsargs="-detach asyncmap 0 lock proxyarp defaultroute noipdefault crtscts modem"
portgroup=root
serverip=10.101.156.71


   Please help me thanx in advance!!!!

---


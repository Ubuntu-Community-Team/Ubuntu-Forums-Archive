---
title: "Mobile Broadband :Adding the initial Signal Strength to the gnome-ppp connection log"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by alexfish on 2009-12-01
**Adding the initial Signal Strength to the gnome-ppp connection log **

 The signal strength on a mobile connection can in many cases be obtained by sending a special 'AT' string to it. I add an extra init string to gnome-ppp so it is reported in the connection log when using mobile broadband dongles which do not display signal strength. This is only a snapshot but does help if you have a poor connection and want to know why. I therefore set: 



......................................................................

 Init 4 = AT+CSQ 



......................................................................

 which writes a line in the log file in the format:



......................................................................

  **+CSQ: <rssi>,<ber>**
  where
<rssi> is the  Received Signal Strength Indicator
  0 = 113 dBm or less
  1 = 111 dBm
  2 to 30 = 109 to 53 dBm
  31 = 51 dBm or greater
<ber> is the Bit Error Rate, in percent (99 is not known or not detectable)


.......................................................................................................................

 In practice, if the signal strength is below 10 then GPRS connections are unreliable. Values around 15 are good, 25 is excellent. The log file is accessible whilst connected by right clicking on the connection icon in the panel -> Connection Log

added 
the link worth reading

[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)

---

### Post by alexfish on 2010-06-19
Further to the above : I have written a small script that will continually monitor the signal strength of the modem ; Note the connection must be established first as there appears to be a bug in the " modem:cmd " 

#!/bin/sh                                           
  MYVERSION="0.0.1" 

##########################################################################
# 3gsignalstrength   for use with gnomeppp or wvdial                      #                                                                        
##########################################################################
#                                                                        
# 3gsignalstrength  Version 0,0.1 2010/05/20                             
#                                                                        
#  This program is free software; you can redistribute it and/or modify  
#  it under the terms of the GNU General Public License as published by  
#  the Free Software Foundation; either version 2 of the License, or     
#  (at your option) any later version.                                   
#                                                                        
#  WITHOUT ANY WARRANTY statement above includes additional charges you  
#  may receive from your operator by using this script, defects to your  
#  SIM card including but not limited to being PIN blocked, defects on   
#  your hardware, 3G service ban etc. USE WITH CARE. Author has no       
#  responsibility for what may happen to you.                            
#                                                                        
#  Author is not related in any way with any of the companies, being     
#  operators or modem manufacturers, other than being a customer to      
#  some of them.                                                         
##########################################################################
#                                                   
# dependancy " modem-cmd " ; must be installed     
#                                                   
# requires modem with two or more control ports 
#                                                   
#  typical ZTE MF 626  on ttyUSB1                   
#  to find usb devices                              
#   ls -al /dev/ttyU*                               
#   edit tty port  "modem-cmd /dev/ttyUSB* AT+CSQ"  
#     AT+CSQ =  aquire signal strength              
#                                                   
# +CSQ: <rssi>,<ber>                                
# where                                             
# <rssi> is the Received Signal Strength Indicator  
# 0        = 113 dBm or less                        
# 1        = 111 dBm                                
# 2  to 30 = 109 to 53 dBm                          
# 31 = 51 dBm or greater                            
#  <ber> is the Bit Error Rate, in percent          
#  (99 is not known or not detectable)                      
#####################################################
                                                    
 while [ 1 ]    # loop for ever                     
                                                    
   do                                               
                                                    
      reset                                         
                                                    
    echo &date                                      
echo                                                
    echo Signal Strength                            
                                                    
#          edit ttyXXXX port to suit                
 modem-cmd /dev/ttyUSB1 AT+CSQ                         
                                                     
 sleep $((2*60))  # edit for timing                 
                                                    
done                                                
                                                    
#####################################################

---


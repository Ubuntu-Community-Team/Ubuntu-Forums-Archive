---
title: "Huawei Mobile Broadband Devices (Ubuntu 12.04)"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by alexfish on 2012-05-06
Hi all,

Having problems getting connected  -: Huawei  " next generation devices"

can have a look at this Extract from a How To:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For Now link to drivers: for the HMP try googling best source / re your provider may have released both 
[http://www.huaweidevice.com/tcpsdown...oadID=NDAzMjM=]("http://www.huaweidevice.com/tcpsdownload/downLoadCenter?category=&flay=software&downloadID=NDAzMjM=")

Relevance:" If I can get the dongle to be recognised, would it then be  possible to  run the included software (on the dongle) using either wine  or Windows  XP in parallel to connect to the internet?"  POST  #[**1**]("http://ubuntuforums.org/showpost.php?p=11847881&postcount=1")

For mobile partner latest version try googling Mobile Partner 21 , make  sure its, Linux version , re when on the site , it will indicate Linux ,  if not indicating Linux then avoid , have tested some of these sites ,  BAH , See Screen Shots , 3 is the drivers 4 is the inside of the Linux  Mobile Partner  tar file
to install just use unzip at the location , the use terminal >  cd to where the files reside then ./install . 
follow prompts .

problem find official huawei driver/Mobile Partner : can try looking  here : Use at Own Risk , Did an install of this , no Problems as of yet
[http://bloglinux-patenpisan.blogspot...003280003.html]("http://bloglinux-patenpisan.blogspot.com/2011/09/huawei-mobile-partner-linux-21003280003.html")

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
From POST ::   			#[**64**]("http://ubuntuforums.org/showpost.php?p=11709821&postcount=64")
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

download and install at own risk : If a Novic or New User then suggest using the bloglinux link 

need Help with installing Feel free to post

alexfish

---

### Post by alexfish on 2012-05-13
**UPDATING SOME INFO RE POST #1**

Huawei Lte Devices ; Note these devices usually have 2 modem ports , 3g and lte

to by-pass NM RE: Modem Manager / may want to connect to /dev/ttyUSB_utps_modem or Huawie rules not installed /dev/ttyUSB0
modem manager will nearly always want to connect 3g:- IE to the above ports

Use ppp:

use ppp to use ports
**EXAMPLES:**
No Huawei rules ; or as listed by ls -al /dev/serial/by-id
```
connect 3g /dev/ttyUSB0
connect lte /dev/ttyUSB2
```with Huawie rules probable best option to use
```
connect 3g port /dev/ttyUSB_utps_modem
connect lte port /dev/ttyUSB_utps_pcui
```if using gammu or wammu ; configure to use port not in use by ppp

to configure ppp
```
sudo pppconfig
```to call ppp
```
pon <your-connection>
```also check the user privileges else will have to use "sudo" . if using lte set baud to 480000 or higher will have to test
if the device has been in use then usually dial command "*99#" or "*99***1#" will do , if cdma type connection , then "#777"

example listing from usb-devices say he I think
```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option  EPs=3 and Prot=01 = modem port
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=huawei_ether
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=huawei_ether
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option  EPs=2 and Prot=02 = lte port
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```Test script for modem-manager[FONT=monospace]
[/FONT]```
#!/bin/bash

########################################################################
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by 
# the Free Software Foundation; either version 2 of the License, or   
# (at your option) any later version.                                  
#                                                                      
# This program is distributed in the hope that it will be useful,      
# but WITHOUT ANY WARRANTY; without even the implied warranty of      
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the        
# GNU General Public License for more details:                        
########################################################################
# cisabfone-MM-Dbus-Test (0.1.b)                                      
#  (0.1.b) added CDMA support (untested)                                  
# Copywrite (C) cisabfone@gmail.com                                       
# BUGS and ALL : ah.cisab@gmail.com                                       
########################################################################

INTERFACE_PROPERTIES="org.freedesktop.DBus.Properties"
MM_DBUS_SERVICE="org.freedesktop.ModemManager"
DBUS_PATH="/org/freedesktop/ModemManager"
DBUS_INTERFACE="org.freedesktop.ModemManager"
MODEM="org.freedesktop.ModemManager.Modem"
MODEM_CDMA="org.freedesktop.ModemManager.Modem.Cdma"
GSM_CARD="org.freedesktop.ModemManager.Modem.Gsm.Card"
GSM_NETWORK="org.freedesktop.ModemManager.Modem.Gsm.Network"
MODEM_SIMPLE="org.freedesktop.ModemManager.Modem.Simple"
MM="org.freedesktop.ModemManager"
GET_INFO="org.freedesktop.ModemManager.Modem.GetInfo"
GSM_NETWORK_SCAN="org.freedesktop.ModemManager.Modem.Gsm.Network.Scan" 
GSM_NETWORK_REG_INFO="org.freedesktop.ModemManager.Modem.Gsm.Network.GetRegistrationInfo"
MODEM_ENABLE="org.freedesktop.ModemManager.Modem.Enable"
Get_Esn="org.freedesktop.ModemManager.Modem.Cdma.GetEsn"
Get_Serving_System="org.freedesktop.ModemManager.Modem.Cdma.GetServingSystem"
Get_Registration_State="org.freedesktop.ModemManager.Modem.Cdma.GetRegistrationState"
###############################################################

################################################################
MM_ENUM=$(dbus-send --print-reply --system --dest=$MM \
    $DBUS_PATH $MM.EnumerateDevices |grep org | cut -c19-)
#################################################################
#***************** MAIN_LOOP_START + SET COUNTER  0 *************
#################################################################
COUNT=0
for DEV in $MM_ENUM
do
    COUNT=`expr $COUNT + 1`
    DEV=$(echo $DEV |sed s:\"::g)
    MM_DEVICE_INFO=$(dbus-send --print-reply --system --dest=$MM $DEV $GET_INFO |grep string | cut -c14-)
    MM_DEVICE_INFO=$(echo $MM_DEVICE_INFO |sed s:\"::g)
    MM_DEVICE_TYPE=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Type" |tail -n1|cut -c25-)
    MM_DEVICE_DRIVER=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Driver" |tail -n1|cut -c25-)
    MM_DEVICE_DRIVER=$(echo $MM_DEVICE_DRIVER |sed s:\"::g)
    MM_DEVICE_MASTER=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"MasterDevice" |tail -n1|cut -c25-)
    MM_DEVICE_MASTER=$(echo $MM_DEVICE_MASTER |sed s:\"::g)
    MM_DATA_DEVICE=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Device" |tail -n1|cut -c25-)
    MM_DATA_DEVICE=$(echo $MM_DATA_DEVICE |sed s:\"::g)
    MM_DATA_DEVICE_PIN_STAT=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"UnlockRequired" |tail -n1|cut -c25-)
    MM_DATA_DEVICE_IP=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"IpMethod" |tail -n1|cut -c25-)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
#########################################################################
# Need to see if device Enabled from MM_DATA_DEVICE_ENABLED true or false
# if false enable the device : else network info not available : WARNING :If connect by Network-Manager this will drop the connection
#########################################################################
    echo
    echo " ----*-----* MM-TEST DEVICE_ENABLE_DISABLE *-----*----"
    echo
    if [ $MM_DATA_DEVICE_ENABLED = "true" ]
    then
    echo " DEVICE ENABLED : true"
    echo " ACTION :disconnect"
    MM_DEVICE_ENABLE=$(dbus-send --print-reply --system --dest=$MM $DEV $MODEM_ENABLE boolean:false)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
    fi
################################################
    if [ $MM_DATA_DEVICE_ENABLED = "false" ]
    then
    echo " DEVICE ENABLED : false"
    echo " ACTION :enable"
    true = "(True)"
    MM_DEVICE_ENABLE=$(dbus-send --print-reply --system --dest=$MM $DEV $MODEM_ENABLE boolean:true)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
    echo " DEVICE ENABLE :$MM_DATA_DEVICE_ENABLED"
    fi
    if [ $MM_DATA_DEVICE_ENABLED = "false" ]
    then
    echo " SETTING ENABLE_DEVICE : fail"
    fi
###################################################
    echo
    echo " ----*-----* MM-TEST DEVICE_INFO *-----*----"
    echo
    echo " DEVICE :$COUNT"
    echo " MASTER_DEVICE :$MM_DEVICE_MASTER"
    echo " ENUMERATED DEVICE TYPE :$MM_DEVICE_TYPE"
    echo " DEVICE INFO :$MM_DEVICE_INFO"
##################################################
    if [ $MM_DEVICE_TYPE -eq 1 ]    
    then
    MODEM_TYPE="GSM"
    echo " MODEM TYPE :$MODEM_TYPE"
    dial="*99#"
    echo " DIAL COMMAND :$dial"
    MM_GSM_NETWORK_INFO=$(dbus-send --print-reply --system --dest=$MM $DEV $GSM_NETWORK_REG_INFO |grep string | cut -c14-)
    MM_GSM_NETWORK_INFO=$(echo $MM_GSM_NETWORK_INFO |sed s:\"::g)
    data=0
    for INFO in $MM_GSM_NETWORK_INFO
        do
            if [ $data -eq 0 ]
                then
                MCC=$(echo $INFO | cut -c -3)
                MNC=$(echo $INFO | cut -c 4-)
                echo " NETWORK MCC :$MCC"
                echo " NETWORK MNC :$MNC"
            fi
##########################################
            if [ $data -eq 1 ]
                then
                echo " PROVIDER   :$INFO"
            fi
##########################################
            if [ $data -eq 2 ]
                then
                echo " REGISTERED :$INFO"
            fi
##########################################
        data=`expr $data + 1`
        done
        echo
    fi
##################################################
    if [ $MM_DEVICE_TYPE -eq 2 ]
        then
        MODEM_TYPE="CDMA"
######### UNTESTED ##############################################
        echo " MODEM TYPE :$MODEM_TYPE"
        dial="#777"
        echo " DIAL COMMAND :$dial"
        MM_DEVICE_ESN=$(dbus-send --print-reply --system --dest=$MM $DEV $Get_Esn)
        echo $MM_DEVICE_ESN
        MM_DEVICE_SERVING_SYSTEM=$(dbus-send --print-reply --system --dest=$MM $DEV $Get_Serving_System |grep uint | cut -c14-) # 
        for INFO in $MM_DEVICE_SERVING_SYSTEM
            do
            echo $INFO
        done

        echo
    fi
##################################################
    echo " ----*-----* MM-TEST MM-INFO *-----*-----"
    echo
    echo " DRIVER :$MM_DEVICE_DRIVER"
    echo " DEVICE :/dev/$MM_DATA_DEVICE"
    echo " PIN STATUS :$MM_DATA_DEVICE_PIN_STAT"
##################################################
    if [ $MM_DATA_DEVICE_IP -eq 0 ]
        then
        echo " ENUMERATED IP METHOD :Use PPP to get the address."
    fi
##################################################
    if [ $MM_DATA_DEVICE_IP -eq 1 ]
        then
        echo " ENUMERATED IP METHOD :Static configuration, the modem will provide IP information."
    fi
##################################################
    if [ $MM_DATA_DEVICE_IP -eq 2 ]
        then
        echo " ENUMERATED IP METHOD :Use DHCP."
    fi
############## END OF UNTESTED ######################### show true then set false
    echo " DEVICE ENABLED :$MM_DATA_DEVICE_ENABLED"
    echo " ACTION :disconnect"
    MM_DEVICE_ENABLE=$(dbus-send --print-reply --system --dest=$MM $DEV $MODEM_ENABLE boolean:false)
    MM_DATA_DEVICE_ENABLED=$(dbus-send --print-reply --system --dest=$MM $DEV $INTERFACE_PROPERTIES.Get string:$MODEM string:"Enabled" |tail -n1|cut -c25-)
    echo " DEVICE ENABLE :$MM_DATA_DEVICE_ENABLED"
###################################################
    echo
    echo
done
#***************** MAIN_LOOP_END ************************
```[FONT=monospace]
[/FONT]also look at these posts
                          #[**75**]("http://ubuntuforums.org/showpost.php?p=11865849&postcount=75")  and               #[**77**]("http://ubuntuforums.org/showpost.php?p=11866235&postcount=77")

---


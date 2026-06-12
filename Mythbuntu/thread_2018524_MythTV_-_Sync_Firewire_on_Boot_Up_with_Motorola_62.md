---
title: "MythTV - Sync Firewire on Boot Up with Motorola 6200"
date: 2012-07-06
forum: Mythbuntu
---

### Post by one30nav on 2012-07-06
This script is a re-purposed version of Steve Adeff's awesome, 6200changer.sh at [http://www.mythtv.org/wiki/Bus_Reset_Safe_Firewire_Priming_Script_with_Channel_Changer](http://www.mythtv.org/wiki/Bus_Reset_Safe_Firewire_Priming_Script_with_Channel_Changer) 
 
What's different, is that it establishes a primed firewire connection on boot up by using  firewire_tester -R to reset the bus until a stable connection is achieved. It primarily benefits those that record HD *through* the firewire cable. 
 
I am aware that MythTV will attempt to regain sync via firewire cable internally, but only when it *starts* recording from a firewire source. When configured, MythTV will attempt to reset the bus internally until data is detected. Outstanding option, but there could be a slight time penalty if your system is not already synced. For instance, you may lose some portion of the first part of a recording while MythTV tries to reset the bus. In mythtv-setup, if you uncheck "Disable Firewire Reset" you get this functionality. 
 
I use *both* the internal bus reset option and this script. Why not get a great sync on boot up and not lose part of a recording? 
 
What the script does: Initially selects a known, unencrypted channel (in my case, channel 2); determines the node that GUID is associated with to run firewire_tester (node 0 or 1); determines stability of the connection with firewire_tester -B; if not stable, runs firewire_tester -R until stable; if necessary, changes to another, known unencrypted channel (channel 24) and tries it for another round. 
 
Initially changing the channel to an unencrypted one is a critical safeguard step to clear a hard lock condition. In the unfortunate case when you try to record via firewire from a 5C encrypted channel and the recording fails, the firewire connection will become hard-locked on that channel until an internal channel change is implemented. A normal reboot will bring you right back to the 5C encrypted channel again and won't clear that lockup. 
 
NOTE: Run plugreport or gscanbus to get your set top box GUID. Paste that GUID into one place in the script below and between the quotation marks. This script uses 6200ch, firewire_tester, and plugreport.

```
#!/bin/bash 
 
GUID="[COLOR=Red]**Your 16-digit GUID goes here**[/COLOR]" 
 
echo "Changing to channel 2" 
6200ch -v -g $GUID 2 
 
#maybe a pause is needed? 
sleep 2 
 
STABILIZE="1" 
COUNT=0 
TOTALCOUNT=0 
STABLECOUNT=0 
 
echo "Stabilizing Firewire Connection!" 
 
#while [ "$STABILIZE" != "Broadcast Fix: Success (already stable)" ] 
while [ $STABLECOUNT -lt 2 ] 
do 
  NODE=`plugreport | grep $GUID | awk '{if (($1 == "Node") && ($4 == "'"0x$GUID"'")) print $2}'` 
  echo "Node: '$NODE'" 
  STABILIZE=`firewire_tester -B -n$NODE|grep "already stable"` 
  if [[ "$STABILIZE" != "Broadcast Fix: Success (already stable)" ]] 
  then 
    echo "Not Stable! Attempt $COUNT" 
    firewire_tester -R 
    sleep 2 
    ((COUNT+=1)) 
    ((TOTALCOUNT+=1)) 
    if [ $TOTALCOUNT -gt 30 ] 
    then 
        echo "FAILED to Stabilize!" 
        exit 1 
    fi 
    if [ $COUNT -gt 10 ] 
    then 
        echo "Changing to channel 24"           
        6200ch -v -g $GUID 24 
        COUNT=0 
        sleep 2 
    fi 
  else 
    echo $STABILIZE 
    ((STABLECOUNT+=1)) 
  fi 
done 
echo "Stable!" 
exit 0
```Save to /usr/bin/firewiresync.sh with editor of choice

Copy to /usr/bin

```
sudo cp firewiresync.sh /usr/bin/
```Make executable

```
sudo chmod 777 /usr/bin/firewiresync.sh
```Edit /etc/rc.local to run firewiresync.sh on bootup. Do, sudo nano /etc/rc.local and make it look like the following:

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
/usr/bin/firewiresync.sh > "/tmp/firewiresync.log" 2>&1  
exit 0
```Make rc.local executable

```
sudo chmod 777 /etc/rc.local
```Reboot your system and nano /tmp/firewiresync.log if you want to view the logfile to see how things went. 
 
Hope this helps. Cheers, Al

---

### Post by one30nav on 2012-07-12
Updated the script: You just need to input the GUID once.

---

### Post by ozite on 2012-07-14
Thanks for sharing this.

---

### Post by nickrout on 2012-07-15
> **one30nav said:**
> Updated the script: You just need to input the GUID once.

The place to post this is probably the mythtv wiki.

---

### Post by one30nav on 2012-07-16
> **nickrout said:**
> The place to post this is probably the mythtv wiki.

Thanks --  makes sense. I'll figure out how to do that and attempt to post this week.

---


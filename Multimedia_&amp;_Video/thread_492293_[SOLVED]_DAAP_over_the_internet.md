---
title: "[SOLVED] DAAP over the internet"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by Megaqwerty on 2007-07-04
I was wondering if anyone knew how to use an SSH tunnel (or any other method really) to connect to a DAAP server over the net with Rhythmbox.

Thanks,

Megaqwerty

---

### Post by Megaqwerty on 2007-08-10
While I wasn't able to pull it off with Rhythmbox, I was able to get it working with Banshee as the client.

I also created a script to automate the process:
```
#!/bin/bash
# SSH Tunnel script for DAAP
# Author: Matthew Beaver (megaqwerty22@gmail.com)
# This script is licenced under the GPL, the GPL can be found in /usr/share/common-licenses/GPL

#Get some variables from the user
zenity --info --text "Please enter your ip address...it will look something like '192.168.1.3' and can be found in the next prompt."
ifconfig | zenity --text-info --height 500 --width 500
ipaddress=`zenity --entry --text "Your ip address:"`
server=`zenity --entry --text "What server do you want to connect to?" --title "Server Name"`
user=`zenity --entry --text "What is your username on $server?"`

#Due to security measures put in place by ssh, we must refer the user to the terminal for password entry
zenity --info --text "Please enter your password in the terminal"
ssh $user@$server -N -f -L $ipaddress:6689:localhost:3689

#Determines whether the command was successful (via return value) and 
RET=$?
if [ $RET -eq 0 ]; then
zenity --info --text "DAAP tunnel successfully established"
else
zenity --info --text "DAAP tunnel was not successfully established"; exit;
fi


#Broadcast port 6689 so that Banshee can see the DAAP server
zenity --info --text "Making the DAAP server visable to Banshee"
avahi-publish-address -v -H `hostname`.local -s "My DAAP server" _daap._tcp. 6689 &

#Does the user have banshee installed? If not, tell them how to install it.
Cmd=`which banshee`;
if [ ! -n $Cmd ]
then
    zenity --info --text "`command-not-found banshee`"
    exit
fi



#If they do have Banshee installed, ask if starting Banshee would be helpful
zenity --question --text "Do you want to start Banshee?"
banshee=$?
if [ $banshee -eq 0 ]; then
banshee &
else
exit
fi
```

---


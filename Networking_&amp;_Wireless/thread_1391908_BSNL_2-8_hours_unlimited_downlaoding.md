---
title: "BSNL 2-8 hours unlimited downlaoding"
date: 2010-01-27
forum: Networking &amp; Wireless
---

### Post by aloke_ranjan on 2010-01-27
Hi Guys I have BSNL dataone broadband connection, Home500 C+ scheme. I want utilize free hours downloading between 2-8hours. My modem is HUAWEI MT841, my system is Ubuntu 9.10 (karmic), Gnome:2.28.1 and Kernel:2.28.1.
I want to enable and disable the modem router by some software. I got following in some forum:

1  RECOMMENDED:- configure your modem to autodial
2  install expect
3  install kalarm in gnome or KDE if it is not already installed, and make sure it run at startup or add the daemon to sessions
4  RECOMMENDED:- Disable internet time server updates (NTP) 
    sudo update-rc.d ntp-server remove
5  create a file router.exp with the following contents
         Code:      
#!/usr/bin/expect -f

set timeout 20
set echo  off

# router user name
set name admin

# router password
set pass admin

# your router IP address
set routerip 192.168.1.1

# Read command as arguments to this script

set switch [ lrange $argv 0 1]

if {$switch == "" } {send_user "usage:ntrouter ONntrouter OFFntrouter validcommandnn"
exit
} else {

   if {$switch == "ON"} {set routercmd "pppoe set transport 1 autoconnect enabledr"
   } else {
   if {$switch == "on"} {set routercmd "pppoe set transport 1 autoconnect enabledr"
   } else {
   if {$switch == "OFF"} {set routercmd "pppoe set transport 1 disabledr"
   } else {
   if {$switch == "off"} {set routercmd "pppoe set transport 1 disabledr"
   } else {
   set switch [ lrange $argv 0 9]
   set routercmd "$switchr"
   }}}}
   
}

send_user "sending router:- $switch n"

#other useful commands 
# set routercmd "pppoe list transportsr"
# set routercmd "pppoe show transport 1r"
# set routercmd "pppoe list transportsr"

# start telnet
spawn telnet $routerip

# send username & password
expect "Login: "
send "$namer"
expect " "
send "$passr"
expect -i "--> "
send $routercmd
send '^]'
expect "telnet> "
send "closer"
send_user "nDone!n"
exit 
6. Enter your router IP, router username, router password in the script
NOTE : (if you have some other router change the script to respond according to the menu that you get while you telnet your router)

7.  Schedule the following commands in kalarm to run in terminal
             Code:      /your_script_location/./router.exp OFF             1:50am and 7:50am ( or fancy your time  ! )
             Code:      /your_script_location/./router.exp ON             2:10am ( or fancy your time ! )
    

I did the above but during the running of the command error message is appearing that "Command file failed to execute" what could be the reason and any modification is suggested. Thank you in advance.

---

### Post by nikefalcon on 2011-04-21
I wrote a script with a simple GUI for such connection scheduling. 
Check it out at [https://launchpad.net/autoconnect](https://launchpad.net/autoconnect).
note that it requires that you have Network manager(v0.8.1 or higher) managing your connections.

---


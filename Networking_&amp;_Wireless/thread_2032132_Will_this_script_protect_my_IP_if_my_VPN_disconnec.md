---
title: "Will this script protect my IP if my VPN disconnects?"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by Stonecold1995 on 2012-07-23
I usually run KTorrent 24/7, and I use BTGuard VPN to protect my IP while it's running.  However, occasionally BTGuard disconnects, and it's very bad when that happens in the middle of the night and KTorrent runs without protection until morning.  Because I can't allow that risk, I've made a small script that kills KTorrent if my external IP address starts leaking (I'm relatively new to bash scripts btw).

```
#!/bin/bash

while true; do
   if [ $(ps -A | grep -c ktorrent) != "0" ]; then
      if [ $(curl -s http://icanhazip.com/) == "xxx.xxx.xxx.xxx (my IP)" ]; then
         killall ktorrent
         sleep 5
         killall -s 9 ktorrent
         (kdialog --title 'Warning!' --msgbox 'KTorrent has been caught running without protection.\nFor your safety, the process ktorrent has been killed.') &
      else
         sleep 60
      fi
   else
      sleep 60
   fi
done
```

My second question is whether using "curl -s http://icanhazip.com/" to get my IP address is a good idea.  After a quick search on Google, I found four *other* ways to do this:
```
1) curl -s http://checkip.dyndns.org/ | sed -e 's/[^[:digit:]|.]//g'
2) curl -s http://automation.whatismyip.com/n09230945.asp
3) curl -s http://ifconfig.me/ip
4) curl -s http://ipogre.com/linux.php | sed -e 's/[^[:digit:]|.]//g'
```

I originally wanted to use #2 (it seemed like the most reliable site), but the site asked scrapers not to go there any more often than once every five minutes (to save bandwidth costs I assume), and my script queries the site every minute, which isn't good.  So I decided to use icanhazip.com instead because it didn't give a limit anywhere.  So my question is, is using *only* icanhazip.com a bad idea?  I tried replacing icanhazip.com with a non-existent site to test how the script would behave if icanhazip.com was ever down.  Unfortunately it only gave an error ("line 5: [: ==: unary operator expected") when it could not reach the site, and it didn't kill KTorrent.

**How can I get my script to kill KTorrent (or preferably retry a few times before doing so) if for any reason it is unable to reach the site?**

---

### Post by Zorael on 2012-07-24
A script is one way of doing it, aye; I use **[http://ifconfig.me](http://ifconfig.me)** for these purposes. If accessed with curl it will only output the IP (and not an entire html page).

I like to keep stuff in separate functions to keep the 'main execution' very simple and straightforward. And ugh I regret starting to mark this up;
```
[COLOR="DimGray"]*#!/bin/bash*[/COLOR]

[COLOR="Green"]BAD_IP=[/COLOR][COLOR="Red"]"xxx.xxx.xxx.xxx"[/COLOR]          [COLOR="DimGray"]*# $1 overrides later*[/COLOR]
[COLOR="Green"]IP_CHECK_URL=[/COLOR][COLOR="Red"]"http://ifconfig.me"[/COLOR] [COLOR="DimGray"]*# modify ip_is_bad() if need be*[/COLOR]
[COLOR="Green"]LOOPDELAY=[/COLOR][COLOR="Red"]60[/COLOR]                      [COLOR="DimGray"]*# how long to rest between checks*[/COLOR]
[COLOR="Green"]KILLDELAY=[/COLOR][COLOR="Red"]5[/COLOR]                       [COLOR="DimGray"]*# how long to wait between sending kill signals*[/COLOR]


[COLOR="RoyalBlue"]ip_is_bad()[/COLOR] **{**
    [COLOR="Purple"]**[**[/COLOR] [COLOR="Red"]"[/COLOR][COLOR="Green"]$([/COLOR]curl -s [COLOR="Red"]"[/COLOR][COLOR="Green"]$IP_CHECK_URL[/COLOR][COLOR="Red"]"[/COLOR][COLOR="Green"])[/COLOR][COLOR="Red"]"[/COLOR] = [COLOR="Red"]"[/COLOR][COLOR="Green"]$BAD_IP[/COLOR][COLOR="Red"]"[/COLOR] ] **&& [COLOR="Purple"]return[/COLOR]** 0 [COLOR="DimGray"]*# abandon ship!*[/COLOR]
    **[COLOR="Purple"]return[/COLOR]** 1
**}**

[COLOR="RoyalBlue"]inform()[/COLOR] **{**
    **[COLOR="DarkOrchid"]kdialog[/COLOR]** --title [COLOR="Red"]'Warning!'[/COLOR] --msgbox \
[COLOR="Red"]'KTorrent has been caught running without protection.\n\
For your safety, the process ktorrent has been killed.'[/COLOR] >/dev/null **&**
**}**

[COLOR="RoyalBlue"]freakout()[/COLOR] **{**
    **[COLOR="DarkOrchid"]kdialog[/COLOR]** --title [COLOR="Red"]'Fatal error!'[/COLOR] --msgbox \
[COLOR="Red"]'Could not close KTorrent, even with SIGKILL!\n\
Permissions issue? Woe is you, regardless.'[/COLOR] >/dev/null **&**
    **[COLOR="Purple"]exit[/COLOR]** 1 [COLOR="DimGray"]*# comment if you want the script looping endlessly*[/COLOR]
**}**

[COLOR="RoyalBlue"]ktorrent_is_running()[/COLOR] **{**
    **[COLOR="DarkOrchid"]pidof[/COLOR]** ktorrent >/dev/null
    **[COLOR="Purple"]return[/COLOR]** [COLOR="Green"]$?[/COLOR]
**}**

[COLOR="RoyalBlue"]kill_it_with_fire()[/COLOR] **{**
    **for** signal **in** 15 9; **do**
        [COLOR="DarkOrchid"]**killall**[/COLOR] -[COLOR="Green"]$signal[/COLOR] ktorrent
        [COLOR="DarkOrchid"]**sleep**[/COLOR] [COLOR="Green"]$KILLDELAY[/COLOR]
        ktorrent_is_running **||** [COLOR="DimGray"]*return 0 # return if no longer running*[/COLOR]
    **done**
    [COLOR="DimGray"]*# we didn't manage to kill it :<*[/COLOR]
    freakout
**}**


[COLOR="DimGray"]*## execution start ##*[/COLOR]

[COLOR="DimGray"]*# if $1 supplied, use it as BAD_IP*[/COLOR]
**[COLOR="DarkOrchid"][[/COLOR]** [COLOR="Red"]"[/COLOR][COLOR="Green"]$1[/COLOR][COLOR="Red"]"[/COLOR] **[COLOR="Purple"]][/COLOR]** **&&** [COLOR="Green"]BAD_IP=[/COLOR][COLOR="Red"]"[/COLOR][COLOR="Green"]$1[/COLOR][COLOR="Red"]"[/COLOR]

**[COLOR="Purple"]echo[/COLOR]** [COLOR="Red"]"Starting loop ..."[/COLOR]

**while** true; **do**
    **(** ktorrent_is_running **&&** ip_is_bad **) &&** kill_it_with_fire
    
    *[COLOR="DimGray"]# the script should sleep in all cases to let the user reconnect[/COLOR]*
    **[COLOR="DarkOrchid"]sleep[/COLOR]** [COLOR="Green"]$LOOPDELAY[/COLOR]
**done**
```

A different approach is to do some iptables wizardry and have traffic that match some criteria always go via a specific gateway. When you lose your VPN connection you should also lose access to its gateway (logically), and then ktorrent just... stops. "Unable to connect", etc etc.

Said criteria can be port ranges, application user/group ownership, and lots more I don't know about. I used the port range approach a while ago.

---

### Post by Stonecold1995 on 2012-07-24
How does this script differ from mine in terms of functionality (aside from using ifconfig.me instead of icanhazip.com)?  Is it more secure or just written differently?]

Is ifconfig.me better than icanhazip.com?  All of those sites I mentioned only either display the IP plain (like "xxx.xxx.xxx.xxx") or with a short message ("<html><head><title>IP Lookup</title></head><body>IP Address: xxx.xxx.xxx.xxx</body></html>"), so the size of index.html isn't really a problem.

My biggest issue still is if for any reason the site goes down, my script will just give an error but won't kill KTorrent.  So how do I get it to do something if there's an error?  The only thing I know of is using "set -e" but that will completely stop the script after any error.  I want my script to be able to try to connect a few more times in the case of an error, and kill KTorrent if it is unable to.  Or better yet, if it is unable to connect to icanhazip.com it'll try to connect to a different site if it's down.

EDIT: I modified my script a little.
```
#!/bin/bash

REAL_IP="xxx.xxx.xxx.xxx" # this is my real IP
CHECK_INTERVAL=120        # how long to wait (in seconds) before checking again
COUNT=0                   # do not change this, it must stay at 0

while true; do
   if [ $(ps -A | grep -c ktorrent) != 0 ]; then
      # this loop adds redundancy to the check in case one of the URLs is down
      let COUNT=COUNT+1
      if [ $COUNT == 1 ]; then
         CHECK_URL="http://icanhazip.com/"
      fi
      if [ $COUNT == 2 ]; then
         CHECK_URL="http://ifconfig.me/ip"
      fi
      if [ $COUNT == 3 ]; then
         CHECK_URL="http://myip.dnsomatic.com/"
      fi
      if [ $COUNT == 4 ]; then
         CHECK_URL="http://automation.whatismyip.com/n09230945.asp"
         COUNT=0
      fi
      if [ $(curl -s "$CHECK_URL") == $REAL_IP ]; then
         # IP address is not hidden, but KTorrent is running!  Sending terminate signal to Ktorrent.  Sleeping 5 seconds.
         killall ktorrent
         sleep 5
         # sending kill signal to KTorrent (in case it is still running).
         killall -s 9 ktorrent
         (kdialog --title 'Warning!' --msgbox 'KTorrent has been caught running without protection.\nFor your safety, the process ktorrent has been killed.') &
      else
         # KTorrent is running, but IP address is hidden.  Sleeping for $CHECK_INTERVAL seconds.
         sleep $CHECK_INTERVAL
      fi
   else
      # KTorrent is not running, so it doesn't matter if the IP is hidden or not.  Sleeping for $CHECK_INTERVAL seconds.
      sleep $CHECK_INTERVAL
   fi
done

```

Is there a more efficient way for me to cycle between URLs?  All those "if"s are getting the script cluttered.  There's *got* to be an easier way to do this in bash, but I'm rather new to bash so I'm using the technique I used when I was still programming with TI-BASIC. :oops:

This is unrelated, but how do you get your code's syntax highlighted like that?  I know how to color text but is there a forum option to do that or do you just color it manually?

---

### Post by Zorael on 2012-07-25
I'm not trying to impose my habits onto you, no worries. :3 And yes, I started marking it up manually, and promptly regretted it a few minutes in. >.< An auto-markup feature would be glorious, but alas.

Breaking out functionality into separate functions just strikes me as easier to manage. You know what bits happen where, and in case something requires a lots of nested **if** clauses, placing some in a separate function lowers your level of indentation.

As for long lists of if-else if-else if-else, you could use **case** (switch in some other languages). man case. Like so;
```
for i in $(seq 1 5); do
    # $i will be 1, then 2, then 3, then 4, then 5. man seq
    case $i in
        1) HOST="icanhazip.com" ;;
        2) HOST="ifconfig.me/ip" ;;
        3) HOST="myip.dnsomatic.com" ;;
        4) HOST="automation.whatismyip.com/n09230945.asp" ;;
        *) ;; # unexpected $i; do we care? throw error? continue/break? etc
    esac
    echo "curl -s $HOST etc etc"
done
```

Ignoring the function-thing, when you want to iterate through something you're most often better off using **for**.
[list][*]You could depend on an integer, and use a **case** clause as above. You could technically also use a while-loop and manually increment a variable (eg **$COUNT**), but for and seq would automate that.
[*]You could also put all your hosts-to-curl in a variable, with addresses separated by some character (saved in [**$IFS**](http://en.wikipedia.org/wiki/Internal_field_separator)) that's invalid to URLs (and won't conflict with valid addresses, like / would). Compare **$PATH** which separates paths with colons.
[*]You could also [hardcode](http://en.wikipedia.org/wiki/Hard_coding) the hosts into the for statement, which is technically what $(seq 1 5) does;
```
for address in icanhazip.com ifconfig.me/ip myip.dnsomatic.com automation.whatismyip.com/n09230945.asp; do
    [...]
done
```Hardcoding values is seldom a good thing to do, though. Defining them as variables uptop in one spot makes them easy to change, such as if you want to add another host or modify your real IP. Much like functions! ;3[/list]

Another example, not as easy on the eyes this time;
```
#!/bin/bash

REAL_IP="xxx.xxx.xxx.xxx" # this is my real IP
IFS='|'                   # separator between hosts to probe for current ip
HOSTS="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"
CHECK_INTERVAL=120        # how long to wait (in seconds) before checking again

while true; do
    if [ $(ps --user $UID -o comm | grep -c ktorrent) -gt 0 ]; then
        # one or more instances of ktorrent running (owned by current user)
        # so let's iterate through all address entries in $HOSTS as separated
        # by $IFS, and resolve our IP through them

        for address in $HOSTS; do
            # so address will be icanhazip.com, then ifconfig.me/ip, etc etc

            # the [ command uses a single = for comparison
            if [ "$(curl -s "$address")" = "$REAL_IP" ]; then
                # ruh roh, host reported your real ip
                # Sending terminate signal to Ktorrent.  Sleeping 5 seconds.
                killall ktorrent
                sleep 5

                # sending kill signal to KTorrent (in case it is still running).
                killall -s 9 ktorrent
                (kdialog --title 'Warning!' --msgbox 'KTorrent has been caught running without protection.\nFor your safety, the process ktorrent has been killed.') &

                # break out all the way down to sleep $CHECK_INTERVAL
                break
            else
                # the else case here is just 'your real IP wasn't returned',
                # which either means that it returned your VPN's IP, or that
                # you simply couldn't get a good answer from the host.
                # since the point of using multiple hosts is to ward yourself
                # incase the host is down, it's probably just smarter to let
                # the 'for address' loop continue rather than break out and
                # continue the 'while true' loop.
                # ...you *could* craft a regex expression to see if what you get
                # is an IP, though. that'd be fun!
                sleep 5
            fi
        done
    fi

    # you want to sleep for $CHECK_INTERVAL in all cases before it reloops
    # (cases being ktorrent not running, running but not real IP, running and real IP)
    # so we only need one here at the very bottom
    sleep $CHECK_INTERVAL
done
```

---

### Post by Stonecold1995 on 2012-07-25
So then would this work?
```
#!/bin/bash

REAL_IP="xxx.xxx.xxx.xxx" # this is my *real* external IP address
CHECK_INTERVAL=120        # how long to wait (in seconds) before checking again
IFS='|'                   # separator between hosts to probe for current ip
HOSTS="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"

while true; do
   if [ $(ps --user $UID -o comm | grep -c ktorrent) != 0 ]; then
      # this loop adds redundancy to the check in case one of the URLs is down
      for CHECK_URL in $HOSTS; do
         if [ $(curl -s "$CHECK_URL") == $REAL_IP ]; then
            # IP address is not hidden, but KTorrent is running!  Sending terminate signal to Ktorrent.  Sleeping 5 seconds.
            killall ktorrent
            sleep 5
            # sending kill signal to KTorrent (in case it is still running).
            killall -s 9 ktorrent
            (kdialog --title 'Warning!' --msgbox 'KTorrent has been caught running without protection.\nFor your safety, the process ktorrent has been killed.') &
            break
         else
            # KTorrent is running, but IP address is hidden.  Sleeping for $CHECK_INTERVAL seconds.
            sleep $CHECK_INTERVAL
         fi
      done
   fi
      # KTorrent is not running, so it doesn't matter if the IP is hidden or not.  Sleeping for $CHECK_INTERVAL seconds.
      sleep $CHECK_INTERVAL
 done
```



Will this check four times in a row if KTorrent is running?  If so, would it be a good idea to do something like this instead?
```
#!/bin/bash

REAL_IP="xxx.xxx.xxx.xxx" # this is my *real* external IP address
CHECK_INTERVAL=120        # how long to wait (in seconds) before checking again
IFS='|'                   # separator between hosts to probe for current ip
HOSTS="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"

while true; do
   if [ $(ps --user $UID -o comm | grep -c ktorrent) != 0 ]; then
      # this loop adds redundancy to the check in case one of the URLs is down
      for CHECK_URL in $HOSTS; do
         if [ $(curl -s "$CHECK_URL") == $REAL_IP ]; then
            # IP address is not hidden, but KTorrent is running!  Sending terminate signal to Ktorrent.  Sleeping 5 seconds.
            killall ktorrent
            sleep 5
            # sending kill signal to KTorrent (in case it is still running).
            killall -s 9 ktorrent
            (kdialog --title 'Warning!' --msgbox 'KTorrent has been caught running without protection.\nFor your safety, the process ktorrent has been killed.') &
            break
         else
            [B]if [ $(ps --user $UID -o comm | grep -c ktorrent) == 0 ]; then
               # KTorrent is no longer running, so there is no reason to continue checking my IP
               break
            fi[/B]
            # KTorrent is running, but IP address is hidden.  Sleeping for $CHECK_INTERVAL seconds.
            sleep $CHECK_INTERVAL
         fi
      done 
   fi
      # KTorrent is not running, so it doesn't matter if the IP is hidden or not.  Sleeping for $CHECK_INTERVAL seconds.
      sleep $CHECK_INTERVAL
 done
```

---

### Post by Zorael on 2012-07-26
Certainly it would work! I'm just being picky.

```
if [ $(curl -s "$CHECK_URL") **[COLOR="Red"]==[/COLOR]** $REAL_IP ]; then
```
A bit pedantic, but remember that **[** technically wants a single = for string comparison. From man **[**;
```
***[...]***
       STRING1 = STRING2
              the strings are equal

       STRING1 != STRING2
              the strings are not equal

       INTEGER1 -eq INTEGER2
              INTEGER1 is equal to INTEGER2

       INTEGER1 -ge INTEGER2
              INTEGER1 is greater than or equal to INTEGER2

       INTEGER1 -gt INTEGER2
              INTEGER1 is greater than INTEGER2

       INTEGER1 -le INTEGER2
              INTEGER1 is less than or equal to INTEGER2

       INTEGER1 -lt INTEGER2
              INTEGER1 is less than INTEGER2

       INTEGER1 -ne INTEGER2
              INTEGER1 is not equal to INTEGER2***[...]***
```
Also if you ever want to compare variables where one *may* be completely empty, always encase at least the could-be-empty one in quotes.
```
unset A
# $A is completely empty

if [ $A ];   then echo "this works, but only because it allows for..."; fi
if [ ];      then echo "this, which is exactly the same as the above"; fi
if [ ! $A ]; then echo "this also works, but again only because it allows for..."; fi
if [ ! ];    then echo "this"; fi

if [ $A = "abc" ]; then echo "this does *not* work as it is the same as the following:"; fi
if [ = "abc" ];    then echo "throws error 'unary operator expected'"; fi
if [ "abc" = $A ]; then echo "this doesn't work either, for self-explanatory reasons"; fi
if [ "abc" = ];    then echo "you guessed it"; fi

if [ "$A" = "abc" ]; then echo "always safe"; fi
if [ "" = "abc" ];   then echo "always safe, translates to exactly the same as above"; fi
if [ "abc" = "" ];   then echo "always safe"; fi

# assuming $A was to be a number (but it's suddenly empty), you get the same thing with the integer operands
# $A is still unset, mind
if [ $A -gt 0 ]; then echo "doesn't work, exactly the same as below"; fi
if [ -gt 0 ];    then echo "as above"; fi
if [ 0 -gt $A ]; then echo "..."; fi
if [ 0 -gt ];    then echo "..."; fi
# so while you'd think you could do "$A" -gt 0, that's comparing a string to a number and doesn't work either.
# you could only avoid this by using default values, but that's overthinking things.
# I imagine the integer operands are faster, but everything is slow in shell scripting anyway, so might as well stick to strings.
```

```
         else
            # KTorrent is running, but IP address is hidden.  Sleeping for $CHECK_INTERVAL seconds.
            sleep $CHECK_INTERVAL
         fi
```
I think it's a bit much to sleep for the entire $CHECK_INTERVAL here. If so, you might as well remove the one at the bottom. Consider how it would run in a scenario where your VPN connection is fine;
```
while true
    if ktorrent running
        check host 1
            IP is okay, sleep 60 seconds
        check host 2
            IP is okay, sleep 60 seconds
        check host 3
            IP is okay, sleep 60 seconds
        check host 4
            IP is okay, sleep 60 seconds
    sleep 60 seconds
repeat
```
After host 4 it would sleep 120 seconds, and if you closed ktorrent after checking host 1 the script would still check all the other hosts with the entirety of $CHECK_INTERVAL inbetween, before checking again if ktorrent is still running. (Much like you seem to be onto yourself.)

If you want to repeat checks for whether ktorrent is running, consider just changing the order of the loops.
```
for CHECK_URL in $HOSTS; do
    if [ $(ps --user $UID -o comm | grep -c ktorrent) != 0 ]; then
        # ...
    fi
    sleep $CHECK_INTERVAL
done
```
This would change the script behavior from "do a batch of host checks and then sleep $CHECK_INTERVAL" to "do a host check, then sleep for $CHECK_INTERVAL before continuing with the next host". So it's up to preference! Assuming the current behavior, ktorrent closing after the loop has started has less of an impact if you just have it sleep ~5 seconds inbetween hosts (and then increase $CHECK_INTERVAL if you think you want a longer delay between checks).

If you want to keep the current order of loops, consider breaking out the ps | grep ktorrent check into its own function to reuse code.

---

### Post by Stonecold1995 on 2012-07-26
Okay, so this looks like it's probably the final version.  Does it look good?

```
#!/bin/bash

# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.

REAL_IP="xxx.xxx.xxx.xxx"       # this is my *real* external IP address
CHECK_INTERVAL=60               # how long to wait (in seconds) before checking again
IFS='|'                         # separator between hosts to probe for current ip
CLIENT="ktorrent"               # the name of the torrent client's parent process
ALLOW_MULTIPLE=0                # whether to allow multiple running instances of not
LOCKFILE="/tmp/.vpn_check.lock" # location of the lock file for this script to use
HOSTS="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"  # what sites to use to check the external IP

# make sure only one instance of the script is running
if [ $ALLOW_MULTIPLE = 0 ]; then
   if [ -e $LOCKFILE ]; then
      kdialog --error "Only one instance of the script can be running at a time.  If you believe this is a mistake, remove $LOCKFILE and try again."
      exit 1
   fi
   # set up lockfile and trap relevant signals
   echo -e "$(date)\n$0\nPID $$" > $LOCKFILE
   trap "rm -f $LOCKFILE; exit $?" INT TERM EXIT
fi

while true; do
   if [ $(pgrep -c $CLIENT) != 0 ]; then
      # this loop adds redundancy to the check in case one or more of the servers are down
      for CHECK_URL in $HOSTS; do
         if [ $(curl -s "$CHECK_URL") = $REAL_IP ]; then
            # IP address is not hidden, but your torrent client is running!  Sending terminate signal to the client.  Sleeping 5 seconds.
            killall $CLIENT
            sleep 5
            # sending kill signal to the client (in case it is still running).
            killall -s 9 $CLIENT
            (kdialog --title 'Warning!' --msgbox 'Your torrent client has been caught running without protection.\nFor your safety, the process ktorrent has been killed.') &
            break
         else
            if [ $(pgrep -c $CLIENT) = 0 ]; then
               # The torrent client is no longer running, so there is no reason to continue checking my IP
               break
            fi
            # The torrent client is running, but my IP address is hidden.  Sleeping for $CHECK_INTERVAL seconds.
            sleep $CHECK_INTERVAL
         fi
      done
   fi
      # The torrent client is not running, so it doesn't matter if my IP hidden or not.  Sleeping for $CHECK_INTERVAL seconds.
      sleep $CHECK_INTERVAL
done
```

I think I might eventually add a logging feature so it'll tell me when my IP changes or the state of KTorrent changes in a log file.  Any tips on how to do that or do you think this is good?

---

### Post by Stonecold1995 on 2012-08-02
This is my script so far, now that I've added logging and several other features:
```
#!/bin/bash

# variables to control the behavior of this script
real_ip="xxx.xxx.xxx.xxx"       # this is my *real* external IP address
check_interval=60               # how long to wait (in seconds) before checking again
IFS='|'                         # separator between hosts to probe for current ip
client="ktorrent"               # the name of the torrent client's parent process
allow_multiple=0                # whether to allow multiple running instances of not
lockfile="/tmp/.vpncheck.lock"  # location of the lock file for this script to use
max_logs=5                      # maximum number of logs to keep at once before compressing and archiving them
log_dir="/home/alex/.vpncheck"   # directory to put log files in
log_name="vpncheck_log_$(date +%a_%b_%d_%T_%Z_%Y).txt"  # format to name logfiles
hosts="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"  # what sites to use to check the external IP

# command line options
if [ "$1" != "" ]; then
   if [ "$1" = "--help" -o "$1" = "-h" ]; then
      echo "
This is a little script which checks to see if your IP address is hidden so you can
torrent safely.  It will periodically compare your real IP address with your visible
IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
kills you torrent client to prevent it from leaking your IP to the MAFIAA.

This script will NOT protect you if you don't already have some kind of VPN or proxy
set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
your real IP changes and you don't edit this script it will be pretty much useless
(e.g. if you have a laptop and you use a different router for any reason, such as going
to a friend's house, a public cafe, you get a new router, etc).


Command line options:

      -h, --help    display this help


"
      exit 0
   fi
   echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
   exit 1
fi

# logging function
function log {
   echo -n "<$(date)>     " >> "$log_file"
   echo -e $1 >> "$log_file"
}

# prepare log directory and create a new log file
mkdir -p "$log_dir"
log_file="$log_dir/$log_name.tmp.$$"
echo "
Script started on $(date) with a process name of $0 (PID $$)
Real external IP address is set to $real_ip.
Checking actual external IP address every $check_interval seconds.
Target process is $client.


" >> "$log_file"

# make sure only one instance of the script is running if allow_multiple is set to 0
if [ $allow_multiple -eq 0 ]; then
   if [ -e "$lockfile" ]; then
      log "Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run."
      kdialog --error "Only one instance of the script can be running at a time.  If you believe this is a mistake, remove $lockfile and try again."
      rename 's/\'.tmp.$$'$//' "$log_file"
      exit 1
   fi
   echo -e "$(date)\n$0\nPID $$" > "$lockfile"
   log "allow_multiple is set to 0.  Lockfile has been generated."
else
   if [ -e "$lockfile" ]; then
      log "Another instance of this script appears to be running already, but allow_multiple is set to 1.  This script will continue to run, but please note that this may cause problems."
   fi
   # make sure the script won't remove the lockfile for another instance if allow_multiple is set to 1
   lockfile=
fi

# trap relevant signals
function finish_up {
   log "Script recieved signal and will now terminate.  Removing $lockfile."
   rename 's/\'.tmp.$$'$//' "$log_file"
   cd "$log_dir"
   mkdir -p old
   if [ $(ls -l *.txt | wc -l) -gt $max_logs ]; then
      gzip -9 $(ls -1t *.txt | tail -1)
      mv *.gz old
   fi
   rm -f "$lockfile"
   exit $?
}
trap finish_up SIGHUP SIGINT SIGTERM

# state logging function
function check_state {
   if [ "$state" != "$last_state" ]; then
      case "$state" in
         1) log "$client is no longer running.  IP monitoring will be turned off."
            ;;
         2) log "$client is running, but IP is hidden.  Current IP address is $current_ip."
            ;;
         3) log "WARNING: The process $client has been caught running without protection.  It has been killed."
            ;;
      esac
   fi
   last_state=$state
}

# STATES:
#  1: client is not running, IP monitoring can be off
#  2: client is running, and IP is hidden
#  3: client is running, but IP is NOT hidden (!)
while true; do
   if [ $(pgrep -c $client) -ne 0 ]; then
      # this loop adds redundancy to the check in case one or more of the servers are down
      while true; do
         for check_url in $hosts; do
            current_ip=$(curl -s $check_url)
            if [ "$check_url" = "" ]; then
               log "WARNING: Could not connect to $check_url.  Moving on..."
            fi
            if [ "$current_ip" = "$real_ip" ]; then
               # IP address is not hidden, but your torrent client is running!  Sending terminate signal to the client.
               state=3
               check_state
               killall -q $client
               sleep 3
               # sending kill signal to the client (in case it is still running)
               killall -qs 9 $client
               kdialog --title 'Warning!' --msgbox "The process $client has been caught running without protection.\nFor your safety, $client has been killed." &
               break
            else
               if [ $(pgrep -c $client) -eq 0 ]; then
                  # the torrent client is no longer running, so there is no reason to continue checking my IP
                  state=1
                  check_state
                  break
               fi
               # the torrent client is running, but my IP address is hidden
               state=2
               check_state
               sleep $check_interval
            fi
         done
         if [ $state -eq 1 ]; then
            break
         fi
      done
   fi
      # the torrent client is not running, so it doesn't matter if my IP hidden or not
      sleep $check_interval
done

```

If anyone sees something I missed or a way to make the code more efficient (or smaller) please tell me.  I'm currently trying to learn how to use getopt so I can pass on arguments to the script, but it's [really confusing]("http://www.pictureshack.us/images/48777_IM_CONFUS.jpg").

---

### Post by Zorael on 2012-08-07
Hello again!

See the attached file for some comments and examples. It's sadly not based on the one in your new/edited post, but the state before that (that I saved to disk). :/

From your newest paste;
```
***[...]***
            else
               if [ $(pgrep -c $client) -eq 0 ]; then
                  # the torrent client is no longer running, so there is no reason to continue checking my IP
                  **state=1**
                  check_state
                  [COLOR="Red"]**break**[/COLOR]
               fi
               # the torrent client is running, but my IP address is hidden
               state=2
               check_state
               sleep $check_interval
            fi
         done
         if [ **$state -eq 1** ]; then
            [COLOR="red"]**break**[/COLOR]
         fi
***[...]***
```
You can specify how many layers to break directly, simply with '**break *n***'. Like so;
```
            else
               if [ $(pgrep -c $client) -eq 0 ]; then
                  # the torrent client is no longer running, so there is no reason to continue checking my IP
                  state=1
                  check_state
                  [b]# break two levels
                  [COLOR="green"]break _2_[/B][/color]
               fi
               # the torrent client is running, but my IP address is hidden
               state=2
               check_state
               sleep $check_interval
            fi
         done
         [I][COLOR="Gray"]#if [ $state -eq 1 ]; then
         #   break
         #fi[/COLOR][/I]
```

Looks pretty good otherwise!

You may want to try to lower indentation a bit, perhaps. You're at 6 levels at your deepest, and a maximum of 4 is a decent target. I admit it's not always easy (like when you're nesting while-loop-if-else), but you can get pretty far by just separating your if-elses to single ifs, and use **continue** (or break) when you reach the end of them. And, you know, break out functionality into functions. :3

---

### Post by Stonecold1995 on 2012-08-09
Is there a way for me to have multiple clients and IP addresses to monitor so something like this is supported?

```
client="ktorrent|kvirc|nmap"
real_ip="xxx.xxx.xxx.xxx|yyy.yyy.yyy.yyy"
```

---

### Post by Zorael on 2012-08-11
Certainly! You would just need to change the logic you use to detect if your clients' processes are running, and iterate through all your real/unmasked IPs once per host response.

See the attached example. I deleted earlier comments to unclutter it some.

I also removed the lockfile behavior (in this working copy!), so ignore those missing bits and pieces. (I'm not sure if that functionality is worth the code complexity it incurs?)

---

### Post by Zorael on 2012-08-12
Also, don't forget this very simple solution.

---

### Post by Stonecold1995 on 2012-08-12
> **Zorael said:**
> Also, don't forget this very simple solution.

I don't have tap0 (I'm on a wireless network).  Would tun0 work instead?  I'm still kind of new to this so I don't know much about these network devices aside from the basics of what they are.

---

### Post by Zorael on 2012-08-13
Likely, aye.

My Anonine OpenSSH VPN connection installs itself as a virtual tun0 interface, while when I used a PPTP-based service it ended up as ppp0.

What does it show up as in the network manager widget?

---

### Post by Stonecold1995 on 2012-08-13
It just says "not available" on all the fields.

Also, you use Anonine?  How did you get it to work?  For some reason, the site won't let me sign in (it says I'm using the wrong username or password), and it won't respond to the "I forgot my password" via e-mail, and they won't respond to my question in the "Contact" section, *and* the VPN simply won't connect (it says there's an authentication failure).  This also happened with VPNTunnel, although I can log into those just fine, but the VPN won't connect.  Just wondering if you ran into any of those problems...

---

### Post by Zorael on 2012-08-13
No, it has worked fine for me. I used the PPTP service at first, and it was lesson in frustration to get it working. The support for the protocol in the network interface widget seems to have improved since though, but for a time I fell back to using KVpnc (which crashed regularly), and after that the terminal tool (pppd call, if memory serves).

Now with their OpenSSH offering I just downloaded the .ovpn and .ca.crt files from their site, hit Import in the networking settings, configured passwords etc, and then it Just Worked. I'd recommend it heartily over PPTP. Refer to your syslog for output on the connection process.

Any change of their mails being blocked/filtered as spam? Also their twitter feed mentions them having had problems with captcha back in late July, but outside of that I don't know.

edit:
> **Stonecold1995 said:**
> It just says "not available" on all the fields.
What do you mean by this?

---

### Post by Stonecold1995 on 2012-08-13
Is this what you meant?  Otherwise I don't know where the widget is...

---

### Post by Zorael on 2012-08-13
All right.

I guess I forgot to ask; do you have the necessary network-manager packages for your VPN type installed?
```
# regex voodoo!
zorael:laughlyn ~$ apt-cache search network-manager- | grep -v -- '-\(dbg\|dev\|gnome\) - ' | sed 's:^\(network-manager-.\+\) -:[**b][**url=apt\://\1\]\1[**/url\][**/b] -:g'
**[network-manager-pptp](apt://network-manager-pptp)** - network management framework (PPTP plugin core)
**[network-manager-iodine](apt://network-manager-iodine)** - network management framework (iodine plugin core)
**[network-manager-kde](apt://network-manager-kde)** - transitional package for plasma-widget-networkmanagement
**[network-manager-openconnect](apt://network-manager-openconnect)** - network management framework (OpenConnect plugin)
**[network-manager-openvpn](apt://network-manager-openvpn)** - network management framework (OpenVPN plugin core)
**[network-manager-strongswan](apt://network-manager-strongswan)** - network management framework (strongSwan plugin)
**[network-manager-vpnc](apt://network-manager-vpnc)** - network management framework (VPNC plugin core)
strongswan-nm - strongSwan plugin to interact with NetworkManager
```

And again, see if there is anything of interest in the log files. Yours probably looks a bit different, but it should (when it's working) say something like this;
```
Aug 13 11:21:12 laughlyn NetworkManager[387]: <info> Starting VPN service 'openvpn'...
Aug 13 11:21:12 laughlyn NetworkManager[387]: <info> VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 13212
Aug 13 11:21:12 laughlyn NetworkManager[387]: <info> VPN service 'openvpn' appeared; activating connections
Aug 13 11:21:12 laughlyn NetworkManager[387]: <info> VPN plugin state changed: starting (3)
Aug 13 11:21:12 laughlyn NetworkManager[387]: <info> VPN connection 'anonine' (Connect) reply received.
Aug 13 11:21:12 laughlyn nm-openvpn[13214]: OpenVPN 2.2.1 x86_64-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [eurephia] [MH] [PF_INET6] [IPv6 payload 20110424-2 (2.2RC2)] built on Mar 30 2012
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: LZO compression initialized
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: RESOLVE: NOTE: openvpn-4.anonine.net resolves to 25 addresses
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: UDPv4 link local: [undef]
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: UDPv4 link remote: [AF_INET]xxx.xxx.xxx.xxx:1201
Aug 13 11:21:13 laughlyn nm-openvpn[13214]: [atlas] Peer Connection Initiated with [AF_INET]xxx.xxx.xxx.xxx:1201
Aug 13 11:21:15 laughlyn nm-openvpn[13214]: TUN/TAP device tap0 opened
Aug 13 11:21:15 laughlyn nm-openvpn[13214]: /usr/lib/NetworkManager/nm-openvpn-service-openvpn-helper tap0 1500 1574 xxx.xxx.xxx.xxx 255.255.255.128 init
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> VPN connection 'anonine' (IP Config Get) reply received.
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> VPN Gateway: xxx.xxx.xxx.xxx
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Internal Gateway: xxx.xxx.xxx.xxx
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Tunnel Device: tap0
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Internal IP4 Address: xxx.xxx.xxx.xxx
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Internal IP4 Prefix: 25
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Internal IP4 Point-to-Point Address: 0.0.0.0
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Maximum Segment Size (MSS): 0
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Forbid Default Route: no
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Internal IP4 DNS: xxx.xxx.xxx.xxx
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> Internal IP4 DNS: xxx.xxx.xxx.xxx
Aug 13 11:21:15 laughlyn NetworkManager[387]: <info> DNS Domain: '(none)'
Aug 13 11:21:15 laughlyn nm-openvpn[13214]: Initialization Sequence Completed
Aug 13 11:21:15 laughlyn avahi-daemon[7077]: Joining mDNS multicast group on interface tap0.IPv4 with address xxx.xxx.xxx.xxx.
Aug 13 11:21:15 laughlyn avahi-daemon[7077]: New relevant interface tap0.IPv4 for mDNS.
Aug 13 11:21:15 laughlyn avahi-daemon[7077]: Registering new address record for xxx.xxx.xxx.xxx on tap0.IPv4.
Aug 13 11:21:16 laughlyn NetworkManager[387]: <info> (tap0): writing resolv.conf to /sbin/resolvconf
Aug 13 11:21:16 laughlyn NetworkManager[387]: <info> VPN connection 'anonine' (IP Config Get) complete.
Aug 13 11:21:16 laughlyn NetworkManager[387]: <info> Policy set 'anonine' (tap0) as default for IPv4 routing and DNS.
Aug 13 11:21:16 laughlyn dbus-daemon[305]: dbus[305]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 13 11:21:16 laughlyn dbus[305]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Aug 13 11:21:16 laughlyn NetworkManager[387]: SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap0, iface: tap0)
Aug 13 11:21:16 laughlyn NetworkManager[387]: SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap0, iface: tap0): no ifupdown configuration found.
Aug 13 11:21:16 laughlyn NetworkManager[387]: <warn> /sys/devices/virtual/net/tap0: couldn't determine device driver; ignoring...
Aug 13 11:21:16 laughlyn NetworkManager[387]: <info> VPN plugin state changed: started (4)
Aug 13 11:21:16 laughlyn dbus-daemon[305]: dbus[305]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 13 11:21:16 laughlyn dbus[305]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Aug 13 11:21:19 laughlyn dnsmasq[31791]: reading /var/run/dnsmasq/resolv.conf
Aug 13 11:21:19 laughlyn dnsmasq[31791]: using nameserver xxx.xxx.xxx.xxx#53
Aug 13 11:21:19 laughlyn dnsmasq[31791]: using nameserver xxx.xxx.xxx.xxx#53
Aug 13 11:21:19 laughlyn dnsmasq[31791]: using nameserver xxx.xxx.xxx.xxx#53
```

---

### Post by Stonecold1995 on 2012-08-13
There were a few that weren't installed, and I installed them now.

How do I prune the log to only show messages related to VPN?

---

### Post by Zorael on 2012-08-13
Hmm.

```
*# easy version*
$ grep -i '*network*' **/var/log/syslog**  *# or wherever it saves its logs; /var/log/* if nothing else*

*# wizard version*
$ grep -i '*vpn\|network.\?manager\|ppt\?p*' **/var/log/syslog**  *# likewise*
```

---

### Post by Stonecold1995 on 2012-08-13
OK, so this is the output:

```
alex@kubuntu:~$ grep -i 'vpn\|network.\?manager\|ppt\?p' /var/log/syslog
Aug 13 03:00:41 kubuntu NetworkManager[1768]: <info> VPN: loaded org.freedesktop.NetworkManager.openconnect
Aug 13 03:03:18 kubuntu NetworkManager[1768]: <info> VPN: loaded org.freedesktop.NetworkManager.strongswan
Aug 13 03:03:46 kubuntu NetworkManager[1768]: <info> VPN: loaded org.freedesktop.NetworkManager.vpnc
Aug 13 03:15:48 kubuntu named[13063]: error (network unreachable) resolving 'openvpn.net/A/IN': [not sure if this part is sensitive so I removed it]
Aug 13 03:15:49 kubuntu named[13063]: error (network unreachable) resolving 'openvpn.net/DS/IN': [not sure if this part is sensitive so I removed it]
```

---

### Post by Zorael on 2012-08-13
It's not loading **[openvpn](apt://network-manager-openvpn)** though; did you miss that one? Or was it already loaded?

Regardless, those **/A/IN** and **/DS/IN** bits don't look healthy, but perhaps it may just be a display error.

Open up **/etc/NetworkManager/system-connections/*nameofyourconnection*** in a (root) text editor and make sure the **remote=** line doesn't have that garbage after the openvpn.net host.

```

[vpn]
service-type=org.freedesktop.NetworkManager.openvpn
connection-type=password
password-flags=1
**remote=openvpn-4.anonine.net**
comp-lzo=yes
proto-tcp=no
tap-dev=yes
reneg-seconds=0
port=1201
mssfix=no
username=XXXXXX
ca=/home/zorael/.misc/anonine.ca.crt
```

---

### Post by Stonecold1995 on 2012-08-13
It must have been already loaded.  I know openvpn is installed though.

The config file on my drive looks the same as yours (aside from the location, etc).

---

### Post by Zorael on 2012-08-13
Maybe it's just a display bug, then. Or maybe it's some ipv4 internal jargon I don't know about. Alternatively -- VERY unlikely -- maybe you have weird linebreaks in your definitions file?

```
$ sudo cat -A /etc/NetworkManager/system-connections/*nameofconnection* | grep '^remote'
remote=openvpn.net**[color=green]$[/color]**  *# there should be a dollar sign at the end, if it says **[color=red]^M$[/color]** that's wrong* and very confusing why it could ever have happened
```

Anyway, can you ping openvpn.net? Else you may have stale routes after so many connection attempts. Try disconnecting completely and then reconnect.

---

### Post by Stonecold1995 on 2012-08-13
```
alex@kubuntu:~$ sudo cat -A /etc/NetworkManager/system-connections/* | grep '^remote'
remote=openvpn-4.anonine.net$
remote=vpn.btguard.com$
remote=anna.vpntunnel.se$
```

And yes, I can ping openvpn.net.

---

### Post by Zorael on 2012-08-24
Then I'm out of ideas.

You could try to manually connect from the terminal (with the openvpn cli tool) and see if it outputs any particular error not visible in the logs.

---

### Post by Stonecold1995 on 2012-08-24
Hmm.  Oh well then.  I guess I'll continue using BTGuard, although I might change to IPreditor.

Anyways, I think I've completed my script.

```
#!/bin/bash

#                ###############################################
#                             VPNCHECK by Stonecold
#                ###############################################
#
# This is a little script which checks to see if your IP address is hidden so you can
# torrent safely.  It will periodically compare your real IP address with your visible
# IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
# kills you torrent client to prevent it from leaking your IP to the MAFIAA.
#
# This script will NOT protect you if you don't already have some kind of VPN or proxy
# set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
# of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
# open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
# your real IP changes and you don't edit this script it will be pretty much useless
# (e.g. if you have a laptop and you use a different router for any reason, such as going
# to a friend's house, a public cafe, you get a new router, etc).
#
#
# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.
#
# Last modified: August 23, 2012
#
# TODO: add debug variable instead of doing bash -x ./script.sh
# TODO: test the script under root
# TODO: add function to check if required programs are installed (e.g. curl)

# variables to control the behavior of this script
real_ip="xxx.xxx.xxx.xxx"       # this is my *real* external IP address
check_interval=60               # how many seconds to wait before checking again
IFS='|'                         # separator between hosts to probe for current ip
client="ktorrent"               # the name of the torrent client's parent process
allow_multiple=0                # whether to allow multiple running instances of not (0=no, 1=yes)
lockfile="/tmp/.vpncheck.lock"  # location of the lock file for this script to use
keep_logs=1                     # whether to log events and activities (0=no, 1=yes)
max_logs=5                      # maximum number of logs to keep at once before compressing and archiving them (TODO: make max archived logs)
log_dir="/home/alex/.vpncheck"  # directory to put log files in
log_name="vpncheck_log_$(date +%a_%b_%d_%T_%Z_%Y).txt"  # format to name logfiles
hosts="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"  # what sites to use to check the external IP

# command line options
if [ "$1" != "" ]; then
   if [ "$1" = "--help" -o "$1" = "-h" ]; then
      cat << _EOF

               ###############################################
                            VPNCHECK by Stonecold
               ###############################################

This is a little script which checks to see if your IP address is hidden so you can
torrent safely.  It will periodically compare your real IP address with your visible
IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
kills you torrent client to prevent it from leaking your IP to the MAFIAA.

This script will NOT protect you if you don't already have some kind of VPN or proxy
set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
your real IP changes and you don't edit this script it will be pretty much useless
(e.g. if you have a laptop and you use a different router for any reason, such as going
to a friend's house, a public cafe, you get a new router, etc).


Command line options:

      -h, --help    display this help


This script is licensed under the WTFPL, Version 2.
_EOF
      exit 0
   fi
   echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
   exit 1
fi

# prepare log directory and create a new log file
mkdir -p "$log_dir"
log_file="$log_dir/$log_name.tmp.$$"
# if keep_logs is set to 0, redirect all logging to /dev/null
if [ $keep_logs -eq 0 ]; then
   log_file="/dev/null"
fi
cat << _EOF >> "$log_file"
Script started on $(date) with a process name of $0 (PID $$) by $(id -un) (UID $(id -u)).
Real external IP address ("bad" IP) is set to $real_ip.
Checking external IP address every $check_interval seconds.
Target process is $client.


_EOF

# append the message specified by $1 to the current date and tail that to the log
function log {
   echo -e "<$(date)>     $1" | tee -a "$log_file"
   return 0
}

# make sure only one instance of the script is running if allow_multiple is set to 0
if [ $allow_multiple -eq 0 ]; then
   if [ -e "$lockfile" ]; then
      log "Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run."
      kdialog --error "Only one instance of the script can be running at a time.  If you believe this is a mistake, remove $lockfile and try again."
      rename 's/\'.tmp.$$'$//' "$log_file"
      exit 1
   fi
   echo -e "$(date)\n$0 (PID $$)\n$(id -un) (UID $(id -u))" > "$lockfile"
   log "allow_multiple is set to 0.  Lockfile has been generated."
else
   if [ -e "$lockfile" ]; then
      log "Another instance of this script appears to be running already, but allow_multiple is set to 1.  This script will continue to run, but please note that this may cause problems."
   fi
   # make sure the script won't remove the lockfile for another instance if allow_multiple is set to 1
   lockfile=
fi

# trap relevant signals so the script can finish up cleanly
function finish_up {
   echo | tee -a $log_file
   log "IP has been successfully validated $(($checks-$failed)) times.  Note that the check failed $failed times."
   log "Script recieved signal and will now terminate.  Removing lockfile if present."
   if [ $keep_logs -ne 0 ]; then
      rename 's/\'.tmp.$$'$//' "$log_file"
      cd "$log_dir"
      mkdir -p old
      # if the number of uncompressed logs exceeds max_logs, compress the oldest and move it to the "old" directory
      if [ $(ls -l *.txt | wc -l) -gt $max_logs ]; then
         gzip -9 $(ls -1t *.txt | tail -1) # TODO: use bzip2 instead of gzip for debug logs
         mv *.gz old
      fi
   fi
   rm -f "$lockfile"
   exit $?
}
trap finish_up SIGHUP SIGINT SIGTERM

# log changing states of the client and IP
function check_state {
   state=$1
   if [ "$state" != "$last_state" ]; then
      case "$state" in
         1) log "$client is not running.  IP monitoring will be turned off." ;;
         2) log "$client is running, but IP is hidden.  Current IP address is $current_ip." ;;
         3) log "WARNING: The process $client has been caught running without protection.  SIGTERM has been sent."
            (sleep 3 && log "Sending SIGKILL to $client in case it's still alive.") & ;;
      esac
   fi
   last_state=$state
   return 0
}

# STATES:
#  1: client is not running (IP doesn't matter)
#  2: client is running, and IP is hidden
#  3: client is running, but IP is NOT hidden (!)
failed=0
checks=0
while true; do
   while true; do
      if [ $(pgrep -c $client) -ne 0 ]; then
         # this loop adds redundancy to the check in case one or more of the servers are down
         while true; do
            for check_url in $hosts; do
               last_ip=$current_ip
               current_ip=$(curl --max-time 20 -s $check_url)
               let checks=$checks+1
               if [ "$current_ip" = "" -o $(echo "$current_ip" | grep -Ec '[[:alpha:]]') -ne 0 ]; then # check if the server responded with an IP address and not an error page or anything
                  let failed=$failed+1
                  break 3
               fi
               if [ "$current_ip" = "$real_ip" -a $(pgrep -c $client) -ne 0 ]; then
                  # IP address is not hidden, but my torrent client is running (sending SIGTERM to the client)
                  check_state 3
                  pid=$(pidof $client)
                  killall -q $client
                  sleep 5
                  # sending SIGKILL to the client (in case it is still running)
                  killall -qs 9 $client
                  (kdialog --title 'Warning!' --sorry "Your torrent client has been caught running without protection.\nFor your safety, the process $client($pid) has been killed." &)
                  break 2
               else
                  if [ $(pgrep -c $client) -eq 0 ]; then
                     # the torrent client is no longer running, so there is no reason to continue checking my IP
                     check_state 1
                     break 2
                  fi
                  # the torrent client is running, but my IP address is hidden
                   if [ "$current_ip" != "$last_ip" -a "$last_ip" != "" ]; then
                     log "External IP address has changed from $last_ip to $current_ip."
                  fi
                  check_state 2
                  sleep $check_interval
               fi
            done
         done
      else
         # the torrent client is not running, so it doesn't matter if my IP hidden or not
         check_state 1
      fi
         sleep $check_interval
   done
done

```

---

### Post by repcri on 2012-11-28
Here's a quick thought... What if your real IP address changes during the time that this script is running, and you loose your VPN.

This suddenly will not work as intended.

Or have it stop if your address changes outside of a particular range?

---

### Post by repcri on 2012-11-28
I just modified this a little to stop ktorrent if the external IP address changes as well -- with the VPN I use it doesn't change.


```
#!/bin/bash

#                ###############################################
#                             VPNCHECK by Stonecold
#                ###############################################
#
# This is a little script which checks to see if your IP address is hidden so you can
# torrent safely.  It will periodically compare your real IP address with your visible
# IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
# kills you torrent client to prevent it from leaking your IP to the MAFIAA.
#
# This script will NOT protect you if you don't already have some kind of VPN or proxy
# set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
# of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
# open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
# your real IP changes and you don't edit this script it will be pretty much useless
# (e.g. if you have a laptop and you use a different router for any reason, such as going
# to a friend's house, a public cafe, you get a new router, etc).
#
#
# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.
#
# Last modified: August 23, 2012
#
# TODO: add debug variable instead of doing bash -x ./script.sh
# TODO: test the script under root
# TODO: add function to check if required programs are installed (e.g. curl)

# variables to control the behavior of this script
real_ip="xxx.xxx.xxx.xxx"          # this is my *real* external IP address
check_interval=1               # how many seconds to wait before checking again
IFS='|'                         # separator between hosts to probe for current ip
client="ktorrent"               # the name of the torrent client's parent process
allow_multiple=0                # whether to allow multiple running instances of not (0=no, 1=yes)
lockfile="/tmp/.vpncheck.lock"  # location of the lock file for this script to use
keep_logs=1                     # whether to log events and activities (0=no, 1=yes)
max_logs=5                      # maximum number of logs to keep at once before compressing and archiving them (TODO: make max archived logs)
log_dir="/home/chris/.vpncheck" # directory to put log files in
log_name="vpncheck_log_$(date +%a_%b_%d_%T_%Z_%Y).txt"  # format to name logfiles
hosts="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com|automation.whatismyip.com/n09230945.asp"  # what sites to use to check the external IP

# command line options
if [ "$1" != "" ]; then
   if [ "$1" = "--help" -o "$1" = "-h" ]; then
      cat << _EOF

               ###############################################
                            VPNCHECK by Stonecold
               ###############################################

This is a little script which checks to see if your IP address is hidden so you can
torrent safely.  It will periodically compare your real IP address with your visible
IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
kills you torrent client to prevent it from leaking your IP to the MAFIAA.

This script will NOT protect you if you don't already have some kind of VPN or proxy
set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
your real IP changes and you don't edit this script it will be pretty much useless
(e.g. if you have a laptop and you use a different router for any reason, such as going
to a friend's house, a public cafe, you get a new router, etc).


Command line options:

      -h, --help    display this help


This script is licensed under the WTFPL, Version 2.
_EOF
      exit 0
   fi
   echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
   exit 1
fi

# prepare log directory and create a new log file
mkdir -p "$log_dir"
log_file="$log_dir/$log_name.tmp.$$"
# if keep_logs is set to 0, redirect all logging to /dev/null
if [ $keep_logs -eq 0 ]; then
   log_file="/dev/null"
fi
cat << _EOF >> "$log_file"
Script started on $(date) with a process name of $0 (PID $$) by $(id -un) (UID $(id -u)).
Real external IP address ("bad" IP) is set to $real_ip.
Checking external IP address every $check_interval seconds.
Target process is $client.


_EOF

# append the message specified by $1 to the current date and tail that to the log
function log {
   echo -e "<$(date)>     $1" | tee -a "$log_file"
   return 0
}

# make sure only one instance of the script is running if allow_multiple is set to 0
if [ $allow_multiple -eq 0 ]; then
   if [ -e "$lockfile" ]; then
      log "Another instance of this script appears to be running already, and allow_multiple is set to 0.  This script will not be run."
      kdialog --error "Only one instance of the script can be running at a time.  If you believe this is a mistake, remove $lockfile and try again."
      rename 's/\'.tmp.$$'$//' "$log_file"
      exit 1
   fi
   echo -e "$(date)\n$0 (PID $$)\n$(id -un) (UID $(id -u))" > "$lockfile"
   log "allow_multiple is set to 0.  Lockfile has been generated."
else
   if [ -e "$lockfile" ]; then
      log "Another instance of this script appears to be running already, but allow_multiple is set to 1.  This script will continue to run, but please note that this may cause problems."
   fi
   # make sure the script won't remove the lockfile for another instance if allow_multiple is set to 1
   lockfile=
fi

# trap relevant signals so the script can finish up cleanly
function finish_up {
   echo | tee -a $log_file
   log "IP has been successfully validated $(($checks-$failed)) times.  Note that the check failed $failed times."
   log "Script recieved signal and will now terminate.  Removing lockfile if present."
   if [ $keep_logs -ne 0 ]; then
      rename 's/\'.tmp.$$'$//' "$log_file"
      cd "$log_dir"
      mkdir -p old
      # if the number of uncompressed logs exceeds max_logs, compress the oldest and move it to the "old" directory
      if [ $(ls -l *.txt | wc -l) -gt $max_logs ]; then
         gzip -9 $(ls -1t *.txt | tail -1) # TODO: use bzip2 instead of gzip for debug logs
         mv *.gz old
      fi
   fi
   rm -f "$lockfile"
   exit $?
}
trap finish_up SIGHUP SIGINT SIGTERM

# log changing states of the client and IP
function check_state {
   state=$1
   if [ "$state" != "$last_state" ]; then
      case "$state" in
         1) log "$client is not running.  IP monitoring will be turned off." ;;
         2) log "$client is running, but IP is hidden.  Current IP address is $current_ip." ;;
         3) log "WARNING: The process $client has been caught running without protection.  SIGTERM has been sent."
            (sleep 3 && log "Sending SIGKILL to $client in case it's still alive.") & ;;
      esac
   fi
   last_state=$state
   return 0
}

# STATES:
#  1: client is not running (IP doesn't matter)
#  2: client is running, and IP is hidden
#  3: client is running, but IP is NOT hidden (!)
failed=0
checks=0
while true; do
   while true; do
      if [ $(pgrep $client) -ne 0 ]; then
         # this loop adds redundancy to the check in case one or more of the servers are down
         while true; do
            for check_url in $hosts; do
               last_ip=$current_ip
               current_ip=$(curl --max-time 20 -s $check_url)
               let checks=$checks+1
               if [ "$current_ip" = "" -o $(echo "$current_ip" | grep -Ec '[[:alpha:]]') -ne 0 ]; then # check if the server responded with an IP address and not an error page or anything
                  let failed=$failed+1
                  break 3
               fi
               if [ "$current_ip" = "$real_ip" -a $(pgrep $client) -ne 0 ]; then
                  # IP address is not hidden, but my torrent client is running (sending SIGTERM to the client)
                  check_state 3
                  pid=$(pidof $client)
                  killall -q $client
                  sleep 5
                  # sending SIGKILL to the client (in case it is still running)
                  killall -qs 9 $client
                  (kdialog --title 'Warning!' --sorry "Your torrent client has been caught running without protection.\nFor your safety, the process $client($pid) has been killed." &)
                  break 2
               else
                  if [ $(pgrep $client) -eq 0 ]; then
                     # the torrent client is no longer running, so there is no reason to continue checking my IP
                     check_state 1
                     break 2
                  fi
                  # the torrent client is running, but my IP address is hidden
                   if [ "$current_ip" != "$last_ip" -a "$last_ip" != "" ]; then
                     log "External IP address has changed from $last_ip to $current_ip."
                     check_state 3
                     pid=$(pidof $client)
                     killall -q $client
                     sleep 5
                     # sending SIGKILL to the client (in case it is still running)
                     killall -qs 9 $client
                     (kdialog --title 'Warning!' --sorry "Your torrent client may have been caught running without protection. \nExternal IP address changed. \nFor your safety, the process $client($pid) has been killed." &)
                     break 2
                  fi
                  check_state 2
                  sleep $check_interval
               fi
            done
         done
      else
         # the torrent client is not running, so it doesn't matter if my IP hidden or not
         check_state 1
      fi
         sleep $check_interval
   done
done
```

---

### Post by Stonecold1995 on 2013-04-19
This is my current version.  I added a lot more features but in the process I may have made it a bit (or more) sloppy...  I keep having the nagging feeling that this script is really, really bad.
```
#!/bin/bash
#                ###############################################
#                             VPNCHECK by Stonecold
#                ###############################################
#
#
# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.
#
#
#  TODO
#  - If a URL is down, skip it and go on to the next instead of retrying it (IMPORTANT)
#  - Add an option to not compress or archive logs, just let them accumulate
#  - Add support for monitoring multiple clients and IPs at once
#  - Enable passing on arguments to the script to override the default variables
#  - Redirect output messages to stdout and stderr correctly
#  - Add command line option to clean up log files that weren't renamed correctly

# variables to control the behavior of this script
real_ip=xxx.xxx.xxx.xxx         # this is my "real" external IP address
interval=60                     # how many seconds to wait before checking again
client=ktorrent                 # the name of the target process
allow_root=0                    # whether or not to allow the script to run as root (0=no, 1=yes)
lockfile=.vpncheck.lock         # location of the lock file for this script to use
keep_logs=1                     # whether or not to log events and activities (0=no, 1=yes)
max_logs=10                     # maximum number of logs to keep at once before compressing and archiving them
archive=archive                 # directory to move old logs to
log_dir=$HOME/.vpncheck_debug   # directory to put log files in
log_name=vpncheck_log_$(date +%a_%b_%d_%T_%Z_%Y).txt  # format to name logfiles
IFS='|'                         # separator between hosts to probe for current IP
hosts="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com"  # what sites to use to check the external IP


if [ $allow_root -eq 0 -a $UID -eq 0 ]; then
    echo "This script must not be run as root.  To allow root, set allow_root to 1."
    exit 1
fi


# command line options
if [ $# -ne 0 ]; then
    if [ "$1" = "--help" -o "$1" = "-h" ]; then
        cat << _HELP


               ###############################################
                            VPNCHECK by Stonecold
               ###############################################


This is a little script which checks to see if your IP address is hidden so you can
torrent safely.  It will periodically compare your real IP address with your visible
IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP) it
kills you torrent client to prevent it from leaking your IP to the MAFIAA.  I suppose
it could also be used to secure other programs aside from torrent clients, but that's
not what it's intended for.


This script will NOT protect you if you don't already have some kind of VPN or proxy
set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
open and vulnerable.  Also, you have to set your real (vulnerable) IP manually, so if
your real IP changes and you don't edit this script it will be pretty much useless
(e.g. if you have a laptop and you use a different router for any reason, such as going
to a friend's house, a public cafe, you get a new router, etc).


THIS SCRIPT WILL NOT PROVIDE PROTECTION IF YOU HAVE A DYNAMIC IP ADDRESS
UNLESS YOU MANUALLY CHANGE THE "BAD" IP TO YOUR CURRENT IP






Command line options:


      -h, --help    display this help




This script is licensed under the WTFPL, Version 2.
_HELP
        exit 0
    fi
    echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
    exit 1
fi


# if keep_logs is set to 0, don't create log_dir and redirect all logging to /dev/null
log_file=/dev/null
if [ $keep_logs -eq 1 ]; then
    mkdir -p "$log_dir"
    #log_file="$log_dir/$log_name.tmp.$$" # disable because of a problem with trap
    log_file="$log_dir/$log_name"
fi


# TODO: the script should mention it's current SHA-1 sum here
cat << _LOG >> "$log_file"
Script started on $(date) with a process name of $0 (PID $$) by $(id -un) (UID $(id -u)).
Real external IP address ("bad" IP) is set to $real_ip.
Checking external IP address every $interval seconds.
Target process is $client.




_LOG


# append $1 to the current date and tail that to the log
function log() {
    echo -e "<$(date)>     $1" | tee -a "$log_file"
    return 0
}


# trap relevant signals so the script can finish up cleanly
function finish_up() {
    echo | tee -a "$log_file"
    log "IP has been successfully validated $(($checks-$failed)) times.  Note that the check failed $failed times."
    log "Script recieved signal and will now terminate.  Removing lockfile if present."
    if [ $keep_logs -eq 1 ]; then
        #rename 's/\'.tmp.$$'$//' "$log_file" # disabled because of a problem with trap
        cd "$log_dir" 2>/dev/null
        # if the number of uncompressed logs exceeds max_logs, compress the oldest and move it to archive
        if [ $(stat -c %n *.txt 2>/dev/null | wc -l) -gt $max_logs -a -d "$log_dir" ]; then
            bzip2 -9 $(ls -1t *.txt | tail -1)
            mkdir -p "$archive"
            mv *.bz2 "$archive"
        fi
    fi
    rm "$lockfile"
    exit 0 # our job is done, stop the script!
}
trap finish_up SIGHUP SIGINT SIGTERM


# prevent opening dialog boxes if X isn't available
function kdialog_x() {
    if pidof X &>/dev/null && [ -n "$DISPLAY" ]; then
        kdialog $@
    else
        echo "$4"
    fi
    return 0
}


# exit if the lockfile inexplicably vanishes
function check_lock() {
    if ! [ -e "$lockfile" -a "$(cat $lockfile)" = $$ ]; then # is checking if the lockfile stores the correct PID necessary?
        log "The lockfile has inexplicably vanished.  The script will now exit."
        pidof "$client" &>/dev/null && append_message="  For your safety, the process $client("$(pidof $client)") has also been killed."
        (kdialog_x --title "$(basename $0)" \
                   --sorry "The lockfile has inexplicably vanished.  The script will now exit.$append_message" &)
        (killall -q "$client" && sleep 5 && killall -qs 9 "$client" &) # send SIGKILL to the target process (in case it's still running)
        finish_up
    fi
}


# log changing states of the client and IP (just log, don't do anything about it
last_state=0
function log_state() {
    state=$1
    if [ $state -ne $last_state ]; then
        case $state in
            1) log "$client is not running.  IP monitoring will be turned off." ;;
            2) log "$client is running, but IP is hidden.  Current IP address is $current_ip." ;;
            3) log "WARNING: The process $client has been caught running without protection.  SIGTERM has been sent."
               (sleep 3; log "Sending SIGKILL to $client in case it's still alive." &) ;;
        esac
    fi
    last_state=$state
    check_lock
    return 0
}


# return true if IP is valid
# TODO: study this stolen code because I'm stupid and don't understand the syntax or style
function is_valid_ipv4() {
    local IFS='.'
    local -a octets=($1)
    local RETURNVALUE=0
    [ ${#octets
[*]} -ne 4 ] && return 1
    for octet in ${octets
[*]}; do
        if [[ ${octet} =~ ^[0-9]{1,3}$ ]]; then # find a different technique
            ((RETURNVALUE += octet>>8))
        else
            return 1
        fi
    done
    return ${RETURNVALUE}
}


# set correct lockfile variable
if [ -z "$TMPDIR" ]; then
    lockfile=/tmp/"$lockfile"
else
    lockfile="$TMPDIR/$lockfile" # what's the difference between TMP and TMPDIR?
fi


# only allow one instance to run at a time
if [ -O "$lockfile" -a -e "/proc/$(cat $lockfile)/comm" ]; then # this seems pretty sloppy...
    log "Another instance of this script appears to be running already.  The script will not be run."
    (kdialog_x --title "$(basename $0)" \
               --error "Only one instance of the script can be run at a time.  If you believe this is a mistake, remove $lockfile and try again." &)
    #rename 's/\'.tmp.$$'$//' "$log_file" # disabled because of a problem with trap
    exit 1
fi
echo -n $$ > "$lockfile" # is it necessary to disable the trailing newline?


# STATES:
#  0: state unknown, or no state
#  1: client is not running (IP doesn't matter)
#  2: client is running, and IP is hidden
#  3: client is running, but IP is NOT hidden!
failed=0
checks=0
while true; do
    while true; do
        if pidof "$client" &>/dev/null; then
            # this loop adds redundancy to the check in case one or more of the servers are down
            while true; do
                for url in $hosts; do
                    last_ip="$current_ip"
                    current_ip=$(curl --max-time 20 -s $url)
                    ((checks++))
                    if ! is_valid_ipv4 "$current_ip"; then
                        ((failed++))
                        break 3
                    fi
                    if [ "$current_ip" = "$real_ip" ] && pidof $client &>/dev/null; then
                        # IP address is not hidden, but the target process is running (sending SIGTERM to the client)
                        # the kdialog line must be a command or two above the killall line so it has time to get the client's PID before it is killed
                        (kdialog_x --title "$(basename $0)" \
                                   --sorry "The target process has been caught running without protection.\nFor your safety, the process $client($(pidof $client)) has been killed." &)
                        log_state 3
                        (killall -q $client && sleep 5 && killall -qs 9 $client &) # send SIGKILL to the target process (in case it's still running)
                        break 2
                    else
                        if ! pidof $client &>/dev/null; then
                            # the target process is no longer running, so there is no reason to continue checking my IP 
                            log_state 1
                            break 2
                        fi
                        # the target process is running, but my IP address is hidden
                        if [ "$current_ip" != "$last_ip" -a -n "$last_ip" ]; then
                            log "External IP address has changed from $last_ip to $current_ip."
                        fi
                        log_state 2
                        sleep $interval
                    fi
                done
            done
        else
            # the target process is not running, so it doesn't matter if my IP hidden or not
            log_state 1
        fi
            sleep $interval
    done
done


# u dun goofed
echo 'lolwut?  This should never happen, something broke!'
exit 1
```

I'm probably going to add an option eventually to bring down all networking.  That'll be easier (and safer) than killing each target process manually.

---

### Post by kevinkhill on 2013-06-04
This is exactly what I was looking for! I think it is working, I put transmission-daemon in the script instead of ktorrent, and I put my real IP. It says it is working, which I double checked. I registered to thank you for this, and to ask one question. How do I get this script to run in the background instead of blocking the terminal when I run it? And as a side note, just thought I would be neat if possible, can you query the script and get it to reply with the output message? or would I just tail the logfile?

Thanks again!

---

### Post by Stonecold1995 on 2013-06-04
> **kevinkhill said:**
> This is exactly what I was looking for! I think it is working, I put transmission-daemon in the script instead of ktorrent, and I put my real IP. It says it is working, which I double checked. I registered to thank you for this, and to ask one question. How do I get this script to run in the background instead of blocking the terminal when I run it? And as a side note, just thought I would be neat if possible, can you query the script and get it to reply with the output message? or would I just tail the logfile?

Thanks again!
To run the script in the background just run it like this:
```
./vpncheck.sh &
```

Or my solution is to put it in my autostart directory.  On KDE distros like Kubuntu, it's in ~/.kde/Autostart.

As for getting the current state of the script, tailing the logfile would probably be the best idea.

Also, I've updated the script quite a bit since my last post.  It's now more agressive and will disable networking instead of a single process.

```
#!/bin/bash

# VPNCHECK by Stonecold
#
# This program is free software. It comes without any warranty, to
# the extent permitted by applicable law. You can redistribute it
# and/or modify it under the terms of the Do What The **** You Want
# To Public License, Version 2, as published by Sam Hocevar. See
# http://sam.zoy.org/wtfpl/COPYING for more details.
#
#
#  TODO
#  - Add an option to not compress or archive logs, just let them accumulate
#  - Enable passing on arguments to the script to override the default variables
#  - Redirect output messages to stdout and stderr correctly
#  - Add command line option to clean up log files that weren't renamed correctly
#  - Look into using /etc/vpncheck.conf instead of editing the script's variables
#  - Create installer to install and daemonize the script
#  - Keep version information
#
#  - IMPORTANT: Make sure the polkit-1 rules are set correctly so NetworkManager
#               can be controled by any user on any tty (there is little security
#               risk on a single user computer).


# variables to control the behavior of this script
real_ip=xxx.xxx.xxx.xxx         # this is my current "real" external IP address
ip_check_interval=60            # how many seconds to wait before checking the current IP again
network_check_interval=10       # how many seconds to wait before checking if the network is still down
allow_root=0                    # whether or not to allow the script to run as root (0=no, 1=yes)
broadcast_messages=1            # broadcast messages to all terminals (0=no, 1=yes)
lockfile=.vpncheck.lock         # location of the lock file for this script to use
keep_logs=1                     # whether or not to log events and activities (0=no, 1=yes)
max_logs=0                      # maximum number of logs to keep at once before archiving them (0=infinite)
archive=archive                 # directory to move old logs to
log_dir=$HOME/.vpncheck         # directory to put log files in
log_name=vpncheck_"$(date +%a_%b_%d_%T_%Z_%Y)".log  # format to name logfiles
IFS='|'                         # separator between hosts to probe for current IP
hosts="icanhazip.com|ifconfig.me/ip|myip.dnsomatic.com"  # what sites to use to check the external IP (TODO: how to make this safer?)




# prevent opening dialog boxes if X isn't available (MUST HAVE TWO ARGUMENTS, e.g. --sorry "message goes here")
function alert() {
    if pidof X &>/dev/null && [ -n "$DISPLAY" ]; then # is there a better way to tell if X is running?
        (kdialog $@ &)
    elif [ $broadcast_messages = 1 ]; then
        echo "$4" | wall
    else
        echo "$4"
    fi
    return 0
}


# append $1 to the current date and tail that to the log
function log() {
    echo -e "$(date +'[ %D %r ]:')" $1 | tee -a "$log_file"
    return 0
}


# trap relevant signals so the script can finish up cleanly
function finish_up() {
    echo | tee -a "$log_file"
    log "IP has been successfully validated $(($checks-$failed)) times.  Note that the check failed $failed times."
    log "Script recieved signal and will now terminate.  Removing lockfile if present."
    if [ $keep_logs = 1 ]; then
        #rename 's/\'.tmp.$$'$//' "$log_file" # disabled because of a problem with trap
        cd "$log_dir" 2>/dev/null # sloppy...
        # if the number of uncompressed logs exceeds max_logs, compress the oldest and move it to archive
        # TODO: fix this so it is not dependent on the extension ".log"
        if [ $(stat -c %n *.log 2>/dev/null | wc -l) -gt $max_logs -a $max_logs -ne 0 -a -d "$log_dir" ]; then
            gzip -9 $(ls -1t *.txt | tail -1)
            mkdir "$archive"
            mv *.gz "$archive"
        fi
    fi
    rm "$lockfile"
    exit 0 # our job is done, stop the script!
}
trap finish_up SIGHUP SIGINT SIGTERM


# would something like isup_network be a better name?
function check_networking() {
    dbus-send --system --print-reply --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Get string:"org.freedesktop.NetworkManager" string:"NetworkingEnabled" | grep -q true
    return $?
}


# VERY IMPORTANT!
function disable_networking() {
    dbus-send --print-reply --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.Enable boolean:false
    sleep 3 # is this even necessary (i.e. does the above command take effect immediately)?
    if ! check_networking; then
        log "Networking has been disabled."
        notify-send --urgency=critical WARNING "Networking has been disabled by $(basename $0)."
        return 0
    else
        # TODO: don't hardcode the time before killing all processes!
        log "Error: Networking could not be disabled.  Killing all processes in 10 seconds."
        alert --sorry "NETWORKING COULD NOT BE DISABLED.  KILLING ALL PROCESSES IN TEN SECONDS..."
        sleep 10
        kill -9 -1
        return 1 # would exit 1 be better?
        # TODO: we should NEVER be here, have the script alert the user that "kill -9 -1" failed and take action
    fi
}


# exit if the lockfile inexplicably vanishes
# TODO: use $append_message so this doesn't try to bring down the network if it's already down?
function check_lock() {
    if ! [ -e "$lockfile" -a "$(cat $lockfile)" = $$ ]; then # is checking if the lockfile stores the correct PID necessary?
        log "The lockfile has inexplicably vanished.  The network has been brought down for safety.  The script will now exit."
        alert --sorry "The lockfile has inexplicably vanished.  The network has been brought down for safety.  The script will now exit."
        disable_networking
        finish_up
    fi
    return 0
}


# log changing states of the network and IP (just log, don't do anything about it)
# STATES:
#  0: state unknown, or no state
#  1: network is down
#  2: network is up and IP is hidden
#  3: network is up but IP is NOT hidden
last_state=0
function log_state() {
    state=$1
    if [ $state -ne $last_state ]; then
        case $state in
            1) log "Network is down.  IP monitoring will be turned off." ;;
            2) log "Network is up, but IP is hidden.  Current IP address is $current_ip." ;;
            3) log "WARNING: IP is not hidden."
        esac
    fi
    last_state=$state
    check_lock
    return 0
}


# return true if IP is valid
# TODO: study this stolen code because I'm stupid and don't understand all of it
function is_valid_ipv4() {
    local IFS='.'
    local -a octets=($1)
    local RETURNVALUE=0
    [ ${#octets
[*]} -ne 4 ] && return 1
    for octet in ${octets
[*]}; do
        if [[ ${octet} =~ ^[0-9]{1,3}$ ]]; then # find a different technique
            ((RETURNVALUE += octet>>8))
        else
            return 1
        fi
    done
    return ${RETURNVALUE}
}


# not tested under root, so to be safe disallow running with elevated privileges
if [ $allow_root != 1 -a $UID -eq 0 ]; then
    alert --error "This script must not be run as root.  To allow root, set allow_root to 1."
    exit 1
fi


# command line options
if [ $# -ne 0 ]; then
    if [ "$1" = "--help" -o "$1" = "-h" ]; then
        cat << _HELP


               ###############################################
                            VPNCHECK by Stonecold
               ###############################################


This is a little script which checks to see if your IP address is hidden so you can
torrent safely.  It will periodically compare your real IP address with your visible
IP, and if they are the same (i.e. you don't have a VPN or proxy hiding your IP), it
disables networking entirely.  If that fails for any reason, it forcibly logs out as
a last resort by killing all processes.


This script will NOT protect you if you don't already have some kind of VPN or proxy
set up as a SYSTEM CONNECTION.  It only adds an extra layer of security in the form
of a fail-safe in the case that your first line of defense (VPN) fails and leaves you
open and vulnerable.


You must set your real (vulnerable) IP manually, so if your real IP changes and you
don't edit this script, it will be pretty much useless.








Command line options:


      -h, --help    display this help




This script is licensed under the WTFPL, Version 2.
_HELP
        exit 0
    fi
    echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
    exit 1
fi


# first run, alert the user that he must set his IP address
if ! is_valid_ipv4 "$real_ip"; then
    echo "WARNING: You have not set your IP address.  Please change the variable 'real_ip' to the IP you want protected."
    exit 1
fi


# if keep_logs is not set to 1, don't create log_dir and redirect all logging to /dev/null
log_file=/dev/null
if [ $keep_logs = 1 ]; then
    mkdir -p "$log_dir"
    #log_file="$log_dir/$log_name.tmp.$$" # disable because of a problem with trap
    log_file="$log_dir/$log_name"
fi


# TODO: the script should mention it's current MD5 hash here
cat << _LOG >> "$log_file"
Script started on $(date) with a process name of $0 (PID $$) by $(id -un) (UID $(id -u)).
Real external IP address ("bad" IP) is set to $real_ip.
Checking external IP address every $interval seconds.




_LOG


# set correct lockfile variable
if [ -z "$TMPDIR" ]; then
    lockfile=/tmp/"$lockfile"
else
    lockfile="$TMPDIR/$lockfile" # what's the difference between TMP and TMPDIR?
fi


# only allow one instance to run at a time
if [ -O "$lockfile" -a -e "/proc/$(cat $lockfile)/comm" ]; then # this seems pretty sloppy...
    log "Another instance of this script appears to be running already.  The script will not be run."
    alert --error "Only one instance of the script can be run at a time.  If you believe this is a mistake, remove $lockfile and try again."
    #rename 's/\'.tmp.$$'$//' "$log_file" # disabled because of a problem with trap
    exit 1
fi
echo -n $$ > "$lockfile" # is it necessary to disable the trailing newline?


failed=0
checks=0
while true; do
    while true; do
        if check_networking; then
            # this loop adds redundancy to the check in case one or more of the servers are down
            while true; do
                for url in $hosts; do
                    last_ip="$current_ip"
                    #current_ip=$(curl --max-time 20 -s $url) # curl is too bulky
                    current_ip=$(wget -U "" -q -4 -t 5 -T 20 -O - "$url") # TODO: disable networking if wget fails several times in a row (e.g. when networking is ON but the internet is not available)
                    ((checks++))
                    if ! is_valid_ipv4 "$current_ip"; then
                        ((failed++))
                        break 3
                    fi
                    if [ "$current_ip" = "$real_ip" ]; then
                        # IP address is not hidden, bring down the network!
                        alert --sorry 'The network is up, but your IP is not hidden!  Networking has been disabled.'
                        log_state 3
                        disable_networking
                        break 2
                    else
                        if ! check_networking; then
                            # the network is down, no reason to continue trying to check IP 
                            log_state 1
                            break 2
                        fi
                        # networking is enabled, but my IP is hidden
                        if [ "$current_ip" != "$last_ip" -a -n "$last_ip" ]; then
                            log "External IP address has changed from $last_ip to $current_ip."
                        fi
                        log_state 2
                        sleep $ip_check_interval
                    fi
                done
            done
        else
            # the network is down, no reason to continue trying to check IP
            log_state 1
        fi
            sleep $network_check_interval
    done
done


# u dun goofed
echo 'lolwut?  This should never happen, something is b0rked!'
exit 1

```

Some changes:
- Disables networking instead of killing a single process
- Different check intervals when networking is active vs inactive
- Ability to notify all users' terminals by setting broadcast_messages to 1
- Added a few sanity checks
- Improved some lazy scripting
- Organized functions a bit more

The command which brings down networking is:
```
dbus-send --print-reply --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.Enable boolean:false
```
(replace "false" with "true" to re-enable networking via command line)

If that doesn't work then the updated script will be ineffective.

---

### Post by Stonecold1995 on 2013-06-05
Does anyone know of any sites which output only your IP address?  I only know of three, icanhazip.com, ifconfig.me/ip, and myip.dnsomatic.net, but it would be good to be able to use more so these sites don't block the IP address for connecting so often.

---

### Post by ghost-face on 2013-10-10
Hi. I am not so familiar with linux scripts but could be done here a user friendly extention of it? The tool is really  awesome!!!
What I would like to have is right after I call the script a message box should appears (in a Terminal or GUI Frame) where I can type my unhidden IP. 
Now I have always to edit the script file and I think a message box makes the configuration faster. Does anyone know how to do this related to the Script from Stonecold1995? Thx a lot!

---

### Post by rsmith317in on 2013-12-16
Some nice scripts here :) I wrote something similar awhile back that keeps an  eye on your IPs using a couple of different methods and gives some  options for notification and such. A friend of mine talked me into putting it up not long ago, so it's a pet project now. It was written for CentOS but it  wouldn't take much to adapt it to Debian flavours (some of the binary paths are probably a little different, and the network shutdown command is in the comments). Feedback and feature requests are welcome.

  [http://code.google.com/p/ipcheck/source/browse/ipcheck.sh](http://code.google.com/p/ipcheck/source/browse/ipcheck.sh)

---

### Post by tpcarmen on 2014-03-09
> **rsmith317in said:**
> Some nice scripts here :) I wrote something similar awhile back that keeps an  eye on your IPs using a couple of different methods and gives some  options for notification and such. A friend of mine talked me into putting it up not long ago, so it's a pet project now. It was written for CentOS but it  wouldn't take much to adapt it to Debian flavours (some of the binary paths are probably a little different, and the network shutdown command is in the comments). Feedback and feature requests are welcome.

  [http://code.google.com/p/ipcheck/source/browse/ipcheck.sh](http://code.google.com/p/ipcheck/source/browse/ipcheck.sh)

OK, so this has been a really long thread with lots of suggestions, but I need to put on my Master of the Obvious hat . . . 8-)

in a command prompt type:

ifconfig

There will be a number of entries, but the last one will be something like ppp0 or tun0 or some other virtual adapter created by your VPN.

Just go into ktorrent and under settings->configure ktorrent-> network, there is a dropdown. Select the interface associated with your VPN.

If the VPN isn't up, ktorrent won't have a network connection.

Terry

---


---
title: "Help setting up a modem pppd connect init.d bootup script"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by OrangeVixen on 2009-12-01
I wrote a script to run pppd to connect my modem to my ISP (dialup).

Now I want it to run at bootup and I was wondering what values do I need to set for the INIT INFO section, here is what I have so far:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          modem-connect-isp
# Required-Start:    mountkernfs udev
# Required-Stop:     
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: Connects/disconnects the modem from the ISP
# Description:       Establishes a persistent dialup Internet connection by
#                    instructing the modem to connect/disconnect to the ISP
#                    (Internet Service Provider) using pppd(8) (PPP Daemon)
### END INIT INFO

```

When I try this at startup, sometimes the modem connects but then fails, I think it may be because the modem /dev/ttyS0 was not initialized first.

Note that this script actually calls my real script in /etc/ppp/pppd-connect.sh which has a while[] statement for persistent connection. But for some reason it gets terminated (the whole script) so I was wondering what do I need to set for Default-Start and Default-Stop and other such values?

---

### Post by OrangeVixen on 2009-12-11
Bump.

It keeps failing, and looking at /var/log/messages it seems that chat(8) keeps terminating for some reason.

Am I starting it at the correct runlevel?

---

### Post by OrangeVixen on 2010-01-02
Bump, hoping someone knows?

Should there be a "sleep" in the script?

---

### Post by peepingtom on 2010-01-02
Are you sure you don't want to use /etc/network/interfaces instead?


Post both of your scripts if you want help.

---

### Post by OrangeVixen on 2010-01-02
Below is the init.d script:

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          modem-connect-isp
# Required-Start:    mountkernfs udev
# Required-Stop:     
# Default-Start:     3 4 5
# Default-Stop:      0 1 6
# Short-Description: Connects/disconnects the modem from the ISP
# Description:       Establishes a persistent dialup Internet connection by
#                    instructing the modem to connect/disconnect to the ISP
#                    (Internet Service Provider) using pppd(8) (PPP Daemon)
### END INIT INFO

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Connection to the ISP"

# This script calls the pppd scripts in /etc/ppp, if your pppd scripts
# are installed in a different location then change the value for BASE
# below
BASE=/etc/ppp
NAME=pppd-connect.sh
DAEMON=$BASE/pppd-connect.sh
DAEMON_ARGS=""
PIDFILE=/var/run/pppd-connect.pid
SCRIPTNAME=/etc/init.d/modem-connect-isp

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	$BASE/pppd-connect.sh &	
}

#
# Function that stops the daemon/service
#
do_stop()
{
	$BASE/pppd-disconnect.sh
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	$BASE/pppd-reconnect.sh
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	return "$RETVAL"
}

#
# Entry
#
case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:

```

Here is the pppd-connect.sh script, it works if I run it alone but chat(8) always terminated if pppd-connect.sh is runned from the init.d script at startup.

```

#!/bin/bash

# pppd(8) - PPP Daemon - Connect Script
#
# Usage: pppd-connect.sh &
#        pppd-connect.sh <ISP_NAME> <LOGIN_NAME> &
#        pppd-connect.sh <ISP_NAME> <LOGIN_NAME> <ACCESS_PHONE_NUMBER> &
#        pppd-connect.sh --help
#
# Runs the PPP Daemon (pppd) to instruct the modem to connect to the
# Internet Service Provider (ISP).
#
# Returns:
#
#	0	Successfully connected at least once.
#	1	Already connected.
#	2	Unable to connect.
#
# See also:
#
# pppd-disconnect.sh
# pppd-reconnect.sh
# pppd-status.sh
# chat-pap
# pap-secrets 
# chap-secrets
# chat-report
# /var/run/pppd-connect.pid
#


# ISP Information:
#
# The ACCESS_SITE_PHONE_NUMBER specifies the complete phone number
# (including access codes) for the modem to dial in order to connect
# to the ISP's access site.
#
# The ISP_NAME and LOGIN_NAME specifies the ISP and Login Name
# (respectively). This information is matched with the password in
# /etc/ppp/pap-secrets and /etc/ppp/chap-secrets and will be used to
# authenticate the login process after the modem connects and handshakes
# with the ISP's access site modem.
#

#	Defaults for Ultimate Internet Access (UIA) - uia.net
#
ACCESS_SITE_PHONE_NUMBER="6060183"
ISP_NAME="uia"
LOGIN_NAME="sandrac"


# Chat Script File:
#
# Used by chat(8) to negotiate the login process after the modem connects
# and handshakes with the ISP's access site modem.
#
CHAT_SCRIPT="/etc/ppp/chat-pap"

# Chat Report File:
#
# Generated by chat(8) to report messages received from the modem,
# including, but not limited to, the connection speed.
#
CHAT_REPORT_FILE="/etc/ppp/chat-report"


# Connect Script Process ID File:
#
# Used to indicate that this Connect Script (not pppd) is running and
# that we should (re)run pppd(8) while this file exists. This effectively
# acts as an indicator to maintain the connection whenever pppd(8) exits
# unexpectedly. So in order to disconnect, this file needs to be removed
# first and then kill pppd(8) afterwards.
#
PID_FILE="/var/run/pppd-connect.pid"


# Modem Device Path:
#
#MODEM_DEVICE="/dev/modem"
MODEM_DEVICE="/dev/ttyS0"


# Program Paths:
#
ECHO="/bin/echo"
PPPD="/usr/sbin/pppd"
CHAT="/usr/sbin/chat"


#
# End of settings, operations begin here...
#


# Print Help:
#
if [ "$1" = "--help" ] || [ "$1" = "-help" ] || [ "$1" = "-h" ]; then
 $ECHO -e -n "\
Usage: $0 &\n\
       $0 <isp_name> <login_name> &\n\
       $0 <isp_name> <login_name> <access_site_phone_number> &\n\
\n\
Runs the PPP Daemon (pppd) to instruct the modem to connect to the\n\
Internet Service Provider (ISP).\n\
\n\
    The <isp_name> and <login_name> specifies the ISP and Login Name\n\
    (respectively). This information is matched with the password in\n\
    /etc/ppp/pap-secrets and /etc/ppp/chap-secrets and will be used to\n\
    authenticate the login process after the modem connects and handshakes\n\
    with the ISP's access site modem.\n\
\n\
    The <access_site_phone_number> specifies the complete phone number\n\
    (including access codes) for the modem to dial in order to connect\n\
    to the ISP's access site.\n\
\n"
 exit 0
fi


# If the ISP_NAME and LOGIN_NAME were specified from the command line
# then use those instead, overriding the default ISP_NAME and LOGIN_NAME
# set in this script.
#
if [ -n "$1" ]; then
 if [ -n "$2" ] && [ -n "$3" ]; then
  ISP_NAME="$1"
  LOGIN_NAME="$2"
  ACCESS_SITE_PHONE_NUMBER="$3"
 else
 # ISP_NAME specified but LOGIN_NAME was not specified, print a brief
 # usage message and then exit
 $ECHO -e -n "\
Usage: $0 &\n\
       $0 <isp_name> <login_name> &\n\
       $0 <isp_name> <login_name> <access_site_phone_number> &\n"
  exit 2
 fi
fi


# Check if this script is already running by testing if the Process ID
# File for this script exists.
#
if [ -f "$PID_FILE" ]; then

 # Verify that the Process ID refered to by the Process ID File exists
 ls "/proc/`cat "$PID_FILE"`" > /dev/null 2> /dev/null
 if [ "$?" = "0" ]; then

  # Tell the user that this script appears to already be running and
  # what options are available to override.
  $ECHO -e -n "\
Already connected.\n\
\n\
To disconnect, run:\n\
\n\
# pppd-disconnect.sh\n\
\n\
If the connect script is no longer running but its lock file still exists\n\
then try moving the lock file and running the connect script again:\n\
\n\
# rm \"$PID_FILE\"\n\
# $0 $@&\n\
"
 exit 1

 else
 # The Process ID File exists but the Process ID does not.

 # Remove the Process ID File and continue with connecting
 rm "$PID_FILE" > /dev/null 2> /dev/null

 fi

fi

# Check if the modem's device exists
#
if [ ! -w "$MODEM_DEVICE" ]; then
 $ECHO -e -n "\
Unable to open the modem device \"$MODEM_DEVICE\" for writing.\n\
\n\
Make sure that the modem is actually installed and intialized correctly.\n\
\n\
If it is located somewhere else on your system then you may need to edit\n\
this script and change the value for \$MODEM_DEVICE.\n\
\n\
In some cases you may need to run this script with a higher permission in\n\
order to access the modem device, try:\n\
\n\
# sudo $0 $@&\n\
"
 exit 2
fi


# Check if pppd(8) exists.
#
if [ ! -f "$PPPD" ]; then
 $ECHO -e -n "\
Unable to find the PPP Daemon \"$PPPD\".\n\
\n\
Make sure that the PPP Daemon is installed on your system.\n\
\n\
If it is located somewhere else on your system then you may need to edit\n\
edit this script and change the value for \$PPPD.\n\
"
 exit 2
fi

# Check if pppd(8) is executable.
#
if [ ! -x "$PPPD" ]; then
 $ECHO -e -n "\
You do not have permission to execute \"$PPPD\".\n\
\n\
You may need to run this script with a higher permission, such as:\n\
\n\
# sudo $0 $@&\n\
"
 exit 2
fi


# Check if chat(8) exists.
#
if [ ! -f "$CHAT" ]; then
 $ECHO -e -n "\
Unable to find Chat \"$CHAT\".\n\
\n\
Make sure that Chat is installed on your system.\n\
\n\
If it is located somewhere else on your system then you may need to edit\n\
edit this script and change the value for \$CHAT.\n\
"
 exit 2
fi

# Check if chat(8) is executable.
#
if [ ! -x "$CHAT" ]; then
 $ECHO -e -n "\
You do not have permission to execute \"$CHAT\".\n\
\n\
You may need to run this script with a higher permission, such as:\n\
\n\
# sudo $0 $@&\n\
"
 exit 2
fi


# Create the Process ID File containing this Connection Script's process
# ID and will indicate to maintain the connection in the "Main Connection
# Loop" below.
#
$ECHO -n "$$" > "$PID_FILE"


# Main Connection Loop:
#
# Maintain the connection while the Process ID File exists.
#
while [ -f "$PID_FILE" ]; do

 # Remove the previous chat report file (if any):
 #
 if [ -f "$CHAT_REPORT_FILE" ]; then
  rm "$CHAT_REPORT_FILE"
 fi

 # Run the PPP Daemon (pppd):
 #
 "$PPPD" "$MODEM_DEVICE" 115200 connect \
 "$CHAT -v -f $CHAT_SCRIPT -T $ACCESS_SITE_PHONE_NUMBER -r $CHAT_REPORT_FILE" \
 -detach crtscts modem defaultroute \
 remotename $ISP_NAME user $LOGIN_NAME > /dev/null

 # pppd(8) exited, most likely the connection was broken, wait 5 seconds
 # and reconnect
 #
 sleep 5

done


# Remove the previous chat report file (if any):
#
if [ -f "$CHAT_REPORT_FILE" ]; then
 rm "$CHAT_REPORT_FILE"
fi

```

---


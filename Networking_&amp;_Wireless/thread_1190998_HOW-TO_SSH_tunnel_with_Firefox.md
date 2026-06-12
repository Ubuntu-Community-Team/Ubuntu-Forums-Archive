---
title: "HOW-TO SSH tunnel with Firefox"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by sufslnd on 2009-06-18
I made this for my dad, so even YOU can use it ;)

What you need:
- Login to a ssh server
- Firefox with the [Switchproxy addon]("https://addons.mozilla.org/en-US/firefox/addon/125")

I've mad a bash script that ensures you don't need to mess with firefox settings yourself. (This is my first bash script, please be gentle :) )

```
#!/bin/bash
# To use local ports under 1024 you need to run the script as root
#
# FUNCTIONS
# Shuts down all processes beginning with ssh, if anyone has a better way
# of doing this, please let me know.
function shutdown {
		clear; echo "Shutting down tunnels.."; echo
		killall "ssh"
		echo
}
# Initiates the setup of the tunnel
function start {
		clear; echo "Setting up SSH tunnel.."; echo
		checkfirefoxdnssettings
		connectssh
}
# Gathers information and logs into the remote server.
# Again, run as root to use local ports under 1024
function connectssh {
		echo -ne "Logon name:	"; read USERNAME
		echo -ne "Remote address:	"; read SERVERNAME; 
		echo -ne "Local port:	"; read LOCALPORT
		echo -ne "Remote port:	"; read SERVERPORT; echo
		CONNECT="ssh -D $LOCALPORT -f -C -q -N $USERNAME@$SERVERNAME -p $SERVERPORT"
		echo "Connecting to $SERVERNAME as $USERNAME.."; $CONNECT
		sshcheck
}
# Function checks if there is a prosess with the provided connection options.
# If anyone has a better way of doing this, let me know.
function sshcheck {
		SSHCHECK=`ps aux | awk "/ssh -D $LOCALPORT -f -C -q -N $USERNAME@$SERVERNAME -p $SERVERPORT/" | awk '{print $11,$12,$13,$14,$15,$16,$17,$18,$19,$20}'`

		if [ "$SSHCHECK" = "$CONNECT" ]; then
			echo; echo "Secure connection set up on local socks port $LOCALPORT"; echo
		else
			echo "Not connected to server. Check username and password. Host may be down."
		fi		
		exit		
}
# Checks to see if Firefox will forward DNS requests over the proxy
# If not sets the parameter. Remember to shut down firefox first.
function checkfirefoxdnssettings {
	# Chekcs to see if Firefox is running
	cd "${FIREFOXPATH:0:$LENGTH}${PREFSFOLDER:5}"
	LOCK=`ls | awk '/^lock/'`

	if [ "$LOCK" = 'lock' ]; then
		read -p "Firefox is running. Shut it down and press a key."
		checkfirefoxdnssettings
	else
		# Locates the Firefox about:config for check and editing
		FIREFOXPATH=`locate .mozilla/firefox/profiles.ini`
		PREFSFOLDER=`cat $FIREFOXPATH | grep Path`
		let LENGTH=`expr length $FIREFOXPATH`-12
		CONFIGPATH="${FIREFOXPATH:0:$LENGTH}${PREFSFOLDER:5}/prefs.js"
		DNSCHECK=`cat $CONFIGPATH | awk '/network.proxy.socks_remote_dns/ {print $2}'`
		# Checks to see if DNS proxying is on
		if [ "$DNSCHECK" = 'true);' ]; then
			echo "Firefox DNS proxy: ON"; echo
		else
		# Adds the value to the end of the config file
			echo "Setting DNS proxy settings.."
			echo 'user_pref("network.proxy.socks_remote_dns", true);' >> $CONFIGPATH
			checkfirefoxdnssettings	
		fi
	fi
}

# Main script
clear
echo "Select option:"
OPTIONS="Start Shutdown"
select opt in $OPTIONS; do
	if [ "$opt" = "Start" ]; then
		start
		exit
	elif [ "$opt" = "Shutdown" ]; then
		shutdown
		exit
	else
		clear
		echo "Quitting"
		exit
	fi
done
```

Run the script. After it finishes set up a proxy in Switchproxy.
- Choose Add in the manage proxies menu
- Then Standard
- Write a name for your proxy under Proxy Label (This can be anything)
- Under SOCKS Proxy write 127.0.0.1 and supply with the localport you chose when you ran the script.
- Select SOCKS v5 and press ok

Everytime you want to use the proxy run the script first, then use the proxy you just set up in firefox.


Suggestions? :)

---


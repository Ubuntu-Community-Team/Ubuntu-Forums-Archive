---
title: "Weird pre-shutdown check script behavior"
date: 2008-07-19
forum: Mythbuntu
---

### Post by nomexous on 2008-07-19
I wrote an pre-shutdown check script so I could use it in a manner similar to the "shutdown" command. When I want to shutdown my Mythbox for the night, I simply SSH into it and issue "sudo autoshutdown enable". Then I can go to bed, and MythTV will finish what it needs to do, and shutdown.

The command "sudo autoshutdown enable" writes a file named .allow_auto_shutdown to mythtv's home directory. The pre-shutdown check script has mythtv running "autoshutdown status", which checks for the existence of the .allow_auto_shutdown file, and decides whether or not to exit 1 or exit 0.

The problem is that MythTV doesn't consistently honor the script. For example, when my Mythbox is started up, despite the fact that there is no .allow_auto_shutdown file in /home/mythtv, it goes ahead and does a shutdown after the idle period. But if I stop the backend daemon (sudo /etc/init.d/mythtv-backend stop) and restart it, MythTV will honor the script.

I can't figure out what I might have done wrong. I'm pretty sure it's not my script, because it runs just fine. If anyone has any idea what might be causing this odd behavior, let me know.

Pre-shutdown check script:

/usr/bin/autoshutdown
[PHP]#!/bin/bash

FILE=/home/mythtv/.allow_auto_shutdown

case $1 in

	enable|yes|allow|on)
		if [ $USER == "mythtv" ]; then
			touch $FILE;
		elif [ $USER == "root" ]; then
			touch $FILE;
			echo
			echo "Autoshutdown enabled."
			echo
		else
			echo "You must be root to do this."
		fi
		;;

	disable|no|disallow|off)
		if [ $USER == "mythtv" ]; then
			if [ -f $FILE ]; then
				rm $FILE
			fi
		elif [ $USER == "root" ]; then
			if [ -f $FILE ]; then
				rm $FILE
			fi
			echo
			echo "Autoshutdown disabled."
			echo
		else
			echo "You must be root to do this."
		fi
		;;

	status)
		if [ $USER == "mythtv" ]; then
			if [ -f $FILE ]; then
				rm $FILE
				exit 0
			else
				exit 1
			fi
		else
			if [ -f $FILE ]; then
				echo
				echo "Autoshutdown: ENABLED"
				echo
			else
				echo
				echo "Autoshutdown: DISABLED"
				echo
			fi
		fi
		;;
	
	*)
		echo "Usage: $0 [enable|yes|allow|on|disable|no|disallow|off|status]"
		;;
esac
[/PHP]

---

### Post by nomexous on 2008-07-19
Never mind, found what was wrong.

Turns out that when the mythtv-backend daemon was calling the pre-shutdown check script, the Bash environment variables weren't being set. When I started the daemon up manually, however, they were, accounting for the inconsistent behavior I mentioned before. So I just put a check in the script to see if $USER is unset. If it is unset, assume it's "mythtv".

Fixed /usr/bin/autoshutdown:
[PHP]#!/bin/bash

FILE=/home/mythtv/.allow_auto_shutdown

# The fix.
USER=${USER:='mythtv'}

case $1 in

    enable|yes|allow|on)
        if [ $USER == "mythtv" ]; then
            touch $FILE;
        elif [ $USER == "root" ]; then
            touch $FILE;
            echo
            echo "Autoshutdown enabled."
            echo
        else
            echo "You must be root to do this."
        fi
        ;;

    disable|no|disallow|off)
        if [ $USER == "mythtv" ]; then
            if [ -f $FILE ]; then
                rm $FILE
            fi
        elif [ $USER == "root" ]; then
            if [ -f $FILE ]; then
                rm $FILE
            fi
            echo
            echo "Autoshutdown disabled."
            echo
        else
            echo "You must be root to do this."
        fi
        ;;

    status)
        if [ $USER == "mythtv" ]; then
            if [ -f $FILE ]; then
                rm $FILE
                exit 0
            else
                exit 1
            fi
        else
            if [ -f $FILE ]; then
                echo
                echo "Autoshutdown: ENABLED"
                echo
            else
                echo
                echo "Autoshutdown: DISABLED"
                echo
            fi
        fi
        ;;
    
    *)
        echo "Usage: $0 [enable|yes|allow|on|disable|no|disallow|off|status]"
        ;;
esac[/PHP]
Thanks for all your help........ guys.:lolflag:

---


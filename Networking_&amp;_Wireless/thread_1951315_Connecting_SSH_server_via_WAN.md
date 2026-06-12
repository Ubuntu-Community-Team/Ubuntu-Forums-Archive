---
title: "Connecting SSH server via WAN"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by layr on 2012-04-02
Hey, I have set up a home SSH server and written a bash script that automaticalli backs up onto it. At the moment, my script first tries to connect server via LAN address, if that fails, tries the WAN address. Now I've come to think of it, was it actually necessary? Say the client is currently on the same LAN as the server and tries to connect it with WAN address. Would the actual data transfer go through the internet or LAN?

---

### Post by papibe on 2012-04-02
Hi layr.

I think you when you say WAN IP address, you are referring to your Public IP, isn't? The one you can get in your browser if you go to [IP Chicken]("http://www.ipchicken.com/") or [WhatIsMyIP]("http://www.whatismyip.org/"). Is that right?

> **layr said:**
> Hey, I have set up a home SSH server and written a bash script that automaticalli backs up onto it. At the moment, my script first tries to connect server via LAN address, if that fails, tries the WAN address. Now I've come to think of it, was it actually necessary?
Yes.

Unfortunately, accessing your server from your LAN using its public IP is not even possible since almost all consumer routers won't allow it.

BTW, I'm curious, What method are you using to determine if you are in your LAN or not?

Regards.

---

### Post by layr on 2012-04-03
> **papibe said:**
> I think when you say WAN IP address, you are referring to your Public IP, isn't?
That is correct.
> **papibe said:**
> Unfortunately, accessing your server from your LAN using its public IP  is not even possible since almost all consumer routers won't allow it.
Ok, then I'll leave the script as it is. Unfortunately my ISP is blocking ports, so I'm unable to test it.
> **papibe said:**
> BTW, I'm curious, What method are you using to determine if you are in your LAN or not?
First I tried listing (ls command) random location on the ssh server. Then I found [this]("http://forums.fedoraforum.org/showpost.php?p=1430792&postcount=5") post on fedoraforum.org, which offers pretty neat solutions.
tl;dr: check via ssh whether a specific file exists on sever.

My script is still under development and looks messy and rawish, but as of now it seems to be doing what it should. It has two files - one for client (that backs up onto server) and other for server (backs the client data up onto other HDD). I'll leave my parameters in (for explanation purpose and simply because I don't bother cleaning it up:))

**data_backup**: (client side script)
```
#!/bin/bash
####################################
#
# 03.04.12
#
# TODO: implement wakeonlan into script. Have worked out a working solution, simply needs integrating into this script.
#
# Backup script for backing up files onto a remote SSH server using rsync. Meant for running hourly.
# Requires ssh login with RSA keys.
# If there's another rsync process running (on server side) for unreasonably long time, error report gets sent onto mail (requires msmtp to be installed and configured).
# (example msmtp config file, that should be located at $HOME/.msmtprc  : http://msmtp.sourceforge.net/doc/msmtprc.txt )
#
# Requires creating folder '.rsync' into home folder.    ( mkdir $HOME/.rsync )
# Obviously requires rsync
#
# To set the script run every hour: 'crontab -e' and enter new line: '0 * * * * /usr/local/bin/data_backup'    # Assumes the filename is 'data_backup' and located at /usr/local/bin
# Once a week with --delete flag (with prompt): '0 1 * * 0 xfce4-terminal --command="data_backup delete automated"'    # This example is obviously for xfce4 terminal.
#
# Usage:    data_backup
#        data_backup delete        # Adds --delete flag to rsync command, so the files not existing on client will get removed.
#        data_backup delete automated    # Automated variable adds few extra messages and closing prompt in the beginning (works only with 'delete' variable)
#
# Written by Laur Aliste <laur.aliste ät gmail>
# Great thanks to user dstewart on http://forums.fedoraforum.org/, whose solutions (http://forums.fedoraforum.org/showpost.php?p=1430792&postcount=5) are also used here.
###########################################################################################################
user="serveruser"                # Remote user to login to.
host_LAN="192.168.1.101"        # Remote host LAN address
host_WAN="host.com"            # Remote host WAN address. www.no-ip.com or similar service can be used for obtaining static hostname.
host_home="home/$user"            # Location of relevant files on host
email=""                # Where to send the error report to
email2=""                # ... and a copy (optional)
errorfile="/tmp/.error.dat"        # Name and location of temporary errorfile, that gets sent to email and error logfile
error_log="$HOME/.rsync/.error.log"    # Name and location of rsync error logfile    # This script writes into it, not rsync itself.
rsync_log="$HOME/.rsync/rsync.log"    # Name and location of rsync logfile    # Rsync will log into this file, not this script.
status_file=".rsync/.status_check.dat"    # Name of the system status file. This will be used by client to determine whether the server is online. Do not forget creating this file on the server!
limit="5M"                # Limits the maximum file size to be uploaded in case the connection is established over WAN (for saving bandwidth). Do not leave this option empty. If you don't need this, simply enter a large number. Accepted suffixes K, M and G.
blockfile=".rsync/.blockfile.dat"    # Name of the system rsync block file. Rsync will not start if this file exists (prevents simultaneous rsync processes on client and server. Also helps notifying if one of the rsync processes hasn't finished correctly.)
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
bold="tput smso"
offbold="tput rmso"

########################################### Argument check ###########################################
if [[ $# > 2 ]]; then
    echo "====================================================="
    echo "                  Too many arguments!"
    echo "====================================================="; exit 1
elif ! [[ -z $1 ]]; then
    clear
    if [[ "$1" == "delete" ]]; then
        if ! [[ -z $2 ]]; then
            if [[ "$2" != "automated" ]]; then
                echo "====================================================="
                echo "  Only \"automated\" is accepted as second argument"
                echo "====================================================="; exit 1
            else
                $bold
                echo "This is a weekly automated script for backing up with --delete flag."
                $offbold
            fi    
        fi
        echo "Delete files at remote host that no longer exist on the client?"
        echo -e "i.e. add --delete flag?  (y/n)\n"
        read prompt
        if [[ "$prompt" == "y" ]]; then
            delete_flag="--delete --delete-before"
            clear
            $bold
            echo "--delete flag selected"
            $offbold
        else
            clear
            $bold
            echo "--delete flag NOT selected"
            $offbold
        fi
            sleep 2
    else
        echo "====================================================="
        echo "    Only \"delete\" is accepted as first argument"
        echo "====================================================="; exit 1
    fi
fi
########################################### FUNCTIONS ###########################################
# Error compilation:
function report {
    echo -e "To: $email\nCc: $email2" > $errorfile
    echo -e "Subject: $subject" >> $errorfile
    echo -e "$body" >> $errorfile
    mail_sent=0
    echo $(date) >> $errorfile
    sed -e '/'$email'/d'   \
           -e '/'$email2'/d' < $errorfile >> $error_log
    if [[ "$connection" == "1" ]]; then
        msmtp -t < $errorfile            # sends the email
        mail_sent=1
    fi
    clear
    echo -e "$feedback"
    if [[ "$mail_sent" == "1" ]]; then
        echo "An error report was sent onto predefined email account."
        echo "This error was successfully reported." >> $error_log
    else
        echo "Error report was not sent onto email. Probable cause: internet connection offline."
        echo "!!! This error was NOT reported" >> $error_log
    fi
    echo "-------------------------------------------------------------------" >> $error_log
}
################################################################################################
# Check whether the client is connected to the internet:
if ping -W 2 -c 1 google.com > /dev/null 2>&1; then
    connection=1
else
    connection=0
fi
# Check whether to connect via LAN or WAN; send report if connection cannot be established either way or other error occurs:
ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -n $user@$host_LAN test -f /$host_home/$status_file > /dev/null 2>&1
status=$?
if [[ "$status" == "0" ]]; then
    host=$host_LAN
elif [[ "$connection" == "1" ]] && [[ "$status" == "255" ]]; then    # i.e. there's internet connection and couldn't locally connect to server (status can only be 255)
    ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -n $user@$host_WAN test -f /$host_home/$status_file > /dev/null 2>&1
    status=$?
    limit_flag="--max-size=$limit"
    if [[ "$status" == "0" ]]; then
        host=$host_WAN
    elif [[ "$status" == "255" ]]; then
        subject="rsync: server unreachable.\n"
        body="SSH server unreachable via LAN nor WAN, but client has active Internet connection. Check the server.\n(Exit code 255 @WAN)"
        feedback="Server offline or client connection faulty."
        report
        exit 1
    fi
elif [[ "$status" == "1" ]]; then
    subject="rsync: server reachable, but status file cannot be read.\n"
    body="SSH server is reachable via LAN or WAN, but the status file cannot be read. Check the server.\n(Exit code 1 @ LAN or WAN)"
    feedback="Server online, but the status file could not be read."
    report
    exit 1
elif [[ "$status" == "255" ]]; then
    subject="rsync: server unreachable.\n"
    body="SSH server unreachable via LAN and client has no active Internet connection. Check the server or client connection.\n(Exit code 255 @ LAN)"
    feedback="SSH server unreachable via LAN and client has no active Internet connection. Check the server or client connection.\n(Exit code 255 @ LAN)"
    report
    exit 1
else
    subject="rsync: unexpected error; abort.\n"
    body="Unexpected exit code: neither 0, 1 nor 255."
    feedback="Unexpected error; abort."
    report
    exit 1
fi
# What to backup:
backup_files="$HOME/Documents $HOME/Desktop $HOME/Music $HOME/Pictures $HOME/.gnome2 $HOME/.mpd $HOME/.ncmpcpp $HOME/.ssh $HOME/.fonts.conf $HOME/.msmtprc $HOME/.conky"
# Where to backup to:
dest="$user@$host:/$host_home/Documents/8510w_backups/running_backups/"    # Here $HOME cannot be used, unless the server and client usernames match.
#################################################################################################
count=5

# Check whether there are other rsync process currently running (i.e. check for blockfile):
ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -n $user@$host test -f /$host_home/$blockfile > /dev/null 2>&1
status=$?
if [[ "$status" == "0" ]]; then
    until [[ "$status" == "1" ]] || [[ "$count" == "0" ]]; do    # Wait until already running rsync process finishes.
        clear
        $bold
        echo "Other rsync process in progress."
        $offbold
        echo "Sleeping for 5 min and then trying again ($count attempt(s) remaining)..."
        sleep 300
        ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -n $user@$host test -f /$host_home/$blockfile > /dev/null 2>&1
        status=$?
        let count=$count-1
    done
    if [[ "$count" == "0" ]]; then    # If already running rsync process didn't end, then print error, compile error file and send to email account.
        subject="rsync error on client machine.\n"
        body="Rsync blockfile remained present. Error sent from client."
        feedback="There seems to be a problem with current running rsync process\nor server itself. Please try again or check the server; aborting."
        report
        exit 1
    fi
elif [[ "$status" == "255" ]]; then
        subject="rsync error on client machine.\n"
        body="For some reason, server has become unreachable during the process.\n(Exit code 255 on blockfile)"
        feedback="For some reason, server has become unreachable during the process.\n(Exit code 255 on blockfile). Abort."
        report
        exit 1
elif [[ "$status" != "1" ]]; then
        subject="rsync error on client machine.\n"
        body="Unexpected error.\n(Exit code on blockfile neither 0, 1, nor 255) Abort."
        feedback="Unexpected error.\n(Exit code on blockfile neither 0, 1, nor 255) Abort."
        report
        exit 1
fi

echo "Presence of this file indicates that a rsync process is running on client side" | ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no $user@$host "cat > /$host_home/$blockfile" > /dev/null 2>&1    # Create blockfile, so server side couldn't start syncing while client's process is running.

# Feedback:
$bold
echo "Backing up $backup_files"
$offbold
echo "to"
$bold
echo "$dest"
$offbold
# Syncing commands:
rsync -ravh $delete_flag $limit_flag --log-file=$rsync_log $backup_files $dest
syncstat=$?
echo "-------------------------------------------------------------------" >> $rsync_log
rsync_exit_stat="rsync exit status code legend;
0\tSuccess
1\tSyntax or usage error
2\tProtocol incompatibility
3\tErrors selecting input/output files, dirs
4\tRequested  action not supported: an attempt was made to manipulate 64-bit files on a platform that cannot support them; or an option was specified that is supported by the client and not by the server.
5\tError starting client-server protocol
6\tDaemon unable to append to log-file
10\tError in socket I/O
11\tError in file I/O
12\tError in rsync protocol data stream
13\tErrors with program diagnostics
14\tError in IPC code
20\tReceived SIGUSR1 or SIGINT
21\tSome error returned by waitpid()
22\tError allocating core memory buffers
23\tPartial transfer due to error
24\tPartial transfer due to vanished source files
25\tThe --max-delete limit stopped deletions
30\tTimeout in data send/receive"
#
# Check for rsync errors and compile message if detected:
if [[ "$syncstat" != "0" ]]; then
    subject="rsync completed with an error (on client).\n"
    body="Rsync error code: $syncstat\n\n$rsync_exit_stat"
    feedback="Rsync completed with an error. Check log for more info."
    report
fi
# Most usable rsync flags: 
#    -r = recursive
#    -a = archive; preserves all attributes like ownership, timestamps, etc; also copies symlinks
#    -z = compress; saves bandwidth but is harder on your CPU so use it for slow/expensive connections only
#    -u = skip files that are newer on the receiver (avoids copying the files that we already have in the destination folder that have not been modified in the source folder.)
#    -h = output numbers in a human-readable format, i.e. the file sizes are given in K's, M's, G's
#    -e = specify the remote shell to use (e.g. -e ssh)
#    -v = verbose; this parameter will print information about the execution of the command, such as the files that are successfully transferred, so we can use this as a way to keep track of the progress of rsync.
#    --size-only = compare files based on their size instead of hashes (less CPU, so faster) i.e. skip files that match in size
#    --progress = shows you the progress of all the files that are being synced
#    --delete = delete files remotely that no longer exist locally
#    --dry-run = show what would have been transferred, but do not transfer anything    
#    --delete-before = receiver deletes files that don't exist in the source before xfer, not during
#    --log-file=/var/log/rsync.log = self explanatory
#    --max-size=SIZE = don't transfer any file larger than SIZE    # Available suffixes are  M,K and G
#    --min-size=SIZE = don't transfer any file smaller than SIZE    # Available suffixes are  M,K and G


# Print end status message:
$bold
echo "Backup finished"
$offbold
ssh -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no $user@$host "rm /$host_home/$blockfile" > /dev/null 2>&1    # Remove blockfile when finished.
if [[ "$2" == "automated" ]]; then
    echo "Press enter to close the window..."
    read dummy_variable    # Prevents opened terminal window from closing automagically.
fi
exit
```**server_backup**: (server side script)
```
#!/bin/bash
####################################
#
# 03.04.12
#
# Backup script for syncing two disks on a server using rsync. Meant for running once a week.
# If there's another rsync process running (on client side) for unreasonably long time, error report gets sent onto mail (requires msmtp to be installed and configured).
# More explanatory comments in data_backup script (client side script).
#
# Requires creating folder '.rsync' into home folder.    ( mkdir $HOME/.rsync )
# Obviously requires rsync.
#
# To set the script run every hour: 'crontab -e' and enter new line: '30 * * * * /usr/local/bin/server_backup'    # Assumes the filename is 'server_backup' and located at /usr/local/bin
# Weekly: 0 0 * * 0 /usr/local/bin/server_backup    # Runs at midnight on Sunday
#
# Written by Laur Aliste <laur.aliste ät gmail>
# Great thanks to user dstewart on http://forums.fedoraforum.org/, whose solutions (http://forums.fedoraforum.org/showpost.php?p=1430792&postcount=5) are also used here.
#################################### EDIT ONLY THESE VALUES: ####################################
backup_files="$HOME/Documents/8510w_backups"    # What to backup. (If a slash is at the end of a folder name, then only the contents will be backed up into $dest instead of the folder itself.)
dest="/media/60gb/backups/"            # Where to backup to (second HDD mountpoint for instance)
errorfile="/tmp/.error.dat"            # Name and location of temporary errorfile, that gets sent to email
error_log="$HOME/.rsync/.error.log"        # Name of rsync error file    # This script writes into it, not rsync itself.
rsync_log="$HOME/.rsync/rsync.log"        # Name and location of rsync logfile    # Rsync will log into this file, not this script.
email=""                    # Where to send the error report to
email2=""                    # ... and a copy (optional)
blockfile="$HOME/.rsync/.blockfile.dat"        # Name of the system rsync block file. Rsync will not start if this file exists (prevents simultaneous rsync processes on client and server. Also helps notifying if one of the rsync processes hasn't finished correctly.)
#################################################################################################
bold="tput smso"
offbold="tput rmso"
########################################### FUNCTIONS ###########################################
# Create function of adding a dateline, logfile cleanup and sending mail if there's active internet connection:
function report {
    echo -e "To: $email\nCc: $email2" > $errorfile
    echo -e "Subject: $subject" >> $errorfile
    echo -e "$body" >> $errorfile
    mail_sent=0
    echo $(date) >> $errorfile
    sed -e '/'$email'/d'   \
           -e '/'$email2'/d' < $errorfile >> $error_log
    if [[ "$connection" == "1" ]]; then
        msmtp -t < $errorfile            # sends the email
        mail_sent=1
    fi
    clear
    echo -e "$feedback"
    if [[ "$mail_sent" == "1" ]]; then
        echo "An error report was sent onto predefined email account."
        echo "This error was successfully reported." >> $error_log
    else
        echo "Error report was not sent onto email. Probable cause: internet connection offline."
        echo "!!! This error was NOT reported" >> $error_log
    fi
    echo "-------------------------------------------------------------------" >> $error_log
}
################################################################################################
# Check for internet connection:
if ping -W 2 -c 1 google.com > /dev/null 2>&1; then
    connection=1
else
    connection=0
fi
count=5
# Check whether there are other rsync process currently running:
if [ -f $blockfile ]; then 
    until [ ! -f $blockfile ] || [[ "$count" == "0" ]]; do
        clear
        $bold
        echo "Other rsync process in progress."
        $offbold
        echo "Sleeping for 5 min and then trying again ($count attempt(s) remaining)..."
        sleep 300
        let count=$count-1
    done
    if [[ "$count" == "0" ]]; then
        subject="rsync error on server.\n"
        body="Rsync blockfile remained present. Error sent from server."
        feedback="There seems to be a problem with current running rsync process. Please try again\nor check the client running the process; aborting."
        report
        exit 1
    fi
fi
echo "Presence of this file indicates that a rsync process is running on server side" > $blockfile

# Feedback:
$bold
echo "Backing up $backup_files"
$offbold
echo "to"
$bold
echo "$dest"
$offbold
# Syncing commands:
rsync -ravh --delete --delete-before --log-file=$rsync_log $backup_files $dest
syncstat=$?
echo "-------------------------------------------------------------------" >> $rsync_log
rsync_exit_stat="rsync exit status code legend;
0\tSuccess
1\tSyntax or usage error
2\tProtocol incompatibility
3\tErrors selecting input/output files, dirs
4\tRequested  action not supported: an attempt was made to manipulate 64-bit files on a platform that cannot support them; or an option was specified that is supported by the client and not by the server.
5\tError starting client-server protocol
6\tDaemon unable to append to log-file
10\tError in socket I/O
11\tError in file I/O
12\tError in rsync protocol data stream
13\tErrors with program diagnostics
14\tError in IPC code
20\tReceived SIGUSR1 or SIGINT
21\tSome error returned by waitpid()
22\tError allocating core memory buffers
23\tPartial transfer due to error
24\tPartial transfer due to vanished source files
25\tThe --max-delete limit stopped deletions
30\tTimeout in data send/receive"
#
# Check for rsync errors:
if [[ "$syncstat" != "0" ]]; then
    subject="rsync completed with an error (on server)\n"
    body="Rsync error code: $syncstat\n\n$rsync_exit_stat"
    feedback="Rsync completed with an error. Check log for more info."
    report
fi    
# Most usable rsync flags: 
#    -r = recursive
#    -a = archive; preserves all attributes like ownership, timestamps, etc; also copies symlinks
#    -z = compress; saves bandwidth but is harder on your CPU so use it for slow/expensive connections only
#    -u = skip files that are newer on the receiver (avoids copying the files that we already have in the destination folder that have not been modified in the source folder.)
#    -h = output numbers in a human-readable format, i.e. the file sizes are given in K's, M's, G's
#    -e = specify the remote shell to use (e.g. -e ssh)
#    -v = verbose; this parameter will print information about the execution of the command, such as the files that are successfully transferred, so we can use this as a way to keep track of the progress of rsync.
#    --size-only = compare files based on their size instead of hashes (less CPU, so faster) i.e. skip files that match in size
#    --progress = shows you the progress of all the files that are being synced
#    --delete = delete files remotely that no longer exist locally
#    --dry-run = show what would have been transferred, but do not transfer anything    
#    --delete-before = receiver deletes files that don't exist in the source before xfer, not during
#    --log-file=/var/log/rsync.log = self explanatory
#    --max-size=SIZE = don't transfer any file larger than SIZE    # Available suffixes are  M,K and G
#    --min-size=SIZE = don't transfer any file smaller than SIZE    # Available suffixes are  M,K and G

# Print end status message:
$bold
echo "Backup finished"
$offbold
rm $blockfile
exit
```

---

### Post by papibe on 2012-04-03
Thanks for sharing those scripts :)

> **layr said:**
> Ok, then I'll leave the script as it is. Unfortunately my ISP is blocking ports, so I'm unable to test it.

ssh's port is very well known (22), so it's usually blocked. However, it can be easily change. I would try one on the the dynamic range (49152 to 65535).

You would have to adjust your scripts accordingly.

Tell us if you need more help with that.
Regards.

---

### Post by layr on 2012-04-04
> **papibe said:**
> Thanks for sharing those scripts :)
No problem. I'm probably pausing the further development for some time. I first thought the script would be 10 lines or so, but it grows and grows. It's time to actually learn bash a bit (not everything can be done with if-s and elses :D)
> **papibe said:**
> ssh's port is very well known (22), so it's usually blocked. However, it can be easily change. I would try one on the the dynamic range (49152 to 65535).
Regards.
I've tried it already. Default ports have been changed in sshd and ssh configs. It's never good idea to run your server on port 22.

---


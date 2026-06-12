---
title: "Trouble Building A Server"
date: 2012-02-29
forum: Networking &amp; Wireless
---

### Post by deckerry on 2012-02-29
It looks long, but if you want the quick details, just read the dark text.

----------------------------------------
The Short Story:
----------------------------------------

     Hi. I tried following the directions on this page [http://www.intac.net/build-your-own-server](http://www.intac.net/build-your-own-server) so I could build a server.

     I even made a script that does everything on that tutorial except auto-login and configure and run putty.

     I was almost 100% that I did everything correct and guess what. It didn't work.

     Plus, I have no idea how to use PUTTY so my misconfiguring that program might be the whole reason why I'm having a problem. (Actually I don't know much about proftp or vnc either.)

----------------------------------------
The Long Story:
----------------------------------------

    [COLOR="DimGray"] I tried this originally on Debian 6 as a virtual machine without a GUI. I couldn't get it to work. So I installed LXDE in Debian and wrote a script based on the instructions on that web page that I mentioned earlier ([http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/)) because I was tired of going back and forth in the terminal. I still couldn't get it to work.

     Then I remembered that I had Xubuntu 10.04 Lucid installed on another computer - a real machine (not virtual). I decided to try my script on that computer because I thought maybe it wasn't working on Debian because it was a virtual machine.

----------------------------------------
The Script:
----------------------------------------

[COLOR="DimGray"]I recommend only running this in a virtual machine so that it doesn't change your SAMBA, PROFTP, AND VNC settings.

Most of the commands have been commented out to protect users from changing something they might not want to change.

So, [/COLOR]to use this script, you'll have to remove the appropriate # marks.

```
#!/bin/sh




#############################################
# This explains that you have to or "sudo su" to make this script work.

clear
echo ----------------------------------------------------
echo "I hope you're ready to set-up your server!!!"
echo "F-YEA!!!!!!"
echo ----------------------------------------------------

echo
echo 'If you did not use the "sudo su" command before running
this program, then it will most likely fail. If so, then quit
this program (either by clicking the "x" to close the terminal
or by using pushing "ctrl+c") and start it again.

If you did use "sudo su", then just push enter.'
read poop
echo $poop








# This is step 4 from this tutorial: http://www.intact.net/build-your-own-server/








############################################
#update the package manager

#apt-get update
#apt-get upgrade

#########################################
#        SAMBA            #
#########################################

##################################
#Install samba

#apt-get install samba

###################################
#Backup smb cfg!!!!!

#mv /etc/samba/smb.conf /etc/samba/smb.conf.bak

###################################
#Update samba config:

#Manually or...

#sudo TEXTEDITOR /etc/samba/smb.conf

#...Automatically

#echo '[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "workgroup"
netbios name = "ryan"
invalid users = root
security = user
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no

#Share Definitions

[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700' > /etc/samba/smb.conf

######################################
#Restart Samba: (Use only one of these two-whichever one is compatible
#with your system.)

#/etc/init.d/samba restart
#service smbd stop;service smbd start

######################################
#Samba Password:

#smbpasswd -a SAMBAUSER









# This is step 5 from this tutorial: http://www.intact.net/build-your-own-server/







#########################################
#        proFtp config        #
#########################################

########################################
#Install proftp

#apt-get install proftpd

#######################################
#Create proftp.conf

#Manually or...

#sudo TEXTEDITOR /etc

#...Automatically

#echo 'ServerName            "ENTER A NAME"
ServerType            standalone
ServerIdent            on        "ENTER A NAME"
DeferWelcome            on
DefaultServer            on

DisplayLogin            .welcome    # Textfile to display on login
DisplayConnect            .connect    # Textfile to display on connection
#DisplayFirstChdir               .firstchdir    # Textfile to display on first changedir

UseReverseDNS               off
IdentLookups                off

Port                21
Umask                022
MaxInstances                    15
MaxClientsPerHost               3         "Only %m connections per host allowed"
MaxClients                      10         "Only %m total simultanious logins allowed"
MaxHostsPerUser                 1

User                nobody
Group                nogroup

ScoreboardFile             /var/log/scoreboard

# Some logging formats
LogFormat                    default     "%h %l %u %t \"%r\" %s %b"
LogFormat                    auth        "%v [%P] %h %t \"%r\" %s"
LogFormat                    write       "%h %l %u %t \"%r\" %s %b"

# Define log-files to use
TransferLog                  /var/log/proftpd.xferlog
ExtendedLog                 /var/log/proftpd.access_log    WRITE,READ write
ExtendedLog                  /var/log/proftpd.auth_log      AUTH auth
ExtendedLog                  /var/log/proftpd.paranoid_log  ALL default


AllowStoreRestart         on
AllowRetrieveRestart        on
RequireValidShell               off
PathDenyFilter                  "\\.ftp)|\\.ht)[a-z]+$"
DefaultRoot             /
DenyFilter             \*.*/

ListOptions            "" strict
' > /etc/proftpd/proftpd.conf

########################################
#Backup proftp

#cp /etc/proftpd/proftpd.conf /etc/proftpd/proftpd.conf.bak

########################################
#Restart proFtp

#/etc/init.d/proftpd restart









# This is step 6 from this tutorial: http://www.intact.net/build-your-own-server/












#########################################
#        Install SSH        #
#########################################
apt-get install openssh-server

#########################################
#        Install VNC        #
#########################################
apt-get install x11vnc
apt-get install vnc4server
apt-get install tightvncserver

########################################
#Make a password directory.
#This will give an error if the .vnc folder already exists.
#You can most likely just ignore this error because I haven't learned
#"if then else" commands yet

#mkdir /home/USER/.vnc
#echo "If you already have a .vnc folder,"
#echo 'then ignore the "already exists" error.'

#########################################
#Set vnc password

#echo
#echo "Set a password for VNC."
#vncpasswd /home/USER/.vnc/passwd

#######################################
#Open the port

#echo 5900 > /home/USER/.vnc/port

##########################################
#create custom login program
#echo '#!/bin/sh
x11vnc -nap -bg -many -rfbauth /home/ryan/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}" \
|grep -Eo "[0-9]{4}">/home/ryan/.vnc/port' > /usr/local/bin/sharex11vnc

#########################################
#make it executable

#chmod 755 /usr/local/bin/sharex11vnc

#########################################
#autostart vnc

#cp /usr/local/bin/sharex11vnc /etc/init.d/sharex11vnc

#########################################
#Figure out how to script autologin!    #
#########################################
echo 
echo 
echo 
echo 
echo 
echo 
echo 
echo 
echo "Done! Congratulations! I hope you didn't get any errors!"
echo 
echo ------------------------------------------------------------
echo 'If you see the "#" prompt instead of the "$" prompt then
you are logged in as root and might completely destroy your
computer if you do not log out of root and back to your normal
user account.

If you see "#," simply push Enter, then use the "exit" command.
If you see "$," instead then nevermind. If you have no idea what
I am talking about, then just push Enter, then type "exit" and
push Enter again.'
echo ------------------------------------------------------------


read poop
$poop
```

[COLOR="DimGray"]P.S. I have spent hours and hours on this stupid project so I'm pulling my hair out at this point. And this is my second script ever written so even though it seems to be a failure at this point, I'm pretty proud of it anyway.[/COLOR]

---


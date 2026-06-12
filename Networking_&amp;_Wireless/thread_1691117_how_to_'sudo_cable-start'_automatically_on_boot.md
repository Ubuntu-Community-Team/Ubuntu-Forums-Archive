---
title: "how to 'sudo cable-start' automatically on boot ?"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by doron387 on 2011-02-19
hi guys,
i use ubuntu 10.10 installed in wubi on my girlfriend's machine.
in order to connect to the internet i had to install a dialer script and then i need to type in terminal :
sudo cable-start
and then password
BUT 
i wish this to happen automatically when booting the machine.
i am sure that it is possible, but have no clue how to do it, 
will you help me please ?
thanks
doron387

---

### Post by Rubi1200 on 2011-02-19
Hi,
Who is the ISP?

Can you provide a link for the instructions you used to set this up?

Do you have a cable modem or wireless router?

Thanks.

---

### Post by doron387 on 2011-02-19
the ISP is an Israeli company, named 012-BARAK.
the istructions were to download a folder with a dialer program, 
then go to terminal and type everytime that i want internet connection : sudo cable-start.
it's a cable modem connection.
here is the code of the dialer program, note that i 'commented' the first 4 lines that made a problem : asked me continuously for root password.

the code :[COLOR="Blue"]
#!/bin/sh
#Made by Marcelo A.

# Must be root
#if test "$UID" != 0 ; then
# echo -e "This script must be run as root.\nType in root password, please."
# exec su -c "DISPLAY=$DISPLAY $0"
# exit 1
#fi
   
# Must have pppd
if [ ! -x "`which pppd`" ] ; then
    echo "Oops, I can't execute the program pppd.  You"
    echo "must install the PPP software suite, version 2.3.10 or later."
    exit 1
 fi

# If pptp or pptp-linux aren't found ,abort installation
if ! [ -x /usr/sbin/pptp-linux -o -x ./pptp-linux -o -x "`which pptp`" ] ; then
    echo "Can't execute the program pptp. You should" 
    echo "install the pptp linux client that comes with your distribution ,version 1.1.0 or later"
    echo ""
    echo "NOTE! ,Mandrake users should install the package pptp-adsl *NOT* pptp-linux!"
    echo ""
    echo "If all fails and your distro dosen't come with a pre-compiled pptp" 
    echo "client, you could try the one in ./scripts , just copy it"
    echo "to the parent directory .. or /usr/sbin"
  
  exit 1
fi

if ! pptp 2>&1 |grep "nolaunchpppd" 2>&1 > /dev/null ; then
 LINUXPPTP="./scripts/pptp-linux"
   echo "Your pptp client is old, consider upgrading ppp and pptp to the latest version..."
   echo "Using pptp-linux binary..."
fi
     
mkdir -p /usr/sbin
for i in ip-up-bak ; do 
        if [ ! -x /etc/ppp/$i ] ; then 

           if [ -x /etc/ppp/ip-up ] ; then

echo "Backing up /etc/ppp/ip-up and /etc/ppp/ip-down to ip-up-back and ip-down-bak"
               cp -d /etc/ppp/ip-up /etc/ppp/ip-up-bak
               cp -d /etc/ppp/ip-down /etc/ppp/ip-down-bak
               install -c -m 755 ./scripts/ip-* /etc/ppp ; 
           fi
        else 
                echo "NOT overwriting existing /etc/ppp/$i ip-down-bak" ;
                echo "Consider running Uninstall before Reinstalling again.." 
        fi 
done
	
#Nasty hack that checks if /usr/sbin is writable 
#case it isn't, it will place cable-s* files in current directoy;
#solves the issue with live-cds where /usr/sbin is readonly
for i in ./scripts/cable-s* ; do
  if ( : > /usr/sbin/1234a ) &>/dev/null ; then
install -c -m 755 $i $LINUXPPTP /usr/sbin
rm -f /usr/sbin/1234a
  else
install -c -m 755 $i $LINUXPPTP ./
  fi     
done 

mkdir -p /etc/ppp

for i in pptp.conf ; do 
        if [ ! -f /etc/ppp/$i ] ; then 
                install -c -m 644 ./config/$i /etc/ppp 
        else 
                echo "NOT overwriting existing /etc/ppp/$i" 
                install -c -m 644 ./config/$i /etc/ppp/$i-1.0 
        fi 
done
									
if [ -f /etc/redhat-release ] ; then 
        echo "Looks like a Red Hat system; installing /etc/rc.d/init.d/cable" 
        mkdir -p /etc/rc.d/init.d 
        install -c -m 755 ./scripts/cable-init /etc/rc.d/init.d/cable 
fi
if [ -f /etc/turbolinux-release ] ; then 
        echo "Looks like a TurboLinux system; installing /etc/rc.d/init.d/cable" 
        mkdir -p /etc/rc.d/init.d 
        install -c -m 755 ./scripts/cable-init-turbolinux /etc/rc.d/init.d/cable 
fi
if [ -f /etc/SuSE-release ] ; then 
        echo "Looks like a SuSE Linux system; installing /etc/rc.d/init.d/cable" 
        mkdir -p /etc/rc.d/init.d 
        install -c -m 755 ./scripts/cable-init-suse /etc/rc.d/init.d/cable 
fi
echo ""
exec sh ./scripts/cable-setup[/COLOR]

---

### Post by Rubi1200 on 2011-02-19
I don't think you need to do this. Ubuntu is very good at recognizing these types of connections. Just plug the ethernet cable from the modem into the computer and you should be automatically connected.

---


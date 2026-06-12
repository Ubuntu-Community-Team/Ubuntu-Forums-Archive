---
title: "Can't automate IP script at login"
date: 2012-03-16
forum: Networking &amp; Wireless
---

### Post by wannabe user on 2012-03-16
**SOLVED**
I'll post how I solved it, it might help someone in the future

Basically the script was running, however it couldn't find the macsip file that contains the IP addresses, I'm assuming this is because the script is ran as root and the file is stored in the user dir. 

Ah well.
************


Title maybe isn't great. The script assigns an IP based on a MAC address, I have a Perl script and a basic shell script to test if I can get either to work. I've tried starting them in several different ways, from startup applications, to rc.local and even upstarts.

Both scripts work fine if they're executed from the terminal when I'm logged in, however getting them to do this when the user logs in seems to be a problem. I know I can do what these scripts do in other ways, such as DHCP but this is the method I need.

My conclusion is, that network manager, or network connections as it seems to be called is starting after the script executes thus overriding the script. This may seem obvious I may be wrong, I don't know enough and I'm going mad trying to work it out. The reason I think this is because I entered a sleep command of 2 minutes and then tried 4 minutes and sure as anything startup was delayed on reboot, so I know something is happening :confused:.

I've also ran it with startup applications using xterm, I left sudo command in the script and it worked, in the sense the script did start and I was asked for the sudo password, however entering the password is fine but the script doesn't actually work; again leading me to believe the beginning of the script has been executed early.


Does anyone know if I'm going in completely the wrong direction or have anything they might be able to help me with. I don't need DHCP or really anything so it can all be disabled if needs be. Here are the scripts if that helps. 

The Perl script will read from the macsip file, find its MAC and use the IP from it, as I say it works fine if I run it from terminal. The other script is something I've just been using for testing to see if it's my dodgy Perl.

Any help is very appreciated at this point.

```
#!/usr/bin/perl
#
#Script to set IP based on MAC address.
#
#use warnings;
use strict;
#
#Global variables
#sleep 120;
my @mac = ();
my @eth = ();
my @nameserver = ("192.168.19.254","192.168.19.253");
#
my $ipadd = "";
my $host = "";
my $currentmac = "";
my $interface = "";
my $mask = "255.255.255.0";
my $gateway = "192.168.19.254";
#
#For loop to get all MAC addresses - push these to the mac array
for (my $i=0; $i<5; $i++){
    #Get the current MACs
    my $rec = `/sbin/ifconfig eth$i | grep "HWaddr"`;
    my ($eth, $field2, $field3, $field4, $cmac) = split(/\s+/, $rec);
    push (@mac, "$cmac");    
    push (@eth, "$eth");
}
#Parse macsip file, if MAC mataches assign hostname and ip address variable.
#Open the file containing MACs
open (FILE, 'macsip');
while (<FILE>){
    chomp;#Chomp the whitespace
    my ($temphostname, $tempmac, $tempip) = split("\t");
    for (my $i=0; $i<5; $i++){
    if($mac[$i] eq $tempmac){
        $ipadd = $tempip;
        $host = $temphostname;
        $currentmac = $mac[$i];
        $interface = $eth[$i];
        goto END;#If MAC mathces before 5, break from the loop
        }
    }
}
END:#End for MAC address.
close (FILE);#Close the file containing MACs
#
#kill DHCP, assign IP, gateway and DNS.
system "killall dhclinet";
system `sudo ifconfig $interface up $ipadd netmask $mask`;
#system "sudo ip route add default via $gateway";
#
open ( DNS, ">resolv.tmp");
print DNS "nameserver $nameserver[0]\n";
print DNS "nameserver $nameserver[1]\n";
close (DNS);
system "sudo mv resolv.tmp /etc/resolv.conf";
#
system "sudo /etc/init.d/networking restart";
```The macsip file:
```
PC1    08:00:27:16:4a:0d    192.168.19.223
PC2    08:00:27:f9:fd:96    192.168.19.2
PC3    00:11:22:33:44:55    192.168.19.3
PCtest    08:00:27:57:ab:b3    192.168.19.19
```And the test shell script:
```
#!/bin/sh

#Bobby Basic script to change IP address.


#MAC addresses for each system
pc1mac="08:00:27:16:4a:0d"
pc2mac="08:00:27:f9:fd:96"
pc3mac="00:11:22:33:44:55"

#Get the current MAC for eth0
cmac=`ifconfig | grep 'eth0' | tr -s ' ' | cut -d ' ' -f5`

#Check the current mac against each system - assign ipadd variable required IP
if [ $cmac = $pc1mac ]
    then
    ipadd=192.168.1.1
fi
if [ $cmac = $pc2mac ]
    then
    ipadd=192.168.1.2
fi
if [ $cmac = $pc3mac ]
    then
    ipadd=192.168.1.3    
fi

#kill DHCP, assign IP, gateway and DNS.
killall dhclinet
sudo ifconfig eth0 up $ipadd netmask 255.255.255.0
sudo route add default gw 192.168.1.254


echo "nameserver 192.168.1.254" >> resolv.tmp
sudo mv resolv.tmp /etc/resolv.conf

sed '/^options.*/d' /etc/resolv.conf >>resolv.tmp
echo "options retrans:1 retry:1" >> resolv.tmp
sudo mv resolv.tmp /etc/resolv.conf

sudo /etc/init.d/networking restart

```

---

### Post by MrSaltyBeard on 2013-03-12
How did you solve the problem??
 Thanks for what you have posted.

---


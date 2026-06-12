---
title: "vpnc with Nortel Contivity VPN using group auth"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by ghat on 2009-07-02
hi

This is in continuation of

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=441042](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=441042)

I just want to report success as of today on jaunty...

[B]DISCLAIMER: 
USE AT YOUR OWN RISK, PLEASE CONSULT YOUR COMPANY IT DEPARTMENT TO SEE IF THE FOLLOWING PROCEDURE
IS LEGAL. I AM NOT AND NO ONE IS, RESPONSIBLE FOR ANY OF YOUR ACTIONS AFTER READING THIS POST..[/B]

Here are my instructions... 

0. Install the compile tools

apt-get install build-essentials subversion
apt-get build-dep vpnc


1. Get the source code (note that I am mentioning release number as it is the most current release as of the day of this post, and has worked for me) 

   svn co -r 414 [http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel](http://svn.unix-ag.uni-kl.de/vpnc/branches/vpnc-nortel)

2. cd vpnc-nortel
3. vi Makefile # edit the PREFIX and set it to /usr
4. make

if all compiles well (which it should)

5. sudo make install

6. sudo mv /etc/vpnc/default.conf /etc/vpnc/default.conf.install

7.
Create the following config file..

> 
before this step, open your Windows Nortel Contivity client and connect as usual... 
next right-click the icon in the task-bar and open the status window
Note: the options for

Security: 
IKE: (Diffie Hellman=>"dh")
Compression:
Destination IP Address
IPSec NAT Traversal
etc... 

and write them down so you can see them when editing the file here..

next on your ubuntu box, type
vpnc --long-help
and see if any of the options noted above have any co-relation with the options available with vpnc... if so change them accordingly... 

vi /etc/vpnc/contivity-ip-split.conf

```

#===== /etc/vpnc/contivity-ip-split.conf
IPSec gateway XXX.XXX.XXX.XXX
IPSec ID COMPANY_GROUP_ID
IPSec secret COMPANY_GROUP_ID_PSK

# This is specific to  Nortel Contivity Server Config 
# please update accodingly
Vendor nortel
Nortel Client ID V06_01
IKE DH Group dh5
IKE Authmode gpassword

## To add your username and password,
## use the following lines:
Xauth username MY_LOGIN
Xauth password MY_PASSWD

Script /etc/vpnc/contivity-ip-split-script

# No Detach # This is for debugging purposes only... runs vpnc in foreground
# Debug 99  # Again for debug purposes check vpnc --long-help for verbosity levels
#            # NEVER post debug99 log on the internet, it  contains username and passwd


```8. sudo chmod 600 /etc/vpnc/contivity-ip-split.conf
9. Create the following split script...

vi /etc/vpnc/contivity-ip-split-script
```

#!/bin/sh
# ===== /etc/vpnc/contivity-ip-split-script

add_ip ()
{
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_ADDR=$1
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASK=255.255.255.255
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASKLEN=32
        export CISCO_SPLIT_INC=$(($CISCO_SPLIT_INC + 1))
}
add_Csubnet ()
{
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_ADDR=$1
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASK=255.255.255.0
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASKLEN=24
        export CISCO_SPLIT_INC=$(($CISCO_SPLIT_INC + 1))
}
add_Bsubnet ()
{
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_ADDR=$1
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASK=255.255.0.0
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASKLEN=16
        export CISCO_SPLIT_INC=$(($CISCO_SPLIT_INC + 1))
}
add_Asubnet ()
{
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_ADDR=$1
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASK=255.0.0.0
        export CISCO_SPLIT_INC_${CISCO_SPLIT_INC}_MASKLEN=8
        export CISCO_SPLIT_INC=$(($CISCO_SPLIT_INC + 1))
}

# Initialize empty split tunnel list
export CISCO_SPLIT_INC=0

# Delete DNS info provided by VPN server to use internet DNS
# Comment following line to use DNS beyond VPN tunnel
unset INTERNAL_IP4_DNS

# List of IPs beyond VPN tunnel
# These should be listed in /etc/hosts also...

add_ip 10.XXX.XXX.XXX  #email server
add_ip 10.YYY.YYY.YYY # www server
add_ip 10.AAA.BBB.CCC # your workstation
add_ip 10.ZZZ.ZZZ.ZZZ # some other server
# add_Asubnet 10.0.0.0     # full 10.0.0.0 private class A subnet
# add_Bsubnet 10.10.0.0   # eg class B subnet
# add_Csubnet 10.10.10.0 # eg class C subnet

# Execute default script
. /etc/vpnc/vpnc-script

# End of script

```Note that we are switching off the 'internal DNS' and hence name resolution is left upto
the /etc/hosts and my understanding is that you would want to access only a few hosts from your work instead of the whole network. In my case I am really content with my 
IMAP/mail server, the intra--office web-server, and my workstation on which I run VNC.
I usually work off my VNC so things run much faster than over the network... 

In theory you can write a split script which gives access to your whole companies intranet and run your own DNS server which can forward your queries appropriately, however I guess it is  more insecure, than using split which itself is insecure!!!

10.  chmod 700 /etc/vpnc/contivity-ip-split-script

11.  Finishing touches...
cd /etc/vpnc/
ln -s contivity-ip-split.conf default.conf

# create these 2 aliases in your .cshrc/..bashrc

alias vpnc 'sudo \vpnc'
alias vpnc-disconnect 'sudo \vpnc-disconnect'

# --------------------- ALL DONE  ------------------------------------

To connect type
vpnc

to disconnect type
vpnc-disconnect

Note that your contivity admin has configured a "MAX" for number of consecutive failed
login attempts, so my recommendation is if it does not work and you are playing around with your config to get it right, then use your WinDOZE box to connect and disconnect after every 2 failed tries using the method described here, else your account could get locked out..

Hope this helps... 

> 
toubleshooting tips

[LIST=1]
[*] : Feb 2011:
[/LIST]
[INDENT]Sometimes the company network is set to route packets through various subnets (I guess), so if a certain other IP address is not available as you specifically set the add_ip (without a custom route) then it will not work.. in this case you may want to use the add_*subnet functions... the worst/best scenario is to use a list of all subnets available in your company, which you can ping using[/INDENT][INDENT]e.g. (if you company uses the 10.0.0.0 class A private subnet. )
```

nmap -oG mySubnets.txt -sP 10.1-255.1-255.1-255 

```
(now that will take a really long time to run...) 
[/INDENT]
Ghat

---

### Post by finite9 on 2009-08-28
good guide!  lots of info on what to configure here.  I just wrote my own, thinking there werent any guides out there, and forgot to search ubuntuforums before i posted.  duh.  seems like the most recent versions of vpnc do not have any issues.

---

### Post by ghat on 2009-09-03
hi guys...

Here is how I solved the DNS problem after disabling the vpn-dns...

1. apt-get install bind9

2. vi /etc/bind/named.conf.options

put your ISP name servers here


```

        forwarders {
                192.168.0.1; // your home gateway router
                isp.dns1.ip_address ; // put your ISP primary DNS
                isp.dns2.ip_address ; // put your ISP secondary DNS
                208.67.222.222; // opendns1
                208.67.220.220; // opendns2
        };

```

3. In the example below I am assuming that your company intranet uses the complete private ip-address space 10.0.0.0
if it is different then the name of the reverse dns zone will change...see the bind9 manual or DNS RFQ's.

login to some machine inside your company network and find the DNS servers which are used... say these are

10.10.10.254 ns1.company.com
10.10.11.254 ns2.company.com

4. vi /etc/bind/named.conf.local

```

//
// Do any local configuration here
//
zone "company.com" {
        type forward;
        forwarders {
               10.10.10.254;
               10.10.11.254;
                192.168.0.1; // your home gateway router
                isp.dns1.ip_address ; // put your ISP primary DNS
                isp.dns2.ip_address ; // put your ISP secondary DNS
                208.67.222.222; // opendns1
                208.67.220.220; // opendns2
               };
        };

zone "**10.in-addr.arpa**" {
        type forward;
        forwarders {
               10.10.10.254;
               10.10.11.254;
                192.168.0.1; // your home gateway router
                isp.dns1.ip_address ; // put your ISP primary DNS
                isp.dns2.ip_address ; // put your ISP secondary DNS
                208.67.222.222; // opendns1
                208.67.220.220; // opendns2
               };
        };

zone "mydomain.homeip.net" {
       type master ;
       file "/etc/bind/zones/mydomain.homeip.net.db";
       };

zone "0.0.168.192.in-addr.arpa" {
       type master ;
       file "/etc/bind/zones/rev.0.0.168.192.in-addr.arpa.db" ;
       };

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

```5. Now point your /etc/resolv.conf to the localhost using


```
nameserver 127.0.0.1
```you can then check if the name resolution works... when the vpnc tunnel is up....

---

### Post by jwhendy on 2009-10-04
Serious apologies for bumping this old thread... I'm hoping it attracts the attention of some of the posters though, as I've not found a better source of info for vpnc-nortel and Contivity.

I think I've got everything done correctly EXCEPT that I cannot for the life of me figure out how to find my 'group secret.' Where in the world is this???

Is only my IT admin able to provide this? From the .tbk file on my work windows box, I can find the group ID, but not any hash or indication of a password. I just keep hitting enter when vpnc prompts and I think I'm on the right track, as instead of previous errors, it's not saying 'Check group password' and right before that has the error 'ISAKMP_N_AUTHENTICATION_FAILED'

There's a dh_shared_secret, skeyid, and expected hash in the debug log... would any of these help me?


Best regards,
John

---

### Post by jwhendy on 2009-10-04
Holy crap! It worked! I don't really know what I just did, but fiddling with the .conf file a bit more worked. All of the sudden it said vpnc was started in the background and out of glee I attempted to visit a site about guns and was blocked! Maybe not the best way to test, but it worked!

Happy camper here!


Best regards,
John

---

### Post by pwyll72 on 2009-11-03
Fantastic! I had earlier only found the previous thresd here: [http://www.ubuntuforums.org/showthread.php?t=441042](http://www.ubuntuforums.org/showthread.php?t=441042) and that one never worked for me, but this one did! I only had to make the following changes to the recipe:

step 0: also, needed to do "sudo apt-get install subversion"
step 7: neede to change DH Group to dh1
step 11. when starting, needed to use the commandline option --enable-1des

Thanks again, really appreciate the info!

---

### Post by ghat on 2009-11-05
> **pwyll72 said:**
> 
step 0: also, needed to do "sudo apt-get install subversion"

Fixed above... I have CVS, mercurial, subversion, RCS etc all installed by default on my system...

> **pwyll72 said:**
> 
step 7: neede to change DH Group to dh1
step 11. when starting, needed to use the commandline option --enable-1des


These are specific to your companies VPN config, not specific to the instructions posted here.. 
I have said earlier that you need to tweak these to match your companies VPN by looking at 
the setup on the windows client. 

Ghat...

---

### Post by freerkkalsbeek on 2009-11-17
I tried to get it working, and it looks promising.
I get connected, but I'm not able to connect to any IP behind the VPN.

Looks like routing setup is not working as it should.

Does anyone have ideas about debugging this? I really like to get it working so I can get rid of my VirtualBox for VPN access.

Freerk

---

### Post by ghat on 2010-01-07
> **freerkkalsbeek said:**
> I tried to get it working, and it looks promising.
I get connected, but I'm not able to connect to any IP behind the VPN.

Looks like routing setup is not working as it should.

Does anyone have ideas about debugging this? I really like to get it working so I can get rid of my VirtualBox for VPN access.

Freerk

Did you get past your problems ? Let me know if you need help...

G

---

### Post by Scoubidou on 2010-04-14
Hi guys!

Ok, so here I am trying again to connect to my work nortel vpn. And I've got futher than ever before follwing this thread!

Like the last poster, I connect to the VPN but then I can't reach any local IPs.

here some more info

I used the last sub version (449) and needed one more lib to compile (libgnutls-dev) 

I had (ISAKMP_N_INVALID_EXCHANGE_TYPE)(7) error. It was just a typo in my group ID. 

So here's some of my output

```

# netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
x.y.120.192 0.0.0.0         255.255.255.255 UH        0 0          0 tun0
x.y.87.174  0.0.0.0         255.255.255.255 UH        0 0          0 tun0
a.b.235.122.50  0.0.0.0         255.255.255.255 UH        0 0          0 tun0
r.t.47.249.40   192.168.1.1     255.255.255.255 UGH    1500 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
x.y.16.0    0.0.0.0         255.255.240.0   U         0 0          0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

```

```
# cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	box1

x.y.87.174   host1.sub1.domain.com
r.t.122.50   host2.sub2.domain.com
x.y.120.192  host3.sub1.domain.com


```

```
# ifconfig

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:x.y.20.123  P-t-P:142.180.20.123  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:6508 (6.5 KB)


```

As you can see I can send packet in the tunnel but they don't come back.. :confused:

I'm on 9.10 x64 if that anything to do with it.
I was able to connect to a cisco vpn using the vpnc version in the repo

I can browse the internet when connected (I'm connected to my vpn right now)

Any thing would help.

Thanks.

---

### Post by ghat on 2011-01-12
hi

I found this one helpful in locating the group password/IPSecret from the windows client...

[http://www.snadboy.com/](http://www.snadboy.com/)


To the earlier poster, I guess there is some issue with the routing tables in your PC.
Note that you home/personal subnet should not be used in the company....

eg, most companies large/small will use private IP's in the 10.0.0.0 network, if so you should setup your local subnet in 172.16.X.X subnet or 192.168.X.X so routing is simple... 

if you have time and a fast pc/linux on the office network you can try running

nmap -sP -oG ~/myPingScan.txt 10.1-254.1-254.1-254 172.16.1-254.1-254 192.168.1-254.1-254 

overnight and use the output to figure out what IP address' are in use in your office..
and then decide the subnet you should setup in your home

G

---

### Post by victorbrca on 2011-06-10
I'm also getting the same error, wondering if anyone could give me a hand:

```
/usr/sbin/vpnc: response was invalid [1]:  (ISAKMP_N_INVALID_EXCHANGE_TYPE)(7)
```

Here's my original configuration in Windows:

[IMG]http://imagebin.org/index.php?mode=image&id=157639[/IMG]
[Status]("http://imagebin.org/157639")

[IMG]http://imagebin.org/index.php?mode=image&id=157640[/IMG]
[Authentication Options]("http://imagebin.org/157640")

[IMG]http://imagebin.org/index.php?mode=image&id=157641[/IMG]
[Two factor authentication options]("http://imagebin.org/157641")

[IMG]http://imagebin.org/index.php?mode=image&id=157642[/IMG]
[Version]("http://imagebin.org/157642")

And here's my conf file:

```
victor@linux-x5ee:/etc/vpnc> sudo grep -v '^#' contivity-ip-split.conf
root's password:
IPSec gateway access.[DOMAIN].ca
IPSec ID [GROUP]
IPSec secret [GROUP PASS]

Vendor nortel
Nortel Client ID V06_01
IKE DH Group dh5
IKE Authmode PIN-token
NAT Traversal Mode natt

Xauth username [USER]
Xauth PIN [PIN]

Script /etc/vpnc/contivity-ip-split-script

Debug 99  # Again for debug purposes check vpnc --long-help for verbosity levels
```

Any ideas? I noticed that vpnc only had df5, and it looks like I'm using df8.

Thanks,
Vic.

---

### Post by vince0609 on 2011-06-10
[FONT=Calibri]I picked up the MF60 last week. I previously had the MF30, but struggled with signal strength due to my location (5kms outside Torquay, Vic). Previous to that I had the Virgin E5832 and could get no signal in Torquay.[/FONT]

---

### Post by Scoubidou on 2011-06-10
Victor, 

Try : IKE DH Group dh2

---

### Post by victorbrca on 2011-06-10
> **Scoubidou said:**
> Victor, 

Try : IKE DH Group dh2

I love you!!!! Thank so much for the tip... and Thank you 'ghat' for the tutorial... 

I should note that by adding the subnet of my work I was able to access most of the nodes without needing to make any modifications to my host files.

And if anyone has multiple group profiles, here's a quick and dirty script for changing it on the fly:

```
#!/bin/bash

#----------------------------------------------------------------------------
# Variables and functions
#----------------------------------------------------------------------------

INSTALLDIR="/etc/vpnc"
DEFAULT_CONF="default.conf"
DEFAULT_CONF_FILE=${INSTALLDIR}/${DEFAULT_CONF}

checkERR () {
if [ "$STATUS" -ne 0 ]
 then
  echo "Previous proccess failed"
  exit 1
fi
}


#----------------------------------------------------------------------------
# Starts selection and menu
#----------------------------------------------------------------------------

echo "#################################"
echo "# MENU TO START VPN CONNECTIONS #"
echo -e "#################################\n"
echo "Please type in a selection"
echo "1- Connect to Group1"
echo "2- Disconnect from VPN"
read ANSWER

# Checks if symlink exists for default file
if [ -h "$DEFAULT_CONF_FILE" ]
 then
  sudo unlink "$DEFAULT_CONF_FILE" ; STATUS="$?"
  checkERR
fi

case $ANSWER in
  1) CURRENT_FILE="/etc/vpnc/Group1.conf"
     ;;
  2) 
     echo "Disconnecting VPN"
     sudo /usr/sbin/vpnc-disconnect ; STATUS="$?"
     checkERR
     echo "VPV diconnected"
     sleep 1
     exit 0
     ;;
  *) 
     echo "Option not valid"
     echo "Exiting ..."
     sleep 1
     exit 1
     ;;
esac

# Handles default files
if [ ! -f "$CURRENT_FILE" ]
 then
   echo "Configuration file \"$CURRENT_FILE\" does not exist"
    exit 1
fi

echo "Attempting to create a link for configuration file $CURRENT_FILE"
sudo ln -s "$CURRENT_FILE" /etc/vpnc/default.conf ; STATUS="$?"
checkERR
echo "Configuration file in place. Attempting to start vpnc"
sudo /usr/sbin/vpnc ; STATUS="$?"
checkERR
echo "VPN started"
sleep 1

exit 0
```

---

### Post by dalmeida on 2011-08-07
> **Scoubidou said:**
> Hi guys!

Ok, so here I am trying again to connect to my work nortel vpn. And I've got futher than ever before follwing this thread!

Like the last poster, I connect to the VPN but then I can't reach any local IPs.



```
# ifconfig

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:x.y.20.123  P-t-P:142.180.20.123  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1412  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:6508 (6.5 KB)


```

As you can see I can send packet in the tunnel but they don't come back.. :confused:

I'm on 9.10 x64 if that anything to do with it.
I was able to connect to a cisco vpn using the vpnc version in the repo

I can browse the internet when connected (I'm connected to my vpn right now)

Any thing would help.

Thanks.

I was having this same issue and I changed my config file as shown below:

from:
NAT Traversal Mode natt
to:
NAT Traversal Mode nortel-udp

Hope this helps,if it doesn't, try the other modes: <natt/none/force-natt/cisco-udp/nortel-udp>

---

### Post by Scoubidou on 2011-08-07
Thank you VERY much!

> NAT Traversal Mode nortel-udp


That's the line that was missing

After more than 3 years I can FINALLY connect to my work vpn with my Ubuntu! I started trying with Ubuntu 8.04 and now I'm running 11.04! 

So here's my config file if it can help someone

```

cat /etc/vpnc/my-vpn.conf 
IPSec gateway vpn.mycie.com
IPSec ID mycie
IPSec secret mycie-secret
#Enable Single DES
IKE DH Group dh2
NAT Traversal Mode nortel-udp
Xauth username myusername
Vendor nortel
Nortel Client ID V05_01
#No Detach
Script /etc/vpnc/vpnc-script

```

:guitar:

---

### Post by fire-fly on 2012-09-20
Hi 
Please help, using the attached image, how should configure /etc/vpnc/default.conf ?

/etc/vpnc/default.conf
IPSec gateway [same as destination]
IPSec ID [???]
IPSec secret [same as Pin ?]

#IKE Authmode hybrid
Vendor nortel
Nortel Client ID V06_01
IKE DH Group dh2
IKE Authmode PIN-token
NAT Traversal Mode nortel-udp
Xauth username [same as User]
#Xauth password 

Thanks in advance.

---

### Post by ghat on 2013-03-15
cool thread is still active on/off...

off topic...
does anyone of know of any non-dell/sonicwall client for a dell-sonicwall vpn ?

---

### Post by wildmanne39 on 2013-03-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---


---
title: "Moblock Doesn't Start Post-Update"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by BJ_Covert_Action on 2009-03-24
Howdy All,

I just recently updated moblock with the update that involved transferring the content of the 

/etc/moblock/iptables-custom-insert.sh
/etc/moblock/iptables-custom-remove.sh

to 

/lib/iptables/libipt_blockout_fw.so
/lib/iptables/libipt_blockout_out.so 

After doing the upgrade, I wasn't exactly sure I needed to do anything involving the above four files, so I just let the upgrade finish automatically and went on with my life. However, upon trying to run moblock with the:

sudo moblock-control start command

I was given the message: 

Moblock is starting...

and nothing happened.

When I ran sudo moblock-control test from a different terminal I was told moblock was not running. So, I copied the .sh files mentioned above (they resided in the /etc/moblock directory) to /lib/iptables/ under the two .so filenames mentioned above (because I thought that was the step I skipped during the configuration after my latest update). Anyways, that also led to a failed start as now when I tell moblock to start, I am awarded with being taken immediately to the next command line and still no moblock running. 

The first 50 or so lines of my /var/log/moblock-control.log file looks like this:

```

2010-03-23 20:07:33 PDT Begin: blockcontrol stop
Deleting iptables ...iptables v1.3.8: Couldn't load target `blockcontrol_in':/lib/iptables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_out':/lib/iptables/libipt_blockcontrol_out.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_fw':/lib/iptables/libipt_blockcontrol_fw.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name

[74G[[31mfail[39;49m]
 [33m*[39;49m There occured some errors during the deletion of the iptables rules.
 [33m*[39;49m The most common reason for this is that they did not exist, because MoBlock
 [33m*[39;49m was not running. In this case you don't have to worry.
 [33m*[39;49m But if MoBlock was running there is some problem. Most probably you have
 [33m*[39;49m installed another firewall application that did delete the iptables rules.
 [33m*[39;49m A "blockcontrol restart" will then fix the situation.
Executing /etc/blockcontrol/iptables-custom-remove.sh ...
[74G[ OK ]
Stopping MoBlock ...
[74G[ OK ]
2009-03-23 20:07:34 PDT End: blockcontrol stop
2009-03-23 09:13:01 PM PDT Begin: moblock-control start
Building blocklist... Removing the following lines from TBG_Primary_Threats:
BOGDAN_LUCIAN_CRISTIAN-YAHOOCOM:208.98.12.0-208.98.12.63

CHRISTOSLOIZOU-HOTMAILCOM:208.98.50.192-208.98.50.255

Cuyahooga County Bar Assoc:66.73.60.72-66.73.60.79

GOOGLE-NL:213.19.160.192-213.19.160.207

```

Any ideas?

Thanks in advance.

---

### Post by BJ_Covert_Action on 2009-03-24
Any ideas, anyone?

---

### Post by jre on 2009-03-24
> **BJ_Covert_Action said:**
> I just recently updated moblock with the update that involved transferring the content of the 

/etc/moblock/iptables-custom-insert.sh
/etc/moblock/iptables-custom-remove.sh

to 

/lib/iptables/libipt_blockout_fw.so
/lib/iptables/libipt_blockout_out.so


No, you don't have to do that.

If you don't use (=have edited them yourself) those 2 files, you don't have to do anything.

If you have, you have to change the chain names in them, and copy them to /etc/blockcontrol.

```
The first 50 or so lines of my /var/log/moblock-control.log file looks like this:

```
This part is useless. Post a part with the complete "start" section.

What distribution are you on? Did you do anything else for the update? What's in /var/log/moblock.log?

---

### Post by BJ_Covert_Action on 2009-03-26
Actually my /var/log/moblock.log file is empty.

I am running Ubuntu 8.04.

I am not exactly sure what you meant by a "start" section, but browsing through it revealed the following section in my /va/log/moblock-control.log file

```

Inserting iptables ...iptables v1.3.8: host/network `192.168.1.100-192.168.1.255' not found
Try `iptables -h' or 'iptables --help' for more information.

[74G[[31mfail[39;49m]
2009-03-23 09:32:07 PM PDT Begin: moblock-control start
Inserting iptables ...iptables v1.3.8: host/network `192.168.1.100-192.168.1.255' not found
Try `iptables -h' or 'iptables --help' for more information.

[74G[[31mfail[39;49m]
2009-03-23 09:32:42 PM PDT Begin: moblock-control start
Inserting iptables ...iptables: Chain already exists

[74G[[31mfail[39;49m]
2009-03-23 09:37:19 PM PDT Begin: moblock-control start
Inserting iptables ...iptables: Chain already exists

[74G[[31mfail[39;49m]
2009-03-23 10:34:18 PM PDT Begin: blockcontrol start
Inserting iptables ...iptables: Chain already exists

[74G[[31mfail[39;49m]


2009-03-23 10:34:18 PM PDT Begin: blockcontrol start
Inserting iptables ...iptables: Chain already exists

[74G[[31mfail[39;49m]
2009-03-24 07:07:11 PDT Begin: blockcontrol stop
Deleting iptables ...iptables v1.3.8: Couldn't load target `blockcontrol_in':/lib/iptables/libipt_blockcontrol_in.so: cannot open shared object file: No such file or directory

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_out':/lib/iptables/libipt_blockcontrol_out.so: invalid ELF header

Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.8: Couldn't load target `blockcontrol_fw':/lib/iptables/libipt_blockcontrol_fw.so: invalid ELF header

Try `iptables -h' or 'iptables --help' for more information.
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name

[74G[[31mfail[39;49m]
 [33m*[39;49m There occured some errors during the deletion of the iptables rules.
 [33m*[39;49m The most common reason for this is that they did not exist, because MoBlock
 [33m*[39;49m was not running. In this case you don't have to worry.
 [33m*[39;49m But if MoBlock was running there is some problem. Most probably you have
 [33m*[39;49m installed another firewall application that did delete the iptables rules.
 [33m*[39;49m A "blockcontrol restart" will then fix the situation.
Executing /etc/blockcontrol/iptables-custom-remove.sh ...
[74G[ OK ]
Stopping MoBlock ...
[74G[ OK ]
2009-03-24 07:07:11 PDT End: blockcontrol stop
2009-03-25 22:35:02 PDT Begin: blockcontrol update
Updating blocklists ...
Updating TBG_Primary_Threats... done.
Extracting TBG_Primary_Threats, detected gz... done.
Updating TBG_General_Corporate_Ranges... done.
Extracting TBG_General_Corporate_Ranges, detected gz... done.
Updating TBG_Business_ISPs... done.
Extracting TBG_Business_ISPs, detected gz... done.
Updating TBG_Search_Engines... done.
Extracting TBG_Search_Engines, detected gz... done.
Updating TBG_Hijacked... done.
Extracting TBG_Hijacked, detected gz... done.
Updating TBG_Bogon... done.
Extracting TBG_Bogon, detected gz... done.
Updating Bluetack_level1... done.
Extracting Bluetack_level1, detected gz... done.
Updating Bluetack_level2... done.
Extracting Bluetack_level2, detected gz... done.
Updating Bluetack_level3... done.
Extracting Bluetack_level3, detected gz... done.
Updating Bluetack_ads... done.
Extracting Bluetack_ads, detected gz... done.
Updating Bluetack_bogon... done.
Extracting Bluetack_bogon, detected gz... done.
Updating Bluetack_spyware... done.
Extracting Bluetack_spyware, detected gz... done.
Updating Bluetack_Microsoft... done.
Extracting Bluetack_Microsoft, detected gz... done.
Updating Bluetack_proxy... done.
Extracting Bluetack_proxy, detected gz... done.
Updating Bluetack_hijacked... done.
Extracting Bluetack_hijacked, detected gz... done.
Updating Bluetack_badpeers... done.
Extracting Bluetack_badpeers, detected gz... done.
Updating Bluetack_rangetest... done.
Extracting Bluetack_rangetest, detected gz... done.
Updating Bluetack_dshield... done.
Extracting Bluetack_dshield, detected gz... done.
Blocklists updated.
 * MoBlock is not running, doing nothing.
2009-03-25 22:45:38 PDT End: blockcontrol update


```

I'm not sure that's any more useful actually. I could attach the file, but I can't find the attachment button for some reason.

Does this help at all? I am still relatively new at figuring out what is what in a log file.

---

### Post by BJ_Covert_Action on 2009-03-26
Incidentally, I just tried running it again, this time with the blockcontrol start command and browsed through my /var/log/blockcontrol.log file for today's date and found this after a lengthy list of IP addresses:

```

Inserting iptables ...iptables v1.3.8: host/network `192.168.1.100-192.168.1.255' not found
Try `iptables -h' or 'iptables --help' for more information.

^M^[74G[^[31mfail^[39;49m]


```

---

### Post by jre on 2009-03-26
I think you misconfigured blockcontrol. It seems as if you want to whitelist your LAN: 192.168.1.100-192.168.1.255.
First off, you probably don't need to do this manually because the LAN gets whitelisted automatically (in most cases ;-))

If you need to do thismanually, then you can add this to /etc/blockcontrol/allow.p2p:
```
My LAN:192.168.1.100-192.168.1.255
```

I guess you added this erroneously to the variables WHITE_IP_IN and/or WHITE_IP_OUT in /etc/blockcontrol/blockcontrol.conf. But that would be the wrong syntax for these variables.

Only use the custom iptables rules (/etc/blockcontrol/iptables-custom-insert.sh and ...remove.sh), if you want to do special things. If you just want to whitelist single IPs, IP ranges or ports it should be easier to use blockcontrol's options instead of your own iptables rules.

Undo all changes that you made in /lib/iptables/... What was your intention with that? For me this doesn't make sense at all ;-)

If you need further assistance, please post the output of
```
blockcontrol show_config"
```

BTW: There is currently no mobloquer package for Ubuntu hardy (because the Qt version in hardy is too old). As a temporariy solution I have set up a static repository with the old packages. Change your sources.list entry to ```
deb http://moblock-deb.sourceforge.net/20090109 hardy main
``` This is only important if you want to use mobloquer AND want to stay on hardy, otherwise I strongly recommend to stay with the new packages.


Finally: posting in code tags is fine. I prefer that to attachments.

Greets
jre

---

### Post by BJ_Covert_Action on 2009-03-26
So I did this:

> **jre said:**
> 
If you need to do thismanually, then you can add this to /etc/blockcontrol/allow.p2p:
```
My LAN:192.168.1.100-192.168.1.255
```


And this:

> **jre said:**
> 
Undo all changes that you made in /lib/iptables/... What was your intention with that? For me this doesn't make sense at all ;-)


...which involved deleting the two files I copied as mentioned near the beginning of the post. As for why I did that, I can never be certain of my own intentions...I seem to recall, during the configuration after the installation of the new packages, something about switching the content of the allow lists to the /lib/iptables files, so I just copied whatever I had (which it didn't appear was much) and prayed to the Ubuntu gods that such a mindless exercise would work (lesson learned).

Then I ran:

```

sudo blockcontrol start

```

and:

```

sudo blockcontrol test

```

only to be rewarded with: "moblock is not running"

blockcontrol show_config yeilds:

```

blockcontrol current settings:
ACCEPT="1"
ACCEPT_MARK="20"
ALLOW_FW=""
ALLOW_IN="/etc/blockcontrol/allow.p2p"
ALLOW_OUT="/etc/blockcontrol/allow.p2p"
BLOCKLIST_FORMAT="p"
BLOCKLISTS_DIR="/var/spool/blockcontrol"
BLOCKLISTS_LIST="/etc/blockcontrol/blocklists.list"
CONTROL_CONF="/etc/blockcontrol/blockcontrol.conf"
CONTROL_LIB="/usr/lib/blockcontrol/blockcontrol.lib"
CONTROL_LOG="/var/log/blockcontrol.log"
CONTROL_NAME="blockcontrol"
CONTROL_SCRIPT="/usr/bin/blockcontrol"
CRON="1"
CRON_MAILTO="root"
DAEMON="/usr/bin/moblock"
DAEMON_LOG="/var/log/moblock.log"
DESC="MoBlock"
E_BADARGS="2"
E_BLOCKLIST="9"
E_CONFIG="6"
E_IPTABLES="8"
E_NETWORK_DOWN="171"
E_NOTROOT="4"
E_XBIN="5"
E_XCD="66"
E_XEXTERNAL="170"
E_XFILE="7"
INIT="0"
IP_REMOVE="google;yahoo;altavista;hotmail"
IPTABLES_ACTIVATION="1"
IPTABLES_CUSTOM_DELETE="/etc/blockcontrol/iptables-custom-remove.sh"
IPTABLES_CUSTOM_INSERT="/etc/blockcontrol/iptables-custom-insert.sh"
IPTABLES_SETTINGS="1"
IPTABLES_TARGET="NFQUEUE"
IPTABLES_TARGET_WHITELISTING="RETURN"
LOG_IPTABLES=""
LOG_SYSLOG="0"
LOG_TIMESTAMP="1"
LSB="/lib/lsb/init-functions"
LSB_MODE="0"
MASTER_BLOCKLIST_DIR="/var/lib/blockcontrol"
MD5SUM_FILE="/var/spool/blockcontrol/MD5SUM"
NAME="moblock"
NFQUEUE_NUMBER="92"
PATH="/usr/bin:/bin:/sbin:/usr/sbin:/usr/local/bin:/usr/local/sbin"
PIDFILE="/var/run/moblock.pid"
REJECT="1"
REJECT_FW="DROP"
REJECT_IN="DROP"
REJECT_MARK="10"
REJECT_OUT="REJECT"
STATFILE="/var/log/MoBlock.stats"
STDIFS=" "
TESTHOST="iblocklist.com"
VERBOSITY="1"
WGET_OPTS="wget -q -t 5 -T 120 -w 5"
WHITE_IP_FORWARD=""
WHITE_IP_IN="192.168.1.0/24 http https"
WHITE_IP_OUT="192.168.1.0/24 http https"
WHITE_LOCAL="1"
WHITE_TCP_FORWARD=""
WHITE_TCP_IN=""
WHITE_TCP_OUT="http https"
WHITE_UDP_FORWARD=""
WHITE_UDP_IN=""
WHITE_UDP_OUT=""

The following blocklists are configured to be used:
http://list.iblocklist.com/?list=ijfqtofzixtwayqovmxn
http://list.iblocklist.com/?list=ecqbsykllnadihkdirsh
http://list.iblocklist.com/?list=jcjfaxgyyshvdbceroxf
http://list.iblocklist.com/?list=pfefqteoxlfzopecdtyw
http://list.iblocklist.com/?list=tbnuqfclfkemqivekikv
http://list.iblocklist.com/?list=ewqglwibdgjttwttrinl
http://list.iblocklist.com/?list=bt_level1
http://list.iblocklist.com/?list=bt_level2
http://list.iblocklist.com/?list=bt_level3
http://list.iblocklist.com/?list=bt_ads
http://list.iblocklist.com/?list=bt_bogon
http://list.iblocklist.com/?list=bt_spyware
http://list.iblocklist.com/?list=bt_microsoft
http://list.iblocklist.com/?list=bt_proxy
http://list.iblocklist.com/?list=bt_hijacked
http://list.iblocklist.com/?list=bt_templist
http://list.iblocklist.com/?list=bt_rangetest
http://list.iblocklist.com/?list=bt_dshield

```

...while my /var/log/blockcontrol.log file has this most recent entry:

```

2009-03-26 17:42:02 PDT Begin: blockcontrol stop
Deleting iptables ...iptables: No chain/target/match by that name
iptables: No chain/target/match by that name
iptables: No chain/target/match by that name

[74G[[31mfail[39;49m]
 [33m*[39;49m There occured some errors during the deletion of the iptables rules.
 [33m*[39;49m The most common reason for this is that they did not exist, because MoBlock
 [33m*[39;49m was not running. In this case you don't have to worry.
 [33m*[39;49m But if MoBlock was running there is some problem. Most probably you have
 [33m*[39;49m installed another firewall application that did delete the iptables rules.
 [33m*[39;49m A "blockcontrol restart" will then fix the situation.
Executing /etc/blockcontrol/iptables-custom-remove.sh ...
[74G[ OK ]
Stopping MoBlock ...
[74G[ OK ]
2009-03-26 17:42:02 PDT End: blockcontrol stop
2009-03-26 06:01:52 PM PDT Begin: blockcontrol start
Building blocklist... Removing the following lines from TBG_Primary_Threats:
BOGDAN_LUCIAN_CRISTIAN-YAHOOCOM:208.98.12.0-208.98.12.63

CHRISTOSLOIZOU-HOTMAILCOM:208.98.50.192-208.98.50.255

Cuyahooga County Bar Assoc:66.73.60.72-66.73.60.79

GOOGLE-NL:213.19.160.192-213.19.160.207

GOOGLE/PLANET LABS:208.185.40.192-208.185.40.223

GOOGLE/PLANET LABS:208.185.4.128-208.185.4.159

GOOGLE/PLANET LABS:208.185.42.96-208.185.42.127

MS Hotmail:64.4.0.0-64.4.63.255


<MORE IP ADDRESSES>

...

Removing the following lines from Bluetack_rangetest:

[74G[ OK ]
Removing the following lines from Bluetack_dshield:

[74G[ OK ]

[74G[ OK ]
Inserting iptables ...iptables v1.3.8: host/network `http' not found
Try `iptables -h' or 'iptables --help' for more information.

[74G[[31mfail[39;49m]

```

...which makes me think there is more syntax errors with my WHITE_IP_IN variables and WHITE_IP_OUT variables. So I am going to try editing those as well and see what happens. Stay tuned....

---

### Post by BJ_Covert_Action on 2009-03-26
Alright, so I went back into /etc/blockcontrol/blockcontrol.conf and removed 

```

WHITE_IP_IN="http https"
WHITE_IP_OUT="http https"

```

however I did leave an IP range I had specified in there from the first time I configured Moblock (a few months ago) so now the content of that file looks like:

```


WHITE_TCP_OUT="http https"
INIT="0"
IP_REMOVE="google;yahoo;altavista;hotmail"
WHITE_IP_IN="192.168.1.0/24"
WHITE_IP_OUT="192.168.1.0/24"


```

....which I think is legitimate?

after doing: 

```

sudo blockcontrol restart command
sudo blockcontrol test

```

I get:

```

Testing MoBlock:

CAUTION: This is just a simple test to check if MoBlock blocks outgoing
connections. For this, an IP from the blocklist will be pinged. Then the test
checks if this IP appears in the logfile /var/log/moblock.log.

MoBlock marks packets to be blocked. This means you have to make sure that the
marked packets are also blocked later (with appropriate iptables rules). If you
are using the default configuration and MoBlock is started after other firewalls
this will be the case.

This test does not check if you have sane iptables rules or if your complete
blocklist is in the correct format. Therefore success doesn't imply that
everything is working as you expect it.

Also have a look at "blockcontrol status" and test manually with traceroute.

Trying to ping 4.17.112.255 from /var/lib/blockcontrol/guarding.p2p ...
 * MoBlock did not mark the IP to be blocked.
 * Was MoBlock already loaded completely? Wait some minutes and try again.
 * 
 * 4.17.112.255 did not answer.
 * 
 * Maybe 4.17.112.255 is down/doesn't answer to pings
 * (this would still mean that MoBlock is not working)
 * or your firewall filtered the ping before MoBlock could check it
 * (then MoBlock may be working as desired, check your iptables rules).


```

Unfortunately I am not exactly how to check my iptables rules or what I would be looking for...yet.

Anyways, doing a 

```

sudo blockcontrol status

```

yields:

```

Current IPv4 iptables rules (this may take a while):

Chain INPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
    1    78 ACCEPT     udp  --  *      *       192.168.1.1          0.0.0.0/0           
   46  1932 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 DROP       all  --  wlan0  *       0.0.0.0/0            255.255.255.255     
    1   235 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
   59 76520 INBOUND    all  --  wlan0  *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 ACCEPT     tcp  --  *      *       192.168.1.102        192.168.1.1         tcp dpt:53 
    2   124 ACCEPT     udp  --  *      *       192.168.1.102        192.168.1.1         udp dpt:53 
   46  1932 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
    0     0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
   47  3707 OUTBOUND   all  --  *      wlan0   0.0.0.0/0            0.0.0.0/0           
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
   59 76520 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpts:6881:6889 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpts:6881:6889 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:25544 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:25544 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8080 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8080 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:8118 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:8118 
    0     0 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:9050 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:9050 
    0     0 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
    0     0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
    0     0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
    0     0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
    0     0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    1    84 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
   45  3579 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    1    44 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Current IPv6 iptables rules (this may take a while):

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Please check if the above printed iptables rules are correct!

 * moblock is running

```

...which apparently has my iptables rules in it and means moblock is running. So now I get to start Azureus and see if it fails epic like now...

Thanks so far this has been a great help and a wonderful learning experience. Eventually, I am hoping a lot of this networking jargon and administration and moblock control commands will sink in to be habit...I have to start using my home computer more often...damn Windows machines at work corrupting my brain...

If anyone has anything to add or any light they would like to shed or any further comments or responses or general rubbish, please don't be shy...this is the way I learn.

Cheers and thanks again Jre..

- Brady C. Jackson

---

### Post by jre on 2009-03-27
The config seems to be ok *now*.
But in the iptables rules I miss the blockcontrol rules. See "How to make sure that MoBlock is integrated correctly with any other firewall" in post #1 in [this thread]("http://ubuntuforums.org/showthread.php?t=803183") to understand.

Did you restart your firewall application (I guess you are using firestarter or ufw!?) after restarting blockcontrol? This might have thrown away blockcontrol's iptables rules.
To get them in again, you have to do a ```
sudo blockcontrol restart
``` again.

---

### Post by BJ_Covert_Action on 2009-03-30
I did do a blockcontrol restart, but I never did a firestarter restart (which is the one I use).

I'll take a look at the thread you posted and see what I can discover.

I think things are running decently. When I look at the iptables rules listed in that thread and those listed by my status command, I see all of the same calls to blockcontrol (blockcontrol_fw, blockcontrol_out etc...)

Is that what I am supposed to be looking for?

Cheers and
Thanks.

---

### Post by jre on 2009-03-31
Yes. But in your [other thread]("http://ubuntuforums.org/showpost.php?p=6987164&postcount=1") they were missing.

---

### Post by qkslvrwolf on 2009-06-29
I am having a similar problem, but I can't get blockcontrol to output any log messages either.  I noticed after installing that the logs weren't automatically created, so I created them with touch, but I don't know the owner and permissions that they need.  

Here is my configuration file from a block control show_config:

```

blockcontrol current settings:
ACCEPT="1"
ACCEPT_MARK="20"
ALLOW_FW=""
ALLOW_IN="/etc/blockcontrol/allow.p2p"
ALLOW_OUT="/etc/blockcontrol/allow.p2p"
BLOCKLIST_FORMAT="p"
BLOCKLISTS_DIR="/var/spool/blockcontrol"
BLOCKLISTS_LIST="/etc/blockcontrol/blocklists.list"
CONTROL_CONF="/etc/blockcontrol/blockcontrol.conf"
CONTROL_LIB="/usr/lib/blockcontrol/blockcontrol.lib"
CONTROL_LOG="/var/log/blockcontrol.log"
CONTROL_NAME="blockcontrol"
CONTROL_SCRIPT="/usr/bin/blockcontrol"
CRON="1"
CRON_MAILTO="root"
CUSTOM_DAEMON_OPTS=""
DAEMON="/usr/bin/moblock"
DAEMON_LOG="/var/log/moblock.log"
DESC="IP block daemon"
E_BADARGS="2"
E_BLOCKLIST="9"
E_CONFIG="6"
E_IPTABLES="8"
E_NETWORK_DOWN="171"
E_NOTROOT="4"
E_XBIN="5"
E_XCD="66"
E_XEXTERNAL="170"
E_XFILE="7"
INIT="0"
IP_REMOVE=""
IPTABLES_ACTIVATION="1"
IPTABLES_CUSTOM_DIR="/etc/blockcontrol"
IPTABLES_SETTINGS="1"
IPTABLES_TARGET="NFQUEUE"
IPTABLES_TARGET_WHITELISTING="RETURN"
LOG_IPTABLES=""
LOG_SYSLOG="0"
LOG_TIMESTAMP="1"
LSB="/lib/lsb/init-functions"
LSB_MODE="0"
MASTER_BLOCKLIST_DIR="/var/lib/blockcontrol"
MD5SUM_FILE="/var/spool/blockcontrol/MD5SUM"
NAME="moblock"
NFQUEUE_NUMBER="92"
PATH="/usr/bin:/bin:/sbin:/usr/sbin:/usr/local/bin:/usr/local/sbin"
PIDFILE="/var/run/moblock.pid"
REJECT="1"
REJECT_FW="DROP"
REJECT_IN="DROP"
REJECT_MARK="10"
REJECT_OUT="REJECT"
STATFILE="/var/log/MoBlock.stats"
STDIFS=" "
TESTHOST="iblocklist.com"
VERBOSITY="1"
WATCHDOG="1"
WATCHDOG_PATH="/usr/bin/blockcontrol.watchdog"
WATCHDOG_SLEEP="300"
WGET_OPTS="wget -q -t 5 -T 120 -w 5"
WHITE_IP_FORWARD=""
WHITE_IP_IN="192.168.0.0/255.255.255.0"
WHITE_IP_OUT="192.168.0.0/255.255.255.0"
WHITE_LOCAL="1"
WHITE_TCP_FORWARD=""
WHITE_TCP_IN=""
WHITE_TCP_OUT="http https"
WHITE_UDP_FORWARD=""
WHITE_UDP_IN=""
WHITE_UDP_OUT=""

The following blocklists are configured to be used:
http://list.iblocklist.com/?list=ijfqtofzixtwayqovmxn
http://list.iblocklist.com/?list=ecqbsykllnadihkdirsh
http://list.iblocklist.com/?list=jcjfaxgyyshvdbceroxf
http://list.iblocklist.com/?list=pfefqteoxlfzopecdtyw
http://list.iblocklist.com/?list=tbnuqfclfkemqivekikv
http://list.iblocklist.com/?list=ewqglwibdgjttwttrinl
http://list.iblocklist.com/?list=bt_proxy
http://list.iblocklist.com/?list=bt_templist
http://list.iblocklist.com/?list=bt_dshield

```

Also, my output from blockcontrol test:  

```
Testing moblock:
 * moblock is not running

```

First time I ran it it updated all my blacklists, but I killed that window.

I'm not entirely sure where to go without any log output...any help would be much appreciated.

---


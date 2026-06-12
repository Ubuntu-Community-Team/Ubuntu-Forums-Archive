---
title: "cant open  5060 port"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by mehdymahmood on 2009-11-06
i am trying to open port 5060 . 

root@mehdy-desktop:/home/mehdy# iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5060  -j ACCEPT
root@mehdy-desktop:/home/mehdy# iptables-save 

root@mehdy-desktop:/home/mehdy# nmap 192.168.1.102 -p5000-6000

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-07 05:11 BDST
Interesting ports on 192.168.1.102:
Not shown: 1000 closed ports
PORT     STATE SERVICE
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 13.53 seconds

i dont know the reason why the iptables isnt save . please help me .

---

### Post by DGortze380 on 2009-11-06
> **mehdymahmood said:**
> i am trying to open port 5060 . 

root@mehdy-desktop:/home/mehdy# iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5060  -j ACCEPT
root@mehdy-desktop:/home/mehdy# iptables-save 

root@mehdy-desktop:/home/mehdy# nmap 192.168.1.102 -p5000-6000

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-07 05:11 BDST
Interesting ports on 192.168.1.102:
Not shown: 1000 closed ports
PORT     STATE SERVICE
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 13.53 seconds

i dont know the reason why the iptables isnt save . please help me .

Do you actually have a service listening on that port? Just adding a firewall rule won't necessarily make it show up on that scan.

---

### Post by mehdymahmood on 2009-11-06
thank you , yes i have checked it , i turn my sip phone which use 5060 , and scan ports . i have 
root@mehdy-desktop:/home/mehdy# nmap 192.168.1.102 -p0-65535

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-07 06:02 BDST
Interesting ports on 192.168.1.102:
Not shown: 65531 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
23/tcp   open  telnet
111/tcp  open  rpcbind
950/tcp  open  oftep-rpc
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 19.56 seconds

there was no 5060 . what must be the reason ?

---

### Post by DGortze380 on 2009-11-07
> **mehdymahmood said:**
> thank you , yes i have checked it , i turn my sip phone which use 5060 , and scan ports . i have 
root@mehdy-desktop:/home/mehdy# nmap 192.168.1.102 -p0-65535

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-11-07 06:02 BDST
Interesting ports on 192.168.1.102:
Not shown: 65531 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
23/tcp   open  telnet
111/tcp  open  rpcbind
950/tcp  open  oftep-rpc
5900/tcp open  vnc

Nmap done: 1 IP address (1 host up) scanned in 19.56 seconds

there was no 5060 . what must be the reason ?

Again, that scan will not necessarily show 5060/tcp.
Maybe try? nmap -sT 192.168.1.102 -p0-65535 

Is the device working correctly?
Are you behind firewall or router that also needs the port opened?

---

### Post by mehdymahmood on 2009-11-07
thank you . im trying to call  from my lan . there is no firewall . my pc are directly connected through lan . nmp  -sT 192.68.1.102 -pp0-5300  give the same result . and device working , becasuse it can listen other ports expect 5060. what could this be ?

---

### Post by DGortze380 on 2009-11-07
> **mehdymahmood said:**
> thank you . im trying to call  from my lan . there is no firewall . my pc are directly connected through lan . nmp  -sT 192.68.1.102 -pp0-5300  give the same result . and device working , becasuse it can listen other ports expect 5060. what could this be ?

Are you trying to call from inside your LAN to Outside? Or from one computer on the LAN to another?

Are you sure it's TCP? Those types of connections tend to be UDP.

---

### Post by mehdymahmood on 2009-11-08
thank you [DGortze380]("http://ubuntu-ky.ubuntuforums.org/member.php?u=390930") , 
i got the solution  . i used ethereal for the port scan . and it showed 5060 port is working . their is may be other reason i think .   

i am using following package 
os ubuntu 
asterisk-1.6.0.15
dahdi-linux-complete-2.2.0.2+2.20
libpri-1.4.10.1

sip.conf 
[general]
context=default
allowoverlap=no
bindport=5060
bindaddr=0.0.0.0
tcpenable= yes
tcpbindaddr=0.0.0.0
srvlookup= no

register => joahim1:******@192.168.1.101/davy1
register => davy1:******@192.168.1.100/jaohim1


[joahim1]
type=friend
secret=******
qualify= yes
nat=yes
host= 192.168.1.101
dtmfmode=rfc2833
canreinvite=no
username=joahim1 
context= mehdy 
allow= all

[davy1]
type=friend
secret=******
qualify=yes
nat=yes
host= 192.168.1.100
dtmfmode=rfc2833
canreinvite=no
username=davy1                              
context=mehdy 
allow =all 


extension.conf 

[general]
static=yes
writeprotect=no

[globals]
CONSOLE=Console/dsp
IAXINFO=guest                    
TRUNK=DAHDI/G2                    

DAVY=SIP/davy1
TRUNKMSD=1

[mehdy]

exten => 101,1,Answer()
exten => 101,n,Background(demo-nogo)
exten => 101,n,WaitExten()

exten => 1,1,Dial(SIP/jaohn1,10)

exten => 2,1,Dial(${DAVY},10)



ion for 'joahim1@192.168.1.101' timed out, trying again (Attempt #86)
[Nov  8 14:24:14] NOTICE[3656]: chan_sip.c:9740 sip_reg_timeout:    -- Registration for 'joahim1@192.168.1.101' timed out, trying again (Attempt #86)
[Nov  8 14:24:34] NOTICE[3656]: chan_sip.c:9740 sip_reg_timeout:    -- Registration for 'davy1@192.168.1.100' timed out, trying again (Attempt #87)
[Nov  8 14:24:34] NOTICE[3656]: chan_sip.c:9740 sip_reg_timeout:    -- Registration for 'davy1@192.168.1.100' timed out, trying again (Attempt #87)
[Nov  8 14:24:34] NOTICE[3656]: chan_sip.c:9740 sip_reg_timeout:    -- Registration for 'joahim1@192.168.1.101' timed out, trying again (Attempt #87)
[Nov  8 14:24:34] NOTICE[3656]: chan_sip.c:9740 sip_reg_timeout:    -- Registration for 'joahim1@192.168.1.101' timed out, trying again (Attempt #87)



== Using SIP RTP CoS mark 5
[Nov  8 13:56:51] WARNING[3818]: app_dial.c:1499 dial_exec_full: Unable to create channel of type 'SIP' (cause 20 - Unknown)
[Nov  8 13:56:51] WARNING[3818]: app_dial.c:1499 dial_exec_full: Unable to create channel of type 'SIP' (cause 20 - Unknown)
  == Everyone is busy/congested at this time (1:0/0/1)
    -- Auto fallthrough, channel 'SIP/davy1-091efb50' status is 'CHANUNAVAI


please help me .

---

### Post by Topazgb on 2011-01-11
I had similar problem with Twinkle but solved it


sudo nmap -sS -sV -O -p- -PI -PT 192.168.1.2
Showed me what was using the port
(nmap is in the software centre.  Your IP may be different)

SIP Express Router was using the port

Not sure if it installed when I installed a windows softphone on wine ? 

I just unistalled SIP Express Router and Twinkle connected

Unfortunately sound did not work on Twinkle so I installed SLFphone with full success

---


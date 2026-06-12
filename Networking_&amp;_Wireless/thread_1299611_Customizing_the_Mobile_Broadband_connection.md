---
title: "Customizing the Mobile Broadband connection"
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by cong06 on 2009-10-24
I'm using a safaricom modem, and it's amazing how easy it is to install and set up.
What it doesn't handle, though, is dial-on-demand, and other re-connection options (sometimes it connects, but has no connection, and a re-connect fixes it).

What I need, is a way to keep the Mobile Broadband connection up constantly. Consider that I'm setting this up for people that may or may not know what they're doing. I want this to be as fool-proof as possible.

I think it should be pretty straight forward to add some scripting in /etc/ppp/ip-up.d/ but I'm honestly not sure how to go about recalling the connection.
What command does the Network Manager use for Mobile Broadband?

Where can I look to learn more about how Ubuntu manages the specific Mobile Broadband?
(I could mess around with wvdial, but I like the interface with the Network Manager)

---

### Post by cong06 on 2010-02-19
The file is:
/etc/ppp/options

Though I'm not convinced that the 'persist' option works...

---

### Post by alexfish on 2010-02-19
hi

not sure which NM your using, however 


I have noticed that the Resolves ppp and NM Resolves are store in two  separate files

On the Ubuntu system there should be two files “serviceproviders.2.dtd”  and “serviceproviders.xml”


The “serviceproviders.xml” is the  actual database used by the NM

info for NS1 and NS2 can be found in this database , I found setting the IPv4 in the NM to Automatic (PPP) address only the best solution if you have problems , 

example my settings ; set the tab to  Automatic (PPP) address only 

in the DNS servers **Box** enter the NS1 and NS2 : eg ; 49.254.192.126, 149.254.201.126

as for details on the NM database and how to modify you can have a look at my posts / 

[http://ubuntuforums.org/showthread.php?t=1331660&page=3](http://ubuntuforums.org/showthread.php?t=1331660&page=3)

---

### Post by cong06 on 2010-02-19
I'm confused. How does that help to set my ppp connection (with network manager) to persist?

---

### Post by alexfish on 2010-02-24
> **cong06 said:**
> I'm confused. How does that help to set my ppp connection (with network manager) to persist?


                                 Hi
 

  Persist is not the issue when using the network manager
 

  Most of the data changes for the option files get bypassed when using the Network Manager via the already mentioned providers.xml.  Database , so if using NM for the connection try to leave options file at default unless you want to use other methods such as  wvdial as most of these can be set directly through the network manager.  
 

 However the Network Manager is still a bit buggy when Trying to return the resolved addresses of the named servers , this appears to be your problem from reading your post  &#8220;  (sometimes it connects, but has no connection, and a re-connect fixes it). &#8220; , this can be caused by various factors &#8230;
 

 To help with the understanding ,there are two files you could examine &#8220; / etc/resolve.conf   and the etc/ppp/resolv.conf  &#8220;  the first is the result of the NM . Look at the results after making the connection in relation to your problems as first mentioned.
 

 

 The work around which I find best is to set the Ipv4 connection as previously mentioned to &#8220; Automatic (PPP) addresses only&#8221;
 

 

 

 another option is to install Gnome ppp , this is a front end tool to wvdial . Or VMC .Here there are options to change the options file  
 

 Extract :
 

 **Changes required in /etc/ppp/options**

 Some other options need to be set for many mobile network connections to prevent them timing out. These are not possible via the GUI interface and I change them in the the 'master' pppd (I think that stands for ppp daemon) set up file which is **/etc/ppp/options** so the changes apply to all users. We can look at the current options which are set by:

 sudo egrep -v '#|^ *$' /etc/ppp/options

 It is desirable to make a backup before editing the /etc/ppp/options file so to make a copy and open a terminal:

 sudo cp /etc/ppp/options /etc/ppp/options_bak

sudo gedit /etc/ppp/options

 I have made three changes to the file. The first two are essential for most GPRS connections and disable the sending and checking of the echo response sent to check the connection is alive - the echo is not implemented by most mobile service providers and the default result is that 4 echo response requests are sent at 30 second intervals and after the 4th failure to receive a response the connection is broken. If you are disconnected after 2 minutes that is the cause. The new values of 0 inhibit the sending and checking:

 lcp-echo-failure 0

lcp-echo-interval 0

 The third change is essential for the Vodafone PCMCIA Connect Card but does not impact other connections significantly so I do it routinely so I do not forget. It involves disabling negotiation of Van Jacobson style IP header compression by un-commenting

 -vj

 I have also tried modifying the /ect/ppp/options file to add an extra delay before connection as I was sometimes not getting a correct DNS delivered using gnome-ppp with the Vodafone but it seems to have little benefit but you can try.

 connect-delay 5000

 **Permissions again**: I have once had a problem after installing and uninstalling the vodafone connect software with gnome-ppp complaining about permissions which did not seem to be cured by the setting your user permissions as above - it seemed that the other software had modified something and gnome-ppp or more precisely the pppd daemon needed to be run as root. This was cured by setting the setuid attribute with:

 sudo chmod u+s /usr/sbin/pppd

 When an executable file has been given the setuid attribute by root, normal users on the system can execute this file and gain the privileges of root who owns the file.
 
Hope this site can be of help

 [http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm)
 
regards

alexfish

---

### Post by cong06 on 2010-02-24
For my own personal use I am tempted to use wvdial or similar simply because I have more control. However for the lab, I'm going to need to use Network Manager so that users have a fairly easy gui to control the network connections.


> **alexfish said:**
> Persist is not the issue when using the network manager
That's great... but I don't know what you mean by this. You mean that network manager is already set to persist and auto re-dial connections? Maybe the /etc/ppp/options option: persist actually just keeps the connection alive if there's no bandwidth?

> **alexfish said:**
> However the Network Manager is still a bit buggy when Trying to return the resolved addresses of the named servers , this appears to be your problem from reading your post  “  (sometimes it connects, but has no connection, and a re-connect fixes it). “ , this can be caused by various factors …

Actually, in most cases this is caused by a weak connection. Often times the connection will make an attempt and die. Other times it will connect and because there is a very weak signal it will go through but have no effect.

The fix of resetting the connection in some cases works, and in other cases doesn't (depending on the strength of the signal) It's possible that your post is correct, but in order to be absolutely sure of the fix, I will need a persist/auto-redial option.

I wonder if there's a way to write a script so that it calls the dialing again after it's disconnected? Connect Automatically might be what I want...


> **alexfish said:**
> The work around which I find best is to set the Ipv4 connection as previously mentioned to “ Automatic (PPP) addresses only”
What does this mean, exactly?

On a related note, my usb modem is occasionally disconnecting part way through usage, randomly, without log notes (other then Modem Hangup).

---

### Post by alexfish on 2010-02-28
Hi

with regards to the above

The best advice I can give at present is to look at how the PPP works and at the options etc ,also the how to for creating your own user scripts , from this site

[http://tldp.org/HOWTO/PPP-HOWTO/dns.html](http://tldp.org/HOWTO/PPP-HOWTO/dns.html)



With the best intention

 A little reading helps

Regards

alexfish

---

### Post by alexfish on 2010-03-02
Further to post #6

Here I have change the IPCP configure-NAKs returned before starting ,  remove the # and set the number to 30

Code:

sudo gedit  /etc/ppp/options

# Set the maximum number of IPCP configure-NAKs  returned before starting
# to send configure-Rejects instead to  <n> (default 10).
ipcp-max-failure 30


save the file and exit

then leave the NM IPv4 settings to Automatic (PPP)  instead of Setting the NM to IPv4 settings to Automatic (PPP) address  only and having to enter the numerical addresses in the DNS servers text  box.

see how it goes

to keep the connection : Set the NM to connect Automatically

regards

alexfish

---

### Post by cong06 on 2010-03-22
It's still doing it :/

I've tried everything you've said, with /etc/ppp/options and with Network Manager.

Is there no way to script /etc/ip-down.d/ to just reconnect?

/var/log/messages
```

Mar 22 11:17:26 kimende-s pppd[6176]: LCP terminated by peer
Mar 22 11:17:26 kimende-s pppd[6176]: Connect time 21.7 minutes.
Mar 22 11:17:26 kimende-s pppd[6176]: Sent 838478 bytes, received 15196347 bytes.
Mar 22 11:17:26 kimende-s pppd[6176]: Modem hangup
Mar 22 11:17:26 kimende-s pppd[6176]: Connection terminated.
Mar 22 11:17:26 kimende-s pppd[6176]: Using interface ppp0
Mar 22 11:17:26 kimende-s pppd[6176]: Connect: ppp0 <--> /dev/ttyUSB0

```

suspicious lines in /var/log/syslog at the same time:
```

Mar 22 11:17:26 kimende-s pppd[6176]: rcvd [LCP TermReq id=0xb]
Mar 22 11:17:26 kimende-s pppd[6176]: LCP terminated by peer
Mar 22 11:17:26 kimende-s pppd[6176]: Connect time 21.7 minutes.
Mar 22 11:17:26 kimende-s pppd[6176]: Sent 838478 bytes, received 15196347 bytes.
Mar 22 11:17:26 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 8 -> 7
Mar 22 11:17:26 kimende-s pppd[6176]: Script /etc/ppp/ip-down started (pid 7992)
Mar 22 11:17:26 kimende-s pppd[6176]: sent [LCP TermAck id=0xb]
Mar 22 11:17:26 kimende-s pppd[6176]: Modem hangup
Mar 22 11:17:26 kimende-s pppd[6176]: Connection terminated.
Mar 22 11:17:26 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9
Mar 22 11:17:26 kimende-s NetworkManager: <WARN>  monitor_cb(): Could not read ppp stats: No such device
Mar 22 11:17:26 kimende-s NetworkManager: <debug> [1269245846.236957] nm_serial_device_close(): Closing device 'ttyUSB0'
Mar 22 11:17:26 kimende-s NetworkManager: <info>  Marking connection 'Zain' invalid.
Mar 22 11:17:26 kimende-s NetworkManager: <info>  Activation (ttyUSB0) failed.
Mar 22 11:17:26 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3
Mar 22 11:17:26 kimende-s NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Mar 22 11:17:26 kimende-s NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Mar 22 11:17:26 kimende-s NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Mar 22 11:17:26 kimende-s pppd[6176]: using channel 5
Mar 22 11:17:26 kimende-s pppd[6176]: Using interface ppp0
Mar 22 11:17:26 kimende-s pppd[6176]: Connect: ppp0 <--> /dev/ttyUSB0
Mar 22 11:17:26 kimende-s pppd[6176]: sent [LCP ConfReq id=0x2 <asyncmap 0x0> <magic 0x3ae3e107> <pcomp> <accomp>]
Mar 22 11:17:26 kimende-s named[2217]: received control channel command 'reconfig'
Mar 22 11:17:26 kimende-s named[2217]: loading configuration from '/etc/bind/named.conf'
Mar 22 11:17:26 kimende-s named[2217]: max open files (1024) is smaller than max sockets (4096)
Mar 22 11:17:26 kimende-s named[2217]: using default UDP/IPv4 port range: [1024, 65535]
Mar 22 11:17:26 kimende-s named[2217]: using default UDP/IPv6 port range: [1024, 65535]
Mar 22 11:17:26 kimende-s named[2217]: no longer listening on 172.20.35.72#53
Mar 22 11:17:26 kimende-s named[2217]: reloading configuration succeeded
Mar 22 11:17:26 kimende-s named[2217]: any newly configured zones are now loaded
Mar 22 11:17:26 kimende-s named[2217]: received control channel command 'reconfig'
Mar 22 11:17:26 kimende-s named[2217]: loading configuration from '/etc/bind/named.conf'
Mar 22 11:17:26 kimende-s named[2217]: max open files (1024) is smaller than max sockets (4096)
Mar 22 11:17:26 kimende-s named[2217]: using default UDP/IPv4 port range: [1024, 65535]
Mar 22 11:17:26 kimende-s named[2217]: using default UDP/IPv6 port range: [1024, 65535]
Mar 22 11:17:26 kimende-s named[2217]: reloading configuration succeeded
Mar 22 11:17:26 kimende-s named[2217]: any newly configured zones are now loaded
Mar 22 11:17:26 kimende-s postfix/master[2479]: reload configuration /etc/postfix
Mar 22 11:17:26 kimende-s pppd[6176]: Script /etc/ppp/ip-down finished (pid 7992), status = 0x0
Mar 22 11:17:26 kimende-s postfix/master[2479]: reload configuration /etc/postfix

```
followed by those "named[XXXX]: network unreachable resolving: '....'" errors
```

cat /var/log/syslog.0 | grep -c "Mar 22 11\:17\:26 kimende-s named\[2217\]\: network unreachable resolving"
190

```

---

### Post by alexfish on 2010-03-22
Hi

looking at the log file the your peer is terminating the connection

Hi



 pppd[6176]: [COLOR=RoyalBlue]LCP terminated by peer[/COLOR]
 kimende-s pppd[6176]: Connect time 21.7 minutes.
 kimende-s pppd[6176]: Sent 838478 bytes, received 15196347 bytes.
 kimende-s NetworkManager: <info>  (ttyUSB0): device state change: 8 -> 7
 kimende-s pppd[6176]: Script /etc/ppp/ip-down started (pid 7992)
 kimende-s pppd[6176]: sent [LCP TermAck id=0xb]
 kimende-s pppd[6176]: Modem hangup

maybe LCP echo is not implemented by your peer

this can be resolved by editing the /etc/ppp/options



lcp-echo-failure 0

lcp-echo-interval 0

regards 

alexfish

---

### Post by cong06 on 2010-03-22
> **alexfish said:**
> 
this can be resolved by editing the /etc/ppp/options



lcp-echo-failure 0

lcp-echo-interval 0


That's interesting because I already have those settings...
Does the network manager actually use the /etc/ppp/options file?

(coincidentally the "Send PPP echo packets" is also disabled.)

/etc/ppp/options file:
```

root@kimende-s:/# cat /etc/ppp/options | grep -v "^#" | grep -v "^$"
asyncmap 0
noauth
crtscts
lock
hide-password
modem
debug
kdebug 4 
proxyarp
lcp-echo-interval 0
lcp-echo-failure 0 
ipcp-max-terminate 30 
noipx
persist

```

---

### Post by alexfish on 2010-03-22
Hi

I have looked up the a debug of this output

Extract:

Sep  3 13:54:44 ayaki pppd[22271]: pppd 2.4.4 started by root, uid 0
Sep  3 13:54:44 ayaki pppd[22271]: Using interface ppp0
Sep  3 13:54:44 ayaki pppd[22271]: Connect: ppp0 <--> /dev/ttyACM0
Sep  3 13:54:47 ayaki pppd[22271]: PAP authentication succeeded
Sep  3 13:54:47 ayaki pppd[22271]: LCP terminated by peer
Sep  3 13:54:50 ayaki pppd[22271]: Connection terminated.
Sep  3 13:54:50 ayaki pppd[22271]: Modem hangup
Sep  3 13:54:50 ayaki pppd[22271]: Exit.


Note the successful authentication, then connection  termination by the remote end. 
That, or  successful negotiation followed by the inability to send and receive IP  packets, could also indicate that your cellular service has barring  active on data connections. You'd need to talk to the accounts people at  your provider.

from

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing](https://wiki.ubuntu.com/NetworkManager/Hardware/3G/Probing)

at present these are the settings in my options file

alexfish@alexfish-desktop:~$ cat /etc/ppp/options | grep -v "^#" | grep -v "^$"
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
replacedefaultroute
noipx

Note the " replacedefaultroute " this is a option I have been trying from details on post with this forum, although the ipcp-max-failure has been more successful at getting the  connections first time.both of these methods help in getting the Primary and Secondary addresses returned by the NM into the etc/resolv.conf

As regards the options file working 100 % with NM, some seem to work, I can only assume that editing the options file is dependant on how your peer is configured .The NM as far as I know tries different methods in obtaining the correct 
which one takes priority NM or the options file I am not sure. never tested but worth experimenting with.or further reading required.


configurations,therefore if by altering the options file produces an error then reverse the changes, if it is a success then I can assume the changes work

I will search further into  details about scripting for the ppp as there are several sites which may be of help

regards

alexfish

---

### Post by alexfish on 2010-03-22
hi

back with a site which may be of use, note this link will place you at an option mentioned in your first post

**15.3. Other options to consider  adding**

There are a couple useful things you might want to add  to the /etc/ppp/options file.
One is an idle time. Pppd can terminate the connection if it  has been idle for too long. This could be nice if your isp charges by time, or if you  don't want to keep your phone line tied up. To use this feature, simply add  the line:

# Idle after X seconds

idle X

Replace 'X' with the number of  seconds you wish the connection to terminate after.

The next feature is "dial on demand". This means that every  time you attempt to open an interent connection, pppd will try to open a PPP connection to your ISP. In order to do this, add the following lines to /etc/ppp/options

# dial on demand

demand

The link

[http://tldp.org/HOWTO/PPP-HOWTO/x980.html](http://tldp.org/HOWTO/PPP-HOWTO/x980.html)

also in ubuntu the network setting etc can be found in the gconf 

from the terminal enter this code

Code:

gconf-editor

[https://help.ubuntu.com/community/NetworkManager#Editing%20Network%20Settings%20in%20Nm-editor]("https://help.ubuntu.com/community/NetworkManager#Editing%20Network%20Settings%20in%20Nm-editor")

regards

alexfish

---

### Post by cong06 on 2010-03-23
> **alexfish said:**
> 
Sep  3 13:54:44 ayaki pppd[22271]: pppd 2.4.4 started by root, uid 0
Sep  3 13:54:44 ayaki pppd[22271]: Using interface ppp0
Sep  3 13:54:44 ayaki pppd[22271]: Connect: ppp0 <--> /dev/ttyACM0
Sep  3 13:54:47 ayaki pppd[22271]: PAP authentication succeeded
Sep  3 13:54:47 ayaki pppd[22271]: LCP terminated by peer
Sep  3 13:54:50 ayaki pppd[22271]: Connection terminated.
Sep  3 13:54:50 ayaki pppd[22271]: Modem hangup
Sep  3 13:54:50 ayaki pppd[22271]: Exit.

Note the successful authentication, then connection  termination by the remote end. 
That, or  successful negotiation followed by the inability to send and receive IP  packets, could also indicate that your cellular service has barring  active on data connections. You'd need to talk to the accounts people at  your provider.

The one thing I should clarify is that ppp is connecting, and I'm even downloading a bit. The amount of time after which it disconnects (without reason) is very sporadic. Sometimes after 30 seconds of downloading it disconnects, sometimes after 2 hours of downloading it disconnects. I'm fairly certain it's the same error...


> **alexfish said:**
> ```

replacedefaultroute
idle X
demand
```
I'll try messing around with these and post back if I have any luck (or lack of it).
Unfortunately I couldn't find the option "replacedefaultroute" so I think I'll do a bit more research before I just type it in my /etc/ppp/options file.

I do have one question about the demand option:
```
# Initiate the link only on demand, i.e. when data traffic is present. 
# With this option, the remote IP address must be specified by the user on
# the command line or in an options file.  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppda will
# commence passing data packets (i.e., IP packets) across the link.
```
Personally I'm not sure which IP address to specify or where...

> **alexfish said:**
> 
[https://help.ubuntu.com/community/NetworkManager#Editing%20Network%20Settings%20in%20Nm-editor]("https://help.ubuntu.com/community/NetworkManager#Editing%20Network%20Settings%20in%20Nm-editor")
It's unfortunate that that link doesn't seem to discuss the right topics, or point me in the right direction...
Most of the things discussed there were only for wireless, and I have already experimented with auto-connecting to no avail.

---

### Post by cong06 on 2010-03-23
I tried demand and idle.
With both enabled the network manager refused to connect.
Since I couldn't disable demand without idle:
```

# Specifies that pppd should disconnect if the link is idle for <n> seconds.
# The link is idle when no data packets (i.e. IP packets) are being sent or
# received.  [COLOR="Red"]Note: it is not advisable to use this option with the persist
# option without the demand option.[/COLOR]  If the active-filter option is given,
# data packets which are rejected by the specified activity filter also
# count as the link being idle.
```

I tried disabling persist and idle, but the problem probably has to do with the missing IP:
```

# Initiate the link only on demand, i.e. when data traffic is present. 
# [COLOR="Red"]With this option, the remote IP address must be specified by the user on
# the command line or in an options file.[/COLOR]  Pppd will initially configure
# the interface and enable it for IP traffic without connecting to the peer. 
# When traffic is available, pppd will connect to the peer and perform
# negotiation, authentication, etc.  When this is completed, pppd will
# commence passing data packets (i.e., IP packets) across the link.

```

---

### Post by cong06 on 2010-04-10
So I just stumbled on a hint.

I have a laptop with UNR Karmic. In this version/build, if I use the modem, I have noticed it to auto-reconnect sporadically.
I suspect the feature that I'm digging for in Jaunty is built into Karmic.

While I do expect to upgrade some machines to Lucid (where I would expect the feature to be carried over) I wonder if there's a solution to this in Jaunty so that those that aren't upgraded will have a solution.

Would upgrading Network Manager make a difference?

---

### Post by alexfish on 2010-04-24
hi cong06

did you upgrade, any further progress RE; configuring the network manager

found where details for the NM connections details  are stored on the system

to get to it from the terminal

Code:

gksudo nautilus

then steer to this file etc/NetworkManager/system-connections  select the file and  open with gedit

maybe this could be cross referenced to any details edited in the options file, not sure if this is a working file , and gets updated when the connection is made, however treat with caution / IE , use at your own risk

regards

alexfish

---

### Post by cong06 on 2010-05-05
Unfortunately, in my case the PPP connections aren't listed in that folder...

---

### Post by alexfish on 2010-05-05
> **cong06 said:**
> Unfortunately, in my case the PPP connections aren't listed in that folder...

Hi

as regards the Network Manager my version = version 0.8

the system-connections does exist in this folder and can confirm it is a working file used by the system

these are two extracts from the file / changed the IPv4 settings 


                                  [ipv4]  
 method=auto  
 dns=149.254.201.126;149.254.192.126;  
 ignore-auto-routes=false  
 ignore-auto-dns=true  
 dhcp-send-hostname=false  
 never-default=false
 

 [ipv4]  
 method=auto  
 ignore-auto-routes=false  
 ignore-auto-dns=false  
 dhcp-send-hostname=false  
 never-default=false
 

 also changes to the options file also appear in this file but have not checked them all

can't confirm where the working files are in jaunty or karmic if the NM is lest than o.8

I have seen some of the options listed on some sites regarding what you were looking for . But will have to back track

if you upgrade ensure NM and  Modem Manager Versions are the same

regards

alexfish

---

### Post by cong06 on 2010-05-05
Again, I should have clarified.
I have 3 connections set up with Network Manager:
eth0:
"Auto Eth0"
ppp:
"Safaricom"
"Zain"

However, when I open up /etc/NetworkManager/system-connections, there is only "Auto Eth0"

So my question should have been:
How do I write a config for "Zain" and "Safaricom" without knowing what they're supposed to look like?

---

### Post by alexfish on 2010-05-05
say for instance NM connection name is T-Mobile Default

then if I do a search under that name then it finds the file .copy and  paste so get no typos err . all I can suggest .

Update:

did a direct edit of this file  and the NM lost the info IE NO Mobile broadband connection. leading to add new connection , gave it a different name 

have tried to trace under the name but does not show ? ... but the  original file still exists 

Need to look into this further .

---

### Post by cong06 on 2010-05-05
I guess I don't understand.
In my "/etc/NetworkManager/" folder, there are only 3 files:

```

root@kimende-s:/etc/NetworkManager# tree
.
|-- dispatcher.d
|   `-- 01ifupdown
|-- nm-system-settings.conf
`-- system-connections
    `-- Auto eth0

```
So files for mobile broadband aren't available.
Unless you think I should copy them off the "Auto eth0" file?

---

### Post by alexfish on 2010-05-05
basically the same with exception of VPN dir

Have Checked back to 9.10 . here is an assumption

when the system is first installed the NM or what ever is Writing the configs to the System connections . and also recognised by the name .

subsequent connections are stored else where , problem been can't find the file by name
how ever direct editing of the file renders the file obsolete in the eyes of nm/ assuming date stamp /or other . in one sense , good security . but can't confirm
problem here is trying to find the other configs stored by NM.

Looks like  your only option at present will be to use PPP directly if you can't get NM to Totally cooperate with the options files etc .

I will continue to look at the above ,

PS ; Readers , Looks if my assumption on post #17 was correct " treat with caution " I Know how to fix this , Some may not . You have been Warned 
regards

alexfish

---

### Post by cong06 on 2010-05-06
Maybe another easy option would be to install karmic+ network manager into jaunty installs.
Jaunty's version is 0.7.1~rc4.1.cf199a964-0ubuntu2
What's the version in Karmic? (I don't have a karmic computer anymore :/)

---

### Post by cong06 on 2010-11-22
I don't think I properly explained what the issue was:
I wanted to have the modem re-dial.

Now, it turns out that the main issue was that in order to re-dial, I had to unplug and replug it.

I found this:
[http://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line](http://askubuntu.com/questions/645/how-do-you-reset-a-usb-device-from-the-command-line)

If you compile the code that they give, you can create an executable. I put it in /usr/bin and named it usbreset.

Then I created this script:
```

#!/bin/bash

# Check if Root
if [ "$(whoami)" != "root" ]; then
    echo "Sorry, you are not root."
    exit 1
fi

device=`lsusb | grep Huawei | cut -d ' ' -f 4 | sed -e 's/://g'`
bus=`lsusb | grep Huawei | cut -d ' ' -f 2`

usbreset /dev/bus/usb/$bus/$device

```

and saved it in:
/etc/ppp/ip-down.d/reset_modem

Then the only thing left was to set my modem to "connect automatically" in Network Manager.

When the modem disconnects, the script runs, resetting the modem. It's as if its redectecting the modem again. This resets it's entry in the Network Manager, causing it to respond as if it's just been inserted, and so it dials.

And actually, the 'usbreset' is much much faster than pulling out the modem manually; lets say 10 seconds instead of 3 minutes.

---


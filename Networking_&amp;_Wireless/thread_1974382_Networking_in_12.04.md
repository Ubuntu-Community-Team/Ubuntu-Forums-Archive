---
title: "Networking in 12.04"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by AnupamMitra on 2012-05-06
Today I installed Ubuntu 12.04 besides of Windows 7. I'm having wired connection in my PC. Though there is connection of internet in UBUNTU 12.04, but the Mozilla browser is not opening. I'm attaching the screen shot of internet connection information.

[ATTACH]217378[/ATTACH]

I think somewhere something is wrong.

Please help me.

---

### Post by AnupamMitra on 2012-05-08
Adding further :
 
Whenever I'm opening the browser, it shows Problem Loading Page. Current connection information and ifcong is given below.
 
[ATTACH]217527[/ATTACH]
 
Can anybody fix it?

---

### Post by chili555 on 2012-05-08
The 10.42.x.y IP address suggests you've set up an ad-hoc or computer-to-computer connection in Network Manager. You want computer to router. Please try deleting all the connection data in Network Manager and rebooting. Let Network Manager communicate to the router and obtain an IP address automatically, I assume in the 192.168.x.y range.

Are there other Windows computers on the network? What IP address range do they have?

---

### Post by AnupamMitra on 2012-05-08
Sorry, adding further. 
 
Screenshot of Ifconfig is given below
 
[ATTACH]217529[/ATTACH]

---

### Post by AnupamMitra on 2012-05-08
Thank you Sir for your cooperation. As per your advice I have deleted all the connection and rebooted. But now I'm not getting any connection. Earlier I put "Shared to other Computers" in IPv4 settings. 
 
In Windows Computers IP adress is 117.194.1.237 and it is a static IP.
 
Awaiting for your further advice.

---

### Post by chili555 on 2012-05-08
> Earlier I put "Shared to other Computers" in IPv4 settings.
Is that what you really want? That means computer-to-computer. I suggest you change it to Automatic-DHCP.

---

### Post by AnupamMitra on 2012-05-08
As per your suggestion, now IPv4 is fixed at "Automatic-DHCP". But network is not getting any connection. However, there is a "ping". I'm giving two screen shots for your information.

[ATTACH]217540[/ATTACH]

[ATTACH]217541[/ATTACH]

Please advice.

---

### Post by chili555 on 2012-05-08
Please reboot and let me see the screenshots for the interface *eth0* and not *lo*.

---

### Post by AnupamMitra on 2012-05-09
As suggested, I'm giving below the screenshots of interface etho.

[ATTACH]217588[/ATTACH]

Please help.

---

### Post by Sergius14 on 2012-05-09
I'm guessing that you don't have a router but directly a modem/cablemodem CPE which is directly attach to a switch... Then from switch to both PC's...

this is correct?

---

### Post by AnupamMitra on 2012-05-09
Yes, you are correct.

---

### Post by Sergius14 on 2012-05-09
Ok.

Easy: Your ISP is limiting you Public IP addresses release to only one. This is very usual and expected.

In your case a router should be installed on your side, so then you have a LAN (addresses 192.168.x.x, 172.16.x.x, 10.x.x.x, etc.) and the router has in it WAN interface your single Public IP address.

Another way is to have two NIC's in one PC and use it as router.


Meantime: Unplug the Win7 PC. Unplug your CableModem CPE. Wait a few seconds to let your carrier knwon that you device is off and then plug in again. Now this time the Ubuntu Machinne you shoud have Internet.

The IP address is leased to a specific MAC address that is released if you unplug the device.

Some ISP give you two or more IP address if you ask them for (may have extra charges). Even if you do this, both PC (Win and Ubuntu) will be directly at the Internet instead of a LAN (can't share resourses easily and secure between them).


My advice: Use a router if you need to set up a LAN and learn about a bit about NAT/PAT and routing.


Let us known if you solve this issue.

---

### Post by chili555 on 2012-05-09
> **AnupamMitra said:**
> As suggested, I'm giving below the screenshots of interface etho.

[ATTACH]217588[/ATTACH]

Please help.When you run this terminal command:```
sudo lshw -C network
```Under the ethernet listing for eth0, does it say *link=yes*? Can you please run this command and show us a screenshot?```
dmesg | grep eth0
```If it's easier, you can copy and paste it here. The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by AnupamMitra on 2012-05-09
> **chili555 said:**
> When you run this terminal command:```
sudo lshw -C network
```Under the ethernet listing for eth0, does it say *link=yes*? Can you please run this command and show us a screenshot?```
dmesg | grep eth0
```If it's easier, you can copy and paste it here. The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

As suggested, I'm pasting the result.

 anupam@ubuntu:~$ sudo lshw -C network
  [sudo] password for anupam:
    *-network               
         description: Ethernet interface
         product: 82566DC Gigabit Network Connection
         vendor: Intel Corporation
         physical id: 19
         bus info: pci@0000:00:19.0
         logical name: eth0
         version: 02
         serial: 00:19:d1:e2:3a:a2
         size: 100Mbit/s
         capacity: 1Gbit/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.1-0 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
         resources: irq:45 memory:70300000-7031ffff memory:70324000-70324fff ioport:30c0(size=32)
  anupam@ubuntu:~$ ^C
  anupam@ubuntu:~$
  


 anupam@ubuntu:~$ dmesg \ grep etho
   
  Usage:
   dmesg [options]
   
  Options:
   -C, --clear                 clear the kernel ring buffer
   -c, --read-clear            read and clear all messages
   -D, --console-off           disable printing messages to console
   -d, --show-delta            show time delta between printed messages
   -E, --console-on            enable printing messages to console
   -f, --facility <list>       restrict output to defined facilities
   -h, --help                  display this help and exit
   -k, --kernel                display kernel messages
   -l, --level <list>          restrict output to defined levels
   -n, --console-level <level> set level of messages printed to console
   -r, --raw                   print the raw message buffer
   -s, --buffer-size <size>    buffer size to query the kernel ring buffer
   -T, --ctime                 show human readable timestamp (could be
                               inaccurate if you have used SUSPEND/RESUME)
   -t, --notime                don't print messages timestamp
   -u, --userspace             display userspace messages
   -V, --version               output version information and exit
   -x, --decode                decode facility and level to readable string
   
  Supported log facilities:
      kern - kernel messages
      user - random user-level messages
      mail - mail system
    daemon - system daemons
      auth - security/authorization messages
    syslog - messages generated internally by syslogd
       lpr - line printer subsystem
      news - network news subsystem
   
  Supported log levels (priorities):
     emerg - system is unusable
     alert - action must be taken immediately
      crit - critical conditions
       err - error conditions
      warn - warning conditions
    notice - normal but significant condition
      info - informational
     debug - debug-level messages
   
  anupam@ubuntu:~$
  

Thanks for your continuous support.

---

### Post by chili555 on 2012-05-09
> anupam@ubuntu:~$ dmesg \ grep ethoThat is incorrect. You want:```
dmesg | grep eth0
```That is the pipe symbol | and not the slash \. Also, it is eth0; in other words eth-zero and not eth-oh.

I believe that Sergius14 has the correct answer:> Your ISP is limiting you Public IP addresses release to only one. This is very usual and expected.

In your case a router should be installed on your side, so then you have a LAN (addresses 192.168.x.x, 172.16.x.x, 10.x.x.x, etc.) and the router has in it WAN interface your single Public IP address.

Another way is to have two NIC's in one PC and use it as router.


Meantime: Unplug the Win7 PC. Unplug your CableModem CPE. Wait a few seconds to let your carrier knwon that you device is off and then plug in again. Now this time the Ubuntu Machinne you shoud have Internet.

The IP address is leased to a specific MAC address that is released if you unplug the device.

Some ISP give you two or more IP address if you ask them for (may have extra charges). Even if you do this, both PC (Win and Ubuntu) will be directly at the Internet instead of a LAN (can't share resourses easily and secure between them).

---

### Post by AnupamMitra on 2012-05-10
> **chili555 said:**
> That is incorrect. You want:```
dmesg | grep eth0
```That is the pipe symbol | and not the slash \. Also, it is eth0; in other words eth-zero and not eth-oh.

I believe that Sergius14 has the correct answer:

Sorry for the trouble. Due to ignorance, I couldn't follow your instruction. However, I'm pasting below the result of code dmesg | grep eth0.

 anupam@ubuntu:~$ dmesg | grep eth0
  [    7.786529] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:19:d1:e2:3a:a2
  [    7.786536] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
  [    7.786565] e1000e 0000:00:19.0: eth0: MAC: 6, PHY: 6, PBA No: FFFFFF-0FF
  [   31.239589] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   34.180517] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   34.181068] ADDRCONF(NETDEV_UP): eth0: link is not ready
  [   35.520875] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
  [   35.520884] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
  [   35.521198] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
  [   46.000014] eth0: no IPv6 routers present
  [   94.160068] eth0: no IPv6 routers present
  [  142.752013] eth0: no IPv6 routers present
  anupam@ubuntu:~$ ^C
  anupam@ubuntu:~$
  
However, I would like to clarify that I'm not maintaining two PCs. In a single PC, I'm having dual booting system i.e. WINDOWS 7 & and UBUNTU 12.04. Therefore, is it necessary to create a LAN for internet connection, as Sergius14 has suggested ? Earlier when I was using UBUNTU older version, say 2009 and/or 2010, there was no problem of getting internet connection.

Thanks for your continuous support. Awaiting for your advice.

---

### Post by chili555 on 2012-05-10
Before we continue, let's just clarify and confirm. You have one computer and it is connected to a DSL or cable modem. The computer dual-boots and sometimes is booted into Ubuntu and sometimes Windows 7; is that correct? Is there any other device involved, a router or switch or anything?

If it's a DSL modem, is a user name and password required?

---

### Post by AnupamMitra on 2012-05-10
I conform that I'm having one Computer and it is connected to an ADSL Modem. Sometimes it is booted into UBUNTU and sometimes WINDOWS 7. No other device is involved, neither Switch nor Router. My Modem requires User Name and Password.

---

### Post by chili555 on 2012-05-10
Thank you for the clarification. I have a much better understanding now.

Is the user name and password authentication set up in the ADSL modem or in the Ubuntu computer? Network Manager can handle all this for you.

---

### Post by AnupamMitra on 2012-05-11
The user name and password authentication set up is in the ADSL Modem.

---

### Post by chili555 on 2012-05-11
Let's see what Network Manager is doing while trying to connect. Please run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Thanks.

---

### Post by AnupamMitra on 2012-05-11
> **chili555 said:**
> Let's see what Network Manager is doing while trying to connect. Please run and post:```
sudo cat /var/log/syslog | grep etwork | tail -n20
```Thanks.

The following is the result of the suggested code.

 anupam@ubuntu:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
  [sudo] password for anupam:
  May 11 22:12:39 ubuntu NetworkManager[814]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
  May 11 22:12:39 ubuntu NetworkManager[814]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
  May 11 22:12:39 ubuntu NetworkManager[814]: <info> dhclient started with pid 1975
  May 11 22:12:39 ubuntu NetworkManager[814]: <info> Activation (eth0) Beginning IP6 addrconf.
  May 11 22:12:39 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
  May 11 22:12:39 ubuntu NetworkManager[814]: <info> (eth0): DHCPv4 state changed nbi -> preinit
  May 11 22:12:59 ubuntu NetworkManager[814]: <info> (eth0): IP6 addrconf timed out or failed.
  May 11 22:12:59 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
  May 11 22:12:59 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
  May 11 22:12:59 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
  May 11 22:13:24 ubuntu NetworkManager[814]: <warn> (eth0): DHCPv4 request timed out.
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1975
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) started...
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> (eth0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> Marking connection 'Wired connection 1' invalid.
  May 11 22:13:24 ubuntu NetworkManager[814]: <warn> Activation (eth0) failed.
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> Activation (eth0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> (eth0): device state change: failed -> disconnected (reason 'none') [120 30 0]
  May 11 22:13:24 ubuntu NetworkManager[814]: <info> (eth0): deactivating device (reason 'none') [0]
  anupam@ubuntu:~$
  

I inform you further that when I was using older version of UBUNTU, I was used to give command of *sudo pon dsl-provider *to open internet and *sudo poff dsl-provider* to close. There was no problem with this.

Awaiting for your suggestion.

---


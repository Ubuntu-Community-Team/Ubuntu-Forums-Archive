---
title: "How can i get ubuntu online via windows mobile cellphone?"
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by piergen on 2011-01-15
I have a HTC Touch with windows mobile 6.5. I would like to be able to connect my xubuntu to internet via cellphone. I use a usb cable to connect windowspc and that works for iwndows laptop but not for xubuntu.

I have found [this thread ]("http://ubuntuforums.org/showthread.php?t=869229")that is spot on topic. But as i dont have dsl connection or anything else at the moment I can install anything via terminal. And choosing to [get packages]("http://packages.ubuntu.com/hardy/subversion") will as often before result in broken dependencies and that makes it impossible to come around.

1: Is there a way to determine if I allready have subversion installed? (terminal command?)

2: Have any one else solved this issue somehow? Remember I live out in the bush far away from any wirelss lan or even neighbours. So how can I connect xubuntu to internet via 3G from the windows mobile cellphone? Somehow I must be able to install everything needed without running into dependencies problems.

---

### Post by piergen on 2011-01-15
As I did not get any respons on this thread I will try out everything I can think of that might get me connected and online with the ubuntu box.
First thing I have done is to for the moment drop to connect to windows mobile cellphone directly to ubuntu pc. Rather I try to use a shared internet connection from the winxp pc. Also I will use a Linksys router WRT54 GL with dd-wrt firmware v24.


I have turned off DHCP in router but still I can't share internet connection.

Here is the error I get:

> A LAN connection is already configured
 with the IP address that is required for automatic IP addressing
[B]
I guess there must be some subnet issues here?[/B]


When I run ipconfig I get this:

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\xxxxx>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.215.200
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Wireless Network Connection:

        Media State . . . . . . . . . . . : Media disconnected

Ethernet adapter Local Area Connection 3:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . . . . :

Ethernet adapter Local Area Connection 6:

        Connection-specific DNS Suffix  . : xxx.xxx.xx
        IP Address. . . . . . . . . . . . : 192.168.0.102
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1

C:\Documents and Settings\xxxxx>
```

Is there any reasson why I can not share the internet connection now?

---

### Post by piergen on 2011-01-15
so here I must have done somethong wrong, what values do I put in here in the network setup part in dd-wrt settings?

[IMG]http://www.wi-fiplanet.com/img/2006/08/dhcprange_sm.gif[/IMG]

Should the router be DHCP or not? I mean when I try to set the winxp pc up for internet sharing I belive winxp will turn itself into a DHCP and give out IP adresses, correct?
So how can I setup dd-wrt router in a way that I can connect the two pc's yet without interfearing with the internet connection sharing from winxp?

---

### Post by piergen on 2011-01-15
Hmm. Maybe I have done wrong here? Maybe I need to connect winxp pc to the Internet port on the back of the router? Then things must work? Even if I leave DHCP enebled on router?

---

### Post by piergen on 2011-01-15
Running 
```
sudo dhclient
```

I get this:

> Listening on LPF/eth0/00:1d:60:88:23:81
Sending on   LPF/eth0/00:1d:60:88:23:81
Listening on LPF/vmnet8/00:50:56:c0:00:08
Sending on   LPF/vmnet8/00:50:56:c0:00:08
Listening on LPF/vmnet1/00:50:56:c0:00:01
Sending on   LPF/vmnet1/00:50:56:c0:00:01
Sending on   Socket/fallback
DHCPDISCOVER on vmnet8 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.130.129 from 192.168.130.254
DHCPREQUEST of 192.168.130.129 on vmnet8 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPACK of 192.168.130.129 from 192.168.130.254
bound to 192.168.130.129 -- renewal in 780 seconds.

One would belive there should be possible to connect this pc and the  winxp pc to share a internet connection now as they are on different  subnet?

---

### Post by piergen on 2011-01-15
As I now have struggled for days with the lack of internet connection on the ubuntu I am getting fed up.
If there is anything more I need to post for the thread to make sense pls let me know and I will update as soon as possible. 

Surely there must be a way to get a Linux pc online via cell and 3G OR via internet connection sharing?

I can not realy belive I am the only one that has struggled with this so there must be people that know both network, linux and windows here that can help me?

---

### Post by piergen on 2011-01-15
Ok I have dropped the switch and are now using a Linksys WRT54 GL router with dd-wrt firmware v24.

I now have the windowspc and the ubuntu on different subnet.
Here is my ```
 sudo dhclient
```> Listening on LPF/eth0/00:1d:60:88:23:81
Sending on   LPF/eth0/00:1d:60:88:23:81
Listening on LPF/vmnet8/00:50:56:c0:00:08
Sending on   LPF/vmnet8/00:50:56:c0:00:08
Listening on LPF/vmnet1/00:50:56:c0:00:01
Sending on   LPF/vmnet1/00:50:56:c0:00:01
Sending on   Socket/fallback
DHCPDISCOVER on vmnet8 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.130.129 from 192.168.130.254
DHCPREQUEST of 192.168.130.129 on vmnet8 to 255.255.255.255 port 67
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPACK of 192.168.130.129 from 192.168.130.254
bound to 192.168.130.129 -- renewal in 780 seconds.[U]
Ipconfig on windows give this result:[/U]

[B]
Here is the part for the usb cable connection between windows mobile cellphone and windowspc:[/B]


> Ethernet adapter Local Area Connection 6:

        Connection-specific DNS Suffix  . : xxx.xxx.xx
        IP Address. . . . . . . . . . . . : 192.168.[COLOR=Blue]**0.102**[/COLOR]
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1**And this is for the wired lan connection via Linksys router:**


> Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Autoconfiguration IP Address. . . : 169.254.215.200
        Subnet Mask . . . . . . . . . . . : 255.255.0.0
        Default Gateway . . . . . . . . . :Clearly the two connections are now on different subnets, right?

In theory there should be no reasson for the same error message anymore as the two connections are on different subnets.

Why can I still not get xubuntu online?

---

### Post by piergen on 2011-01-16
Is there anything I might need to submit of information in order to get help pls let me know and I will adress that asap. Hope someone has seen and solved issues like this before.

I am sure I must have overlooked something here. Maybe if some fresh eyes looks closely we can solve this.

---

### Post by piergen on 2011-01-16
Really is this matter impossible to solve? Or is it maybe me who have problems writing in an adequate language? Is it maybe my poorly discription of the problems or the steps I hae taken to try to overcome connection problems?

I must say I am a bit disappointed. It used to be that ubuntuforums was full of people keen to help out others, and that was one of the reassons I chose ubuntu in the first place. 

This time I have struggled with several problems for more then two weeks. Neither one is solved properly even though I have done several posts here.  Is this just seen thru the eyes of a beaten and tired old man, or has the community spirit got lost somewhere along the way?

I mean this thread I have worked with for days and nights now, or close to 48 hours. Yet not one have given me any thoughts or ideas how to overcome issues.

Really there must have been other that has managed to resolve issues like this?

---


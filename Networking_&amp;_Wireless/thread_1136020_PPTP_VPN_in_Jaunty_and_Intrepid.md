---
title: "PPTP VPN in Jaunty and Intrepid"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by SabreWolfy on 2009-04-24
This worked for me. Use at your own risk. YMMV. **[COLOR="Red"]Edit: See post #4 below for an important update to this post ...[/COLOR]**

I've bleated previously here and on Launchpad about how PPTP VPN worked perfectly under Hardy and was broken under Intrepid and Jaunty. For me, this was a "deal-breaker" because I need PPTP VPN access. I have not upgraded my desktop Hardy machine for this reason. I did upgrade my laptop to Intrepid and now to Jaunty and got around the problem by using PPTP VPN in a Xubuntu Hardy VirtualBox.

I've spent the evening looking at this again and I've managed to get PPTP VPN working on my Jaunty laptop. I'm not a PPTP or VPN expert by any means.

I used [this]("http://kryptoz.wordpress.com/2007/08/07/linux-pptp-vpn-client-configuration/") post as starting point, so thanks to kryptoz. The problem as I can see it is that Network Manager 0.7 (Intrepid and Jaunty) and the associated PPTP plugin are broken. Under Hardy (Network Manager 0.6.6) everything works. There are many posts detailing the myriad problems with Network Manager 0.7. However, using the Network Manager applet is simply a front-end to calling PPTP and PPPD which actually make the connection (I think).

My solution does not involve the Network Manager applet at all. The connection is established by calling PPPD. The pptp-linux and ppp (for pppd) package must be installed and the pptpd package as well (I think).

1. Add the following to /etc/ppp/chap-secrets:

```
Username   PPTP   Password   *
```

2. Create /etc/ppp/peers/vpn1. The 'peers' folder may be owned by group 'dip' so get around that by adding yourself to the group (I have no idea if this is a good solution, but it worked). Add the following to the vpn1 file:

```
pty "pptp remote.gateway.address.here  --nolaunchpppd"
name Username
remotename PPTP
require-mppe-128
file /etc/ppp/options.pptp
ipparam vpn1

```

3. Edit the options.pptp file as required. I commented out the 'refuse-chap' and 'refuse-mschap-v2' lines.

4. Establish the VPN connection with:

```
sudo pppd call vpn1
```

or

```
sudo pon vpn1
```

5. Drop the connection when you're done with:

```
sudo poff vpn1
```

That establishes a VPN connection but I could not get any traffic through it. Therefore, create '/etc/ppp/ip-up.d/route-traffic' as follows. I don't know why the file needs to have that name or be located in that folder, because it does not appear to be executed automatically. Thanks to [this]("http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html") site for this information:

```

#!/bin/bash
NET="10.0.0.0/8"
IFACE="ppp0"
route add -net ${NET} dev ${IFACE}

```

Make the file executable.

Replace the "10.0...." address with the range of addresses you need to access on your remote machine. For me, this was the same range as that which I originally included when setting the VPN up in Hardy. It may look like "10.2.0.0/16" for example. The values don't have to be in the "10" range (mine were not).

So, to get the VPN up in Jaunty, I did the following (in /etc/ppp/ip-up.d):

```

sudo pon vpn1
sudo ./route-traffic

```

**[COLOR="Red"]Edit: See post #4 below for an important update to this post ...[/COLOR]**

---

### Post by AntiBodies on 2009-04-25
this is really lame

i to cannot get the pptp vpn network manager plugin to work

it gives no feedback as to what is happening.. sometimes coming up with failed messages

ive been coming accross a few things that just arn't working in jaunty and have been regressions.. what is up with this? i suppose it is the nature of foss software but man it eems like things go 1 step forward 3 steps back

---

### Post by SabreWolfy on 2009-04-26
PPTP VPN worked for me in Hardy but not since. The scripts presented in my first post above are working well for me now. Hardly an ideal solution though -- it's such a pity that a great OS like Ubuntu which is meant to be a serious competitor to the established ones, is brought down by silly issues like this -- having to drop to a command line and hack away at scripts to establish a VPN connection! There IS a PPTP PVN plugin, there IS a network manager, bugs HAVE been reported since Hardy, etc. It irritates me because it is bad for Ubuntu and will turn people away. The vast majority of users are not going to have the time or inclination to wade through my first post and hack away at config files in order to establish a VPN connection. They'll just ditch Ubuntu as a half-baked effort and return to other OS's which "just work". It's only the "techies" who have time and inclination and interest to play and hack to get stuff to work. The average user needs it to work. I've been following the problems with PPTP VPN since Intrepid. Nothing has changed it seems for Jaunty. At least a fairly simple work-around does exist, as I have explained above. I'm no expert on PPTP or VPN at all. I know there are different kinds like Cisco and OpenVPN, etc. and I don't really know the differences. All I know is that to get my PPTP VPN to work in Jaunty, I have to run those little scripts. In Hardy, I clicked on the Network Manager plugin, followed the wizard there and it worked. No problems. The file that is exported by that plugin is not readable by later versions in Intrepid and Jaunty. Bugs for this have been filed ages ago. Maybe in Karmic ... :-)

---

### Post by SabreWolfy on 2009-04-26
**Update:** I've spent the last few hours using my PPTP VPN connection in Jaunty, as described in the original post (#1 above). However, I was experiencing a very strange problem. When I attempted to paste a URL into the remote ssh terminal, only the first few characters would appear and then the connection would hang. The connection would also hang when I attempted to generate "large" amounts of traffic, such as when taking a long 'ls' or 'cat'ting a large file. Some searching led me [here]("http://www.snailbook.com/faq/mtu-mismatch.auto.html"), which reminded me that I needed to set the mru and mtu values (which were present in the exported settings file from Hardy). I don't know what values these should really have, but the following worked for me. Edit the vpn1 file mentioned earlier and add:

```
mru 1412
mtu 1412

```

Worked for me! :-)

---

### Post by virkang on 2009-04-28
Hi everyone,

I found a way to make it work in Jaunty (at least for me ...).
- When you configure the VPN connexion, go to the "advanced" settings"
- Uncheck "EAP" at the top
- check the "mppe" parameter
- Try to connect to your microsoft VPN server, i should work now

I hope this trick will help you out there ...

---

### Post by Major_Kong on 2009-04-28
> **virkang said:**
> Hi everyone,

I found a way to make it work in Jaunty (at least for me ...).
- When you configure the VPN connexion, go to the "advanced" settings"
- Uncheck "EAP" at the top
- check the "mppe" parameter
- Try to connect to your microsoft VPN server, i should work now

I hope this trick will help you out there ...

Doesn't work for me. I get the "secrets" error message. ](*,)

Any fresh ideas to make the network-manager work properly ?

---

### Post by SabreWolfy on 2009-04-28
It's broken in Intrepid and Jaunty AFAIK; hence my long post starting this thread, which describes the work-around I am using.

---

### Post by FrancisT on 2009-04-29
> **SabreWolfy said:**
> It's broken in Intrepid and Jaunty AFAIK; hence my long post starting this thread, which describes the work-around I am using.

PPTP is working for me in Jaunty with the network manager applet. You just have to disable EAP and enable MPPE. Beofre I disabled EAP i got a bunch of weird errors though

However it isn't perfect. I'm having issues with SAMBA possibly to do with split horizon stuff. Fortunately the only thing I really need to do is FTP, SSH and Rdesktop and all those work fine

---

### Post by carmadamus on 2009-04-30
Worked for me. Thanks for the tip.

---

### Post by dmaximos on 2009-04-30
So I'm one of those noob users who decided to give Ubuntu a try b/c I'm sick of Microsoft and the viruses that come with it. I've been researching all over the web about how to get VPN to work in Ubuntu. So far I am able to get it to work except all of my network traffic goes through my work vpn. I tried clicking on the "Use this connection for resources only for resources on its network" hoping that I can remote desktop to my computer and have all my local network traffic use my fios, but it doesn't work.

Am I understand that this is a bug  or is there some configuration issue that I'm not following. I can dual boot to XP, but I'd really like to use Ubuntu instead. Is there any documentation on this tool? TIA

---

### Post by SabreWolfy on 2009-05-01
@dmaximos:

Hi,

Welcome to Ubuntu! :-) Which version are you using? Setting up routing under Hardy was quite easy, but setting it up under Intrepid is not that difficult either.

I'm no expert in VPN. However, what I do know is that you need to know the range of IP addresses which must be routed through the VPN. In other words, you need to tell Ubuntu that whenever a request is made to contact an IP is the specified range, it must route that request through the VPN.

In Hardy this can be setup via the VPN plugin (on the last tab I think). In Jaunty, you need to follow the instructions in the second part of my first post.

If your corporate network uses addresses in the range, for example, of X.X.1.1 to X.X.255.255 then you would use the expression X.X.0.0/16 to specify all those addresses. If you use X.X.X.1 to X.X.X.255 then use X.X.X.0/8. You can see that the first one has more addresses in it than the second one, because the first one only has two X's and the second one has three X's.

All of this applies to my experience using PPTP VPN. There are other systems like Cisco VPN and OpenVPN, but I don't know anything about them or how similar they are to PPTP.

Good luck. I can also suggest searching on the 'net for tutorials or assistance with this. I'm sure you'll find something that will help you.

Cheers.

---

### Post by Major_Kong on 2009-05-01
> **Major_Kong said:**
> 

Any fresh ideas to make the network-manager work properly ?


A follow up:
By turning off the firewall i can connect to the vpn network, but i still can't use the connection...

EDIT: Forgot to turn MPPE encryption. It's working now.

---

### Post by dmarsh2 on 2009-05-01
What was mentioned before wasn't working for me. I've tried almost every combination of settings in the network applet, but based on some other posts I found one way that seems to force 128 bit MPPE (this was my problem - based on network logs it looks like the VPN server I was connecting to was canceling my connection because Ubuntu was trying to connect with the 128 OR 40 bit encryption). There's probably a config file for this, but if you run gconf-editor and go to system-networking-connections-(choose a number)-vpn and set "require_mppe" to no and "require_mppe-128" to yes, I was finally able to connect to my VPN.

---

### Post by calebbontrager on 2009-05-01
I just installed the 32 bit version of Ubuntu 9.04 and am also unable to connect to a pptp vpn server through network manager. I get the secrets error message referenced earlier: "The VPN Connection failed because there were no valid secrets". 

I had been running Ubuntu 8.10 x64 before installing 32bit 9.04. Under 32bit 8.10, pptp VPN literally worked fine out of the box; no hassle other than entering gateway, username, and password. I find it odd that pptp is now broken in 32 bit 9.04.

I have not yet tried the method recommended by SabreWolf. Trying that next.

---

### Post by zyrorl on 2009-05-01
This thread may help for all those with vpn issues

[http://ubuntuforums.org/showthread.php?t=964255](http://ubuntuforums.org/showthread.php?t=964255)

(note i havent had to use pptp since intrepid but it certainly fixed it then)

---

### Post by Major_Kong on 2009-05-02
For those of you with Firestarter installed this may be the origin of your problems:

> Firestarter 1.0 does not support VPN configurations without some tweaking. VPN capability in Firestarter is currently planned for version 1.1. 
[http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php)

---

### Post by krazyd on 2009-05-02
I connect to a PPTP VPN regularly, and I've found that the easiest, simplest way is to download kvpnc ( [http://home.gna.org/kvpnc/en/download.html](http://home.gna.org/kvpnc/en/download.html) ).

You need to get the latest deb from the link above (the intrepid one works fine with jaunty - I'm using it right now). Don't install the one from the repos because it's an older version and is a little buggy.

It has a simple wizard which should get you VPNing in no time :)

I also gave up on the nm-applet for VPN as I just couldn't get it to connect.

---

### Post by olmecnz on 2009-05-06
> **dmaximos said:**
> So I'm one of those noob users who decided to give Ubuntu a try b/c I'm sick of Microsoft and the viruses that come with it. I've been researching all over the web about how to get VPN to work in Ubuntu. So far I am able to get it to work except all of my network traffic goes through my work vpn. I tried clicking on the "Use this connection for resources only for resources on its network" hoping that I can remote desktop to my computer and have all my local network traffic use my fios, but it doesn't work.

Am I understand that this is a bug  or is there some configuration issue that I'm not following. I can dual boot to XP, but I'd really like to use Ubuntu instead. Is there any documentation on this tool? TIA

I am experiencing the same issue. I can connect and view VPN just fine but all my traffic goes over the VPN connection when.

I want normal web requests to go out over the normal gateway...

When I tick "Use this connection for resources only for resources on its network" in the routes section of the network manager VPN editor to stop me being able to view resources over the VPN (but I can browse the web)

I am connecting to a network that uses 10.3.X.X addresses

Thanks for advice on this.

---

### Post by philtrim on 2009-05-06
I had the error (no secrets) and kept trying, retrying, deleting the VPN, recreating the connection, very frustrating.

I finally gave up and decided to do a simple restart, then re-tried my VPN connection, boom, connected first time.

Although, I'm still working out browsing shares, and terminal services connectivity issues, though.

I love a good challenge!

Great Forum!

Jaunty version

---

### Post by area124 on 2009-05-18
This has worked for me in jaunty. I had my VPN for work set up and working,
but all traffic was going though the VPN. I used the following procedure.

I used the network manager in the upper right hand corner of my desktop.
Click on "VPN Connections", then "Configure VPN..."
In the Network Connections window, select your VPN Connection and then click
the "Edit" button. 
In the "Editing Your_VPN PPTP" window, click on the "IPv4 Settings" and then the "Routes..." button.
In the "Editing IPv4 routes...." window, check the box for "Use this 
connection only for resources on its network".
Now click the "Add" button. Note, this kind of works a little funny. as I 
added the Address/Netmask/Gateway information I had to click each box as it
seemed to loose the curser position. In my case I work address were in the
XXX.YYY.0.0 range so I used a netmask of 255.255.0.0. I set the Gateway to
my local router which is 192.168.1.1 (pretty standard). I also used the
value "1" for the Metric. I had to click the "Add" button. This was the
only way I could get it to take.
 
Here was another little tip. While attempting to use this GUI I ended up
with several empty routes by accident. The GUI would not let me click on
"OK" until I deleted all the empty routes. Just try clicking below your
last route. If you are able to make a selection, you have an empty route.
Just click the "Delete" button and you should be good.
Click on "OK", then "Apply", then "Close". Now test your VPN and see if 
it works any better.

I use "http://www.speakeasy.net/speedtest/" to test my bandwidth before
and after. My connection though my work VPN is really slow. Using the
above web site very clearly indicated that all my non-work traffic was no
longer going over my work VPN.

I hope that this is helpful for some of you.
Good luck!:)

---

### Post by jbolivar on 2009-05-31
> **area124 said:**
> This has worked for me in jaunty. I had my VPN for work set up and working,
but all traffic was going though the VPN. I used the following procedure.

I used the network manager in the upper right hand corner of my desktop.
Click on "VPN Connections", then "Configure VPN..."
In the Network Connections window, select your VPN Connection and then click
the "Edit" button. 
In the "Editing Your_VPN PPTP" window, click on the "IPv4 Settings" and then the "Routes..." button.
In the "Editing IPv4 routes...." window, check the box for "Use this 
connection only for resources on its network".
Now click the "Add" button. Note, this kind of works a little funny. as I 
added the Address/Netmask/Gateway information I had to click each box as it
seemed to loose the curser position. In my case I work address were in the
XXX.YYY.0.0 range so I used a netmask of 255.255.0.0. I set the Gateway to
my local router which is 192.168.1.1 (pretty standard). I also used the
value "1" for the Metric. I had to click the "Add" button. This was the
only way I could get it to take.
 
Here was another little tip. While attempting to use this GUI I ended up
with several empty routes by accident. The GUI would not let me click on
"OK" until I deleted all the empty routes. Just try clicking below your
last route. If you are able to make a selection, you have an empty route.
Just click the "Delete" button and you should be good.
Click on "OK", then "Apply", then "Close". Now test your VPN and see if 
it works any better.

I use "http://www.speakeasy.net/speedtest/" to test my bandwidth before
and after. My connection though my work VPN is really slow. Using the
above web site very clearly indicated that all my non-work traffic was no
longer going over my work VPN.

I hope that this is helpful for some of you.
Good luck!:)

Thanks! This worked great for me :)

---

### Post by pearle on 2009-06-08
I followed the steps suggested by area124 and it works for about 10 seconds and then I start receiving 100% packet loss over the vpn and to the internet. Anyone have any ideas?

'Ignore automatically obtained routes' is unchecked.
'Use this connection only for resources on its network' is checked.

In the routes listing I have the following:

address / netmask / gateway  /metric
10.10.0.0 / 255.255.0.0 / 192.168.1.1 / 1

Again, this works perfectly for about 10 seconds but then the packet loss kicks in and nothing works.

Any suggestions?

---

### Post by Lucky. on 2009-06-10
Hey thanks for the post.  I'm using Jaunty Desktop, and this information combined with the tutorials on the PPTP client website got me up and going.

Once again for the record, I'm on Jaunty, and connecting to a Windows 2003 Server VPN.

After reading through the tutorials of configuring things manually, I got a better feel for the settings I needed in the GUI.  I tried them out, and...bam, they worked!  Network manager with the PPTP client worked great.  Tried it a million times before to no avail.  But now it works good, with no need to manually configure stuff.  Weird.

My notes are as follows:

1.  Add a PPTP connection with network manager.

2.  When it comes to typing your username, simply type your username.  Don't worry about DOMAIN\USERNAME.  Just type the username.

3.  For the domain name, type in the domain name.  No slashes or anything crazy.

4.  Click Advanced.  Leave all the authentication methods checked, but uncheck EAP.

5.  Check “Use Point-to-Point encryption”.

6.  Connect!

7.  The DNS works fine, but you need to use the fully qualified domain name to get to stuff on the VPN side.  For example to remote desktop into my remote computer in the VPN LAN, in Windows XP I could just connect to "mycomputer".  In Ubuntu, it's "mycomputer.mydomain.anypossibleotherstuff.blah"

It just seems strange that all of this suddenly works now...A few things on my mind about this:

1.  Following your instructions, I tweaked around a number of files in /etc/ppp while doing things manually, so perhaps these led to network manager "appearing" to be working now (since it's fixed under the hood?).  I tried putting everything back the way it was, but who knows...maybe I didn't.

2.  I seemed to notice issues while logged in under my normal account.  I'd configure a connection, and it wouldn't work.  Then I'd change stuff, and it still wouldn't work.  Then I'd delete the connection altogether, but it would still appear on the drop down list (Not the configuration list, but the quick-connect list).  Sometimes new connections wouldn't show up on the drop-down list.  Made me wonder whether things were getting saved correctly.  I've noticed some other Jaunty desktop problems that were a result of not being logged in as root, so I logged in as root to ensure my configuration changes were being saved.  This seemed to work.  Of course I couldn't duplicate the problem after the fact, so maybe root has nothing to do with it, and I finally just got my settings correct.

I'm going to reformat tomorrow and try these settings out with a fresh install of Jaunty.  I'll report back and let you know if it all just "works" with pure GUI.

---

### Post by Lucky. on 2009-06-13
Sorry it took a few days longer, but indeed it does work purely with network manager and no extra work.  The settings I listed get the job done for a Windows 2003 Server VPN.

Yay!

---

### Post by cmon on 2009-06-27
> **virkang said:**
> Hi everyone,

I found a way to make it work in Jaunty (at least for me ...).
- When you configure the VPN connexion, go to the "advanced" settings"
- Uncheck "EAP" at the top
- check the "mppe" parameter
- Try to connect to your microsoft VPN server, i should work now

I hope this trick will help you out there ...

Thank you so much for this tip! I had almost lost hope of getting my vpn connection to work again

---

### Post by Wtwine on 2009-06-29
When I go to VPN connections >Configure VPN and select the VPN connection to edit in network manager applet in Jaunty, I don't see the "Advanced settings" option everyone keeps mentioning in order to change EAP, MMPE settings etc.  

WHAT AM I MISSING HERE?

---

### Post by Wtwine on 2009-07-08
Aaaaah...following on from previous message, I was adding a new VPN connection using the "Cisco compatible" option, not PPT. Duh!

---

### Post by Praill on 2009-07-15
> **virkang said:**
> Hi everyone,

I found a way to make it work in Jaunty (at least for me ...).
- When you configure the VPN connexion, go to the "advanced" settings"
- Uncheck "EAP" at the top
- check the "mppe" parameter
- Try to connect to your microsoft VPN server, i should work now

I hope this trick will help you out there ...

Thanks so much this did the trick. Also for me if anyone else is ](*,) like I was: You need to make sure under the VPN tab that 'Available to all users' is NOT checked. This made weird errors for me that removed all authentication information and wouldnt connect.

I also have to agree with the above poster that stated this was just sad. A simple pptp VPN connection should NOT be hard to configure. I know pptp is an MS thing but it's still pretty common.

---

### Post by zivley on 2009-08-12
> **SabreWolfy said:**
> This worked for me. Use at your own risk. YMMV. **[COLOR="Red"]Edit: See post #4 below for an important update to this post ...[/COLOR]**

I've bleated previously here and on Launchpad about how PPTP VPN worked perfectly under Hardy and was broken under Intrepid and Jaunty. For me, this was a "deal-breaker" because I need PPTP VPN access. I have not upgraded my desktop Hardy machine for this reason. I did upgrade my laptop to Intrepid and now to Jaunty and got around the problem by using PPTP VPN in a Xubuntu Hardy VirtualBox.

I've spent the evening looking at this again and I've managed to get PPTP VPN working on my Jaunty laptop. I'm not a PPTP or VPN expert by any means.

I used [this]("http://kryptoz.wordpress.com/2007/08/07/linux-pptp-vpn-client-configuration/") post as starting point, so thanks to kryptoz. The problem as I can see it is that Network Manager 0.7 (Intrepid and Jaunty) and the associated PPTP plugin are broken. Under Hardy (Network Manager 0.6.6) everything works. There are many posts detailing the myriad problems with Network Manager 0.7. However, using the Network Manager applet is simply a front-end to calling PPTP and PPPD which actually make the connection (I think).

My solution does not involve the Network Manager applet at all. The connection is established by calling PPPD. The pptp-linux and ppp (for pppd) package must be installed and the pptpd package as well (I think).

1. Add the following to /etc/ppp/chap-secrets:

```
Username   PPTP   Password   *
```

2. Create /etc/ppp/peers/vpn1. The 'peers' folder may be owned by group 'dip' so get around that by adding yourself to the group (I have no idea if this is a good solution, but it worked). Add the following to the vpn1 file:

```
pty "pptp remote.gateway.address.here  --nolaunchpppd"
name Username
remotename PPTP
require-mppe-128
file /etc/ppp/options.pptp
ipparam vpn1

```

3. Edit the options.pptp file as required. I commented out the 'refuse-chap' and 'refuse-mschap-v2' lines.

4. Establish the VPN connection with:

```
sudo pppd call vpn1
```

or

```
sudo pon vpn1
```

5. Drop the connection when you're done with:

```
sudo poff vpn1
```

That establishes a VPN connection but I could not get any traffic through it. Therefore, create '/etc/ppp/ip-up.d/route-traffic' as follows. I don't know why the file needs to have that name or be located in that folder, because it does not appear to be executed automatically. Thanks to [this]("http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html") site for this information:

```

#!/bin/bash
NET="10.0.0.0/8"
IFACE="ppp0"
route add -net ${NET} dev ${IFACE}

```

Make the file executable.

Replace the "10.0...." address with the range of addresses you need to access on your remote machine. For me, this was the same range as that which I originally included when setting the VPN up in Hardy. It may look like "10.2.0.0/16" for example. The values don't have to be in the "10" range (mine were not).

So, to get the VPN up in Jaunty, I did the following (in /etc/ppp/ip-up.d):

```

sudo pon vpn1
sudo ./route-traffic

```

**[COLOR="Red"]Edit: See post #4 below for an important update to this post ...[/COLOR]**

Thanks a lot to sabrewolfy for this nice solution, I've got it working fine ONLY after I used this method, all the other methods I've found around didn't get me connected to my MS VPN until I tried this one!

I allowed myself to improve it a little bit adding some more custom stuff for it to be easier to work, always following the example given on the original howto.

For a person like me, that has a lot of routings to be set to the VPN connection it can be a little tedious to do NET1, NET2, NET3 .... NET20!
and then a command for each one, so I used an array where all I need is to put every net I want to route, and to change it is as simple as adding or removing a line from the array, always keeping the same format.
So here's the routing script
This is the routing script I've wrote
Create '/etc/ppp/ip-up.d/route-traffic'
```
gksu gedit /etc/ppp/ip-up.d/route-traffic
```
Paste this code and save the file
```

#!/bin/bash
IFACE="ppp0"
NETWORKS=(
"10.1.0.0/24"
"10.2.0.0/24"
"10.3.0.0/24"
"192.168.123.0/24"
)

for NET in "${NETWORKS[@]}"
do
  route add -net $NET dev $IFACE
done

exit 0

```
Make it executable
```
sudo chmod +x /etc/ppp/ip-up.d/route-traffic
```

I've also created a "on/off toggle" script that will connect to the VPN if is disconnected and disconnect if connected.
Create the file '/usr/local/bin/vpn1'
```
gksu gedit /usr/local/bin/vpn1
```
Paste the following code and save the file
```

#!/bin/bash

VPN=vpn1

if [ ! "$(pidof pppd)" ]
then
  sudo pon $VPN
  zenity --info --text="Connected to $VPN" --no-wrap
else
  sudo poff $VPN
  zenity --info --text="Disconnected from $VPN" --no-wrap
fi

```
Make it executable
```
sudo chmod +x /usr/local/bin/vpn1
```
Now you can create a launcher on desktop if you like, right click on desktop then "Create Launcher"
Fill the fields as shown here:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124597&d=1250101949[/IMG]
Chose any icon you want and save it.
Now you'll be able to double click on the desktop icon to connect/disconnect from the VPN
Hope this helps
Ziv

---

### Post by SabreWolfy on 2009-08-12
> **zivley said:**
> 
<snip>


@zivley: I'm glad it worked you and thanks for the improvements, especially the last section! :-)

---

### Post by dash86no on 2009-08-24
> **Lucky. said:**
> Hey thanks for the post.  I'm using Jaunty Desktop, and this information combined with the tutorials on the PPTP client website got me up and going.

Once again for the record, I'm on Jaunty, and connecting to a Windows 2003 Server VPN.

After reading through the tutorials of configuring things manually, I got a better feel for the settings I needed in the GUI.  I tried them out, and...bam, they worked!  Network manager with the PPTP client worked great.  Tried it a million times before to no avail.  But now it works good, with no need to manually configure stuff.  Weird.

My notes are as follows:

1.  Add a PPTP connection with network manager.

2.  When it comes to typing your username, simply type your username.  Don't worry about DOMAIN\USERNAME.  Just type the username.

3.  For the domain name, type in the domain name.  No slashes or anything crazy.

4.  Click Advanced.  Leave all the authentication methods checked, but uncheck EAP.

5.  Check “Use Point-to-Point encryption”.

6.  Connect!

7.  The DNS works fine, but you need to use the fully qualified domain name to get to stuff on the VPN side.  For example to remote desktop into my remote computer in the VPN LAN, in Windows XP I could just connect to "mycomputer".  In Ubuntu, it's "mycomputer.mydomain.anypossibleotherstuff.blah"

It just seems strange that all of this suddenly works now...A few things on my mind about this:

1.  Following your instructions, I tweaked around a number of files in /etc/ppp while doing things manually, so perhaps these led to network manager "appearing" to be working now (since it's fixed under the hood?).  I tried putting everything back the way it was, but who knows...maybe I didn't.

2.  I seemed to notice issues while logged in under my normal account.  I'd configure a connection, and it wouldn't work.  Then I'd change stuff, and it still wouldn't work.  Then I'd delete the connection altogether, but it would still appear on the drop down list (Not the configuration list, but the quick-connect list).  Sometimes new connections wouldn't show up on the drop-down list.  Made me wonder whether things were getting saved correctly.  I've noticed some other Jaunty desktop problems that were a result of not being logged in as root, so I logged in as root to ensure my configuration changes were being saved.  This seemed to work.  Of course I couldn't duplicate the problem after the fact, so maybe root has nothing to do with it, and I finally just got my settings correct.

I'm going to reformat tomorrow and try these settings out with a fresh install of Jaunty.  I'll report back and let you know if it all just "works" with pure GUI.

Cheers mate, followed the steps above and got VPN working through the GUI with no tweaking.

---

### Post by idlehands on 2010-01-22
karmic:

tried gui version fails.

Tested out cli, but before mucking with routes, i tried to bring up the vpn, and i didn't even get an ip from the vpn, is that normal? I gave up at that point. 

Hints? This is killing me. I've also puttered with my mac to try and get that to connect, since i really need to get to the vpn for a project.

---

### Post by idlehands on 2010-01-24
Ok, so when I config the network manager(latest from truck to fix the issue where it doesn't preserve settings) on karmic with the following settings

gateway:set
username/password set and keep
no nt domain

-adv-settings:
use pptp/allow stateful
that forces only mschap/chapv2

nothing else set

I get the following log:
```

VPN connection 'Cloud' (IP Config Get) reply received.
Jan 24 12:40:01 johannt61p NetworkManager: <info>  VPN Gateway: --ip removed-
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Tunnel Device: ppp0
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Internal IP4 Address: 172.16.8.52
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Internal IP4 Prefix: 32
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Internal IP4 Point-to-Point Address: 172.16.8.2
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Maximum Segment Size (MSS): 0
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Internal IP4 DNS: 172.16.0.2
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Internal IP4 DNS: 172.16.0.3
Jan 24 12:40:01 johannt61p NetworkManager: <info>  DNS Domain: '(none)'
Jan 24 12:40:01 johannt61p NetworkManager: <info>  Login Banner:
Jan 24 12:40:01 johannt61p NetworkManager: <info>  -----------------------------------------
Jan 24 12:40:01 johannt61p NetworkManager: <info>  (null)
Jan 24 12:40:01 johannt61p NetworkManager: <info>  -----------------------------------------
Jan 24 12:40:02 johannt61p NetworkManager: <info>  VPN connection 'Cloud' (IP Config Get) complete.
Jan 24 12:40:02 johannt61p NetworkManager: <info>  Policy set 'Cloud' (ppp0) as default for routing and DNS.
Jan 24 12:40:02 johannt61p NetworkManager: <info>  VPN plugin state changed: 4
Jan 24 12:40:02 johannt61p nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
```

I dug up this thread:
[http://ubuntuforums.org/showthread.php?t=979001](http://ubuntuforums.org/showthread.php?t=979001) and tried adding a executable script to /etc/ppp/ip-up.d/
with modified mtu settings which made no difference

When I follow the script version of this, I get the following log:
```

CPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Jan 24 12:48:35 johannt61p NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Jan 24 12:49:07 johannt61p NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)


```

and this in messages
```

Connect: ppp0 <--> /dev/pts/4
Jan 23 08:10:02 johannt61p pppd[15729]: LCP: timeout sending Config-Requests
Jan 23 08:10:02 johannt61p pppd[15729]: Connection terminated.

```

I didn't configured the routes via cli as when i tested and didn't see ppp0 getting a 172.*.*.* ip, i assumed it wasn't making the connection. 

Also this file  /etc/ppp/chap-secrets, i assume the "Password" there is the password to authenticate to the pptp? not the word "Password"?


Thanks!

---

### Post by rootk1t on 2010-03-04
I've got a problem with PPTP VPN with multiple user login: some users are receiving the same IP and they are disconnected :(

Has someone the same problem?

I have in pptpd.conf

localip 10.1.1.45
remoteip 10.1.1.180,10.1.1.181,10.1.1.182,10.1.1.183,10.1.1.184,10.1.1.185

I've tried with the remote ip by writing a range, but still not working well,some users are receiving the same IP.

---

### Post by rootk1t on 2010-03-04
And, another problem I have: sometimes, from time to time, interface ppp0 is missing when I ifconfig the interfaces!

---


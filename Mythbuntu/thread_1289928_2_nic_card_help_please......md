---
title: "2 nic card help please....."
date: 2009-10-12
forum: Mythbuntu
---

### Post by ConXtionS on 2009-10-12
Hello

I dont know the correct way to say this sooooo please bare with me.

My Myth computer has 2 nic cards (yes that is how many I wanted)

I want to SPLIT my home network at the nic box ...

so the NIC that is on the mother board I want connected to my current home next work with an ip address like 192.168.2.222

the other nic I want to be kind of like a NEW ACCESS POINT

with a different set of ip addresses....

I want to put an access point on the second nic and make like a little video and music server...

How do I config the two cards please????

thanks

Jim

---

### Post by zarthon on 2009-10-13
Hi Jim,

Where are you at in getting all this setup?
Do you have MythTV up and running and recording TV on your comptuer?
Did you configure your home LAN yourself? 
Do you know how to configure your wireless access point(s) and router by accessing the administration web pages?

It is not hard to set up the NIC cards. They will be called eth0 and eth1. Start by testing each Ethernet interface. Go to system->preferences=>networking and see if you have two wired interfaces listed. To see if they both work correctly try accessing your current network through one and then the other by moving the wire over to the other port.
After this disconnect from your current lan (and the internet) to avoid any IP address conflicts. Attach your wireless Access Point to it's intended port. Using your web browser go into the Access Point administration pages for DHCP and set the address ranges you want for your second LAN. You will have to also change the administration IP for your Acess point to an address within the new address rage. After you make this change you will likely have to correct the URL and log backin to the access point. Now go into DHCP and assign a static address for your comptuer on the second lan.

Will computers connected to the new access point on the second NIC need to have access to the Internet and current LAN?  If so you will need to configure either "bridging" or network address translation (NAT) to pass data from one lan to another. 

Do you care if others on your existing LAN can browse your Myth server?
If so then configure myth to only listen on eth1 interface.

I accept that you want 2 NIC cards on the comptuer.... for no other reason its fun.  I am having some trouble understanding why you want to set it up that way. There are a few single network configurations even if you want to secure your Myth server from access from some of the computers on your LAN. You can limit access by MAC address and can log access to the IP ports that MythTV back end uses.

Almost all routers sold today have an integrated switch rather than hub architecture so lets say you have computers A, B,C and D on a wired network.If computer A transfers an enormous file to comptuer B this will have no impact on computer C accessing the Internet or transferring a large file to computer D. The "SPLITER"  comptuer however will create a bottleneck for any computer attaching to the Internet through it. 

There are some clear advantages to having the 2 NICs namely if your eth1 becomes congested from serving up TV, your Internet access for the MythTV box will not be affected. 
 
Good luck!
John

---

### Post by ConXtionS on 2009-10-13
Hello Mr John,

Im going to try to answer your questions as best I know how... so it could take some explaining that is really not revelant to the project.

"Where are you at in getting all this setup?"

I have 9.10 desktop and 9.10 myth tv running.  I have not put any server componets on the box yet as I am still not sure what I am going to need.   I figured one step at a time.   Both Desktop and MYTHTV seem to work fine.  I have the news feeds and the weather going... I can record tv shows.  I have not tried the music, pictures or dvd stuff yet.


"Do you have MythTV up and running and recording TV on your comptuer?"  Yes sir, I believe it is all running, but Myth can do so MUCH that I am not sure it is all perfect as of yet.

"Did you configure your home LAN yourself?"  Yes sir... its not much Comcast comes in, hits a lil router, one of the eithernet ports runs up stairs in to  eth1 of my myth box which I have assigned the ip of 192.168.2.99.   ETH0 has not been assigned as yet.

Do you know how to configure your wireless access point(s) and router by accessing the administration web pages?  Yes sir I do.

******** Background Information *********

The wife and I spend a good deal of the summer camping .... Currently the camp ground has no Internet service (I am trying to get a wireless provider to do a survey there now) and the nice spot the wife and I have near the pond gets TERRIBLE TV reception.  While my wife is an attractive woman after 26 years of marriage you can only look at her so long and the one station of tv that comes in during the day has the wonders of Jerry Springer and that bunch on it.   So I am left staring at the pond or cleaning up dog poop on most days.

This year I have been recording tv shows lori and I like using windows media center, burning 4 or 5 of them to DVD when ever we come home to visit.  Needless to say this is a wasteful but better than nothing process.

The campground has one tv antenna on the OTHER SIDE of the camp ground from me.  The owners say I can put up an antenna there and get all of the chicago, indianapolis, lafayette stations.  So, I have a place to CAPTURE the tv.

Of course when I told the owners what I wanted to do they added what they would like.

So, long story short my wish list is

A myth box that one NIC will hook to the new internet coming to the camp ground that I will give the owners complete access too.  I want the box to record live tv from the antenna and store it on the hard drive.  Then on the second nic I want to set up a wireless network (tranzeo) access point with a walled garden (captive portal) so I can control LIL JOHNNYS access to the net, but allow him to view my new "CAMPERTV".

I want anyone with a lap top, ipod touch, to be able to access the network, and watch what I have recorded ....  However the internet side has to be closely guarded as the wireless internet service provider has some strict limits on downloads and such.  So I cant let lil johnny just run amok ....

So, I need a myth box, media server, and hot spot controller all in one?????

thanks for the Help Mr John

Jim

---

### Post by desktopj on 2009-10-15
What is the model of the router that is connecting to the internet? If you can access it, may be easier to restrict internet connections via it's administration menu. Usually you go to 192.168.2.1 or 192.168.1.254 with your browser. 

Easier than creating a dual homed system.

---

### Post by zarthon on 2009-10-16
Pondered some on all of this. 

How large is the campsite? 
I suggest you break the project into separate sub-projects and then see where you can overlap the setup between projects.

Setting up a wireless community network that supports local video on demand to a heterogeneous set of clients is not trivial and will require some planning. I would concern myself about this LAST, and price out all the hardware involved. You will want to read a book on creating wireless public networks and join discussions directly related to this.
I have set up home and corporate networks wired and wireless.

If there are serious limitations on your Internet service then I'd keep Internet access private. If you install both nics the default is that they are separate networks so your second nic will not have any Internet access through your box. Devices that join will be able to see eachother and your box and that is it.

Focus on your own access first. Is there a line of site between the antenna where the myth back-end is and your campsite or is there a bunch of oaks,maples, and pines in the way? Even worse are there metal structures?  How far is it? There are tables to estimate the kind of signal you will get. You can also consult information about the access point you are considering. You may want to look into building high gain directional antennas or install an intermediate wireless bridge. Research your own access throughly and see what is evolved with insuring you will have the bandwidth to access your MythTV box.

For a start to understand what is involved in creating community access to the Internet I found a how to(link below). Another approach may be to search for a "virtual appliance" that will provide this functionality. 
[http://www.andybev.com/index.php/Setting_up_a_captive_portal_from_scratch_using_Debian#Configure_Squid](http://www.andybev.com/index.php/Setting_up_a_captive_portal_from_scratch_using_Debian#Configure_Squid)

From what you have described using bridging between interfaces will not do since you need control. Search and read about network address translation (nat) and ip masquerading using iptables.

I would make an administration connection for yourself by putting an access point on the Internet side outside of your firewall. This will allow you to hack at both sides and manage the system from your place. It will give you a connection to the outside if your captured portal is not working. You can join in on the other side when you need to test. Also why Share? This "admin" connection could be a good door to your box avoiding congestion when  others start viewing and accessing the Internet. It will get slow and even unable at some threshold and you will be at a disadvantage on the other side of the park! 

For your own entertainment at home or anywhere you have unlimited downloads (and for saving disk space) checked out hulu.com and tvguide.com !  There is terrabytes and terrabytes of video online now ! Unfortunately they have developed effective tech to insert commercials. Yuck !  Pbs.org is another option.

---

### Post by zarthon on 2009-11-12
I was in staples last week and noticed new N+ routers that operate on both wlan frequency ranges. I have not used or tested this equipment but these routers claim to have a much greater range, and a broader bandwidth and may make your project easy.  You would need an N+ adapter or second N+ access point acting as a bridge to a wired network at your camper.
Prices were higher than the standard G access points but it may solve the need to run Ethernet cables or have an enclosure and power at a few places on the campground.
Along similar lines I noticed newer blueray players among other devices have built in access to TV services and local media servers.

---

### Post by ian dobson on 2009-11-12
Hi,

If you want both cards to have a static address, the easiest way would be to set them up in /etc/network/interface.

Here's my file:-

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth3
iface eth3 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.254

auto eth3:0
iface eth3:0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255

```

Note my ethernet interfaces are called eth3 and eth3:0, you'll need to use ifconfig to findout what linux calls your network cards.

Regards
Ian Dobson

---


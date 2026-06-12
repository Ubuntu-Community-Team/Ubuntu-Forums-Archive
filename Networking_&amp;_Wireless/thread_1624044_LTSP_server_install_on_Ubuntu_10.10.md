---
title: "LTSP server install on Ubuntu 10.10"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by riptool on 2010-11-17
Im new here, been messing with Ubuntu about 2 yrs but want to explain my problems over the last few days with LTSP and how I got it working to try and help others. 

I installed in Virtualbox many times and the clients would not connect. The config of the dhcpd.conf was the problem.
Now,
Everywhere I kept reading it said I had to turn off my hardware routers dhcp. Thats wrong, I have it working with it on and with one network card. Heres the nuts and bolts.
Dlink 4100 hardware router assigning address block 192.168.2.200-250 to pcs on the lan. Router is set to reserve and IP for the ltps server nic so it gets the same IP assigned every time from the hardware router. No need to force linux to an ip when it can be set in the router.

Then installed LTSP from alt-cd.
Once done, dhcp wont run because it conflicts with the hardware dhcp. Found out by trying to restart it and it said stop - Fail when it tried to stop it. 
sudo /etc/init.d/dhcp3-server restart


So edit /etc/ltsp/dhcpd.conf.
sudo gedit /etc/ltsp/dhcpd.conf

Mine attached below: 
The subnet, as long as the 1st three numbers match the rest of lan setup it will work.(192.168.2.0), rest of my lan is 192.168.2.x.
Now notice the range is a different block than the hardware dhcp server uses. So all thin clients that connect will be assigned something 192.168.2.100-150 and all hardware connected pcs will be assigned 192.168.2.200-250 from the hardware router. So no conflicts. Then for the domain name server, set it to the hardware router ip. My hardware router is 192.168.2.2. Set option router to the same as hardware router of 192.168.2.2 Nothing in my dhcpd.conf file is pointing to the ltsp dhcp server. 
Nothing else had to be edited in the dhcpd.conf

Next hurdle I had, after any change of the dhcpd.conf, ip's might have changed and  you have to reconfig the ssh and the image.
run these 2 commands.
sudo ltsp-update-sshkeys
then
sudo ltsp-upadte-image
then
sudo /etc/init.d/dhcp3-server restart

Then thin clients/lan boot pcs all can connect after that.

I have since installed again at work in virtual box, booted from another vbox client and booted from a separate lan pc. Then installed again at home on AMD 3200 Athlon, 1 gig mem. Booted from my main pc PhenomX4, no problems. Pc's must have lan boot available in the bios or net boot available on the network card(most consumer add on cards do not). But most motherboard lan connection do.
Hope this helps
Good luck, have fun, Im an Ubuntu convert now. Windows is only good for games and kiddie play and infections now. lol :lolflag:


_______________________________________
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.100 192.168.2.150;
    option domain-name "example.com";
    option domain-name-servers 192.168.2.2;
    option broadcast-address 192.168.2.255;
    option routers 192.168.2.2;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
_______________________________

summry notes
Dlink router is 192.168.2.2 and assigns 192.168.2.200-250 to lan pc's
LTSP server's nic gets assigned 192.168.2.215 from the Dlink router every time.
LTSP server's dhcp then assigns 192.168.2.100-150 to clients and uses the Dlink router(192.168.2.2) for dns queries.


Hope it helps some.

EDIT. Just noticed after a reboot dhcp3-server doesnt autostart for me. I have to login to the LTSP machine and run 
sudo /etc/init.d/dhcp3-server restart
it says stopping server FAIL
Start server OK
THen all lan booting is back to working.
Not sure why it doesnt start automatically.

---

### Post by riptool on 2010-11-18
Some more testing on speed.

Initial machine is a AMD Athlon3200, 1 gig ram, nvidia 6600gtx agp, 10/100 on board lan.
Browsing the net is fine, used about 10Mib on the lan speed and very little processor. Then went to youtube and played a video. Not even an HD rez one and it maxed out the lan at 80Mib and 100% processor usage and was choppy as hell. 
So I added a gigbit net card, played same video, lan usage was about 125Mib and 100% processor. Still choppy but was better.

Then installed LTSP on better machine. AMDPhenonx2-3000, 4 gig ram, ati video, gigalan.
Start same video on your tube, very smooth and using about 140Mib lan speed, 70% usage on both processors. Opened a second youtube video in new window, lan went to 270Mib with 85% or so used of processors. Was still silky smooth. 

Part of the improvement could be the lan is not a bottle neck along with the cpu be maxed out but I think part is also the ATI video on the server and ATI video on the lan booted client. Where as the 1st setup was an nvidia server machine with an ATI client. Of which the nvidia driver, when installed, freaked out the ATI cleint. Words, menus, everything was reversed left/right and up/down. So the default xorg had to be run on server and client with pretty much no video acceleration at all. Not that ATI is batter but running a client with the same vid specs as the server got rid of a lot of hassle in having to install a video driver just in one clients config, which from what Ive read, can be a pain. 

So I dont see a 100Mib connection being capable of supporting 10 users. If just one goes to youtube or another video site, its going to slow down everyone.

Maybe its my resolution, Most thin clients, old pc's I guess would be running at 800x600 or less. I was running my client machine at 1680x1050 so I assume that can contribute a LOT to the bandwidth use.

---

### Post by Rakeshvijayan on 2011-07-05
will you share whole configuration here

---

### Post by riptool on 2011-07-05
Not sure what you need that wasnt stated above.

Main problem with LTSP is getting the dhcpd.conf file right.

Mine again:

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.100 192.168.2.150;
    option domain-name "example.com";
    option domain-name-servers 192.168.2.2;
    option broadcast-address 192.168.2.255;
    option routers 192.168.2.2;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

Explain each:
-subnet, 1st 3 numbers should match your local network numbers, 4th is zero in most cases.
-Range, the range of addresses you want the LTSP serve to assign ti its LTSP clients when they sign in. Again, 1st 3 same as lan, 4th should be start and end points. like 100-150.
-Option doamin name , I never changed
-optional domain name servers, set to your router ip or an actual DNS server. Tell LSTP where to look for DNS lookups.
-Optional broadcast address, should always be the same 1st 3 numbers as the lan, then 255.
-optinal routers, can be set to another router on the lan, but just make it same as your router.
-All else is the default.

---


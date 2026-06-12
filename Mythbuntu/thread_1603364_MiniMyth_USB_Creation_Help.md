---
title: "MiniMyth USB Creation Help"
date: 2010-10-22
forum: Mythbuntu
---

### Post by hundred1906 on 2010-10-22
Can anyone help me in creating a minimyth local boot USB. I get the feeling it should be straightforward but the documentation around is pretty stiff to wade through.

Just here <http://www.mythpvr.com/mythtv/distribution/minimyth/compact-flash-install.html> the guidance looks relatively straight forward but the links are out of date and instructions include lines like "Create a directory name "conf/default"" which as far as I can see is not a legal file name.

---

### Post by ian dobson on 2010-10-22
Hi,

Hmmmm, my frontend boots from a 8Gb CF card in a CF->SATA adapter and I just installed mythbuntu as if it's from a normal harddisk. Maybe if the installer sees the usb stick as a normal drive (which I think it does) then just try a normal install.

Regards
Ian Dobson

---

### Post by lank23 on 2010-10-22
If you want a small frontend, you should do a boot on lan setup of either mythbuntu or minimyth.  But note that minimyth is mainly for epia boards.

I have setup both of the above, but on the mythbuntu setup the mythtv is compiled for 686 processors, but my epia-cl processor does not have the CMOV instruction so I had to re-compile mythtv to get it working. 

Check out these links.

[http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless]("http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless")

[http://www.minimyth.org/document-boot.html]("http://www.minimyth.org/document-boot.html")

lank23

---

### Post by hundred1906 on 2010-11-19
Thanks for the replies. So far I gave up on Minimyth and as a temporary solution loaded mythbuntu frontend install onto an unused IDE disk connected up through USB. This works OK but has lots of cables and some noise.

So I am attracted to a network boot option but the instructions look substantial and I get the feel there are some fairly complex pre-assumptions especially when it comes to setting up DHCP and other stuff.

My revised question therefore is has anyone used the instructions here <http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless> on 10.10 and do they work right through. It is just that I am reluctant to end up with my desktop/back-end machine tied into an impenetrable knot.

---

### Post by lank23 on 2010-11-19
> **hundred1906 said:**
> 
My revised question therefore is has anyone used the instructions here <http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless> on 10.10 and do they work right through. It is just that I am reluctant to end up with my desktop/back-end machine tied into an impenetrable knot.

These instructions work for 10.04 "have my epia-cl booting minimyth or mythbuntu" and should work for 10.10.

What is your hardware for your frontend?

---

### Post by hundred1906 on 2010-11-20
Hardware for the front-end is a HP Thin-Client t5725. Seems to run MythTV well as a front-end although at present it is from a local drive.

I am using the in-built graphics engine which is giving all the video quality I need so no need for extra an extra card. If I was going to add anything it would probably be a sound card.

Meanwhile I need to get on with converting to a network boot arrangement so any help with things I could trip up over would be good. Thanks

---

### Post by lank23 on 2010-11-20
> **hundred1906 said:**
> Hardware for the front-end is a HP Thin-Client t5725. Seems to run MythTV well as a front-end although at present it is from a local drive.

I am using the in-built graphics engine which is giving all the video quality I need so no need for extra an extra card. If I was going to add anything it would probably be a sound card.

Meanwhile I need to get on with converting to a network boot arrangement so any help with things I could trip up over would be good. Thanks

Ok.

---

### Post by hundred1906 on 2010-11-21
As far as I can tell from other sites I need to disable the DHCP option in my router. This means I lose wireless connectivity for other devices like the iphone. Is this correct or do I need to add more options into /etc/network?

---

### Post by lank23 on 2010-11-21
> **hundred1906 said:**
> As far as I can tell from other sites I need to disable the DHCP option in my router. This means I lose wireless connectivity for other devices like the iphone. Is this correct or do I need to add more options into /etc/network?

Yes you have to turn off the routers DHCP, and either use static IP address for all your machines, phones, etc... or when you install the DHCP server on your backend you allow it assign the IP's, this is the way my network is setup but with a setting close to static DHCP by making use of the "host" option in the "/etc/ltsp/dhcpd.conf"

---

### Post by hundred1906 on 2010-11-23
Grief. I just knew it was going to be more complicated than advertised. Aside from the fact that my /etc/ltsp/ does not contain a dhcpd.conf (I will chase that down later) what is the "host" option or where can I read about it? And does it then mean that my wireless devices log themselves on or do I have to set up specific MAC addresses for each - which would not be good.

And what then is the next problem, because I am beginning to think that the extra local disk plus messy cables is the more attractive option.

---

### Post by lank23 on 2010-11-23
> **hundred1906 said:**
> Grief. I just knew it was going to be more complicated than advertised. Aside from the fact that my /etc/ltsp/ does not contain a dhcpd.conf (I will chase that down later) what is the "host" option or where can I read about it? And does it then mean that my wireless devices log themselves on or do I have to set up specific MAC addresses for each - which would not be good.

And what then is the next problem, because I am beginning to think that the extra local disk plus messy cables is the more attractive option.

Don't be discouraged, it was a learning process for me also.

1:  You might not have that file "/etc/ltsp/dhcpd.conf" due that you might not have "Linux Terminal Server Project" installed, when you follow the procedure this package will be installed and configured to do simple DHCP for you network.

2:  My "/etc/ltsp/dhcpd.conf" is posted below but but I have changed the MAC address ;)  You can see how to setup if the "host" settings to do a static DHCP for each machine, ipod, etc...  Note my router is 192.168.1.1, and my server is 192.168.1.2

```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.3 192.168.1.20;
    option domain-name "mythbuntu.server.home.com";
    option domain-name-servers 192.168.1.1;
    option broadcast-address 192.168.1.255;
    option routers 192.168.1.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
     
    } else {
        filename "/ltsp/i386/nbi.img";
    }

    host ipod-touch {
	hardware ethernet 90:84:0d:12:34:G5;  #Ipod-touch WLAN
	fixed-address 192.168.1.10;
	}

    host E6400-laptop {
	hardware ethernet 00:21:6a:09:87:F4;  #E6400 Laptop WLAN
	fixed-address 192.168.1.4;
	}

    host Epia {
	hardware ethernet 00:40:63:30:31:E3;  #Epia-CL Eth0
	fixed-address 192.168.1.5;
	}

    host D620-laptop {
	hardware ethernet 00:21:80:40:41:D2;  #D620 Laptop WLAN
	fixed-address 192.168.1.6;
	}

}

```

lank23

---

### Post by hundred1906 on 2010-11-26
I thought I went right through the procedure. Where does it install "Linux Terminal Server Project" and how do I know if I have it or not. Hang-on, cancel that, I just realised what ltsp stands for.

If you mean this line <sudo apt-get install mythbuntu-diskless-server-standalone tftpd-hp> I thought I already did that. How do I check or do I just do it again.

Plus what about the sequence at:
 <sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials="your-user-id-here:your-password-here"
For the credentials do not use "mythtv" it will already be created. Later we will setup mythtv ID to auto-login>

It would be useful to clarify userid and password (whose and why). And where is the auto-login sequence set within the scripts.

---

### Post by lank23 on 2010-11-26
> 
sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials="your-user-id-here:your-password-here"

For the credentials do not use "mythtv" it will already be created. Later we will setup mythtv ID to auto-login>


say your normal login name to the server is "hundred1906"
say your normal login password to the server is "coffee"

then the command would read

```
sudo ltsp-build-client --mythbuntu --mythbuntu-user-credentials="hundred1906:coffee"
```

the second part about mythtv ID, is just telling you not to run the above command with the username "mythtv" due it was be created and used to run the mythtv software. Nothing to worry about.

---

### Post by hundred1906 on 2010-12-01
Thanks for the reply. I am still interested but away. Back later this week and will give it all a try again.

---

### Post by hundred1906 on 2011-01-14
Am still going to need help with this.

LTSP is now installed but I need to set up my DHCP server address. I should say I am now running up from a basic Ubuntu Server install with the instructions from [http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless) applied. The DHCP3...conf file says that the LTSP ... conf takes precedence so that is the one to work on as per your notes below.
 Q1 How did you set up so that your server and router addresses are as you give below.

Q2 the wiki instructions talk about an "allow booting" configuration. Do I use this or not, if so where; in LTSP or DHCP?

Q3 did I make a mistake in selecting the standalone install - how would I know?

Thanks.

is at > **lank23 said:**
> Don't be discouraged, it was a learning process for me also.

1:  You might not have that file "/etc/ltsp/dhcpd.conf" due that you might not have "Linux Terminal Server Project" installed, when you follow the procedure this package will be installed and configured to do simple DHCP for you network.

2:  My "/etc/ltsp/dhcpd.conf" is posted below but but I have changed the MAC address ;)  You can see how to setup if the "host" settings to do a static DHCP for each machine, ipod, etc...  Note my router is 192.168.1.1, and my server is 192.168.1.2

[CODE]


lank23

---

### Post by hundred1906 on 2011-01-14
Am still going to need help with this.

LTSP is now installed but I need to set up my DHCP server address. I should say I am now running up from a basic Ubuntu Server install with the instructions from [http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless) applied. The DHCP3...conf file says that the LTSP ... conf takes precedence so that is the one to work on as per your notes below.
 Q1 How did you set up so that your server and router addresses are as you give below.

Q2 the wiki instructions talk about an "allow booting" configuration. Do I use this or not, if so where; in LTSP or DHCP?

Q3 did I make a mistake in selecting the standalone install - how would I know?

Thanks.

is at > **lank23 said:**
> Don't be discouraged, it was a learning process for me also.

1:  You might not have that file "/etc/ltsp/dhcpd.conf" due that you might not have "Linux Terminal Server Project" installed, when you follow the procedure this package will be installed and configured to do simple DHCP for you network.

2:  My "/etc/ltsp/dhcpd.conf" is posted below but but I have changed the MAC address ;)  You can see how to setup if the "host" settings to do a static DHCP for each machine, ipod, etc...  Note my router is 192.168.1.1, and my server is 192.168.1.2

[CODE]


lank23

---

### Post by hundred1906 on 2011-01-14
Am still going to need help with this.

LTSP is now installed but I need to set up my DHCP server address. I should say I am now running up from a basic Ubuntu Server install with the instructions from [http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless) applied. The DHCP3...conf file says that the LTSP ... conf takes precedence so that is the one to work on as per your notes below.
 Q1 How did you set up so that your server and router addresses are as you give below.

Q2 the wiki instructions talk about an "allow booting" configuration. Do I use this or not, if so where; in LTSP or DHCP?

Q3 did I make a mistake in selecting the standalone install - how would I know?

Thanks.

---

### Post by lank23 on 2011-01-15
Not saying this is he best way to do a setup, but I set my sever as DHCP, and then set my router as a static DHCP.  Or you can search for setting a static IP "likely be editing /etc/networks/interfaces  file"

> **hundred1906 said:**
> Am still going to need help with this.

LTSP is now installed but I need to set up my DHCP server address. I should say I am now running up from a basic Ubuntu Server install with the instructions from [http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless](http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless) applied. The DHCP3...conf file says that the LTSP ... conf takes precedence so that is the one to work on as per your notes below.
 Q1 How did you set up so that your server and router addresses are as you give below.

Q2 the wiki instructions talk about an "allow booting" configuration. Do I use this or not, if so where; in LTSP or DHCP?

Q3 did I make a mistake in selecting the standalone install - how would I know?

Thanks.

is at

---

### Post by hundred1906 on 2011-01-16
> **lank23 said:**
> Not saying this is he best way to do a setup, but I set my sever as DHCP, and then set my router as a static DHCP.  Or you can search for setting a static IP "likely be editing /etc/networks/interfaces  file"

Thanks, but that is pretty much pure Martian from where I am now as I have DHCP in the Ubuntu Server install and have the router set so it's not providing DHCP. I think I tell the server where the router is using the "option-routers 192.168.2.1" statement (is that the right ip - how would I know). Plus how do I set the ip for my server and how do I tell the router that address.

---

### Post by lank23 on 2011-01-17
You set your server IP address by editing "/etc/networks/interfaces" file.

You likely have something like this

```

auto eth0
iface eth0 inet dhcp

```

You will need to edit these lines to something like this

```

iface eth0 inet static
address 192.168.1.2   
netmask 255.255.255.0
gateway 192.168.1.1

```

Where "address" equals the IP address you want for your server
Where "gateway" equals the IP address of your router
Where "netmask" equals the same as the router netmask


To find these values open the configuration webpage of your router, if you know the make model you can search for the default values
View / Edit configuration located at 
```

http://192.168.1.1/   or  http://192.168.0.1   ....etc

```

lank23

---

### Post by hundred1906 on 2011-01-19
Lank23, thanks for that advice. My server is now obtaining an ip address and is chatting away to the router. ifconfig gives

eth0      Link encap:Ethernet  HWaddr 00:--:--:--:--:--  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: ----::---:----:----:------ Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:909899 (909.8 KB)  TX bytes:357832 (357.8 KB)
          Interrupt:19 Base address:0xb000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15644 (15.6 KB)  TX bytes:15644 (15.6 KB)

I don't think that DHCP is running though because I cannot see it in the list of running processes and because a second machine connected into the router is not being given a network address even though I have set up a host/mac entry for it inside my dhcpd.conf file within the ltsp folder, as below. Obviously I have blanked the MAC addresses for this post:

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.2.0 netmask 255.255.255.0 {
    range 192.168.2.20 192.168.2.250;
    option domain-name "Culture-Server.home.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.2.255;
    option routers 192.168.2.1;
    next-server 192.168.2.2;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
    host hp-frontend {
	hardware ethernet 00:--:--:--:--:--
	fixed-address 192.168.2.20
    }

---

### Post by lank23 on 2011-01-19
I think you're missing a " ; " at the end of the line "hardware ethernet 00:--:--:--:--:--"

if that " ; " is really missing in the real /etc/ltsp/dhcpd.conf file it will make the dhcp deamon terminate due to bad conf file on the test config step.

you could also stop and then start the dhcp deamon from the terminal by running these commands, if there are issue you should see them when the deamon starts.

```

sudo /etc/init.d/./dhcp3-server stop

```
then
```

sudo /etc/init.d/./dhcp3-server start

```

also check to make sure that port 67,  and 68  are not blocked on your firewall / router


lank23

---

### Post by hundred1906 on 2011-01-20
Yes, it was the pesky semi-colons.

Two steps forwards, one step back - now where is the pxelinux.0 file?

I followed the build instructions (sudo ltsp-build-client --mythbuntu ...), and there is a linux build there under /opt/ltsp/i386 but where is that specific file.

---

### Post by lank23 on 2011-01-20
Yes you got to watch for those config file issues.

Look in "/var/lib/tftpboot/ltsp/i386" 

This is where all the needed boot files and config files are located.
Open the "default" file within the pxelinux.cfg folder to modify your boot options.

lank23

---


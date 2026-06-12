---
title: "Diskless server installation stalling"
date: 2009-09-03
forum: Mythbuntu
---

### Post by pssturges on 2009-09-03
Hi,

I'm trying to set up the diskless server via MCC. Under system roles I check "Diskless Server" the click apply. The process begins and continues for about 30secs, then stalls at "Enabling overylay directory for mythbuntu diskless". It's been going about 6 hours now so it's definately locked up. Any thoughts what could be causing this?

I don't know if it matters, but I was on 9.04 plus fixes, but havinging read other posts that say that the diskless  won't work with the fixes, I rolled everything back.


One other question. I already have a DHCP server running on this box. I notice that DHCP server is not already ticked in MCC. Should I tick it? How will this affect my current DHCP config?

Thanks in advance.

Phil

---

### Post by pssturges on 2009-09-06
Still can't get this working. When I launch MCC from the command line then try to enable Diskless Server I get the following after I ctrl-C to kill MCC when it stalls:

```
phil@htpcserver:~/Desktop$ sudo mythbuntu-control-centre --debug
/var/lib/python-support/python2.6/MySQLdb/__init__.py:34: DeprecationWarning: the sets module is deprecated
  from sets import ImmutableSet
/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/changer.py:48: DeprecationWarning: The popen2 module is deprecated.  Use the subprocess module.
  from popen2 import Popen3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/core.py", line 1363, in apply_pressed
    call_applicator(self,to_install,to_remove,to_reconfigure)
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/core.py", line 1350, in call_applicator
    apply.commit_changes()
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/changer.py", line 251, in commit_changes
    self.process_configuration()
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/changer.py", line 449, in process_configuration
    self.communicator.run("set","mythbuntu-diskless/share_host " + network)
  File "/var/lib/python-support/python2.6/mythbuntu_common/debconftalk.py", line 44, in run
    response = debconf_read.readlines()[0].partition(' ')
IOError: [Errno 4] Interrupted system call
^CTraceback (most recent call last):
  File "/usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre", line 47, in <module>
    script.run()
  File "/usr/lib/python2.6/dist-packages/MythbuntuControlCentre/core.py", line 212, in run
    gtk.main()
KeyboardInterrupt
phil@htpcserver:~/Desktop$ 

```

I have googled "IOError: [Errno 4] Interrupted system call" which appears at about the same time as it stalls. It seems to be some sort of python bug? I have no idea where to go from there.

Any input much appreciated.

Phil

---

### Post by pssturges on 2009-09-07
Well I've given up trying to get this working with MCC and have tried setting it up the command line method as described [here.]("https://help.ubuntu.com/community/MythTV/Install/Hardy/Diskless") The install went smoothly but my clients will not boot. They go through all the DHCP stuff then stops at "TFTP". I then get an error "PXE-32: TFTP open timeout".

I'm not sure whether this has something to do with my dhcp setup. As I said in my first post I already had a dhcp server set up on my server machine, so I didn't use the standalone version and have attempted to modify my current dhcp config. The config file /etc/dhcpd.conf is as follows:

```
# Sample /etc/dhcpd.conf
# (add your comments here) 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option netbios-name-servers 192.168.0.10;
option domain-name-servers 192.168.0.1;
option domain-name "home";

subnet 192.168.0.0 netmask 255.255.255.0 {
	option domain-name "home";
	option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
        }
	host router {
		hardware ethernet 00:18:4d:5e:98:2e;
		fixed-address 192.168.0.1;
		}
	host htpcserver {
		hardware ethernet 00:18:F3:64:BF:37;
		fixed-address 192.168.0.10;
		}
	host theatrepc {
		hardware ethernet 00:E0:B0:E6:68:6C;
		fixed-address 192.168.0.2;
		}
	host bed1htpc {
		hardware ethernet 00:0F:1F:E1:9C:03;
		fixed-address 192.168.0.3;
		}
	host windowspc {
		hardware ethernet 00:14:C2:C8:F7:EA;
		fixed-address 192.168.0.11;
		}
	host laptop02 {
		hardware ethernet 00:0F:1F:17:E9:1D;
		fixed-address 192.168.0.12;
		}
	host jacobpc {
		hardware ethernet 00:16:D3:59:F8:B1;
		fixed-address 192.168.0.13;
		}
	host phillaptop {
		hardware ethernet 00:22:20:01:4E:FD;
		fixed-address 192.168.0.14;
		}
	host phillaptop-w {
		hardware ethernet 00:22:43:46:06:34;
		fixed-address 192.168.0.21;
		}
	host marionlaptop-w {
		hardware ethernet 00:1e:65:2e:f4:be;
		fixed-address 192.168.0.22;
		}
	host philsiphone {
		hardware ethernet 00:21:e9:56:90:3c;
		fixed-address 192.168.0.31;
		}
	host marionsiphone {
		hardware ethernet 00:21:E9:59:3B:A0;
		fixed-address 192.168.0.32;
		}
	host megansphone {
		hardware ethernet 00:24:7C:6C:27:64;
		fixed-address 192.168.0.33;
		}
	range 192.168.0.1 192.168.0.200;
	}

```

I have added the root path and the bit about the boot image as per the edubuntu reference.

I gotta say, I really don't quite understand the working of this diskless server business, just blindly following the instructions, so I'm sure I'm missing something very basic.

Once again thanks in advance for any help.

Phil

---

### Post by encom on 2009-09-08
You should have:

next-server 10.100.0.195;

That should be placed on the line above your "option root-path"

Replace the IP with the IP of your machine the diskless image is located.

---

### Post by pssturges on 2009-09-09
Thanks for the reply. Unfortunately it did not seem to help. I'm still getting the same error. 

Perhaps I should explain my setup a little more. I have an adsl modem router (192.168.0.1) with dhcp turned off. My server (192.168.0.10) handles mythbackend, dhcp, samba, cups and is the one I'm trying to set up the diskless server on. 

Cheers
phil

---

### Post by pssturges on 2009-09-15
Still haven't been able to get this working. Any ideas?

---

### Post by AlexanderDGreat on 2009-09-22
Hi, I have the same problem, I have no problems booting to LTSP server, but when I ENABLE the DHCP that comes from my router, it doesn't BOOT!

I've looked all around and yet can't find an answer!

---

### Post by blackoper on 2009-09-22
I avoided all this by using a dd-wrt router and the DNSMasq entry of something like: 
dhcp-boot=ltsp/i386/pxelinux.0,,192.168.1.153

Works perfectly with no pxe dhcp server needed

ddwrt wiki entry: [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=4662&highlight=pxe]("http://www.dd-wrt.com/phpBB2/viewtopic.php?t=4662&highlight=pxe")

Everything just works with this kind of setup.

---

### Post by SgtDude on 2009-09-23
> **blackoper said:**
> I avoided all this by using a dd-wrt router and the DNSMasq entry of something like: 
dhcp-boot=ltsp/i386/pxelinux.0,,192.168.1.153


Just tried it, and it worked for me.  You saved me a ton of time and effort.  Thanks much.

---

### Post by AlexanderDGreat on 2009-09-23
Hi, I've read that but I don't have that kind of router available in my area, I live in the Far East.

Anyway, thanks for the link, glad it helped someone.

If anyone is also reading this, what I did after installing the LTSP server:

I put a MAC Filter on the router and IP Filter to port 67 - which is DHCP's port.

Now it boots beatifully. My dhcpd.conf is the default one provided by LTSP.

Kind regards.

@pssturges: Do you have a firewall? Or do you have something in /etc/hosts.allow or /etc/hosts.deny? Also try giving only IP's to specific MAC addresses:

host test1 {
   hardware ethernet 00:11:22:33:44:55:66;
   fixed-address 192.168.0.15;
}

Finally, try to add the host "test1" in your /etc/hosts

127.0.0.1     localhost
127.0.0.1     (hostname)
192.168.0.15  test1

- this way you clients can quickly find their designation via your server.

I will post my /etc/ltsp/dhcpd.conf here later because I'm at work.

---


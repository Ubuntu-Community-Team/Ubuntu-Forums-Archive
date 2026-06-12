---
title: "Juniper Network Connect Help"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by lordhaworth on 2010-08-26
Hi,

Some history...
I used to be able to connect to my uni secure access vpn by navigating to the appropriate page, logging in and clicking "start" by "Network Connect" etc. etc.
After an update to firefox it had been failing, giving me a "session timeout" MsgBox. I have tried clearing history etc and reinstalling firefox. I have also tried different browsers with no success. 

So, I have since upgraded to 9.10 and now I get "Setup Failed, Sorry" in the bottom left of the screen (where "Done" is displayed once a page has loaded)...

I am now trying a different approach. I have downloaded ncui-6.5R2.i386.rpm and unpacked it fine. I have tried running it, without success and have also run the diagnostic - I will post results below:



When I try and run ./ncsvc I get the following:
```

ncsvc> Failed to setuid to root. Error 1: Operation not permitted

```


So I did a sudo ./ncsvc , which gives:
```

mkdir(/root/.juniper_networks) failed: Permission denied

```

I am pretty sure that my password above is correct - I re-tried it and got the same message... I can definitely do, e.g., sudo apt-get update fine. 


I then ran all of the tests available in ncdiag (./ncdiag -A) which gave the following info which might be useful

```

NC Diagnostics for Linux. 
Version 1.0.
Release Date/Time: Dec  9 2009 04:36:09
+=======================================================================
+=======+
|   Tests:			|    	 Results:		               |
+=======================================================================
+=======+

       o  NC Installation Check 	 Failed
       o  NC Diagnostics 			
             NC Service 		 Not Running
             NC Driver Test 		 Passed
             NC Tunnel Test 		 Not established

       o  Host Details  			
             Hostname 			 thomas-laptop
             Domainname 		 (none)
             IP Routing Enabled 	 No
             IP Loopback test 		 Passed
             Nameserver Details 	
              192.168.100.254 		 Ping Passed
             Gateway Ping Test 			 
             192.168.100.254 		 Ping Passed

       o  Network Connection Diagnostics  			

	     Interface:   		 lo
	     IP Address:  		 127.0.0.1
	     Netmask:     		 255.0.0.0
	     MTU:         		 16436

	     Interface:   		 usb0
	     IP Address:  		 192.168.100.100
	     Netmask:     		 255.255.255.0
	     Broadcast:   		 192.168.100.255
	     MTU:         		 1500
      o  Route Info 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 usb0

       Finished running tests 
+=======================================================================
+=======+

```

Any ideas on what more I can do to get this running?

Cheers

---

### Post by Fire_Chief on 2010-08-26
Might try switching to the root account to run the setup instead of using sudo.

---

### Post by lordhaworth on 2010-08-26
Cheers, I'll give it a go tonight.

---


---
title: "IPSec VPN Tunnel Connection Help &gt; ....."
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by stoynev on 2010-02-17
Hello, I am getting this error when I try to bring up IPSec Tunnel... Looking for someone help.. Thanks...

> Starting connection with command /usr/sbin/ipsec auto --up 'paycode-to-vivacom' ..

104 "paycode-to-vivacom" #7: STATE_MAIN_I1: initiate
003 "paycode-to-vivacom" #7: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106 
003 "paycode-to-vivacom" #7: ignoring Vendor ID payload [FRAGMENTATION c0000000]
106 "paycode-to-vivacom" #7: STATE_MAIN_I2: sent MI2, expecting MR2
003 "paycode-to-vivacom" #7: received Vendor ID payload [Cisco-Unity]
003 "paycode-to-vivacom" #7: received Vendor ID payload [XAUTH]
003 "paycode-to-vivacom" #7: ignoring unknown Vendor ID payload [c5e228ecee81618df6d2cd7eef3b0bb4]
003 "paycode-to-vivacom" #7: ignoring Vendor ID payload [Cisco VPN 3000 Series]
003 "paycode-to-vivacom" #7: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: no NAT detected
108 "paycode-to-vivacom" #7: STATE_MAIN_I3: sent MI3, expecting MR3
010 "paycode-to-vivacom" #7: STATE_MAIN_I3: retransmission; will wait 20s for response
003 "paycode-to-vivacom" #7: discarding duplicate packet; already STATE_MAIN_I3
003 "paycode-to-vivacom" #7: discarding duplicate packet; already STATE_MAIN_I3
003 "paycode-to-vivacom" #7: discarding duplicate packet; already STATE_MAIN_I3
010 "paycode-to-vivacom" #7: STATE_MAIN_I3: retransmission; will wait 40s for response
003 "paycode-to-vivacom" #7: next payload type of ISAKMP Hash Payload has an unknown value: 31
003 "paycode-to-vivacom" #7: malformed payload in packet
031 "paycode-to-vivacom" #7: max number of retransmissions (2) reached STATE_MAIN_I3.  Possible authentication failure: no acceptable response to our first encrypted message
000 "paycode-to-vivacom" #7: starting keying attempt 2 of at most 3, but releasing whack


ipsec.conf 

> conn paycode-to-vivacom
        auth=esp
        authby=secret
        auto=start
        esp=3des-168
        ike=3des-md5
        ikelifetime=8h
        keyexchange=ike
        keyingtries=3
        keylife=1h
        left=95.43.208.250
        leftid=95.43.208.250
        leftnexthop=95.43.208.249
        pfs=yes
        right=212.39.72.21
        rightsubnet=10.16.0.0/24
        type=tunnel


**PLESE, any help or suggestions will be very appreciated!**

**Connection Configuration >>>**  [http://i48.tinypic.com/1823ba.jpg](http://i48.tinypic.com/1823ba.jpg)

---

### Post by stoynev on 2010-02-19
:/ any help ?

---

### Post by whit on 2010-03-10
Which IPsec package are you using? Is there a subnet on your side you're trying to connect? Is your ipsec.secrets file set up? Are you sure PFS is on on the other end? If that "connection configuration" file is right, the IPs it lists aren't within your right subnet's /24. There's really not enough information in your post here to tell.

---

### Post by stoynev on 2010-03-11
**SOLVED thank you :)**

---

### Post by mondalaci on 2011-07-25
> **stoynev said:**
> **SOLVED thank you :)**

You might as well share with us what the solution is, especially considering that I'm having the same issue.

---

### Post by stoynev on 2011-07-25
> **mondalaci said:**
> You might as well share with us what the solution is, especially considering that I'm having the same issue.

Make sure that the other side has the right configuration setup for you! That was my problem, I was sending the right information to the other side of the tunnel but I didn't received any response, that was because mine IP was wrong from the other side configuration.
Please make sure and let me know whats the result.

Thank you.

---

### Post by mondalaci on 2011-07-25
> **stoynev said:**
> Make sure that the other side has the right configuration setup for you! That was my problem, I was sending the right information to the other side of the tunnel but I didn't received any response, that was because mine IP was wrong from the other side configuration.
Please make sure and let me know whats the result.

Thank you.

Thanks for the super fast reply!  Can you provide me the exact line in your configuration that you've added to make this happen?

Thanks in advance!

---


---
title: "wvdial disconnects immediately after connecting - ppp deamon dies"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by ub07 on 2012-07-08
I've seen this problem posted on various forums including this one, but nothing that was proposed was helpful to me. I have just installed Ubuntu 12.04 and am struggling to get dial-up to work satisfactorily. I managed to get wvdial to work under one administrator account without using sudo wvdial. However, on subsequent accounts that I have created, I run into the problem where the ppp daemon dies shortly after authenication. Specifically here is what I get:

<mycomputer>:~$ wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ4
ATZ4
OK
--> Modem initialized.
--> Sending: ATDT483 4052
--> Waiting for carrier.
ATDT483 4052
CONNECT 50666/ARQ/V92/LAPM/V44
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas36.2in1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: <mylogin>
<mylogin>
Password: 
--> Looks like a password prompt.
--> Sending: (password)
LDAP authenticated against <mylogin>
    Entering PPP Session.
    IP address is 4.252.88.51
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Sun Jul  8 10:56:33 2012
--> Pid of pppd: 2355
--> Disconnecting at Sun Jul  8 10:56:33 2012
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)

I have changed the permissions on pap-secrets, chap-secrets and options, and I added them to group dip. (There was an initial problem with this.) I have also added the users to the appropriate groups of dialout and dip.

The simple solution is to run sudo wvdial (which works), but that is not satisfactory to me because I want others to have access to the internet on this computer, and I don't feel comfortable giving them administrator accounts. In addition, I'm worried about the possible security problems associated with running wvdial as root.


Any help with this would be GREATLY appreciated.

Thanks.

---


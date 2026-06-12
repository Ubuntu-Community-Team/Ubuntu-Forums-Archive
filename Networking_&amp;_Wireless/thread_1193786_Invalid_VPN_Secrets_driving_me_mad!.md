---
title: "Invalid VPN Secrets driving me mad!"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by jegan21 on 2009-06-21
Under Ubuntu 9.04, I've created a VPN connection using the NetworkManager applet.  When I attempt to establish a connection, I receive the message "VPN Connection Failed...Invalid VPN secrets".  Now I have vpnc configured, and can establish a vpn connection outside of the NM applet by using vpnc on the command line.  I've tried removing the ~/.gnome2/keyings, answering the prompts differently, and tried several solutions I found on the Internet, but nothing works.  Oddly I had a vpn connection working through NM on another PC, but now when I just tried it, it too failed due to invalid vpn secrets.

---

### Post by cgineste on 2009-06-24
Hi, 

I have the same problems, using Ubuntu Jaunty, and Intrepid on two different machines. It seems that this is due to the Gnome-keyring manager. I have also tried a range of different solutions proposed on the net, without success. 

Help would be very appreciated, 

Thank you 

Cedric

---

### Post by cgineste on 2009-06-24
Hi again, 

Just to clarify my previous post. I had no problems in accessing my university through VPN, except that I would have to enter my keyring password at every new session. 

I recently requested the keyring manager to save the password, and ever since I am unable to connect through the VPN. 

I feel that the solution should be with the settings of the keyring manager, and I had no success so far. 

Any ideas?
 
Thank you, 
Cedric

---

### Post by SL666 on 2009-06-30
I had the secrets error but it was solved by restarting network manager

sudo /etc/init.d/network-manager restart

Now i have the connection dropping after 5 minutes :(

---

### Post by jegan21 on 2009-06-30
If restarted the NetworkManager, deleted my gnome keyring files, and a whole lot more, and still I get the invalid VPN secrets error.

Bummer.

---

### Post by SL666 on 2009-06-30
tried connecting from the command line?

I managed to fix my 5min disconnections too.. as simple as enabling "Disable Dead Peer Detection"

---

### Post by jegan21 on 2009-07-04
Yes, I tried checking "Disable Dead Peer Detection" before, and it had no affect.  How do you attempt a connection from the command line?  I could then run an strace to see what files are being accessed.

-Thanks

---

### Post by jegan21 on 2009-07-04
I tried running the NetworkManager from the command line under strace, and still no answer:

strace -e trace=open NetworkManager --no-daemon

open("/etc/NetworkManager/VPN", O_RDONLY|O_NONBLOCK|O_DIRECTORY|O_CLOEXEC) = 9
open("/etc/NetworkManager/VPN/nm-vpnc-service.name", O_RDONLY) = 10
NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'...
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 15820
NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections
NetworkManager: <info>  VPN plugin state changed: 1
NetworkManager: <info>  VPN plugin state changed: 3
** Message: <info>  vpnc started with pid 15829

NetworkManager: <info>  VPN connection 'moe-boca' (Connect) reply received.
/usr/sbin/vpnc: hash comparison failed:  (ISAKMP_N_AUTHENTICATION_FAILED)(24)
check group password!

** (process:15820): WARNING **: <WARN>  vpnc_watch_cb(): vpnc exited with error code 2

NetworkManager: <info>  VPN plugin failed: 0
NetworkManager: <info>  VPN plugin state changed: 6
NetworkManager: <info>  VPN plugin state change reason: 10
NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.
NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
syscall_293(0x7fff4f83d0d0, 0x80000, 0x4637c8, 0x7fb147816750, 0, 0x1553fd0, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160, 0x7fff4f83d160) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
--- SIGCHLD (Child exited) @ 0 (0) ---
NetworkManager: <debug> [1246681021.002029] ensure_killed(): waiting for vpn service pid 15820 to exit
NetworkManager: <debug> [1246681021.002170] ensure_killed(): vpn service pid 15820 cleaned up

---

### Post by SL666 on 2009-07-04
command line:

vpnc-connect

enter all the details.

vpnc-disconnect

---

### Post by jegan21 on 2009-07-05
I should have mentioned that I am able to establish a VPN connecting using vpnc.  I just can't using the NetworkManager.  I've tried so many ways using Applications -> Accessories -> Passwords and Encryption Keys, and System -> Preferences -> Encryption and Key Rings.  I've deleted my .gnome2/keyrings.  I've also manipulated the NetworkManager files such as /home/bernie/.gconf/system/networking/connections/1/vpn, among other's, and still get an "Invalid VPN Secrets" error!!!

---

### Post by subvertbeats on 2009-07-15
Hmmm very similar issues here. Did you get any closer to a solution?

Heres some relevant entries from my daemon.log

Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.pptp'... 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 23319 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info> VPN service 'org.freedesktop.NetworkManager.pptp' just appeared, activating connections 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info>  VPN plugin state changed: 3 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info>  VPN connection 'work' (Connect) reply received. 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <WARN> nm_vpn_connection_connect_cb(): VPN connection 'work' failed to connect: 'No VPN secrets!'. 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <WARN> connection_state_changed(): Could not process the request because no VPN connection was active. 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info>  (wlan0): writing resolv.conf to /sbin/resolvconf 
Jul 14 21:13:17 bwilliams-t60p NetworkManager: <info>  Policy set 'Auto SKY15375' (wlan0) as default for routing and DNS. 
Jul 14 21:13:29 bwilliams-t60p NetworkManager: <debug> [1247602409.005135] ensure_killed(): waiting for vpn service pid 23319 to exit 
Jul 14 21:13:29 bwilliams-t60p NetworkManager: <debug> [1247602409.005252] ensure_killed(): vpn service pid 23319 cleaned up

---

### Post by kstephens on 2009-07-17
I thought this was broken for me, but I really did have "invalid VPN secrets".  Check your group password, mine was very cryptic.

---

### Post by hibliss on 2009-07-17
There is a thread [here]("http://ubuntuforums.org/showthread.php?t=1215168") that says he solved this issue.

For me to connect to a PPTP VPN, I had to follow [this]("http://www.splatdot.com/2008/11/19/ubuntu-810-how-connect-microsoft-vpn") guide. PPTP VPN connections did not work for me out of the box in Intrepid or Jaunty until I did this.

The VPN secrets thing had to do with Keyring no saving the password properly, and I remember a workaround for that, but thought it had been resolved.

---

### Post by soan on 2009-08-11
Had this problem and was also driving me crazy.

Did this:
sudo /etc/init.d/networking restart

And tried to connect again, got a nice popup asking for access to keyring which you just say yes too. Now VPN working.

---

### Post by leonsmith on 2009-08-19
This thread is appropriately named. I am ready to throw my laptop out the window and go buy one with Windows installed. Anybody that knows me knows that I would rather eat broken glass than use Windows. 

I have tried every tip on the net regarding this "invalid VPN secrets" crap. Could we a little more arcane ? WHAT friggin secrets ? 

I did like learning about the config editor more, but come on, I work on three machines, I have a client on retainer and I HAVE to have VPN access. I only need it when things go wrong and they need me to fix something. The more urgent the fix the more likely that something in Ubuntu that has worked forever will all of a sudden take a crap for no reason whatsoever. 

So thanks a lot for the suggestions on this thread but I am out of ideas, a pissed off client, and a laptop in danger of the dump.

I'll go calm down and try again as always.

---

### Post by nickpiggott on 2009-08-24
I had this problem occur directly after installed some 3rd party software (the 3 UK mobile phone network's own linux package for controlling their MF627 USB stick).

That package had (re)written my /etc/ppp/options file, which included:

```
refuse-chap
refuse-mschap
refuse-mschap-v2
refuse-eap

```

Renaming the options file to old-options fixed the problem immediately. (It also meant that Gnome Dialer, which I use intermittently as a wrapper to wvdial, also worked again).

It looks like the options file overrides any settings made in individual dialling configurations. I've no idea if the 3 software will work any more.

---

### Post by phorque on 2010-01-08
hey guys,

i was having a similar problem in karmic.

turns out my LDAP password had changed in the VPN and i'd forgotten to change the one in my keyring. I ran Seahorse from the terminal to do so and then my VPN connected fine. :)

Thanks for the leads!

---

### Post by SumoSy on 2010-01-09
I cannot get past the keyring lock message to even see if my vpnc connection is working. 
 
I have read alot here and on the internet regarding the "keyring is locked" message. From what I can tell the keyring is an encrypted password repository. I have many solutions found here and nothing seems to work.
 
When I got to configure my vpnc I import the contents of my PCF file and when I got to save it I get the keyring is locked message and I am prompted for a password. I use my login password and it is declined. I changed my default password in the keyring to my login password and re-tried my vpnc config and got the seem problem.
 
I guess one thing I do not understand is how or what mechanism makes the relationship between my vpnc password config and the keyring? I suppose what I am saying is I really do not understand how the keyring works. If it is trying to validate a password in my vpnc config against the default keyring this isn't going to work...
 
Any help would be appreciated.   John

---

### Post by dedmeet on 2010-03-18
Hi,

I had the same (or similar issues)
pptp vpn would not connect.

Kept getting error in log:

nm_vpn_connection_connect_cb(): VPN connection 'xxxxxxx' failed to connect: 'No VPN secrets!'.

I removed the 'available to all users' tick in the config, which then made it work.

Hope this is as simple for others.

using Karmic

---

### Post by synlub on 2010-04-22
> **dedmeet said:**
> Hi,

I had the same (or similar issues)
pptp vpn would not connect.

Kept getting error in log:

nm_vpn_connection_connect_cb(): VPN connection 'xxxxxxx' failed to connect: 'No VPN secrets!'.

I removed the 'available to all users' tick in the config, which then made it work.

Hope this is as simple for others.

using Karmic

This solution is working for me in lucid beta2

---

### Post by nNifty on 2010-06-01
> **dedmeet said:**
> Hi,
I removed the 'available to all users' tick in the config, which then made it work.

Hope this is as simple for others.


Thanks! Works for me in Lucid (10.04) final.

---

### Post by derekshaw on 2010-10-05
> **dedmeet said:**
> Hi,
...
I removed the 'available to all users' tick in the config, which then made it work.

This fix worked for me using Lucid (10.04.1)

although the log now shows "Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.", the VPN does work.

---

### Post by faheyd on 2010-12-01
> **dedmeet said:**
> Hi,

I had the same (or similar issues)
pptp vpn would not connect.

Kept getting error in log:

nm_vpn_connection_connect_cb(): VPN connection 'xxxxxxx' failed to connect: 'No VPN secrets!'.

I removed the 'available to all users' tick in the config, which then made it work.

Hope this is as simple for others.

using Karmic

Thanks, this worked for me in 10.10 !

---

### Post by nmilyaev on 2011-11-29
I had this error due to the wrong password. The day before I changed my linux password on the target box and since the network manager kept the old password the connection did fail. I have changed the password in network manager and it all worked.

Thanks for the tip with the "Availabke to all users", that helped me earlier.

---

### Post by Sean.m on 2012-06-14
I know this is kind of an old thread but if it's a Cisco vpn, check your "GroupPwd=" line in your pfc file, if it's blank and instead you have an "enc_GroupPwd=", NetworkManager doesn't recognize this as a group password. Go [here]("http://www.unix-ag.uni-kl.de/%7Emassar/bin/cisco-decode") to get your decrypted group password and reenter it in NetworkManager. This did the trick for me.

---


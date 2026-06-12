---
title: "Samba isn't working"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by CalcProgrammer1 on 2008-12-13
I'm trying to get Samba to work, but it just won't.

I'm on a university dorm LAN, which is pretty much our entire floor (maybe even building) on an Ethernet switch network.  In Windows, the Network page shows 20+ PC's with around 10 workgroups.

Since I have multiple computers, I decided it'd be good to name them all ADAM-<computer> (since I'm Adam).  This means I have:

ADAM-DESKTOP (my Ubuntu machine)
ADAM-LAPTOP (my Vista 64 laptop)
ADAM-THINKPAD (my old XP laptop)

To group them, I'm using a workgroup ADAM-COMPUTERS for all of them.

I have a few folders I want to share with everyone (no users, just anyone who accesses it, no password).  I do not want people to write to these folders, just read.  My problem right now is that I can't even access my computer, let alone read anything.  It shows up under the network listing properly (as ADAM-DESKTOP under workgroup ADAM-COMPUTERS) but clicking on it leads to a long period of waiting followed by an error saying the server cannot be found/doesn't exist/etc.  When I booted my desktop, I was able to get a logon box (asking for username/password) for a few seconds before the PC finished booting, but then it went back to errors.  Problem is, I don't want it asking for passwords, I want anyone to be able to access it!

I have a really messed up smb.conf too, probably has errors, I tried gadmin-samba but it messed up more than it fixed.

What would I need to put in my smb.conf to make it do what I want?

---

### Post by gregphil on 2008-12-13
Samba configuration is not as simple as you would like it to be (or it should be).

It should be easy for you to share some directories to everyone in read-only mode.  You will have to enable "guest" access.

Ubuntu broke GUI **browsing** of **[COLOR=Black]authenticated[/COLOR]** Windows shares (at Hardy and above), so you probably won't be able to browse Windows shares on other machines unless they happen to allow unsecure anonymous connections.  You can still connect to them if you know and enter the FULL path to the share.

I suggest you install the Samba-doc package and then read all about Samba configuration, I know it is a pain but there really is no easy way.  Don't forget to stop and restart the smb service after editing the /etc/samba/smb.conf file to make the changes take effect. (as root do  /etc/init.d/samba restart ).

Good Luck.

---

### Post by CalcProgrammer1 on 2008-12-13
Hmm, after messing around with the smb.conf, I managed to get it to share.  However, it ONLY WORKS if I type my domain (r01amhb59.device.mst.edu).  If I type ADAM-DESKTOP it just denies it.  This is quite annoying, because ADAM-DESKTOP is what shows up in the Windows list, so it should work.

I'm wondering if this has anything to do with WINS server or DNS proxy, as I don't know what to put for those options.  I'm using the usershare feature so that Nautilus-share's Share dialog works (it does, the shares I made in Nautilus work over the domain connection).

Adding:
usershare max shares = 1000 (is there a way to do infinite? not that I'll need over 1000 shares)
usershare owner only = false
usershare allow guests = yes

seemed to get nautilus-share working.

Adding:

guest ok = yes

to [global] seemed to get it to display the list rather than prompt for passwords.

I also want to get my printer to work.  It's a Photosmart C4480 and is already detected and working in Ubuntu, in fact, it already shows up on Windows if I access my share by domain.  The error I get when clicking on it is:

"Operation could not be completed (error 0x00000709).  Make sure that you have typed the name correctly, and that the printer is connected to network."

The printer is sort of important, but mainly I want to get the name thing sorted out, other people won't know what my domain name is, they can only see the network list, so that needs to work.

---

### Post by CalcProgrammer1 on 2008-12-13
Apparently this has to do with NetBIOS broadcasting.  I don't think my network uses a WINS server (how do you tell?) and watching Wireshark there were some name broadcasts, but not from my desktop.

I added:

netbios name = ADAM-DESKTOP

but this doesn't seem to do anything.

---

### Post by CalcProgrammer1 on 2008-12-14
Hmm...this is getting more and more confusing.  I installed Winbind and my server shows up in the directory list again, and I can still connect via IP.  Although it shows up on the list, I still can't access it by name.

However, when I do

ping adam-desktop

in XP, it says that it resolved adam-desktop to 131.151.158.238, while my actual IP is 131.151.158.128.  This may be the source of the problem.  Why would it resolve to the wrong address?

---

